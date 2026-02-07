Bibliotecas de Terceiros no Java
O que é uma biblioteca de código
Uma biblioteca de código (ou biblioteca de funções) é um conjunto de funções, classes e recursos prontos para serem usados em um programa. Ela oferece soluções para tarefas comuns e complexas, permitindo que você não precise reinventar a roda ao programar. Em vez de escrever todo o código do zero, você pode simplesmente utilizar esses recursos já prontos.

Comparando com o Mundo Real
Imagine que você está montando um móvel e, em vez de criar todas as ferramentas do zero (martelo, parafuso, prego, etc.), você compra um conjunto de ferramentas prontas para usar. Isso é o que uma biblioteca faz em programação: ela fornece ferramentas prontas para resolver problemas, como cálculos, manipulação de texto, ou até mesmo criar interfaces gráficas.

Como funciona em Java
Em Java, as bibliotecas são agrupadas em pacotes (ou packages) e podem ser acessadas por meio de importação. Quando você importa uma biblioteca, você pode usar suas classes e métodos no seu programa sem precisar reescrever o código.

Por exemplo, se você quiser trabalhar com números de forma mais avançada (como cálculos matemáticos), você pode usar a biblioteca Math que já tem várias funções prontas para isso e que faz parte do próprio java.



import java.lang.Math;

public class Main {
    public static void main(String[] args) {
        double raizQuadrada = Math.sqrt(16);  // Calcula a raiz quadrada de 16
        System.out.println("Raiz quadrada de 16: " + raizQuadrada);
    }
}


Além de utilizar as bibliotecas disponibilizadas pela própria linguagem de programação, você pode utilizar bibliotecas de terceiros.

O que são bibliotecas de terceiros?
Bibliotecas de terceiros são bibliotecas criadas por outras pessoas ou empresas (fora do núcleo oficial da linguagem de programação) e que você pode usar no seu próprio projeto. Elas oferecem funcionalidades prontas para você, muitas vezes com uma implementação mais avançada ou especializada, sem que você precise fazer tudo do zero.

Essas bibliotecas são externas ao Java, ou seja, não fazem parte do pacote padrão da linguagem (como a biblioteca java.util ou java.io). Elas são desenvolvidas por outras pessoas, comunidades ou empresas, e você pode integrá-las ao seu código para estender a funcionalidade do seu programa.

Por exemplo, você pode usar bibliotecas para:

Manipulação de imagens (como a biblioteca ImageIO ou bibliotecas como Apache Commons Imaging).
Conexão com bancos de dados (como JDBC ou bibliotecas como Hibernate e Spring Data).
Frameworks para construção de sites (como Spring, JSF, ou Play Framework).
Teste de código (como JUnit ou Mockito).
Desenvolvimento de interfaces gráficas (como JavaFX ou Swing).
Essas bibliotecas de terceiros ajudam a acelerar o desenvolvimento, pois elas já vêm com muitas funcionalidades prontas e bem testadas.

Como usar uma biblioteca de terceiros em Java?
O uso de bibliotecas de terceiros pode ser feito de várias maneiras, mas o processo geralmente envolve:

Baixar a biblioteca: Você precisa obter o arquivo da biblioteca (normalmente um arquivo .jar - Java ARchive) que contém o código da biblioteca.

Adicionar o arquivo .jar ao seu projeto: Depois de baixar o arquivo .jar, você precisa adicioná-lo ao classpath do seu projeto. Isso significa basicamente dizer ao seu projeto onde encontrar o código da biblioteca.

Se você estiver utilizando o VSCode para basta adicionar o arquivo  .jar no diretório lib do seu projeto.

Importar as classes da biblioteca: Após adicionar o arquivo .jar, você pode usar as classes e métodos dessa biblioteca no seu código, com a palavra-chave import.

Utilizando a biblioteca stringUtils do projeto Apache
A biblioteca Apache Commons Lang oferece várias funcionalidades úteis para manipulação de strings, datas e outras operações comuns. A classe StringUtils é uma das mais populares dessa biblioteca e oferece métodos como isEmpty, join, reverse, entre outros.

Passo 1: Baixar a Biblioteca Apache Commons Lang
Vá até o site do Apache Commons Lang:
Acesse a página oficial para baixar a versão mais recente da biblioteca:

Apache Commons Lang
Baixe o arquivo .jar:

Na seção "Binaries", baixe o arquivo commons-lang3-3.17.0-bin.zip mais recente, que geralmente é um arquivo comprimido .zip.
O arquivo terá um nome como commons-lang3-3.x.x-bin.zip (o número da versão pode variar).
Após realizar o download, descompacte o arquivo e o  .jar e identifique o arquivo commons-lang3-3.x.x.jar. Você precisará mover este arquivo para a pasta lib do seu projeto.
Passo 2: Escrever o Código para Usar StringUtils
Crie um novo projeto java.

Mova o arquivo commons-lang3-3.x.x.jar identificado anteriormente para a pasta lib do seu projeto.

Escreva o código abaixo para você testar os métodos da classe StringUtils.

import org.apache.commons.lang3.StringUtils;

