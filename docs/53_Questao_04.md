# ✅ Questão 04 — Tratamento de Exceções (Java) — Terreno

---

## Código fornecido (com UTF-8 normalizado)

    // Questão 04
    // Ajuste o código para que ele NÃO seja interrompido por exceções.
    // Use try/catch para tratar valores inválidos digitados pelo usuário e quaisquer outras exceções.

    //Escreva um algoritmo que leia as dimensões de um terreno (frente e lateral).
    //Leia também o valor do metro quadrado.
    //Após as leituras, calcule a area total do terreno e o valor do terreno com base no valor do metro quadrado.
    //Caso o terreno seja um quadrado perfeito, aumente o valor do terreno em 10% pois este terreno é mais valioso.
    //Caso o terreno não seja um quadrado perfeito, de um desconto no valor total de 2%.

    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class App {

        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            try {
                int frenteMts, lateralMts;
                float valorMetroQuadrado, valorTerreno;

                System.out.print("Digite a metragem da frente do terreno: ");
                frenteMts = teclado.nextInt();

                System.out.print("Digite a metragem da lateral do terreno: ");
                lateralMts = teclado.nextInt();

                System.out.print("Digite o valor do metro quadrado: ");
                valorMetroQuadrado = teclado.nextFloat();

                // calculando o valor do terreno
                valorTerreno = frenteMts * lateralMts * valorMetroQuadrado;

                // estrutura de decisão composta
                if (frenteMts == lateralMts) { // condicao para ver se é um quadrado
                    // este bloco é executado se a condição (frenteMts == lateralMts) for verdadeira
                    // que o valor do terreno seja acrescido em 10%
                    valorTerreno = (valorTerreno * 1.1f);
                } else { // se nao for quadrado da um desconto
                    // este bloco é executado se a condição (frenteMts == lateralMts) for falsa
                    // que o valor do terreno seja reduzido em 2%
                    valorTerreno = (valorTerreno * 0.98f);
                }

                System.out.printf("O valor do terreno é: R$ %.2f reais%n", valorTerreno);

            } catch (InputMismatchException e) {
                System.out.println("Erro: você digitou um valor inválido. Digite apenas números (inteiro para metros e decimal para valor).");
            } catch (Exception e) {
                System.out.println("Erro inesperado: ocorreu um problema durante a execução do programa.");
                e.printStackTrace();
            } finally {
                // garante que o Scanner será fechado mesmo se ocorrer exceção
                teclado.close();
            }
        }
    }

---

## Complemento da Lição

### 🧠 Por que ainda “interrompe”?
O `try/catch` do jeito atual **trata o erro**, mas **não volta a pedir o valor**. Ou seja:
- o usuário erra uma vez → cai no `catch` → imprime mensagem → termina o `main`.

Para “não ser interrompido”, você precisa que **cada leitura** tenha um “loop de tentativa”:
- errou → mostra aviso → limpa a entrada inválida → tenta de novo
- acertou → segue o programa

---

### ✅ Padrão correto (mentalidade)
- **Leitura robusta = `while` + `try/catch`**
- No `catch (InputMismatchException)` você precisa **descartar o que o usuário digitou**, senão o Scanner fica “preso” no mesmo erro.

---

### 🧩 Estrutura-base para você aplicar nas 3 entradas

#### A) Ler inteiro positivo (frente/lateral)
    int valor = 0;

    while (true) {
        try {
            System.out.print("...mensagem...");
            valor = teclado.nextInt();

            if (valor <= 0) {
                System.out.println("Erro: informe um número maior que 0.");
                continue;
            }

            break; // saiu porque deu certo
        } catch (InputMismatchException e) {
            System.out.println("Erro: digite um número inteiro (ex.: 10).");
            teclado.nextLine(); // descarta a entrada inválida
        }
    }

#### B) Ler float positivo (valor do m²)
    float valor = 0f;

    while (true) {
        try {
            System.out.print("...mensagem...");
            valor = teclado.nextFloat();

            if (valor <= 0) {
                System.out.println("Erro: informe um valor maior que 0.");
                continue;
            }

            break;
        } catch (InputMismatchException e) {
            System.out.println("Erro: digite um número decimal (ex.: 35.60).");
            teclado.nextLine(); // descarta a entrada inválida
        }
    }

---

### 🎯 Tarefa objetiva (sem pular etapa)
1) Substitua **apenas** a leitura de `frenteMts` pelo padrão A.  
2) Teste digitando: `abc` (tem que avisar e pedir de novo).  
3) Depois replique para `lateralMts` e `valorMetroQuadrado`.

---

### ✅ Observação importante (Brasil)
No Java, `nextFloat()` pode falhar se você digitar **vírgula** dependendo da Locale do Scanner.

---

**Pergunta (uma só):** quando você digita o valor do metro quadrado, você usa **vírgula** (`35,60`) ou **ponto** (`35.60`)?

<!-- nav_start -->
---
Anterior: [52 Questao 03](../docs/52_Questao_03.md) | Proximo: [54 Questao 05](../docs/54_Questao_05.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
