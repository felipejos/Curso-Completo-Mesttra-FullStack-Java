# Indentação

---

## O que é Indentação?

Indentação é o processo de usar espaços ou tabulações para alinhar o código de forma que ele fique visualmente organizado. No código, isso geralmente significa adicionar espaços ou tabulações antes de linhas de código para mostrar que elas estão dentro de blocos ou seções diferentes.

---

## Por que a Indentação é Importante?

### Clareza e Legibilidade

- **Facilita a Leitura:** Código bem indentado é mais fácil de ler e entender. Se você usa indentação consistente, fica claro qual código pertence a qual bloco ou estrutura. Por exemplo, um bloco de código dentro de uma função ou um loop está claramente separado do restante do código.
- **Ajuda na Estrutura:** A indentação ajuda a visualizar a estrutura do programa, mostrando claramente quais comandos estão dentro de quais blocos de código.

### Evita Erros

- **Organização:** Se o código não estiver bem indentado, pode ser difícil ver onde começa e termina um bloco de código, como um `if` ou um `for`. Isso pode levar a erros, como colocar comandos no lugar errado.
- **Facilita a Identificação de Problemas:** Com uma boa indentação, você pode identificar mais facilmente onde algo pode estar errado, como uma chave (`{`) que está faltando ou sobrando.

### Padrão de Código

- **Consistência:** Usar um padrão de indentação ajuda a manter o código consistente, especialmente quando várias pessoas estão trabalhando no mesmo projeto. Isso facilita a colaboração e revisão de código.

---

## Como Indentar o Código

Aqui está um exemplo básico de código Java para mostrar a importância da indentação:

### Sem Indentação

    public class Main{
    public static void main(String[] args) {
    String nome;
    int idade;
    float peso;

    nome = "Rogério";
    int = 42;
    peso = 88.5f;
    }

### Com Indentação

    public class Main{
        public static void main(String[] args) {
             String nome;
             int idade;
             float peso;

             nome = "Rogério";
             int = 42;
             peso = 88.5f;
        }
    }

---

## Regras Básicas de Indentação
- **Consistência:** Use o mesmo padrão de indentação. Sempre utilize **1 TAB** para indentar o seu código.
- **Blocos de Código:** Sempre que você abrir um bloco de código com `{`, coloque o próximo nível de código dentro desse bloco com uma indentação.
- **Fechamento de Blocos:** Quando você fechar um bloco de código com `}`, alinhe com o nível anterior.

---

## Conclusão

A indentação é uma prática essencial para escrever código claro e organizado. Ela ajuda a garantir que seu código seja legível e compreensível, o que é fundamental para evitar erros e colaborar com outras pessoas. Boa indentação é uma habilidade básica, mas muito importante, para qualquer programador!

---

# Complemento da Lição

## 1) Uma forma simples de “enxergar” blocos no Java
No Java, chaves definem blocos:

- `{` abre um bloco (entra um nível)
- `}` fecha um bloco (volta um nível)

A indentação não muda a execução do Java, mas deixa **óbvio** onde começa e termina cada bloco.

---

## 2) Detalhe importante no exemplo (para você não copiar o erro)
No trecho:

    int = 42;

isso não compila, porque `int` é o **tipo**, não o nome da variável.  
A ideia do exemplo é mostrar estrutura/indentação, mas quando você for escrever de verdade, precisa atribuir para a variável (ex.: `idade`).

---

## 3) Exercício rápido (fixação)
Reescreva mentalmente (ou no seu editor) este fluxo com indentação correta:

- ler nome
- se nome estiver vazio, imprimir “Nome obrigatório”
- senão, imprimir “Olá, <nome>”

---

## 4) Pergunta única (para checar se fixou)
Quando você vê um `}` no código, você deve **aumentar** ou **diminuir** um nível de indentação?

---

<!-- nav_start -->
---
Anterior: [21 Caractere de Escape](../docs/21_Caractere_de_Escape.md) | Proximo: [23 Conceito Operadores Matematicos](../docs/23_Conceito_Operadores_Matematicos.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
