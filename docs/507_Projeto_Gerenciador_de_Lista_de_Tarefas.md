# Gerenciador de Lista de Tarefas

---

## Contexto

Gerado inicialmente pelo chatgpt e ajustado pelo instrutor.

Prompt Utilizado: Sugira para estudantes de programação um projeto de back end do tipo todo-list que possa ser desenvolvido para compor um portifolio. Crie uma extensa explicação das funcionalidades, modelo de dados e demais informações relevantes para que o desenvolvedor saiba o que implementar.

---

## Descrição geral

Este projeto consiste em desenvolver um sistema backend no formato API RESTful, ou pacote com classes onde os usuários poderão criar, gerenciar, organizar e acompanhar tarefas. O sistema deve permitir CRUD completo, filtros, autenticação (opcional, mas recomendado) e boas práticas de API.

---

## Objetivos principais do projeto

Esta API serve para demonstrar domínio de:

- Criação de endpoints REST
- Organização de código backend (MVC, Services, Controllers)
- Persistência de dados em banco de dados
- Tratamento de erros
- Validações
- Autenticação com JWT
- Operações CRUD reais
- Paginação e filtros
- Documentação

---

## Modelo de Dados Sugerido

Tabela: tarefa

| Campo                  | Tipo               | Descrição                                                                 |
|------------------------|--------------------|---------------------------------------------------------------------------|
| id                     | inteiro            | Identificador único                                                       |
| titulo                 | string             | Título da tarefa                                                          |
| descricao              | string (opcional)  | Detalhes da tarefa                                                        |
| completada             | boolean            | Se a tarefa está concluída                                                |
| prioridade             | enum               | prioridade (baixa, média, alta)                                           |
| data _limite           | date (opcional)    | Data limite                                                               |
| data_criacao           | datetime           | Data de criação                                                           |
| data_ultima_atualizacao| datetime           | Data da última atualização                                                |
| id_usuario             | inteiro            | (Opcional) Relacionamento com usuário caso queira que o sistema seja multi usuário |

Esse modelo pode crescer conforme a versão do projeto.

---

## Explicação Completa das Funcionalidades

A seguir, cada funcionalidade é explicada em detalhes, com foco tanto no valor para o usuário quanto na implementação no backend.

---

### 1️ - Criar nova tarefa (Create – POST /tasks)

O que deve acontecer  
O usuário envia para a API um título e, opcionalmente, descrição, prioridade e data limite.  
A API:

- Valida os dados.
- Cria o registro no banco.
- Retorna a tarefa criada com o ID gerado.

Pontos importantes:
- O título deve ser obrigatório.
- prioridade deve aceitar apenas valores válidos (ex: 1,2,3 ou “baixa/média/alta”).
- data_limite deve ser uma data válida e não pode ser no passado (opcional).
- A tarefa deve iniciar com completada = false.

Validações comuns:
- título vazio → erro 400
- prioridade inválida → erro 422
- data inválida → erro 422

---

### 2 - Listar todas as tarefas (Read – GET /tasks)

O que deve acontecer  
A API retorna uma lista de tarefas.  
Aqui entram pontos importantes de qualidade:

Filtros opcionais:
- completada=true/false → listar por status
- prioridade=alta → filtrar por prioridade
- data_limite=2025-01-10 → filtrar por data limite
- busca=palavra → buscar por título ou descrição

Paginação:
- ?page=1
- ?limit=10

A API deve retornar:

    {
      "page": 1,
      "total_pages": 10,
      "total_items": 94,
      "items": [ ... ]
    }

---

### 3️ - Buscar uma tarefa específica (GET /tasks/:id)

O que deve acontecer  
Retorna os dados de uma tarefa pelo ID.

Tratamento de erros:
- ID inválido → erro 400
- Tarefa não encontrada → erro 404

---

### 4️ - Atualizar uma tarefa (PUT ou PATCH /tasks/:id)

Tipos de atualização:
- PUT → atualiza todos os campos
- PATCH → atualiza apenas os enviados

Permite alterar:
- título
- descrição
- prioridade
- completada(true/false)
- data_limite

Regras importantes:
- Se o usuário tentar marcar como concluída e já está concluída, retornar sucesso da mesma forma → idempotência
- Atualizar data_ultima_atualizacao automaticamente

---

### 5️ - Excluir uma tarefa (DELETE /tasks/:id)

Deve:
- Verificar se a tarefa existe
- Excluir permanentemente
- Retornar 204 sem body

Alternativa:
Implementar exclusão lógica:
- adicionar campo excluido = true no banco de dados
- remover só logicamente
- excluir fisicamente apenas via processo futuro

---

### 6️ - Marcar tarefa como concluída (PATCH /tasks/:id/complete)

Funcionalidade específica muito comum em apps de tarefas.

O que faz:
- Define completada = true
- Registra a data de conclusão ( opcional )
- Atualiza data_ultima_atualizacao

Boas práticas:
- Se já estiver concluída, retornar apenas o status atual sem erro
- Retornar a tarefa atualizada

---

### 7️ - Desmarcar tarefa como concluída (PATCH /tasks/:id/uncomplete)

O que faz:
- completed = false
- remove data de conclusão
- Mostra compreensão de estados da aplicação.

---

### 8️ - Definir prioridade da tarefa (PATCH /tasks/:id/priority)

Exemplo de corpo:
    { "prioridade": "alta" }

Regras:
- Aceitar somente valores pré-definidos
- Retornar erro caso seja inválido

