# Gerenciamento de Contatos V2

---

## Contexto (conteúdo fornecido)

Gerenciamento de Contatos V2


Nesta versão, a classe pessoa permite que seja cadastrado apenas um único email porem permite o cadastro de vários telefones para cada pessoa.

Estude o funcionamento deste código comparado com a versão V1, posteriormente tente resolver a sugestão de exercício abaixo.



Sugestão de Exercício: Altere os arquivos deste projeto para que seja possível cadastrar vários emails para cada contato.

Resumo das alterações:

- Alterar a classe pessoa para que o atributo email seja um ArrayList.

- Realizar os ajustes na classe App.java para permitir a inclusão e exclusão dos emails. 



-Após as alterações anteriores e testes de validação, modifique o codigo para utilizar o padrão MVC

---

## classe Pessoa.java (conteúdo fornecido)

classe Pessoa.java

    import org.apache.commons.lang3.StringUtils;
    import java.util.ArrayList;

    public class Pessoa {
        public static int contador;
        private int id;
        private String nome;
        private ArrayList<telefones> = new ArrayList();
        private String email;

        //construtor da classe pessoa
        public Pessoa(String nome,  ArrayList telefones, String email) {
            contador++;
            this.id = contador;
            setNome(nome);
            this.telefones = telefones;
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

        public void setTelefone(String ddd, String telefone) {
            //aqui implementariamos as validações necessárias
            //antes de inserir o telefone 
            telefones.add(new Telefone(ddd, telefone));
        }

        public ArrayList getTelefones() {
            return telefones;
        }

        public void setEmail(String email) {
            //aqui implementariamos as validações necessárias
            //antes de inserir o email 
            this.email = email;
        }

        public String getEmail() {
            return email;
        }

        //cria o método to string utilizado para converter o objeto para string
        //quando for necessário imprimir os dados do objeto na tela por outra parte do nosso
        //programa
        @Override
        public String toString() {
            String strTelefones = "";
            
            if (!telefones.isEmpty()) {
                for (Telefone telefone : telefones) {
                    strTelefones += telefone.toString() + ", ";
                }
            }

            return "ID: " + id + ", Nome: " + nome + ", Telefones: " +  StringUtils.removeEnd(strTelefones, ", ") + ", Email: " + email;
        }
    }

---

## Classe Telefone.java (conteúdo fornecido)

Classe Telefone.java

    public class Telefone {
        public static int contador;
        int id;
        private String ddd;
        private String telefone;

        public int getId() {
            return id;
        }

        public String getDdd() {
            return ddd;
        }

        public String getTelefone() {
            return telefone;
        }
        
        public Telefone(String ddd, String telefone) {
            contador++;
            id = contador;
            this.ddd = ddd;
            this.telefone = telefone;
        }

        @Override
        public String toString() {
            return "ID: " + id + " (" + ddd + ") " + telefone;
        }
    }

---

## Classe App.java (conteúdo fornecido)

Classe App.java

    import java.io.IOException;
    import java.util.ArrayList;
    import java.util.Scanner;

    public class App {
        //Aqui definimos a lista contatos e teclado como variaveis globais
        //pois já estamos utilizando a orientação a objetos para ter uma melhor
        //separação não sendo necessário termos tanta proteção às variaveis do
        //programa principal
        private static ArrayList listaContatos = new ArrayList();
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

        private static void processarEscolhaMenuAlterarContato(int opcao, Pessoa pessoa){
            switch (opcao) {
                case 1:
                    alterarDadosBasicosContato(pessoa);
                    pausa();
                    break;
                // case 2:
                //  TODO: Implementar a alteração de um telefone existente de um contato
                //     alterarUmTelefone();
                //     break;
                case 3:
                    inserirNovoTelefone(pessoa.getTelefones());
                    pausa();
                    break;
                case 4:
                    excluirTelefone(pessoa.getTelefones());
                    pausa();
                    break;
                case 5:
                    System.out.println("Voltar ao menu anterior");
                    break;
                default:
                    System.out.println("Opção inválida. Tente novamente.");
            }
        }

        private static void alterarDadosBasicosContato(Pessoa pessoa){
            System.out.print("\nDigite o novo nome (ou deixe em branco para manter): ");
                String nome = teclado.nextLine();

                //metodo isBlank retorna true se a string estiver vazia
                //é equivalente a fazer nome.equals("");
                if (!nome.isBlank())
                    pessoa.setNome(nome);

                System.out.print("Digite o novo email (ou deixe em branco para manter): ");
                String email = teclado.nextLine();
                if (!email.isBlank())
                    pessoa.setEmail(email);

                System.out.println("Contato alterado com sucesso!");
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

        private static int obterEscolhaMenuAlterarContato(){
            int opcao;

            System.out.println("\n--- Menu Alteração de Contatos ---\n");

            System.out.println("1. Alterar Dados Básicos");
            System.out.println("2. Alterar um Telefone");
            System.out.println("3. Inserir novo Telefone");
            System.out.println("4. Excluir Telefone");
            System.out.println("5. Sair");

            System.out.print("\nEscolha uma opção: ");
            opcao = teclado.nextInt();
            teclado.nextLine(); // Limpeza buffer

            return opcao;
        }

        private static boolean inserirNovoTelefone(ArrayList telefones){
            int resposta;
            System.out.print("Deseja adicionar um contato telefônico [s/n]? ");
            resposta  = teclado.nextLine().toLowerCase().charAt(0);

            if (resposta == 's'){
                telefones.add(obterTelefone());
                System.out.println("\nNovo telefone inserido com sucesso.");
                return true;
            } else{
                System.out.println("\nInserção de novo telefone cancelado.");
                return false;
            }
        }

        private static void incluirContato() {
            ArrayList telefones = new ArrayList();

            System.out.print("Digite o nome: ");
            String nome = teclado.nextLine();

            System.out.print("Digite o email: ");
            String email = teclado.nextLine();

            boolean resposta;

            do {
               resposta = inserirNovoTelefone(telefones);
            } while (resposta);
            
            Pessoa novaPessoa = new Pessoa(nome, telefones, email);
            listaContatos.add(novaPessoa);

            System.out.println("\nContato incluído com sucesso!");
        }

        private static Telefone obterTelefone(){
            String ddd, telefone;

            System.out.print("Digite o ddd do telefone: ");
            ddd = teclado.nextLine();

            System.out.print("Digite o telefone: ");
            telefone = teclado.nextLine();

            return new Telefone(ddd, telefone);

        }

        private static void alterarContato() {
            System.out.print("Digite o ID do contato a ser alterado: ");
            int id = teclado.nextInt();
            teclado.nextLine(); // limpeza buffer
            
            limparTela();

            //busca a pessoa especificada pelo id
            Pessoa pessoa = encontrarContatoPorId(id);
            
            if (pessoa != null) {
                //imprime os dados do contato

                System.out.println(pessoa);
                //obtem a opcao desejada pelo usuario
                int opcao = obterEscolhaMenuAlterarContato();

                //executa a funcionalidade conforme escolhido pelo usuario
                processarEscolhaMenuAlterarContato(opcao, pessoa);
            } else {
                System.out.println("\nContato não encontrado.");
                pausa();
            }
        }

        private static void consultarContatos() {
            //metodo isEmpty verifica se a lista esta vazia
            if (listaContatos.isEmpty()) {
                System.out.println("\nNenhum contato cadastrado.");
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
            teclado.nextLine(); // limpeza do buffer

            //encontra o contato
            Pessoa pessoa = encontrarContatoPorId(id);
            
            //excluir o contato
            if (pessoa != null) {
                listaContatos.remove(pessoa);
                System.out.println("\nContato excluído com sucesso!");
            } else {
                System.out.println("\nContato não encontrado.");
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

        private static void excluirTelefone(ArrayList telefones){
            // Verifica se a pessoa tem telefones cadastrados
            if (telefones.isEmpty()) {
                System.out.println("\nNão há telefones cadastrados para esta pessoa.");
                return;
            }
            
            int idTelefone;
            System.out.print("Digite o ID do telefone a ser excluído: ");
            idTelefone = teclado.nextInt();
            teclado.nextLine(); //limpeza buffer

            
            boolean encontrado = false;
            for (int i = 0; i < telefones.size(); i++) {
                Telefone telefone = telefones.get(i);
                
                // Se o telefone encontrado tiver o id correspondente, remove-o
                if (telefone.getId() == idTelefone) {
                    telefones.remove(i);
                    System.out.println("\nTelefone com ID " + idTelefone + " foi removido.");
                    encontrado = true;
                    break;
                }
            }

            // Caso não tenha encontrado o telefone
            if (!encontrado) {
                System.out.println("\nTelefone com ID " + idTelefone + " não encontrado.");
            }
        }

        private static void pausa(){
            System.out.println("\nTecle ENTER para continuar.");
            teclado.nextLine();
        }

        private static void limparTela(){
            try {
                if (System.getProperty("os.name").contains("Windows"))
                    new ProcessBuilder("cmd", "/c", "cls").inheritIO().start().waitFor();
                else
                    new ProcessBuilder("clear").inheritIO().start().waitFor();

            } catch (IOException | InterruptedException ex) {}
        }
    }

---

# Complemento da Lição

## 1) O que mudou do V1 para o V2 (comparação direta)
No V1:
- **Pessoa** tinha `telefone` como `String` (um só).
- **Pessoa** tinha `email` como `String` (um só).

No V2:
- **Pessoa** passa a ter **vários telefones** (lista de `Telefone`).
- **Pessoa** continua com **um único e-mail** (ainda `String`).
- **App** ganha um **sub-menu** de alteração para lidar com telefones (inserir / excluir).

---

## 2) Fluxo do V2 (para entender rápido o código)
### Inclusão (menu 1)
- cria `ArrayList telefones`
- pede nome e e-mail
- entra num loop perguntando se deseja adicionar telefone
- cria `Pessoa(nome, telefones, email)` e adiciona na lista

### Alteração (menu 2)
- busca contato por ID
- mostra o contato na tela
- abre o “Menu Alteração de Contatos”
- permite:
  - alterar dados básicos (nome / email)
  - inserir novo telefone
  - excluir telefone

### Consulta (menu 3)
- percorre a lista e imprime `pessoa` (via `toString()`)

### Exclusão (menu 4)
- busca por ID e remove o objeto da lista

---

## 3) Pontos de atenção (para evitar travar em erro de compilação)
Alguns trechos do conteúdo fornecido indicam pontos que normalmente precisam de ajuste para compilar sem warnings/erros:

- Uso de `ArrayList` sem tipo (raw type), por exemplo:
  - `private static ArrayList listaContatos = new ArrayList();`
  - métodos que recebem/retornam `ArrayList` sem `<>`

- Declaração de telefones na `Pessoa` (como está escrito):
  - `private ArrayList<telefones> = new ArrayList();`
  Isso costuma exigir:
  - nome do atributo + tipo correto da lista (ex.: lista de `Telefone`)
  - generics com `Telefone` (não “telefones”)

- No `excluirTelefone`, o código assume que:
  - `Telefone telefone = telefones.get(i);`
  Isso normalmente depende do `ArrayList` estar tipado como `ArrayList<Telefone>`.

📌 Ideia principal: **tipar as listas** ajuda o Java a impedir erros e facilita o `for-each`.

---

## 4) Exercício proposto: “Vários e-mails por contato” (passo a passo guiado)
Objetivo: trocar `email` (String) por uma **lista de e-mails** e dar opção de **incluir/excluir** na `App`.

### Passo 1 — Model (Pessoa)
Crie uma regra clara antes de codar:
- Vai permitir e-mails duplicados?
- Vai permitir e-mail vazio?
- Vai guardar “em ordem de cadastro”?

Depois, a mudança de estrutura fica assim (conceito):
- `email` deixa de ser `String`
- vira uma **lista de strings** (um e-mail por item)

O que você precisa ter na `Pessoa`:
- um método para **adicionar** e-mail
- um método para **remover** e-mail
- um método para **listar** e-mails (para imprimir no console)

### Passo 2 — View/Console (App)
Você vai precisar de um “mini-menu” para e-mails, parecido com o que já existe para telefones:
- inserir novo e-mail
- excluir e-mail existente
- listar e-mails do contato (antes de excluir)

📌 Dica de implementação (sem entregar o código pronto):
- Na exclusão, você pode usar:
  - índice (posição 0, 1, 2…)
  - ou um “ID” (igual telefone faz)
- Índice é mais simples para `String`, ID exige criar uma classe `Email` (mais avançado).

### Passo 3 — Validação (testes manuais)
Roteiro mínimo de testes:
- cadastrar contato com 0 e-mails (se permitido)
- cadastrar com 1 e-mail
- cadastrar com 2+ e-mails
- excluir e-mail que existe
- tentar excluir e-mail que não existe
- listar depois de excluir para confirmar

---

## 5) Próximo passo: migrar para MVC (organização profissional)
**MVC** separa responsabilidades para o projeto crescer sem virar bagunça:

### Model (dados e regras do domínio)
- `Pessoa`
- `Telefone`
- (futuro) `Email` ou `ArrayList<String> emails`

### View (tela/console)
- imprime menus
- lê entradas do usuário
- mostra mensagens e listas

### Controller (orquestra o fluxo)
- chama as funções para incluir/alterar/excluir
- decide qual ação executar conforme o menu
- valida entradas básicas (ex.: opção inválida)

📌 Roteiro prático de migração (ordem segura):
1) Criar uma classe `ContatoController` com métodos:
   - incluir, alterar, consultar, excluir
2) Mover do `App` para o controller toda lógica que mexe em `listaContatos`
3) Deixar o `App` apenas como “início do programa” (main) chamando o controller
4) Criar uma `ConsoleView` para centralizar prints e leituras (menu e entradas)

---

## 6) Checagem rápida (para você confirmar que entendeu)
1) No V2, por que foi criada a classe `Telefone` em vez de usar apenas `String`?  
2) Onde a lista de telefones é preenchida no fluxo de inclusão do contato?  
3) Para o exercício de “vários e-mails”, você prefere remover e-mail por **índice** ou criar uma classe `Email` com ID?

---
<!-- nav_start -->
---
Anterior: [Gerenciamento de Contatos V1](../docs/160_Contatos_V1.md) | Próximo: [VÃ­deo: Primeira AplicaÃ§Ã£o de Console com o Banco de Dados](../docs/162_Video_Primeira_App_BD.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

