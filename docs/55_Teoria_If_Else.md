# Teoria If Else

## Estruturas de Decisão em Programação

### O que são Estruturas de Decisão?

Em qualquer sistema — seja um site, aplicativo, jogo ou software corporativo — as decisões fazem parte do comportamento esperado. Por exemplo:

- Um jogo precisa verificar se o jogador perdeu ou venceu.
- Um site precisa saber se o usuário está logado para liberar o acesso.
- Um caixa eletrônico precisa saber se há saldo suficiente antes de permitir um saque.

Essas decisões são feitas com **estruturas de decisão**, que são instruções que dizem ao computador:

> “Se tal condição for verdadeira, então faça isso; senão, faça outra coisa.”

---

### Como funcionam?

O computador executa as instruções de cima para baixo, linha por linha.  
Quando ele encontra uma estrutura de decisão, ele avalia uma condição (por exemplo: `idade > 18`). Essa condição só tem dois resultados possíveis:

- ✅ **Verdadeiro (true):** a condição é satisfeita e o bloco de código associado é executado.
- ❌ **Falso (false):** a condição não é satisfeita e o programa pode seguir outro caminho (caso exista um `else`, por exemplo).

---

## ✅ Principais Estruturas de Decisão em Java

### 1) `if` (se)

A estrutura mais básica.  
Ela executa um bloco de código **somente se a condição for verdadeira**.

**Exemplo:**

    int idade = 20;

    if (idade >= 18) {
        System.out.println("Você é maior de idade.");
    }

**Explicação:**
- A condição `idade >= 18` é avaliada.
- Como a idade é 20, o resultado é **verdadeiro**.
- O programa executa o código dentro do bloco `{}`.

---

### 2) `if` + `else`

Permite dois caminhos:  
- um se a condição for verdadeira  
- outro se for falsa

**Exemplo:**

    int idade = 16;

    if (idade >= 18) {
        System.out.println("Pode entrar na festa.");
    } else {
        System.out.println("Você ainda é menor de idade.");
    }

**Explicação:**
- Se a idade for maior ou igual a 18 → entra na festa.
- Se não for → exibe outra mensagem.

---

### 3) `if` + `else if` + `else`

Quando você precisa verificar **várias condições diferentes**.

**Exemplo:**

    int nota = 65;

    if (nota >= 90) {
        System.out.println("Nota A");
    } else if (nota >= 70) {
        System.out.println("Nota B");
    } else if (nota >= 60) {
        System.out.println("Nota C");
    } else {
        System.out.println("Reprovado");
    }

**Como funciona:**
- O Java verifica as condições **em ordem**, de cima para baixo.
- Assim que encontra a **primeira condição verdadeira**, ele executa aquele bloco e ignora o restante.

---

## ⚠️ Dicas e Cuidados Importantes

### 1) Comparação de Strings

Para comparar textos em Java, **não use `==`**.  
Isso compara endereços de memória, e não o conteúdo.

✅ Use o método `.equals()`:

    String nome = "João";

    if (nome.equals("João")) {
        System.out.println("Bem-vindo, João!");
    }

---

### 2) Sempre use chaves `{}` para blocos

Mesmo que seja só uma linha, usar `{}`:
- evita erros,
- melhora a legibilidade,
- deixa o código mais seguro.

✅ Boa prática:

    if (x > 10) {
        System.out.println("Maior que 10");
    }

---

### 3) Cuidado com a ordem no `else if`

O Java para de avaliar os blocos assim que encontra o primeiro `true`.  
Se você colocar uma condição muito genérica no topo, as outras nunca serão verificadas.

❌ Ordem errada:

    if (nota >= 50) {
        System.out.println("Passou");
    } else if (nota >= 70) {
        // Nunca será executado, pois 70 também é maior que 50
        System.out.println("Nota B");
    }
