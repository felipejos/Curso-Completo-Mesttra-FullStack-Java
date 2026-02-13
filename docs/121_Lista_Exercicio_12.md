# Lista Exercício 12

Questão 01: Escreva um algoritmo que leia 10 valores inteiros do usuário. Ao término da leitura, exiba quantos números pares e quantos ímpares foram lidos.



Questão 02: Escreva uma função que execute o mesmo comportamento que o método indexOf(), ou seja, a função deve receber como parametro um texto e um caractere a ser pesquisado. A função deve verificar se o caractere existe dentro da string. Caso exista, deve ser retornado a posição em que o caractere foi encontrado. Caso as string não tenha o caractere pesquisado, deve retornar o valor -1. Para a solução deste algoritmo, deve ser utilizado apenas laço e o método charAt(). 



Questão 03: A prefeitura de uma cidade fez uma pesquisa entre seus habitantes, coletando dados sobre o salário e número de filhos. A prefeitura deseja saber:  



a) média do salário da população;

b) média do número de filhos;

c) maior salário;

d) percentual de pessoas com salário até R$1.200,00.



Faça a leitura de múltiplos valores, parando somente quando o usuário responder que não deseja inserir mais informações.



Questão 04: Em uma eleição para síndico de condomínio existem quatro candidatos A, B, C e D. Os votos são informados através de códigos. Os dados utilizados para a contagem dos votos obedecem à seguinte codificação:  



- 1,2,3,4 = voto para os respectivos candidatos: Candidato A, Candidato B, Candidato C e Candidato D;

- 5 = voto nulo;

- 6 = voto em branco;



Escreva um algoritmo que simule uma urna realizando a leitura de múltiplos votos. A urna paralisa o processo de leitura quando é executado o código 102045.

Ao término da votação deve ser exibido a quantidade total de votos e o percentual em relação ao total de votos, além o candidato ganhador, caso não exista empate.



Total de Votos: x votos

Candidato A: x votos (y%)

Candidato B: x votos (y%)

Candidato C: x votos (y%)

Candidato D: x votos (y%)

Votos Nulos: x votos (y%)

Votos em Branco: x votos (y%)



Candidato Ganhador: Candidato X

---

# Complemento — soluções em Java (com foco em repetição, contadores e acumuladores)

Abaixo estão implementações **didáticas e completas** para cada questão.  
Dica geral: nesses exercícios, você vai usar muito:

- **contador** (quantas entradas foram lidas)
- **acumulador** (somar valores para depois calcular média)
- **maior/menor** (comparações durante o loop)
- **sentinela** (um código especial que encerra o loop, como `102045`)

---

## Questão 01 — Ler 10 inteiros e contar pares e ímpares

**Ideia:** usar um `for` que roda exatamente 10 vezes, e contar com `% 2`.

    import java.util.Scanner;

    public class Q01ParesImpares {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            int pares = 0;
            int impares = 0;

            for (int i = 1; i <= 10; i++) {
                System.out.print("Digite o " + i + "º número inteiro: ");
                int n = teclado.nextInt();

                if (n % 2 == 0) {
                    pares++;
                } else {
                    impares++;
                }
            }

            System.out.println("\nQuantidade de pares: " + pares);
            System.out.println("Quantidade de ímpares: " + impares);

            teclado.close();
        }
    }

---

## Questão 02 — Função tipo `indexOf()` usando `charAt()` + laço

**Regras que você definiu:**
- Recebe `String texto` e `char alvo`
- Se achar, retorna a **posição**
- Se não achar, retorna **-1**
- Usar **apenas laço e `charAt()`**

    import java.util.Scanner;

    public class Q02IndexOfManual {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            System.out.print("Digite um texto: ");
            String texto = teclado.nextLine();

            System.out.print("Digite um caractere para procurar: ");
            char alvo = teclado.nextLine().charAt(0);

            int posicao = meuIndexOf(texto, alvo);

            System.out.println("Posição encontrada: " + posicao);

            teclado.close();
        }

        static int meuIndexOf(String texto, char alvo) {
            for (int i = 0; i < texto.length(); i++) {
                if (texto.charAt(i) == alvo) {
                    return i;
                }
            }
            return -1;
        }
    }

**Observação importante:** essa função retorna a **primeira ocorrência**, exatamente como `indexOf()`.

---

## Questão 03 — Pesquisa da prefeitura (média, maior salário e percentual <= 1200)

**Ideia principal:** repetir leitura **até o usuário dizer que não quer continuar**.  
Você vai precisar de:

- `double somaSalarios`
- `int somaFilhos`
- `double maiorSalario`
- `int totalPessoas`
- `int pessoasAte1200`

