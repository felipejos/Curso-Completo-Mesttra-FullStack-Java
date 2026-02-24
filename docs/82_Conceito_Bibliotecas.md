# 📚 Entendendo o Conceito de Bibliotecas

---

## O que é uma biblioteca?

Uma **biblioteca** (ou **library**) é um conjunto de **códigos prontos** criados por outras pessoas (ou por você mesmo) para realizar tarefas específicas.

Você **importa** essa biblioteca no seu programa e usa suas **funções, classes ou métodos** como se fossem parte do seu código.

---

## 🧩 Funções, procedimentos e métodos

Nestes dois vídeos você verá na prática o início do uso de **funções** e **procedimentos**, em Java chamados de **métodos**, escritos em um arquivo separado do nosso código principal.

**Funções e procedimentos** são trechos de códigos que escrevemos e colocamos em um bloco de comandos fora do nosso bloco `main`.

### Exemplo em Java

    public class Main{
        public static void main(String[] args) {
            //Comandos escritos
            //no bloco principal
            //de codigo main
        }

        static void procedimento1(){
            //bloco de comandos que faz
            //parte do procedmento 1
        }

        static void procedimento2(){
            //bloco de comandos que faz
            //parte do procedmento 2
        }

        static int funcao1(){
            //bloco de comandos que faz
            //parte da funcao1

            return algumresultado; //em funcoes e obrigatorio o uso do comando return
        }
    }

---

## 🎥 Assista aos dois vídeos a seguinr:

## Parte 01
https://youtu.be/27yz0ieaXTU

[![Parte 01](https://img.youtube.com/vi/27yz0ieaXTU/hqdefault.jpg)](https://youtu.be/27yz0ieaXTU)

## Parte 02
https://youtu.be/v-FfjjSIQeg

[![Parte 02](https://img.youtube.com/vi/v-FfjjSIQeg/hqdefault.jpg)](https://youtu.be/v-FfjjSIQeg)

---

# Complemento da Lição

---

## 🧠 Módulo 1 — Biblioteca em linguagem “bem do dia a dia”

Imagine que você está montando um móvel.

- Você pode **fazer suas próprias ferramentas** do zero (difícil e demorado).
- Ou pode usar uma **caixa de ferramentas pronta** (chave de fenda, martelo, etc.).

Uma **biblioteca** é essa “caixa de ferramentas” no mundo da programação:
- já vem com coisas prontas
- você só usa quando precisa

---

## 🔧 Módulo 2 — O que significa “importar” uma biblioteca?

“Importar” é dizer para o Java:

> “Java, eu quero usar ferramentas que não estão no meu arquivo agora. Traga elas para mim.”

Exemplo do mundo real:
- é como pegar um livro na estante e colocar na mesa para consultar.

No Java, isso aparece assim:

    import java.util.Scanner;

Significa:
- “Vou usar a classe `Scanner` (entrada pelo teclado) que está dentro do pacote `java.util`.”

---

## 🧩 Módulo 3 — Função vs Procedimento (explicação simples)

### ✅ Procedimento (em Java: método `void`)
- **faz uma ação**
- **não devolve um resultado**

Exemplo do mundo real:
- “imprimir um comprovante” (você faz e pronto)

Em Java:

    static void procedimento1() {
        // faz algo, mas não retorna valor
    }

### ✅ Função (em Java: método com retorno)
- **faz uma ação**
- **devolve um resultado** com `return`

Exemplo do mundo real:
- “calcular o troco” (você faz e devolve um número)

Em Java:

    static int funcao1() {
        return algumresultado;
    }

---

## 🧠 Módulo 4 — Onde os métodos ficam no Java?

No seu exemplo:
- `main()` é o “ponto de entrada” do programa.
- Outros métodos ficam **fora do main**, mas **dentro da classe**.

Regra visual:
- **Classe** é a “caixa grande”
- **main** é o “botão de iniciar”
- **métodos** são “ferramentas internas” que o `main` pode chamar

---

## ✅ Módulo 5 — Como o `main` usa um método (chamar método)

Seu exemplo mostra os métodos, mas aqui vai o raciocínio de uso (sem mudar seu conteúdo original):

1) Você cria o método:
- `static void procedimento1() { ... }`

2) Você chama dentro do `main`:
- `procedimento1();`

Exemplo mental:
- “Eu tenho uma ferramenta chamada procedimento1”
- “Agora vou usar essa ferramenta”

---

## ⚠️ Módulo 6 — Correções de escrita (sem alterar o original)

No texto original aparece:
- “a seguinr” → o correto é “a seguir”
- “procedmento” → o correto é “procedimento”
- “funcao1” → o correto em PT-BR seria “função1” (mas em código normalmente não usamos acento)
- “obrigatorio” → “obrigatório”
- “funcoes” → “funções”

Esses pontos são importantes para manter a escrita profissional em materiais didáticos.

---

## 🧪 Exercícios (para fixar)

1) Crie um **procedimento** chamado `mostrarMenu()` que só imprime:
- “1 - Jogar”
- “2 - Sair”

2) Crie uma **função** chamada `somar(int a, int b)` que retorna a soma.

3) No `main`, chame:
- `mostrarMenu();`
- `int r = somar(2, 3);`
- imprima `r`

---


<!-- nav_start -->
---
Anterior: [81 Vilao Heroi](../docs/81_Vilao_Heroi.md) | Proximo: [83 Debug Codigo](../docs/83_Debug_Codigo.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
