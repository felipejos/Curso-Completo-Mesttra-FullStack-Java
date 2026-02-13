# ArrayList

## Introdução

ArrayList
O ArrayList é uma das classes mais utilizadas da biblioteca Java Collections Framework.
![OnlineGDB - exemplo](../images/arraylist.png)
---

## Definição sobre estruturas de dados em Java

Definição sobre estruturas de dados em Java:

https://www.devmedia.com.br/java-collections-como-utilizar-collections/18450

https://www.w3schools.com/java/java_data_structures.asp

https://www.w3schools.com/java/java_collections.asp

---

## O que é um ArrayList

Um ArrayList em Java é uma estrutura de dados da biblioteca padrão (java.util) que representa uma lista de tamanho dinâmico. Diferentemente de um array tradicional, cujo tamanho precisa ser definido no momento da criação e não pode ser alterado, o ArrayList consegue crescer e diminuir automaticamente conforme elementos são adicionados ou removidos.

---

## Relação com arrays tradicionais

Relação com arrays tradicionais

Internamente, o ArrayList utiliza um array comum para armazenar seus elementos. Ou seja, apesar de oferecer uma interface mais flexível para o programador, ele ainda depende do mesmo conceito básico de memória contígua utilizado pelos arrays em Java.

Quando um ArrayList é criado, ele possui uma capacidade inicial, que representa quantos elementos podem ser armazenados antes que seja necessário um redimensionamento. Essa capacidade não é o mesmo que o tamanho lógico da lista (quantidade de elementos realmente inseridos).

---

## Redimensionamento do array interno

Redimensionamento do array interno

O ponto-chave do funcionamento do ArrayList é o redimensionamento automático. Quando o array interno atinge sua capacidade máxima e um novo elemento é adicionado, o ArrayList realiza os seguintes passos:

1. Cria um novo array maior na memória.

2. Copia todos os elementos do array antigo para o novo.

3. Substitui o array interno antigo pelo novo.

Esse processo é transparente para o programador, mas tem um custo computacional, pois envolve alocação de memória e cópia de dados. Por isso, a adição de elementos em um ArrayList é considerada, em média, eficiente (O(1) amortizado), mas pode ocasionalmente ser mais custosa quando ocorre o redimensionamento.

---

## Crescimento da capacidade

Crescimento da capacidade

O Java não aumenta o array interno apenas em uma posição. Em geral, ele cresce de forma proporcional (aproximadamente 50% a mais da capacidade atual), reduzindo a frequência de redimensionamentos e melhorando o desempenho em operações de inserção contínua.

Além disso, o programador pode definir uma capacidade inicial ao criar o ArrayList, o que é útil quando já se sabe previamente a quantidade aproximada de elementos:

ArrayList<String> nomes = new ArrayList<>(100);

---

## Conclusão

Conclusão

Em resumo, o ArrayList é uma abstração poderosa sobre arrays tradicionais. Ele simplifica o gerenciamento de tamanho ao automatizar o redimensionamento do array interno, permitindo maior flexibilidade no desenvolvimento de aplicações. No entanto, entender que esse redimensionamento existe é fundamental para escrever código mais eficiente, especialmente em cenários com grande volume de dados ou muitas inserções.

O ArrayList armazena apenas objetos (não tipos primitivos diretamente), mantém a ordem de inserção dos elementos e permite elementos duplicados. Ele pertence ao pacote java.util e implementa a interface List.

---

## Criação de um ArrayList

Criação de um ArrayList

Para usar um ArrayList, é necessário importá-lo e definir o tipo de dados que ele irá armazenar:

import java.util.ArrayList;

ArrayList<String> nomes = new ArrayList<>();
Nesse exemplo, o ArrayList nomes armazena objetos do tipo String. O uso dos símbolos < > implementa o conceito de generics. Sem o uso deste conceito seria necessário aplicar o casting para converter o objeto para o tipo correto da variável. O exemplo abaixo descreve como seria o exemplo sem gerenerics.

import java.util.ArrayList;

ArrayList<String> nomes = new ArrayList();

nomes.add(new String("Maria"));
String p = (String) nomes.get(0); // cast obrigatório

---

## Métodos

Métodos	Descrição
add() 
Adiciona elementos ao fim da lista.
get()  
Retorna o elemento de uma posição específica.
set()
Substitui um elemento em uma determinada posição.
remove() 
Remove um elemento em uma determinada posição.
size()
Retorna a quantidade de elementos existentes na lista.

---

## Adicionando elementos

Adicionando elementos

Os elementos são adicionados com o método add():

