Resumo de Classes e Objetos
Em Java, os atributos podem ser estáticos (static) ou não estáticos (também chamados de atributos/variáveis de instância/objeto).

1 - Atributos Estáticos (static)
Atributos estáticos pertencem à classe, e não ao objeto.
Estes atributos são compartilhados por todas as instâncias (objetos), que foram criadas à partir de uma classe.
Quando um atributo é declarado como static, ele é criado apenas uma vez dentro da classe e é acessível por qualquer instância da classe ou diretamente pela própria classe.
Atributos estáticos são usados quando você deseja que todos os objetos da classe compartilhem um valor comum. Isto ocorre, pois quando o valor do atributo estático é alterado, todos os objetos sofrem a alteração, ou seja, todos os objetos terão o mesmo conteúdo para este atributo.
Este compartamento não ocorre quando um atributo não é estático.
2 - Atributos Não Estáticos
Os atributos não estáticos são individualizados para cada objeto, ou seja, um atributo definido em uma classe como não estático, ao ser alterado, não afeterá o mesmo atributo dos outros objetos. Cada objeto, terá o seu próprio atributo com valores independentes. Em resumo, quando um objeto realizar a alteração do conteúdo do seu atributo não estatático, esta alteração não será propagada para o mesmo atributo nos outros objetos.
Os atributos não estáticos por serem atributos de objetos/instâncias, só podem ser manipulados a partir do momento que se cria um objeto.
Exemplo 01: O exemplo abaixo, mostra uma classe que possui dois atributos estáticos "variáveis": nome e valor. Como estes atributos são estáticos, eles podem ser manipulados por qualquer método sem a necessidade de criar um objeto. Agora analise o Exemplo 02.
//Exemplo 01
public class Teste{
    static String nome;
    static int valor;

    public static void main(String[] args) {
        nome = "Java";
        valor = 8;
    }
}
Note no exemplo 02 que os atributos agora são não estáticos, ou seja, não existe a palavra static antes da variável/atributo. Logo o método main não não poderá ser executado pois está ocorrendo uma tentativa de manipular as variáveis fora do objeto, ou seja, sem a existência de um objeto criado previamente: 
//Exemplo 02
public class Teste{
    String nome;
    int valor;

    public static void main(String[] args) {
        nome = "Java";
        valor = 8;
    }
}
Para que o método main possa ser executado mantendo as variáveis/atributos como não estáticos, é necessário primeiro criar um objeto, para que os atributos pertencam ao objeto e não à classe. Assim o código correto seria:
//Exemplo 02
public class Teste{
    String nome;
    int valor;

    public static void main(String[] args) {
        Teste teste = new Teste();
        teste.nome = "Java";
        teste.valor = 8;
    }
}
A decisão de montar uma classe que deve ser utilizada posteriormente como um objeto, se dá quando o programador precisa ter várias versões/instâncias daquela classe, sem que os valores de cada objeto seja perdido quando ocorrer a necessidade de manipulação dos valores destes objetos. Exemplos de classes que precisam ser modeladas como um objeto seria: carro, pessoa, instrumento, ferramenta, aluno, avaliação .
3 - Exemplos de classes que são modeladas para não se tornarem um objeto.
Classes que não precisam de instâncias e podem ser modeladas com métodos e atributos estáticos incluem:

Classes utilitárias com métodos de ajuda.
Classes de configuração com valores constantes.
Gerenciadores globais (como log, banco de dados).
Classes de validação ou conversão que realizam tarefas específicas.
Essas classes geralmente são utilizadas quando você não precisa de estado específico para cada instância, mas quer ter funções que podem ser acessadas de qualquer lugar no código.

Classe Utilitária ou de Ajuda (Helper Class)

Uma classe que contém apenas métodos estáticos e não possui estado (atributos) ou comportamento específico para instâncias.
Exemplo: Math, String, StringUtils. Essas classes oferecem funcionalidades úteis sem necessidade de criar um objeto para usá-las.
Exemplo:

Arquivo: MathUtils.java
public class MathUtils {
    // Método estático
    public static int soma(int a, int b) {
        return a + b;
    }

    public static int subtracao(int a, int b){
        return b - a;
    }

    //outros metodos com os demais calculos matematicos mais comuns
}

Arquivo: App.java
public class App {
   public static void main (String[] args){
        // Usando sem criar um objeto
        int resultado = MathUtils.soma(5, 10);
   }
}

Classe para Configurações ou Parâmetros Globais

Classes que mantêm constantes ou configurações globais que não precisam de instâncias, já que são as mesmas para toda a aplicação.
Exemplo: uma classe conexaoBanco que mantém constantes e métodos para se conectar à um banco de dados, etc.
public class ConfiguracoesBanco {
    // Parâmetros de configuração como constantes
    public static final String URL_BANCO = "jdbc:mysql://localhost:3306/meuBanco";
    public static final String USUARIO = "admin";
    public static final String SENHA = "senha123";
    public static final String DRIVER = "com.mysql.cj.jdbc.Driver";
    
    // Método estático para obter uma conexão com o banco
    public static void conectar() {
        try {
            Class.forName(DRIVER);  // Carrega o driver JDBC
            System.out.println("Conectando ao banco de dados...");
            // Aqui você pode adicionar o código real de conexão com o banco
            // Connection conn = DriverManager.getConnection(URL_BANCO, USUARIO, SENHA);
        } catch (Exception e) {
            System.out.println("Erro ao conectar ao banco: " + e.getMessage());
        }
    }
}

Classe de Validação ou Conversão

