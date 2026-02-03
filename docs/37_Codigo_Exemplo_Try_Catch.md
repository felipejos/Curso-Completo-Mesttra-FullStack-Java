# 🧪 Código de Exemplo para o Try/Catch

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
