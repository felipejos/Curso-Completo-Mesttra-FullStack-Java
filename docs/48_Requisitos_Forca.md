# ✅ Requisitos do Jogo da Forca

## 🧩 Jogo da Forca — Requisitos Funcionais

### Requisito 1.1: Leitura das Palavras
- O sistema deve carregar uma lista de palavras a partir de um arquivo de texto (**palavras.txt**).
- Cada linha do arquivo representa uma palavra distinta.
- Caso o arquivo não exista ou esteja vazio, o jogo não deve iniciar e uma mensagem de erro deve ser exibida.

### Requisito 1.2: Seleção da Palavra Secreta
- O jogo deve escolher aleatoriamente uma palavra da lista carregada.
- A palavra escolhida deve ser convertida para letras minúsculas.

### Requisito 1.3: Mecânica de Jogo
- A cada interação do jogo a console deve ser limpa para gerar a sensação de tela atualizada.
- O jogador inicia com **6 vidas**.
- A cada rodada, o jogador deve digitar **uma letra**.
- Letras repetidas não devem ser aceitas novamente. Caso isto ocorra o jogador deve ser alertado e solicitado a digitar outra letra.
- Se a letra estiver na palavra, ela é exibida nas posições corretas conforme a palavra.
- Se a letra não estiver na palavra, o jogador perde uma vida, e um novo desenho da forca deve ser exibido.

### Requisito 1.4: Fim de Jogo
- O jogo termina quando:
  - O jogador acerta todas as letras da palavra (**vitória**).
  - O jogador perde todas as vidas (**derrota**).
- Ao final do jogo, deve ser exibida:
  - A palavra secreta.
  - Uma mensagem de vitória ou derrota e o estado de como estava a forca.

### Requisito 1.5: Exibição da Forca
- A cada erro, uma nova parte da forca deve ser exibida, até completar o desenho ao fim das 6 tentativas.
- A forca deve ser desenhada utilizando caracteres de texto para simular ao conceito de **Art ASCII**.

### Requisito 1.6: Interface de Texto
- O jogo deve funcionar em um terminal/console.
- A tela deve ser limpa a cada nova jogada para atualizar a exibição do estado atual do jogo.

### Requisito 1.7: Informações Visuais Durante o Jogo
Durante o jogo, deve ser exibido:
- Quantidade de vidas restantes.
- Letras já tentadas.
- A palavra com letras adivinhadas no formato `__X__` onde **X** são as letras já adivinhadas e `_____` para as letras ainda ocultas.
- A forca correspondente ao número de erros.

---

## 🎭 Desenho da Forca (ASCII)

### 6 vidas:
    +---+
    |   |
        |
        |
        |
        |
    =========

### 5 vidas:
    +---+
    |   |
    O   |
        |
        |
        |
    =========

### 4 vidas:
    +---+
    |   |
    O   |
    |   |
        |
        |
    =========

### 3 vidas:
    +---+
    |   |
    O   |
   /|   |
        |
        |
    =========

### 2 vidas:
    +---+
    |   |
    O   |
   /|\  |
        |
        |
    =========

### 1 vida:
    +---+
    |   |
    O   |
   /|\  |
   /    |
        |
    =========

### Perdeu:
    +---+
    |   |
    O   |
   /|\  |
   / \  |
        |
    =========

---

# 🛡️ Requisitos Não Funcionais

## 2.1. Estrutura de Arquivo
- O arquivo **palavras.txt** deve estar localizado em um caminho acessível e correto, definido no código.
- Exemplo de caminho absoluto:
  - `C:\jogoForca\src\palavras.txt`

## 2.3. Usabilidade
- O jogo deve ser jogável apenas com entrada de texto via teclado.
- Não deve permitir entrada inválida (como strings ou números em vez de uma única letra).

---

# 🖥️ Exemplos de Telas

- Início do Jogo
![OnlineGDB - exemplo](../images/1_inicio_jogo.png)

- Algumas Letras já tentadas
![OnlineGDB - exemplo](../images/2_tentadas.png)

- Algumas Letras Acertadas
![OnlineGDB - exemplo](../images/3_acertadas.png)

- Letra Repetida
![OnlineGDB - exemplo](../images/4_repetida.png)

- Jogador Perdeu
![OnlineGDB - exemplo](../images/5_perdeu.png)

- Jogador Ganhou
![OnlineGDB - exemplo](../images/6_ganhou.png)
