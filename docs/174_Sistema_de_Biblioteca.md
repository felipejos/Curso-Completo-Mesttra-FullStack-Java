# Sistema de Biblioteca

---

Sistema de Biblioteca  
Descrição geral:  
Este projeto consiste em desenvolver um sistema backend no formato API RESTful, onde os usuários operadores do sistema de biblioteca poderão criar e gerenciar: usuarios, alunos, livros, autores, editoras, categorias, emprestimos e devoluções. O sistema deve permitir CRUD completo para: usuarios, alunos, livros, autores, editoras, categorias e operações de emprestimo e devolução de livros. O sistema utilizará mecanismo de autenticação e autorização para controlar operações restritas e públicas. A única operação pública, será a possibilidade de consulta de livros pelos alunos. O restante das operações só pode ser realizada pelos usuários autorizados.

Arquivo do projeto em Java inicial e script para criar o banco de dados: https://drive.google.com/drive/folders/1iraXuFei2KvDaCXlVWf8tnwdXe6yolsc?usp=sharing 

Objetivos principais do projeto  
Esta API serve para demonstrar domínio de:

Criação de endpoints REST

Organização de código backend utilizando o conceito arquitetural de camadas (Model, DAO, Services e Controllers)

Persistência de dados em banco de dados

Tratamento de erros

Validações

Autenticação com JWT

Operações CRUD reais

Modelo de Dados DER: Diagrama de Entidade Relacionamento 

Explicação Completa das Funcionalidades  
A seguir, cada funcionalidade é explicada em detalhes.

1️ - CRUD de Aluno (/biblioteca/aluno/)  
1.1 - Criar Aluno (POST /aluno/)

1.2 - Consultar Aluno 

     1.2.1 - Consultar por ID (GET /aluno/id/{id})

     1.2.2 - Consultar por parte do Nome (GET /aluno/nome/{nome})

1.3 - Excluir Aluno por ID (DELETE /aluno/id/{id})

1.4 - Atualizar Aluno por ID (PUT /aluno/id/{id})

1.1 -Criar Aluno  
O usuário envia para a API uma requisição POST com os dados de cadastro de um novo aluno:

{
  "nome": "João da Silva",
  "cpf": "12345678901",
  "telefone": "34999998888",
  "email": "joao@email.com",
  "cep": "38400000",
  "estado": "MG",
  "cidade": "Uberlândia",
  "endereco": "Rua das Flores, 123",
  "bairro": "Centro"
}

A API deve:

Validar os campos obrigatórios com base na cor do losango do modelo DER do banco de dados.

Validar os dados de CPF (cpf válido) e email (segue o padrão de construção).

Cria o registro no banco.

Retorna o ID do usuário criado.

1.2 - Consultar Aluno  
O usuário envia para a API uma requisição GET para uma das duas possíveis rotas:

1.2.1 - /aluno/id/{id}

1.2.2 - /aluno/nome/{nome}

No caso da requisição 1.2.1 a API irá retornar um JSON com os dados do usuário encontrado ou um status de aluno não encontrado.

No caso da requisição 1.2.2 a API irá retornar um JSON contendo a lista dos usuários encontrados ou um status de aluno não encontrado.

1.3 - Excluir Aluno  
O usuário envia para a API uma requisição DELETE para a rota /aluno/id/{id}.

Se a exclusão ocorrer com sucesso a API deve retornar o status HTTP 204 No Content.

Se o ID informado não existir no banco de dados a API deve retornar o status HTTP 404 Not Found.

Caso ocorra qualquer erro de SQL a API deve devolver o status HTTP 409 Conflit.

1.4 - Atualizar Aluno  
O usuário envia para a API uma requisição PUT para a rota /aluno/id/{id}.

Se a atualização ocorrer com sucesso a API deve retornar o status HTTP 200 com um jSON representando os dados do aluno atualizado.

Se o ID informado não existir no banco de dados a API deve retornar o status HTTP 404 Not Found.

Caso ocorra qualquer erro de SQL a API deve devolver o status HTTP 409 Conflit.

Você deve entender o funcionamento deste esqueleto inicial e posteriormente implementar o CRUD de Editora, Autor

---

# Complemento da Lição

---

## 🧭 Aula 1 — O que você precisa “entender” no esqueleto (roteiro de leitura)

A meta aqui é conseguir explicar: **“como uma requisição entra, passa pelas camadas e vira resposta”**.

### 1) Comece pelo fluxo (de fora para dentro)
1. **Controller** recebe a requisição HTTP (ex.: `POST /biblioteca/aluno/`)
2. **Service** aplica regras e validações (CPF, e-mail, obrigatórios)
3. **DAO** faz a operação no banco (insert/select/update/delete)
4. Volta: DAO → Service → Controller → resposta HTTP (status + JSON)