public class App {
    public static void main(String[] args) {
        String texto = "   Hello, World!   ";
        // Remover espaços extras no começo e no final
        String textoTrimmed = StringUtils.trim(texto);
        System.out.println("Texto original: '" + texto + "'");
        System.out.println("Texto sem espaços extras: '" + textoTrimmed + "'");

        // Verificar se a string é vazia
        if (StringUtils.isEmpty(textoTrimmed)) {
            System.out.println("Texto está vazio!");
        } else {
            System.out.println("Texto não está vazio.");
        }

        // Inverter a string
        String textoInvertido = StringUtils.reverse(textoTrimmed);
        System.out.println("Texto invertido: " + textoInvertido);
    }
}

---

# Opção melhorada

---

## 📚 Bibliotecas em Java (visão organizada)

### ✅ O que é uma biblioteca de código
- **Biblioteca** = conjunto de **classes**, **funções/métodos** e **recursos prontos**.
- Objetivo: **reutilizar soluções** e acelerar o desenvolvimento.
- Benefício: menos “reinventar a roda”, mais foco na regra de negócio.

---

## 🧰 Analogia do mundo real
Uma biblioteca é como um **kit de ferramentas**:
- você não fabrica um martelo do zero,
- você **pega pronto** e usa para resolver o problema mais rápido.

---

## 🧩 Como bibliotecas funcionam em Java
### Pacotes (packages) e import
- As bibliotecas são organizadas em **pacotes**.
- Para usar uma classe, você normalmente faz **import**.
- Exemplo típico (Math): o `Math` já vem no Java e pode ser usado direto (o `import java.lang.Math;` é opcional porque `java.lang` já é importado automaticamente).

---

## 🧱 Biblioteca padrão x Bibliotecas de terceiros

### 📌 Biblioteca padrão (JDK)
Exemplos comuns:
- `java.util` (listas, scanner, datas básicas)
- `java.io` (arquivos)
- `java.math` (BigDecimal, BigInteger)

### 🌍 Bibliotecas de terceiros
São bibliotecas externas ao JDK, criadas por comunidades/empresas:
- ORM / Banco: Hibernate, Spring Data
- Testes: JUnit, Mockito
- Utilitários: Apache Commons
- Web: Spring, JSF, Play Framework

---

## 📦 Maneiras de usar bibliotecas de terceiros

### 1) Via arquivo .jar (manual)
- Baixa o `.jar`
- Adiciona no **classpath** (ex.: VS Code usando pasta `lib`)
- Importa as classes e usa

**Ponto importante:**  
O **classpath** é o “caminho” onde o Java procura classes/bibliotecas na hora de compilar/executar.

---

### 2) Via gerenciador de dependências (padrão do mercado)
Em projetos profissionais, o mais comum é **Maven** ou **Gradle**, porque:
- baixa dependências automaticamente,
- resolve versões/transitivas,
- evita “jar perdido” na máquina.

#### Maven (pom.xml) – Apache Commons Lang
    <dependency>
        <groupId>org.apache.commons</groupId>
        <artifactId>commons-lang3</artifactId>
        <version>3.17.0</version>
    </dependency>

#### Gradle (build.gradle) – Apache Commons Lang
    dependencies {
        implementation 'org.apache.commons:commons-lang3:3.17.0'
    }

---

## 🧪 Apache Commons Lang (StringUtils) — uso prático

### O que a StringUtils ajuda a resolver
- validações de string (`isBlank`, `isEmpty`)
- normalização (`trim`)
- utilidades (`reverse`, `join`)

### Versão “mais completa” do exemplo (com isBlank)
    import org.apache.commons.lang3.StringUtils;

    public class App {
        public static void main(String[] args) {
            String texto = "   Hello, World!   ";

            String textoTrimmed = StringUtils.trim(texto);

            System.out.println("Texto original: '" + texto + "'");
            System.out.println("Texto sem espaços extras: '" + textoTrimmed + "'");

            if (StringUtils.isBlank(textoTrimmed)) {
                System.out.println("Texto está vazio ou só tem espaços!");
            } else {
                System.out.println("Texto tem conteúdo.");
            }

            String textoInvertido = StringUtils.reverse(textoTrimmed);
            System.out.println("Texto invertido: " + textoInvertido);
        }
    }

---

## 🧠 Dicas rápidas que evitam erros comuns
- **isEmpty**: considera vazio apenas `""` (não vê espaço como vazio).
- **isBlank**: considera vazio `""` e também `"   "` (somente espaços).
- Se você estiver formatando números/dinheiro em Java, geralmente é melhor usar:
  - `BigDecimal` para valores monetários
  - `NumberFormat` / `DecimalFormat` para exibição

---

## ✅ Exercícios (para fixar)
1) Crie uma string com vários espaços e teste:
   - `StringUtils.isEmpty(...)`
   - `StringUtils.isBlank(...)`
   Explique a diferença no resultado.

2) Leia um texto do usuário e:
   - aplique `trim`
   - mostre o texto invertido
   - mostre quantos caracteres ele tem (use `.length()`)

3) Use `StringUtils.join(...)` para juntar um array de palavras com `" - "` no meio.
   Ex.: `["Java", "SQL", "Git"]` → `Java - SQL - Git`
<!-- nav_start -->
---
Anterior: [Entrega: Hackathon](../docs/148_Entrega_Hackathon.md) | Próximo: [O que Ã© um pacote em Java](../docs/150_O_que_e_Pacote.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

