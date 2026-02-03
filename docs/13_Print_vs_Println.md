# DiferenÃ§a entre `print` e `println` em Java â˜•

DiferenÃ§a entre print e println

Em Java, System.out.print e System.out.println sÃ£o usados para imprimir texto no console, mas hÃ¡ uma diferenÃ§a fundamental entre eles.

DiferenÃ§a Principal:
System.out.print: Imprime o texto, mas nÃ£o adiciona uma nova linha no exibiÃ§Ã£o dos dados na console. Isso significa que o prÃ³ximo texto impresso serÃ¡ mostrado na mesma linha na console.

System.out.println: Imprime o texto e, em seguida, adiciona uma nova linha na console. Isso significa que o prÃ³ximo texto impresso serÃ¡ mostrado na linha seguinte.

Exemplos:
- Usando System.out.print:

```java
public class Main {
    public static void main(String[] args) {
        System.out.print("Hello, ");
        System.out.print("World!");
    }
}
SaÃ­da na console:

Hello, World!
ExplicaÃ§Ã£o: Ambos os textos foram impressos na mesma linha porque System.out.print nÃ£o adiciona uma nova linha ao tÃ©rmino da impressÃ£o dos dados.

Usando System.out.println:

public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, ");
        System.out.println("World!");
    }
}
SaÃ­da na console:

Hello,
World!
ExplicaÃ§Ã£o: Cada chamada de System.out.println adiciona uma nova linha apÃ³s imprimir o texto, entÃ£o "World!" Ã© impresso na linha seguinte.

Combinando System.out.print e System.out.println:

public class Main {
    public static void main(String[] args) {
       System.out.print("Hello, ");
       System.out.println("World!");
       System.out.print("Welcome to Java Programming.");
    }
}
SaÃ­da:

Hello, World!
Welcome to Java Programming.
ExplicaÃ§Ã£o: O primeiro System.out.print imprime "Hello, " sem adicionar uma nova linha, entÃ£o "World!" aparece na mesma linha. O segundo System.out.println adiciona uma nova linha apÃ³s "World!", entÃ£o "Welcome to Java Programming." aparece na linha seguinte.

Resumo:
Use System.out.print quando quiser que o texto seja impresso na mesma linha.
Use System.out.println quando quiser que o texto seja impresso e movido para a prÃ³xima linha.
Isso Ã© essencial para controlar a formataÃ§Ã£o da saÃ­da no console, dependendo do que vocÃª deseja que o usuÃ¡rio veja.
<!-- nav_start -->
---
Anterior: [Leitura de Dados com a Classe Scanner](../docs/12_Leitura_Dados_Scanner.md) | Próximo: [VariÃ¡veis](../docs/14_Variaveis.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

