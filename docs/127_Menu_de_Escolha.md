Aplicação com Menu de Escolha


https://youtu.be/FZwm0QVFX3s

---

**Complementos (para ficar mais completo e fácil de entender)**

### 1) O que é um “menu de escolha” na prática?
Um **menu de escolha** é um padrão muito comum em programas de console onde o usuário:

- vê uma lista de opções (1, 2, 3…)
- escolhe uma opção digitando um número (ou letra)
- o programa **executa uma ação**
- e normalmente **volta pro menu** até o usuário pedir para sair

Esse tipo de aplicação treina MUITO bem:
- **entrada e saída** (Scanner / leitura)
- **estruturas de decisão** (`switch`/`if`)
- **repetição** (`do...while`, `while`, `for`)
- **validação de entrada** (evitar quebrar o programa se o usuário digitar errado)
- **organização em métodos** (procedimentos/funções)

---

### 2) Estrutura “clássica” de um menu (fluxo mental)
Um menu geralmente segue este passo a passo:

1) Exibe o menu
2) Lê a opção do usuário
3) Valida a opção (se é válida)
4) Executa a ação (`switch`)
5) Repete (até a opção “Sair”)

Por isso, **do...while** costuma ser a melhor escolha, porque:
- o menu precisa aparecer **pelo menos uma vez**
- só depois você decide se continua ou se encerra

---

### 3) Exemplo de “esqueleto” de menu (bem parecido com o que você vai ver no vídeo)
*(A ideia aqui é você entender o padrão, não decorar.)*

    int opcao;

    do {
        System.out.println("\n=== MENU ===");
        System.out.println("1 - Opção A");
        System.out.println("2 - Opção B");
        System.out.println("0 - Sair");

        System.out.print("Escolha: ");
        opcao = teclado.nextInt();

        switch (opcao) {
            case 1:
                System.out.println("Você escolheu A");
                break;
            case 2:
                System.out.println("Você escolheu B");
                break;
            case 0:
                System.out.println("Saindo...");
                break;
            default:
                System.out.println("Opção inválida!");
        }

    } while (opcao != 0);

---

### 4) Melhoria importante: separar em métodos (organização)
Um menu fica MUITO mais fácil de manter quando você separa em métodos, por exemplo:

- `exibirMenu()`
- `lerOpcao()`
- `processarOpcao(opcao)`

Isso evita:
- repetição de `System.out.println(...)`
- um `main` gigante
- bagunça na leitura do código

---

### 5) Problema clássico: “Scanner travando” na mistura de nextInt e nextLine
Se você usar:
- `nextInt()` para ler a opção  
e depois quiser ler texto com:
- `nextLine()`

Pode acontecer do `nextLine()` “pular” porque o ENTER fica no buffer.

Solução simples:
- após `nextInt()` faça um `nextLine()` extra para limpar o buffer
ou use sempre `nextLine()` e converta para int.

---

### 6) Validação de entrada (o que deixa o menu profissional)
Menus reais tratam estas situações:
- usuário digitou letra em vez de número
- digitou número fora das opções
- digitou vazio (quando usa String)

A ideia é: o programa **não quebra**, ele só pede de novo.

---

### 7) Checklist do que você deve observar no vídeo
Enquanto assiste, tenta identificar:

- Onde o menu é exibido?
- Qual estrutura decide a opção? (`switch` ou `if`)
- Existe repetição pra voltar ao menu?
- Tem opção de saída?
- O programa trata entrada inválida?
- O código está separado em métodos ou está tudo no `main`?

Se você conseguir responder essas perguntas, você entendeu o padrão do “Menu de Escolha”.

---

<!-- nav_start -->
---
Anterior: [Vetores bidimensionais (ou matrizes)](../docs/126_Matrizes.md) | Próximo: [Desafio: Jogo da Forca](../docs/128_Desafio_Forca.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

