# charAt() - Obtendo uma posição de uma String

---

## O que é o método charAt() em Java?

O método charAt() é usado para pegar um caractere específico dentro de uma String (um texto).

---

## Como funciona

Imagine que uma String é como uma caixinha cheia de letras, e cada letra tem uma posição (ou índice) que começa no número 0.

---

## Por exemplo:

String palavra = "Java";

---

## As posições das letras são:

Índice	Letra  
0	J  
1	a  
2	v  
3	a  

---

## Se quisermos pegar a letra 'v', usamos:

char letra = palavra.charAt(2);  
System.out.println(letra);

---

## Saída:

v

---

## Importante lembrar:

- O primeiro caractere tem índice 0 (não 1!).
- Se você tentar acessar uma posição que não existe, o Java vai dar um erro chamado  
  StringIndexOutOfBoundsException que pode ser tratado via try catch.

---

## Exemplo de erro:

String texto = "Oi";  
char c = texto.charAt(5); // ERRO! só existem posições 0 e 1

---

## Resumo:

O que faz	Pega um caractere específico dentro de uma string  
Sintaxe	- string.charAt(posicao)  
Retorna	- Um char (caractere único)  
Índices válidos	- De 0 até string.length() - 1  

---

# Complemento da Lição

---

## Aula em passos (raciocínio bem simples)

1. **Toda String tem posições**: a primeira letra fica no **índice 0**.
2. **Você escolhe a posição** (um número inteiro).
3. **O Java devolve exatamente 1 caractere** (tipo `char`).

Exemplo mental:
- `"Casa"`
- índices: `0=C`, `1=a`, `2=s`, `3=a`
- `charAt(2)` → `'s'`

---

## Como evitar erro (boa prática)

Antes de usar `charAt(posicao)`, verifique se a posição existe:

- A menor posição possível é `0`
- A maior posição possível é `string.length() - 1`

Exemplo:

String s = "Oi";  
int posicao = 1;  

if (posicao >= 0 && posicao < s.length()) {  
    char c = s.charAt(posicao);  
    System.out.println(c);  
} else {  
    System.out.println("Posição inválida!");  
}

---

## Tratando com try/catch (quando você quer capturar o erro)

String texto = "Oi";  

try {  
    char c = texto.charAt(5);  
    System.out.println(c);  
} catch (StringIndexOutOfBoundsException e) {  
    System.out.println("Erro: posição não existe na String.");  
}

---

## Erros comuns (e como corrigir)

- **Erro 1: achar que começa em 1**
  - `"Java".charAt(1)` não pega `J`, pega `a`.
- **Erro 2: usar índice igual ao tamanho**
  - Se `length()` é 4, o último índice é 3.
- **Erro 3: não validar posição vinda do usuário**
  - Sempre checar com `posicao < length()`.

---

## Exercícios (com foco em iniciante)

1. Crie uma String `"Banana"` e imprima:
   - a primeira letra (índice 0)
   - a última letra (usando `length() - 1`)
2. Faça um código que:
   - recebe uma String
   - recebe um número (posição)
   - imprime o caractere se a posição for válida
   - senão imprime `"Posição inválida"`
3. Com a String `"Programação"`, imprima o caractere do índice `4` e do índice `8`.

---


<!-- nav_start -->
---
Anterior: [75 Resposta Lista Exercicios 06](../docs/75_Resposta_Lista_Exercicios_06.md) | Proximo: [77 Exemplo charAt](../docs/77_Exemplo_charAt.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
