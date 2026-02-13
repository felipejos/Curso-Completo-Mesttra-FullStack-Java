# Primeiro Projeto Spring Boot

---

## Primeiro Projeto Spring Boot
Projeto exemplo Spring Boot apresentado no dia 12/02/2026

Vídeo: https://youtu.be/xct9jIiwJ8k

[![Assistir no YouTube](https://img.youtube.com/vi/xct9jIiwJ8k/hqdefault.jpg)](https://youtu.be/xct9jIiwJ8k)

Código: https://drive.google.com/drive/folders/1a2WOA_IPDou0GggNIpGBiLgHe80cY-43?usp=sharing

---

## Complemento da Lição

### 🎯 Objetivo do projeto (o que você deve aprender aqui)
- Entender o “esqueleto” de uma aplicação **Spring Boot**
- Rodar a aplicação localmente e confirmar que está funcionando
- Identificar onde ficam:
  - **Controllers** (rotas/endpoints)
  - **Services** (regras de negócio)
  - **Repositories** (acesso a dados, quando existir)
  - **Configurações** (`application.properties` ou `application.yml`)

---

### ✅ Checklist rápido (para validar que você entendeu o projeto)
- Você consegue apontar onde está a classe `...Application` (a que tem o `main`)
- Você consegue rodar o projeto e ver que **subiu** sem erro no console
- Você consegue chamar pelo navegador ou pelo Postman algum endpoint (ex.: `/`, `/hello`, `/api/...`) caso exista
- Você consegue explicar o “caminho” de uma requisição:
  **Controller → Service → (Repository) → resposta**

---

### 🧩 Passo a passo de estudo (sem inventar detalhes do código)
1) Abra o projeto e procure por:
   - `pom.xml` (dependências)
   - `src/main/java/...` (código Java)
   - `src/main/resources/application.properties` (configurações)
2) Identifique a classe principal (a que tem `public static void main`).
3) Procure por classes com `@RestController` ou `@Controller`.
4) Dentro do controller, observe as anotações de rota:
   - `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`
5) Verifique se há classes com `@Service` e se o controller chama essas classes.

---

### 🧠 Vocabulário essencial (em português simples)
- **Endpoint/Rota**: o “caminho” que você acessa (ex.: `/produtos`)
- **Controller**: a “porta de entrada” que recebe a requisição
- **Service**: onde ficam as regras (ex.: validar, calcular, decidir)
- **Repository**: onde o código conversa com banco de dados (quando existir)
- **DTO**: objeto usado para transportar dados (entrada/saída)

---

### 🧪 Exercícios rápidos (para fixar)
1) Anote 3 endpoints que existirem no projeto e diga:
   - método (GET/POST/PUT/DELETE)
   - caminho
   - o que ele retorna (texto/JSON)
2) Pegue 1 endpoint e responda:
   - qual método Java é executado?
   - ele chama algum service? qual?
3) Se existir `application.properties`, encontre:
   - porta (`server.port`)
   - configuração de banco (se houver)

---

<!-- nav_start -->
---
Anterior: [169 Protocolo HTTP](../docs/169_Protocolo_HTTP.md) | Proximo: [501 Orientacoes](../docs/501_Orientacoes.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
