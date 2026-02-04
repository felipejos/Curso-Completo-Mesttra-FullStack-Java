Exercícios Sobre Funções e Procedimentos
         

Faça a alteração dos códigos abaixo da seguinte forma:



O Bloco de comandos que estiver destacado em verde deve ser convertido para funções;

O Bloco de comandos que estiver destacado em vermelho deve ser convertido para procedimentos:

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
                
                //Exemplo: frenteMts = lerValorFloat(teclado, "Quantos metros o terreno possui de frente: ");
                System.out.print("Quantos metros o terreno possui de frente: ");
                frenteMts = teclado.nextFloat();

                //Exemplo: lateralMts = lerValorFloat(teclado, "Quantos metros o terreno possui de lateral: ");                
                System.out.print("Quantos metros o terreno possui de lateral: ");
                lateralMts = teclado.nextFloat();
                
                //Exemplo: valorMetroQrd = lerValorFloat(teclado, "Informe o valor do metro quadrado: ");  
                System.out.print("Informe o valor do metro quadrado: ");
                valorMetroQrd = teclado.nextFloat();
                
                //Exemplo: areaTotalMts = calcularAreaTotal(frenteMts, lateralMts);
                areaTotalMts = (frenteMts * lateralMts);

                //Exemplo: exibirDados(frenteMts, lateralMts, valorMetroQrd);
                System.out.print("Area total o terreno de " + frenteMts + " metros de frente com " +  lateralMts + " metros de lateral é: ");
                System.out.println( areaTotalMts + " mts.");
                System.out.print("Valor total do terreno: R$ " + (valorMetroQrd * areaTotalMts) );
        }
}
Para os próximos códigos, você decidirá qual será o nome das funções e dos procedimentos.
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
                
                System.out.print("Digite o valor do salário do funcionário: R$ ");
                salarioFuncionario = teclado.nextFloat();
                
                System.out.print("Digite o valor do salário mínimo: R$ ");
                salarioMinimo = teclado.nextFloat();
                
                resultado = (salarioFuncionario / salarioMinimo);
                
                System.out.print("O funcionario ganha " + resultado + " salários. ");
        }
}

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
            System.out.println("Voce digitou um valor invalido. Por favor, digite apenas números.");
        } catch (Exception e) {
            System.out.println("Ocorreu um erro inesperado: ");
            e.printStackTrace();
        }

        //Fechamos a conexao com o teclado
        teclado.close(); 
    }
}
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
            System.out.print("Digite o valor do salário: R$ ");
            salario = teclado.nextFloat();
            
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
            System.out.println("Voce digitou um valor invalido. Por favor, digite apenas números.");
        } catch (Exception e) {
            System.out.println("Ocorreu um erro inesperado: ");
            e.printStackTrace();
        }
        
        //fechando o a conecao com o teclado
        teclado.close();
    }
}


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

            System.out.printf("O valor total para identicar %d frangos é R$ %.2f reais.", qtdeFrangos, gastoTotalAneis);
        } catch (InputMismatchException e) {
            // trata o erro quando o usuário digita um valor que não é um número inteiro
            System.out.println("Erro: você deve digitar um número inteiro.");
        } catch (Exception e){
            // trata qualquer outro erro que possa ocorrer
            System.out.println("\nErro inesperado: ");
            e.printStackTrace();
        }

        teclado.close();
    }
}
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

            System.out.printf("\nPara fabricar %d sanduiches, você precisará de:\n\n", qtdeSanduiches);
            System.out.printf("%.2f kg de mussarela\n", pesoMussarelaKgs);
            System.out.printf("%.2f kg de presunto\n", pesoPresuntoKgs);
            System.out.printf("%.2f kg de hamburguer\n", pesoHamburguerKgs);

        }  catch (InputMismatchException e) {
            System.out.println("Voce digitou um valor invalido. Por favor, digite apenas números.");
        } catch (Exception e) {
            System.out.println("Ocorreu um erro inesperado: ");
            e.printStackTrace();
        }
        
        //fechando o a conecao com o teclado
        teclado.close();                
    }
}

