# Variáveis

---

## Conteúdo

### Variáveis
https://www.youtube.com/watch?v=qAgzr8Fo6LM

[![Assistir no YouTube](https://img.youtube.com/vi/qAgzr8Fo6LM/hqdefault.jpg)](https://www.youtube.com/watch?v=qAgzr8Fo6LM)

---

<!-- nav_start -->
---
Anterior: [Diferença entre print e println](../docs/13_Print_vs_Println.md) | Próximo: [Tipos de Variáveis no JAVA](../docs/15_Tipos_Variaveis_Java.md) | [Voltar ao Índice](../README.md)

---

# Complemento da Lição

## 1) O que é uma variável (bem simples)
Uma **variável** é um “**espaço na memória**” com um **nome**, usado para guardar um valor que o programa vai usar.

### Exemplo do mundo real
Pense numa **caixinha etiquetada**:
- etiqueta: `nome`
- dentro: `"Felipe"`

---

## 2) Por que variáveis são essenciais
Sem variáveis, você não consegue:
- guardar o que o usuário digitou
- calcular (somar, comparar, validar)
- montar textos dinâmicos (ex.: “Olá, Felipe”)
- controlar decisões (if/else) e repetições (loops)

---

## 3) Passo a passo mental (como usar)
1) **Declarar**: dizer o tipo e o nome
2) **Atribuir**: colocar um valor
3) **Usar**: imprimir, comparar, calcular
4) **Atualizar**: mudar o valor quando necessário

---

## 4) Exemplo prático (estilo console)
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            System.out.print("Digite seu nome: ");
            String nome = teclado.nextLine();

            System.out.print("Digite sua idade: ");
            int idade = Integer.parseInt(teclado.nextLine());

            System.out.println("Olá, " + nome + "! Você tem " + idade + " anos.");
        }
    }

---

## 5) Erros comuns (para evitar travar)
- Misturar texto com número sem converter (ex.: ler idade como texto e tentar somar sem converter).
- Declarar e nunca usar (variável “sobrando”).
- Dar nomes genéricos demais (ex.: `a`, `x`, `teste`) quando o valor é importante.

---

## 6) Exercícios rápidos (fixação)
1) Crie 3 variáveis para um contato:
   - `nome` (texto)
   - `email` (texto)
   - `id` (número)
2) Leia essas 3 informações do usuário e imprima uma frase:
   - “Contato cadastrado: ID X - Nome Y - Email Z”
3) Atualize o `email` e imprima novamente para confirmar a mudança.

---

## 7) Pergunta única (para checar se fixou)
Quando você quer guardar o que o usuário digitou no console, você precisa **apenas imprimir** ou precisa **criar uma variável para armazenar**?

---
<!-- nav_end -->

