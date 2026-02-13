# Jogo da Forca — Recurso de Estudo

---

## Jogo da Forca
https://www.youtube.com/watch?v=OGoLkleEGys

[![Assistir no YouTube](https://img.youtube.com/vi/OGoLkleEGys/hqdefault.jpg)](https://www.youtube.com/watch?v=OGoLkleEGys)

---

## Complemento da Lição

### Objetivo do mini-projeto
Construir um **jogo da forca** para treinar:
- **Entrada e validação de dados** (letras, repetição, limite de tentativas)
- **Laços de repetição** (o jogo roda até ganhar ou perder)
- **Condição** (acertou/errou, já tentou essa letra, acabou tentativas)
- **Estruturas de dados** (lista/conjunto de letras tentadas)
- **Strings** (revelar letras, comparar, montar a palavra “mascarada”)

---

### Regras do jogo (modelo simples)
- O jogo escolhe **uma palavra secreta**
- O jogador digita **uma letra por vez**
- Se a letra existir na palavra, ela é revelada
- Se não existir, **perde 1 tentativa**
- Vitória: quando **todas as letras** forem reveladas  
- Derrota: quando **as tentativas** chegarem a 0

---

### Checklist do que observar no vídeo
- Como ele representa a palavra escondida (ex.: `_ _ _ _`)
- Como ele armazena letras já tentadas (para bloquear repetição)
- Em que momento ele decrementa tentativas (apenas em erro “novo”)
- Como ele verifica vitória (comparando máscara vs palavra, ou contador)

---

### Passo a passo de lógica (sem código completo)
1. Defina a **palavra secreta**
2. Crie a **máscara inicial** (ex.: `_` para cada letra)
3. Crie um conjunto/lista de **letras tentadas**
4. Defina **tentativas máximas**
5. Loop principal:
   - Mostra máscara e tentativas
   - Lê uma letra
   - Valida: é 1 caractere? é letra? já foi tentada?
   - Se acertou: atualiza a máscara
   - Se errou: diminui tentativas
   - Checa vitória/derrota

---

### Exercícios rápidos (para fixar)
1. Faça a validação aceitar **somente 1 letra** (se digitar “ab”, rejeita).
2. Não descontar tentativa quando o usuário repetir uma letra já tentada.
3. Permitir palavras com **acentos** (ex.: “maçã”) ou normalizar para comparar.
4. Modo extra: aceitar o jogador tentar adivinhar a **palavra inteira** (com penalidade se errar).

---

<!-- nav_start -->
---
Anterior: [If Else: ExercÃ­cio 2](../docs/45_If_Else_Exercicio_2.md) | Próximo: [Jogo da Forca](../docs/47_Jogo_da_Forca.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