---

## Opção melhorada

### 1) Terreno (convertendo blocos em funções e procedimentos)

Objetivo:
- **Funções**: retornam valor (ex: leitura e cálculo).
- **Procedimentos**: apenas exibem (ex: impressão).

    // importa a classe scanner para lidar com a entrada de dados
    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {

            Scanner teclado = new Scanner(System.in);

            float frenteMts = lerValorFloat(teclado, "Quantos metros o terreno possui de frente: ");
            float lateralMts = lerValorFloat(teclado, "Quantos metros o terreno possui de lateral: ");
            float valorMetroQrd = lerValorFloat(teclado, "Informe o valor do metro quadrado: ");

            float areaTotalMts = calcularAreaTotal(frenteMts, lateralMts);

            exibirDadosTerreno(frenteMts, lateralMts, areaTotalMts, valorMetroQrd);

            teclado.close();
        }

        // FUNÇÃO (retorna float)
        static float lerValorFloat(Scanner teclado, String mensagem) {
            float valor = 0;

            while (true) {
                try {
                    System.out.print(mensagem);
                    valor = teclado.nextFloat();
                    teclado.nextLine(); // limpar buffer
                    return valor;
                } catch (InputMismatchException e) {
                    System.out.println("Valor inválido. Digite apenas números.");
                    teclado.nextLine(); // limpar buffer
                }
            }
        }

        // FUNÇÃO (retorna área)
        static float calcularAreaTotal(float frenteMts, float lateralMts) {
            return frenteMts * lateralMts;
        }

        // PROCEDIMENTO (só exibe)
        static void exibirDadosTerreno(float frenteMts, float lateralMts, float areaTotalMts, float valorMetroQrd) {
            System.out.print("Area total o terreno de " + frenteMts + " metros de frente com " + lateralMts + " metros de lateral é: ");
            System.out.println(areaTotalMts + " mts.");
            System.out.print("Valor total do terreno: R$ " + (valorMetroQrd * areaTotalMts));
        }
    }

---

### 2) Salário mínimo (você decide nomes)

O que vira função:
- ler salário (função de leitura)
- calcular quantos salários mínimos (função de cálculo)

O que vira procedimento:
- exibir resultado

    // importa a classe scanner para lidar com a entrada de dados
    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {

            Scanner teclado = new Scanner(System.in);

            float salarioFuncionario = lerFloat(teclado, "Digite o valor do salário do funcionário: R$ ");
            float salarioMinimo = lerFloat(teclado, "Digite o valor do salário mínimo: R$ ");

            float resultado = calcularQtdSalarios(salarioFuncionario, salarioMinimo);

            exibirQtdSalarios(resultado);

            teclado.close();
        }

        // FUNÇÃO
        static float lerFloat(Scanner teclado, String mensagem) {
            while (true) {
                try {
                    System.out.print(mensagem);
                    float valor = teclado.nextFloat();
                    teclado.nextLine();
                    return valor;
                } catch (InputMismatchException e) {
                    System.out.println("Valor inválido. Digite apenas números.");
                    teclado.nextLine();
                }
            }
        }

        // FUNÇÃO
        static float calcularQtdSalarios(float salarioFuncionario, float salarioMinimo) {
            return salarioFuncionario / salarioMinimo;
        }

        // PROCEDIMENTO
        static void exibirQtdSalarios(float resultado) {
            System.out.print("O funcionario ganha " + resultado + " salários. ");
        }
    }

---

### 3) Cavalos e ferraduras

Funções:
- ler quantidade de cavalos
- ler valor ferradura
- calcular gasto total

