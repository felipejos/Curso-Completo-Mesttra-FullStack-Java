# ðŸ§¯ Uso do Try/Catch

No Java, o **tratamento de exceÃ§Ãµes** Ã© uma maneira de lidar com erros que podem acontecer enquanto um programa estÃ¡ sendo executado. Erros sÃ£o eventos inesperados que podem fazer o programa parar ou funcionar de forma incorreta.

Para evitar que o programa â€œquebreâ€ quando um erro acontece, usamos o **tratamento de exceÃ§Ãµes** com as palavras-chave:

- `try` â†’ **tenta** executar um trecho de cÃ³digo
- `catch` â†’ **captura e trata** o erro caso ele aconteÃ§a

---

## 1) âš ï¸ O que Ã© uma ExceÃ§Ã£o?

Uma exceÃ§Ã£o Ã© como um â€œalertaâ€ que indica que algo deu errado.

âœ… Exemplos comuns:
- Tentar dividir um nÃºmero por **zero**
- Tentar abrir um arquivo que **nÃ£o existe**
- Digitar texto quando o programa espera um **nÃºmero**

Quando isso acontece, o Java **lanÃ§a** (gera) uma exceÃ§Ã£o. Se vocÃª **nÃ£o tratar**, o programa pode **parar a execuÃ§Ã£o**.

### Exemplo (sem tratamento)

    public class Main{
        public static void main(String[] args) {
            // Tentamos fazer uma divisÃ£o
            int resultado = 10 / 0; // Isso gera uma exceÃ§Ã£o

            System.out.println("O programa continua executando...");
        }
    }

Ao executar, o programa **nÃ£o termina** e aparece algo como:

    Exception in thread "main" java.lang.ArithmeticException: / by zero
        at Main.main(Main.java:13)

---

## 2) ðŸ§ª O bloco `try`

O bloco `try` Ã© onde vocÃª coloca o cÃ³digo que **pode dar erro**.

Ã‰ como dizer:  
> â€œVou tentar executar isso aqui, mas pode acontecer algum problema.â€

    try {
        // CÃ³digo que pode gerar uma exceÃ§Ã£o
        int resultado = 10 / 0; // Isso vai gerar uma exceÃ§Ã£o
    }

---

## 3) ðŸ› ï¸ O bloco `catch`

Se uma exceÃ§Ã£o ocorrer dentro do `try`, o Java â€œpulaâ€ direto para o `catch`.

Ã‰ como dizer:  
> â€œSe der erro, trate aqui e mostre uma mensagem.â€

    try {
        int resultado = 10 / 0; // Isso vai gerar uma exceÃ§Ã£o
    } catch (Exception e) {
        // CÃ³digo para lidar com a exceÃ§Ã£o
        System.out.println("Erro: NÃ£o Ã© possÃ­vel dividir por zero.");
    }

---

## 4) âœ… Exemplo completo (Try/Catch funcionando)

    public class Main{
        public static void main(String[] args) {
            try {
                // Tentamos fazer uma divisÃ£o
                int resultado = 10 / 0; // Isso gera uma exceÃ§Ã£o
            } catch (Exception e) {
                // Se ocorrer uma exceÃ§Ã£o, isso Ã© executado
                System.out.println("Erro: NÃ£o Ã© possÃ­vel dividir por zero.");
            }

            System.out.println("O programa continua executando...");
        }
    }

ðŸ“Œ Execute esse exemplo e note que, mesmo com erro, o programa **continua** e imprime:

- a mensagem do `catch`
- e depois: **"O programa continua executando..."**

âœ… Agora faÃ§a um teste:
- Troque o `0` por outro nÃºmero (ex: `2`)
- Execute novamente
- VocÃª verÃ¡ que **nÃ£o ocorre erro**, pois a divisÃ£o passa a ser vÃ¡lida.

---

## ðŸ§  O que acontece no cÃ³digo?

- O cÃ³digo dentro do `try` tenta fazer a divisÃ£o.
- Dividir por zero nÃ£o Ã© permitido â†’ o Java lanÃ§a uma exceÃ§Ã£o.
- O `catch` captura a exceÃ§Ã£o e executa o tratamento.
- O programa continua normalmente apÃ³s o `catch`.

---

## ðŸ’¡ Por que usar `try` e `catch`?

Usar `try/catch` deixa seu programa mais **robusto** e evita que ele â€œmorraâ€ ao encontrar um problema.

âœ… Em vez de parar tudo, ele pode:
- mostrar uma mensagem clara para o usuÃ¡rio
- pedir uma nova entrada
- continuar o fluxo do sistema

Isso melhora muito a **experiÃªncia do usuÃ¡rio** e a qualidade do seu cÃ³digo.

<!-- nav_start -->
---
Anterior: [VÃ­deo: Formatando casas decimais](../docs/32_Video_Casas_Decimais.md) | Próximo: [VÃ­deo 01: Try Catch](../docs/34_Video_01_Try_Catch.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

