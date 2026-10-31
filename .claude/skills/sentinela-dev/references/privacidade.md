# Privacidade

**Barreira antes de qualquer saída: skill `guarda-sensivel`.** Esta skill não verifica dados sensíveis e não tem script para isso. O que a barreira faz e não cobre está no SKILL.md (Antes de qualquer saída; Regras).

A política de foto, retenção, push e offline está em "Decisões fixas" do SKILL.md. Aqui, o que as complementa.

## LGPD e consentimento (pontos a confirmar com o professor)
- Imagem de pessoa é dado pessoal, e de idoso em contexto de cuidado tende a ser dado sensível. Base legal e papéis (controlador e operador) **não estão decididos**: perguntar.
- Piloto: termo de consentimento da pessoa e do responsável, assinado antes de qualquer gravação. Modelo do termo: a fazer com o professor.
- Minimização: só a foto do momento; sem vídeo contínuo; residente por apelido.

## O que é guardado e por quanto tempo
| Dado | Onde | Quanto tempo |
|---|---|---|
| Foto do alerta | disco da API | até fechar o alerta ou o prazo de retenção |
| Registro em texto do alerta | banco | permanece no histórico |
| Quem abriu a foto | `acesso_midia` | permanece |
| Vídeos de teste com pessoas reais | máquina local, fora do Git | só enquanto o treino/teste precisar; apagar ao fim |

## Captura de tela e orientação à equipe
- Não tirar print nem colar no chat/documento imagem de pessoa real. Para documento e apresentação, use vídeo/cena encenada por colegas com consentimento, ou desenho.
- Dataset de treino com pessoas reais não vai para nuvem de terceiros.
- Vazou algo? Avise o grupo e o professor; não apague histórico do Git sozinho sem alinhar.

## Checklist de revisão de privacidade
- [ ] `.gitignore` cobre imagens, vídeos, `.env`, `runs/`, pesos e datasets reais.
- [ ] Nenhuma senha, chave, token no código (nomes de variáveis sim, valores não).
- [ ] A limpeza de fotos tem teste que passou.
- [ ] `guarda-sensivel` rodou antes da saída.
