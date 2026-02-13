# ✅ Respostas — Expressões Lógicas (Java)

---

## 1) “tenhoOvos ou o preço dos ovos que faltam para completar 5 é menor que o dinheiro que tenho.”

✅ Expressão correta:

`tenhoOvos || (((5 - qtdeOvosQueTenho) * precoOvo) < dinheiroQueTenho)`

---

## 2) Resultado de `((x + 11) != (y + 2)) || (x < 10)`

Variáveis:

    int x = 9;
    int y = 20;

Cálculo:
- (x + 11) = 9 + 11 = 20
- (y + 2) = 20 + 2 = 22
- (20 != 22) → true
- (x < 10) → (9 < 10) → true
- true || true → ✅ **true**

✅ Resposta: **True (Verdadeiro)**

---

## 3) “tenhoOvos e tenhoFarinha e fornoLigado”

Variáveis:

    boolean tenhoOvos;
    boolean tenhoFarinha;
    boolean fornoDesligado;

Se existe `fornoDesligado`, então `fornoLigado` é a negação disso:

✅ Expressão correta:

`(tenhoOvos && tenhoFarinha && ! fornoDesligado)`

---

## 4) Resultado de `(estaFrio && estaNublado && (tenhoChocolateQuente || meuDinheiro >= 35.60))`

Variáveis:

    boolean estaFrio = true;
    boolean estaNublado = true;
    boolean tenhoChocolateQuente = false
    float meuDinheiro = 40.55;

Cálculo:
- (tenhoChocolateQuente || meuDinheiro >= 35.60)
- false || (40.55 >= 35.60) → false || true → true
- true && true && true → ✅ true

✅ Resposta: **True (Verdadeiro)**

---

## 5) “x não é igual a 90”

✅ Expressão correta:

`x != 90`

---

## 6) “x é igual a 90 e y é menor que 12”

✅ Expressão correta:

`(x == 90) && (y < 12)`

---

## 7) Resultado de `(estaSol || estaNublado)`

Variáveis:

    boolean estaSol = true;
    boolean estaNublado = false;

Cálculo:
- true || false → ✅ true

✅ Resposta: **True (Verdadeiro)**

---

## 8) Resultado de `(estaFrio && estaNublado && tenhoChocolateQuente)`

Variáveis:

    boolean estaFrio = true;
    boolean estaNublado = false;
    boolean tenhoChocolateQuente = true

Cálculo:
- true && false && true → ✅ false

✅ Resposta: **False (Falso)**

---

## 9) “x é maior ou igual a 90 e x é menor ou igual a 100”

✅ Expressão correta:

`(x <= 100) && (x >= 90)`

---

## 10) “notaFinalAluno está entre 30 (incluso) e 60 (não incluso) e percentualFaltas é menor a 20%”

✅ Expressão correta:

---

## Complemento da Lição

### Como montar o item 10 (passo a passo, sem “pular”)
Você tem **3 condições** para juntar com `&&` (E):

1) **Entre 30 (incluso) e 60 (não incluso)**  
- “30 incluso” vira: `notaFinalAluno >= 30`  
- “60 não incluso” vira: `notaFinalAluno < 60`

2) **Percentual de faltas menor que 20%**  
Aqui depende de **como você guarda o percentual** no código:
- Se `percentualFaltas` vai de **0 a 100** (ex.: 20 significa 20%) → compara com `20`
- Se `percentualFaltas` vai de **0 a 1** (ex.: 0.20 significa 20%) → compara com `0.20`

### Exercício (pra você completar)
Escreva a expressão final juntando as 3 partes com `&&`:

- Parte A: `notaFinalAluno >= 30`
- Parte B: `notaFinalAluno < 60`
- Parte C: `percentualFaltas < ...` (20 ou 0.20)

**Pergunta (responda só essa):** no seu código, `percentualFaltas` está no formato **0–100** ou **0–1**?

`notaFinalAluno >= 30 && notaFinalAluno < 60 && percentualFaltas < 0.2`

<!-- nav_start -->
---
Anterior: [50 Questao 01](../docs/50_Questao_01.md) | Proximo: [52 Questao 03](../docs/52_Questao_03.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
