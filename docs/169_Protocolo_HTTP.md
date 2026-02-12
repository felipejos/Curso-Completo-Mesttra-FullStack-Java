# Protocolo HTTP

---

## Fundamentos

Uma API HTTP RESTful é uma interface de comunicação entre sistemas que utiliza o protocolo HTTP seguindo os princípios da arquitetura REST (Representational State Transfer). Nesse modelo, os recursos da aplicação são identificados por URIs e manipulados por meio dos métodos HTTP, como GET, POST, PUT/PATCH e DELETE.

---

## Protocolo HTTP

O protocolo HTTP (Hypertext Transfer Protocol) é o principal padrão de comunicação utilizado na Web para permitir a troca de informações entre clientes (ex: browser) e servidores (servidor web). Ele pertence à camada de aplicação do modelo OSI e define um conjunto de regras que possibilita que diferentes dispositivos e sistemas se comuniquem por meio de requisições e respostas. Nesse modelo, o cliente envia uma solicitação a um endereço identificado por uma URI/URL, acompanhada de cabeçalhos e dados, e o servidor retorna uma resposta contendo o recurso solicitado ou informações adicionais. Dessa forma, o HTTP viabiliza o acesso a páginas, imagens, vídeos e outros conteúdos disponíveis na Internet ou em redes corporativas, garantindo uma comunicação padronizada e eficiente entre as máquinas.

---

## Comunicação Cliente-Servidor (pacotes HTTP)

Em comunicações web, o cliente se comunica com o servidor através da troca de pacotes de dados. As informações inseridas pelo cliente (normalmente o browser) nestes pacotes são compostas de uma linha de requisição (request line), cabeçalho (header) e um corpo (body message). Estes itens serão explicados no decorrer deste texto.

### Comunicação entre Cliente Servidor

Comunicação entre Cliente Servidor

### Requisição com o verbo POST

Requisição com o verbo POST

### Requisição com o verbo GET

Requisição com o verbo GET

### Resposta HTTP

Resposta HTTP

---

## Origem dos dados enviados na requisição

As informações inseridas neste pacote de dados são baseadas no que é digitado na barra de endereços do browser (navegador de Internet por exemplo) + conteúdo presente no formulário html. Parte do conteúdo presente no request line e header, são ouriundos do que é digitado na barra de endereços do browser.

O conteúdo digitado na barra de endereços pode ser composto por algumas estruturas. A imagem a seguir, apresenta um exemplo mais completo possível de informações digitadas em um endereço no browser.

---

## URI, URL e URN

### URI

É o acrônimo de Uniform Resource Identifier (Identificador de Recursos Universal). É um mecanismo de identificação que pode ser uma página, uma imagem, um email, um vídeo, um livro etc., Uma URI é qualquer identificador de recurso. Ela não precisa dizer onde está, apenas como identificar o recurso.

Exemplos:

- https://meusite.com/foto.jpg
- mailto:rogerio@email.com
- urn:isbn:9788575225633

### URL

É um tipo de URI que, identifica E diz onde encontrar o recurso E como acessar que é o (protocolo). Ou seja, fornece localização + meio de acesso. URL é uma sigla para Uniform Resource Locator (Localizador de Recursos Universal), como o próprio nome diz, é um endereço, que identifica unicamente um recurso na rede de computadores. A URL é composta do protcolo [protocol], um conjunto opcional de dados [user info] como um nome de usuário [username] e uma senha [pass], um endereço de destino [host] mais um caminho de recurso [pathname].

Este conjunto de informações identifica basicamente como acessar um servidor, em qual endereço e qual o recurso solicitado. Este servidor pode estar na Internet ou até mesmo uma rede local, como uma rede corporativa de uma empresa, ou de uma residencia.

Exemplos:

- http://google.com.br/                                                          ==> aqui temos presente apenas o protocolo + hostname
- https://www.lojavirtual.com.br/produtos                        ==> aui temos presente o protocolo + hostname + pathname
- https://minhaapp:8080/produtos?id=9&status=ativo   ==> aqui temos presente o protocolo + hostname + porta + pathname + search

### URN

Também é um tipo de URI, mas identifica somente o recurso, não informa onde ele está. URN é sigla para Uniform Resource Name (Nome de Recursos Universal), é o nome do recurso que será acessado. Desta forma é menos comum no dia a dia da web do que URL, então vale começar com uma verdade direta: você quase nunca “acessa” uma URN no navegador. Na prática, URNs aparecem mais em padrões, metadados, XML, bibliotecas digitais, sistemas distribuídos e identificadores globais, não como links clicáveis.

Exemplo de URN:

- urn:isbn:9788575225633

---

## Verbos HTTP

Os verbos HTTP são os métodos de requisição usados para indicar a ação que será executada quando chamamos um recurso de uma API Rest. Segue a lista dos mais conhecidos e utilizados:

- GET: Responsável por buscar/consultar informações por meio de uma URI. É um método idempotente, isto é, não altera nada, não importa quantas vezes a requisitamos, será o mesmo resultado.
- POST: Responsável por enviar informações com conteúdo embutido no corpo, podendo ser JSON, XML ou texto por meio de uma URI. É utilizado muitas vezes para gravar uma nova informação no sistema.
- DELETE: Responsável por remover informações por uma URI.
- PUT: Responsável por atualizar informações, com conteúdo embutido no corpo, podendo ser XML ou JSON.

---

## HTTP Status Code

O Status Code de uma requisição é parte importante de uma Web API, pois com ele é possível reconhecer facilmente o que aconteceu com a requisição. O código é um padrão numérico que apresenta o resultado da ação. Seguem alguns exemplos:

- 200 - OK: A requisição foi bem-sucedida.
- 201 - Created: O pedido foi cumprido e resultou em um novo recurso que está sendo criado.
- 401 - Unauthorized: A URI especificada precisa de autenticação.
- 403 - Forbidden: Indica que o servidor se recusa a atender à solicitação.
- 404 - Not Found: O recurso requisitado não foi encontrado.
- 500 - Internal Server Error: Indica um erro do servidor ao processar a solicitação.

---

# Complemento da Lição

## 1) Estrutura mental do HTTP (para memorizar rápido)

- Request:
  - Request Line (método + caminho + versão)
  - Headers (metadados)
  - Body (dados, quando necessário)

- Response:
  - Status Line (versão + status code)
  - Headers
  - Body (conteúdo/resultado)

---

## 2) Mapa “CRUD ↔ Verbos HTTP” (associação prática)

- Create (criar) → POST
- Read (ler) → GET
- Update (atualizar) → PUT / PATCH
- Delete (remover) → DELETE

---

## 3) Exercícios de fixação (prática rápida)

1) Pegue a URL abaixo e identifique: protocolo, host, porta, pathname e search:  
   - https://minhaapp:8080/produtos?id=9&status=ativo

2) Escreva 4 endpoints (somente método + caminho) para um CRUD de contatos:
   - ex.: GET /contatos, POST /contatos, GET /contatos/{id}, ...

3) Para cada status code, escreva um cenário real do seu sistema:
   - 200, 201, 401, 403, 404, 500

4) Simule uma requisição “na cabeça” (sem ferramenta):
   - Qual método você usaria para “listar todos os contatos”?
   - Qual status code você espera quando um contato novo é criado com sucesso?

---

<!-- nav_start -->
---
Anterior: [VÃ­deos: Gerenciando Contatos V2](../docs/163_Videos_Contatos_V2.md) | Próximo: [Roteiros de Estudo](../docs/165_Roteiros_Estudo.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->