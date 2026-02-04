# Exemplo: Contagem de caracteres

Código para realizar a contagem de caracteres maiúsculos e minúsculos e um texto.

    public class App {

            public static void main(String[] args) {
                    // Constantes com letras
                    final String MINUSCULAS = "abcdefghijklmnopqrstuvwxyz";
                    final String MAIUSCULAS = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";

                    String texto = "ExEmPlO de StrInG CoM LeTrAs";

                    int qtdeMinusculas = 0;
                    int qtdeMaiusculas = 0;

                    for (int posicao = 0; posicao < texto.length(); posicao++) {
                            
                            char caractere = texto.charAt(posicao);
                             
                            // chamada da função para identificar se o caractere é minúsculo
                            if (ehMinuscula(caractere, MINUSCULAS)) 
                                  minusculas++;
                            // chamada da função para identificar se o caracteere é maiúsculo
                            else if (ehMaiuscula(caractere, MAIUSCULAS)) 
                                  maiusculas++;
                    }

                    System.out.println("Letras minúsculas: " + qtdeMinusculas);
                    System.out.println("Letras maiúsculas: " + qtdeMaiusculas);
            }

        // Função que verifica se um caractere está nas minúsculas
            public static boolean ehMinuscula(char c, String MINUSCULAS) {

                    // percorre cada letra da constante
                    for (int i = 0; i < MINUSCULAS.length(); i++) {

                            // compara o caractere c com a letra atual da constante
                            if (c == MINUSCULAS.charAt(i)) {
                                 return true; // encontrou
                            }
                    }

                    return false; // não encontrou
            }

            // Função que verifica se um caractere está nas maiúsculas
            public static boolean ehMaiuscula(char c, String MAIUSCULAS) {
                    //pesquise sobre o métodolo indexOf
                    //note que este código é muito mais simples em termos de uso
                    return MAIUSCULAS.indexOf(c) != -1;
            }
    }

---

## Complemento: o que esse algoritmo faz na prática

Esse código percorre o texto caractere por caractere e tenta responder 2 perguntas:

- **Esse caractere é uma letra minúscula?**
- **Se não for minúscula, ele é uma letra maiúscula?**

Se for minúscula, soma 1 na contagem de minúsculas.  
Se for maiúscula, soma 1 na contagem de maiúsculas.  
Se não for letra (espaço, número, símbolo), ele **ignora**.

---

## Complemento: atenção (tem 2 erros de variável no código)

No seu código você declarou:

- `int qtdeMinusculas = 0;`
- `int qtdeMaiusculas = 0;`

Mas na hora de incrementar você usou:

- `minusculas++;`
- `maiusculas++;`

Essas variáveis (`minusculas` e `maiusculas`) **não existem**, então o código não compila.

✅ O correto, mantendo sua lógica, seria incrementar as variáveis que existem:

- `qtdeMinusculas++;`
- `qtdeMaiusculas++;`

Ou seja, esse trecho deveria ser:

    if (ehMinuscula(caractere, MINUSCULAS)) 
          qtdeMinusculas++;
    else if (ehMaiuscula(caractere, MAIUSCULAS)) 
          qtdeMaiusculas++;

---

## Complemento: como a função `ehMinuscula` funciona (passo a passo)

A função recebe:
- o caractere atual (`c`)
- a string com todas as letras minúsculas (`MINUSCULAS`)

Depois ela:
1. percorre cada letra de `"abcdefghijklmnopqrstuvwxyz"`
2. compara se `c` é igual à letra atual
3. se achar, retorna `true`
4. se terminar o loop sem achar, retorna `false`

Isso é basicamente uma “busca manual”.

---

## Complemento: como a função `ehMaiuscula` funciona (e por que é menor)

Aqui você usou:

    return MAIUSCULAS.indexOf(c) != -1;

### O que o `indexOf` faz?
Ele procura o caractere dentro da string:
- se encontrar, retorna a posição (0, 1, 2...)
- se não encontrar, retorna `-1`

Então:
- `!= -1` significa “achou”
- `== -1` significa “não achou”

Ou seja, é a mesma ideia do `ehMinuscula`, mas em uma linha.

---

## Complemento: por que usar `else if` aqui faz sentido
Você escreveu:

- se for minúscula → conta minúscula
- senão, se for maiúscula → conta maiúscula

Isso evita contar duas vezes o mesmo caractere (o que não aconteceria, mas é uma boa prática de lógica).

---

## Complemento: melhoria conceitual (mais simples em Java)
Como você já está estudando, vale saber que o Java tem verificação pronta para isso:

- `Character.isLowerCase(c)` → minúscula
- `Character.isUpperCase(c)` → maiúscula

Mas sua abordagem atual é ótima para treinar:
- `for`
- `charAt`
- funções
- comparação de caracteres

---

<!-- nav_start -->
---
Anterior: [Exemplo: CÃ¡lculo de mÃ©dia de mÃºltiplos valores](../docs/117_Media_Multiplos_Valores.md) | Próximo: [Exemplo: Identificar o maior e o menor valor](../docs/119_Maior_Menor.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

