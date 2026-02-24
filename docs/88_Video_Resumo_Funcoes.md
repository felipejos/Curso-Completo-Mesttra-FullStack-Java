## 🎥 Vídeo Resumo: Funções e Procedimentos

### ✅ Orientação
Assista ao vídeo abaixo:

- https://youtu.be/g_o0mTIEnXY

---

# Complemento da Lição

---

## 🧠 Módulo 1 — Antes de assistir: o que você precisa conseguir responder

Enquanto assiste, tente encontrar no vídeo as respostas destas perguntas:

- O que é um **procedimento** em Java?
- O que é uma **função** em Java?
- Qual é a diferença prática entre **`void`** e **retorno com `return`**?
- O que é **parâmetro** e o que é **argumento**?
- O que significa o código “sair do `main` e entrar no método” e depois “voltar”?

---

## 🧩 Módulo 2 — Mini mapa mental (para acompanhar o vídeo)

### ✅ Procedimento (método `void`)
- faz uma ação
- não devolve valor
- exemplo mental: “mostrar menu”

Estrutura:

    static void exibirMenu() {
        // faz algo
    }

Chamada:

    exibirMenu();

---

### ✅ Função (método com retorno)
- calcula/processa algo
- devolve um valor com `return`
- exemplo mental: “calcular área”

Estrutura:

    static double calcularAreaCirculo(double raio) {
        return 3.14159 * raio * raio;
    }

Chamada:

    double area = calcularAreaCirculo(2.0);

---

## 🔁 Módulo 3 — Fluxo de execução (como o programa “anda”)

Quando o Java encontra uma chamada:

    calcularAreaCirculo(2.0);

Ele faz:

1) pausa o `main`
2) entra no método
3) executa as linhas do método
4) encontra `return`
5) volta para o ponto da chamada, entregando o valor

---

## ✅ Módulo 4 — Atividade curta pós-vídeo (para fixar)

Depois de assistir, sem olhar anotações, tente escrever (em poucas palavras):

1) Procedimento é: ______________________
2) Função é: ___________________________
3) Parâmetro é: ________________________
4) Argumento é: ________________________

---

## 🧪 Exercício rápido (prático)

Crie mentalmente (ou no papel) um exemplo de cada:

- 1 procedimento `void` que imprime “Olá!”
- 1 função que recebe 2 números e retorna a soma

Objetivo: você conseguir dizer qual usa `return` e qual não usa.

---


---

<!-- nav_start -->
---
Anterior: [87 Funcoes](../docs/87_Funcoes.md) | Proximo: [90 Morangos Macas](../docs/90_Morangos_Macas.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
