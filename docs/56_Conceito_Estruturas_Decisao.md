# Conceito de Estruturas de Decisão

---

## Conceito de Estruturas de Decisão
https://www.youtube.com/watch?v=ii61LQyIpiI

[![Assistir no YouTube](https://img.youtube.com/vi/ii61LQyIpiI/hqdefault.jpg)](https://www.youtube.com/watch?v=ii61LQyIpiI)

    ```

---

## Complemento da Lição

### 🎯 Objetivo deste conteúdo
Entender o que são **estruturas de decisão** e por que usamos `if`, `else if` e `else` para fazer o programa “escolher caminhos”.

---

### 🧠 Ideia central (tradução simples)
Uma estrutura de decisão é a regra:

> **Se** uma condição for verdadeira, faça uma coisa; **senão**, faça outra.

Exemplos do mundo real:
- Se o usuário estiver logado → liberar página; senão → pedir login
- Se o saldo for suficiente → permitir saque; senão → negar

---

### ✅ O que uma condição precisa ter (para funcionar no `if`)
Ela precisa virar **true** ou **false** (Verdadeiro/Falso).

Exemplos de condições:
- `idade >= 18`
- `saldo > valorSaque`
- `nota >= 60`

---

### 🧩 Blocos mais comuns em Java

#### 1) `if` (um caminho)
Executa **somente** quando a condição for verdadeira.

#### 2) `if` + `else` (dois caminhos)
- `if` quando for verdadeiro
- `else` quando for falso

#### 3) `if` + `else if` + `else` (vários caminhos)
O Java testa de cima para baixo:
- executa o **primeiro** bloco que der `true`
- ignora os demais

---

### ⚠️ Dica prática para não errar `else if`
Em “faixas” (nota, IMC, idade), use uma destas estratégias:
- **do maior para o menor**, ou
- faixas exclusivas (ex.: `>= 30` e `< 60`)

---

### 🔁 Atividades rápidas (para treinar)
1) Crie uma condição que diga se `n` é **par**.
2) Crie uma condição que diga se `idade` permite entrar (ex.: `>= 1

<!-- nav_start -->
---
Anterior: [55 Teoria If Else](../docs/55_Teoria_If_Else.md) | Proximo: [57 Resumo Estruturas Decisao](../docs/57_Resumo_Estruturas_Decisao.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
