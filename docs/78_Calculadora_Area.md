## 🧮 Calculadora de Área de Figuras Geométricas

### ✅ O que esse programa faz?
Este programa exibe um menu com 3 figuras geométricas e calcula a **área** da figura escolhida pelo usuário:

- **1 — Círculo**
- **2 — Retângulo**
- **3 — Triângulo**

Ele usa `switch case` para decidir qual cálculo executar e `try-catch` para evitar que o programa quebre caso o usuário digite algo inválido.

---

### 💻 Código (Java)

    // Calculadora de área de Figuras Geométricas

    import java.util.Scanner;
    import java.lang.Math;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            double area;

            String mensagem = "";

            int opcao = 0;

            System.out.println("== Sistema para cálculo da área de figuras geométricas ==\n");
            System.out.println("1 - Círculo");
            System.out.println("2 - Retângulo");
            System.out.println("3 - Triângulo\n");

            try {
                System.out.print("Digite o número da opção desejada: ");
                opcao = teclado.nextInt();

                switch (opcao) {
                    case 1:
                        double raio;

                        try {
                            System.out.print("Digite o valor do raio da circunferencia em metros: ");
                            raio = teclado.nextDouble();

                            area = 3.14159 * raio * raio;
                            mensagem = "Área do círculo: " + Math.round(area);

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

---

# Complemento da Lição

---

## 🧠 Módulo 1 — Visão geral do fluxo (passo a passo do raciocínio)

1. O programa **mostra um menu** com 3 opções.
2. O usuário digita um número (1, 2 ou 3).
3. O `switch` escolhe qual “caminho” executar:
   - `case 1` → calcula área do **círculo**
   - `case 2` → calcula área do **retângulo**
   - `case 3` → calcula área do **triângulo**
4. O resultado é guardado na variável `mensagem`.
5. No final, imprime `mensagem`.

Exemplo do mundo real:
- `switch` funciona como um **porteiro**:
  - “Se você escolheu 1, vai por esta porta.”
  - “Se escolheu 2, vai por aquela.”
  - “Se escolheu 3, vai pela outra.”

---

## 🧩 Módulo 2 — Por que usar `try-catch` aqui?

Quando você usa `nextInt()` e `nextDouble()`, o Java espera **números**.

Se a pessoa digitar:
- `"abc"` em vez de `2`
- `"5,5"` em vez de `5.5` (dependendo do teclado/região)
- ou deixar em branco e apertar Enter em alguns cenários

o Java pode lançar uma exceção e o programa pode quebrar.

O `try-catch` serve para:
- **tentar** ler/rodar
- **capturar o erro** e mostrar uma mensagem amigável

---

## ⚠️ Módulo 3 — Pontos importantes do código (comportamentos reais)

### 1) `mensagem` pode ficar vazia
Se der erro no raio (case 1) ou se a opção for inválida, `mensagem` pode continuar `""`.
Mesmo assim, o programa faz:

    System.out.println(mensagem);

Resultado: imprime uma linha vazia (não quebra, mas fica “estranho”).

---

### 2) Unidades inconsistentes (metros vs metros²)
O programa fala “em metros” ao pedir valores, mas imprime:

- `"Área do retângulo: ... metros"`
- `"Área do triângulo: ... metros"`

Área é medida em **metros quadrados (m²)**.

---

### 3) Círculo: arredondamento sem unidade e sem casas decimais
No círculo:

    mensagem = "Área do círculo: " + Math.round(area);

Isso remove casas decimais e não mostra unidade.

---

## ✅ Módulo 4 — Boas práticas aplicáveis (sem mudar sua ideia)

### 1) Validar números e limpar o buffer do Scanner
Quando ocorre exceção com `Scanner`, ele pode “ficar preso” no valor inválido.
Uma prática comum é consumir a entrada inválida:

    teclado.nextLine();

(para limpar e permitir continuar lendo corretamente)

---

### 2) Padronizar saída
Deixar todas as mensagens com:
- unidade `m²`
- formatação com 2 casas decimais
- sempre imprimir algo útil

Exemplo de formato (ideia):
- `Área do retângulo: 12.50 m²`

---

## 🧪 Exercícios (iniciante, mas úteis)

1) Ajuste as mensagens finais para:
- Retângulo → `"Área do retângulo: X m²"`
- Triângulo → `"Área do triângulo: X m²"`
- Círculo → `"Área do círculo: X m²"`

2) Faça o programa não imprimir `mensagem` vazia:
- Se `mensagem` estiver `""`, imprima `"Não foi possível calcular a área."`

3) Faça o círculo imprimir com 2 casas decimais, sem arredondar inteiro.

4) Adicione uma 4ª opção:
- **4 — Quadrado**
- peça o lado
- área = lado * lado

---


<!-- nav_start -->
---
Anterior: [77 Exemplo charAt](../docs/77_Exemplo_charAt.md) | Proximo: [79 Pedra Papel Tesoura](../docs/79_Pedra_Papel_Tesoura.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
