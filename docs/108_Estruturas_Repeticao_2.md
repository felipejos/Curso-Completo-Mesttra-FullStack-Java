# Estruturas de Repetição


O que são estruturas de repetição?
Estruturas de repetição, também chamadas de loops, são blocos de comandos fundamentais na programação que permitem executar um mesmo conjunto de instruções várias vezes, sem que seja necessário escrever esse conjunto repetidamente no código.



Imagine que você precisa fazer uma tarefa repetitiva, como:

contar de 1 até 100,

verificar cada item de uma lista,

enviar uma mensagem para vários usuários,

ou somar vários números.

Se você tentasse fazer isso escrevendo manualmente cada passo, o código ficaria enorme, cansativo e difícil de manter.
Estruturas de repetição existem justamente para resolver esse problema.

Elas permitem dizer ao computador:

“Repita estas instruções até que uma certa condição aconteça.”

Em outras palavras, você escreve o bloco de ações uma única vez, e a estrutura de repetição se encarrega de executá-lo quantas vezes for necessário.

Para que elas são usadas?
1. Automatizar tarefas repetitivas
Evitar a repetição manual de código é o uso mais óbvio.
Por exemplo, se você quer imprimir “Olá!” dez vezes, não precisa escrever dez comandos — um loop faz isso automaticamente.

2. Processar coleções de dados
Quando trabalhamos com listas, tabelas, arquivos, registros ou qualquer conjunto de informações, normalmente precisamos analisar item por item.
Estruturas de repetição percorrem cada elemento de maneira organizada.

3. Executar algo até que uma condição seja satisfeita
Às vezes não sabemos quantas vezes uma ação precisa acontecer.
Por exemplo:

continuar pedindo ao usuário uma senha até que ele digite a correta,

continuar lendo dados enquanto houver dados disponíveis,

continuar tentando conectar à internet até conseguir.

O loop continua rodando enquanto a condição definida for verdadeira.

4. Diminuir erros e facilitar manutenção
Menos código duplicado significa:

menos chance de erro humano,

menos partes para corrigir caso algo mude.

5. Tornar o programa mais eficiente
O computador consegue repetir instruções muito mais rapidamente do que qualquer pessoa escreveria manualmente.
Loops permitem aproveitar totalmente a velocidade da máquina.

Como pensar em uma repetição?
Na programação, sempre que você percebe que:

“Eu preciso fazer a mesma ação várias vezes, talvez mudando só algum detalhe a cada repetição”

…é um sinal de que você deve usar uma estrutura de repetição.

Uma repetição geralmente envolve três elementos básicos:

Um ponto de partida — onde a repetição começa.

Uma condição — o que define se o loop continua ou para.

Um bloco de ações — o que acontece a cada volta.

Resumo simples
Estruturas de repetição são mecanismos que permitem executar um mesmo conjunto de instruções várias vezes.

Elas servem para automatizar tarefas repetitivas, percorrer listas, esperar condições serem atendidas e evitar código duplicado.

A ideia central é: escreva uma vez, execute muitas.

---

## Complemento: deixando o conceito mais claro (com mentalidade de iniciante)

### A ideia-chave do loop (do jeito mais simples)
Um loop é como um “voltar e fazer de novo”, controlado por uma regra.

Você diz ao programa:
- **comece aqui**
- **repita esse bloco**
- **enquanto** (ou **até**) uma condição acontecer
- **pare** quando a condição mandar parar

Se você esquecer a parte do “pare”, o loop vira um **loop infinito** (fica rodando sem fim).

---

## Tipos de repetição mais comuns em Java (visão geral)

### 1) `for` (quando você sabe quantas vezes vai repetir)
Use quando já tem uma quantidade definida.

Exemplo mental:
- “Repita 10 vezes”
- “Conte de 1 até 100”
- “Percorra do índice 0 até o índice 9”

Estrutura:
- **inicialização** (onde começa)
- **condição** (quando continua)
- **incremento** (como avança)

Exemplo:
    for (int i = 1; i <= 10; i++) {
        System.out.println("Olá!");
    }

Leitura humana:
- começa com `i = 1`
- enquanto `i <= 10`, executa
- no fim de cada volta, faz `i++` (soma 1)

---

### 2) `while` (quando você não sabe exatamente quantas vezes)
Use quando a repetição depende de uma condição.

Exemplo mental:
- “Enquanto a senha estiver errada, peça de novo”
- “Enquanto o usuário não digitar 0, continue somando”

Exemplo:
    int numero = 1;

    while (numero != 0) {
        System.out.print("Digite um número (0 para sair): ");
        numero = teclado.nextInt();
    }

Leitura humana:
- enquanto `numero` for diferente de 0, continua rodando
- quando o usuário digitar 0, a condição fica falsa e o loop para

---

### 3) `do-while` (quando você precisa executar pelo menos 1 vez)
A diferença é simples:
- no `while`, ele **checa antes**
- no `do-while`, ele **executa primeiro e checa depois**

Exemplo mental:
- “Mostre o menu e só depois veja se deve repetir”
- “Peça a entrada ao menos uma vez”

Exemplo:
    int opcao;

    do {
        System.out.println("1 - Continuar");
        System.out.println("0 - Sair");
        System.out.print("Escolha: ");
        opcao = teclado.nextInt();
    } while (opcao != 0);

---

## 3 coisas que TODO loop precisa (pra você nunca se perder)

### 1) Controle (variável de controle)
É a variável que muda e controla as repetições.
Ex: `i`, `opcao`, `tentativas`, `numero`.

### 2) Condição de parada
É a regra que decide quando acaba.
Ex: `i <= 10`, `opcao != 0`, `senhaErrada == true`.

### 3) Atualização (passo)
É o que faz o loop “andar” em direção ao fim.
Ex: `i++`, `tentativas++`, ler um novo valor do usuário.

Se você esquecer a atualização, você pode travar em loop infinito.

---

## Exemplos bem práticos (para conectar com o mundo real)

### Contar de 1 a 5
    for (int i = 1; i <= 5; i++) {
        System.out.println(i);
    }

### Somar números até o usuário digitar 0
    int n;
    int soma = 0;

    do {
        System.out.print("Digite um número (0 para sair): ");
        n = teclado.nextInt();
        soma += n;
    } while (n != 0);

    System.out.println("Soma total: " + soma);

### Pedir senha até acertar
    String senha = "";
    String senhaCorreta = "1234";

    while (!senha.equals(senhaCorreta)) {
        System.out.print("Digite a senha: ");
        senha = teclado.nextLine();
    }

    System.out.println("Acesso liberado!");

---

## Quando escolher cada um? (regra simples)
- **`for`** → quando você sabe o número de repetições
- **`while`** → quando depende de condição (não sabe quantas vezes)
- **`do-while`** → quando precisa executar pelo menos uma vez

---

## Erros comuns (pra você evitar desde já)
- **Loop infinito**: esqueceu de atualizar a variável de controle.
- **Condição errada**: usou `<=` quando era `<` (ou vice-versa).
- **Comparar String com `==`**: em Java use `equals()`.

---

<!-- nav_start -->
---
Anterior: [107 Lista 10](../docs/107_Lista_10.md) | Proximo: [109 Analogia Repeticao](../docs/109_Analogia_Repeticao.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
