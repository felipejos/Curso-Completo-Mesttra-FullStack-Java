# 🔎 Entendendo os Operadores de Comparação

## ✅ O que são operadores relacionais (ou de comparação)?
Os operadores **relacionais** (ou **de comparação**) avaliam dois operandos. Mais precisamente, eles definem se o operando à esquerda é:

- menor
- menor ou igual
- maior
- maior ou igual
- igual
- diferente

➡️ O resultado de uma comparação sempre será um **booleano**: `true` (verdadeiro) ou `false` (falso).

---

## ✅ Operadores de comparação

- `==`  
  Utilizado quando desejamos verificar se uma variável é **igual** a outra.

- `!=`  
  Utilizado quando desejamos verificar se uma variável é **diferente** de outra.

- `>`  
  Utilizado quando desejamos verificar se uma variável é **maior** que outra.

- `>=`  
  Utilizado quando desejamos verificar se uma variável é **maior ou igual** a outra.

- `<`  
  Utilizado quando desejamos verificar se uma variável é **menor** que outra.

- `<=`  
  Utilizado quando desejamos verificar se uma variável é **menor ou igual** a outra.

---

## 🧪 Exemplo em Java

    public class Main{
        public static void main(String[] args) {
            boolean resultado;
            int a;
            int b;

            a = 10;
            b = 10;

            resultado = (a > b);
            System.out.println("Resultado: " + resultado); //Resultado: false

            resultado = (a >= b);
            System.out.println("Resultado: " + resultado); //Resultado: true

            resultado = (a < b);
            System.out.println("Resultado: " + resultado); //Resultado: false

            resultado = (a <= b);
            System.out.println("Resultado: " + resultado); //Resultado: true

            resultado = (a == b);
            System.out.println("Resultado: " + resultado); //Resultado: true

            resultado = (a != b);
            System.out.println("Resultado: " + resultado); //Resultado: false

        }
    }

---

# Complemento da Lição

## 1) O que significa “operando” (bem simples)
**Operando** é cada valor que participa da comparação.

Exemplo:  
`a > b`  
- `a` é um operando  
- `b` é outro operando  
- `>` é o operador de comparação

---

## 2) Como ler comparações em voz alta (ajuda MUITO no início)
- `a > b`  → “a é maior que b?”
- `a >= b` → “a é maior ou igual a b?”
- `a == b` → “a é igual a b?”
- `a != b` → “a é diferente de b?”

Se a frase for verdadeira, o resultado é `true`. Se não for, é `false`.

---

## 3) Exemplo prático usando `if` (como isso vira decisão)
Comparação é usada para tomar decisões.

    public class Main{
        public static void main(String[] args) {
            int idade = 17;

            if (idade >= 18) {
                System.out.println("Entrada liberada");
            } else {
                System.out.println("Entrada negada");
            }
        }
    }

---

## 4) Atenção: `==` em String
Para texto (`String`), o padrão correto é usar `.equals()`.

✅ Correto:
    String s1 = "Ana";
    String s2 = "Ana";

    System.out.println(s1.equals(s2)); // true

⚠️ Evite:
    System.out.println(s1 == s2); // pode dar true/false dependendo do caso

---

## 5) Exercícios rápidos (fixação)
### Exercício 1
Crie duas variáveis `x` e `y` e mostre no console:
- `x > y`
- `x < y`
- `x == y`
- `x != y`

### Exercício 2
Leia um número inteiro e diga se ele é:
- maior que 0
- menor que 0
- igual a 0

### Exercício 3
Leia duas idades e diga qual é maior (ou se são iguais), usando `if` + comparações.

<!-- nav_start -->
---
Anterior: [OperaÃ§Ãµes de ComparaÃ§Ã£o](../docs/40_Operacoes_Comparacao.md) | Próximo: [Operadores LÃ³gico](../docs/42_Operadores_Logico.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