Procedimento:
- exibir resultado

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class App {
        public static void main(String[] args) {

            Scanner teclado = new Scanner(System.in);

            float qtdeCavalos = lerFloat(teclado, "Digite a quantidade de cavalos comprados: ");
            float valorFerradura = lerFloat(teclado, "Digite o valor de cada ferradura: R$ ");

            float gasto = calcularGastoFerraduras(qtdeCavalos, valorFerradura);

            exibirGastoFerraduras(qtdeCavalos, gasto);

            teclado.close();
        }

        // FUNÇÃO
        static float lerFloat(Scanner teclado, String mensagem) {
            while (true) {
                try {
                    System.out.print(mensagem);
                    float valor = teclado.nextFloat();
                    teclado.nextLine();
                    return valor;
                } catch (InputMismatchException e) {
                    System.out.println("Voce digitou um valor invalido. Por favor, digite apenas números.");
                    teclado.nextLine();
                }
            }
        }

        // FUNÇÃO
        static float calcularGastoFerraduras(float qtdeCavalos, float valorFerradura) {
            return qtdeCavalos * 4 * valorFerradura;
        }

        // PROCEDIMENTO
        static void exibirGastoFerraduras(float qtdeCavalos, float gasto) {
            System.out.print("Para equipa " + qtdeCavalos + " cavalos sera qasto R$ " + gasto + " reais. ");
        }
    }

---

### 4) Salário reajustado + descontos

Funções:
- ler salário
- calcular salário reajustado
- calcular INSS
- calcular FGTS
- calcular total descontos
- calcular salário final

Procedimento:
- exibir relatório

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class App {
        public static void main(String[] args) {

            Scanner teclado = new Scanner(System.in);

            float salario = lerFloat(teclado, "Digite o valor do salário: R$ ");

            float salarioReajustado = calcularReajuste(salario);
            float inss = calcularINSS(salarioReajustado);
            float fgts = calcularFGTS(salarioReajustado);
            float totalDesconto = calcularTotalDesconto(inss, fgts);
            float salarioFinal = calcularSalarioFinal(salarioReajustado, totalDesconto);

            exibirRelatorioSalario(salarioReajustado, inss, fgts, totalDesconto, salarioFinal);

            teclado.close();
        }

        // FUNÇÃO
        static float lerFloat(Scanner teclado, String mensagem) {
            while (true) {
                try {
                    System.out.print(mensagem);
                    float valor = teclado.nextFloat();
                    teclado.nextLine();
                    return valor;
                } catch (InputMismatchException e) {
                    System.out.println("Voce digitou um valor invalido. Por favor, digite apenas números.");
                    teclado.nextLine();
                }
            }
        }

        // FUNÇÕES (cálculo)
        static float calcularReajuste(float salario) {
            return salario * 1.15f;
        }

        static float calcularINSS(float salarioReajustado) {
            return salarioReajustado * 0.11f;
        }

        static float calcularFGTS(float salarioReajustado) {
            return salarioReajustado * 0.08f;
        }

        static float calcularTotalDesconto(float inss, float fgts) {
            return inss + fgts;
        }

        static float calcularSalarioFinal(float salarioReajustado, float totalDesconto) {
            return salarioReajustado - totalDesconto;
        }

        // PROCEDIMENTO
        static void exibirRelatorioSalario(float salarioReajustado, float inss, float fgts, float totalDesconto, float salarioFinal) {
            System.out.println("Salario reajustado: R$ " + salarioReajustado);
            System.out.print("Desconto INSS: R$ " + inss + "\n");
            System.out.print("Desconto FGTS: R$ " + fgts + "\n");
            System.out.println("Total de descontos (INSS + FGTS): R$ " + totalDesconto);
            System.out.println("Salario Final: R$ " + salarioFinal);
        }
    }

---

### 5) Frangos (chips)

Funções:
- ler inteiro (qtde frangos)
- calcular gasto total

