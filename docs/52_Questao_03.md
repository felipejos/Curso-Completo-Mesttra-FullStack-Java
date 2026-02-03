# âœ… Respostas â€” ExpressÃµes LÃ³gicas (Java)

---

## 1) â€œtenhoOvos ou o preÃ§o dos ovos que faltam para completar 5 Ã© menor que o dinheiro que tenho.â€

âœ… Alternativa correta:

`tenhoOvos || (((5 - qtdeOvosQueTenho) * precoOvo) < dinheiroQueTenho)`

---

## 2) â€œtenhoOvos e tenhoFarinha e fornoLigadoâ€

âœ… Alternativa correta:

`(tenhoOvos && tenhoFarinha && ! fornoDesligado)`

---

## 3) â€œnotaFinalAluno estÃ¡ entre 30 (incluso) e 60 (nÃ£o incluso) e percentualFaltas Ã© menor a 20%â€

âœ… Alternativa correta:

`notaFinalAluno >= 30 && notaFinalAluno < 60 && percentualFaltas < 0.2`

---

## 4) â€œnotaFinalAluno Ã© maior ou igual a 60 e percentualFaltas Ã© menor a 20%â€

âœ… Alternativa correta:

`(notaFinalAluno >= 60) && (percentualFaltas < 0.2)`

---

## 5) â€œx Ã© maior ou igual a 90 e x Ã© menor ou igual a 100â€

âœ… Alternativa correta:

`(x <= 100) && (x >= 90)`

---

## 6) â€œx nÃ£o Ã© igual a 90â€

âœ… Alternativa correta:

`x != 90`

---

## 7) â€œx Ã© igual a 90 e y Ã© menor que 12â€

âœ… Alternativa correta:

`(x == 90) && (y < 12)`

<!-- nav_start -->
---
Anterior: [QuestÃ£o 02](../docs/51_Questao_02.md) | Próximo: [QuestÃ£o 04](../docs/53_Questao_04.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

