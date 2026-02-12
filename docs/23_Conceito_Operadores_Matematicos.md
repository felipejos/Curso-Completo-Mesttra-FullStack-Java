# Conceito: Operadores Matemáticos

---

## Conceito: Operadores Matemáticos

Nas linguagens de programação quando desejamos realizar operações matemáticos utilizamos os operadores matemáticos. Em Java, os operadores aritméticos são basicamente os mesmos utilizados em outras linguagens de programação. Aqui estão os principais operadores aritméticos e o que eles fazem:

---

## Adição (`+`)

**Uso:** `a + b`  
**Descrição:** Soma os valores das variáveis `a` e `b`. Se `a` e `b` forem números, o resultado será a soma desses números. Se forem strings, o operador realiza a concatenação das strings.

    public class Main{
        public static void main(String[] args) {
            int soma;
            int a, b;

            soma = (5 + 3);
            System.out.println("Soma: " + soma);  //Soma: 8

            a = 4;
            b = 6;
            soma = (a + b);
            System.out.println("Soma: " + soma);  //Soma: 10

            //a variavel concatenacao contera o valor
            String concatenacao = "Olá, " + "Mundo!";
            System.out.println("Concatenação: " + concatenacao);  //Concatenação: "Olá, Mundo!"
        }
    }

---

## Subtração (`-`)

**Uso:** `a - b`  
**Descrição:** Subtrai o valor de `b` do valor de `a`. O resultado é a diferença entre `a` e `b`.

    public class Main{
        public static void main(String[] args) {
            int subtracao;
            int a, b;

            subtracao = (10 - 4);
            System.out.println("Subtracao: " + subtracao);   //Subtracao: 6

            a = 17;
            b = 10;
            subtracao = a - b;
            System.out.println("Subtracao: " + subtracao);   //Subtracao: 7
        }
    }

---

## Multiplicação (`*`)

**Uso:** `a * b`  
**Descrição:** Multiplica os valores de `a` e `b`. O resultado é o produto desses valores.

    public class Main{
        public static void main(String[] args) {
            int produto;
            int a, b;

            produto = (7 * 6);
            System.out.println("Produto: " + produto);      //Produto: 42

            a = 4;
            b = 3;
            produto = (a * b);
            System.out.println("Produto: " + produto);      //Produto: 12
        }
    }

---

## Divisão (`/`)

**Uso:** `a / b`  
**Descrição:** Divide o valor de `a` pelo valor de `b`. O resultado é o quociente da divisão. Para inteiros, a divisão descarta a parte decimal (ou seja, faz uma divisão inteira). Para números de ponto flutuante (`float` ou `double`), a parte decimal é preservada.

No caso de uma divisão entre dois números inteiros, basta realizar a conversão de tipos utilizando a técnica de *casting* adicionando a palavra `(float)` através de uma das duas variáveis inteiras, o que irá forçar o Java a considerar o resultado no formato fracionário.

    public class Main{
        public static void main(String[] args) {
            float divisao;
            int a, b;

            divisao = (10 / 6);
            System.out.println("Divisão: " + divisao); //Divisão: 1

            a = 13;
            b = 4;
            divisao = (a / b);
            System.out.println("Divisão: " + divisao); //Divisão: 3

            a = 6;
            b = 5;
            divisao = ((float) a / b);
            System.out.println("Divisão: " + divisao); //Divisão: 1.2
        }
    }

---

## Módulo (`%`)

**Uso:** `a % b`  
**Descrição:** Calcula o resto da divisão de `a` por `b`. É útil para encontrar se um número é divisível por outro ou para realizar operações cíclicas.

    public class Main{
        public static void main(String[] args) {
            float resto;
            int a, b;

            resto = (10 % 6);
            System.out.println("Resto: " + resto); //Resto: 4

            a = 7;
            b = 5;
            resto = (a % b);
            System.out.println("Resto: " + resto); //Resto: 2
        }
    }

---

# Complemento da Lição

## 1) Regra prática para não errar divisão
Se `a` e `b` forem `int`, então `a / b` vira **divisão inteira** (corta a parte decimal).

Para manter decimal:
- transforme pelo menos um lado em `float` ou `double`

Exemplos (para você comparar mentalmente):
    System.out.println(10 / 6);
    System.out.println((float) 10 / 6);

---

## 2) Onde o módulo (`%`) aparece em programas reais
- saber se é **par/ímpar**: `n % 2`
- rodízio / ciclos (ex.: “a cada 3 itens”): `contador % 3`
- validar múltiplos (ex.: múltiplo de 5): `n % 5 == 0`

---

## 3) Exercícios rápidos (fixação)

1) Sem executar: qual saída você espera?
    System.out.println(9 / 2);
    System.out.println(9 % 2);

2) Faça um programa que leia um número e diga:
- “Par” se `n % 2 == 0`
- “Ímpar” caso contrário

3) Faça um programa que calcule:
- média de 3 notas (use `double`)

---

## 4) Pergunta única (para checar que fixou)
Qual operador você usa para descobrir o **resto** de uma divisão?

---

<!-- nav_start -->
---
Anterior: [IndentaÃ§Ã£o](../docs/22_Indentacao.md) | Próximo: [VÃ­deo: Operadores MatemÃ¡ticos](../docs/24_Video_Operadores_Matematicos.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