Procedimento:
- exibir gasto

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class App {
        public static void main(String[] args) {

            Scanner teclado = new Scanner(System.in);

            int qtdeFrangos = lerInt(teclado, "Digite a quantidade de frangos a ser identificados: ");

            float valorChipIdentificacao = 4f;
            float valorChipAlimento = 3.5f;

            float gastoTotalAneis = calcularGastoAneis(qtdeFrangos, valorChipIdentificacao, valorChipAlimento);

            exibirGastoFrangos(qtdeFrangos, gastoTotalAneis);

            teclado.close();
        }

        // FUNÇÃO
        static int lerInt(Scanner teclado, String mensagem) {
            while (true) {
                try {
                    System.out.print(mensagem);
                    int valor = teclado.nextInt();
                    teclado.nextLine();
                    return valor;
                } catch (InputMismatchException e) {
                    System.out.println("Erro: você deve digitar um número inteiro.");
                    teclado.nextLine();
                }
            }
        }

        // FUNÇÃO
        static float calcularGastoAneis(int qtdeFrangos, float chipId, float chipAlimento) {
            return qtdeFrangos * (chipId + (2 * chipAlimento));
        }

        // PROCEDIMENTO
        static void exibirGastoFrangos(int qtdeFrangos, float gastoTotalAneis) {
            System.out.printf("O valor total para identicar %d frangos é R$ %.2f reais.", qtdeFrangos, gastoTotalAneis);
        }
    }

---

### 6) Sanduíches

Funções:
- ler quantidade de sanduíches
- calcular kg de mussarela
- calcular kg de presunto
- calcular kg de hamburguer

Procedimento:
- exibir relatório

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class App {
        public static void main(String[] args) {

            Scanner teclado = new Scanner(System.in);

            int qtdeSanduiches = lerInt(teclado, "Digite a quantidade de sanduiches a serem fabricados: ");

            int qtdeFatiasMussarela = 2, qtdeFatiasPresunto = 1, qtdeHamburguer = 1;
            float fatiaMussarelaGrms = 50, fatiaPresuntoGrms = 50, hamburguerGrms = 120;

            float pesoMussarelaKgs = calcularPesoKg(qtdeSanduiches, qtdeFatiasMussarela, fatiaMussarelaGrms);
            float pesoPresuntoKgs = calcularPesoKg(qtdeSanduiches, qtdeFatiasPresunto, fatiaPresuntoGrms);
            float pesoHamburguerKgs = calcularPesoKg(qtdeSanduiches, qtdeHamburguer, hamburguerGrms);

            exibirIngredientes(qtdeSanduiches, pesoMussarelaKgs, pesoPresuntoKgs, pesoHamburguerKgs);

            teclado.close();
        }

        // FUNÇÃO
        static int lerInt(Scanner teclado, String mensagem) {
            while (true) {
                try {
                    System.out.print(mensagem);
                    int valor = teclado.nextInt();
                    teclado.nextLine();
                    return valor;
                } catch (InputMismatchException e) {
                    System.out.println("Voce digitou um valor invalido. Por favor, digite apenas números.");
                    teclado.nextLine();
                }
            }
        }

        // FUNÇÃO (cálculo genérico de peso)
        static float calcularPesoKg(int qtdeSanduiches, int qtdeItensPorSanduiche, float gramasPorItem) {
            return (qtdeSanduiches * qtdeItensPorSanduiche * gramasPorItem) / 1000f;
        }

        // PROCEDIMENTO
        static void exibirIngredientes(int qtdeSanduiches, float mussarelaKg, float presuntoKg, float hamburguerKg) {
            System.out.printf("\nPara fabricar %d sanduiches, você precisará de:\n\n", qtdeSanduiches);
            System.out.printf("%.2f kg de mussarela\n", mussarelaKg);
            System.out.printf("%.2f kg de presunto\n", presuntoKg);
            System.out.printf("%.2f kg de hamburguer\n", hamburguerKg);
        }
    }

---

<!-- nav_start -->
---
Anterior: [DESAFIO PRIMEIRA HACKATHON](../docs/135_Primeira_Hackathon.md) | Próximo: [ExercÃ­cio Salvando dados em txt](../docs/137_Salvando_TXT.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

