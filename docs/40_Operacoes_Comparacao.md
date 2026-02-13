# Operações de Comparação

## Orientação rápida
- Caso a resolução do vídeo esteja baixa, aumente a resolução na barra do YouTube.

---

## Vídeo — Operações de Comparação

**Link (YouTube):**  
https://www.youtube.com/watch?v=vK6JpjMn_Eg

[![Assistir no YouTube](https://img.youtube.com/vi/vK6JpjMn_Eg/hqdefault.jpg)](https://www.youtube.com/watch?v=vK6JpjMn_Eg)

---

# Complemento da Lição

## 1) O que são “operações de comparação” (explicação simples)
Operações de comparação são comandos que **comparam dois valores** e retornam **verdadeiro (true)** ou **falso (false)**.

Você usa isso quando quer tomar decisões no código, por exemplo:
- “Se a idade for maior ou igual a 18…”
- “Se a senha digitada for igual à senha esperada…”

---

## 2) Comparadores mais usados em Java
Em Java, os principais operadores de comparação são:

- `>`  maior que
- `<`  menor que
- `>=` maior ou igual
- `<=` menor ou igual
- `==` igual (comparação)
- `!=` diferente

✅ Todos eles geram um resultado do tipo **boolean** (`true` ou `false`).

---

## 3) Exemplo bem direto (para testar no console)
    public class Main {
        public static void main(String[] args) {
            int a = 10;
            int b = 5;

            System.out.println(a > b);   // true
            System.out.println(a < b);   // false
            System.out.println(a == b);  // false
            System.out.println(a != b);  // true
            System.out.println(a >= 10); // true
            System.out.println(b <= 4);  // false
        }
    }

---

## 4) Comparação + decisão (usando `if`)
A comparação normalmente é usada dentro de um `if` (se).

    public class Main {
        public static void main(String[] args) {
            int idade = 17;

            if (idade >= 18) {
                System.out.println("Pode entrar.");
            } else {
                System.out.println("Não pode entrar.");
            }
        }
    }

---

## 5) Cuidado importante: `==` em String
Para **texto (String)**, o correto é usar `.equals(...)` em vez de `==`.

✅ Certo:
    String senhaDigitada = "123";
    String senhaCorreta = "123";

    System.out.println(senhaDigitada.equals(senhaCorreta)); // true

⚠️ Evite (pode dar resultado inesperado):
    System.out.println(senhaDigitada == senhaCorreta);

---

## 6) Exercícios rápidos (fixação)
### Exercício A — Maioridade
Crie um programa que:
- leia uma idade
- imprima `true` se for `>= 18`, senão `false`

### Exercício B — Número positivo, negativo ou zero
- leia um número inteiro
- se for `> 0` imprima “positivo”
- se for `< 0` imprima “negativo”
- senão imprima “zero”

### Exercício C — Comparação de senha
- leia uma senha (String)
- compare com `"admin123"` usando `.equals`
- imprima “acesso liberado” ou “acesso negado”

---

## 7) Checklist do que você deve sair sabendo
- [ ] Sei que comparação retorna `true` ou `false`
- [ ] Sei usar `> < >= <= == !=`
- [ ] Sei aplicar isso dentro de `if/else`
- [ ] Sei que `String` compara com `.equals()`, não com `==`

<!-- nav_start -->
---
Anterior: [39 Solucao Lista Exercicios 1](../docs/39_Solucao_Lista_Exercicios_1.md) | Proximo: [41 Entendendo Operadores Comparacao](../docs/41_Entendendo_Operadores_Comparacao.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
