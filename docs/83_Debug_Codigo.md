# Realizando o Debug de Código

---

## O que é “debug”?

A palavra **debug** vem do inglês:

- **de** = tirar  
- **bug** = erro (ou “inseto”, mas na programação significa erro no código)

Então, **debugar** significa literalmente **“tirar o erro do código”**.

---

## O que é o processo de debug?

O processo de debug é o **passo a passo** que o programador faz para **encontrar e corrigir erros** (os *bugs*) no programa.

Em vez de apenas rodar o programa e tentar adivinhar o que deu errado, o debug permite **analisar o código enquanto ele está sendo executado**.

---

## Como o debug funciona na prática?

A maioria das IDEs (como **Visual Studio Code**, **Eclipse**, **IntelliJ**, **Code::Blocks**, etc.) tem uma ferramenta de depuração (**debugger**). Com ela, você pode:

- Colocar um **ponto de parada** (*breakpoint*) em uma linha do código  
  → o programa vai **pausar exatamente ali**.

- Executar o código **passo a passo**, vendo o que acontece em cada linha.

- Ver o **valor das variáveis** naquele momento  
  → por exemplo, descobrir se alguma variável está com um **valor errado**.

- Descobrir onde o programa **“sai dos trilhos”**  
  → ou seja, **em que linha o erro começa a acontecer**.

---

## Quando utilizamos o debug?

Usamos debug quando:

- O programa **não funciona como esperado**;
- Um erro aparece e você **não entende o motivo**;
- O resultado final está **errado**, mas **não há mensagem de erro**;
- Você quer entender como o código funciona internamente  
  (muito útil ao estudar ou trabalhar em código de outras pessoas).

---

## Vídeo

Assista ao vídeo a seguir para entender na prática como fazer o processo de Debug:

- Vídeo: https://youtu.be/JGWpLPd8nho

---

# Complemento da Lição

---

## 🧠 Módulo 1 — O que o debugger faz (explicação bem simples)

Sem debug, você só vê:
- **Entrada** (o que você digitou)
- **Saída** (o que o programa mostrou)

Com debug, você consegue ver o que acontece **no meio do caminho**.

Exemplo do mundo real:
- Sem debug: você só vê o “antes e depois” de uma receita.
- Com debug: você para a receita em cada etapa e confere:
  - “colocou sal demais?”
  - “misturou errado?”
  - “o forno estava ligado?”

---

## 🧩 Módulo 2 — Conceitos principais (sem jargão)

### ✅ Breakpoint (ponto de parada)
É uma marcação que você coloca em uma linha para o programa **parar ali**.

Pense como:
- “Pausa aqui que eu quero olhar com calma.”

### ✅ Step Over (passar por cima)
Executa **a linha atual** e vai para a próxima.

Pense como:
- “Vai indo linha por linha.”

### ✅ Step Into (entrar)
Se a linha chama um método, o debugger **entra dentro do método**.

Pense como:
- “Agora eu quero ver o que acontece dentro dessa função.”

### ✅ Step Out (sair)
Termina o método atual e volta para a linha de onde ele foi chamado.

Pense como:
- “Já vi o suficiente aqui dentro, volta.”

### ✅ Watch / Variáveis (inspecionar valores)
Você vê o valor das variáveis em tempo real.

Pense como:
- “Mostra quanto vale `x` agora.”

---

## 🔎 Módulo 3 — Passo a passo prático (jeito padrão de debugar)

1) **Reproduza o erro**
- Rode o programa e faça o erro acontecer de novo.

2) **Escolha um lugar para parar**
- Coloque breakpoint em uma linha “importante”.
- Normalmente:
  - antes de um `if`
  - dentro de um `while`
  - antes de um cálculo

3) **Rode no modo Debug**
- Em vez de “Run”, use “Debug”.

4) **Ande linha por linha**
- Use Step Over para acompanhar o fluxo.

5) **Observe as variáveis**
- Veja se alguma variável está diferente do esperado.

6) **Encontre o ponto onde o valor “vira errado”**
- A linha anterior costuma ser a causa.

---

## ⚠️ Módulo 4 — Tipos de erro que o debug ajuda a achar

### 1) Erro lógico (mais comum)
O programa roda, mas dá resultado errado.

Exemplo:
- você queria somar, mas multiplicou
- a condição do `if` está ao contrário

### 2) Erro de fluxo
O programa “entra” onde não deveria.

Exemplo:
- um `if` que sempre cai no `else`
- um `while` que nunca para

### 3) Erro de dados
A variável vem errada desde o começo.

Exemplo:
- você leu uma String e tentou converter errado
- a entrada do usuário tem espaço e você não tratou

---

## ✅ Módulo 5 — Debug vs Print (System.out.println)

Muita gente começa “debugando” com prints, por exemplo:

    System.out.println("x = " + x);

Isso ajuda, mas tem limitações:
- polui o console
- você precisa ficar mudando o código
- não dá para ver tudo ao mesmo tempo

O debugger:
- mostra tudo sem alterar o código (na prática)
- permite ver o caminho exato que o programa está seguindo

Trade-off (bem direto):
- print é rápido e simples
- debugger é mais poderoso para entender o fluxo

---

## 🧪 Exercícios (para treinar debug de verdade)

1) Crie um programa que some números de 1 a 5, mas coloque um erro proposital (ex.: comece do 0).
- Use breakpoints para ver a variável somando.

2) Faça um `if` com condição errada (ex.: `>=` no lugar de `<=`).
- Debugue para ver por que ele cai no bloco errado.

3) Faça um `while` que não para (ex.: esqueça de incrementar).
- Use debug para ver por que a condição nunca muda.

---


<!-- nav_start -->
---
Anterior: [82 Conceito Bibliotecas](../docs/82_Conceito_Bibliotecas.md) | Proximo: [84 Conceito Geral Funcoes](../docs/84_Conceito_Geral_Funcoes.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