### 2) Checklist para achar cada parte no projeto
Procure no projeto (pelos nomes, geralmente assim):
- `Controller` (ou pasta `controllers/`)
- `Service` (ou pasta `services/`)
- `DAO` (ou pasta `dao/`)
- `Model` (ou pasta `model/` ou `entity/`)
- `Exception` / `Handler` (tratamento global de erros)
- `Security` / `JWT` / `Auth` (autenticação e autorização)
- `application.properties` (config banco/porta)

### 3) Checklist para rodar sem travar (ordem correta)
1. Executar o **script do banco** (criar tabelas)
2. Configurar o **application.properties** (URL, usuário, senha)
3. Subir a API
4. Testar endpoints (Postman/Insomnia) começando pelos GET

---

## 🧱 Aula 2 — Arquitetura recomendada para CRUD de Editora e Autor

A ideia é **copiar o mesmo padrão do CRUD de Aluno** e trocar apenas “a entidade”.

### Estrutura (camadas)
- **Model**: `Editora`, `Autor`
- **DAO**: `EditoraDAO`, `AutorDAO`
- **Service**: `EditoraService`, `AutorService`
- **Controller**: `EditoraController`, `AutorController`

### Rotas (padrão consistente com Aluno)
Sugestão de padrão (mantenha o mesmo que existe no projeto):
- Editora:
  - `POST   /biblioteca/editora/`
  - `GET    /biblioteca/editora/id/{id}`
  - `GET    /biblioteca/editora/nome/{nome}`
  - `PUT    /biblioteca/editora/id/{id}`
  - `DELETE /biblioteca/editora/id/{id}`
- Autor:
  - `POST   /biblioteca/autor/`
  - `GET    /biblioteca/autor/id/{id}`
  - `GET    /biblioteca/autor/nome/{nome}`
  - `PUT    /biblioteca/autor/id/{id}`
  - `DELETE /biblioteca/autor/id/{id}`

---

## 🧩 Aula 3 — Modelo de dados: como NÃO inventar campos

Você vai olhar o **script SQL** e o **DER** do projeto e extrair daí:

1) Nome da tabela (ex.: `editora`, `autor`)
2) Colunas (ex.: `id`, `nome`, etc.)
3) Obrigatórios (NOT NULL)
4) Unicidade (UNIQUE)
5) Relacionamentos (FK)

Regra prática:
- **Model** em Java deve refletir essas colunas (pelo menos as principais).
- **Validação** deve respeitar NOT NULL e formato (ex.: e-mail, CPF quando existir).

---

## 🧪 Aula 4 — Implementação: primeiro o “contrato”, depois o código

A seguir vai um **modelo de implementação** (template) para você adaptar ao padrão que já existe no projeto.

### 4.1 Model (exemplo de estrutura)
Ajuste os campos conforme o seu banco/DER:

    public class Editora {
        private Long id;
        private String nome;

        public Editora() {}

        public Editora(Long id, String nome) {
            this.id = id;
            this.nome = nome;
        }

        public Long getId() {
            return id;
        }

        public void setId(Long id) {
            this.id = id;
        }

        public String getNome() {
            return nome;
        }

        public void setNome(String nome) {
            this.nome = nome;
        }
    }

    public class Autor {
        private Long id;
        private String nome;

        public Autor() {}

        public Autor(Long id, String nome) {
            this.id = id;
            this.nome = nome;
        }

        public Long getId() {
            return id;
        }

        public void setId(Long id) {
            this.id = id;
        }

        public String getNome() {
            return nome;
        }

        public void setNome(String nome) {
            this.nome = nome;
        }
    }

### 4.2 DAO (assinaturas mínimas que um CRUD precisa)
A ideia é manter a mesma “cara” do DAO de Aluno:

    import java.util.List;
    import java.util.Optional;

    public interface EditoraDAO {
        Long criar(Editora editora);
        Optional<Editora> buscarPorId(Long id);
        List<Editora> buscarPorNome(String nome);
        boolean atualizar(Long id, Editora editora);
        boolean excluir(Long id);
    }

    import java.util.List;
    import java.util.Optional;

    public interface AutorDAO {
        Long criar(Autor autor);
        Optional<Autor> buscarPorId(Long id);
        List<Autor> buscarPorNome(String nome);
        boolean atualizar(Long id, Autor autor);
        boolean excluir(Long id);
    }

