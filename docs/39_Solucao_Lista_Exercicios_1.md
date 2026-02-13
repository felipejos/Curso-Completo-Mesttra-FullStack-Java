# ✅ Solução — Lista de Exercícios 1

Abaixo estão as soluções dos exercícios da **Lista 1**.

💡 **Dica:** copie **um exercício por vez** para testar no seu editor/IDE, porque cada solução possui uma classe principal (`Main` ou `App`) e imports próprios.

---

## 🟦 Exercício 01 — Terreno (área e valor de venda)

### 📌 O que o programa faz
- Lê **frente (m)** e **lateral (m)**
- Calcula a **área**
- Lê o **valor do m²**
- Mostra a **área** e o **valor total do terreno**

### ✅ Código

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

## 🟩 Exercício 02 — Quantos salários mínimos ganha

### 📌 O que o programa faz
- Lê o **salário do funcionário**
- Lê o **salário mínimo**
- Calcula quantos **salários mínimos** o funcionário recebe

### ✅ Código

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

---

## 🟨 Exercício 03 — Ferraduras para os cavalos

### 📌 O que o programa faz
- Lê a **quantidade de cavalos**
- Lê o **valor da ferradura**
- Calcula o gasto considerando **4 ferraduras por cavalo**
- Usa `try/catch` para entrada inválida

### ✅ Código

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

---

## 🟥 Exercício 04 — Reajuste + descontos INSS e FGTS

### 📌 O que o programa faz
- Lê o **salário**
- Aplica **aumento de 15%**
- Desconta **INSS (11%)** e **FGTS (8%)**
- Mostra: salário reajustado, descontos, total e salário final
- Usa `try/catch` para entrada inválida

### ✅ Código

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

## 🟪 Exercício 05 — Gasto total com anéis dos frangos

### 📌 O que o programa faz
- Lê a **quantidade de frangos**
- Usa:
  - anel com chip: **R$ 4,00**
  - anel de alimento: **R$ 3,50** (são **2** por frango)
- Calcula gasto total
- Usa `try/catch` para entrada inválida

### ✅ Código

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

---

## ⬛ Exercício 06 — Ingredientes (kg) para sanduíches

### 📌 O que o programa faz
- Lê a quantidade de **sanduíches**
- Considera:
  - queijo: **2 fatias** (50g cada)
  - presunto: **1 fatia** (50g)
  - hambúrguer: **1 rodela** (120g)
- Converte gramas → **kg**
- Usa `try/catch` para entrada inválida

### ✅ Código

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

# Complemento da Lição

## 1) Checklist rápido de validação (para cada exercício)
- [ ] Rodei o programa e testei com valores “normais”
- [ ] Testei com **letras** no lugar de números (entrada inválida)
- [ ] Verifiquei se a saída faz sentido (unidades, casas decimais, fórmula correta)
- [ ] Conferi se não ficou travado esperando entrada sem mostrar mensagem
- [ ] O programa encerra normalmente

---

## 2) Padrão profissional (console) para evitar problemas comuns
### ✅ 2.1 Quando usar `float` e quando usar `double`
- `float`: funciona, mas tem **menos precisão**
- `double`: é o padrão mais comum para cálculos com decimais

### ✅ 2.2 `Scanner` e “vírgula vs ponto” (caso apareça erro)
Em alguns ambientes, digitar `8,5` pode quebrar a leitura numérica.
Se isso acontecer, o ideal é padronizar a entrada (por exemplo, sempre usar **ponto** `8.5`) ou ajustar a configuração de leitura.

---

## 3) Exercício de evolução (refatoração simples)
Escolha **1 dos exercícios** e refaça assim:

### 🎯 Meta
Separar em 3 métodos (organização tipo “mini-arquitetura”):
- `lerDados()`
- `calcular()`
- `imprimirResultado()`

### ✅ Resultado esperado
Você passa a ter um `main()` pequeno e um código mais legível (cada parte com uma responsabilidade).

---

## 4) Exercício extra (Try/Catch consistente)
Aplique `try/catch` também no **Exercício 01** e **Exercício 02** (eles importam `InputMismatchException`, mas não tratam a entrada).

### Regras
- Se o usuário digitar texto, mostrar mensagem amigável
- Encerrar o programa normalmente (sem “stack trace” obrigatório)
"""

<!-- nav_start -->
---
Anterior: [38 Sugestao Exercicio](../docs/38_Sugestao_Exercicio.md) | Proximo: [40 Operacoes Comparacao](../docs/40_Operacoes_Comparacao.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
