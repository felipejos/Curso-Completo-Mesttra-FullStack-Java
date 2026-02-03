# Conceito: Operadores MatemÃ¡ticos

Nas linguagens de programaÃ§Ã£o quando desejamos realizar operaÃ§Ãµes matemÃ¡ticos utilizamos os operadores matemÃ¡ticos. Em Java, os operadores aritmÃ©ticos sÃ£o basicamente os mesmos utilizados em outras linguagens de programaÃ§Ã£o. Aqui estÃ£o os principais operadores aritmÃ©ticos e o que eles fazem:

---

## AdiÃ§Ã£o (+)

**Uso:** `a + b`  
**DescriÃ§Ã£o:** Soma os valores das variÃ¡veis `a` e `b`. Se `a` e `b` forem nÃºmeros, o resultado serÃ¡ a soma desses nÃºmeros. Se forem strings, o operador realiza a concatenaÃ§Ã£o das strings.

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
            String concatenacao = "OlÃ¡, " + "Mundo!"; 
            System.out.println("ConcatenaÃ§Ã£o: " + concatenacao);  //ConcatenaÃ§Ã£o: "OlÃ¡, Mundo!" 
        }
    }

---

## SubtraÃ§Ã£o (-)

**Uso:** `a - b`  
**DescriÃ§Ã£o:** Subtrai o valor de `b` do valor de `a`. O resultado Ã© a diferenÃ§a entre `a` e `b`.

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

## MultiplicaÃ§Ã£o (*)

**Uso:** `a * b`  
**DescriÃ§Ã£o:** Multiplica os valores de `a` e `b`. O resultado Ã© o produto desses valores.

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

## DivisÃ£o (/)

**Uso:** `a / b`  
**DescriÃ§Ã£o:** Divide o valor de `a` pelo valor de `b`. O resultado Ã© o quociente da divisÃ£o. Para inteiros, a divisÃ£o descarta a parte decimal (ou seja, faz uma divisÃ£o inteira). Para nÃºmeros de ponto flutuante (`float` ou `double`), a parte decimal Ã© preservada.

No caso de uma divisÃ£o entre dois nÃºmeros inteiros, basta realizar a conversÃ£o de tipos utilizando a tÃ©cnica de *casting* adicionando a palavra `(float)` atravÃ©s de uma das duas variÃ¡veis inteiras, o que irÃ¡ forÃ§ar o Java a considerar o resultado no formato fracionÃ¡rio.

    public class Main{
        public static void main(String[] args) {
            float divisao;
            int a, b;

            divisao = (10 / 6); 
            System.out.println("DivisÃ£o: " + divisao); //DivisÃ£o: 1

            a = 13;
            b = 4;
            divisao = (a / b);
            System.out.println("DivisÃ£o: " + divisao); //DivisÃ£o: 3 

            a = 6;
            b = 5;
            divisao = ((float) a / b);
            System.out.println("DivisÃ£o: " + divisao); //DivisÃ£o: 1.2   
        }
    }

---

## MÃ³dulo (%)

**Uso:** `a % b`  
**DescriÃ§Ã£o:** Calcula o resto da divisÃ£o de `a` por `b`. Ã‰ Ãºtil para encontrar se um nÃºmero Ã© divisÃ­vel por outro ou para realizar operaÃ§Ãµes cÃ­clicas.

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

<!-- nav_start -->
---
Anterior: [IndentaÃ§Ã£o](../docs/22_Indentacao.md) | Próximo: [VÃ­deo: Operadores MatemÃ¡ticos](../docs/24_Video_Operadores_Matematicos.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

