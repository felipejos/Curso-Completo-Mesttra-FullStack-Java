# Vídeo: Esqueleto API Spring Boot

Vídeo: https://youtu.be/7yUOZ4_L8vU

Arquivo: https://drive.google.com/file/d/1ebXMwaMCcIUdoE7Kvje_X3rPHSHq16D1/view?usp=sharing

---

# Complemento da Lição

---

## 🎯 O que significa “esqueleto” de uma API (bem simples)

Um **esqueleto** é a base do projeto pronta para você só “plugar” as regras de negócio depois.

Em uma API Spring Boot, isso normalmente inclui:
- **estrutura de pastas**
- **dependências**
- **configuração de execução**
- **primeiros endpoints (rotas)**
- **padrão de camadas** (para o código não virar bagunça)

---

## 🧱 Visão de camadas (arquitetura bem comum em API)

Pense como uma “fila de atendimento”:

1) **Controller** (porta de entrada)
- recebe a requisição HTTP (GET/POST/PUT/DELETE)
- valida entrada
- chama o service

2) **Service** (regras do negócio)
- decide o que pode e não pode
- chama o repositório quando precisa salvar/buscar dados

3) **Repository** (acesso a dados)
- conversa com banco (via Spring Data JPA, por exemplo)

4) **Domain/Entity + DTO**
- **Entity**: representa a tabela/objeto do banco (quando você usa JPA)
- **DTO**: “objeto de entrada/saída” para a API (evita expor a entity direto)

---

## 🗂️ Estrutura de pastas recomendada (organização profissional, mas simples)

Exemplo (padrão por “feature” ou por “camadas”; aqui está por camadas):

    src/main/java/com/seuprojeto/
        controller/
        service/
        repository/
        domain/         (ou entity/)
        dto/
        exception/
        config/

    src/main/resources/
        application.properties (ou application.yml)

Ideia prática:
- se você sabe “onde colocar cada coisa”, você programa mais rápido e erra menos.

---

## 🧩 Dependências mínimas (o básico para uma API nascer)

No Spring Boot, as “peças” vêm por dependências.

Mínimo comum:
- `spring-boot-starter-web` (para API REST)
- `spring-boot-starter-validation` (validações: @NotNull, @Size...)
- (opcional) `spring-boot-starter-data-jpa` + driver do banco (se tiver persistência)
- (opcional) `lombok` (reduzir código repetitivo, mas não é obrigatório)

---

## 🚦 Fluxo de execução (como a requisição “anda”)

Quando alguém chama um endpoint:

Cliente (Postman/Front)  
→ Controller (recebe HTTP)  
→ Service (regras)  
→ Repository (banco)  
→ Service (monta resposta)  
→ Controller (retorna HTTP)

Você pode usar isso como checklist mental:
- “Se deu erro, em que etapa está quebrando?”

---

## 🧪 Esqueleto mínimo de código (para entender, não para decorar)

### 1) Controller (porta de entrada)
    import org.springframework.web.bind.annotation.GetMapping;
    import org.springframework.web.bind.annotation.RequestMapping;
    import org.springframework.web.bind.annotation.RestController;

    @RestController
    @RequestMapping("/api")
    public class HealthController {

        @GetMapping("/health")
        public String health() {
            return "OK";
        }
    }

O que isso prova:
- seu projeto sobe
- seu endpoint responde

### 2) Service (regras)
    import org.springframework.stereotype.Service;

    @Service
    public class ExemploService {

        public String mensagem() {
            return "Regra de negócio aqui";
        }
    }

---

## ▶️ Como “validar” se o esqueleto está correto (checklist de iniciante)

Ao abrir/rodar o projeto, confira:

1) Existe uma classe principal com:
- `@SpringBootApplication`

2) O projeto sobe e mostra no console que está rodando (porta 8080 por padrão)

3) Você consegue testar ao menos 1 endpoint:
- exemplo: `GET /api/health`

4) A estrutura faz sentido:
- controller não tem regra de negócio pesada
- service não imprime no console como “saída final”
- repository não tem regra do sistema, só acesso a dados

---

## 🧭 Como estudar o ZIP (arquivo do Drive) sem se perder

Quando você abrir o arquivo do Drive (zip do projeto), procure:

- `pom.xml` (Maven) ou `build.gradle` (Gradle)
  - aqui você vê as dependências

- `src/main/resources/application.properties` (ou `.yml`)
  - aqui você vê porta, banco, configs

- `src/main/java/.../` (pacote base)
  - veja se tem pastas: controller/service/repository

- `README.md` (se existir)
  - normalmente tem como rodar

---

## 🧠 Exercícios (para você reescrever sem copiar, do jeito certo)

1) **Esqueleto mínimo**
- Crie uma API que responda:
  - `GET /api/health` → `OK`

2) **Controller → Service**
- Faça o controller chamar um service e retornar a mensagem do service.

3) **DTO (entrada/saída)**
- Crie um endpoint:
  - `POST /api/echo`
- Recebe um DTO com um texto e devolve o mesmo texto.
  - (Objetivo: treinar RequestBody e Response)

4) **Organização**
- Garanta que:
  - Controller só recebe e responde
  - Service decide e processa

---

<!-- nav_start -->
---
Anterior: [169 Protocolo HTTP](../docs/169_Protocolo_HTTP.md) | Proximo: [171 Primeiro Projeto Spring Boot](../docs/171_Primeiro_Projeto_Spring_Boot.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
