# Operador Ternário

---

O **operador ternário** é uma forma compacta de escrever uma estrutura condicional `if-else` em Java (e em várias outras linguagens). Ele foi criado para substituir a estrutura `if else` que tem o seguinte comportamento:

---

## Exemplo usando `if/else`

    double valor;
    double desconto;

    if (valor >= 40.6) {
        desconto = 0.05;
    } else {
        desconto = 0.02;
    }

Note que neste código estamos querendo **atribuir um determinado valor** à variável `desconto` baseado em critério.  
Se o resultado for **verdadeiro** da condição atribuimos o valor `0.05`, caso contrário atribuimos o valor `0.02`.

O operador ternário só poderá ser utilizado em situações como esta, onde queremos **atribuir um valor caso verdadeiro** a uma variável ou **outro valor na mesma variável em caso falso**.

---

## O mesmo exemplo usando operador ternário

    double valor;
    double desconto;

    desconto = (valor > 40.6) ? 0.05 : 0.02;

---

## Sintaxe do operador ternário

    variavel = (expressao_a_ser_avaliada) ? resultado_quando_verdadeiro : resultado_quando_falso;

---

## Complemento da Lição

### ✅ Como “ler” o ternário em português (sem travar)
Pense assim:

    condicao ? A : B

Lê como:
- **Se** a condição for verdadeira → use **A**
- **Senão** → use **B**

Exemplo:
    desconto = (valor > 40.6) ? 0.05 : 0.02;

Lê como:
- Se `valor > 40.6`, desconto recebe `0.05`
- Senão, desconto recebe `0.02`

---

### ⚠️ Atenção ao detalhe do seu exemplo
No `if/else` você usa `valor >= 40.6`, mas no ternário ficou `valor > 40.6`.  
Para ficar exatamente igual, o ternário também deve usar `>=`.

---

### ✅ Quando usar (regra prática)
Use ternário quando:
- você quer **atribuir um valor**
- com base em **uma condição simples**
- sem precisar executar várias linhas

Exemplos típicos:
- escolher texto: `"Aprovado"` ou `"Reprovado"`
- escolher taxa: `0.10` ou `0.05`
- escolher cor/ícone/label (em UI)

---

### ❌ Quando evitar (fica confuso)
Evite quando:
- a condição é muito grande
- você tem ternário dentro de ternário (aninhado)
- você precisa executar várias ações (prints, cálculos longos, loops)

---

### 🧩 Exercícios rápidos (sem resolver por você)
1) Dado `idade`, atribua `String status` como `"Maior"` ou `"Menor"`.
2) Dado `nota`, atribua `String resultado` como `"Aprovado"` se `nota >= 60` senão `"Reprovado"`.
3) Dado `litros` e `tipo`, atribua a taxa de desconto usando ternário (um caso por combustível).

---

<!-- nav_start -->
---
Anterior: [61 Video Switch Case](../docs/61_Video_Switch_Case.md) | Proximo: [63 Video Operador Ternario](../docs/63_Video_Operador_Ternario.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
