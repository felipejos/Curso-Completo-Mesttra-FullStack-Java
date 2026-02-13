# Lista de Exercícios 4: Switch Case

> **Observação:** Estes exercícios **não precisam ser entregues**.  
> **Objetivo:** Converter os códigos abaixo para utilizarem **switch case** (quando for possível) e implementar **try-catch** para tratar erros de entrada.

---

## Código 01 — Dias da Semana (Switch Case + Try-Catch)

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class DiasDaSemanaSwitch {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);

            try {
                System.out.print("Digite um número de 1 a 7: ");
                int dia = scanner.nextInt();

                switch (dia) {
                    case 1:
                        System.out.println("Domingo");
                        break;
                    case 2:
                        System.out.println("Segunda-feira");
                        break;
                    case 3:
                        System.out.println("Terça-feira");
                        break;
                    case 4:
                        System.out.println("Quarta-feira");
                        break;
                    case 5:
                        System.out.println("Quinta-feira");
                        break;
                    case 6:
                        System.out.println("Sexta-feira");
                        break;
                    case 7:
                        System.out.println("Sábado");
                        break;
                    default:
                        System.out.println("Dia inválido");
                        break;
                }

            } catch (InputMismatchException e) {
                System.out.println("Erro: você deve digitar um número inteiro (1 a 7).");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            } finally {
                scanner.close();
            }
        }
    }

---

## Código 02 — Conceito de Notas (Switch Case + Try-Catch)

> Aqui o switch case é possível **após transformar a média em uma “faixa” (categoria)**.  
> Exemplo:  
> - média == 10 → A+  
> - média >= 9 → A  
> - média >= 8 → B  
> - média >= 7 → C  
> - média >= 6 → D  
> - senão → F  

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class ConceitoNotasSwitch {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);

            try {
                System.out.print("Digite a nota 1 (0 a 10): ");
                double nota1 = scanner.nextDouble();

                System.out.print("Digite a nota 2 (0 a 10): ");
                double nota2 = scanner.nextDouble();

                System.out.print("Digite a nota 3 (0 a 10): ");
                double nota3 = scanner.nextDouble();

                System.out.print("Digite a nota 4 (0 a 10): ");
                double nota4 = scanner.nextDouble();

                boolean notasValidas =
                        (nota1 >= 0 && nota1 <= 10) &&
                        (nota2 >= 0 && nota2 <= 10) &&
                        (nota3 >= 0 && nota3 <= 10) &&
                        (nota4 >= 0 && nota4 <= 10);

                if (!notasValidas) {
                    System.out.println("Uma ou mais notas são inválidas. Todas devem estar entre 0 e 10.");
                } else {
                    double media = (nota1 + nota2 + nota3 + nota4) / 4;
                    System.out.printf("Média: %.2f%n", media);

                    int faixa;

                    if (media == 10) {
                        faixa = 5; // A+
                    } else if (media >= 9) {
                        faixa = 4; // A
                    } else if (media >= 8) {
                        faixa = 3; // B
                    } else if (media >= 7) {
                        faixa = 2; // C
                    } else if (media >= 6) {
                        faixa = 1; // D
                    } else {
                        faixa = 0; // F
                    }

                    switch (faixa) {
                        case 5:
                            System.out.println("Conceito A+");
                            break;
                        case 4:
                            System.out.println("Conceito A");
                            break;
                        case 3:
                            System.out.println("Conceito B");
                            break;
                        case 2:
                            System.out.println("Conceito C");
                            break;
                        case 1:
                            System.out.println("Conceito D");
                            break;
                        default:
                            System.out.println("Conceito F");
                            break;
                    }
                }

            } catch (InputMismatchException e) {
                System.out.println("Erro: você digitou um valor inválido. Digite apenas números.");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            } finally {
                scanner.close();
            }
        }
    }

---

