# 📘 Lista de Exercícios 03 — Estruturas de Decisão

> **Objetivo:** praticar **if / else / else if**, comparações e regras de negócio simples.

---

## ✅ Exercício 01 — Média do aluno

Faça um programa para a leitura de **duas notas parciais** de um aluno.  
O programa deve **calcular a média** e apresentar:

- **"Aprovado"** → se a média for **>= 7**
- **"Reprovado"** → se a média for **< 7**
- **"Aprovado com Distinção"** → se a média for **== 10**

---

## ✅ Exercício 02 — Posto de combustível com desconto

Um posto está vendendo combustíveis com a seguinte tabela:

### Álcool
- até 20 litros → **3%** de desconto por litro  
- acima de 20 litros → **5%** de desconto por litro  

### Gasolina
- até 20 litros → **4%** de desconto por litro  
- acima de 20 litros → **6%** de desconto por litro  

### 🔎 Entrada
- número de litros vendidos  
- tipo de combustível (inteiro):
  - **1** → álcool
  - **2** → gasolina

### 💰 Preços
- gasolina: **R$ 5,50**
- álcool: **R$ 3,90**

### 🎯 Saída
- valor total a pagar, já com desconto aplicado

---

## ✅ Exercício 03 — Loja de frutas

Tabela de preços:

### Até 5 Kg
- Morango → **R$ 2,50 / Kg**
- Maçã → **R$ 1,80 / Kg**

### Acima de 5 Kg
- Morango → **R$ 2,20 / Kg**
- Maçã → **R$ 1,50 / Kg**

📌 Regra extra: se o cliente comprar  
- mais de **8 Kg** **OU**
- valor total > **R$ 25,00**  
aplicar **10% de desconto** no total.

### 🔎 Entrada
- Kg de morangos
- Kg de maçãs

### 🎯 Saída
- valor final a pagar

---

## ✅ Exercício 04 — Reajuste salarial

Receba o salário atual do colaborador e aplique aumento:

- até **R$ 280,00** (incluindo) → **20%**
- entre **R$ 280,00 e R$ 700,00** → **15%**
- entre **R$ 700,00 e R$ 1500,00** → **10%**
- acima de **R$ 1500,00** → **5%**

### 🎯 Exibir ao final
- salário antes do reajuste
- percentual aplicado
- valor do aumento
- novo salário

---

## ✅ Exercício 05 — Folha de pagamento

Faça um programa que calcule a folha de pagamento.

### 🔎 Entrada
- valor da hora
- quantidade de horas trabalhadas no mês

### 📌 Descontos
- **IR** (depende do salário bruto)
- **Sindicato**: 3%
- **FGTS**: 11% (**não desconta**, empresa deposita)

### Tabela do IR
- até **900** (inclusive) → isento
- até **1500** (inclusive) → 5%
- até **2500** (inclusive) → 10%
- acima de **2500** → 20%

### 🎯 Imprimir no formato do exemplo
QTDE de Horas Trabalhadas: 5  
Valor da hora trabalhada R$: 220.00  

  Salário Bruto: (5 * 220)        : R$ 1.100,00  
  (-) IR (5%)                              : R$       55,00  
  (-) INSS ( 10%)                      : R$     110,00  
  (-) Sindicato (3%)                 : R$        33,00  
  FGTS (11%)                           : R$     121,00  
  Total de descontos               : R$     198,00  
  Salário Liquido                      : R$     902,00  

---

## ✅ Exercício 06 — Dia da semana

Leia um número e mostre o dia correspondente:

1 - Domingo  
2 - Segunda  
3 - Terça  
4 - Quarta  
5 - Quinta  
6 - Sexta  
7 - Sábado  

Se o usuário digitar outro valor → **"valor inválido"**

---

## ✅ Exercício 07 — Conceito por média

Leia duas notas, calcule a média e mostre o conceito:

- 9 a 10 → **A**
- 7.5 a 9 → **B**
- 6 a 7.5 → **C**
- 4 a 6 → **D**
- 0 a 4 → **E**

---

## ✅ Exercício 08 — Triângulo

Receba 3 lados e verifique:

### 1) Pode ser triângulo?
Cada lado deve ser menor que a soma dos outros dois.

### 2) Tipo do triângulo
- Equilátero → 3 lados iguais
- Isósceles → 2 lados iguais
- Escaleno → 3 lados diferentes

---

## ✅ Exercício 09 — Investigação criminal

Perguntas:

1. Telefonou para a vítima?
2. Esteve no local do crime?
3. Mora perto da vítima?
4. Devia para a vítima?
5. Já trabalhou com a vítima?

Respostas:
- **1** → sim
- **0** → não

