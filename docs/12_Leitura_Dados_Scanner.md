# Leitura de Dados com a Classe Scanner

---

## Conteúdo

## Leitura de Dados com a Classe Scanner
https://www.youtube.com/watch?v=Z6Y8zupCKfk

[![Assistir no YouTube](https://img.youtube.com/vi/Z6Y8zupCKfk/hqdefault.jpg)](https://www.youtube.com/watch?v=Z6Y8zupCKfk)

Neste vídeo da Loiane, ela está utilizando uma IDE de desenvolvimento chamada **Eclipse**. Não se preocupe com as diferenças entre a IDE Eclipse e o site **onlinegdb**, se concentre apenas na explicação do código.

Outro ponto importante: você deve ignorar a primeira linha de código onde está `package...` e alguns comentários relativos à orientação a objetos por enquanto. Iremos trabalhar esses assuntos posteriormente.

---

# Complemento da Lição

## 1) O que é a classe Scanner (simples)
A **Scanner** é uma “ferramenta” do Java para **ler dados que o usuário digita** no console.

### Exemplo do mundo real
É como um **atendente** anotando o que você fala:
- você fala (digita)
- o atendente registra (Scanner lê)

---

## 2) O padrão mínimo para usar Scanner (passo a passo)

### Passo 1 — Importar
    import java.util.Scanner;

### Passo 2 — Criar o Scanner (ligado ao teclado)
    Scanner teclado = new Scanner(System.in);

### Passo 3 — Perguntar e ler
    System.out.print("Digite seu nome: ");
    String nome = teclado.nextLine();

### Passo 4 — Mostrar o resultado
    System.out.println("Você digitou: " + nome);

---

## 3) Diferença prática entre `nextLine()` e outros métodos
- `nextLine()` lê a linha inteira (inclui espaços).
- Outros métodos como `nextInt()` leem um tipo específico (número inteiro).

📌 Regra prática para iniciante:
- Se estiver lendo **texto** (nome, endereço), use `nextLine()`.

---

## 4) Exercício rápido (fixação)
1) Faça um programa que peça:
   - nome
   - idade
   - cidade
2) No final, imprima:
   - “Nome: X | Idade: Y | Cidade: Z”

---

## 5) Pergunta única (para eu saber que fixou)
Qual método você usaria para ler um texto com espaços, como “Rua das Flores 123”?

---
<!-- nav_start -->
---
Anterior: [Comandos de entrada e saÃ­da de dados no JAVA](../docs/11_Entrada_Saida_Dados_Java.md) | Próximo: [DiferenÃ§a entre print e println](../docs/13_Print_vs_Println.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

