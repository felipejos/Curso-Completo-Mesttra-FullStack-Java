# Empacotando a Aplicação

---

## Vídeos (conteúdo fornecido)

Empacotando a Aplicação


Todo o procedimento abaixo é apresentado com detalhes nos vídeos à seguir:



Parte 01: https://youtu.be/eLDRg1TjHSg

[![Parte 01](https://img.youtube.com/vi/eLDRg1TjHSg/hqdefault.jpg)](https://youtu.be/eLDRg1TjHSg)

Parte 02: https://youtu.be/7M2Zi6EAiik

[![Parte 02](https://img.youtube.com/vi/7M2Zi6EAiik/hqdefault.jpg)](https://youtu.be/7M2Zi6EAiik)

Parte 03: https://youtu.be/Y2FdV7gvjVg

[![Parte 03](https://img.youtube.com/vi/Y2FdV7gvjVg/hqdefault.jpg)](https://youtu.be/Y2FdV7gvjVg)

Parte 04: https://youtu.be/pNx0qnpVdvk

[![Parte 04](https://img.youtube.com/vi/pNx0qnpVdvk/hqdefault.jpg)](https://youtu.be/pNx0qnpVdvk)

---

## Objetivo (conteúdo fornecido)

Quando finalizamos um projeto e desejamos instalar a aplicação final na máquina do usuário, é necessário realizarmos o "build" do projeto, ou seja, compilarmos e empacotarmos a nossa aplicação em um arquivo .jar, para facilitar este processo de entrega do projeto.

---

## Estrutura de diretórios (conteúdo fornecido)

Considere o projeto com a seguinte estrutura de diretórios:



projeto/
├── src/
│     └── br/
|           └── com/
|                  ├── app/
|                  |      └── App.java
│                  └── service/
|                             └── Teste.java
├── lib/
│   └── commons-lang3-3.17.0.jar
├── dist/
├── bin/
src/: é o diretório onde está o nosso código fonte.

lib/: é o diretório onde está todas as bibliotecas de terceiros utilizadas em nosso projeto.

dist/: é o diretório onde será armazenado o pacote .jar gerado da nossa aplicação. dist é a abreviação de distribuition ou distribuição em português.

bin: é o diretório onde será gerado os arquivos compilados .class da nossa aplicação.

---

## Arquivo App.java (conteúdo fornecido)

Arquivo App.java

    package br.com.app;

    import org.apache.commons.lang3.StringUtils;
    import br.com.service.Teste;
    import java.util.Scanner;

    public class App {
        public static void main(String[] args) throws Exception {
            Scanner teclado = new Scanner(System.in);
            Teste teste = new Teste();

            limparTela();

            teste.nome = "joão";
            teste.peso = 80.5f;

            System.out.println("Nome: " + StringUtils.capitalize(teste.nome) + " Peso: " + teste.peso);

            System.out.println("Tecle ENTER para finalizar.");
            teclado.nextLine();

        }

        public static void limparTela() {
            try {
                if (System.getProperty("os.name").contains("Windows")) {
                    // Comando para limpar o console no Windows
                    new ProcessBuilder("cmd", "/c", "cls").inheritIO().start().waitFor();
                } else {
                    // Comando para limpar o console em sistemas Unix/Linux/Mac
                    new ProcessBuilder("clear").inheritIO().start().waitFor();

                }
            } catch (Exception e) {
                System.out.println("Erro ao tentar limpar a tela: " + e.getMessage());
            }
        }
    }

---

## Arquivo Teste.java (conteúdo fornecido)

Arquivo Teste.java

    package br.com.service;

    public class Teste {
        public String nome;
        public float peso;
    }

---

## Passos para gerar a aplicação final (conteúdo fornecido)

Para gerarmos a aplicação final é necessário executar os passos à seguir:

### 1. Compilar os arquivos
Abra o Prompt de Comando e navegue até a pasta raiz do projeto:

cd caminho\para\projeto


Agora, compile o código com:

javac -encoding UTF-8 -cp .\lib\* -d .\bin .\src\br\com\app\* .\src\br\com\service\*
javac é o compilador Java. Ele é usado para compilar arquivos fonte .java em bytecode Java, que é armazenado emarquivos .class.
-encoding UTF-8 especifica a codificação de caracteres a ser usada ao ler os arquivos fonte. No caso, UTF-8 é um tipode codificação que pode representar qualquer caractere em praticamente qualquer língua do mundo principalmente linguas que utilizam acentuação como no caso do português.
-cp: permite que você inclua as dependências externas para que o compilador reconheça as classes usadas no seu código.
-d especifica o diretório de destino onde os arquivos .class (código compilado) serão colocados após acompilação.
.\bin\ indica que os arquivos compilados devem ser armazenados na pasta bin (geralmente, a pasta bin éonde o bytecode compilado é armazenado em um projeto no VSCode).
.\src\br\com\app\*: Este é o caminho onde estão todos os arquivos pertencentes ao pacote br.com.app.
.\src\br\com\service\*: Este é o caminho onde estão todos os arquivos pertencentes ao pacote br.com.service.

### 2. Executar o programa para testar o funcionamento após compilação
Execute o programa com:

java -cp ".\bin;.\lib\*" br.com.app.App
java é o compilador Java. Ele é usado para compilar arquivos fonte .java em bytecode Java, que é armazenado emarquivos .class
-cp: permite que você informe o local onde está os arquivos compilados bem como onde está as dependências externas usadas no seu código.

### 3. Empacotar a aplicação
Execute o comando:

jar -cfe dist\App.jar br.com.app.App -C bin .
jar O comando jar é uma ferramenta fornecida utilizada para empacotar "arquivo compactado" arquivos.class, bibliotecas e outros recursos em um arquivo JAR.
c é uma opção que indica que o objetivo do comando é criar um novo arquivo JAR.
f é uma opção que indica que o nome do arquivo JAR será fornecido diretamente a seguir. Ou seja, f informa aojar que o próximo argumento será o nome do arquivo JAR a ser criado.
e especifica a classe principal do programa. Essa é a classe que contém o método main e será executada quando o JAR for executado com java -jar.
App.jar é o nome do arquivo JAR que será criado. Esse arquivo irá conter as classes compiladas e outros arquivos que você especificar.
-C a opção -C permite mudar temporariamente o diretório de trabalho ao empacotar os arquivos.
.\bin\ especifica o diretório a partir do qual os arquivos serão empacotados. No caso, o diretório bin, que é onde você compilou as classes (de acordo com o comando javac -d .\bin\ que discutimos anteriormente).
O ponto (.) ao final do comando significa incluir todos os arquivos e subdiretórios do diretório atual (que, após o-C, é .\bin\) no arquivo JAR.
Após este procedimento será gerado um arquivo App.jar dentro do diretório dist do seu projeto

Execute o comando abaixo para testar o pacte jar gerado:

java -cp ".\lib\*;.\dist\App.jar" br.com.app.App
A partir deste ponto, a aplicação está pronta para ser enviada para o ambiente do usuário, sendo necessário que o usuário tenha apenas o java jre instalado. Basta copiar a pasta lib e dist para a máquina do usuário. 

Imagine e copiamos a pasta dist e lib para dentro de uma pasta c:\minhaAplicacao\. Bata agora criar um arquivo texto com a extensão .bat dentro do diretório c:\minhaAplicacao\App.bat com o conteúdo baixo:

cd c:\minhaAplicacao
java -cp "lib\*;dist\App.jar" br.com.app.App
 Pronto, todas as vezes que o usuário entrar no diretório c:\minhaAplicacao e executar o arquivo App.bat a aplicação java será executada sem a necessidade do vscode por exemplo.

Para facilitar ainda a vida do usuário, pode-se criar um atalho do arquivo App.bat na área de trabalho do usuário.

---

## Thin JAR vs Fat JAR (conteúdo fornecido)

Neste processo utilizamos o conceito do thin jar ou jar magro. Neste processo não incluimos as bibliotecas externas dentro do nosso próprio jar. Uma outra possibilidade seria criarmos um fat jar ou jar gordo. Neste processo, todas as bibliotecas externas são incluidas no próprio jar.



Thin JAR
Um thin JAR (JAR "magro") contém apenas as classes do seu projeto (arquivos .class) e os metadados necessários, como o manifesto (META-INF/MANIFEST.MF). Ele não inclui as dependências externas dentro do arquivo JAR.

Características:
Tamanho menor: O arquivo JAR é pequeno, pois inclui apenas as classes do seu projeto.
Dependências externas separadas: As bibliotecas externas (arquivos JAR) precisam estar disponíveis no classpath na hora da execução.
Fácil atualização: Se uma dependência precisa ser atualizada, basta substituir o JAR da biblioteca sem recriar o JAR do projeto.
Flexibilidade: Usado em ambientes onde as dependências já estão instaladas ou gerenciadas, como em servidores de aplicativos.



Fat JAR
Um fat JAR (JAR "gordo"), contém não apenas as classes do seu projeto, mas todas as dependências externas agrupadas em um único arquivo JAR.

Características:
Tamanho maior: O arquivo JAR é grande, pois inclui todas as dependências externas.
Autossuficiente: Não precisa de bibliotecas separadas no classpath, tornando-o mais fácil de distribuir e executar.
Atualização trabalhosa: Se uma dependência precisa ser atualizada, o fat JAR precisa ser recriado.
Facilidade de execução: Você só precisa de um único arquivo para executar o programa.
A execução de um fat jar seria:

java -jar App.jar

---
# Complemento da Lição

## 1) “Build” em uma frase (para fixar)
Você transforma:
- **.java (código fonte)** → **.class (compilado)** → **.jar (pacote para distribuir)**

---

## 2) Como pensar na estrutura do projeto (o que cada pasta “faz”)
- `src/`: onde você programa (arquivos `.java`)
- `bin/`: onde ficam os `.class` gerados pela compilação
- `lib/`: dependências externas (outros `.jar`)
- `dist/`: onde fica o `.jar` final para entregar

---

## 3) O que é “classpath” (sem complicar)
**Classpath** é a “lista de lugares” onde o Java procura:
- suas classes compiladas (`bin/`)
- e dependências (`lib/*.jar`)

Se o classpath estiver errado, aparece erro tipo:
- `ClassNotFoundException`
- `NoClassDefFoundError`

---

## 4) Por que o thin jar exige copiar lib + dist
No thin jar:
- seu `App.jar` não carrega bibliotecas dentro dele
- então você precisa distribuir junto a pasta `lib/` para o Java achar as dependências

---

## 5) Quando vale usar fat jar
Vale quando você quer:
- 1 arquivo só pra rodar
- menos chance de erro de classpath

Mas paga o preço:
- arquivo maior
- atualizar dependência exige gerar o jar de novo

---

## 6) Exercícios rápidos (para praticar de verdade)
1) Troque o nome do jar para `MinhaAplicacao.jar` e ajuste o comando de execução.
2) Quebre propositalmente o classpath (não incluir `lib\*`) e anote qual erro aparece.
3) Mude o package `br.com.app` para outro nome e observe o que precisa mudar no comando do `jar -cfe`.
4) Faça um `.bat` que imprime uma mensagem antes e depois de rodar o programa.

---

<!-- nav_start -->
---
Anterior: [163 Videos Contatos V2](../docs/163_Videos_Contatos_V2.md) | Proximo: [165 Padrões Arquiteturais e Padrões de Projeto](../docs/165_Padrões_Arquiteturais_e_Padrões_de_Projeto.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
