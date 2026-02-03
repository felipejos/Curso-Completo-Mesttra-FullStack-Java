# âœ… SoluÃ§Ã£o â€” Lista de ExercÃ­cios 1

Abaixo estÃ£o as soluÃ§Ãµes dos exercÃ­cios da **Lista 1**.  
> ðŸ’¡ Dica: copie **um exercÃ­cio por vez** para testar no seu editor/IDE, porque cada soluÃ§Ã£o possui uma classe principal (`Main` ou `App`) e imports prÃ³prios.

---

## ðŸŸ¦ ExercÃ­cio 01 â€” Terreno (Ã¡rea e valor de venda)

    // importa a classe scanner para lidar com a entrada de dados
    import java.util.InputMismatchException;
    import java.util.Scanner; 
    public class Main
    {
            public static void main(String[] args) {
                    float frenteMts, lateralMts, areaTotalMts;
                    float valorMetroQrd;
                    
                    Scanner teclado;
                    
                    teclado = new Scanner(System.in);
                    
                    System.out.print("Quantos metros o terreno possui de frente: ");
                    frenteMts = teclado.nextFloat();
                    
                    System.out.print("Quantos metros o terreno possui de lateral: ");
                    lateralMts = teclado.nextFloat();
                    
                    System.out.print("Informe o valor do metro quadrado: ");
                    valorMetroQrd = teclado.nextFloat();
                    
                    areaTotalMts = (frenteMts * lateralMts);
                    System.out.print("Area total o terreno de " + frenteMts + " metros de frente com " +  lateralMts + " metros de lateral: ");
                    System.out.println( areaTotalMts + " mts.");

                    System.out.print("Valor total do terreno: R$ " + (valorMetroQrd * areaTotalMts) );
            }
    }

---

## ðŸŸ© ExercÃ­cio 02 â€” Quantos salÃ¡rios mÃ­nimos ganha

    // importa a classe scanner para lidar com a entrada de dados
    import java.util.InputMismatchException;
    import java.util.Scanner; 
    public class Main
    {
            public static void main(String[] args) {
                    float salarioMinimo, salarioFuncionario;
                    float resultado;
                    
                    Scanner teclado;
                    
                    teclado = new Scanner(System.in);  //Teclado sera util para lermos os valores do teclado
                    
                    System.out.print("Digite o valor do salÃ¡rio do funcionÃ¡rio: R$ ");
                    salarioFuncionario = teclado.nextFloat();
                    
                    System.out.print("Digite o valor do salÃ¡rio mÃ­nimo: R$ ");
                    salarioMinimo = teclado.nextFloat();
                    
                    resultado = (salarioFuncionario / salarioMinimo);
                    
                    System.out.print("O funcionario ganha " + resultado + " salÃ¡rios. ");
            }
    }

---

## ðŸŸ¨ ExercÃ­cio 03 â€” Ferraduras para os cavalos

    // importa a classe scanner para lidar com a entrada de dados
    import java.util.InputMismatchException;
    import java.util.Scanner; 

    public class App
    {
        public static void main(String[] args) {
            float qtdeCavalos;
            float valorFerradura;
        
            //Teclado sera util para lermos os valores do teclado
            Scanner teclado = new Scanner(System.in);  ;
            
            try {
                System.out.print("Digite a quantidade de cavalos comprados: ");
                qtdeCavalos = teclado.nextFloat();
                
                System.out.print("Digite o valor de cada ferradura: R$ ");
                valorFerradura = teclado.nextFloat();
                
                System.out.print("Para equipa " +  qtdeCavalos + " cavalos sera qasto R$ " + (qtdeCavalos * 4 * valorFerradura) + " reais. ");
            }  catch (InputMismatchException e) {
                System.out.println("Voce digitou um valor invalido. Por favor, digite apenas nÃºmeros.");
            } catch (Exception e) {
                System.out.println("Ocorreu um erro inesperado: ");
                e.printStackTrace();
            }

            //Fechamos a conexao com o teclado
            teclado.close(); 
        }
    }

---

