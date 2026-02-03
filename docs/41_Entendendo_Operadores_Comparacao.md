# 🔎 Entendendo os Operadores de Comparação

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
