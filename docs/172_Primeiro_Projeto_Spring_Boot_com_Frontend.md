# Primeiro Projeto Spring Boot + Frontend

---

## 📦 Arquivo do Projeto (FrontEnd + BackEnd)

Arquivo do Projeto FrontEnd + BackEnd: https://drive.google.com/drive/folders/146cYX8Fy4ETh29dgidxyuyHB_POSVhhn

---

## 🧭 Obs (como abrir no VSCode)

Obs: Depois de descompactar o arquivo: abra dois VSCode, em uma das janelas do VSCode abra a pasta agenda_mavem que é o backend. Na outra janela do VSCode abra a pasta agenda_mavem_front

---

## 🎥 Vídeos

Parte 1 - Funcionamento básico da aplicação: https://youtu.be/BXlmN7w_9UE

Parte 2 - Funcionamento básico da aplicação: https://youtu.be/MRnk58-FTpA

Parte 3 - Funcionamento básico da aplicação: https://youtu.be/8df0ujrGKMM

Parte 4 - Funcionamento básico da aplicação: https://youtu.be/Bt5smbo7WY0

---

# Complemento da Lição

---

## 🎯 Objetivo prático deste projeto (em 1 frase)

Rodar **BackEnd (Spring Boot)** + **FrontEnd** juntos, entender como eles “conversam” (requisições HTTP) e aprender a organizar o código por responsabilidades.

---

## 🧱 Módulo 1 — “Mapa mental” da aplicação (BackEnd + FrontEnd)

### BackEnd (agenda_mavem)
Pense em 3 camadas principais:

1) **Controller**  
Recebe requisições (GET/POST/PUT/DELETE) e devolve resposta.

2) **Service**  
Onde ficam as regras do sistema (validações e decisões).

3) **Repository**  
Onde ficam as operações com banco (buscar, salvar, deletar).

> Dica de leitura: controller chama service, service chama repository.

### FrontEnd (agenda_mavem_front)
Pense em 3 partes principais:

1) **Telas/Pages/Views**  
O que o usuário vê.

2) **Componentes**  
Partes reutilizáveis da tela (botões, formulários, listas).

3) **Serviço de API (HTTP)**  
Código que chama o BackEnd (axios/fetch).

---

## ✅ Módulo 2 — Checklist de pré-requisitos (sem adivinhar versões)

Antes de rodar, confira no projeto:

### BackEnd
- Existe `pom.xml` (Maven) ou `build.gradle` (Gradle)
- Qual Java o projeto espera (geralmente aparece no `pom.xml` / `build.gradle`)

### FrontEnd
- Existe `package.json`
- Veja os scripts em `"scripts"` (ex.: `dev`, `start`, `build`)

---

## ▶️ Módulo 3 — Rodando o BackEnd (passo a passo)

Dentro da pasta **agenda_mavem**:

1) Abra o terminal do VSCode nessa pasta.
2) Procure se existe o arquivo **mvnw** (Maven Wrapper).
   - Se existir, o padrão é usar ele.
3) Rode o projeto.

Comandos comuns (use o que existir no seu projeto):

- Se existir `mvnw`:
    ./mvnw spring-boot:run

- Se não existir `mvnw`:
    mvn spring-boot:run

O que observar:
- O console deve mostrar que “subiu” e em qual porta está rodando (muito comum ser `8080`).
- Se aparecer erro de porta em uso, significa que já tem algo usando aquela porta.

---

## ▶️ Módulo 4 — Rodando o FrontEnd (passo a passo)

Dentro da pasta **agenda_mavem_front**:

1) Abra o terminal do VSCode nessa pasta.
2) Instale dependências:
    npm install
3) Rode o projeto:
- Se no `package.json` tiver script `dev`:
    npm run dev
- Se tiver script `start`:
    npm start

O que observar:
- O terminal mostra a URL do FrontEnd (ex.: `http://localhost:3000` ou `http://localhost:5173`).

---

## 🔗 Módulo 5 — Como o FrontEnd “acha” o BackEnd (onde procurar)

Quando dá erro de “não conecta”, procure estes lugares no FrontEnd:

- `src/services/` (ou `src/api/`, `src/utils/`)
- arquivo com nome tipo:
  - `api.js`, `api.ts`, `axios.js`, `http.js`
- variáveis de ambiente:
  - `.env`, `.env.local`
  - `VITE_API_URL`, `REACT_APP_API_URL` (exemplos de nomes)

O que você quer encontrar:
- a **baseURL** (endereço base) do BackEnd, exemplo mental:
  - `http://localhost:8080`

---

## 🧪 Módulo 6 — Como testar se está tudo “conversando” (sem depender do Front)

### Teste 1: BackEnd está vivo?
Procure no BackEnd algum endpoint de teste (às vezes existe um `health`, `hello`, etc).
Se não achar, você pode testar os endpoints do projeto via:
- Postman / Insomnia
- extensão REST Client do VSCode

### Teste 2: FrontEnd chama o BackEnd?
Abra o DevTools do navegador:
- Aba **Network**
- Clique no botão/ação do sistema
- Veja se aparece uma requisição (GET/POST)
- Veja:
  - URL que ele chamou
  - status code (200, 404, 500)
  - mensagem de erro

---

## 🧰 Módulo 7 — Erros comuns (e o que significa)

### 1) 404 no FrontEnd ao chamar API
Significa: a rota não existe no BackEnd ou a URL base está errada.

### 2) CORS bloqueando
Significa: o navegador bloqueou a chamada por política de segurança.
Procure no BackEnd:
- configuração de CORS
- `@CrossOrigin`
- classe de configuração (ex.: `WebMvcConfigurer`)

### 3) 500 no BackEnd
Significa: o BackEnd quebrou por erro interno.
Olhe o console do BackEnd e ache a stacktrace (linha do erro).

---

## 🧠 Módulo 8 — Mini-roteiro de estudo pelos vídeos (para não assistir “no automático”)

Enquanto assiste as Partes 1 a 4, foque em identificar:

1) Qual comando roda o BackEnd?
2) Qual comando roda o FrontEnd?
3) Qual URL o FrontEnd usa para chamar o BackEnd?
4) Quais telas existem e quais endpoints elas chamam?
5) Onde ficam:
   - controller
   - service
   - repository
   - arquivo de chamada HTTP no Front

---

## ✅ Checagem rápida (1 pergunta)

Se o FrontEnd estiver abrindo no navegador, mas **não aparece nenhum dado**, qual é a primeira coisa que você deve olhar?
- Responda com 1 item apenas (ex.: “Aba Network do navegador”, “Console do BackEnd”, etc.)

---

## 🧪 Exercícios (para fixar de verdade)

### Exercício 1 — Mapa de rotas (BackEnd)
Liste:
- 3 endpoints (rota + método: GET/POST/PUT/DELETE)
- e diga em qual Controller eles estão

### Exercício 2 — Onde o FrontEnd chama a API
Encontre o arquivo que faz requisições HTTP e anote:
- qual é a baseURL
- um exemplo de chamada (ex.: “GET /contatos”)

### Exercício 3 — Fluxo completo (tela → API → banco)
Escolha 1 ação do sistema (ex.: “cadastrar item”) e escreva o caminho:
- Tela/Componente → serviço HTTP → endpoint → service → repository

---

<!-- nav_start -->
---
Anterior: [171 Primeiro Projeto Spring Boot](../docs/171_Primeiro_Projeto_Spring_Boot.md) | Proximo: [501 Orientacoes](../docs/501_Orientacoes.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->