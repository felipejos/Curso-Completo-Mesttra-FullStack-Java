# Funções


Com base no código abaixo peça o chatgpt para.



Para isto copie e cole o texto e o código no prompt do chatgpt.



Sou iniciante em programação, aprendi sobre variavéis, comandos de entrada e saída e estrutras de decisão, me explique o conceito de funções em java. Explique como é a sintaxe e execução de funções criadas pelo próprio usuário. Quais funções de usuário poderiam ser criadas no código abaixo para otimizar o algoritmo e tirar proveito dos conceitos de funções.



    import java.util.Scanner;
    import java.lang.Math;
    
    public class App {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            double area;
    
            String mensagem = "";
    
            int opcao = 0;
    
            exibirMenu();  // chamada do bloco de código exibirMenu que está definido ao fim deste código
    
            try {
                System.out.print("Digite o número da opção desejada: ");
                opcao = teclado.nextInt();
    
                switch (opcao) {
                    case 1:
                        double raio;
    
                        try {
                            System.out.print("Digite o valor do raio da circunferencia em metros: ");
                            raio = teclado.nextDouble();
    
                            area =  3.14159 * raio * raio;
                            mensagem = "Área do círculo: " +  Math.round(area)   ;
    
                        } catch (Exception e) {
                            System.out.println("Valor inválido para o raio.");
                        }
                            
                        break;
                    case 2:
                        double largura, altura;
                        
                        System.out.print("Digite a largura do retangulo: ");
                        largura = teclado.nextDouble();
                        System.out.print("Digite a altura do retangulo: ");
                        altura = teclado.nextDouble();
    
                        area = largura * altura;
                        
                        mensagem = "Área do retângulo: " + area + " metros";
                        break;
                    case 3:
                        double base;
                        
                        System.out.print("Digite a base do triângulo: ");
                        base = teclado.nextDouble();
                        System.out.print("Digite a altura do triângulo: ");
                        altura = teclado.nextDouble();
    
                        area = (base * altura) / 2;
                        
                        mensagem = "Área do triângulo: " + area + " metros";
                        break;
                    default:
                        System.out.println("Opção inválida.");
                        break;
                }
            } catch (Exception e) {
                System.out.println("Opção inválida.");
            }
    
    
            System.out.println(mensagem);
            teclado.close();
        }
    
        static void exibirMenu(){ //inicio do bloco de código exibirMenu
            System.out.println("== Sistema para cálculo da área de figuras geométricas ==\n");
            System.out.println("1 - Círculo");
            System.out.println("2 - Retângulo");
            System.out.println("3 - Triângulo\n");
        } //fim do bloco de código exibirMenu
    }


---

## Explicação: o que são Funções em Java


No Java, tudo que você escreve “separado em blocos” com nome é chamado de **método**.

- **Procedimento** (você já viu): é um método que **não retorna valor**. Em Java, ele tem `void`.  
  Ex.: `static void exibirMenu() { ... }`

- **Função**: é um método que **retorna um valor** (int, double, String, boolean, etc).  
  Ex.: `static double calcularAreaCirculo(double raio) { ... return area; }`

Pense assim:
- Procedimento = “faz algo”
- Função = “calcula algo e me devolve o resultado”

---

## Sintaxe de uma função (método com retorno)


Estrutura geral:

    modificador static tipoRetorno nomeDaFuncao(tipoParametro1 parametro1, tipoParametro2 parametro2, ...) {
        // comandos
        return algumValorDoMesmoTipoDoRetorno;
    }

Exemplos:
- `tipoRetorno` pode ser `int`, `double`, `String`, `boolean`, etc.
- `return` é obrigatório em funções (porque elas precisam “devolver” algo).

---

## Como a execução de uma função acontece


1. O programa está rodando no `main`.
2. Quando chega numa chamada como `calcularAreaCirculo(raio)`, ele:
   - “entra” na função,
   - executa o código dentro dela,
   - encontra o `return`,
   - “volta” para o ponto onde foi chamada, entregando o valor calculado.

Exemplo simples:

    double area = calcularAreaCirculo(2.0);

- A função calcula e retorna um `double`
- Esse `double` é guardado na variável `area`

---

## Quais funções você poderia criar no código para otimizar


No seu algoritmo, você tem **cálculos que podem virar funções**, porque:
- são tarefas bem definidas (calcular área),
- podem ser reaproveitadas,
- deixam o `main` mais limpo.

Boas funções para criar:

1) **Funções de cálculo (retornam double)**
- `calcularAreaCirculo(double raio)`
- `calcularAreaRetangulo(double largura, double altura)`
- `calcularAreaTriangulo(double base, double altura)`

2) **Funções para leitura segura (retornam valor lido)**
- `lerInt(Scanner teclado, String mensagem)`
- `lerDouble(Scanner teclado, String mensagem)`

Essas funções ajudam muito, porque você concentra o `try-catch` de leitura em um único lugar.

3) **Funções para montar mensagem**
- `montarMensagemArea(String figura, double area)`

---

## Exemplo prático de funções que cabem nesse código


### 1) Funções de cálculo

    static double calcularAreaCirculo(double raio) {
        return 3.14159 * raio * raio;
    }

    static double calcularAreaRetangulo(double largura, double altura) {
        return largura * altura;
    }

    static double calcularAreaTriangulo(double base, double altura) {
        return (base * altura) / 2;
    }

### 2) Função para leitura de double com try-catch (uma opção simples)

Obs.: aqui é só um exemplo didático. Você pode escolher se quer “tentar de novo” ou só “falhar e avisar”.

    static double lerDouble(Scanner teclado, String texto) {
        System.out.print(texto);
        return teclado.nextDouble();
    }

### 3) Como ficaria a ideia no main (conceito)

- Você leria os valores
- Chamaria a função de cálculo
- Montaria a mensagem

    area = calcularAreaRetangulo(largura, altura);
    mensagem = "Área do retângulo: " + area + " metros";

---

## Resumo rápido (para fixar)


- **Função** em Java = método que **retorna** um valor (não usa `void`).
- Sintaxe sempre tem: **tipo de retorno + return**.
- Você deve criar funções quando:
  - existe cálculo isolado,
  - existe repetição,
  - você quer deixar o `main` mais organizado.

Se você quiser, depois você pode me mandar como ficou o seu código refatorado e eu te digo se você realmente transformou em funções do jeito certo (sem mudar a lógica).

<!-- nav_start -->
---
Anterior: [86 Procedimentos Parametros](../docs/86_Procedimentos_Parametros.md) | Proximo: [88 Video Resumo Funcoes](../docs/88_Video_Resumo_Funcoes.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
