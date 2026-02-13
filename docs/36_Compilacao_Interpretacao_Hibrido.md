# ⚙️ Compilação, Interpretação e Híbrido

---

## 📌 Tema
Neste arquivo temos a explicação da diferença entre linguagens **compiladas**, **interpretadas** e **híbridas**:

📄 Artigo:  
https://gabrielmoya.dev/posts/linguagens-compiladas-interpretadas-hibridas

---

## 🎥 Vídeo: comparação (Python vs C vs Assembly)

Neste vídeo temos a comparação do **tempo de escrita** de um código e o **tempo de execução** de um código em **Python**, **C** e **Assembly**.

https://www.youtube.com/watch?v=3PcIJKd1PKU

[![Assistir no YouTube](https://img.youtube.com/vi/3PcIJKd1PKU/hqdefault.jpg)](https://www.youtube.com/watch?v=3PcIJKd1PKU)

---

# Complemento da Lição

## 1) Ideia central (bem direta)
Você pode pensar assim:

- **Compilada** → transforma o código **antes** de rodar.
- **Interpretada** → roda o código **enquanto** lê/“interpreta”.
- **Híbrida** → mistura as duas: compila uma etapa intermediária e depois executa com ajuda de uma máquina/ambiente.

---

## 2) O que muda na prática (o que você sente como dev)
### Linguagem compilada
- Você geralmente gera um **executável** (ou algo equivalente).
- Tende a ter **execução rápida**.
- Exemplo mental: “eu monto tudo e só depois ligo a máquina”.

### Linguagem interpretada
- Você roda direto o arquivo de código (normalmente).
- Tende a ter **ciclo rápido para testar** (editar e rodar).
- Exemplo mental: “eu vou lendo a receita e cozinhando ao mesmo tempo”.

### Linguagem híbrida
- Você gera uma forma intermediária (ex.: **bytecode**) e executa em um ambiente (ex.: **VM**).
- Pode ter bom equilíbrio entre portabilidade e desempenho.

---

## 3) Exemplo que cai muito em aula: Java como híbrido (visão prática)
Fluxo típico:

- **.java** (seu código)
- **javac** compila → **.class** (bytecode)
- **JVM** executa o bytecode

E a JVM ainda pode otimizar em tempo de execução (ideia de “melhorar a performance enquanto roda”).

---

## 4) Mini-atividade (para fixar em 5 minutos)
Faça uma comparação em 3 linhas (no seu caderno):

1) “Compilada é como…”
2) “Interpretada é como…”
3) “Híbrida é como…”

---

## 5) Exercício rápido (fixação)
Classifique (sem pesquisar primeiro) e depois confira no artigo:
- Java
- Python
- C

Escreva o motivo em **uma frase** para cada.

---

## 6) Pergunta única (pra eu saber se fixou)
Quando falamos que Java é “híbrido”, qual é o nome do arquivo intermediário que o Java gera antes de executar?

---

<!-- nav_start -->
---
Anterior: [35 Video 02 Try Catch](../docs/35_Video_02_Try_Catch.md) | Proximo: [37 Codigo Exemplo Try Catch](../docs/37_Codigo_Exemplo_Try_Catch.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
