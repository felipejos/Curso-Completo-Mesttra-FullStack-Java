# Primeiro Projeto Spring Boot + Frontend Console e Swing

---

## 📦 Arquivo do Projeto (FrontEnd Console e Swing)

Arquivo do Projeto FrontEnd Console e Swing: https://drive.google.com/drive/folders/15JxS6t3Gel0ONAmWUBLeKXjX5dzpIJot?usp=sharing

---

## 🧭 Obs (como abrir no VSCode)

Obs: Depois de descompactar o arquivo: abra três VSCode, em uma das janelas do VSCode abra a pasta agenda_mavem do backend do vídeo anterior. Na outra janela do VSCode abra a pasta agenda_mavem_frontConsole e na última janela do VSCode abra a pasta agenda_mavem_frontSwing

---

## 🎥 Vídeo

Funcionamento básico da aplicação: https://youtu.be/lAtwZLffcf8

---

# Complemento da Lição

---

## 🎯 Objetivo prático do projeto (em 1 frase)

Rodar **1 BackEnd (Spring Boot)** e **2 FrontEnds em Java** (Console e Swing), entendendo como ambos chamam a mesma API via HTTP.

---

## 🧱 Módulo 1 — Visão geral (como as partes se conectam)

Pense em 3 peças:

1) **BackEnd (agenda_mavem)**
- expõe endpoints (rotas) da API, por exemplo:
  - listar, cadastrar, editar, excluir

2) **Front Console (agenda_mavem_frontConsole)**
- interface via terminal (texto)
- faz requisições para a API

3) **Front Swing (agenda_mavem_frontSwing)**
- interface com janelas e botões
- também faz requisições para a mesma API

Fluxo mental:
Front (Console ou Swing) → HTTP → BackEnd → resposta → Front mostra ao usuário

---

## ✅ Módulo 2 — Checklist de preparação (antes de rodar)

### 1) BackEnd
- Verifique se existe `pom.xml` (Maven).
- Veja se tem `mvnw` (Maven Wrapper).

### 2) Front Console / Swing
- Verifique se são projetos Java (normalmente com `src/` e classes `.java`).
- Procure se existe:
  - `pom.xml` (se também for Maven), ou
  - estrutura simples com `Main.java` para rodar no VSCode.

---

## ▶️ Módulo 3 — Rodando o BackEnd (passo a passo)

Na pasta **agenda_mavem** (janela 1 do VSCode):

1) Abra o terminal nessa pasta.
2) Suba o servidor.

Comandos comuns:

- Com wrapper:
    ./mvnw spring-boot:run

- Sem wrapper:
    mvn spring-boot:run

O que conferir:
- Console mostrando que está rodando.
- Porta (normalmente `8080`).

---

## ▶️ Módulo 4 — Rodando o Front Console (passo a passo)

Na pasta **agenda_mavem_frontConsole** (janela 2 do VSCode):

1) Encontre a classe principal (geralmente `Main`).
2) Execute pelo VSCode:
- botão **Run** / **Run Java**
ou
- terminal com compilação e execução, se necessário.

O que observar:
- o programa deve mostrar um menu no terminal.
- ao escolher opções, ele deve chamar a API.

---

## ▶️ Módulo 5 — Rodando o Front Swing (passo a passo)

Na pasta **agenda_mavem_frontSwing** (janela 3 do VSCode):

1) Encontre a classe principal (a que tem `public static void main`).
2) Execute no VSCode.

O que observar:
- abre uma janela (GUI)
- botões e campos disparam ações que chamam a API.

---

## 🔗 Módulo 6 — Onde configurar a URL da API (o ponto mais importante)

Quando o Front não “acha” o BackEnd, quase sempre é a URL base.

Procure nos dois frontends por:
- `http://localhost:8080`
- `baseUrl`
- `URL`
- `API_URL`
- classe com nome tipo:
  - `ApiService`, `HttpClient`, `ClienteHttp`, `Requisicao`, `Conexao`

Objetivo:
- Console e Swing precisam apontar para o **mesmo endereço** do BackEnd.

---

## 🧪 Módulo 7 — Teste rápido para saber se está tudo OK

### Teste 1 — BackEnd está vivo
- Rode o BackEnd e veja se não há erro no console.

### Teste 2 — Front Console funciona
- Execute uma operação simples (ex.: listar contatos).
- Se der erro:
  - anote a mensagem e o status (se aparecer).

### Teste 3 — Front Swing funciona
- Clique em “listar” ou ação equivalente.
- Se não carregar:
  - olhe o console do VSCode (às vezes o Swing loga lá).

---

## ⚠️ Módulo 8 — Erros comuns (e como interpretar)

### 1) “Connection refused” / “não conecta”
- BackEnd não está rodando
- ou a porta está errada
- ou a URL base está errada

### 2) 404 (rota não existe)
- Front chamou um endpoint que não existe
- ou o path está diferente no BackEnd

### 3) CORS
- Normalmente afeta Front no navegador.
- Console e Swing geralmente não sofrem CORS (porque não é browser).
- Se der erro, costuma ser outro (URL/rota/servidor).

### 4) Erros de JSON (parse)
- BackEnd devolveu um JSON num formato diferente do que o Front espera.

---

## 🧠 Módulo 9 — Atividade guiada (para você confirmar que entendeu)

Explique com 1 frase:
- Qual é a diferença prática entre o **Front Console** e o **Front Swing** neste projeto?

(Responda só com 1 frase.)

---

## 🧪 Exercícios (para fixar)

1) Ache no Console onde está a chamada HTTP e diga:
- qual URL ele usa
- qual endpoint ele chama para “listar”

2) Ache no Swing onde está a chamada HTTP e diga:
- qual URL ele usa
- qual endpoint ele chama para “cadastrar”

3) Faça um “mapa de fluxo” de 1 ação:
- clicar no botão (Swing) → método chamado → requisição HTTP → controller no BackEnd

---

<!-- nav_start -->
---
Anterior: [171 Primeiro Projeto Spring Boot](../docs/171_Primeiro_Projeto_Spring_Boot.md) | Proximo: [501 Orientacoes](../docs/501_Orientacoes.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->