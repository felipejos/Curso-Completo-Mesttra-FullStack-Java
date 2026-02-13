# SpringBoot

---

## Link
https://roadmap.sh/spring-boot

---

## Complemento da Lição

### 🎯 Para que serve esse roadmap
Usar como trilha para dominar **Spring Boot** e conseguir criar APIs e sistemas de Back-End com:
- rotas/endpoints (Controller)
- regras (Service)
- banco de dados (JPA/Hibernate)
- validação, erros e segurança
- testes e deploy

---

### 🧭 Ordem prática de estudo (sequência recomendada)
1) **Estrutura do projeto**
   - `pom.xml`
   - `src/main/java`
   - `src/main/resources`
   - `application.properties` / `application.yml`

2) **Web / REST**
   - `@RestController`
   - `@RequestMapping`, `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`
   - `@PathVariable`, `@RequestParam`, `@RequestBody`

3) **Injeção de dependência (DI)**
   - `@Component`, `@Service`, `@Repository`
   - `@Autowired` (e o porquê de preferir construtor)

4) **Modelagem e persistência**
   - `@Entity`, `@Id`, `@GeneratedValue`
   - relacionamento: `@OneToMany`, `@ManyToOne`
   - `JpaRepository`

5) **DTO + validação**
   - separar o que entra/saí da API do que é a entidade
   - `@Valid` + Bean Validation (`@NotNull`, `@NotBlank`, `@Size`, etc.)

6) **Tratamento de erros**
   - `@ControllerAdvice`
   - respostas padronizadas de erro

7) **Segurança**
   - Spring Security
   - login + JWT (conceito + prática)

8) **Testes**
   - unitário (Service)
   - integração (Controller)
   - Testcontainers (nível mais avançado)

9) **Documentação**
   - OpenAPI/Swagger

10) **Deploy**
   - build e variáveis de ambiente
   - subir API em uma plataforma

---

### ✅ Checklist “mínimo profissional” de uma API Spring Boot
- CRUD completo com DTO
- validação de entrada
- tratamento de erro padronizado
- conexão com banco (PostgreSQL)
- testes básicos
- Swagger
- README ensinando rodar

---

### 🧩 Mini-projeto recomendado (para acompanhar o roadmap)
**API de Tarefas**
- Endpoints: criar/listar/detalhar/atualizar/deletar
- Campos: título, descrição, status, data de criação
- Extras: filtro por status e paginação

---

### 🎯 Como estudar sem ficar perdido
Para cada tema do roadmap:
1) aprenda o conceito (1 página)
2) aplique no mini-projeto
3) teste no Postman/Insomnia
4) escreva no README o que fez (isso vira portfólio)

---

<!-- nav_start -->
---
Anterior: [504 BackEnd](../docs/504_BackEnd.md) | Proximo: [506 Banco de Dados](../docs/506_Banco_de_Dados.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
