Inicialização de vetores
Inicialização de Vetores em Java
Em Java, um vetor (array) é uma estrutura de dados que armazena múltiplos valores de um mesmo tipo, organizados em posições contíguas na memória. Cada posição do vetor é acessada por um índice, que sempre começa em 0.

A inicialização de vetores é o processo de criar o array e definir seus valores iniciais, seja informando o tamanho que ele terá, seja preenchendo diretamente com os elementos desejados.

1. Inicialização declarando apenas o tamanho
A forma mais comum é criar um vetor definindo quantos elementos ele terá:

    int[] numeros = new int[5];

Nesse caso:

O vetor tem 5 posições.

Como ainda não atribuirmos valores, cada posição recebe o valor padrão do tipo — para int, o valor é 0.

Arrays podem ser definidos para armazenar qualquer tipo de valor:

int, double, short, long

float

boolean

char

Tipos referência (String, objetos)

Depois, você pode preencher manualmente:

    numeros[0] = 10; 
    numeros[1] = 20;

2. Inicialização com valores diretamente
Outra forma é já criar o vetor informando os valores, sem definir o tamanho explicitamente:

    int[] numeros = {10, 20, 30, 40};

Aqui:

O vetor automaticamente terá o tamanho 4.

Os valores já são atribuídos às posições correspondentes.

    String nome[] = {"Juca Bala", "Maria da Silva", "Marcos Paqueta"};

Aqui:

O vetor automaticamente terá o tamanho de 3.
Os valores já são atribuídos às posições correspondentes.
Isso significa que nome[0] terá o valor Juca Bala, nome[1] terá o valor Maria da Silva, nome[2] terá o valor Marcos Paqueta. 



Essa forma é prática e deixa o código mais limpo quando os valores já são conhecidos.

3. Inicialização usando new com valores
Uma variação da forma anterior é:

    int[] numeros = new int[]{10, 20, 30, 40};

Essa forma é necessária quando a inicialização ocorre separada da declaração:

    int[] numeros; 

    numeros = new int[]{10, 20, 30, 40};

4. Inicialização de vetores de objetos
Vetores também podem armazenar objetos:

    String[] nomes = new String[3];

Inicialmente, todas as posições terão null, pois são tipos referência.

Depois é possível atribuir valores:

    nomes[0] = "Ana"; 
    nomes[1] = "Carlos"; 
    nomes[2] = "Beatriz";

5. Por que a inicialização é importante?
Evita erros como NullPointerException ou acesso a posições inexistentes.

Permite controlar exatamente quanto espaço de memória será utilizado.

Garante que cada posição do vetor começa com um valor conhecido.

Exemplo de dois vetores sendo inicializados com valores. Neste código armazenamos o nome dos meses em um vetor de string e a quantidade de dias de cada mês no vetor diasMes. A relação entre o mês e a quantidade de dias é feita pelo mesmo número do índice, ou seja:

meses[0] é janeiro, diasMes[0] é 31 dias
meses[1] é fevereiro, diasMes[1] é 28 dias 
e assim sucessivamente até Dezembro, 31 dias.



public class MesesDias {
    public static void main(String[] args) {

        String[] meses = {
            "Janeiro", "Fevereiro", "Março", "Abril",
            "Maio", "Junho", "Julho", "Agosto",
            "Setembro", "Outubro", "Novembro", "Dezembro"
        };

        int[] diasMes = {31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31};

        // Exibindo os dados
        for (int i = 0; i < meses.length; i++) {
            System.out.println(meses[i] + " tem " + diasMes[i] + " dias.");
        }
    }
}

---

**Complementos (para deixar mais completo e fácil de entender)**

### 1) O que realmente “acontece” quando você inicializa um vetor
Quando você faz:

    int[] numeros = new int[5];

Você está dizendo ao Java:
- “Reserve espaço para **5 inteiros**”
- “E preencha todos com o **valor padrão** do tipo”

Ou seja, imediatamente após criar:
- `numeros[0]` até `numeros[4]` valem `0`

Isso é diferente de alguns tipos referência (como `String`), que iniciam com `null`.

---

### 2) Valores padrão por tipo (muito cobrado em prova)
Quando você cria `new tipo[tamanho]`, o Java preenche com:

- `int` → `0`
- `double` → `0.0`
- `float` → `0.0f`
- `long` → `0L`
- `short` → `0`
- `byte` → `0`
- `boolean` → `false`
- `char` → `'\u0000'` (caractere “vazio”)
- `String` e objetos → `null`

Exemplo:
    String[] nomes = new String[3];
    System.out.println(nomes[0]); // null

---

### 3) Erro comum: achar que “new String[3]” já cria 3 Strings
Na verdade ele cria:
- 3 posições **vazias** (null)
- você ainda precisa colocar um texto em cada posição

Correto:
    String[] nomes = new String[3];
    nomes[0] = "Ana";

Se tentar fazer `nomes[0].length()` antes de atribuir algo, dá `NullPointerException`.

---

### 4) Quando usar cada forma de inicialização (regra prática)
**Use `new int[5]`** quando:
- você sabe o tamanho, mas **ainda vai ler/preencher** depois (teclado, arquivo, cálculo)

**Use `{10, 20, 30}`** quando:
- os valores **já são conhecidos** no código

**Use `new int[]{...}`** quando:
- você precisa atribuir em outro ponto do código (declara primeiro, inicializa depois)

---

### 5) Ligação por índice (seu exemplo meses/dias é perfeito)
A ideia principal do seu exemplo é:
- mesmo índice → informações relacionadas

Isso é muito usado em exercícios.

Melhoria conceitual: sempre que tiver dois vetores “paralelos” (mesmo tamanho), uma boa prática é garantir que:
- ambos tenham o mesmo `length`
- e que o índice de um sempre corresponda ao índice do outro

Exemplo de validação simples:
    if (meses.length != diasMes.length) {
        System.out.println("Erro: vetores com tamanhos diferentes!");
    }

---

### 6) Forma alternativa de percorrer: for-each (quando não precisa do índice)
No seu exemplo, você usa o índice porque precisa acessar `meses[i]` e `diasMes[i]` juntos (ótimo).

Mas quando você só precisa do valor de um vetor:
    for (String mes : meses) {
        System.out.println(mes);
    }

Atenção: aqui você perde o índice, então não serve para “vetores paralelos”.

---

### 7) Checklist rápido para evitar ArrayIndexOutOfBounds
Antes de acessar `v[i]`, garanta:
- `i >= 0`
- `i < v.length`

O loop correto quase sempre é:
    for (int i = 0; i < v.length; i++) {
        // usar v[i]
    }

---

<!-- nav_start -->
---
Anterior: [123 Vetores](../docs/123_Vetores.md) | Proximo: [125 Acessar Elementos Vetor](../docs/125_Acessar_Elementos_Vetor.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
