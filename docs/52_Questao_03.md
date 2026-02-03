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
