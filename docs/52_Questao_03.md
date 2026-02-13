# ✅ Respostas — Expressões Lógicas (Java)

---

## 1) “tenhoOvos ou o preço dos ovos que faltam para completar 5 é menor que o dinheiro que tenho.”

✅ Alternativa correta:

`tenhoOvos || (((5 - qtdeOvosQueTenho) * precoOvo) < dinheiroQueTenho)`

---

## 2) “tenhoOvos e tenhoFarinha e fornoLigado”

✅ Alternativa correta:

`(tenhoOvos && tenhoFarinha && ! fornoDesligado)`

---

## 3) “notaFinalAluno está entre 30 (incluso) e 60 (não incluso) e percentualFaltas é menor a 20%”

✅ Alternativa correta:

`notaFinalAluno >= 30 && notaFinalAluno < 60 && percentualFaltas < 0.2`

---

## 4) “notaFinalAluno é maior ou igual a 60 e percentualFaltas é menor a 20%”

✅ Alternativa correta:

`(notaFinalAluno >= 60) && (percentualFaltas < 0.2)`

---

## 5) “x é maior ou igual a 90 e x é menor ou igual a 100”

✅ Alternativa correta:

`(x <= 100) && (x >= 90)`

---

## 6) “x não é igual a 90”

✅ Alternativa correta:

`x != 90`

---

## 7) “x é igual a 90 e y é menor que 12”

✅ Alternativa correta:

`(x == 90) && (y < 12)`

---

## Complemento da Lição

### 🧠 Leitura mental rápida (como “traduzir” sem travar)
- `>=` → “maior ou igual”
- `<`  → “menor que”
- `&&` → “E” (tudo precisa ser verdadeiro)
- `||` → “OU” (basta uma parte ser verdadeira)
- `!`  → “NÃO” (inverte o boolean)

---

### 🎯 Pegadinhas comuns (e por que suas respostas estão boas)
- **Intervalo “30 incluso e 60 não incluso”** vira exatamente:
  - `notaFinalAluno >= 30` e `notaFinalAluno < 60`
- **PercentualFaltas < 0.2** só faz sentido se o percentual estiver em **0–1** (ex.: 0.15 = 15%).
- **Ordem em `(x <= 100) && (x >= 90)`** está correta (a ordem não muda o resultado, mas o intervalo está bem definido).
- **Parênteses**: em `&&` e `||` eles ajudam leitura, mesmo quando não são obrigatórios.

---

### 🧩 Mini-treino (responda sem calcular demais)
Sem resolver aqui: se `notaFinalAluno = 59.9` e `percentualFaltas = 0.19`, a expressão do item **3** dá **true** ou **false**?

<!-- nav_start -->
---
Anterior: [51 Questao 02](../docs/51_Questao_02.md) | Proximo: [53 Questao 04](../docs/53_Questao_04.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
