## 🍓🍎 Algoritmo: Morangos e Maçãs

### 🎯 Objetivo do estudo
Estude o código abaixo, execute-o, leia comando por comando para entender o que cada um faz.  
Depois de que você julgar que entendeu o código, tente reescrever este código sozinho **sem copiá-lo**.

---

## ✅ Código completo (para análise e execução)

    import java.util.Scanner;
    import java.util.InputMismatchException;

    public class Main {

        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            float qtdeMaca;
            float qtdeMorango;

            float valorTotalMaca, valorTotalMorango;

            qtdeMaca = obterFloat(teclado, "Digite quantos KG de Macas foram comprados: ");
            qtdeMorango = obterFloat(teclado, "Digite quantos KG de Morangos foram comprados: ");

            valorTotalMaca = calcularValorMaca(qtdeMaca);
            valorTotalMorango = calcularValorMorango(qtdeMorango);

            mostrarValorTotal(valorTotalMaca, valorTotalMorango);

            teclado.close();
        }

        //Funcao ou metodo que retorna valor
        static float calcularValorMorango(float qtdeMorango){
            float valorTotalMorango;

            // estrutura de decisao
            if (qtdeMorango > 5) { // e executado quando qtdeMorange é > 5
                valorTotalMorango = qtdeMorango * 2.2f;
            } else { // e executado quando qtdeMorange nao é > 5
                valorTotalMorango = qtdeMorango * 2.5f;
            }
            // o bloco de codigo acima pode ser reescrito assim utilizando um operador ternario
            // valorTotalMorango = (qtdeMorango > 5) ? (qtdeMorango * 2.2f) : (qtdeMorango * 2.5f);

            return valorTotalMorango;
        }
        
        //Funcao ou metodo que retorna valor  
        static float calcularValorMaca(float qtdeMaca) {
            
            float valorTotalMaca;

            if (qtdeMaca <= 5) { // verdade
                valorTotalMaca = qtdeMaca * 1.8f;
            } else { // falso
                valorTotalMaca = qtdeMaca * 1.5f;
            }
            // o bloco de codigo acima pode ser reescrito assim utilizando um operador ternario
            // valorTotalMaca = (qtdeMaca <= 5) ? (qtdeMaca * 1.8f) : (qtdeMaca * 1.5f);

           return valorTotalMaca;
        }

        //Funcao ou metodo que retorna valor
        static float obterFloat(Scanner teclado, String mensagem) {
            //inicializa a variavel valor para evitar erros de variavel nao inicializada
            float valor = 0f;
            System.out.print(mensagem);

            try {
                valor = teclado.nextFloat();
                teclado.nextLine(); // consome a quebra de linha restante
            } catch (InputMismatchException e) {
                System.out.println("Entrada inválida. É necessário digitar um número (ex: 1,5 ou 2).");
            } catch (Exception e) {
                System.out.println("Erro ao ler entrada: " + e.getMessage());
            }

            return valor;
        }

        //Procedimento ou metodo
        static void mostrarValorTotal(float valorTotalMaca, float valorTotalMorango){
            float totalCompra;

            totalCompra = valorTotalMaca + valorTotalMorango;
            System.out.println("O valor total da compra e R$ " + totalCompra);
        }
    }

---

## 🧠 Guia rápido do que observar (sem alterar o conteúdo)

### 1) Fluxo principal (`main`)
- Cria o `Scanner`
- Lê os dois valores via `obterFloat(...)`
- Calcula o total de cada fruta via funções:
  - `calcularValorMaca(qtdeMaca)`
  - `calcularValorMorango(qtdeMorango)`
- Mostra o total via procedimento:
  - `mostrarValorTotal(...)`
- Fecha o teclado

### 2) Funções (retornam valor)
- `calcularValorMaca(...)` → retorna o total da maçã
- `calcularValorMorango(...)` → retorna o total do morango
- `obterFloat(...)` → retorna um `float` digitado (com try/catch)

### 3) Procedimento (não retorna valor)
- `mostrarValorTotal(...)` → só imprime o resultado final

---

<!-- nav_start -->
---
Anterior: [88 Video Resumo Funcoes](../docs/88_Video_Resumo_Funcoes.md) | Proximo: [91 Calcular Area](../docs/91_Calcular_Area.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
