# Lista de Exercícios 1

---

## Aviso

Estes exercícios não precisam ser entregues.

---

## Exercício 01 — Terreno retangular (área e valor de venda)

Uma imobiliária vende apenas terrenos retangulares. Faça um algoritmo para imprimir a área do terreno e o valor de venda do mesmo. Para isto será necessário o usuário informar as dimensões em metros (frente e lateral) do terreno além do valor cobrado pelo metro quadrado.

**Exemplo do Resultado:**
![OnlineGDB - exemplo](../images/L1Ex1.png)

---

## Exercício 02 — Salário mínimo (quantidade de salários)

Faça um algoritmo que receba o valor do salário mínimo e o valor do salário de um funcionário, calcule e mostre a quantidade de salários mínimos que ganha esse funcionário.

**Exemplo do Resultado:**
![OnlineGDB - exemplo](../images/L1Ex2.png)

---

## Exercício 03 — Ferraduras (haras)

Faça um algoritmo para calcular quantas ferraduras são necessárias para equipar todos os cavalos comprados para um haras. O usuário devera informar a quantidade de cavalos adquiridos.

**Exemplo do Resultado:**
![OnlineGDB - exemplo](../images/L1Ex3.png)

---

## Exercício 04 — Aumento + descontos (INSS e FGTS)

Faça um algoritmo para ler o salário de um funcionário e aumentá-lo em 15%. Após o aumento, desconte 11% de INSS e 8% de FGTS. Imprima o salário inicial, o salário com o aumento, o salário final, o desconto do INSS, o desconto do FGTS e o Total de Descontos (INSS+FGTS).

**Resultado esperado:**
![OnlineGDB - exemplo](../images/L1Ex4.png)

---

## Exercício 05 — Granja Frangotech (anéis)

A granja Frangotech possui um controle automatizado de cada frango da sua produção. No pé direito do frango há um anel com um chip de identificação; no pé esquerdo são dois anéis para indicar o tipo de alimento que ele deve consumir. Sabendo que o anel com chip custa R$4,00 e o anel de alimento custa R$3,50, faça um algoritmo para calcular o gasto total da granja para marcar todos os seus frangos que deverá ser informado pelo usuário.

**Resultado esperado:**
![OnlineGDB - exemplo](../images/L1Ex5.png)

---

## Exercício 06 — Lanchonete Gostosura (ingredientes em kg)

A lanchonete Gostosura vende apenas um tipo de sanduíche, cujo recheio inclui duas fatias de queijo, uma fatia de presunto e uma rodela de hambúrguer. Sabendo que cada fatia de queijo ou presunto pesa 50 gramas, e que a rodela de hambúrguer pesa 120 gramas, faça um algoritmo em que o dono forneça a quantidade de sanduíches a fazer, e a máquina informe as quantidades (em quilos) de queijo, presunto e carne necessários para compra.

**Resultado esperado:**
![OnlineGDB - exemplo](../images/L1Ex6.png)

---

# Complemento da Lição

## 1) Roteiro padrão para resolver qualquer exercício (algoritmo)
Use este passo a passo sempre:

1. **Entradas**: o que o usuário vai digitar?
2. **Processamento**: quais contas você precisa fazer (em ordem)?
3. **Saídas**: o que você precisa imprimir no final?

Dica de organização: antes de codar, escreva 3 linhas no papel:
- Entradas:
- Processamento:
- Saídas:

---

## 2) Cuidados comuns (para não errar)

### Porcentagem (ex.: 15%, 11%, 8%)
- Transforme em decimal: `15% → 0,15`, `11% → 0,11`, `8% → 0,08`.
- Desconto normalmente é: **valor * taxa**.

### Unidades (gramas → quilos)
- 1000 gramas = 1 quilo  
- Para converter: **divida por 1000**.

### Inteiro vs decimal
- Se envolver dinheiro/peso, prefira `double` (ou `float`) para não perder casas decimais.

---

## 3) Dicas de raciocínio (sem fazer por você)

### Exercício 01
Pergunta-guia: como calcular **área de retângulo** com frente e lateral?  
Depois: como transformar **área** em **valor de venda** usando “preço por m²”?

### Exercício 02
Pergunta-guia: “quantos salários mínimos cabem dentro do salário do funcionário?”  
Isso normalmente vira uma **divisão**.

### Exercício 03
Pergunta-guia: quantas ferraduras cada cavalo usa?  
Depois: multiplique pela quantidade de cavalos.

### Exercício 04
Pergunta-guia: calcule primeiro o salário com aumento, depois calcule cada desconto com base nesse valor.  
Por fim, some os descontos e subtraia do salário com aumento.

### Exercício 05
Pergunta-guia: quantos anéis por frango existem (direito + esquerdo)?  
Depois: multiplique pelo custo de cada tipo e some tudo.

### Exercício 06
Pergunta-guia: descubra o peso por sanduíche de cada ingrediente e multiplique pela quantidade.  
No final, converta para **kg**.

---

## 4) Checklist de validação (antes de considerar pronto)
- [ ] Testei com valores pequenos (ex.: 1 unidade) para ver se faz sentido.
- [ ] Testei com valores maiores para ver se escala certo.
- [ ] Conferi se os resultados não ficaram “colados” (use espaços/labels no print).
- [ ] Conferi se as unidades estão corretas (g vs kg, R$ etc.).
- [ ] Conferi se usei o tipo certo (`int` vs `double`).

---

<!-- nav_start -->
---
Anterior: [Seu primeiro algoritmo em Java](../docs/25_Primeiro_Algoritmo_Java.md) | Próximo: [InstalaÃ§Ã£o do Java](../docs/27_Instalacao_Java.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

