# ðŸ”Ž Entendendo os Operadores de ComparaÃ§Ã£o

Os operadores **relacionais** (ou **de comparaÃ§Ã£o**) avaliam dois operandos. Mais precisamente, eles definem se o operando Ã  esquerda Ã©:

- menor
- menor ou igual
- maior
- maior ou igual
- igual
- diferente

âž¡ï¸ O resultado de uma comparaÃ§Ã£o sempre serÃ¡ um **booleano**: `true` (verdadeiro) ou `false` (falso).

---

## âœ… Operadores de comparaÃ§Ã£o

- `==`  
  Utilizado quando desejamos verificar se uma variÃ¡vel Ã© **igual** a outra.

- `!=`  
  Utilizado quando desejamos verificar se uma variÃ¡vel Ã© **diferente** de outra.

- `>`  
  Utilizado quando desejamos verificar se uma variÃ¡vel Ã© **maior** que outra.

- `>=`  
  Utilizado quando desejamos verificar se uma variÃ¡vel Ã© **maior ou igual** a outra.

- `<`  
  Utilizado quando desejamos verificar se uma variÃ¡vel Ã© **menor** que outra.

- `<=`  
  Utilizado quando desejamos verificar se uma variÃ¡vel Ã© **menor ou igual** a outra.

---

## ðŸ§ª Exemplo em Java

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

<!-- nav_start -->
---
Anterior: [OperaÃ§Ãµes de ComparaÃ§Ã£o](../docs/40_Operacoes_Comparacao.md) | Próximo: [Operadores LÃ³gico](../docs/42_Operadores_Logico.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

