# Visão (vision/)

Modelo, rastreador e licença: ver "Decisões fixas" no SKILL.md. Aqui só o como.

## Dados e divisão
- Separe treino, validação e teste **por vídeo ou cena**, nunca por quadro. Quadros vizinhos são quase iguais; dividir por quadro vaza a cena para o teste e infla a métrica.
- Imagens reais ficam fora do Git (regra em `privacidade.md`).

## Métricas que importam
Não use só mAP. Meça e registre com o comando usado:
- **Recall de queda**: quedas detectadas / quedas reais nos vídeos de teste.
- **Falsos alarmes por dia**: alertas sem queda em vídeos de rotina (extrapole para 24 h e diga que é estimativa).
- **Tempo até o alerta**: da queda ao evento enviado à API.

## Regra de queda em duas camadas
1. **Sinais por pessoa rastreada**: proporção da caixa (largura/altura passa de ~1), queda brusca da altura da caixa em poucos quadros, tempo parado no chão.
2. **Confirmação por tempo**: só gera evento se a condição de chão durar T segundos (valor inicial 3 a 5 s; ajuste com os vídeos de teste).
- **Zonas de cama** (e sofá): na zona, deitar não é queda; configurável por câmera.
Os limites acima são pontos de partida, não valores medidos.

## Testes automáticos (pytest, com vídeos ou sequências de caixas sintéticas)
Casos mínimos: agachar (não alerta), deitar na cama (não alerta), sentar rápido (não alerta), cair e levantar em poucos segundos (não alerta), cair e ficar parado (alerta), duas pessoas no quadro (rastreio separado).

## Modo demonstração
Lê um arquivo de vídeo no lugar da câmera e envia o evento igual ao real. Sem câmera ao vivo, a demonstração funciona igual.

## Desempenho
Rode em CPU: processe a cada N quadros (comece com N=3 a 5) e reduza a resolução. Meça quadros por segundo reais antes de dizer que aguenta várias câmeras.

## Contrato com a API
Evento = `POST /eventos` (campos em `api.md`). A foto sai do quadro do momento da queda; nunca grave vídeo contínuo.

## Uso da Ultralytics
Só local (detalhes em `skills-apoio.md`): `yolov8n.pt`, versão do pacote fixada no `requirements.txt`.
