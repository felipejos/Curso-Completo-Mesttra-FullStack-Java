Vetores bidimensionais (ou matrizes)


A linguagem Java não fornece vetores multidimensionais, mas como um vetor pode ser declarado e ter qualquer tipo de base, é possível criar vetores de vetores (de vetores etc.), alcançando assim o mesmo efeito.



A declaração de um vetor bidimensional para inteiros, de nome "dados" em Java:



int dados[][] = new int[2][4]; // matriz com 2 linhas X 4 colunas
O primeiro conjunto de colchetes [ ] define as linhas e o segundo colchetes [ ] define as colunas. No exemplo acima, são 2 linhas e 4 colunas.



As respectivas posições de cada "célula" é exibida na tabela abaixo.



dados[0][0]	dados[0][1]	dados[0][2]	dados[0][3]
dados[1][0]	dados[1][1]	dados[1][2]	dados[1][3]


Image que agora nesta matriz de 2 linhas e 4 colunas, temos os seguintes dados.



34
43
25
10
32
23
29
11


A variável dados[1][3] armazena o valor 11.

A variável dados[1][0] armazena o valor 32.

A variável dados[0][2] armazena o valor 25.



Declarando vetores bidimensionais:



1) Com expressões de criação de vetores:



int m[][] = new int[3][3]; // matriz quadrada: 3 linhas X 3 colunas


2) Declarando e inicializando:



int m[][] = { {1, 2, 3}, 
              {4, 5, 6}, 
              {7, 8, 9} 
            };
isto equivale as seguintes atribuições:



// 1ª linha:
m[0][0] = 1;
m[0][1] = 2;
m[0][2] = 3;

// 2ª linha:
m[1][0] = 4;
m[1][1] = 5;
m[1][2] = 6;

// 3ª linha:
m[2][0] = 7;
m[2][1] = 8;
m[2][2] = 9;


3) Com linhas de diferentes tamanhos:

int m[][] = new int[2][];  // cria 2 linhas

m[0] = new int[5]; // cria 5 colunas para a linha 0
m[1] = new int[3]; // cria 3 colunas para a linha 1


4) Declarando e inicializando linhas de diferentes tamanhos:



int m[][] = { 
              {1, 2}, 
              {4, 5, 6, 7, 8}, 
              {9, 10, 11} 
            };
equivale as seguintes atribuições:



// 1ª linha com duas colunas:
m[0][0] = 1;
m[0][1] = 2;

// 2ª linha com 5 colunas:
m[1][0] = 4;
m[1][1] = 5;
m[1][2] = 6;
m[1][3] = 7;
m[1][4] = 8;

// 3ª linha com 3 colunas:
m[2][0] = 9;
m[2][1] = 10;
m[2][2] = 11;
Para conhecer os tamanhos dos vetores deve-se utilizar o campo length:



a) m.length determina o número de linhas

b) m[i].length determina o número de colunas da i-ésima linha



Percorrendo vetores bidimensionais com linhas de diferentes tamanhos:



public class App {
        public static void main(String[] args) {

                int m1[][] = { 
                                {1, 2, 3, 4}, 
                                {5, 6} 
                             };

                int m2[][] = { 
                                {1, 2}, 
                                {3}, 
                                {4, 5, 6} 
                              };

                int i, j;

                System.out.printf("==== Matriz m1 ====\n");
                for (i=0; i < m1.length; i++) {
                        System.out.printf("%dª linha: ", (i+1));

                        for (j=0; j < m1[i].length; j++) {
                                System.out.printf("%d ", m1[i][j]);
                        }

                        System.out.printf("\n");
                }

                System.out.printf("\n\n==== Matriz m2 ====\n");
                
                for (i=0; i < m2.length; i++) {
                        System.out.printf("%dª linha: ", (i+1));

                        for (j=0; j < m2[i].length; j++) {
                                System.out.printf("%d ", m2[i][j]);
                        }

                        System.out.printf("\n");
                }
                System.out.printf("\n" );
        }
}
Este é o resultado impresso pelo algoritmo.



