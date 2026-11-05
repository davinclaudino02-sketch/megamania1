# 🚀 MEGA MANIA — Space Shooter

Jogo de tiro espacial (shmup) de tela fixa para navegador, inspirado no clássico **Megamania** do Atari 2600.

Implementado em um **único arquivo HTML** com JavaScript puro e Canvas API — sem dependências externas.

## 🎮 Como jogar

Basta abrir o arquivo `index.html` diretamente no navegador. Nenhum servidor ou instalação é necessário.

### Controles

| Ação | Teclado | Mobile |
|------|---------|--------|
| Mover | `← →` ou `A` `D` | Arrastar ou botões ◀ ▶ |
| Atirar | `Espaço` ou `Enter` | Botão **FIRE** ou toque |

## 🛸 Mecânicas

- **Nave do jogador** — move-se apenas horizontalmente na parte inferior da tela
- **Barra de energia** — drena continuamente; chega a zero → perde uma vida; eliminar a onda toda → restaura tudo
- **3 vidas** — ao perder todas, fim de jogo
- **Colisão** — encostar em inimigo ou ser atingido por projétil custa uma vida

## 👾 Ondas de inimigos

A cada nível o visual dos inimigos muda, ciclicamente:

| # | Tipo | Paleta |
|---|------|--------|
| 1 | 🛸 Ship | Ciano + Azul |
| 2 | 🚀 Rocket | Vermelho + Laranja |
| 3 | ☄️ Meteor | Cinza + Laranja |
| 4 | 🐉 Dragon | Verde neon + Lima |
| 5 | 💎 Diamond | Magenta + Rosa |

- Grid 8 × 3 inimigos com movimento em bounce e descida gradual
- Inimigos miram no jogador ao atirar
- Mergulhos kamikaze aleatórios (primeira fileira)

## 🖥️ Renderização

- Resolução lógica: **320 × 240 px** (proporção 4:3)
- Escala por múltiplo inteiro (pixelado nítido) com barras pretas nas sobras
- `image-rendering: pixelated` + `imageSmoothingEnabled = false`
- Sprites 100% via código (matrizes de pixels) — sem imagens externas

## 🔊 Áudio

Gerado inteiramente via **Web Audio API**:

- **Tiro** — onda quadrada com frequência descendente (1200 → 300 Hz)
- **Explosão** — ruído branco filtrado + onda grave descendente
- **Level Up** — arpejo ascendente em onda quadrada
- **Morte** — sawtooth cromático descendente

> O áudio é inicializado somente após a primeira interação do usuário, respeitando as políticas dos navegadores modernos.

## 📁 Estrutura do arquivo

O `index.html` está organizado em seções internas comentadas:

```
├── Seção 1 — Constantes e configuração (ajustáveis)
├── Seção 2 — Sprites (pixel art via matrizes)
├── Seção 3 — Áudio (Web Audio API)
├── Seção 4 — Entrada (teclado e toque)
├── Seção 5 — Estado do jogo
├── Seção 6 — Lógica do jogo
├── Seção 7 — Renderização
├── Seção 8 — Loop principal (requestAnimationFrame)
└── Seção 9 — Inicialização e redimensionamento
```

## ⚙️ Constantes ajustáveis

No topo do arquivo `index.html` você encontra constantes que permitem tunar a dificuldade e o comportamento do jogo:

```js
const PLAYER_SPEED        = 110;  // px/s
const PLAYER_BULLET_SPEED = 280;  // px/s
const PLAYER_FIRE_RATE    = 0.22; // segundos entre tiros
const ENERGY_DRAIN_RATE   = 4.5;  // energia perdida por segundo
const ENEMY_COLS          = 8;
const ENEMY_ROWS          = 3;
const ENEMY_SPEED_X_BASE  = 28;   // px/s
const ENEMY_BULLET_SPEED  = 90;   // px/s
// ...e mais
```

## 📄 Licença

MIT — sinta-se livre para usar, modificar e distribuir.
