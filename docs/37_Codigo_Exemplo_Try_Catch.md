# ðŸ§ª CÃ³digo de Exemplo para o Try/Catch

Analise o cÃ³digo abaixo, teste-o em seu computador e entenda as caracterÃ­sticas de funcionamento do **Try/Catch**.

> ðŸ’¡ Dica: execute o programa mais de uma vez e teste cenÃ¡rios diferentes:
> - Digitar letras no lugar de nÃºmeros (ex: `abc`)
> - Digitar `0` como segundo valor (divisÃ£o por zero)
> - Digitar valores vÃ¡lidos (ex: 10 e 2)

---

## âœ… CÃ³digo de exemplo

    // importa a classe scanner para lidar com a entrada de dados
    import java.util.Scanner; 
    // importa a classe InputMismatchException para tratar erros de entrada de dados
    import java.util.InputMismatchException; 
    // importa a classe ArithmeticException para tratar erros aritmÃ©ticos
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

                // Isso gera uma exceÃ§Ã£o quando o valor2 Ã© zero
                float resultado = (valor1 / valor2); 

                // imprime o resultado com 2 casas decimais
                System.out.printf("O resultado Ã©: %.2f", resultado);
            } catch (InputMismatchException e) {
                // trata o erro quando o usuÃ¡rio digita um valor que nÃ£o Ã© um nÃºmero inteiro
                System.out.println("Erro: vocÃª deve digitar um nÃºmero inteiro.");
            } catch (ArithmeticException e) {
                // trata o erro quando o usuÃ¡rio tenta dividir por zero
                System.out.println("Erro: nÃ£o Ã© possÃ­vel dividir por zero.");
            } catch (Exception e) {
                // trata qualquer outro erro que possa ocorrer que nÃ£o foi previsto
                System.out.println("\nErro: Desconhecido.");
                // imprimindo os detalhes do erro para ajudar na identificaÃ§Ã£o da exceÃ§Ã£o
                e.printStackTrace();
            }          

        }
    }

<!-- nav_start -->
---
Anterior: [CompilaÃ§Ã£o, InterpretaÃ§Ã£o e HÃ­brido](../docs/36_Compilacao_Interpretacao_Hibrido.md) | Próximo: [SugestÃ£o ExercÃ­cio](../docs/38_Sugestao_Exercicio.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

