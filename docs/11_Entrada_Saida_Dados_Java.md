Comandos de entrada e saÃ­da de dados no JAVA


No java, para conseguirmos realizar o processo de leitura de dados atravÃ©s do terminal ou console, Ã© necessÃ¡rio introduzirmos uma linha de cÃ³digo no inÃ­cio do arquivo. A estrutura bÃ¡sica de um programa em JAVA Ã© essa:



public class Main
{
        public static void main(String[] args) {
                System.out.println("Hello World");
        }
}
Como em todo programa de console, provavelmente serÃ¡ necessÃ¡rio realizar a leitura de dados a partir do teclado. Se isto ocorrer, serÃ¡ necessÃ¡rio inserirmos o comando import java.util.Scanner; antes da linha que contem a palavra public e posteriomente a linha Scanner teclado = new Scanner(System.in); ficando assim:

import java.util.Scanner; //linha de codigo que permite utilizarmos o comando para a leitura de dados

public class Main
{
        public static void main(String[] args) {
                //a linha de codigo abaixo prepara o teclado para ler os diversos tipos de dados;
                Scanner teclado = new Scanner(System.in);      
        }
}
Quando um desenvolvedor estÃ¡ construindo um programa que precisa interagir com o usuÃ¡rio para obter informaÃ§Ãµes, Ã© necessÃ¡rio utilizarmos o comando System.out.print("Mensagem a ser apresentada para o usuÃ¡rio.") para informar ao usuÃ¡rio do programa o que ele deve fazer. 

Diferentemente do comando de leitura de dados, o comando de saÃ­da de dados nÃ£o precisa de nenhum outro comando de apoio para funcionar. Vamos considerar que o programador precisa escrever um programa que precisa receber do usuÃ¡rio as informaÃ§Ãµes do nome dele, do pai e da mÃ£e.

Neste cenÃ¡rio, o programador deve instruir o computador a exibir em qual ordem ele deseja obter os dados. Assim o programador deve instruir o computador a apresentar uma informaÃ§Ã£o na tela dizendo para o usuÃ¡rio o que ele deve digitar e um outro comando informando que o computador deve obter os dados que o usuÃ¡rio irÃ¡ digitar. 

Para obtermos o nome do usuÃ¡rio seria necessÃ¡rio o seguinte bloco de cÃ³digo:

import java.util.Scanner; //linha de codigo que permite utilizarmos o comando para a leitura de dados

public class Main
{
    public static void main(String[] args) {
        //a linha de codigo abaixo prepara o teclado para ler os diversos tipos de dados;
        Scanner teclado = new Scanner(System.in);      
        
        System.out.print("Digite o seu nome: ");
        teclado.nextLine();
    }
}
ApÃ³s escrever estes comandos e clicar no botÃ£o RUN, o seguinte resultado serÃ¡ apresentado:
![OnlineGDB - exemplo](../images/LinguagemDeProgramacao1.png)

Note que o programa nÃ£o continua a execuÃ§Ã£o enquanto o usuÃ¡rio nÃ£o digitar um conjunto de dados qualquer e pressionar a tecla ENTER no teclado. ApÃ³s o usuÃ¡rio pressionar ENTER, como nÃ£o existe mais nenhum comando apÃ³s a leitura do nome, o programa serÃ¡ finalizado.
![OnlineGDB - exemplo](../images/LinguagemDeProgramacao2.png)

Caso o programador agora queira obter o nome do pai e da mÃ£e deste usuÃ¡rio, serÃ¡ necessÃ¡rio incluir mais dois conjuntos de comandos de saÃ­da e leitura de dados, para obter o nome do pai e da mÃ£e. Nesta situaÃ§Ã£o, teriamos que escrever o seguinte cÃ³digo.

import java.util.Scanner; //linha de codigo que permite utilizarmos o comando para a leitura de dados

public class Main
{
    public static void main(String[] args) {
        //a linha de codigo abaixo prepara o teclado para ler os diversos tipos de dados;
        Scanner teclado = new Scanner(System.in);      
        
        System.out.print("Digite o seu nome: ");
        teclado.nextLine();
        System.out.print("Digite o nome da sua MÃ£e: ");
        teclado.nextLine();
        System.out.print("Digite o nome do seu Pai: ");
        teclado.nextLine();
    }
}
O resultado da execuÃ§Ã£o do programa seria:
![OnlineGDB - exemplo](../images/LinguagemDeProgramacao3.png)

Tente agora alterar este cÃ³digo para obter o endereÃ§o do usuÃ¡rio.
<!-- nav_start -->
---
Anterior: [OnlineGDB](../docs/10_OnlineGDB.md) | Próximo: [Leitura de Dados com a Classe Scanner](../docs/12_Leitura_Dados_Scanner.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

