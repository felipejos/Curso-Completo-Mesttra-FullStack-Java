# 🧯 Uso do Try/Catch

---

## Uso do Try/Catch

No Java, o **tratamento de exceções** é uma maneira de lidar com erros que podem acontecer enquanto um programa está sendo executado. Erros são eventos inesperados que podem fazer o programa parar ou funcionar de forma incorreta.

Para evitar que o programa “quebre” quando um erro acontece, usamos o **tratamento de exceções** com as palavras-chave:

- `try` → **tenta** executar um trecho de código
- `catch` → **captura e trata** o erro caso ele aconteça

---

## 1) ⚠️ O que é uma Exceção?

Uma exceção é como um “alerta” que indica que algo deu errado.

✅ Exemplos comuns:
- Tentar dividir um número por **zero**
- Tentar abrir um arquivo que **não existe**
- Digitar texto quando o programa espera um **número**

Quando isso acontece, o Java **lança** (gera) uma exceção. Se você **não tratar**, o programa pode **parar a execução**.

### Exemplo (sem tratamento)

    public class Main {
        public static void main(String[] args) {
            // Tentamos fazer uma divisão
            int resultado = 10 / 0; // Isso gera uma exceção

            System.out.println("O programa continua executando...");
        }
    }

Ao executar, o programa **não termina** e aparece algo como:

    Exception in thread "main" java.lang.ArithmeticException: / by zero
        at Main.main(Main.java:13)

---

## 2) 🧪 O bloco `try`

O bloco `try` é onde você coloca o código que **pode dar erro**.

É como dizer:  
> “Vou tentar executar isso aqui, mas pode acontecer algum problema.”

    try {
        // Código que pode gerar uma exceção
        int resultado = 10 / 0; // Isso vai gerar uma exceção
    }

---

## 3) 🛠️ O bloco `catch`

Se uma exceção ocorrer dentro do `try`, o Java “pula” direto para o `catch`.

É como dizer:  
> “Se der erro, trate aqui e mostre uma mensagem.”

    try {
        int resultado = 10 / 0; // Isso vai gerar uma exceção
    } catch (Exception e) {
        // Código para lidar com a exceção
        System.out.println("Erro: Não é possível dividir por zero.");
    }

---

## 4) ✅ Exemplo completo (Try/Catch funcionando)

    public class Main {
        public static void main(String[] args) {
            try {
                // Tentamos fazer uma divisão
                int resultado = 10 / 0; // Isso gera uma exceção
            } catch (Exception e) {
                // Se ocorrer uma exceção, isso é executado
                System.out.println("Erro: Não é possível dividir por zero.");
            }

            System.out.println("O programa continua executando...");
        }
    }

📌 Execute esse exemplo e note que, mesmo com erro, o programa **continua** e imprime:

- a mensagem do `catch`
- e depois: **"O programa continua executando..."**

✅ Agora faça um teste:
- Troque o `0` por outro número (ex: `2`)
- Execute novamente
- Você verá que **não ocorre erro**, pois a divisão passa a ser válida.

---

## 🧠 O que acontece no código?

- O código dentro do `try` tenta fazer a divisão.
- Dividir por zero não é permitido → o Java lança uma exceção.
- O `catch` captura a exceção e executa o tratamento.
- O programa continua normalmente após o `catch`.

---

## 💡 Por que usar `try` e `catch`?

Usar `try/catch` deixa seu programa mais **robusto** e evita que ele “morra” ao encontrar um problema.

✅ Em vez de parar tudo, ele pode:
- mostrar uma mensagem clara para o usuário
- pedir uma nova entrada
- continuar o fluxo do sistema

Isso melhora muito a **experiência do usuário** e a qualidade do seu código.

---

# Complemento da Lição

## 1) O que você deve gravar (regra de ouro)
Se um erro pode acontecer **por causa do usuário, do arquivo, da rede ou do banco**, você precisa tratar.

Exemplos práticos:
- usuário digitou letra quando era número
- arquivo não existe
- conexão com banco falhou
- conversão de texto para número falhou

---

## 2) O `catch` mais correto para o exemplo da divisão
No exemplo da divisão por zero, a exceção mais específica é:

- `ArithmeticException`

Isso é melhor do que capturar tudo com `Exception`, porque deixa claro **qual erro** você está tratando.

Exemplo:

    try {
        int resultado = 10 / 0;
    } catch (ArithmeticException e) {
        System.out.println("Erro: divisão por zero.");
    }

---

## 3) Try/Catch + Scanner (caso mais comum em exercícios)
Um erro muito comum é o usuário digitar texto quando o programa espera número.

Exemplo (ideia do padrão):

    try {
        System.out.print("Digite um número: ");
        int n = teclado.nextInt();
    } catch (Exception e) {
        System.out.println("Você digitou algo inválido.");
        teclado.nextLine(); // limpa o buffer
    }

---

## 4) Exercício rápido (fixação)
Faça um programa que:
1) pede um número inteiro
2) tenta dividir `10` por esse número
3) se o usuário digitar `0`, mostre uma mensagem amigável e não deixe o programa quebrar

---

## 5) Pergunta única (para checar que fixou)
No Java, qual bloco é executado quando ocorre um erro dentro do `try`?

---

<!-- nav_start -->
---
Anterior: [32 Video Casas Decimais](../docs/32_Video_Casas_Decimais.md) | Proximo: [34 Video 01 Try Catch](../docs/34_Video_01_Try_Catch.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
