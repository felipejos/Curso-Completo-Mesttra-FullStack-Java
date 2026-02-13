# Exemplos de Uso do Do While
Aqui temos 3 exemplos de uso do do…while em Java, cada um com explicação clara do funcionamento e o motivo de usar essa estrutura.

Exemplo 1: Pedir senha até o usuário digitar corretamente
import java.util.Scanner; 
public class Exemplo1 { 
     public static void main(String[] args) {
         Scanner teclado = new Scanner(System.in); 
         String senhaCorreta = "1234"; 
         String senhaDigitada; 
         do { 
              System.out.print("Digite a senha: ");
               senhaDigitada = teclado.nextLine(); 
         } while (!senhaDigitada.equals(senhaCorreta)); 
         
         System.out.println("Acesso permitido!"); 
     }
}
Reescreva o código acima utilizando a classe que criamos nos textos passados: leitura.lerString(teclado, mensagem) .

Como funciona
O programa sempre pede a senha pelo menos uma vez.

Depois de o usuário digitar, o programa verifica se a senha está correta.

Enquanto a senha estiver errada, o laço se repete.

Quando a senha está certa, a condição se torna falsa e o loop termina.

O fluxo de execução do programa continua sua execução a partir do código que estiver escrito logo depois do termino do bloco de comandos.

Por que usar do…while aqui?
Porque queremos garantir que o usuário seja solicitado a digitar a senha pelo menos uma vez antes de qualquer verificação.

Exemplo 2: Menu interativo que só termina quando o usuário escolhe sair
import java.util.Scanner; 
public class Exemplo2 { 
   public static void main(String[] args) {         
      Scanner teclado = new Scanner(System.in); 
      int opcao; 

      do { 
            System.out.println("\n--- MENU ---"); 
            System.out.println("1 - Dizer Olá"); 
            System.out.println("2 - Mostrar número aleatório");
            System.out.println("3 - Sair"); 

            System.out.print("\nEscolha uma opção: ");             
            opcao = teclado.nextInt(); 
            
            switch (opcao) { 
                  case 1:
                        System.out.println("Olá!"); break; 
                  case 2: 
                        System.out.println("Número aleatório: " + Math.random()); break; 
                  case 3: 
                        System.out.println("Encerrando..."); break; 
                  default:
                        System.out.println("Opção inválida!"); 
            } 
       } while (opcao != 3); 
   } 
}

Reescreva o código acima utilizando a classe que criamos nos textos passados: leitura.lerInteiro(teclado, mensagem) .
Como funciona
O menu é mostrado uma vez antes de qualquer verificação.

O usuário escolhe uma opção.

O programa executa a ação da opção escolhida.

O laço só termina quando a opção digitada for 3 (Sair).

Por que usar do…while aqui?
Porque um menu precisa sempre ser exibido pelo menos uma vez, e só depois verificamos se o usuário quer sair ou continuar.

Exemplo 3 – Ler números e somá-los até que o usuário digite zero
import java.util.Scanner; 
public class Exemplo3 { 
     public static void main(String[] args) { 
          Scanner teclado = new Scanner(System.in); 

          int numero; 
          int soma = 0; 
          
          do { 
               System.out.print("Digite um número (0 para parar): ");
               numero = teclado.nextInt();
               soma += numero; 
          } while (numero != 0); 

          System.out.println("Soma total: " + soma); 
     }
}
Reescreva o código acima utilizando a classe que criamos nos textos passados: leitura.lerInteiro(teclado, mensagem) .

Como funciona
O programa pede um número ao usuário pelo menos uma vez.

O número é somado ao total.

Enquanto o número for diferente de 0, o laço continua.

Quando o usuário digita 0, o laço encerra.

Por que usar do…while aqui?
Porque queremos que o usuário digite ao menos um número, mesmo que ele decida parar imediatamente (digitando 0).

