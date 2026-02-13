# 🧪 Código de Exemplo para Try/Catch

---

## 📌 Objetivo

Analise o código abaixo, teste-o em seu computador e entenda as características de funcionamento do **Try/Catch**.

> 💡 Dica: execute o programa mais de uma vez e teste cenários diferentes:
> - Digitar letras no lugar de números (ex: `abc`)
> - Digitar `0` como segundo valor (divisão por zero)
> - Digitar valores válidos (ex: 10 e 2)

---

## ✅ Código de exemplo

    // importa a classe scanner para lidar com a entrada de dados
    import java.util.Scanner;
    // importa a classe InputMismatchException para tratar erros de entrada de dados
    import java.util.InputMismatchException;
    // importa a classe ArithmeticException para tratar erros aritméticos
    import java.lang.ArithmeticException;

    public class App{
        public static void main(String[] args) throws Exception {
            int valor1, valor2;
            Scanner teclado = new Scanner(System.in);

            try {
                System.out.print("Digite o valor 1: ");
                valor1 = teclado.nextInt();
                teclado.close();

                System.out.print("Digite o valor 2: ");
                valor2 = teclado.nextInt();

                // Isso gera uma exceção quando o valor2 é zero
                float resultado = (valor1 / valor2);

                // imprime o resultado com 2 casas decimais
                System.out.printf("O resultado é: %.2f", resultado);
            } catch (InputMismatchException e) {
                // trata o erro quando o usuário digita um valor que não é um número inteiro
                System.out.println("Erro: você deve digitar um número inteiro.");
            } catch (ArithmeticException e) {
                // trata o erro quando o usuário tenta dividir por zero
                System.out.println("Erro: não é possível dividir por zero.");
            } catch (Exception e) {
                // trata qualquer outro erro que possa ocorrer que não foi previsto
                System.out.println("\nErro: Desconhecido.");
                // imprimindo os detalhes do erro para ajudar na identificação da exceção
                e.printStackTrace();
            }

        }
    }

---

# Complemento da Lição

## 1) O que observar (passo a passo)
1. **Entrada de dados**
   - Quando você digita `abc` no lugar de número, o `Scanner` não consegue converter → cai no `catch (InputMismatchException e)`.

2. **Divisão por zero**
   - Quando `valor2` é `0`, ocorre erro aritmético → cai no `catch (ArithmeticException e)`.

3. **Caminho feliz**
   - Quando `valor1` e `valor2` são válidos e `valor2 != 0`, o programa calcula e imprime o resultado.

---

## 2) Dois detalhes importantes para entender (erros comuns em console)
- **Fechar o Scanner cedo demais**
  - No código, existe `teclado.close();` logo após ler o `valor1`.
  - Isso costuma causar problema ao tentar ler o `valor2`, porque o `Scanner` pode encerrar a entrada (`System.in`) antes da segunda leitura.

- **Divisão inteira sem querer**
  - `valor1` e `valor2` são `int`.
  - Mesmo que você guarde em `float`, a expressão `(valor1 / valor2)` pode fazer **divisão inteira** primeiro (ex.: `10 / 3` vira `3`), e só depois vira `3.0`.

---

## 3) Exercício prático (fixação)
Execute 3 vezes e anote:
1. Entrada: `abc` e depois qualquer coisa
2. Entrada: `10` e `0`
3. Entrada: `10` e `2`

Para cada execução, escreva:
- Qual `catch` foi acionado (ou se nenhum foi)
- Qual mensagem apareceu no console

---

## 4) Pergunta única (pra fixar)
Quando você digita `abc` no lugar de um número, qual `catch` deve ser executado?

---

<!-- nav_start -->
---
Anterior: [36 Compilacao Interpretacao Hibrido](../docs/36_Compilacao_Interpretacao_Hibrido.md) | Proximo: [38 Sugestao Exercicio](../docs/38_Sugestao_Exercicio.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
