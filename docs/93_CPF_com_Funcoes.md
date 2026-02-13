# ✅ Código Validação CPF com Funções

Abaixo temos o código de validação do CPF

---

## 🧠 Código (Java)

    import java.util.Scanner;

    public class App {

        public static void main(String[] args) {

            String cpf;
            int numero1, numero2, numero3, numero4, numero5, numero6, numero7, numero8, numero9;
            int somaPrimeiroDigitoVerificador, somaSegundoDigitoVerificador;
            int primeiroDigitoVerificador, segundoDigitoVerificador;

            Scanner teclado = new Scanner(System.in);

            System.out.print("Digite o seu cpf: ");
            cpf = teclado.nextLine();

            cpf = removerFormatacaoCPF(cpf);

            numero1 = obterNumeroPosicao(cpf, 0);
            numero2 = obterNumeroPosicao(cpf, 1);
            numero3 = obterNumeroPosicao(cpf, 2);
            numero4 = obterNumeroPosicao(cpf, 3);
            numero5 = obterNumeroPosicao(cpf, 4);
            numero6 = obterNumeroPosicao(cpf, 5);
            numero7 = obterNumeroPosicao(cpf, 6);
            numero8 = obterNumeroPosicao(cpf, 7);
            numero9 = obterNumeroPosicao(cpf, 8);

            somaPrimeiroDigitoVerificador = (numero1 * 10) + (numero2 * 9) + (numero3 * 8) + (numero4 * 7) + (numero5 * 6) + (numero6 * 5) + (numero7 * 4) + (numero8 * 3) + (numero9 * 2);

            primeiroDigitoVerificador = calcularDigitoVerificador(somaPrimeiroDigitoVerificador);

            somaSegundoDigitoVerificador = (numero1 * 11) + (numero2 * 10) + (numero3 * 9) + (numero4 * 8) + (numero5 * 7) + (numero6 * 6) + (numero7 * 5) + (numero8 * 4) + (numero9 * 3) + (primeiroDigitoVerificador * 2);

            segundoDigitoVerificador = calcularDigitoVerificador(somaSegundoDigitoVerificador);

            switch (cpf) {
                case "00000000000":
                case "11111111111":
                case "22222222222":
                case "33333333333":
                case "44444444444":
                case "55555555555":
                case "66666666666":
                case "77777777777":
                case "88888888888":
                case "99999999999":
                    System.out.print("CPF Inválido");
                    break;
                default:

                    if (obterNumeroPosicao(cpf, 9) == primeiroDigitoVerificador && obterNumeroPosicao(cpf, 10) == segundoDigitoVerificador) {
                        System.out.print("CPF Válido");
                    } else {
                        System.out.print("CPF Inválido");
                    }

                    break;
            }

            teclado.close();

        }

        static int calcularDigitoVerificador(int soma) {
            int resto = soma % 11;
            int dv;

            if (resto < 2) {
                dv = 0;
            } else {
                dv = 11 - resto;
            }

            return dv;
        }

        static int obterNumeroPosicao(String str, int posicao) {
            // quando e realizado uma subtracao entre dois chars
            // ocorre a subtracao dos respectos codigos ascii.
            // quando subrairmos - '0' teremos a diferente entre o
            // numero e o 0
            return (str.charAt(posicao) - '0');
        }

        static String removerFormatacaoCPF(String cpf) {
            cpf = cpf.replace(".", "");
            cpf = cpf.replace("-", "");

            return cpf;
        }

    }

<!-- nav_start -->
---
Anterior: [92 Lista Exercicios 07](../docs/92_Lista_Exercicios_07.md) | Proximo: [94 Resposta Lista Exercicios 07](../docs/94_Resposta_Lista_Exercicios_07.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