Implementar isso mostra domínio de validações customizadas.

---

### 9️ - Autenticação (Opcional mas muito recomendada)

Adicionar autenticação dá valor enorme ao portfólio.

O sistema deve permitir:
- cadastro de usuário (POST /users)
- login (POST /auth/login)
- gerar token JWT
- rotas protegidas

Cada tarefa pertence a um usuário  
tasks.user_id = id do usuário logado

GET /tasks retorna só as tarefas do usuário

Diferencial:
Implementar Refresh Token + Logout.

---

### Documentação da API (Swagger ou Postman)

Recrutadores valorizam muito.

A documentação deve conter:
- Descrição de cada rota
- Parâmetros
- Exemplo de entrada
- Exemplo de saída
- Códigos de erro

---

### 11 - Tratamento global de erros

Outro grande diferencial.

A API deve retornar:
- 400 → erro do usuário
- 401 → não autenticado
- 403 → proibido
- 404 → não encontrado
- 422 → validação
- 500 → erro interno

Com formato:
    { "error": "ValidationError", "message": "Title is required" }

---

### 12 - Logs e auditoria

Pontuação extra em qualquer portfólio.

Incluir:
- logs de requisição (method, url, tempo de resposta)
- logs de erro
- logs de autenticação (login, logout)

---

### 13 - Testes automatizados (opcional mas deixa excelente)

Testar:
- criação de tarefa
- atualização
- filtros
- autenticação
- erros 404

Pode usar Jest, JUnit, PyTest etc.

---

## Funcionalidades Extras Para Turbinar a API

Etiquetas (tags)  
Cada tarefa pode ter uma ou várias tags.

Tarefas recorrentes
- diária
- semanal
- mensal

Notificações (simuladas)  
Enviar email quando a data estiver próxima.

Arquivamento  
Mover tarefas antigas para um “arquivo”.

---

## Dicas para o portfólio ficar realmente forte

- Sempre escreva README completo (objetivo, rotas, como rodar)
- Use migrations (Sequelize, Prisma, Hibernate, etc.)
- Utilize rotas REST bem definidas
- Testes automatizados (Jest, JUnit, PyTest…)
- Docker para subir o ambiente
- Demonstre arquitetura (MVC, Services, Repository etc.)
- Coloque link para documentação (Swagger / Postman)

---

## Por que este projeto é muito forte para portfólio?

Porque ele demonstra:

- domínio de CRUD completo
- lógica de negócio
- filtros e paginação
- autenticação JWT
- validações robustas
- boas práticas REST
- documentação
- testes
- arquitetura clara
- manipulação de datas
- tratamento de erros

---

# Complemento da Lição

---

## Visão de arquitetura (camadas) para implementar com organização profissional

- Controller
  - recebe HTTP (path, query, body)
  - valida formato básico (ex.: @Valid em DTO)
  - chama Service e devolve Response

- Service
  - regras de negócio (ex.: data_limite não pode ser no passado)
  - idempotência (ex.: “complete” repetido não dá erro)
  - coordena repositórios e conversões DTO ↔ entidade

- Repository
  - acesso ao banco (CRUD e consultas filtradas/paginadas)

- DTOs
  - entrada: CreateTaskRequest / UpdateTaskRequest
  - saída: TaskResponse
  - evita expor detalhes internos do banco

- Handler de erros global
  - padroniza respostas 400/401/403/404/422/500

---

## Padrão de paginação e filtros (contrato claro)

Query params sugeridos:
- page (inteiro, começa em 1)
- limit (inteiro, ex.: 10/20/50)
- completada (true/false)
- prioridade (baixa|média|alta)
- data_limite (YYYY-MM-DD)
- busca (string)

Formato de retorno (já no seu texto) com detalhes úteis:
- page
- total_pages
- total_items
- items

---

## Regras de negócio que valem como “critérios de aceite”

- título obrigatório e não vazio
- prioridade somente valores permitidos (enum)
- data_limite opcional, mas se existir:
  - precisa ser válida
  - não pode ser no passado
- completada inicia false
- data_criacao definida na criação
- data_ultima_atualizacao muda em toda alteração
- complete/uncomplete são idempotentes:
  - chamar 2 vezes seguidas não deve causar erro, apenas manter o estado

---

## Sugestão de entregas por versões (para não travar)

### V1 — CRUD básico
- POST /tasks
- GET /tasks
- GET /tasks/{id}
- PUT/PATCH /tasks/{id}
- DELETE /tasks/{id}
- validações essenciais + erros 400/404/422

### V2 — Filtros e paginação
- filtros por completada/prioridade/data_limite/busca
- paginação page/limit + retorno paginado

### V3 — Segurança (JWT)
- users + login
- rotas protegidas
- tasks do usuário logado

### V4 — Qualidade de portfólio
- Swagger/OpenAPI
- logs
- testes (Service + Controller)
- Docker + migrations

---

## Casos de teste mínimos (para garantir robustez)

- criar tarefa com título vazio → 400 ou 422 (conforme contrato)
- criar tarefa com prioridade inválida → 422
- criar tarefa com data_limite no passado → 422
- buscar por id inexistente → 404
- complete em tarefa já completa → 200 (idempotente)
- paginação: page fora do intervalo → retorno coerente (sem quebrar)

---

## Exercício de fixação (1 passo)
Escreva (em português mesmo) as 3 partes do endpoint **POST /tasks**:
- Entrada (campos obrigatórios e opcionais)
- Processamento (regras e validações)
- Saída (status + corpo de resposta)

---