Depois calcula:
- média salário = `somaSalarios / totalPessoas`
- média filhos = `somaFilhos / (double) totalPessoas`
- percentual até 1200 = `(pessoasAte1200 * 100.0) / totalPessoas`

    import java.util.Scanner;

    public class Q03PesquisaPrefeitura {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            double somaSalarios = 0.0;
            int somaFilhos = 0;

            double maiorSalario = Double.NEGATIVE_INFINITY;

            int totalPessoas = 0;
            int pessoasAte1200 = 0;

            char continuar;

            do {
                System.out.print("Informe o salário: R$ ");
                double salario = teclado.nextDouble();

                System.out.print("Informe o número de filhos: ");
                int filhos = teclado.nextInt();

                somaSalarios += salario;
                somaFilhos += filhos;
                totalPessoas++;

                if (salario > maiorSalario) {
                    maiorSalario = salario;
                }

                if (salario <= 1200.0) {
                    pessoasAte1200++;
                }

                System.out.print("Deseja inserir mais informações? (s/n): ");
                teclado.nextLine(); // limpa o ENTER pendente do nextInt/nextDouble
                continuar = teclado.nextLine().charAt(0);

            } while (continuar == 's' || continuar == 'S');

            if (totalPessoas > 0) {
                double mediaSalario = somaSalarios / totalPessoas;
                double mediaFilhos = (double) somaFilhos / totalPessoas;
                double percentualAte1200 = (pessoasAte1200 * 100.0) / totalPessoas;

                System.out.println("\n--- Resultado da Pesquisa ---");
                System.out.printf("a) Média do salário: R$ %.2f%n", mediaSalario);
                System.out.printf("b) Média do número de filhos: %.2f%n", mediaFilhos);
                System.out.printf("c) Maior salário: R$ %.2f%n", maiorSalario);
                System.out.printf("d) Percentual até R$ 1.200,00: %.2f%%%n", percentualAte1200);
            } else {
                System.out.println("Nenhuma pessoa foi cadastrada.");
            }

            teclado.close();
        }
    }

**Ponto de atenção (muito comum):** após `nextInt()`/`nextDouble()`, o `Scanner` deixa o ENTER no buffer.  
Por isso usamos `teclado.nextLine()` antes de ler o `char` com `nextLine().charAt(0)`.

---

## Questão 04 — Urna (códigos 1 a 6, encerra com 102045)

**Regras:**
- 1..4: votos candidatos A..D
- 5: nulo
- 6: branco
- 102045: encerra
- ao final: total + percentual de cada categoria + vencedor (se não empatar)

**Ideia principal:** loop que só para quando digitar a sentinela `102045`.

    import java.util.Scanner;

    public class Q04UrnaCondominio {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            int votosA = 0;
            int votosB = 0;
            int votosC = 0;
            int votosD = 0;
            int votosNulos = 0;
            int votosBrancos = 0;

            int codigo;

            System.out.println("=== URNA DO CONDOMÍNIO ===");
            System.out.println("1 - Candidato A");
            System.out.println("2 - Candidato B");
            System.out.println("3 - Candidato C");
            System.out.println("4 - Candidato D");
            System.out.println("5 - Voto nulo");
            System.out.println("6 - Voto em branco");
            System.out.println("102045 - Encerrar votação\n");

            do {
                System.out.print("Digite o código do voto: ");
                codigo = teclado.nextInt();

                if (codigo == 102045) {
                    break;
                }

                switch (codigo) {
                    case 1: votosA++; break;
                    case 2: votosB++; break;
                    case 3: votosC++; break;
                    case 4: votosD++; break;
                    case 5: votosNulos++; break;
                    case 6: votosBrancos++; break;
                    default:
                        System.out.println("Código inválido (voto descartado).");
                        break;
                }

            } while (true);

            int totalVotos = votosA + votosB + votosC + votosD + votosNulos + votosBrancos;

            System.out.println("\n--- Resultado da Votação ---");

            if (totalVotos == 0) {
                System.out.println("Total de Votos: 0 votos");
                System.out.println("Nenhum voto foi computado.");
                teclado.close();
                return;
            }

            System.out.println("Total de Votos: " + totalVotos + " votos");

            exibirLinha("Candidato A", votosA, totalVotos);
            exibirLinha("Candidato B", votosB, totalVotos);
            exibirLinha("Candidato C", votosC, totalVotos);
            exibirLinha("Candidato D", votosD, totalVotos);
            exibirLinha("Votos Nulos", votosNulos, totalVotos);
            exibirLinha("Votos em Branco", votosBrancos, totalVotos);

            // Determinar ganhador (somente se NÃO houver empate)
            int maior = votosA;
            String ganhador = "Candidato A";
            boolean empate = false;

            if (votosB > maior) {
                maior = votosB;
                ganhador = "Candidato B";
                empate = false;
            } else if (votosB == maior) {
                empate = true;
            }

            if (votosC > maior) {
                maior = votosC;
                ganhador = "Candidato C";
                empate = false;
            } else if (votosC == maior) {
                empate = true;
            }

            if (votosD > maior) {
                maior = votosD;
                ganhador = "Candidato D";
                empate = false;
            } else if (votosD == maior) {
                empate = true;
            }

            if (empate) {
                System.out.println("\nCandidato Ganhador: Empate (não há ganhador único)");
            } else {
                System.out.println("\nCandidato Ganhador: " + ganhador);
            }

            teclado.close();
        }

        static void exibirLinha(String nome, int votos, int total) {
            double percentual = (votos * 100.0) / total;
            System.out.printf("%s: %d votos (%.2f%%)%n", nome, votos, percentual);
        }
    }

**Detalhe importante:** quando aparece um código inválido (ex: 9), eu marquei como **“voto descartado”** (não entra no total).  
Se você quiser que “inválido” conte como nulo, é só somar em `votosNulos++` no `default`.

---

<!-- nav_start -->
---
Anterior: [120 Exercicio 11](../docs/120_Exercicio_11.md) | Proximo: [122 Material Daniela CV](../docs/122_Material_Daniela_CV.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
