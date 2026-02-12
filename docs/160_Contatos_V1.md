# Gerenciamento de Contatos V1

---

## Visão geral

Gerenciamento de Contatos V1
Aqui temos um exemplo de projeto utilizando Classes e Arraylist.

A classe pessoa, permite que seja cadastrado apenas um único email e um único telefone para cada pessoa.

No próximo artigo temos uma sequência de vídeos exemplicando o funcionamento do código.

---

## Classe Pessoa.java

classe Pessoa.java

    public class Pessoa {
        public static int contador;
        private int id;
        private String nome;
        private String telefone;
        private String email;

        //construtor da classe pessoa
        public Pessoa(String nome, String telefone, String email) {
            contador++;
            this.id = contador;
            setNome(nome);
            setTelefone(telefone);
            setEmail(email);
        }

        public int getId() {
            return id;
        }

        public void setNome(String nome) {
            //aqui implementariamos as validações necessárias
            //antes de inserir o nome  
            this.nome = nome;
        }

        public String getNome() {
            return nome;
        }

        public void setTelefone(String telefone) {
            //aqui implementariamos as validações necessárias
            //antes de inserir o telefone 
            this.telefone = telefone;
        }

        public String getTelefone() {
            return telefone;
        }

        public void setEmail(String email) {
            //aqui implementariamos as validações necessárias
            //antes de inserir o email 
            this.email = email;
        }

        public String getEmail() {
            return email;
        }

        //cria o método toString para sobrescrever através do @overrride "annotations" utilizado
        // para converter o objeto para string
        //quando for necessário imprimir os dados do objeto na tela por outra parte do nosso
        //programa. 
        @Override
        public String toString() {
            return "ID: " + id + ", Nome: " + nome + ", Telefone: " + telefone + ", Email: " + email;
        }
    }

---

## Classe App.java (versão básica)

