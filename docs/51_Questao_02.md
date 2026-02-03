# âœ… Respostas â€” ExpressÃµes LÃ³gicas (Java)

---

## 1) â€œtenhoOvos ou o preÃ§o dos ovos que faltam para completar 5 Ã© menor que o dinheiro que tenho.â€

âœ… ExpressÃ£o correta:

`tenhoOvos || (((5 - qtdeOvosQueTenho) * precoOvo) < dinheiroQueTenho)`

---

## 2) Resultado de `((x + 11) != (y + 2)) || (x < 10)`

VariÃ¡veis:

    int x = 9;
    int y = 20;

CÃ¡lculo:
- (x + 11) = 9 + 11 = 20
- (y + 2) = 20 + 2 = 22
- (20 != 22) â†’ true
- (x < 10) â†’ (9 < 10) â†’ true
- true || true â†’ âœ… **true**

âœ… Resposta: **True (Verdadeiro)**

---

## 3) â€œtenhoOvos e tenhoFarinha e fornoLigadoâ€

VariÃ¡veis:

    boolean tenhoOvos;
    boolean tenhoFarinha;
    boolean fornoDesligado;

Se existe `fornoDesligado`, entÃ£o `fornoLigado` Ã© a negaÃ§Ã£o disso:

âœ… ExpressÃ£o correta:

`(tenhoOvos && tenhoFarinha && ! fornoDesligado)`

---

## 4) Resultado de `(estaFrio && estaNublado && (tenhoChocolateQuente || meuDinheiro >= 35.60))`

VariÃ¡veis:

    boolean estaFrio = true;
    boolean estaNublado = true;
    boolean tenhoChocolateQuente = false
    float meuDinheiro = 40.55;

CÃ¡lculo:
- (tenhoChocolateQuente || meuDinheiro >= 35.60)
- false || (40.55 >= 35.60) â†’ false || true â†’ true
- true && true && true â†’ âœ… true

âœ… Resposta: **True (Verdadeiro)**

---

## 5) â€œx nÃ£o Ã© igual a 90â€

âœ… ExpressÃ£o correta:

`x != 90`

---

## 6) â€œx Ã© igual a 90 e y Ã© menor que 12â€

âœ… ExpressÃ£o correta:

`(x == 90) && (y < 12)`

---

## 7) Resultado de `(estaSol || estaNublado)`

VariÃ¡veis:

    boolean estaSol = true;
    boolean estaNublado = false;

CÃ¡lculo:
- true || false â†’ âœ… true

âœ… Resposta: **True (Verdadeiro)**

---

## 8) Resultado de `(estaFrio && estaNublado && tenhoChocolateQuente)`

VariÃ¡veis:

    boolean estaFrio = true;
    boolean estaNublado = false;
    boolean tenhoChocolateQuente = true

CÃ¡lculo:
- true && false && true â†’ âœ… false

âœ… Resposta: **False (Falso)**

---

## 9) â€œx Ã© maior ou igual a 90 e x Ã© menor ou igual a 100â€

âœ… ExpressÃ£o correta:

`(x <= 100) && (x >= 90)`

---

## 10) â€œnotaFinalAluno estÃ¡ entre 30 (incluso) e 60 (nÃ£o incluso) e percentualFaltas Ã© menor a 20%â€

âœ… ExpressÃ£o correta:

`notaFinalAluno >= 30 && notaFinalAluno < 60 && percentualFaltas < 0.2`

<!-- nav_start -->
---
Anterior: [QuestÃ£o 01](../docs/50_Questao_01.md) | Próximo: [QuestÃ£o 03](../docs/52_Questao_03.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

