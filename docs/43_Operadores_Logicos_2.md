# 🧠 Operadores Lógicos

Os operadores lógicos representam o recurso que nos permite criar expressões lógicas maiores a partir da junção de duas ou mais expressões. Para isso, aplicamos as operações lógicas:

- **E** (representado por `&&`)
- **OU** (representado por `||`)
- **NÃO / Negação** (representado por `!`)

---

## ✅ Operadores

- `&&`  
  Utilizado quando desejamos que **as duas expressões sejam verdadeiras**.

- `||`  
  Utilizado quando precisamos que **pelo menos uma** das expressões seja verdadeira.

- `!`  
  Utilizado quando precisamos realizar a **negação** de uma expressão ou variável.

---

## 📋 Tabela verdade (resumo)

| A     | B     | A && B | A \|\| B | !A    | !B    |
|------:|------:|:------:|:--------:|:-----:|:-----:|
| true  | true  | true   | true     | false | false |
| true  | false | false  | true     | false | true  |
| false | true  | false  | true     | true  | false |
| false | false | false  | false    | true  | true  |

---

## 🧪 Exemplo em Java (com explicações)

    public class Main{
        public static void main(String[] args) {
            boolean resultado;
            int a;
            int b;

            a = 10;
            b = 4;

            resultado = ((a > b) && (b != 4 ));
            // (a > b) irá produzir o resultado true pois a variável a vale 10 e 10 é maior que 4 
            // (b != 4) irá produzir o resultado false pois b vale 4 e não é diferente de 4
            // (true && false) irá produzir o resultado false pois o operador && só produz true
            // quando os dois lados da expressão forem true 
            System.out.println("Resultado: " + resultado); //Resultado: false

            resultado = ((a > b) || (b != 4 ));
            // (a > b) irá produzir o resultado true pois a variável a vale 10 e 10 é maior que 4 
            // (b != 4) irá produzir o resultado false pois b vale 4 e não é diferente de 4
            // (true || false) irá produzir o resultado true pois o operador || só produz false
            // quando os dois lados da expressão forem false
            System.out.println("Resultado: " + resultado); //Resultado: true

            resultado = !((a > b) || (b != 4 ));
            // o resultado será false pois o operador ! irá inverter o resultado de (a > b) || (b != 4 )
            System.out.println("Resultado: " + resultado); //Resultado: false
        }
    }

---

# Complemento da Lição

## 1) Como ler expressões lógicas do jeito certo (passo a passo)
Quando você vê algo como:

- `(a > b) && (b != 4)`

Leia assim:

1. **Resolva cada comparação** (parte relacional):
   - `a > b`
   - `b != 4`

2. **Substitua por `true/false`**
3. **Aplique o operador lógico** (`&&`, `||`, `!`)
4. **Veja o resultado final**

Isso evita confusão e te ajuda a “enxergar” o que o Java está fazendo.

---

## 2) Ordem de avaliação (prioridade) mais comum
Na prática, você vai usar parênteses para não ter dúvida, mas é importante saber:

1. `()` (parênteses)
2. `!` (negação)
3. Comparações (`>`, `<`, `>=`, `<=`, `==`, `!=`)
4. `&&`
5. `||`

Exemplo:
- `!A && B` → primeiro faz `!A`, depois `&&`

---

## 3) Curto-circuito (por que isso existe e por que é útil)
Java “atalha” a avaliação para economizar trabalho e evitar erros:

### `&&` (E)
Se a primeira parte já for `false`, o Java **não avalia** a segunda.
- `false && qualquerCoisa` → já é `false`

### `||` (OU)
Se a primeira parte já for `true`, o Java **não avalia** a segunda.
- `true || qualquerCoisa` → já é `true`

Exemplo que evita erro:
    if (usuario != null && usuario.isAtivo()) {
        System.out.println("Ok!");
    }

Se `usuario` for `null`, o Java não chama `usuario.isAtivo()`.

---

## 4) Exercícios rápidos (fixação)

### Exercício 1 (AND)
Crie:
- `int idade = 17;`
- `boolean temDocumento = true;`

Imprima:
- `(idade >= 18) && temDocumento`

Depois mude `idade` para `18` e veja a diferença.

---

### Exercício 2 (OR)
Crie:
- `boolean temCupom = false;`
- `boolean ehAssinante = true;`

Imprima:
- `temCupom || ehAssinante`

---

### Exercício 3 (NOT)
Crie:
- `boolean bloqueado = false;`

Imprima:
- `!bloqueado`

Depois mude `bloqueado` para `true`.

---

## 5) Erros comuns de iniciante (para evitar)
- Confundir `||` com `&&` (OU vs E)
- Esquecer parênteses e se perder na ordem
- Achar que `!` “nega só a variável” quando na verdade ele nega **a expressão inteira** se estiver assim:
  - `!(A || B)`  → nega o resultado de tudo dentro dos parênteses

<!-- nav_start -->
---
Anterior: [42 Operadores Logico](../docs/42_Operadores_Logico.md) | Proximo: [44 If Else Exercicio 1](../docs/44_If_Else_Exercicio_1.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