Quando você tem uma classe com métodos de validação ou conversões de dados que podem ser usados em qualquer lugar do código sem necessidade de criar instâncias.
Exemplos seria um conjunto de métodos auxiliares para as nossas aplicações como: validarCPF, validarCPJ, validarTelefone, validarSenha, obterNumeroInteiro, obterNumeroFloat.
Métodos como Integer.toString(), Integer.parseInt(), Float.toString(), Float.parseInt(),  Double.valueOf(), Character.isDigit(), etc., são usados frequentemente para conversão e manipulação de tipos primitivos não são utilizadas através de objetos.

---

## Opção melhorada

# Classes, Objetos e Atributos `static` vs. de Instância (Java)

## 1) Ideia central (em 1 frase)
- **`static`**: pertence à **classe** (1 único valor compartilhado).
- **não `static`**: pertence ao **objeto** (cada instância tem o seu próprio valor).

---

## 2) O que muda na prática

### Atributo `static` (da classe)
- Existe **uma única vez** na memória para a classe.
- Todos os objetos “apontam” para o mesmo valor.
- Pode ser acessado assim:
  - `NomeDaClasse.atributo`
  - ou via objeto (funciona, mas é menos claro): `obj.atributo`

**Exemplo (contador global de objetos):**
    public class Pessoa {
        static int totalCriadas = 0;  // compartilhado
        String nome;                  // por objeto

        public Pessoa(String nome) {
            this.nome = nome;
            totalCriadas++;
        }
    }

    public class App {
        public static void main(String[] args) {
            new Pessoa("Ana");
            new Pessoa("Bruno");
            System.out.println(Pessoa.totalCriadas); // 2
        }
    }

---

### Atributo não `static` (de instância / do objeto)
- Cada objeto tem o seu próprio valor.
- Para acessar, **precisa criar o objeto** antes.

**Exemplo (cada carro tem sua cor):**
    public class Carro {
        String cor; // cada carro possui a sua
    }

    public class App {
        public static void main(String[] args) {
            Carro c1 = new Carro();
            Carro c2 = new Carro();

            c1.cor = "Preto";
            c2.cor = "Branco";

            System.out.println(c1.cor); // Preto
            System.out.println(c2.cor); // Branco
        }
    }

---

## 3) Por que “não dá” acessar atributo de instância dentro de `main` direto?
O `main` é `static`, então ele “vive” na classe e **não tem um objeto implícito**.  
Por isso, acessar `nome = "Java";` (sem criar objeto) dá erro: não existe “este objeto” (`this`) ali.

**Certo:**
    public class Teste {
        String nome;

        public static void main(String[] args) {
            Teste t = new Teste();
            t.nome = "Java";
        }
    }

---

## 4) Quando usar `static` (casos clássicos)

### 4.1 Constantes
- Valores fixos e compartilhados.

    public class Config {
        public static final int PORTA = 3306;
        public static final String HOST = "localhost";
    }

### 4.2 Métodos utilitários (helpers)
- Funções sem “estado” de objeto.

    public class MathUtils {
        public static int soma(int a, int b) {
            return a + b;
        }
    }

    public class App {
        public static void main(String[] args) {
            int r = MathUtils.soma(2, 3);
            System.out.println(r);
        }
    }

**Boa prática comum (evitar instanciar helper):**
    public class MathUtils {
        private MathUtils() { } // impede new MathUtils()

        public static int soma(int a, int b) {
            return a + b;
        }
    }

### 4.3 “Estado global” com cuidado
- Ex.: cache, logger, contador global.
- Geralmente exige atenção a concorrência (multi-thread) e testes.

---

## 5) Quando NÃO usar `static` (quando precisa de “estado por objeto”)
Use objetos quando cada “coisa” precisa de seus próprios valores:
- aluno (matrícula, nome, notas)
- pedido (itens, status)
- pessoa (data_nascimento, sexo, contatos)
- carro (placa, cor, modelo)

---

## 6) Um detalhe importante sobre os exemplos de “classe utilitária”
- `Math` é um exemplo clássico de classe com **métodos `static`**.
- `String` **não** é uma classe “somente estática”: normalmente você usa como objeto (`String texto = "abc";`), embora ela tenha métodos estáticos como `String.valueOf(...)`.
- `StringUtils` (Apache Commons) é um exemplo típico de utilitária (muitos métodos `static`).

---

## 7) Mini checklist (decidir rápido)
- Precisa de várias “instâncias” com valores diferentes? → **não `static` (objeto)**
- É uma regra/constante/configuração igual para todo mundo? → **`static final`**
- É uma função “de ajuda” que não precisa guardar estado? → **método `static`**
- Precisa compartilhar um contador/registro global? → **`static` (com cuidado)**

---

## Exercícios

1) Crie uma classe `Aluno` com atributos **não estáticos**: `matricula`, `nome`, `email`. Crie 2 objetos e mostre que alterar um não muda o outro.  
2) Crie uma classe `Contador` com atributo **static** `total`. Some +1 no construtor e imprima `Contador.total` após criar 5 objetos.  
3) Crie uma classe `Conversor` com métodos `static`:
   - `celsiusParaFahrenheit(double c)`
   - `fahrenheitParaCelsius(double f)`
4) Explique (em 2 linhas) por que `main` é `static` e o que isso implica para acessar atributos de instância.

<!-- nav_start -->
---
Anterior: [154 Reescrevendo App BD](../docs/154_Reescrevendo_App_BD.md) | Proximo: [156 Validador](../docs/156_Validador.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
