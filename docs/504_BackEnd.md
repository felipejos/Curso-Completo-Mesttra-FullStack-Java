# BackEnd

---

## Link
https://roadmap.sh/backend

---

## Complemento da Lição

### 🎯 Para que serve esse roadmap
Usar como trilha para aprender **Back-End** (a parte do sistema que roda no servidor) e conseguir:
- criar **APIs** (rotas/endpoints)
- aplicar **regras de negócio**
- acessar **banco de dados**
- trabalhar com **autenticação** e **segurança**
- publicar a aplicação

---

### 🧭 Ordem prática de estudo (sequência recomendada)
1) **HTTP e APIs**
   - métodos: GET/POST/PUT/DELETE
   - status codes (200, 201, 400, 401, 404, 500)
   - JSON (request/response)

2) **Linguagem + Framework**
   - no seu caso: **Java + Spring Boot**
   - controllers, services, DTOs

3) **Banco de dados**
   - SQL básico (SELECT/INSERT/UPDATE/DELETE)
   - modelagem (tabelas, chaves, relacionamentos)
   - ORM (JPA/Hibernate no Spring)

4) **Autenticação e autorização**
   - login (tokens)
   - JWT (conceito e uso)
   - permissões (roles)

5) **Testes**
   - unitários (Service)
   - integração (Controller/API)

6) **Boas práticas**
   - validação de entrada
   - logs
   - tratamento de erros (responses consistentes)

7) **Deploy**
   - variáveis de ambiente
   - build
   - subir em uma plataforma (ex.: Render, Railway, Fly.io, VPS)

---

### ✅ Checklist mínimo para um “Back-End pronto para portfólio”
- CRUD completo (criar/listar/atualizar/deletar)
- validação de dados (não aceitar inválidos)
- respostas padronizadas (JSON claro)
- autenticação (mesmo simples)
- conexão com banco (ex.: PostgreSQL)
- README explicando como rodar

---

### 🧩 Mini-projetos (ordem que evolui bem)
1) **API de Tarefas** (CRUD + validação)
2) **API de Loja** (produtos + categorias)
3) **API com Login** (JWT + permissões)
4) **API com testes** (camadas bem separadas)
5) **API publicada** (deploy + doc)

---

### 🔗 Conexão direta com o seu Spring Boot
O roadmap do Back-End vira muito mais simples se você mapear tudo assim:
- **Controller** → recebe HTTP
- **Service** → regras
- **Repository** → banco
- **DTO** → entrada/saída
- **Exception Handler** → erros bonitos

---

<!-- nav_start -->
---
Anterior: [503 FrontEnd](../docs/503_FrontEnd.md) | Proximo: [505 SpringBoot](../docs/505_SpringBoot.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
