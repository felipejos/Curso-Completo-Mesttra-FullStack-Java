## 📐 Calcular Área Figuras Geométricas

Mesmo algoritmo do dia 23/10/2025 (Calculadora de área de Figuras Geométricas) modificado para utilizar funções e procedimentos.

---

## ✅ Código (Java)

    import java.util.InputMismatchException;
    import java.util.Scanner;
    import java.lang.Math;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            int opcao = 0;
            String nome;
           
            nome = obterString(teclado, "Digite o seu nome: ");

            exibirMenu(nome); 

            try {
                opcao = obterInt(teclado, "Digite o número da opção desejada: ");

                switch (opcao) {
                    case 1:
                        calcularAreaCirculo(teclado); 
                        break;
                    case 2:
                        calcularAreRetangulo(teclado);
                        break;
                    case 3:
                        calcularAreaTriangulo(teclado);
                        break;
                    default:
                        System.out.println("Opção inválida.");
                        break;
                }
            } catch (Exception e) {
                System.out.println("Opção inválida.");
            }

            teclado.close();
        }

        static void exibirMenu(String xyz) {
            System.out.println("== Sistema para cálculo da área de figuras geométricas ==\n");

            System.out.println("Seja bem vindo, " + xyz + "!\n");

            System.out.println("1 - Círculo");
            System.out.println("2 - Retângulo");
            System.out.println("3 - Triângulo\n");
        }

        static int obterInt(Scanner teclado, String mensagem){
            int numero = 0;

            System.out.print(mensagem);

            try {
                numero = teclado.nextInt();
            } catch (InputMismatchException e) {
                System.out.println("Valor digitado é inválido.");
            }

            return numero;     
        }

        static String obterString(Scanner teclado, String mensagem){
            System.out.print(mensagem);
            try {
                return teclado.nextLine();
            } catch (Exception e) {
                System.out.println(e.getMessage());
                return "";
            }
        }

        static void calcularAreaCirculo(Scanner teclado){
            double raio;

            try {
                System.out.print("Digite o valor do raio da circunferencia em metros: ");
                raio = teclado.nextDouble();

                double area =  3.14159 * raio * raio;
                System.out.println("Área do círculo: " +  Math.round(area) + " metros");

            } catch (Exception e) {
                System.out.println("Valor inválido para o raio.");
            }
        }

        static void calcularAreRetangulo(Scanner teclado){
            double largura, altura;
                        
            System.out.print("Digite a largura do retangulo: ");
            largura = teclado.nextDouble();
            System.out.print("Digite a altura do retangulo: ");
            altura = teclado.nextDouble();

        
            System.out.println("Área do retângulo: " + largura * altura + " metros");
        }

        static void calcularAreaTriangulo(Scanner teclado){
             double base;
                        
            System.out.print("Digite a base do triângulo: ");
            base = teclado.nextDouble();
            System.out.print("Digite a altura do triângulo: ");
            double altura = teclado.nextDouble();

            System.out.println("Área do triângulo: " + (base * altura) / 2 + " metros");
        }
    }

---

# Complemento da Lição

---

## 🧠 Módulo 1 — O que você já fez de certo (visão “de professor”)

Você aplicou 2 ideias muito boas de organização:

- **Procedimento** para exibir o menu: `exibirMenu(...)`  
  (faz uma ação e não devolve valor)
- **Funções/Procedimentos auxiliares** para separar responsabilidades:
  - leitura: `obterString`, `obterInt`
  - cálculo + exibição: `calcularAreaCirculo`, `calcularAreRetangulo`, `calcularAreaTriangulo`

Isso deixa o `main` mais legível, porque ele fica focado em:
- perguntar o nome
- mostrar menu
- ler opção
- chamar o “bloco certo” no `switch`

---

## 🧩 Módulo 2 — Diferença prática: função vs procedimento no seu código

Regra simples:
- **Se tem `void` → procedimento**
- **Se retorna um valor (`int`, `double`, `String`) → função**

No seu código:

- ✅ Funções (retornam valor):
  - `obterInt(...)` retorna `int`
  - `obterString(...)` retorna `String`

- ✅ Procedimentos (não retornam valor):
  - `exibirMenu(...)` (void)
  - `calcularAreaCirculo(...)` (void)
  - `calcularAreRetangulo(...)` (void)
  - `calcularAreaTriangulo(...)` (void)

Ponto importante (para fixar o conceito):
- Mesmo com o nome “calcular...”, esses 3 métodos são **procedimentos**, porque eles **imprimem** e não retornam área.

---

## 🧱 Módulo 3 — Um “upgrade” de arquitetura (mais organizado e mais reutilizável)

Uma separação bem comum (e bem fácil) é:

### A) Funções puras (só calculam e retornam)
- `calcularAreaCirculo(double raio) -> double`
- `calcularAreaRetangulo(double largura, double altura) -> double`
- `calcularAreaTriangulo(double base, double altura) -> double`

### B) Procedimentos (só interação com usuário: print/leitura/fluxo)
- `exibirMenu(String nome)`
- `mostrarResultado(String figura, double area)`
- `lerDouble(Scanner teclado, String mensagem)` (pode ser função)

Por que isso ajuda:
- você consegue **reusar o cálculo** sem depender de teclado/console
- fica mais fácil testar: “se eu passar 2 e 3, retorna 6?”

Trade-off (bem direto):
- fica um pouco mais “quebrado em métodos” (mais métodos)
- mas cada método fica mais simples e mais fácil de entender

---

## ⚠️ Módulo 4 — Pontos de atenção (erros comuns que podem aparecer)

### 1) `obterInt` e entrada inválida
Se o usuário digitar texto (ex.: `abc`) no `nextInt()`, ocorre erro, você imprime a mensagem e retorna `0`.

Consequência:
- `opcao` pode virar `0`
- cai no `default` (“Opção inválida.”)
- mas o `Scanner` pode continuar “preso” na entrada inválida se não consumir a linha

Uma técnica simples (bem comum) é consumir a linha depois do erro:
- `teclado.nextLine();`

### 2) Unidade de medida (metros vs m²)
O texto diz “em metros”, mas **área** é **m²**.

Exemplo de saída mais correta:
- `Área do retângulo: 10.0 m²`

### 3) Nome do método: `calcularAreRetangulo`
O nome parece ter um pequeno erro de digitação (“Are”).
Isso não quebra o programa, mas prejudica leitura.

---

## ✅ Módulo 5 — Checklist rápido de “código mais profissional” (sem complicar)

- [ ] Mensagens com acentuação e termos consistentes (“retângulo”, “circunferência”, “Seja bem-vindo”)
- [ ] Área exibida com unidade correta (`m²`)
- [ ] Leitura numérica com validação (não aceitar negativo, por exemplo)
- [ ] Cálculo separado de impressão (função calcula, procedimento mostra)

---

## 🧪 Exercícios (um passo de cada vez, para você praticar de verdade)

1) Transforme **apenas 1** dos métodos em função:
- faça o “círculo” ter uma função que retorna `double` (a área)
- e um procedimento só para imprimir o resultado

2) Padronize a unidade:
- troque “metros” por “m²” nas 3 figuras

3) Ajuste o nome:
- renomeie `calcularAreRetangulo` para `calcularAreaRetangulo`

4) Crie um procedimento `mostrarResultado(String figura, double area)` para evitar repetição de `System.out.println(...)`

---


<!-- nav_start -->
---
Anterior: [90 Morangos Macas](../docs/90_Morangos_Macas.md) | Proximo: [92 Lista Exercicios 07](../docs/92_Lista_Exercicios_07.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