### 4.3 Service (valida, decide status, chama DAO)
Aqui você centraliza regras. Exemplo de validação mínima (sem jargão):

    import java.util.List;

    public class EditoraService {
        private final EditoraDAO dao;

        public EditoraService(EditoraDAO dao) {
            this.dao = dao;
        }

        public Long criar(Editora editora) {
            validarEditora(editora);
            return dao.criar(editora);
        }

        public Editora buscarPorId(Long id) {
            return dao.buscarPorId(id).orElseThrow(() -> new RuntimeException("Editora não encontrada"));
        }

        public List<Editora> buscarPorNome(String nome) {
            List<Editora> lista = dao.buscarPorNome(nome);
            if (lista == null || lista.isEmpty()) {
                throw new RuntimeException("Editora não encontrada");
            }
            return lista;
        }

        public Editora atualizar(Long id, Editora editora) {
            validarEditora(editora);

            boolean ok = dao.atualizar(id, editora);
            if (!ok) {
                throw new RuntimeException("Editora não encontrada");
            }
            return buscarPorId(id);
        }

        public void excluir(Long id) {
            boolean ok = dao.excluir(id);
            if (!ok) {
                throw new RuntimeException("Editora não encontrada");
            }
        }

        private void validarEditora(Editora editora) {
            if (editora == null) {
                throw new IllegalArgumentException("Corpo da requisição é obrigatório");
            }
            if (editora.getNome() == null || editora.getNome().trim().isEmpty()) {
                throw new IllegalArgumentException("Nome da editora é obrigatório");
            }
        }
    }

O `AutorService` segue a mesma lógica (troca Editora por Autor).

### 4.4 Controller (converte HTTP ↔ Service)
Sem depender do framework exato do esqueleto, o padrão é:

- `POST` cria → devolve `201 Created` + ID
- `GET` retorna item/lista → `200 OK`
- `PUT` atualiza → `200 OK` + JSON atualizado
- `DELETE` remove → `204 No Content`

Se o esqueleto já tem um Controller de Aluno, o mais seguro é **copiar o formato dele** (anotações e retornos) e adaptar.

---

## 🛡️ Aula 5 — Status HTTP e erros (mapeamento que você já descreveu)

Você definiu regras importantes:

- Delete:
  - sucesso: `204 No Content`
  - id inexistente: `404 Not Found`
  - erro SQL: `409 Conflit`

- Update:
  - sucesso: `200 OK` + JSON atualizado
  - id inexistente: `404 Not Found`
  - erro SQL: `409 Conflit`

Para ficar consistente em tudo:
- Erro de validação (campo obrigatório/formato): `400 Bad Request`
- Não autenticado: `401 Unauthorized`
- Sem permissão: `403 Forbidden`

Trade-off (bem direto):
- Mapear erro por status deixa a API mais “profissional”, mas exige disciplina para padronizar as respostas.

---

## 🔐 Aula 6 — Segurança (JWT): regra de acesso (como modelar)

Requisito:
- **Operação pública**: consulta de livros pelos alunos
- **Operações restritas**: todo o resto (CRUD e empréstimo/devolução)

Modelo mental simples:
- Rotas públicas: apenas “buscar livros”
- Rotas privadas: exige token (JWT) no header

Header típico:
- `Authorization: Bearer <token>`

Checklist de teste:
1) Chamar rota privada sem token → deve dar `401`
2) Chamar rota privada com token sem permissão → deve dar `403` (se houver roles)
3) Chamar rota pública sem token → deve funcionar

---

## 🧪 Aula 7 — Exercícios práticos (para implementar Editora e Autor sem copiar)

### Exercício 1 — Replicar CRUD do Aluno (Editora)
1) Crie `Editora` (model) com campos do banco
2) Crie `EditoraDAO` copiando o padrão do `AlunoDAO`
3) Crie `EditoraService`:
   - validar obrigatórios (NOT NULL)
   - decidir “não encontrado”
4) Crie `EditoraController` com as rotas

### Exercício 2 — Replicar CRUD do Aluno (Autor)
Mesma sequência do Exercício 1, agora para Autor.

### Exercício 3 — Padronização das respostas
Faça todas as rotas:
- devolverem status corretos
- devolverem JSON consistente quando for `200/201`
- não devolverem corpo em `204`

---

## 🧹 Correções de escrita (sem alterar o original)

- “usuarios” → “usuários”
- “emprestimos” → “empréstimos”
- “devoluções” ok
- “Conflit” → “Conflict”
- “jSON” → “JSON”
- “parametros” → “parâmetros”

---

<!-- nav_start -->
---
Anterior: [171 Primeiro Projeto Spring Boot](../docs/171_Primeiro_Projeto_Spring_Boot.md) | Proximo: [501 Orientacoes](../docs/501_Orientacoes.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->