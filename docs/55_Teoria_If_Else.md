# Teoria If Else

## Estruturas de DecisÃ£o em ProgramaÃ§Ã£o

### O que sÃ£o Estruturas de DecisÃ£o?

Em qualquer sistema â€” seja um site, aplicativo, jogo ou software corporativo â€” as decisÃµes fazem parte do comportamento esperado. Por exemplo:

- Um jogo precisa verificar se o jogador perdeu ou venceu.
- Um site precisa saber se o usuÃ¡rio estÃ¡ logado para liberar o acesso.
- Um caixa eletrÃ´nico precisa saber se hÃ¡ saldo suficiente antes de permitir um saque.

Essas decisÃµes sÃ£o feitas com **estruturas de decisÃ£o**, que sÃ£o instruÃ§Ãµes que dizem ao computador:

> â€œSe tal condiÃ§Ã£o for verdadeira, entÃ£o faÃ§a isso; senÃ£o, faÃ§a outra coisa.â€

---

### Como funcionam?

O computador executa as instruÃ§Ãµes de cima para baixo, linha por linha.  
Quando ele encontra uma estrutura de decisÃ£o, ele avalia uma condiÃ§Ã£o (por exemplo: `idade > 18`). Essa condiÃ§Ã£o sÃ³ tem dois resultados possÃ­veis:

- âœ… **Verdadeiro (true):** a condiÃ§Ã£o Ã© satisfeita e o bloco de cÃ³digo associado Ã© executado.
- âŒ **Falso (false):** a condiÃ§Ã£o nÃ£o Ã© satisfeita e o programa pode seguir outro caminho (caso exista um `else`, por exemplo).

---

## âœ… Principais Estruturas de DecisÃ£o em Java

### 1) `if` (se)

A estrutura mais bÃ¡sica.  
Ela executa um bloco de cÃ³digo **somente se a condiÃ§Ã£o for verdadeira**.

**Exemplo:**

    int idade = 20;

    if (idade >= 18) {
        System.out.println("VocÃª Ã© maior de idade.");
    }

**ExplicaÃ§Ã£o:**
- A condiÃ§Ã£o `idade >= 18` Ã© avaliada.
- Como a idade Ã© 20, o resultado Ã© **verdadeiro**.
- O programa executa o cÃ³digo dentro do bloco `{}`.

---

### 2) `if` + `else`

Permite dois caminhos:  
- um se a condiÃ§Ã£o for verdadeira  
- outro se for falsa

**Exemplo:**

    int idade = 16;

    if (idade >= 18) {
        System.out.println("Pode entrar na festa.");
    } else {
        System.out.println("VocÃª ainda Ã© menor de idade.");
    }

**ExplicaÃ§Ã£o:**
- Se a idade for maior ou igual a 18 â†’ entra na festa.
- Se nÃ£o for â†’ exibe outra mensagem.

---

### 3) `if` + `else if` + `else`

Quando vocÃª precisa verificar **vÃ¡rias condiÃ§Ãµes diferentes**.

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
- O Java verifica as condiÃ§Ãµes **em ordem**, de cima para baixo.
- Assim que encontra a **primeira condiÃ§Ã£o verdadeira**, ele executa aquele bloco e ignora o restante.

---

## âš ï¸ Dicas e Cuidados Importantes

### 1) ComparaÃ§Ã£o de Strings

Para comparar textos em Java, **nÃ£o use `==`**.  
Isso compara endereÃ§os de memÃ³ria, e nÃ£o o conteÃºdo.

âœ… Use o mÃ©todo `.equals()`:

    String nome = "JoÃ£o";

    if (nome.equals("JoÃ£o")) {
        System.out.println("Bem-vindo, JoÃ£o!");
    }

---

### 2) Sempre use chaves `{}` para blocos

Mesmo que seja sÃ³ uma linha, usar `{}`:
- evita erros,
- melhora a legibilidade,
- deixa o cÃ³digo mais seguro.

âœ… Boa prÃ¡tica:

    if (x > 10) {
        System.out.println("Maior que 10");
    }

---

### 3) Cuidado com a ordem no `else if`

O Java para de avaliar os blocos assim que encontra o primeiro `true`.  
Se vocÃª colocar uma condiÃ§Ã£o muito genÃ©rica no topo, as outras nunca serÃ£o verificadas.

âŒ Ordem errada:

    if (nota >= 50) {
        System.out.println("Passou");
    } else if (nota >= 70) {
        // Nunca serÃ¡ executado, pois 70 tambÃ©m Ã© maior que 50
        System.out.println("Nota B");
    }

<!-- nav_start -->
---
Anterior: [QuestÃ£o 05](../docs/54_Questao_05.md) | Próximo: [Conceito de Estruturas de DecisÃ£o](../docs/56_Conceito_Estruturas_Decisao.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

