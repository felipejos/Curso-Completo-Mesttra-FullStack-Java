# Estruturas de Repetição Do e For

Assista os vídeos abaixo sobre as estruturas de repetição Do e For.

Laço While:  https://www.youtube.com/watch?v=VpcYTn_Kqdc

Laço For:  https://www.youtube.com/watch?v=HrfWrbmFUKQ

---

## Complemento: entendendo Do/While e For de forma clara e prática

### 1) Onde cada laço se encaixa melhor (ideia principal)
As estruturas de repetição existem para **executar um bloco várias vezes**, mas cada uma é “mais natural” em um tipo de situação:

- **Do...while**
  - Quando você precisa **executar pelo menos uma vez** antes de verificar a condição.
  - Exemplo típico: **menu** ou **pedir entrada** e validar depois.

- **While**
  - Quando você **só quer repetir se a condição já começa verdadeira**.
  - Exemplo típico: “enquanto tiver dados”, “enquanto não acertar”, “enquanto opção != sair”.

- **For**
  - Quando você **já sabe quantas vezes** quer repetir (ou quer controlar com contador).
  - Exemplo típico: “repita 10 vezes”, “de 1 até 100”, “percorrer índice”.

---

### 2) Diferença mais importante: quando a condição é verificada

#### While (verifica antes)
- Se a condição começar falsa, **não executa nenhuma vez**.

    while (condicao) {
        // executa enquanto condicao for verdadeira
    }

#### Do...while (executa antes, verifica depois)
- **Executa pelo menos uma vez**, e só depois pergunta “repete?”.

    do {
        // executa pelo menos uma vez
    } while (condicao);

#### For (contador embutido)
- Ele é um “pacote completo” com:
  - inicialização
  - condição
  - incremento/decremento

    for (inicio; condicao; passo) {
        // repete seguindo o contador
    }

---

### 3) Exemplo mental rápido para escolher
Quando você estiver codando, pense assim:

- **“Preciso mostrar um menu e só depois checar se sai”** → `do...while`
- **“Preciso repetir enquanto X continuar verdadeiro”** → `while`
- **“Preciso repetir N vezes / tenho um contador”** → `for`

---

### 4) Exemplos simples (sem complicar)

#### Exemplo A — For: imprimir de 1 a 5
    for (int i = 1; i <= 5; i++) {
        System.out.println(i);
    }

- Começa com i = 1
- Repete enquanto i <= 5
- A cada volta faz i++

---

#### Exemplo B — While: ler opção até ser 0
    int opcao = Leitura.lerValorInteiro("Digite uma opção (0 para sair): ");

    while (opcao != 0) {
        System.out.println("Você digitou: " + opcao);
        opcao = Leitura.lerValorInteiro("Digite uma opção (0 para sair): ");
    }

- Só entra no laço se `opcao != 0` desde o início

---

#### Exemplo C — Do...while: menu sempre aparece pelo menos uma vez
    int opcao;

    do {
        System.out.println("1 - Continuar");
        System.out.println("2 - Sair");

        opcao = Leitura.lerValorInteiro("Escolha: ");

    } while (opcao != 2);

- Mesmo que a pessoa digite `2` na primeira tentativa, o menu apareceu 1 vez.

---

### 5) Erro comum (e como evitar)
**Esquecer de atualizar a variável que controla a condição** dentro do laço.

Exemplo de problema:
- Se você faz `while (opcao != 0)` mas nunca lê `opcao` de novo, vira loop infinito.

Regra prática:
- Se a condição depende de uma variável, essa variável precisa **mudar dentro do loop**.

---

<!-- nav_start -->
---
Anterior: [112 Exemplos Do While](../docs/112_Exemplos_Do_While.md) | Proximo: [114 Iteracao Caracteres](../docs/114_Iteracao_Caracteres.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
