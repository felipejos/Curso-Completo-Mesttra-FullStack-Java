# Procedimentos com Parâmetros

Considere o código abaixo:

    public class App{
        public static void main(String[] args) {
            exibirSaudacao(); // chamada do procedimento
        }
    
        // definição do procedimento
        public static void exibirSaudacao() {
            System.out.println("Olá! Seja bem-vindo ao programa!");
        }
    }

O procedimento exibir saudação, possui apenas um único comando que exibe uma saudação ao iniciar a execução do programa.

Vamos imaginar que o desemvolvedor deseja manter a exibição desta saudação separada dentro de um procedimento, mas deseja customizar o resultado apresentado com base no nome do usuário que acessou o sistema.

Vamos considerar que o desenvolvedor irá obter esta informação através do teclado da seguinte forma:

    import java.util.Scanner;
    
    public class App{
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            
            String nome;
    
            System.out.printf("Informe o seu nome:\n");
            nome = teclado.nextLine();
            
            exibirSaudacao(); // chamada do procedimento
        }
    
        // definição do procedimento
        public static void exibirSaudacao() {
            System.out.println("Olá " + nome + ", seja bem-vindo ao programa!");
        }
    }

Como a variável nome foi declarada dentro do bloco do main, ela não é acessível por outros blocos dentro do programa, desta forma dizemos que a variável nome é local ao bloco main e não pode ser visualizada fora deste bloco. Este conceito chamamos de escopo de variável.

Caso o programador queira que a mensagem exibida pelo procedimento seja: 

Olá Fulano de Tal, seja bem-vindo ao programa! 

Será necessário passarmos uma cópia do conteúdo da variável nome para dentro do procedimento. Isto é realizado através do conceito de passagem de parâmetros, algo que também já estamos utilizando à algum tempo. A passagem de parâmetro é realizada quando executamos um comando/procedimento/função que informamos um ou mais valores dentro dos parenteses como o caso abaixo:

    System.out.printf("Informe o seu nome:\n");

Note que estamos executando o printf e informamos dentro dos parenteses o texto "Informe o seu nome: \", isto significa que o printf irá receber um parametro que é o texto que deve ser exibido na tela.

Para atingirmos o mesmo objetivo com o nosso procedimento exibirSaudacao(), precisaremos preparar o procedimento para receber um parametro informado no momento da chamada do procedimento;

A sintaxe de construção de um procedimento com parametros é da seguinte forma:

    modificador tipoRetorno nomeDoProcedimento(tipoParametro1 nomeParametro1, tipoParametro2 nomeParametro2, ...) {
        // corpo do procedimento
    }

Explicando cada parte:

modificador: indica onde e como o método pode ser acessado (ex: public, private, protected).

tipoRetorno: o tipo de dado que o método devolve. Se o método não devolve nada, usamos void.

nomeDoMetodo: o nome que escolhemos (por convenção, começa com letra minúscula e usa camelCase).

tipoParametro nomeParametro: indica que o método espera receber um valor desse tipo.

A construção de um procedimento pode ser realizada sem a necessidade de informar um parametro, pode ter um parametro, ou pode ter vários parametros. Quem irá definir o comportamento do procedimento em relação ao recebimento ou não dos parametros é o desenvolvedor com base na sua necessidade.

Na caso da nossa necessidade o procedimento precisaria ser criado da seguinte forma, concentre-se principalmente nas partes destacadas de vermelho:

    import java.util.Scanner;
    
    public class App{
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);
            
            String nome;
    
            System.out.printf("Informe o seu nome:\n");
            nome = teclado.nextLine();
            
            exibirSaudacao(nome); // chamada do procedimento
        }
    
        // definição do procedimento
        public static void exibirSaudacao(String parametroNome) {
            System.out.println("Olá " + parametroNome + ", seja bem-vindo ao programa!");
        }
    }