Classe App.java
import java.util.ArrayList;
import java.io.IOException;
import java.util.Scanner;

    public class App {
        //Aqui definimos a lista contatos e teclado como variaveis globais
        //pois já estamos utilizando a orientação a objetos para ter uma melhor
        //separação não sendo necessário termos tanta proteção às variaveis do
        //programa principal
        private static ArrayList<Pessoa> listaContatos = new ArrayList<Pessoa>();
        private static Scanner teclado = new Scanner(System.in);

        public static void main(String[] args) {
            //guarda a opcao selecionada pelo usuario no menu
            int opcao;

            do {
                limparTela();
                //obtem a opcao desejada pelo usuario
                opcao = obterEscolhaMenu();

                //executa a funcionalidade conforme escolhido pelo usuario
                processarEscolhaMenu(opcao);
            } while (opcao != 5);
        }

        private static void processarEscolhaMenu(int opcao){
            switch (opcao) {
                case 1:
                    incluirContato();
                    pausa();
                    break;
                case 2:
                    alterarContato();
                    break;
                case 3:
                    consultarContatos();
                    break;
                case 4:
                    excluirContato();
                    pausa();
                    break;
                case 5:
                    System.out.println("Saindo do sistema...");
                    break;
                default:
                    System.out.println("Opção inválida. Tente novamente.");
            }
        }

        private static int obterEscolhaMenu(){
            int opcao;

            System.out.println("\n--- Menu de Gerenciamento de Contatos ---\n");

            System.out.println("1. Incluir Contato");
            System.out.println("2. Alterar Contato");
            System.out.println("3. Consultar Contatos");
            System.out.println("4. Excluir Contato");
            System.out.println("5. Sair");

            System.out.print("\nEscolha uma opção: ");
            opcao = teclado.nextInt();
            teclado.nextLine(); // Limpeza buffer

            return opcao;
        }

        private static void incluirContato() {
            System.out.print("Digite o nome: ");
            String nome = teclado.nextLine();

            System.out.print("Digite o telefone: ");
            String telefone = teclado.nextLine();

            System.out.print("Digite o email: ");
            String email = teclado.nextLine();

            Pessoa novaPessoa = new Pessoa(nome, telefone, email);
            listaContatos.add(novaPessoa);
            System.out.println("Contato incluído com sucesso!");
        }

        private static void alterarContato() {
            System.out.print("Digite o ID do contato a ser alterado: ");
            int id = teclado.nextInt();
            teclado.nextLine(); // limpeza buffer

            limparTela();

            //busca a pessoa especificada pelo id
            Pessoa pessoa = encontrarContatoPorId(id);

            if (pessoa != null) {

                System.out.print("Digite o novo nome (ou deixe em branco para manter): ");
                String nome = teclado.nextLine();
                //metodo isBlank retorna true se a string estiver vazia
                //é equivalente a fazer nome.equals("");
                if (!nome.isBlank())
                    pessoa.setNome(nome);

                System.out.print("Digite o novo telefone (ou deixe em branco para manter): ");
                String telefone = teclado.nextLine();
                if (!telefone.isBlank())
                    pessoa.setTelefone(telefone);

                System.out.print("Digite o novo email (ou deixe em branco para manter): ");
                String email = teclado.nextLine();
                if (!email.isBlank())
                    pessoa.setEmail(email);

                System.out.println("Contato alterado com sucesso!");
            } else {
                System.out.println("Contato não encontrado.");
                pausa();
            }
        }

        private static void consultarContatos() {
            //metodo isEmpty verifica se a lista esta vazia
            if (listaContatos.isEmpty()) {
                System.out.println("Nenhum contato cadastrado.");
            } else {
                System.out.println("\n--- Lista de Contatos ---");
                for (Pessoa pessoa : listaContatos) {
                    System.out.println(pessoa);
                }
            }
            pausa();
        }

        private static void excluirContato() {
            //obtem o id do contato;
            System.out.print("Digite o ID do contato a ser excluído: ");
            int id = teclado.nextInt();
            teclado.nextLine(); // Consumir quebra de linha

            //encontra o contato
            Pessoa pessoa = encontrarContatoPorId(id);
            
            //excluir o contato
            if (pessoa != null) {
                listaContatos.remove(pessoa);
                System.out.println("Contato excluído com sucesso!");
            } else {
                System.out.println("Contato não encontrado.");
            }
        }

        private static Pessoa encontrarContatoPorId(int id) {
            //varre o array list para encontrar o id pesquisado
            for (Pessoa pessoa : listaContatos) {
                if (pessoa.getId() == id) {
                    //encontrou retorna o objeto pessoa
                    return pessoa;
                }
            }
            //se chegou até aqui não existe este id
            return null;
        }


        private static void limparTela(){
            try {
                if (System.getProperty("os.name").contains("Windows"))
                    new ProcessBuilder("cmd", "/c", "cls").inheritIO().start().waitFor();
                else
                    new ProcessBuilder("clear").inheritIO().start().waitFor();

            } catch (IOException | InterruptedException ex) {}
        }

        private static void pausa(){
            System.out.println("\nTecle ENTER para continuar.");
            teclado.nextLine();
        }

    }

---

## App.java (versão modificada com ENUM)

