# Plano

Hoje o projeto está em fase de visão (prototipo de detecção com YOLOv8 já existe no repositório). Datas abaixo vêm do enunciado da equipe; confirmar com o professor as entregas parciais.

## Marcos
| Data | Marco |
|---|---|
| 13/11 | evento simulado vira alerta no banco |
| 20/11 | alerta chega no celular com a PWA instalada |
| 27/11 | ponta a ponta + **congelamento de funcionalidades** |
| 04/12 | documento e apresentação prontos (meta interna) |
| 07/12 (segunda) | entrega |

## Calendário por semana (proposta minha para ajustar com a equipe; só os marcos acima vêm do enunciado)
| Semana | Foco | Pronto quando |
|---|---|---|
| até 06/11 | `docker-compose`, API com login, tabelas, `POST /eventos` | `curl` de evento cria alerta |
| 09 a 13/11 | visão envia evento de vídeo; alertas na API | marco 13/11 |
| 16 a 20/11 | PWA, push, instalação no celular real | marco 20/11 |
| 23 a 27/11 | foto protegida, limpeza, estados, ajuste da regra; revisão de segurança | marco 27/11 |
| 30/11 a 04/12 | só correção, documento, apresentação, ensaio da demonstração | marco 04/12 |

Quem faz cada área entre os 3 integrantes: **não informado**; perguntar.

## Cortes (nesta ordem, quando o prazo apertar)
1. Visão de computador do gestor (painel no computador).
2. Câmera ao vivo.
3. Escalonamento (reenvio a outro contato).
4. WebSocket (usar atualização por consulta).
5. Relatório e modo noite.
Nunca cortar: algo que quebre a meta mínima ou a privacidade.

## Como avaliar o prazo
Liste o que falta para o marco da semana, estime em dias de 1 a 3, compare com os dias úteis restantes e diga: cabe, cabe cortando X, não cabe. Estimativa não é medição: diga isso.

## Riscos
| Risco | Mitigação |
|---|---|
| Regra de queda com falso alarme | testes automáticos, confirmação por tempo, zonas de cama, medir falsos alarmes por dia |
| Push no iPhone só com PWA instalada | testar em iPhone real na semana de 16/11; plano B: abrir o app e ver a lista |
| CPU para várias câmeras | processar a cada N quadros; demonstrar com 1 câmera |
| Piloto não aprovado | demonstração com vídeo encenado |
| Pouco tempo | congelar em 27/11, cortes acima |
| Licença AGPL do Ultralytics | pergunta aberta ao professor |

## Demonstração
Roteiro (5 a 8 min): 1) problema em uma frase; 2) vídeo encenado de queda como câmera simulada; 3) detecção e evento; 4) push no celular com a PWA instalada; 5) abrir a foto, "Estou indo", "Resolver"; 6) mostrar foto apagada e histórico em texto.

Lista de conferência:
- [ ] Celular carregado, PWA instalada, notificação permitida
- [ ] Docker sobe com um comando; banco com dados de demonstração
- [ ] Vídeo de demonstração local (encenado, com consentimento) e plano B em outro vídeo
- [ ] Internet testada; plano B: rede local
- [ ] Uma pessoa narra, outra opera
- [ ] `guarda-sensivel` rodou antes de publicar slides ou documento