## Código 03 — Menu de Opções (Switch Case + Try-Catch)

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class MenuOpcoesSwitch {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);

            try {
                System.out.println("MENU:");
                System.out.println("1 - Cadastrar usuário");
                System.out.println("2 - Listar usuários");
                System.out.println("3 - Editar usuário");
                System.out.println("4 - Remover usuário");
                System.out.print("Escolha uma opção: ");

                int opcao = scanner.nextInt();

                switch (opcao) {
                    case 1:
                        System.out.println("Cadastrar usuário");
                        // aqui futuramente teremos os comandos para cadastrar o usuário
                        break;
                    case 2:
                        System.out.println("Listar usuários");
                        // aqui futuramente teremos os comandos para listar o usuário
                        break;
                    case 3:
                        System.out.println("Editar usuário");
                        // aqui futuramente teremos os comandos para editar o usuário
                        break;
                    case 4:
                        System.out.println("Remover usuário");
                        // aqui futuramente teremos os comandos para remover o usuário
                        break;
                    default:
                        System.out.println("Opção inválida");
                        break;
                }

            } catch (InputMismatchException e) {
                System.out.println("Erro: você deve digitar um número inteiro correspondente ao menu.");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            } finally {
                scanner.close();
            }
        }
    }

---

## Código 04 — Avaliador de Idade (Switch Case + Try-Catch)

> Para usar switch case aqui, transformamos a idade em **faixas**.

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class AvaliadorIdadeSwitch {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);

            try {
                System.out.print("Digite a sua idade: ");
                int idade = scanner.nextInt();

                int faixa;

                if (idade < 0) {
                    faixa = -1; // inválida
                } else if (idade < 12) {
                    faixa = 0; // criança
                } else if (idade < 18) {
                    faixa = 1; // adolescente
                } else if (idade < 60) {
                    faixa = 2; // adulto
                } else {
                    faixa = 3; // idoso
                }

                switch (faixa) {
                    case -1:
                        System.out.println("Idade inválida.");
                        break;
                    case 0:
                        System.out.println("Criança");
                        break;
                    case 1:
                        System.out.println("Adolescente");
                        break;
                    case 2:
                        System.out.println("Adulto");
                        break;
                    default:
                        System.out.println("Idoso");
                        break;
                }

            } catch (InputMismatchException e) {
                System.out.println("Erro: você deve digitar um número inteiro para a idade.");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            } finally {
                scanner.close();
            }
        }
    }

---

## Código 05 — Cálculo de IMC (Switch Case + Try-Catch)

> Para usar switch case, transformamos o IMC em uma **categoria**.

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class CalculoIMCSwitch {
        public static void main(String[] args) {
            Scanner scanner = new Scanner(System.in);

            try {
                System.out.print("Digite seu peso (kg): ");
                double peso = scanner.nextDouble();

                System.out.print("Digite sua altura (m): ");
                double altura = scanner.nextDouble();

                double imc = peso / (altura * altura);
                System.out.printf("Seu IMC é: %.2f%n", imc);

                int categoria;

                if (imc < 18.5) {
                    categoria = 0;
                } else if (imc < 25) {
                    categoria = 1;
                } else if (imc < 30) {
                    categoria = 2;
                } else if (imc < 35) {
                    categoria = 3;
                } else if (imc < 40) {
                    categoria = 4;
                } else {
                    categoria = 5;
                }

                switch (categoria) {
                    case 0:
                        System.out.println("Classificação: Abaixo do peso");
                        break;
                    case 1:
                        System.out.println("Classificação: Peso normal");
                        break;
                    case 2:
                        System.out.println("Classificação: Sobrepeso");
                        break;
                    case 3:
                        System.out.println("Classificação: Obesidade grau I");
                        break;
                    case 4:
                        System.out.println("Classificação: Obesidade grau II");
                        break;
                    default:
                        System.out.println("Classificação: Obesidade grau III");
                        break;
                }

            } catch (InputMismatchException e) {
                System.out.println("Erro: você digitou um valor inválido. Digite apenas números.");
            } catch (ArithmeticException e) {
                System.out.println("Erro: divisão inválida. Verifique se a altura é maior que zero.");
            } catch (Exception e) {
                System.out.println("Erro inesperado: " + e.getMessage());
            } finally {
                scanner.close();
            }
        }
    }

<!-- nav_start -->
---
Anterior: [70 Solucao Teste1 Q05](../docs/70_Solucao_Teste1_Q05.md) | Proximo: [73 Lista Exercicios 05](../docs/73_Lista_Exercicios_05.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