A seguir temos um versão modificada da classe App.java, utilizando o conceito de ENUM para melhorar o código no que se refere ao uso de "códigos mágicos" para processar os itens do menu.
import java.util.ArrayList;
import java.io.IOException;
import java.util.Scanner;

    public class App {

        // ===== ENUM EMBUTIDO =====
        private enum MenuOpcao {

            INCLUIR(1, "Incluir Contato"),
            ALTERAR(2, "Alterar Contato"),
            CONSULTAR(3, "Consultar Contatos"),
            EXCLUIR(4, "Excluir Contato"),
            SAIR(5, "Sair");

            private final int codigo;
            private final String descricao;

            MenuOpcao(int codigo, String descricao) {
                this.codigo = codigo;
                this.descricao = descricao;
            }

            public int getCodigo() {
                return codigo;
            }

            public String getDescricao() {
                return descricao;
            }

            public static MenuOpcao fromCodigo(int codigo) {
                for (MenuOpcao opcao : values()) {
                    if (opcao.codigo == codigo) {
                        return opcao;
                    }
                }
                return null;
            }
        }

        // ===== VARIÁVEIS GLOBAIS =====
        private static ArrayList listaContatos = new ArrayList<>();
        private static Scanner teclado = new Scanner(System.in);

        public static void main(String[] args) {

            MenuOpcao opcao;

            do {
                limparTela();
                opcao = obterEscolhaMenu();
                processarEscolhaMenu(opcao);
            } while (opcao != MenuOpcao.SAIR);
        }

        private static void processarEscolhaMenu(MenuOpcao opcao) {

            if (opcao == null) {
                System.out.println("Opção inválida. Tente novamente.");
                pausa();
                return;
            }

            switch (opcao) {
                case INCLUIR:
                    incluirContato();
                    pausa();
                    break;

                case ALTERAR:
                    alterarContato();
                    break;

                case CONSULTAR:
                    consultarContatos();
                    break;

                case EXCLUIR:
                    excluirContato();
                    pausa();
                    break;

                case SAIR:
                    System.out.println("Saindo do sistema...");
                    break;
            }
        }

        private static MenuOpcao obterEscolhaMenu() {

            System.out.println("\n--- Menu de Gerenciamento de Contatos ---\n");

            for (MenuOpcao opcao : MenuOpcao.values()) {
                System.out.println(opcao.getCodigo() + ". " + opcao.getDescricao());
            }

            System.out.print("\nEscolha uma opção: ");
            int codigo = teclado.nextInt();
            teclado.nextLine(); // limpar buffer

            return MenuOpcao.fromCodigo(codigo);
        }

        // ===== FUNCIONALIDADES =====

        private static void incluirContato() {
            System.out.print("Digite o nome: ");
            String nome = teclado.nextLine();

            System.out.print("Digite o telefone: ");
            String telefone = teclado.nextLine();

            System.out.print("Digite o email: ");
            String email = teclado.nextLine();

            Pessoa novaPessoa = new Pessoa(nome, telefone, email);
            listaContatos.add(novaPessoa);

            System.out.println("Contato incluído com sucesso!");
        }

        private static void alterarContato() {
            System.out.print("Digite o ID do contato a ser alterado: ");
            int id = teclado.nextInt();
            teclado.nextLine();

            limparTela();

            Pessoa pessoa = encontrarContatoPorId(id);

            if (pessoa != null) {
                System.out.print("Digite o novo nome (ou deixe em branco): ");
                String nome = teclado.nextLine();
                if (!nome.isBlank()) pessoa.setNome(nome);

                System.out.print("Digite o novo telefone (ou deixe em branco): ");
                String telefone = teclado.nextLine();
                if (!telefone.isBlank()) pessoa.setTelefone(telefone);

                System.out.print("Digite o novo email (ou deixe em branco): ");
                String email = teclado.nextLine();
                if (!email.isBlank()) pessoa.setEmail(email);

                System.out.println("Contato alterado com sucesso!");
            } else {
                System.out.println("Contato não encontrado.");
                pausa();
            }
        }

        private static void consultarContatos() {
            if (listaContatos.isEmpty()) {
                System.out.println("Nenhum contato cadastrado.");
            } else {
                System.out.println("\n--- Lista de Contatos ---");
                for (Pessoa pessoa : listaContatos) {
                    System.out.println(pessoa);
                }
            }
            pausa();
        }

        private static void excluirContato() {
            System.out.print("Digite o ID do contato a ser excluído: ");
            int id = teclado.nextInt();
            teclado.nextLine();

            Pessoa pessoa = encontrarContatoPorId(id);

            if (pessoa != null) {
                listaContatos.remove(pessoa);
                System.out.println("Contato excluído com sucesso!");
            } else {
                System.out.println("Contato não encontrado.");
            }
        }

        private static Pessoa encontrarContatoPorId(int id) {
            for (Pessoa pessoa : listaContatos) {
                if (pessoa.getId() == id) {
                    return pessoa;
                }
            }
            return null;
        }

        private static void limparTela() {
            try {
                if (System.getProperty("os.name").contains("Windows"))
                    new ProcessBuilder("cmd", "/c", "cls").inheritIO().start().waitFor();
                else
                    new ProcessBuilder("clear").inheritIO().start().waitFor();
            } catch (IOException | InterruptedException e) {}
        }

        private static void pausa() {
            System.out.println("\nTecle ENTER para continuar.");
            teclado.nextLine();
        }
    }