Resumo das vantagens nos exemplos
Exemplo	Por que o do…while é ideal?
Senha	Usuário deve digitar pelo menos uma vez
Menu	O menu precisa aparecer pelo menos uma vez
Soma de números	Um número precisa ser solicitado antes da verificação

---

## Complemento: reescritas usando a classe Leitura (métodos estáticos)

> Observação importante: nos seus textos você citou `leitura.lerString(teclado, mensagem)` e `leitura.lerInteiro(teclado, mensagem)`.
> Porém, o código da classe que você mostrou é `Leitura` e os métodos são:
> - `Leitura.lerValorString(String mensagem)`
> - `Leitura.lerValorInteiro(String mensagem)`
>
> Como o `Scanner` já está dentro da própria classe (atributo `private static Scanner teclado`), **não precisamos passar `teclado` como parâmetro**.
> Então, nos exemplos abaixo eu usei exatamente o padrão do seu código: `Leitura.lerValorString(...)` e `Leitura.lerValorInteiro(...)`.

---

### Exemplo 1 reescrito: pedir senha até acertar (com Leitura.lerValorString)

    public class Exemplo1 {
        public static void main(String[] args) {

            String senhaCorreta = "1234";
            String senhaDigitada;

            do {
                senhaDigitada = Leitura.lerValorString("Digite a senha: ");
            } while (!senhaDigitada.equals(senhaCorreta));

            System.out.println("Acesso permitido!");
        }
    }

#### Por que ficou melhor
- O `main` fica mais limpo (sem `Scanner`, sem `try/catch` repetido).
- A leitura e o tratamento de erro ficam centralizados na classe utilitária `Leitura`.

---

### Exemplo 2 reescrito: menu interativo (com Leitura.lerValorInteiro)

    public class Exemplo2 {
        public static void main(String[] args) {

            int opcao;

            do {
                System.out.println("\n--- MENU ---");
                System.out.println("1 - Dizer Olá");
                System.out.println("2 - Mostrar número aleatório");
                System.out.println("3 - Sair");

                opcao = Leitura.lerValorInteiro("\nEscolha uma opção: ");

                switch (opcao) {
                    case 1:
                        System.out.println("Olá!");
                        break;
                    case 2:
                        System.out.println("Número aleatório: " + Math.random());
                        break;
                    case 3:
                        System.out.println("Encerrando...");
                        break;
                    default:
                        System.out.println("Opção inválida!");
                }

            } while (opcao != 3);
        }
    }

#### Ponto de atenção (bem importante)
Se o usuário digitar algo inválido (ex: letra), sua `Leitura.lerValorInteiro(...)` devolve `0`.  
Nesse caso, o menu vai continuar (porque `0 != 3`) e cair no `default` (opção inválida). Isso é ok e coerente.

---

### Exemplo 3 reescrito: somar números até digitar 0 (com Leitura.lerValorInteiro)

    public class Exemplo3 {
        public static void main(String[] args) {

            int numero;
            int soma = 0;

            do {
                numero = Leitura.lerValorInteiro("Digite um número (0 para parar): ");
                soma += numero;
            } while (numero != 0);

            System.out.println("Soma total: " + soma);
        }
    }

#### Detalhe de lógica
- Mesmo quando o usuário digita `0`, ele entra na soma (`soma += 0`), o que **não altera** o resultado.
- Isso combina perfeitamente com o comportamento do `do...while`: executa uma vez e só depois verifica.

---

## Complemento: “mapa mental” rápido do do...while (pra você revisar olhando o código)

- **Você sempre vê isso:**
  - leitura/ação dentro do `do { ... }`
  - condição no `while ( ... );`

- **Frase para lembrar:**
  “Executa **uma vez** e repete **enquanto** a condição for verdadeira.”

---

<!-- nav_start -->
---
Anterior: [111 Video Do While](../docs/111_Video_Do_While.md) | Proximo: [113 Do e For](../docs/113_Do_e_For.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
