# API (api/)

Stack: ver SKILL.md. Regras de foto, retenção e push: SKILL.md (Decisões fixas); aqui só a implementação.

## Tabelas (Prisma)
| Tabela | Campos principais |
|---|---|
| instituicao | id, nome |
| usuario | id, instituicao_id, nome, email, senha_hash, perfil (cuidador, gestor) |
| residente | id, instituicao_id, apelido, ativo |
| camera | id, instituicao_id, nome, local, ultimo_sinal_em, zonas_cama (json) |
| evento | id, camera_id, tipo, confianca, ocorrido_em, foto_caminho (anulável) |
| alerta | id, evento_id, estado, assumido_por, assumido_em, fechado_em, foto_apagada_em |
| acesso_midia | id, alerta_id, usuario_id, aberto_em |
| contato | id, residente_id, nome, telefone |
| configuracao | instituicao_id, tempo_confirmacao_s, horas_retencao (padrão 24) |
| assinatura_push | id, usuario_id, endpoint, chaves, criado_em |

Senha só como hash. Residente por apelido nas telas e nunca no push.

## Endpoints
| Método e rota | Função |
|---|---|
| POST /login | devolve JWT |
| POST /eventos | recebe evento do serviço de visão (chave de serviço por variável de ambiente) |
| GET /alertas, GET /alertas/:id | lista e detalhe |
| POST /alertas/:id/assumir | Pendente -> Em atendimento |
| POST /alertas/:id/resolver | Em atendimento -> Resolvido ou Falso alarme (corpo indica) |
| GET /alertas/:id/foto | foto protegida; exige JWT e grava em `acesso_midia` |
| CRUD /residentes, /cameras | só gestor altera |
| GET/PUT /configuracao | só gestor |
| POST /push/assinar, DELETE /push/assinar | registra e remove assinatura |

Transições inválidas retornam 409. Dois cuidadores assumindo juntos: o primeiro vence, o outro recebe 409.

## Perfis e autenticação
JWT com expiração curta; perfis cuidador (alertas) e gestor (também residentes, câmeras, configuração, histórico completo). Segredo do JWT em variável de ambiente.

## Foto por endereço protegido
Arquivos fora de pasta pública. Nome aleatório. Servidos só por `GET /alertas/:id/foto` após checar JWT e que o alerta pertence à instituição do usuário. Cada abertura vira linha em `acesso_midia`.

## Rotina de limpeza
Agendada (a cada 15 min): para cada alerta com foto, fechado, **ou** criado há mais de `horas_retencao`: apaga o arquivo, zera `foto_caminho` e grava `foto_apagada_em`. O registro em texto permanece. Teste: criar alerta, fechar, confirmar arquivo ausente e data preenchida; repetir pelo tempo.

## Web Push
Biblioteca `web-push`. Chaves VAPID **só em variáveis de ambiente** (`VAPID_PUBLIC_KEY`, `VAPID_PRIVATE_KEY`, `VAPID_SUBJECT`); `.env.example` com nomes sem valores. Carga: texto curto genérico e id do alerta. Assinatura que retornar 404/410 é removida.

## Alerta de sistema
Se `ultimo_sinal_em` de uma câmera passar de X minutos (padrão 2), cria alerta do tipo sistema "câmera sem sinal" (sem foto) para o gestor.

## Antes de usar uma biblioteca
Confirme a API na documentação atual (skill `find-docs`), não de memória.
