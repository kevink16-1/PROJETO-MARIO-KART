# Mario MMO (Terminal Game)

Um game de batalha por turnos inspirado no universo Mario, executado no terminal com Node.js. Dois jogadores escolhem personagens com atributos distintos, gerenciam itens estratégicos e disputam terrenos aleatórios em rounds dinâmicos até que apenas um permaneça com vida.

---

## Conceito do Projeto

Este projeto foi desenvolvido no bootcamp da DIO com foco em prática de lógica e construção de jogos em linha de comando. A proposta combina mecânicas de RPG leve com elementos clássicos do Mario, explorando estratégia, aleatoriedade e tomada de decisão em cada rodada.

---

## Tecnologias Utilizadas

* **JavaScript (ES Modules)**
* **Node.js**
* Módulo nativo:

  * `readline/promises` para entrada de dados assíncrona no terminal
* ANSI Escape Codes para estilização de saída no terminal

---

## Estrutura do Código

### 1. Interface de Entrada

O jogo utiliza `readline/promises` para capturar ações dos jogadores:

```js
const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout
});
```

---

### 2. Sistema de Personagens

Os personagens são definidos em uma lista de objetos com atributos de desempenho:

```js
const characters = [
  { name: "Mario", vel: 4, des: 3, for: 3, hp: 12 }
];
```

Cada personagem possui:

* **vel (velocidade)** para vantagem em reta
* **des (destreza)** para vantagem em curva
* **for (força)** para vantagem em combate
* **hp (vida)** como total de resistência
* **passiva** com efeito especial

---

### 3. Sistema de Itens

Itens são sorteados ao longo da partida:

```js
const itemsList = [
  { name: "Cogumelo", type: "heal" }
];
```

Tipos de efeito:

* `heal` para cura
* `damage` para dano direto
* `buff` para bônus temporário
* `debuff` para penalidade no oponente

Cada jogador pode carregar até **2 itens**.

---

### 4. Sistema de Turnos

O fluxo de cada turno segue esta ordem:

1. Jogadores podem receber loot (chance de 50%)
2. Um terreno é sorteado:
   * RETA usa velocidade
   * CURVA usa destreza
   * LUTA usa força
3. Cada jogador escolhe uma ação:
   * Atacar
   * Usar item
   * Ver inventário
4. Ambos rolam um dado de 1 a 6
5. O resultado considera:

   ```
   dado + atributo + bônus
   ```

6. O maior valor causa dano ao adversário

---

### 5. Sistema de Combate

* Empates podem ser resolvidos por habilidades passivas
* Dano aplicado:
  * Normal: 1 HP
  * Em LUTA: 2 HP

---

### 6. Animação de Dados

Há uma simulação de rolagem visual para deixar o turno mais dinâmico:

```js
for (let i = 0; i < 8; i++) {
  result = Math.random() * 6;
}
```

---

### 7. Controle Assíncrono

O projeto utiliza:

* `async/await`
* `sleep()` com `setTimeout`

Isso controla o ritmo entre ações e melhora a fluidez da partida no terminal.

---

## Como Executar

### 1. Instale o Node.js (versão 18+)

### 2. Salve o arquivo como:

```
mario-mmo.mjs
```

### 3. Execute:

```bash
node mario-mmo.mjs
```

---

## Como Jogar

* Escolha dois personagens (P1 e P2)
* Em cada rodada:
  * use itens com estratégia
  * aproveite o tipo de terreno sorteado
* A partida termina quando um jogador chegar a **0 HP**

---

## Possíveis Melhorias

* Modo singleplayer com IA
* Multiplayer online
* Sistema de save
* Interface gráfica (Electron ou Web)
* Sons e efeitos
* Balanceamento de personagens

---

## Aprendizados

Este projeto ajuda a praticar:

* Programação assíncrona em JavaScript
* Manipulação de entrada e saída no terminal
* Organização de lógica de jogo por funções
* Estruturação de regras com objetos e arrays

---

## Conclusão

O **Mario MMO (Terminal Edition)** mostra como construir uma experiência de jogo completa apenas com Node.js e criatividade, aplicando lógica, estratégia e interação em um ambiente simples e acessível.

---