nomes.add("Ana");
nomes.add("Carlos");
nomes.add("Ana");
Note que valores duplicados são permitidos.

---

## Acessando elementos

Acessando elementos

Os elementos são acessados por meio do índice, começando do zero, usando o método get():

System.out.println(nomes.get(0)); // Ana

---

## Alterando elementos

Alterando elementos

Para alterar um valor em uma posição específica, utiliza-se o método set():

nomes.set(1, "João");

---

## Removendo elementos

Removendo elementos

Um elemento pode ser removido pelo índice ou pelo próprio valor:

nomes.remove(0);        // remove pelo índice
nomes.remove("Ana");    // remove a primeira ocorrência do valor

---

## Tamanho do ArrayList

Tamanho do ArrayList

O método size() retorna a quantidade de elementos armazenados:

System.out.println(nomes.size());

---

## Percorrendo um ArrayList

Percorrendo um ArrayList

Uma forma comum de percorrer os elementos é usando um laço for-each:

for (String nome : nomes) {
    System.out.println(nome);
}

---

## Conclusão (final)

Conclusão

O ArrayList é ideal quando se precisa de uma estrutura flexível, com acesso rápido aos elementos por índice. No entanto, ele pode ter desempenho inferior em operações frequentes de inserção ou remoção no meio da lista, pois os elementos precisam ser reorganizados.

---
# Complemento da Lição

## 1) O que mais cai em prova (e na prática)

### Capacidade vs. tamanho
- **size()** = quantidade real de elementos.
- **capacidade** = tamanho do array interno (quantos cabem antes de redimensionar).

### Complexidade (regra mental)
- Acesso por índice é rápido.
- Inserir/remover no meio costuma ser caro.

---

## 2) Complexidade das operações (bem cobrado)

- `get(i)` → O(1)
- `set(i, valor)` → O(1)
- `add(valor)` no final → O(1) amortizado (às vezes redimensiona)
- `add(i, valor)` no meio → O(n) (desloca elementos)
- `remove(i)` no meio → O(n) (desloca elementos)
- `remove(valor)` → O(n) (procura + desloca)

---

## 3) Crescimento “~50%”: observação importante
Muitas implementações aumentam a capacidade proporcionalmente (comum algo perto de 1,5x), mas:
- isso pode variar por versão/implementação da JVM
- o que importa como conceito é: **cresce proporcionalmente para reduzir a frequência de redimensionamentos**

---

## 4) Métodos extras úteis (performance e memória)

### Definir capacidade inicial (você já citou)
    ArrayList<String> nomes = new ArrayList<>(100);

### Garantir capacidade mínima (evita vários redimensionamentos)
    import java.util.ArrayList;

    ArrayList<String> nomes = new ArrayList<>();
    nomes.ensureCapacity(1000);

### “Enxugar” capacidade após muitas remoções
    nomes.trimToSize();

---

## 5) Só objetos: autoboxing (tipos primitivos)
ArrayList não guarda `int`, `double`, etc. diretamente:
- usa `Integer`, `Double`, etc.
- isso pode aumentar uso de memória em listas enormes

---

## 6) Pegadinha clássica: `remove` com `ArrayList<Integer>`
`remove` tem duas versões:
- `remove(int index)` (por índice)
- `remove(Object o)` (por valor)

Exemplo (índice vs valor):
    import java.util.ArrayList;

    ArrayList<Integer> nums = new ArrayList<>();
    nums.add(10);
    nums.add(20);
    nums.add(30);

    nums.remove(1); // remove o índice 1 (remove 20)

Para remover o valor 1 (quando existir):
    nums.remove(Integer.valueOf(1));

---

## 7) Iteração e remoção segura (erro comum)
Remover dentro do `for-each` pode causar erro de modificação concorrente.

Forma segura com `Iterator`:
    import java.util.ArrayList;
    import java.util.Iterator;

    ArrayList<String> nomes = new ArrayList<>();
    nomes.add("Ana");
    nomes.add("Carlos");

    Iterator<String> it = nomes.iterator();
    while (it.hasNext()) {
        String nome = it.next();
        if (nome.equals("Ana")) {
            it.remove();
        }
    }

---

## 8) Exercícios rápidos (fixação)
1) Por que `add(i, valor)` no meio do ArrayList tende a ser O(n)?  
2) Explique com suas palavras a diferença entre `size()` e capacidade.  
3) Em `ArrayList<Integer>`, por que `remove(1)` pode não remover o valor 1?

---

---

<!-- nav_start -->
---
Anterior: [157 ENUM](../docs/157_ENUM.md) | Proximo: [159 Video Contatos V1](../docs/159_Video_Contatos_V1.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
