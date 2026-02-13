# Tipos de Dados e Intervalos de Valores

---

## Tipos de Dados e Intervalos de Valores

A tabela abaixo resume os **tipos primitivos** mais comuns em Java, mostrando **tamanho** e **intervalo de valores**.

---

## Tabela de tipos primitivos

| Tipo    | Tamanho (bits) | Valor Mínimo | Valor Máximo |
|--------|----------------:|-------------:|-------------:|
| boolean | 1  | false (0) | true (1) |
| byte    | 8  | -128 | 127 |
| short   | 16 | -32.768 | 32.767 |
| int     | 32 | -2.147.483.648 | 2.147.483.647 |
| long    | 64 | -9.223.372.036.854.775.808 | 9.223.372.036.854.775.807 |
| float   | 32 | 0,000000000000000000000000000000000000000000014 (1,4 × 10^−44) | 340.282.350.000.000.000.000.000.000.000.000.000.000.000.000 (3.4028235 × 10^38) |
| double  | 64 | 4,9 × 10^−324 | 1,7976931348623157 × 10^308 |

---

## O que são tipos primitivos?

O conceito de **tipos primitivos** refere-se aos tipos de dados mais básicos fornecidos por uma linguagem de programação.

Eles são chamados de “primitivos” porque servem como **blocos fundamentais** para construir informações mais complexas e **não são compostos por outros tipos**.

---

# Complemento da Lição

## 1) Como escolher o tipo certo (regra simples)
- **byte / short**: raros no dia a dia (usados em casos específicos de memória/arquivos).
- **int**: padrão para números inteiros (menu, id simples, contagem).
- **long**: quando pode passar do limite do int (ids enormes, timestamps, valores grandes).
- **float / double**: números com casas decimais.
  - `double` é o mais usado (mais precisão).
- **boolean**: verdadeiro/falso (validações e condições).

---

## 2) Termo técnico rápido: “bits”
**Bit** é a menor unidade de informação (0 ou 1).  
Quanto mais bits um tipo tem, **mais valores diferentes** ele consegue representar.

Exemplo do mundo real:  
Mais “dígitos” disponíveis = mais combinações possíveis.

---

## 3) Onde isso aparece no seu projeto de contatos
- `int id` → id do contato/telefone (normalmente cabe em int)
- `String ddd` / `String numero` → telefone costuma ser texto (pode ter zeros à esquerda, formatação)
- `String email` → texto
- `boolean` → flags (ex.: “contatoAtivo”, “telefonePrincipal”)

---

## 4) Exercícios rápidos (fixação)

1) Marque o tipo mais adequado:
- quantidade de contatos no sistema: `int` ou `double`?
- preço de um produto: `int` ou `double`?
- usuário está logado: `boolean` ou `String`?

2) Crie variáveis e imprima:
    int quantidade = 10;
    double preco = 19.90;
    boolean logado = true;

3) (Desafio curto) Explique em 1 frase:
Por que `double` é mais comum que `float` em projetos?

---

<!-- nav_start -->
---
Anterior: [15 Tipos Variaveis Java](../docs/15_Tipos_Variaveis_Java.md) | Proximo: [17 Atribuicao Direta](../docs/17_Atribuicao_Direta.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
