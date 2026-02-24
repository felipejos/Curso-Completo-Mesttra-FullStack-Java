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

# Complemento da Lição

---

## 🧠 Módulo 1 — O que esse programa faz (em 1 frase)
Ele **lê** quantos kg de maçã e morango foram comprados, **calcula** o preço de cada fruta com regras diferentes e **mostra** o total.

---

## 🧩 Módulo 2 — Mapa do fluxo (como o programa “anda”)

1) `main` começa  
2) chama `obterFloat(...)` para ler **kg de maçã**  
3) chama `obterFloat(...)` para ler **kg de morango**  
4) chama `calcularValorMaca(qtdeMaca)` → retorna o valor das maçãs  
5) chama `calcularValorMorango(qtdeMorango)` → retorna o valor dos morangos  
6) chama `mostrarValorTotal(valorTotalMaca, valorTotalMorango)` → imprime o total  
7) fecha o `Scanner`

Ideia-chave:
- **funções** retornam valores (as de cálculo e a de leitura)
- **procedimento** só executa e imprime (mostrar total)

---

## 🔍 Módulo 3 — Entendendo cada método (um por vez)

### 1) `obterFloat(Scanner teclado, String mensagem)` (função)
Responsabilidade: **mostrar uma mensagem e ler um número decimal**.

- Entrada (parâmetros):
  - `teclado` → de onde vai ler
  - `mensagem` → o que vai mostrar antes de ler
- Saída (return):
  - um `float` (ex.: `2.5`)

Detalhe importante:
- `teclado.nextLine()` depois do `nextFloat()` “limpa” a quebra de linha que fica presa, evitando leitura “bugada” na próxima entrada.

### 2) `calcularValorMaca(float qtdeMaca)` (função)
Responsabilidade: **aplicar a regra do preço da maçã**.

Regra (do jeito que o código está):
- se `qtdeMaca <= 5` → preço `1.8f` por kg
- senão → preço `1.5f` por kg

### 3) `calcularValorMorango(float qtdeMorango)` (função)
Responsabilidade: **aplicar a regra do preço do morango**.

Regra (do jeito que o código está):
- se `qtdeMorango > 5` → preço `2.2f` por kg
- senão → preço `2.5f` por kg

### 4) `mostrarValorTotal(float valorTotalMaca, float valorTotalMorango)` (procedimento)
Responsabilidade: **somar e imprimir**.

- Não retorna nada (`void`)
- Faz:
  - `totalCompra = valorTotalMaca + valorTotalMorango`
  - imprime no console

---

## 🧱 Módulo 4 — Por que tem `2.2f`, `1.8f`, `0f`?
O sufixo `f` diz ao Java: “isso é um **float**”.

Exemplo:
- `2.2` (sem `f`) é tratado como `double`
- `2.2f` é tratado como `float`

Isso evita conversões automáticas desnecessárias e deixa o tipo consistente.

---

## ⚠️ Módulo 5 — Pontos de atenção (coisas que iniciantes costumam estranhar)

1) Se o usuário digitar algo inválido em `obterFloat`, o método imprime erro e devolve `0f`.  
   Consequência: o cálculo segue, mas com `0` kg.

2) A mensagem de exemplo diz `1,5`, mas o `Scanner` normalmente aceita `1.5` dependendo da configuração regional.  
   Se a máquina estiver em um formato diferente, pode cair em `InputMismatchException`.

3) O texto “Macas” e “e” sem acento aparecem no console porque são Strings do código.  
   Em materiais didáticos, o ideal é usar “Maçãs” e “é”, mas isso é detalhe de apresentação (sem mudar a lógica).

---

## 🧠 Módulo 6 — Roteiro para reescrever sozinho (sem copiar)

Use este passo a passo para reescrever do zero:

1) Escreva só o esqueleto:
- `class Main` + `main` + `Scanner`

2) Crie as variáveis principais no `main`:
- `qtdeMaca`, `qtdeMorango`, `valorTotalMaca`, `valorTotalMorango`

3) Faça o `main` chamar uma função para ler `float` (mesmo que você ainda não tenha implementado)
- primeiro escreva a chamada, depois crie o método

4) Escreva as duas funções de cálculo (uma de cada fruta)
- comece pela regra do `if/else`
- depois coloque o `return`

5) Escreva o procedimento que soma e imprime

6) Teste com valores fáceis:
- `0` e `0`
- `5` e `5`
- `6` e `6`
- um valor com decimal (ex.: `2.5`)

---

## 🧪 Exercícios (para consolidar)

1) Sem alterar as regras, faça o programa imprimir também:
- “Maçã: R$ X”
- “Morango: R$ Y”
- “Total: R$ Z”

2) Troque o `if/else` das funções por operador ternário (o código já dá a ideia nos comentários).

3) Crie um método extra `somar(float a, float b)` que **retorne** a soma.  
   Use ele dentro de `mostrarValorTotal`.

4) Adicione validação simples:
- se o valor lido for negativo, considerar como inválido e usar `0`.

---


---

<!-- nav_start -->
---
Anterior: [88 Video Resumo Funcoes](../docs/88_Video_Resumo_Funcoes.md) | Proximo: [91 Calcular Area](../docs/91_Calcular_Area.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