Classificação:
- 2 "sim" → **Suspeita**
- 3 ou 4 "sim" → **Cúmplice**
- 5 "sim" → **Assassino**
- caso contrário → **Inocente**

---

## ✅ Exercício 10 — Par/Ímpar e Positivo/Negativo

Leia um número e informe:

- **par ou ímpar**
- **positivo ou negativo**

Se for **0**, imprimir:
- **"O número digitado é neutro."**

Exemplos:

Digite o número: 5  
O número 5 é impar e positivo.

Digite o número: -6  
O número -6 é par e negativo.

Digite o número: 0  
O número digitado é neutro.

---

## ✅ Exercício 11 — Caixa eletrônico

O programa pergunta o valor do saque e informa quantas notas serão entregues.

Notas disponíveis:
- 1, 5, 10, 50 e 100

Regras:
- mínimo: **10**
- máximo: **600**
- não se preocupe com a quantidade de notas na máquina

Exemplos:

- 256 → 2 notas de 100, 1 de 50, 1 de 5, 1 de 1  
- 399 → 3 notas de 100, 1 de 50, 4 de 10, 1 de 5, 4 de 1  

---

## ✅ Exercício 12 — Centenas, dezenas e unidades

Leia um número inteiro menor que 1000 e imprima:

- centenas
- dezenas
- unidades

Exemplos:
- 326 = 3 centenas, 2 dezenas e 6 unidades
- 12 = 1 dezena e 2 unidades

Testar com:
326, 300, 100, 320, 310, 305, 301, 101, 311, 111, 25, 20, 10, 21, 11, 1, 7 e 16

---

## ✅ Exercício 13 — Data válida (sem bibliotecas)

Peça:
- dia
- mês
- ano

E determine se formam uma data válida.

Regras:
- não usar biblioteca adicional
- apenas estruturas de decisão
- pesquisar ano bissexto

Exemplos:

Digite o dia: 29  
Digite o mês: 02  
Digite o ano: 2016  
A data 29/02/2016 é válida

Digite o dia: 29  
Digite o mês: 02  
Digite o ano: 2017  
A data 29/02/2017 é inválida

Digite o dia: 31  
Digite o mês: 04  
Digite o ano: 2017  
A data 31/04/2017 é inválida

Digite o dia: 30  
Digite o mês: 04  
Digite o ano: 2017  
A data 30/04/2017 é válida

---

## ✅ Exercício 14 — Maior e menor

Leia **três números** e mostre:
- o **maior**
- o **menor**

---

## Complemento da Lição

### 🧭 Como atacar qualquer exercício de `if / else / else if` (sempre funciona)
1) **Entrada**: o que o usuário digita? (variáveis)
2) **Processamento**: quais contas/decisões precisam acontecer?
3) **Regras**: transforme o texto em condições (`>=`, `<`, `==`, `&&`, `||`)
4) **Saída**: o que imprimir no final?
5) **Testes**: invente 3 casos:
   - um caso “normal”
   - um caso no **limite** (ex.: exatamente 7, exatamente 20 litros, exatamente 900)
   - um caso “extremo” (ex.: valores inválidos, 0, negativos)

---

### ✅ Padrão de construção de faixas (evita erro no `else if`)
Quando for “intervalo”, use sempre duas metades:
- **incluso** → `>=`
- **não incluso** → `<`

Exemplo de “30 (incluso) e 60 (não incluso)”:
- `valor >= 30 && valor < 60`

---

### 🧩 Checklist de validação (evita bugs básicos)
- Não aceitar valores negativos quando não faz sentido (kg, litros, salário, horas).
- Tratar `0` quando o enunciado pede algo especial (ex.: exercício 10).
- Cuidado com divisão por zero (se aparecer).
- Em “OU” (||): basta **uma** regra ser verdadeira.
- Em “E” (&&): todas precisam ser verdadeiras.

---

### 🎯 Guia rápido por nível de dificuldade
- **Aquecimento:** 01, 06, 10, 14  
- **Faixas (else if):** 04, 07  
- **Regras com desconto e total:** 02, 03  
- **Mais completo (várias linhas e formato):** 05  
- **Lógica mais “algoritmo”:** 11, 12, 13

---

### 🧪 Mini-atividade (sem resolver por você)
Escolha **um** exercício e escreva só isto:
- **Entrada**
- **Saída**
- **3 condições principais** (em português mesmo)

---

<!-- nav_start -->
---
Anterior: [58 Videos Estruturas Decisao](../docs/58_Videos_Estruturas_Decisao.md) | Proximo: [60 Conceito Switch Case](../docs/60_Conceito_Switch_Case.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
