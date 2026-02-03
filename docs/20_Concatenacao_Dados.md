# Concatenação de Dados

**Prompt no chatgpt:** Explique o conceito de concatenação de dados para um iniciante em programação e dê exemplos simples em java.

---

## ✅ O que é concatenação de dados?

**Concatenação** significa **juntar informações (dados)** para formar uma única coisa.

Na programação, geralmente usamos **concatenação de Strings** (textos). Ou seja: juntar dois ou mais textos para formar um novo texto.

---

## Exemplo simples na vida real

Imagine que você tem duas palavras:

- `"Olá"`
- `"mundo"`

Se você concatenar essas palavras, o resultado será:

- `"Olámundo"`

---

## Exemplo simples em Java

```java
public class Main {
    public static void main(String[] args) {
        String nome = "Rogério";
        String sobrenome = "Freitas Ribeiro";

        // O resultado impresso será RogérioFreitas Ribeiro
        // O símbolo + quando inserido entre duas palavras "strings", faz com
        // que o conteúdo seja concatenado, ou seja, os valores serão colocados
        // um na frente do outro
        System.out.println(nome + sobrenome);

        // Neste caso o resultado será Rogério Freitas Ribeiro
        // Note que será juntado um espaço entre o nome e sobrenome. Este espaço
        // precisa ser escrito entre aspas
        System.out.println(nome + " " + sobrenome);
    }
}
```
## Explicação

Criamos duas variáveis do tipo `String` (texto): `nome` e `sobrenome`.

Usamos o símbolo `+` para juntar (concatenar) as variáveis.

O resultado foi impresso na tela.

### Saída

```
RogérioFreitas Ribeiro
Rogério Freitas Ribeiro
```


**Note:** na primeira impressão o nome saiu “colado” no sobrenome. Para inserir um espaço, foi necessário usar `" "`.

---

## Concatenando texto com número

Você também pode concatenar texto com números. O número será transformado em texto automaticamente.

```java
public class Main {
    public static void main(String[] args) {
        String nome = "Maria";
        int idade = 30;
        String frase = nome + " tem " + idade + " anos.";

        // Será impresso na tela: Maria tem 30 anos.
        System.out.println(frase);
    }
}
```

✅ Exemplo direto no System.out.println

```java
public class Main {
    public static void main(String[] args) {
        String nome = "Lucas";
        int idade = 25;

        // O nome é Lucas e a idade é 25 anos.
        System.out.println("O nome é " + nome + " e a idade é " + idade + " anos.");
    }
}
```

## O que acontece aqui

- `"O nome é "` é uma `String`
- `nome` é uma variável do tipo `String`
- `" e a idade é "` é outra `String`
- `idade` é uma variável do tipo `int` (número)
- `" anos."` também é uma `String`
- O operador `+` concatena tudo em uma única mensagem

---

## ⭐ Dica para iniciantes

Sempre que você usar o operador `+` com pelo menos uma `String`, o Java vai tratar tudo como texto.

Para deixar o texto mais legível, lembre-se de incluir espaços quando necessário:

```java
"Olá, " + nome
"Olá," + nome
```
