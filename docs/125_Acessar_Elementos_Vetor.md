Diferentes formas de acessar cada elemento do vetor


No código abaixo temos as formas possíveis de varrer todos os valores de um vetor.

Concentre-se na última versão utilizada for each.

import java.util.Random;

public class App {
        public static void main(String[] args) {
                int[] vetor = new int[10];
                Random random = new Random();

                for (int i = 0; i < vetor.length; i++) {
                        vetor[i] = random.nextInt(101); // valores de 0 a 100
                }

                // Exibir o vetor utilizando um loop for
                System.out.println("Valores gerados (usando for):");
                for (int i = 0; i < vetor.length; i++) {
                        System.out.println("Posição " + i + ": " + vetor[i]);
                }

                // Exibir o vetor utilizando um loop do while
                System.out.println("\nValores gerados (usando do-while):");     
                int i = 0;
                do {
                        System.out.println("Posição " + i + ": " + vetor[i]);
                        i++;
                } while (i < vetor.length);

                // Exibir o vetor utilizando um loop for each
                System.out.println("\nValores gerados (usando for-each):");     
                for (int valor : vetor) {
                        System.out.println("Valor: " + valor);  
                }
        }
}


O que é o for-each em Java?
O for-each é uma forma simplificada do laço for em Java, criado para facilitar a iteração sobre elementos de coleções e arrays. Ele permite percorrer todos os itens de uma estrutura sem precisar controlar índices manualmente, tornando o código mais legível, seguro e menos propenso a erros.

Diferente do for tradicional, onde você precisa declarar uma variável de controle como i ou pos, definir a condição de parada e realizar incrementos, o for-each cuida automaticamente desses detalhes. Assim, você pode focar apenas em acessar cada elemento. O for-each pode ser utilizado sempre que se deseja acessar todas as posições de um vetor.



Sintaxe:
for (Tipo variavel : conjunto) { 
    // código a ser executado para cada elemento 
}
Tipo: tipo do elemento armazenado no array ou coleção.

variavel: variável temporária que recebe, a cada repetição, o valor de um elemento.

conjunto: o array ou coleção sendo percorrido.



Exemplo com array:

int[] numeros = {10, 20, 30, 40}; 
for (int n : numeros) { 
     System.out.println(n); 
}
Nesse exemplo, o loop executa uma vez para cada valor do array numeros. A variável n assume, em sequência, os valores 10, 20, 30 e 40.



Limitações:
O for-each não permite:

Modificar diretamente os índices do array.

Saber em qual posição você está sem criar uma variável auxiliar.

Remover elementos de algumas coleções enquanto percorre.

---

**Complementos (para deixar mais completo e fácil de entender)**

### 1) Diferença prática entre `for`, `do-while` e `for-each` neste exemplo
No seu código, os 3 fazem a mesma coisa: **percorrer e exibir**.

- **for tradicional**  
  Você tem controle total do índice (`i`).  
  Melhor quando você precisa:
  - saber a posição
  - acessar outro vetor pelo mesmo índice (vetores “paralelos”)
  - pular posições (ex: de 2 em 2)
  - percorrer ao contrário

- **do-while**  
  Executa **pelo menos uma vez** antes de testar a condição.  
  Faz sentido quando:
  - você quer garantir que o bloco rode pelo menos 1 vez
  - a condição depende de algo que só existe depois da primeira execução

  Neste caso do vetor, funciona, mas é menos comum do que `for` ou `while`.

- **for-each (enhanced for)**  
  Mais curto e limpo quando:
  - você só precisa do **valor**
  - não precisa do índice
  - quer reduzir chance de erro (ex: índice passando do limite)

---

### 2) O for-each “copia” o valor? O que isso significa na prática?
Para **tipos primitivos** (`int`, `double`, etc.):
- a variável do for-each recebe uma **cópia** do valor daquela posição.

Então isso:
    for (int valor : vetor) {
        valor = 999;
    }
**não altera** o vetor original.

Se você quiser alterar o vetor, precisa do índice:
    for (int i = 0; i < vetor.length; i++) {
        vetor[i] = 999;
    }

Para **objetos** (ex: `String`, `Pessoa`):
- o for-each copia a **referência** (o “endereço” do objeto), não uma cópia do objeto.
- você consegue chamar métodos e alterar o estado interno do objeto (se ele for mutável)
- mas não consegue “trocar” o objeto dentro do array sem usar índice

---

### 3) Quando eu PRECISO do índice? (dica fácil de lembrar)
Você precisa do índice quando quer:
- mostrar “Posição 3”, “Posição 4”… (como você fez no `for` e `do-while`)
- comparar com outro vetor: `diasMes[i]` com `meses[i]`
- alterar valores do array: `vetor[i] = ...`
- percorrer de trás pra frente: `i = vetor.length - 1`
- pular elementos: `i += 2`

Se não tem nada disso, **for-each é a melhor opção**.

---

### 4) Como ter índice e ainda usar um estilo “limpo”
Quando você quer índice + legibilidade, use `for` com `length`:

    for (int i = 0; i < vetor.length; i++) {
        int valor = vetor[i];
        System.out.println("Posição " + i + ": " + valor);
    }

Aqui você fica com:
- índice (`i`)
- valor (`valor`)
- tudo explícito e fácil de ler

---

### 5) Erros comuns ao misturar `nextInt()` e `nextLine()` (vale ouro em exercícios)
No seu código, você só usa `Random`, então tudo ok.

Mas quando existe `Scanner`, um erro muito comum é:
- ler número com `nextInt()`
- depois tentar ler texto com `nextLine()`
- e o `nextLine()` “pula” porque sobrou uma quebra de linha

Solução clássica:
- consumir o buffer com `teclado.nextLine()` após ler número, ou
- usar sempre `nextLine()` e converter quando necessário

---

### 6) Mini comparação (bem rápida) para memorizar
- **for** → “quero controle do índice”
- **while** → “repita enquanto condição for verdadeira”
- **do-while** → “execute ao menos uma vez”
- **for-each** → “quero só os valores, do jeito mais simples”

---

<!-- nav_start -->
---
Anterior: [InicializaÃ§Ã£o de vetores](../docs/124_Inicializacao_Vetores.md) | Próximo: [Vetores bidimensionais (ou matrizes)](../docs/126_Matrizes.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