==== Matriz m1 ====

1ª linha: 1 2 3 4 

2ª linha: 5 6



==== Matriz m2 ====

1ª linha: 1 2

2ª linha: 3

3ª linha: 4 5 6

---

**Complementos (para ficar mais completo e fácil de entender)**

### 1) O que é uma “matriz” em Java de verdade?
Em Java, `int[][]` não é uma “tabela única na memória” como em algumas linguagens mais baixas.
Na prática, é:

- um **vetor de linhas** (`int[][]` → várias linhas)
- e cada linha é um **vetor de colunas** (`int[]`)

Por isso faz sentido existir matriz “torta” (linhas com tamanhos diferentes). Isso é chamado de:
- **matriz irregular** (ou “jagged array”)

---

### 2) Como visualizar `dados[linha][coluna]` (jeito simples)
Pense assim:

- primeiro índice: **qual linha**
- segundo índice: **qual coluna dentro daquela linha**

Exemplo:
- `dados[1][3]` → linha 1, coluna 3  
- `dados[0][2]` → linha 0, coluna 2

Uma forma de memorizar:
- `m[ i ][ j ]` → **i** = linha, **j** = coluna

---

### 3) Preenchendo uma matriz (padrão mais usado)
Quando você cria uma matriz “retangular” (todas as linhas iguais), o jeito padrão é usar **dois for**:

    int[][] dados = new int[2][4];

    int valor = 1;
    for (int i = 0; i < dados.length; i++) {          // linhas
        for (int j = 0; j < dados[i].length; j++) {   // colunas
            dados[i][j] = valor;
            valor++;
        }
    }

Repare que:
- `dados.length` → número de linhas
- `dados[i].length` → número de colunas da linha i

Esse é o padrão mais seguro porque funciona até em matrizes “tortas”.

---

### 4) Percorrendo e exibindo como “tabela”
Se você quiser imprimir com aparência de tabela:

    for (int i = 0; i < dados.length; i++) {
        for (int j = 0; j < dados[i].length; j++) {
            System.out.print(dados[i][j] + "\t");
        }
        System.out.println();
    }

Dica:
- `\t` (TAB) ajuda a alinhar as colunas.

---

### 5) Versão com for-each (boa para leitura, menos boa para alterar)
Para apenas **ler/imprimir**:

    for (int[] linha : dados) {
        for (int valor : linha) {
            System.out.print(valor + " ");
        }
        System.out.println();
    }

Quando usar for-each aqui?
- quando você não precisa do índice
- quando quer código mais limpo para leitura

Quando NÃO usar?
- quando precisa saber “linha i” e “coluna j”
- quando precisa alterar posições específicas com regras baseadas nos índices

---

### 6) Erros clássicos com matriz (pra você evitar)
1) **Trocar a ordem**: `m[coluna][linha]`  
   Sempre pense: `m[linha][coluna]`.

2) **Assumir colunas fixas** em matriz irregular  
   Errado (pode estourar):
       for (int j = 0; j < m[0].length; j++)
   Certo:
       for (int j = 0; j < m[i].length; j++)

3) **Achar que `m.length` é número de colunas**  
   Não. `m.length` é **linhas**.

---

### 7) Onde matrizes aparecem na vida real (pra fixar)
- tabela de notas: aluno x provas
- estoque: produto x loja
- mapa de jogo (grid): linha x coluna
- agenda: dia x horário

Sempre que você enxergar “linha e coluna”, pense em `tipo[][]`.

---

<!-- nav_start -->
---
Anterior: [125 Acessar Elementos Vetor](../docs/125_Acessar_Elementos_Vetor.md) | Proximo: [127 Menu de Escolha](../docs/127_Menu_de_Escolha.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
