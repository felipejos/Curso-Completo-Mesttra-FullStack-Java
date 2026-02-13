# charAt() — Obtendo uma posição de uma String

## O que é o método `charAt()` em Java?

O método `charAt()` é usado para pegar um caractere específico dentro de uma `String` (um texto).

---

## Como funciona

Imagine que uma `String` é como uma caixinha cheia de letras, e cada letra tem uma posição (ou índice) que começa no número **0**.

Exemplo:

    String palavra = "Java";

As posições das letras são:

| Índice | Letra |
|------:|:------|
| 0     | J     |
| 1     | a     |
| 2     | v     |
| 3     | a     |

Se quisermos pegar a letra **'v'**, usamos:

    char letra = palavra.charAt(2);
    System.out.println(letra);

✅ Saída:

    v

---

## Importante lembrar

- O **primeiro** caractere tem índice **0** (não 1!).
- Se você tentar acessar uma posição que não existe, o Java vai dar um erro chamado `StringIndexOutOfBoundsException` (que pode ser tratado via `try-catch`).

Exemplo de erro:

    String texto = "Oi";
    char c = texto.charAt(5); // ERRO! só existem posições 0 e 1

---

## Resumo

| Item | Descrição |
|---|---|
| O que faz | Pega um caractere específico dentro de uma string |
| Sintaxe | `string.charAt(posicao)` |
| Retorna | Um `char` (caractere único) |
| Índices válidos | De `0` até `string.length() - 1` |

<!-- nav_start -->
---
Anterior: [75 Resposta Lista Exercicios 06](../docs/75_Resposta_Lista_Exercicios_06.md) | Proximo: [77 Exemplo charAt](../docs/77_Exemplo_charAt.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
