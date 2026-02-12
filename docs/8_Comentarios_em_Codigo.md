# 💬 Comentários em Código

---

## 💬 Comentários em Código

Neste artigo temos uma abordagem rápida e simples do motivo de utilizarmos comentários em programação.

Leia o artigo, mas **não se preocupe com o código Java em si por enquanto**. Apenas tente entender:
- **por que** comentar um código
- **como** fazer comentários

Caso tenha dúvidas em termos durante a leitura, pesquise o termo na internet ou aqui no ChatGPT.

**Exemplo:** ao se deparar com o termo **"compilador"**, pesquise no ChatGPT com o texto abaixo:

> Sou totalmente iniciante em programação, me explique sem detalhes muito profundos o que significa um compilador.

---

## 🔗 Artigo

https://comoprogramarjava.com.br/comentarios-em-java/

---

## ✅ Exemplos de comentários no Java

No Java, um comentário pode ser escrito em qualquer ponto do código. Veja os exemplos abaixo:

    //exemplo de comentario 1

    public class Main { //exemplo de comentario 2

    //exemplo de comentario 3

        public static void main(String[] args) { //exemplo de comentario 4
            System.out.print("Olá seja bem vindo: "); //exemplo de comentario 5
        }
    //exemplo de comentario 6
    }

---

# Complemento da Lição

## 1) Para que comentários realmente servem (prática)

Comentários servem para **explicar intenção e contexto**, principalmente quando:
- existe uma regra de negócio (“por que isso é assim”)
- existe uma restrição técnica (“por que não dá para fazer diferente”)
- existe risco/pegadinha (“se mexer aqui, quebra ali”)

📌 Um comentário bom ajuda um humano a entender rápido.

---

## 2) Comentário bom x comentário ruim (bem direto)

### Comentário ruim (repete o óbvio)
    i++; // incrementa i

### Comentário bom (explica o motivo)
    // Soma 1 porque o menu começa em 1 (não em 0)
    opcao++;

---

## 3) Tipos de comentário no Java (e quando usar)

### 3.1 `//` (linha)
Use para:
- observação curta
- TODO rápido

### 3.2 `/* ... */` (bloco)
Use para:
- explicação maior
- regra mais detalhada

### 3.3 `/** ... */` (JavaDoc)
Use para:
- documentar métodos/classes (IDE ajuda)

---

## 4) Exercícios rápidos (fixação)

1) Pegue um trecho do seu projeto e escreva 2 comentários:
   - 1 explicando **uma regra**
   - 1 explicando **um risco/pegadinha**
2) Reescreva um comentário “óbvio” para virar um comentário que explique **por quê**.
3) Crie um TODO real:
    - `// TODO: validar e-mail antes de salvar`

---

<!-- nav_start -->
---
Anterior: [Linguagens de Programação](../docs/7_Linguagens_de_Programacao.md) | Pr�ximo: [Comandos de entrada e saída](../docs/9_Comandos_Entrada_Saida.md) | [Voltar ao �ndice](../README.md)
<!-- nav_end -->

