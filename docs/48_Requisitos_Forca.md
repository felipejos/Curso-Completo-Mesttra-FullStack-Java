# âœ… Requisitos do Jogo da Forca

## ðŸ§© Jogo da Forca â€” Requisitos Funcionais

### Requisito 1.1: Leitura das Palavras
- O sistema deve carregar uma lista de palavras a partir de um arquivo de texto (**palavras.txt**).
- Cada linha do arquivo representa uma palavra distinta.
- Caso o arquivo nÃ£o exista ou esteja vazio, o jogo nÃ£o deve iniciar e uma mensagem de erro deve ser exibida.

### Requisito 1.2: SeleÃ§Ã£o da Palavra Secreta
- O jogo deve escolher aleatoriamente uma palavra da lista carregada.
- A palavra escolhida deve ser convertida para letras minÃºsculas.

### Requisito 1.3: MecÃ¢nica de Jogo
- A cada interaÃ§Ã£o do jogo a console deve ser limpa para gerar a sensaÃ§Ã£o de tela atualizada.
- O jogador inicia com **6 vidas**.
- A cada rodada, o jogador deve digitar **uma letra**.
- Letras repetidas nÃ£o devem ser aceitas novamente. Caso isto ocorra o jogador deve ser alertado e solicitado a digitar outra letra.
- Se a letra estiver na palavra, ela Ã© exibida nas posiÃ§Ãµes corretas conforme a palavra.
- Se a letra nÃ£o estiver na palavra, o jogador perde uma vida, e um novo desenho da forca deve ser exibido.

### Requisito 1.4: Fim de Jogo
- O jogo termina quando:
  - O jogador acerta todas as letras da palavra (**vitÃ³ria**).
  - O jogador perde todas as vidas (**derrota**).
- Ao final do jogo, deve ser exibida:
  - A palavra secreta.
  - Uma mensagem de vitÃ³ria ou derrota e o estado de como estava a forca.

### Requisito 1.5: ExibiÃ§Ã£o da Forca
- A cada erro, uma nova parte da forca deve ser exibida, atÃ© completar o desenho ao fim das 6 tentativas.
- A forca deve ser desenhada utilizando caracteres de texto para simular ao conceito de **Art ASCII**.

### Requisito 1.6: Interface de Texto
- O jogo deve funcionar em um terminal/console.
- A tela deve ser limpa a cada nova jogada para atualizar a exibiÃ§Ã£o do estado atual do jogo.

### Requisito 1.7: InformaÃ§Ãµes Visuais Durante o Jogo
Durante o jogo, deve ser exibido:
- Quantidade de vidas restantes.
- Letras jÃ¡ tentadas.
- A palavra com letras adivinhadas no formato `__X__` onde **X** sÃ£o as letras jÃ¡ adivinhadas e `_____` para as letras ainda ocultas.
- A forca correspondente ao nÃºmero de erros.

---

## ðŸŽ­ Desenho da Forca (ASCII)

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

# ðŸ›¡ï¸ Requisitos NÃ£o Funcionais

## 2.1. Estrutura de Arquivo
- O arquivo **palavras.txt** deve estar localizado em um caminho acessÃ­vel e correto, definido no cÃ³digo.
- Exemplo de caminho absoluto:
  - `C:\jogoForca\src\palavras.txt`

## 2.3. Usabilidade
- O jogo deve ser jogÃ¡vel apenas com entrada de texto via teclado.
- NÃ£o deve permitir entrada invÃ¡lida (como strings ou nÃºmeros em vez de uma Ãºnica letra).

---

# ðŸ–¥ï¸ Exemplos de Telas

- InÃ­cio do Jogo
![OnlineGDB - exemplo](../images/1_inicio_jogo.png)

- Algumas Letras jÃ¡ tentadas
![OnlineGDB - exemplo](../images/2_tentadas.png)

- Algumas Letras Acertadas
![OnlineGDB - exemplo](../images/3_acertadas.png)

- Letra Repetida
![OnlineGDB - exemplo](../images/4_repetida.png)

- Jogador Perdeu
![OnlineGDB - exemplo](../images/5_perdeu.png)

- Jogador Ganhou
![OnlineGDB - exemplo](../images/6_ganhou.png)

<!-- nav_start -->
---
Anterior: [Jogo da Forca](../docs/47_Jogo_da_Forca.md) | Próximo: [Teste 1: Deve ser resolvido atÃ© 10/10/2025](../docs/49_Teste_1.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

