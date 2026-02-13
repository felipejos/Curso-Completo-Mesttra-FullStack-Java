# Vídeo: Primeira Aplicação de Console com o Banco de Dados

---

## Orientações (conteúdo fornecido)

Vídeo: Primeira Aplicação de Console com o Banco de Dados
Gerenciando contatos com o banco de dados. Assista os vídeos na sequência. Em todos os vídeos, implemente o seu código junto com o vídeo. Não vá  para o próximo vídeo sem fazer a sua própriaimplementação. Faça as anotações dos pontos de dúvidas para discutirmos posteriormente.

---

## Sequência de vídeos (conteúdo fornecido)

Contatos com MySQL: 1 -  Preparando o Projeto

https://youtu.be/1Bo-8gjb9mA 

[![Contatos com MySQL: 1 - Preparando o Projeto](https://img.youtube.com/vi/1Bo-8gjb9mA/hqdefault.jpg)](https://youtu.be/1Bo-8gjb9mA)

---

Contatos com MySQL: 2 -  Adicionando o Driver de Conexão

https://youtu.be/R3pSUqGcaXQ   

[![Contatos com MySQL: 2 - Adicionando o Driver de Conexão](https://img.youtube.com/vi/R3pSUqGcaXQ/hqdefault.jpg)](https://youtu.be/R3pSUqGcaXQ)

---

Contatos com MySQL: 3 - Inserindo os Contatos

https://youtu.be/Xk2sIOHkTo8

[![Contatos com MySQL: 3 - Inserindo os Contatos](https://img.youtube.com/vi/Xk2sIOHkTo8/hqdefault.jpg)](https://youtu.be/Xk2sIOHkTo8)

---

Contatos com MySQL: 4 - Consultando todos os contatos

https://youtu.be/Ju2v70F9MDs

[![Contatos com MySQL: 4 - Consultando todos os contatos](https://img.youtube.com/vi/Ju2v70F9MDs/hqdefault.jpg)](https://youtu.be/Ju2v70F9MDs)

---

Contatos com MySQL: 5 - Consultando contatos por ID e Nome

https://youtu.be/8DxFcFcHnN4

[![Contatos com MySQL: 5 - Consultando contatos por ID e Nome](https://img.youtube.com/vi/8DxFcFcHnN4/hqdefault.jpg)](https://youtu.be/8DxFcFcHnN4)

---

Contatos com MySQL: 6 -  Excluir contato por ID

https://youtu.be/fl0pYfE4KuM

[![Contatos com MySQL: 6 - Excluir contato por ID](https://img.youtube.com/vi/fl0pYfE4KuM/hqdefault.jpg)](https://youtu.be/fl0pYfE4KuM)

---

Contatos com MySQL: 7 - Alterar contato por ID

https://youtu.be/usgczCLtNyE

[![Contatos com MySQL: 7 - Alterar contato por ID](https://img.youtube.com/vi/usgczCLtNyE/hqdefault.jpg)](https://youtu.be/usgczCLtNyE)

---
# Complemento da Lição

## 1) O que você vai construir ao final (visão clara)
Depois dessa sequência, você terá um CRUD completo no console usando MySQL:

- **Create**: inserir contato
- **Read**: listar todos e buscar por id/nome
- **Update**: alterar contato por id
- **Delete**: excluir contato por id

---

## 2) Checklist por vídeo (para garantir que você não avance sem concluir)

### Vídeo 1 — Preparando o Projeto
- [ ] Projeto Java criado (IDE ou Maven/Gradle)
- [ ] Estrutura de pastas organizada (packages)
- [ ] Classe `App` com menu inicial no console
- [ ] Rodou e mostrou o menu sem erro

### Vídeo 2 — Adicionando o Driver de Conexão
- [ ] Dependência do driver MySQL adicionada (Maven/Gradle ou jar)
- [ ] Driver reconhecido pela IDE
- [ ] Teste de conexão simples funcionando

### Vídeo 3 — Inserindo os Contatos
- [ ] Criou tabela no MySQL (ou confirmou que já existe)
- [ ] Inserção via SQL preparado (PreparedStatement)
- [ ] Validou no banco que o registro entrou

### Vídeo 4 — Consultando todos os contatos
- [ ] SELECT funcionando
- [ ] Lista aparece no console formatada
- [ ] Testou com 2+ registros para validar

### Vídeo 5 — Consultando por ID e Nome
- [ ] Busca por ID retorna 1 registro
- [ ] Busca por nome retorna lista (ou 1) conforme seu SQL
- [ ] Tratou “não encontrado” com mensagem clara

### Vídeo 6 — Excluir por ID
- [ ] Excluiu um registro existente
- [ ] Tentou excluir um ID inexistente e viu mensagem correta
- [ ] Confirmou no MySQL que sumiu

### Vídeo 7 — Alterar por ID
- [ ] UPDATE por id funcionando
- [ ] Confirmou no MySQL e no console após alterar
- [ ] Tratou caso “id não existe”

---

## 3) Conceitos que você vai ver (sem jargão, direto)
### Driver
É a “ponte” que permite o Java conversar com o MySQL.

**Exemplo do mundo real:**  
é como instalar o “aplicativo” que faz seu celular falar com um dispositivo específico.

### PreparedStatement
É uma forma segura de montar SQL com valores, evitando erros e ataques por texto malicioso.

**Exemplo do mundo real:**  
um formulário onde você preenche campos, em vez de escrever tudo no papel misturado.

---

## 4) Padrão de organização recomendado (para não virar bagunça)
Mesmo sendo console, vale separar:

- **Model**: classes de dados (`Contato` / `Pessoa`)
- **DAO/Repository**: classe que fala com o banco (`ContatoDAO`)
- **Service** (opcional): regras do negócio (validar campos, decidir o que fazer)
- **App/ConsoleView**: menu e entrada/saída do usuário

Isso facilita quando você migrar para MVC depois.

---

## 5) Roteiro de dúvidas (modelo de anotação)
Quando algo der errado, anote assim:

- **Vídeo:** (1 a 7)
- **Passo:** (ex.: “adicionar driver”, “executar SELECT”)
- **Erro exato:** (mensagem completa)
- **O que eu esperava:** (ex.: “conectar e listar”)
- **O que aconteceu:** (ex.: “não conecta / retorna vazio”)

---

## 6) Exercícios rápidos (fixação)
1) No “listar todos”, adicione ordenação por nome (ORDER BY).
2) Na “busca por nome”, permita busca parcial (ex.: “Ana” encontra “Ana Paula”).
3) No “inserir”, valide que nome não pode ser vazio.
4) No “alterar”, permita alterar apenas os campos informados (deixar em branco mantém).

---

<!-- nav_start -->
---
Anterior: [161 Contatos V2](../docs/161_Contatos_V2.md) | Proximo: [163 Videos Contatos V2](../docs/163_Videos_Contatos_V2.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
