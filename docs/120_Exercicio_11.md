# Exercício 11: Leitura com repetição em caso de exceção


O código abaixo, é a classe de leitura que desenvolvemos para auxiliar nos processos de leitura de dados. No entantoa última versão, não realizava a leitura novamente de um valor caso ocorresse uma exceção.

Estude o método lerValorInteiro() para verificar a alteração realizada conforme destacado de verde. Esta modificação criou o seguinte comportamento: quando o usuário vai digitar um valor inteiro que o código está usando o método lerValorInteiro() e ele digita uma string ao invés de um dígito, ocorre uma exceção que é trada pelo Catch. Na versão anterior, o código simplesmente parava e dava a mensagem dizendo que o usuário digitou um valor inválido. Agora nesta versão, utilizamos uma estrutura de repetição do tipo Do While() para ler novamente um novo valor, e isto irá ocorrer até que o usuário digite um valor correto.

Faça agora a mesma implementação para os demais métodos: lerValorFloat(), lerValorDouble(), lerValorShort(), lerValorLong() ...

    import java.util.Scanner;

    public class Leitura {
        static Scanner teclado = new Scanner(System.in);

        static void limparBuffer() {
            if (teclado.hasNextLine()) {
                teclado.nextLine();
            }
        }

        // ---------- TIPOS NUMÉRICOS ----------

        static int lerValorInteiro(String mensagem) {
            int valor = 0;
            
            // essa variavel ira controlar se houve algum problema na leitura
            // conhecida na programacao como variavel "flag"
            boolean leituraComProblema = true;

            do {
                try {
                    System.out.print(mensagem);
                    valor = teclado.nextInt();
                    
                    leituraComProblema = false;

                } catch (Exception e) {
                    System.out.println("Valor digitado é incorreto.");
                } finally {
                    limparBuffer();
                }

            } while (leituraComProblema);

            return valor;
        }

        static float lerValorFloat(String mensagem) {
            float valor = 0;
            try {
                System.out.print(mensagem);
                valor = teclado.nextFloat();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            } finally {
                limparBuffer();
            }
            return valor;
        }

        static double lerValorDouble(String mensagem) {
            double valor = 0;
            try {
                System.out.print(mensagem);
                valor = teclado.nextDouble();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            } finally {
                limparBuffer();
            }
            return valor;
        }

        static long lerValorLong(String mensagem) {
            long valor = 0;
            try {
                System.out.print(mensagem);
                valor = teclado.nextLong();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            } finally {
                limparBuffer();
            }
            return valor;
        }

        static short lerValorShort(String mensagem) {
            short valor = 0;
            try {
                System.out.print(mensagem);
                valor = teclado.nextShort();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            } finally {
                limparBuffer();
            }
            return valor;
        }

        static byte lerValorByte(String mensagem) {
            byte valor = 0;
            try {
                System.out.print(mensagem);
                valor = teclado.nextByte();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            } finally {
                limparBuffer();
            }
            return valor;
        }

        // ---------- TIPOS TEXTUAIS ----------

        static String lerValorString(String mensagem) {
            String valor = "";
            try {
                System.out.print(mensagem);
                valor = teclado.nextLine();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            }
            return valor;
        }

        static char lerValorChar(String mensagem) {
            char valor = '\0';
            try {
                System.out.print(mensagem);
                String entrada = teclado.nextLine();
                if (entrada.length() > 0) {
                    valor = entrada.charAt(0);
                }
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            }
            return valor;
        }

        // ---------- TIPOS LÓGICOS ----------

        static boolean lerValorBoolean(String mensagem) {
            boolean valor = false;
            try {
                System.out.print(mensagem);
                valor = teclado.nextBoolean();
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto. Digite true ou false.");
            } finally {
                limparBuffer();
            }
            return valor;
        }
    }

---

## Complemento: mesma lógica do `do...while` aplicada nos outros métodos

A ideia é sempre a mesma:

- Criar uma **flag** `leituraComProblema = true`
- Tentar ler o valor dentro de um `try`
- Se deu certo: `leituraComProblema = false`
- Se deu erro: mostra mensagem e repete
- Sempre chamar `limparBuffer()` no `finally`

Abaixo está a implementação do `do...while` para os métodos que faltavam (float, double, long, short e byte).

    static float lerValorFloat(String mensagem) {
        float valor = 0f;
        boolean leituraComProblema = true;

        do {
            try {
                System.out.print(mensagem);
                valor = teclado.nextFloat();
                leituraComProblema = false;
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            } finally {
                limparBuffer();
            }
        } while (leituraComProblema);

        return valor;
    }

    static double lerValorDouble(String mensagem) {
        double valor = 0d;
        boolean leituraComProblema = true;

        do {
            try {
                System.out.print(mensagem);
                valor = teclado.nextDouble();
                leituraComProblema = false;
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            } finally {
                limparBuffer();
            }
        } while (leituraComProblema);

        return valor;
    }

    static long lerValorLong(String mensagem) {
        long valor = 0L;
        boolean leituraComProblema = true;

        do {
            try {
                System.out.print(mensagem);
                valor = teclado.nextLong();
                leituraComProblema = false;
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            } finally {
                limparBuffer();
            }
        } while (leituraComProblema);

        return valor;
    }

    static short lerValorShort(String mensagem) {
        short valor = 0;
        boolean leituraComProblema = true;

        do {
            try {
                System.out.print(mensagem);
                valor = teclado.nextShort();
                leituraComProblema = false;
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            } finally {
                limparBuffer();
            }
        } while (leituraComProblema);

        return valor;
    }

    static byte lerValorByte(String mensagem) {
        byte valor = 0;
        boolean leituraComProblema = true;

        do {
            try {
                System.out.print(mensagem);
                valor = teclado.nextByte();
                leituraComProblema = false;
            } catch (Exception e) {
                System.out.println("Valor digitado é incorreto.");
            } finally {
                limparBuffer();
            }
        } while (leituraComProblema);

        return valor;
    }

---

## Complemento: por que o `limparBuffer()` é importante aqui?

Quando dá erro ao ler um número (por exemplo, usuário digita "abc"), o `Scanner` fica “preso” nessa entrada inválida.

Se você não limpar o buffer:

- o loop vai repetir
- mas vai tentar ler de novo
- e vai encontrar a mesma entrada inválida
- e vai cair em erro infinitamente

Por isso o `finally { limparBuffer(); }` garante que, **dando certo ou errado**, a próxima tentativa começa “limpa”.

---

## Complemento: dica extra para mensagens mais específicas (opcional)

Você pode mostrar mensagens diferentes dependendo do método:

- inteiro: "Digite um número inteiro."
- double/float: "Digite um número (use vírgula ou ponto dependendo do seu sistema)."
- boolean: "Digite true ou false."

Isso melhora a experiência do usuário porque ele entende exatamente o que fazer.

---

<!-- nav_start -->
---
Anterior: [Exemplo: Identificar o maior e o menor valor](../docs/119_Maior_Menor.md) | Próximo: [Lista ExercÃ­cio 12](../docs/121_Lista_Exercicio_12.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

