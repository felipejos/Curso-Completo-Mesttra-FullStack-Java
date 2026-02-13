Criando o seu próprio pacote


1. Organizar o código
Crie um projeto java em branco. Se você não lembra como criar um projeto novo do zero veja este vídeo Criar Projeto Novo  Java no VSCode:
Dentro da pasta src do seu projeto crie uma estrutra de pasta da seguinte forma. Para isto, clique em src e depois no ícone de criar novo diretório. Crie primeiramente um diretório chamado br. Depois selecione a pasta br e clique novamente em adicionar um novo diretório e digite com no nome do novo diretorio. Selecione o diretório com e clique novamente em criar um novo diretório e digite agora o nome validador. Por último, crie um arquivo chamado validadorSenha.java.
src

└── br

          └── com

                    └── validador

                              └── validadorSenha.java

Coloque o código a seguir no arquivo validadorSenha.java
package br.com.validador;
public class validadorSenha {

    // Método para validar a complexidade da senha
    public static boolean validarSenha(String senha) {
        // Verifica se a senha não é nula e tem pelo menos 8 caracteres
        if (senha == null || senha.length() < 8) {
            throw new IllegalArgumentException("A senha deve ter pelo menos 8 caracteres.");
        }

        // Variáveis para verificar as condições de complexidade
        boolean temMaiuscula = false;
        boolean temMinuscula = false;
        boolean temNumero = false;
        boolean temCaractereEspecial = false;

        // Percorre cada caractere da senha
        for (int i = 0; i < senha.length(); i++) {
            char c = senha.charAt(i);

            // Verifica se o caractere é uma letra maiúscula
            if (Character.isUpperCase(c)) {
                temMaiuscula = true;
            }

            // Verifica se o caractere é uma letra minúscula
            if (Character.isLowerCase(c)) {
                temMinuscula = true;
            }

            // Verifica se o caractere é um número
            if (Character.isDigit(c)) {
                temNumero = true;
            }

            // Verifica se o caractere é um caractere especial
            if (isCaractereEspecial(c)) {
                temCaractereEspecial = true;
            }
        }

        // Verifica se todas as condições de complexidade foram atendidas
        if (!temMaiuscula) {
            throw new IllegalArgumentException("A senha deve conter pelo menos uma letra maiúscula.");
        }
        if (!temMinuscula) {
            throw new IllegalArgumentException("A senha deve conter pelo menos uma letra minúscula.");
        }
        if (!temNumero) {
            throw new IllegalArgumentException("A senha deve conter pelo menos um número.");
        }
        if (!temCaractereEspecial) {
            throw new IllegalArgumentException("A senha deve conter pelo menos um caractere especial.");
        }

        return true;
    }

    // Método auxiliar para verificar se um caractere é um caractere especial
    private static boolean isCaractereEspecial(char c) {
        // Definimos um conjunto de caracteres especiais
        char[] caracteresEspeciais = {'!', '@', '#', '$', '%', '^', '&', '*', '(', ')', '-', '=', '+', '{', '}', '[', ']', ':', ';', '"', '\'', '<', '>', ',', '.', '?', '/', '\\', '|', ' '};

        // Verifica se o caractere está na lista de caracteres especiais
        for (char caractereEspecial : caracteresEspeciais) {
            if (c == caractereEspecial) {
                return true;
            }
        }
        return false;
    }
}
Certifique-se de que a estrutura de diretórios esteja correta e que o código Java esteja no caminho correto para ser compilado.
Como este código se trata de uma biblioteca, não precisaremos do arquivo App.java criado por padrão pelo VSCode. Você pode apagar o arquivo App.java. O arquivo App.java, seria utilizado apenas para testar a classe validador senha, como estamos fornecendo o codigo já testado, então não será necessário o App.java. 
Para entender o que significa a linha package br.com.validador; leia o próximo artigo.
2. Compilar o código
No terminal do VSCode execute o comando abaixo:

javac -encoding UTF-8 -d .\bin\ .\src\br\com\validador\validadorSenha.java
javac é o compilador Java. Ele é usado para compilar arquivos fonte .java em bytecode Java, que é armazenado em arquivos .class.
-encoding UTF-8 especifica a codificação de caracteres a ser usada ao ler os arquivos fonte. No caso, UTF-8 é um tipo de codificação que pode representar qualquer caractere em praticamente qualquer língua do mundo principalmente linguas que utilizam acentuação como no caso do português.
-d especifica o diretório de destino onde os arquivos .class (código compilado) serão colocados após a compilação.
.\bin\ indica que os arquivos compilados devem ser armazenados na pasta bin (geralmente, a pasta bin é onde o bytecode compilado é armazenado em um projeto no VSCode).
.\src\br\com\validador\validadorSenha.java: Este é o caminho do arquivo fonte Java que você deseja compilar.
3. Gerar o pacote para distribuir a sua biblioteca
No terminal do VSCode execute o comando abaixo:

jar cf validadorSenha.jar -C .\bin\ .
jar O comando jar é uma ferramenta fornecida utilizada para empacotar "arquivo compactado" arquivos .class, bibliotecas e outros recursos em um arquivo JAR.
c é uma opção que indica que o objetivo do comando é criar um novo arquivo JAR.
f é uma opção que indica que o nome do arquivo JAR será fornecido diretamente a seguir. Ou seja, f informa ao jar que o próximo argumento será o nome do arquivo JAR a ser criado.
validadorSenha.jar é o nome do arquivo JAR que será criado. Esse arquivo irá conter as classes compiladas e outros arquivos que você especificar.
-C a opção -C permite mudar temporariamente o diretório de trabalho ao empacotar os arquivos.
.\bin\ especifica o diretório a partir do qual os arquivos serão empacotados. No caso, o diretório bin, que é onde você compilou as classes (de acordo com o comando javac -d .\bin\ que discutimos anteriormente).
O ponto (.) ao final do comando significa incluir todos os arquivos e subdiretórios do diretório atual (que, após o -C, é .\bin\) no arquivo JAR.
O que acontece após executar o comando jar?
O comando jar irá criar um arquivo JAR chamado validadorSenha.jar.
Pronto, você tem agora uma biblioteca que pode ser compartilhada com outras pessoas da forma que você quiser. Você pode adicionar a sua biblioteca em seu github ou site.
4. Utilizando a sua própria biblioteca.
Criar um Novo Projeto Java
1 - Primeiramente, você precisa criar um novo projeto Java. 

2 - Copie o arquivo validadorSenha.jar para a pasta lib do seu projeto.

3 - Crie o código abaixo: 

import br.com.validador.validadorSenha;

public class App{
    public static void main(String[] args) {
        // Exemplo de uso da biblioteca validadorSenha
        String senha = "Senha123!";
        
        try {
            boolean valida = validadorSenha.validarSenha(senha);
            System.out.println("Senha válida: " + valida);
        } catch (IllegalArgumentException e) {
            System.out.println("Erro: " + e.getMessage());
        }
    }
}

<!-- nav_start -->
---
Anterior: [150 O que e Pacote](../docs/150_O_que_e_Pacote.md) | Proximo: [152 Esqueleto 4 Operacoes](../docs/152_Esqueleto_4_Operacoes.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
