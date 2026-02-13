# 🧠 Interpretação de Expressões Lógicas (Português)

---

## ✅ Operadores de comparação

### 1) A expressão `x > y` deve ser interpretada como:
✅ **x é maior que y?**

---

### 2) A expressão `x == y` deve ser interpretada como:
✅ **x é igual a y?**

---

### 3) A expressão `x < y` deve ser interpretada como:
✅ **x é menor que y?**

---

### 4) A expressão `x >= 10` deve ser interpretada como:
✅ **x é maior ou igual a 10?**

---

### 5) A expressão `x <= 8` deve ser interpretada como:
✅ **x é menor ou igual a 8?**

---

### 6) A expressão `x != y` deve ser interpretada como:
✅ **x é diferente de y?**

---

### 7) A expressão `(x + y) > z` deve ser interpretada como:
✅ **x mais y é maior que z?**

---

### 8) A expressão `(x - y) == 2` deve ser interpretada como:
✅ **x menos y é igual a 2?**

---

### 9) A expressão `(x * y) == 80` deve ser interpretada como:
✅ **x multiplicado por y é igual a 80?**

---

### 10) A expressão `(x / y) < 1.5` deve ser interpretada como:
✅ **A divisão de x por y é menor que 1.5?**

---

### 11) A expressão `(x + y) > (z + 1)` deve ser interpretada como:
✅ **x mais y é maior que z mais 1?**

---

## 🔁 Associe a interpretação com a expressão lógica

✅ **negação de arroz ou negação de feijao**  
`(!arroz || !feijao)`

✅ **arroz e feijao**  
`(arroz && feijao)`

✅ **negação de arroz ou feijao**  
`(!arroz || feijao)`

✅ **!resultado**  
**negação do conteúdo de resultado**

✅ **(agua || refrigerante)**  
**agua ou refrigerante**

✅ **negação do resultado de arroz e feijao**  
`!(arroz && feijao)`

---

## Complemento da Lição

### 🧩 Tradução mental rápida (atalhos)
- `>`  → **maior que**
- `<`  → **menor que**
- `>=` → **maior ou igual**
- `<=` → **menor ou igual**
- `==` → **igual**
- `!=` → **diferente**
- `&&` → **E** (as duas condições precisam ser verdade)
- `||` → **OU** (basta uma condição ser verdade)
- `!`  → **NÃO / negação** (inverte: true vira false, false vira true)

---

### 🧠 Regra de ouro do `!` (negação)
- `!true`  vira `false`
- `!false` vira `true`

Exemplo do mundo real:
- `arroz = true` significa “tem arroz”
- `!arroz` significa “**não tem** arroz”

---

### ✅ Como ler expressões com parênteses
Leia **de dentro para fora**:

- `!(arroz && feijao)`  
  1) primeiro avalia `arroz && feijao` (tem os dois?)  
  2) depois nega o resultado (NÃO tem os dois)

---

### 🎯 Micro-treino (para fixar)
Imagine:
- `arroz = true`
- `feijao = false`

Tente dizer o resultado (true/false) de:
- `(!arroz || !feijao)`
- `(arroz && feijao)`
- `!(arroz && feijao)`

---

<!-- nav_start -->
---
Anterior: [48 Requisitos Forca](../docs/48_Requisitos_Forca.md) | Proximo: [51 Questao 02](../docs/51_Questao_02.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