---
# Complemento da Lição

## 1) Arquitetura do exemplo (bem simples de visualizar)

### Camada de modelo (dados)
- **Pessoa**
  - guarda os dados do contato (`id`, `nome`, `telefone`, `email`)
  - centraliza o formato de exibição via `toString()`

### Camada de “controle” (fluxo do programa)
- **App**
  - mostra o menu
  - lê teclado
  - decide qual funcionalidade executar (incluir/alterar/consultar/excluir)
  - usa o `ArrayList` como “banco de dados em memória”

---

## 2) Onde entra o ArrayList (e por que funciona bem aqui)
Você está usando `ArrayList` como uma lista de contatos:
- **Adicionar** contato: `listaContatos.add(novaPessoa)` (rápido, normalmente no final)
- **Listar** contatos: `for (Pessoa pessoa : listaContatos)` (simples)
- **Buscar por id**: varre a lista (`for`), então é uma busca linear

📌 Troca importante:
- Simplicidade: excelente para aprender
- Custo: buscar por id vira O(n) conforme a lista cresce

---

## 3) Por que o ENUM melhora o menu (sem “código mágico”)
Na versão básica, o menu depende de números “soltos” (1, 2, 3, 4, 5).
Na versão com `enum MenuOpcao`:
- cada número vira um **significado claro** (INCLUIR, ALTERAR, CONSULTAR, EXCLUIR, SAIR)
- o código fica mais legível e mais difícil de errar
- o `fromCodigo()` centraliza a conversão de número → opção

**Exemplo do mundo real (bem direto):**  
Em vez de decorar que “3” significa “consultar”, você usa uma etiqueta com nome: **CONSULTAR**.

---

## 4) Pontos que valem atenção (coisas que geralmente pegam)

### 4.1) `contador` é estático
`public static int contador;` conta quantas pessoas foram criadas enquanto o programa roda.
- Se você fechar o programa e abrir de novo, o contador volta a 0 (porque não tem persistência).

### 4.2) Busca por id varrendo lista
O método `encontrarContatoPorId(int id)` faz:
- “olhar um por um” até achar o id

Isso é ótimo para aprender, mas em listas grandes tende a ficar lento.

### 4.3) Tipagem (generics) na versão com ENUM
Na versão com `enum`, a lista ficou assim:
- `private static ArrayList listaContatos = new ArrayList<>();`

Isso perde o tipo `Pessoa` e pode gerar avisos e riscos de erro.
A forma tipada (mais segura) seria manter `ArrayList<Pessoa>` como na versão básica.

---

## 5) Evolução natural do projeto (visão de engenharia)
Se você quiser deixar esse projeto com cara mais profissional (organização e manutenção), a evolução costuma ser:

1) **Pessoa** (domínio) continua simples
2) Criar um **ContatoService** para regras (incluir/alterar/excluir/buscar)
3) Criar um **ContatoRepository** (mesmo que em memória) para guardar a lista
4) `App` fica só como “tela/console” (entrada e saída)

Isso separa responsabilidades e reduz bagunça no `App`.

---

## 6) Exercícios curtos (fixação prática)
1) No `Pessoa`, implemente uma validação simples:
   - não aceitar `nome` vazio (usar `isBlank()`).
2) No `App`, antes de alterar/excluir, mostre os contatos e peça o ID.
3) Crie um método `existeEmail(String email)` para evitar cadastro com e-mail repetido na lista.
4) Troque a busca por id para retornar também a posição (índice) do contato e explique por quê.

---
<!-- nav_start -->
---
Anterior: [VÃ­deo: Gerenciamento de Contatos V1](../docs/159_Video_Contatos_V1.md) | Próximo: [Gerenciamento de Contatos V2](../docs/161_Contatos_V2.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