## ðŸŸ¥ ExercÃ­cio 04 â€” Reajuste + descontos INSS e FGTS

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class App
    {
        public static void main(String[] args) {
            float salario, salarioReajustado;
            float inss, fgts;
            float totalDesconto;

            Scanner teclado;
            
            teclado = new Scanner(System.in);  //Teclado sera util para lermos os valores do teclado

            try{
                System.out.print("Digite o valor do salÃ¡rio: R$ ");
                salario = teclado.nextFloat();
                
                //salarioReajustado =  (salario * 0.15f) + salario;
                //salarioReajustado =  (salario * 1.15f) ;
                salarioReajustado =  (salario * (float) 1.15) ;
                System.out.println("Salario reajustado: R$ " + salarioReajustado );
                
                inss = (salarioReajustado * 0.11f);
                fgts = (salarioReajustado * 0.08f);
                totalDesconto = inss + fgts;
                
                System.out.print("Desconto INSS: R$ " + inss + "\n");
                System.out.print("Desconto FGTS: R$ " + fgts + "\n");
                System.out.println("Total de descontos (INSS + FGTS): R$ " + totalDesconto );
                System.out.println("Salario Final: R$ " + (salarioReajustado - totalDesconto) );
            }  catch (InputMismatchException e) {
                System.out.println("Voce digitou um valor invalido. Por favor, digite apenas nÃºmeros.");
            } catch (Exception e) {
                System.out.println("Ocorreu um erro inesperado: ");
                e.printStackTrace();
            }
            
            //fechando o a conecao com o teclado
            teclado.close();
        }
    }

---

## ðŸŸª ExercÃ­cio 05 â€” Gasto total com anÃ©is dos frangos

    // importa a classe scanner para lidar com a entrada de dados
    import java.util.InputMismatchException;
    import java.util.Scanner; 

    public class App {
        public static void main(String[] args) throws Exception {
            Scanner teclado = new Scanner(System.in);

            int qtdeFrangos = 0;
            
            float valorChipIdentificacao = 4f;
            float valorChipAlimento = 3.5f;

            float gastoTotalAneis;

            try {
                System.out.print("Digite a quantidade de frangos a ser identificados: ");
                qtdeFrangos = teclado.nextInt();  
                
                gastoTotalAneis = qtdeFrangos * (valorChipIdentificacao + (2 * valorChipAlimento));

                System.out.printf("O valor total para identicar %d frangos Ã© R$ %.2f reais.", qtdeFrangos, gastoTotalAneis);
            } catch (InputMismatchException e) {
                // trata o erro quando o usuÃ¡rio digita um valor que nÃ£o Ã© um nÃºmero inteiro
                System.out.println("Erro: vocÃª deve digitar um nÃºmero inteiro.");
            } catch (Exception e){
                // trata qualquer outro erro que possa ocorrer
                System.out.println("\nErro inesperado: ");
                e.printStackTrace();
            }

            teclado.close();
        }
    }

---

## ðŸŸ« ExercÃ­cio 06 â€” Ingredientes (kg) para sanduÃ­ches

    import java.util.InputMismatchException;
    import java.util.Scanner; 
    public class App
    {
        public static void main(String[] args) {
            //Teclado sera util para lermos os valores do teclado
            Scanner teclado = new Scanner(System.in);  
            
            int qtdeFatiasMussarela = 2, qtdeFatiasPresunto = 1, qtdeHamburguer = 1;
            float fatiaMussarelaGrms = 50, fatiaPresuntoGrms = 50, hamburguerGrms = 120;
            float pesoMussarelaKgs, pesoPresuntoKgs, pesoHamburguerKgs;

            int qtdeSanduiches;

            try{
                System.out.print("Digite a quantidade de sanduiches a serem fabricados: ");
                qtdeSanduiches = teclado.nextInt();
     
                pesoMussarelaKgs = (qtdeSanduiches * qtdeFatiasMussarela * fatiaMussarelaGrms) / 1000;
                pesoPresuntoKgs = (qtdeSanduiches * qtdeFatiasPresunto * fatiaPresuntoGrms) / 1000;
                pesoHamburguerKgs = (qtdeSanduiches * qtdeHamburguer * hamburguerGrms) / 1000;

                System.out.printf("\nPara fabricar %d sanduiches, vocÃª precisarÃ¡ de:\n\n", qtdeSanduiches);
                System.out.printf("%.2f kg de mussarela\n", pesoMussarelaKgs);
                System.out.printf("%.2f kg de presunto\n", pesoPresuntoKgs);
                System.out.printf("%.2f kg de hamburguer\n", pesoHamburguerKgs);

            }  catch (InputMismatchException e) {
                System.out.println("Voce digitou um valor invalido. Por favor, digite apenas nÃºmeros.");
            } catch (Exception e) {
                System.out.println("Ocorreu um erro inesperado: ");
                e.printStackTrace();
            }
            
            //fechando o a conecao com o teclado
            teclado.close();                
        }
    }

<!-- nav_start -->
---
Anterior: [SugestÃ£o ExercÃ­cio](../docs/38_Sugestao_Exercicio.md) | Próximo: [OperaÃ§Ãµes de ComparaÃ§Ã£o](../docs/40_Operacoes_Comparacao.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

