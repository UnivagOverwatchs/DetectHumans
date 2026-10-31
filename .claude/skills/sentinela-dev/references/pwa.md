# PWA (pwa/)

Stack: ver SKILL.md. Telas numeradas: `prototipo.md`.

## Fluxo principal
Entrar -> Início -> Alerta -> Em atendimento.
- Em Alerta: botão "Estou indo" (assume; vira Em atendimento).
- Em Em atendimento: "Resolver" (Resolvido) e "Falso alarme" (pede confirmação antes).
- O alerta aberto mostra foto (por endereço protegido), câmera, hora e estado.
- Dois cuidadores: se outro já assumiu, mostrar quem e quando.

## Instalação
- No iPhone o push só funciona com a PWA **instalada pelo ícone** (Compartilhar -> Adicionar à Tela de Início). A tela "Instalar" explica isso com passos e imagem.
- Android/Chrome: usar o aviso de instalação do navegador.
- Pedir permissão de notificação só depois do login, por ação do usuário.
- Risco de iPhone e como testar: `plano.md`.

## Offline
Service worker guarda só **texto** (lista de alertas, histórico recente). Nunca foto em cache nem em armazenamento local. Sem rede, a tela de alerta mostra "foto indisponível sem conexão".

## Acessibilidade
- Alvos de toque de pelo menos 44 px.
- Contraste mínimo 4,5:1 para texto.
- Não depender só de cor: cada estado tem ícone e texto.
- Textos em português simples; botão principal único por tela.
- Verificação: Lighthouse e teste manual em celular. A skill de WCAG ainda está "a verificar" (`skills-apoio.md`).

## Push no cliente
Receber o push abre o alerta pelo id. O texto do push não traz nome do residente.