O que fizemos foi preparar o procedimento para receber um parametro e guardá-lo em parametroNome para ser usado dentro do bloco de comandos do procedimento. Isto obriga ao realizar a chamada/execução do procedimento que é necessário realizar a passagem de algum valor para ser armazenado em parametroNome. No nosso caso ao executarmos o comando abaixo, estamos passando o conteúdo da variável nome como parametro que deverá ser armazenado na variável parametroNome do procedimento exibirSaudacao().

Faça perguntas ao chatgpt ou pesquise na internet os seguintes questionamentos:

- O nome da variável parametroNome poderia ser simplesmente nome. 

- O que acontece ser executarmos a chamada do procedimento exibirSaudacao() e não informar um parametro na chamada.

---

# Complemento da Lição

---

## 🧠 Módulo 1 — O que é um parâmetro (explicação simples)

**Parâmetro** é um “espaço” que o método cria para **receber um valor**.

Exemplo do mundo real:
- Você tem uma forma de bolo (o método).
- Você precisa colocar “massa” (o valor).
- A forma não cria a massa, ela só recebe.

No Java:
- `exibirSaudacao(String parametroNome)` cria um espaço chamado `parametroNome`
- Esse espaço vai receber o texto do nome.

---

## 🧩 Módulo 2 — Escopo (por que o `nome` não funciona no método)

A variável:

    String nome;

foi criada **dentro** do `main`.

Regra simples:
- o que nasce dentro de `{ }` só existe lá dentro

Então o método `exibirSaudacao()` não “enxerga” `nome`, porque ele está em outro bloco.

Isso é o **escopo**:
- onde a variável é visível
- onde ela pode ser usada

---

## ✅ Módulo 3 — “Passar parâmetro” na prática (passo a passo)

Quando você faz:

    exibirSaudacao(nome);

Acontece assim:

1) O Java pega o valor que está dentro de `nome` (ex.: `"Fulano"`)
2) Ele “copia” esse valor
3) Ele entrega essa cópia para o método
4) Dentro do método, essa cópia cai dentro de `parametroNome`

Ou seja:
- `nome` (no main) e `parametroNome` (no método) são variáveis diferentes
- mas `parametroNome` recebe o valor de `nome`

---

## 🧪 Atividade guiada (para você responder e fixar)

### Pergunta 1 (uma de cada vez):
No trecho abaixo, qual parte é o **argumento** (valor enviado) e qual parte é o **parâmetro** (variável que recebe)?

    exibirSaudacao(nome);

Responda assim:
- Argumento: _______
- Parâmetro: _______

---

## 📌 Respostas esperadas para os 2 questionamentos do final (sem pular o entendimento)

### 1) O nome da variável `parametroNome` poderia ser simplesmente `nome`?

Sim, poderia.

Mas existe um detalhe importante:
- Esse `nome` do método seria **outro nome** (outra variável), não o mesmo `nome` do `main`.

Exemplo mental:
- `nome` no `main` é uma pessoa
- `nome` no método é outra pessoa, com o mesmo nome (parece igual, mas é diferente)

O Java permite isso porque cada variável está em um escopo diferente.

---

### 2) O que acontece se executarmos `exibirSaudacao()` sem informar um parâmetro?

Aqui depende de como o método foi declarado.

Se o método foi declarado assim:

    public static void exibirSaudacao(String parametroNome)

Então ele **obriga** que você chame assim:

    exibirSaudacao(algumTexto);

Se você tentar chamar assim:

    exibirSaudacao();

O Java vai dar erro de compilação (erro antes de rodar), porque:
- o método pede 1 parâmetro
- e você não enviou nenhum

Exemplo do mundo real:
- é como tentar enviar uma encomenda sem colocar o endereço
- o sistema não deixa nem finalizar

---

## 🧪 Exercícios (para praticar parâmetros)

1) Crie um procedimento `exibirDobro(int n)` que imprime:
- “O dobro é: X”

2) Crie um procedimento `exibirMensagem(String texto)` que imprime o texto recebido.

3) Crie um procedimento `exibirAreaRetangulo(double largura, double altura)` que imprime a área.

---


<!-- nav_start -->
---
Anterior: [85 Procedimentos](../docs/85_Procedimentos.md) | Proximo: [87 Funcoes](../docs/87_Funcoes.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
