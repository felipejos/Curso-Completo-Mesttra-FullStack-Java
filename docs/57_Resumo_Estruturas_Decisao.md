# Resumo Estruturas de Decisão

---

## Estrutura de Decisão Simples

**Estrutura de Decisão Simples:** Nesta estrutura nosso código consegue avaliar e executar um bloco de comandos para apenas uma única condição.

![OnlineGDB - exemplo](../images/1_decisao.png)

---

## Estrutura de Decisão Composta

**Estrutura de Decisão Composta:** Nesta estrutura nosso código consegue avaliar e executar dois blocos de comandos para duas condições.

![OnlineGDB - exemplo](../images/2_decisao.png)

---

## Estrutura de Decisão Múltipla

**Estrutura de Decisão Múltipla:** Nesta estrutura nosso código consegue avaliar e executar três blocos de comandos para cada uma das respectivas condições.

![OnlineGDB - exemplo](../images/3_decisao.png)

---

## Estruturas que não existem

### Else sem um if iniciando:

    else {
    }

### Else com uma condição se if antes:

    else (condicao) {
    }

---

## Complemento da Lição

### 🧠 Tradução rápida (em linguagem simples)
- **Simples (`if`)**: só faz algo **se** a condição for verdadeira.
- **Composta (`if/else`)**: escolhe entre **dois caminhos** (verdadeiro ou falso).
- **Múltipla (`if/else if/else`)**: escolhe entre **vários caminhos**, testando em ordem.

---

### ✅ Como fica no código (modelos)
#### 1) Simples
    if (condicao) {
        // executa se for true
    }

#### 2) Composta
    if (condicao) {
        // executa se for true
    } else {
        // executa se for false
    }

#### 3) Múltipla
    if (condicao1) {
        // true da 1
    } else if (condicao2) {
        // true da 2
    } else {
        // nenhuma foi true
    }

---

### ⚠️ Por que “else (condicao)” não existe?
Porque o `else` **já significa** “caso contrário”.  
Quem recebe condição é o `if` (ou `else if`), nunca o `else`.

✅ O correto é:
    if (condicaoA) {
    } else if (condicaoB) {
    } else {
    }

---

### 🎯 Mini-treino (bem rápido)
Transforme essas frases em estrutura:
1) “Se a nota for >= 60, aprovado.”
2) “Se a idade for >= 18, entra; senão, não entra.”
3) “Se nota >= 90 A, senão se >= 70 B, senão se >= 60 C, senão reprovado.”

---


<!-- nav_start -->
---
Anterior: [Conceito de Estruturas de DecisÃ£o](../docs/56_Conceito_Estruturas_Decisao.md) | Próximo: [VÃ­deos Sobre Estruturas de DecisÃ£o](../docs/58_Videos_Estruturas_Decisao.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

