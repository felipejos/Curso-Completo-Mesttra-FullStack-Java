# 🧯 Uso do Try/Catch

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

    public class Main{
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

    public class Main{
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
