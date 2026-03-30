# Exemplos de Uso de Códigos de Erro HTTP

Uma visão organizada dos códigos de status mais usados ao construir APIs REST e lidar com operações em banco de dados.

## 📚 Conteúdo Original (Mantido na Íntegra)

### ✅ Respostas 2xx — Operações bem-sucedidas

> 200 — OK
> Usado quando a operação foi executada com sucesso.
>
> Exemplo: GET /usuarios
>
> Resposta: 200 OK

> 201 — Created
> Usado quando um recurso foi criado no banco.
>
> Exemplo: POST /usuarios
>
> Resposta: 201 Created

> 204 — No Content
> Usado quando a operação foi executada com sucesso, mas não há conteúdo para retornar.
>
> Exemplo: DELETE /usuarios/10
>
> Resposta: 204 No Content

### ⚠️ Respostas 4xx — Problemas do lado do cliente

> 400 — Bad Request
> Usado quando os dados enviados são inválidos.
>
> Exemplo:
>
> CPF inválido
>
> campo obrigatório ausente
>
> formato de data inválido
>
> Resposta: 400 Bad Request

> 401 — Unauthorized
> Usado quando o usuário não está autenticado.
>
> Exemplo:
>
> token ausente
>
> token inválido
>
> Resposta: 401 Unauthorized

> 403 — Forbidden
> Usado quando o usuário está autenticado, mas não tem permissão.
>
> Exemplo:
>
> usuário comum tentando excluir administrador
>
> Resposta: 403 Forbidden

> 404 — Not Found
> Usado quando o recurso solicitado não existe no banco.
>
> Exemplo:  GET /usuarios/999
>
> Resposta: 404 Not Found

> 409 — Conflict
> Usado quando há conflito de dados no banco.
>
> Exemplos: violação de chave única
>
> tentativa de inserir registro duplicado
>
> conflito de estado
>
> Tentando inserir um usuário com login já existente.
>
> Exemplo: POST /usuarios
>
> Resposta: 409 Conflict

> 422 — Unprocessable Entity
> Usado quando os dados são válidos sintaticamente, mas violam regra de negócio.
>
> Exemplo:
>
> CPF inválido
>
> idade menor que o permitido
>
> saldo insuficiente
>
> Resposta: 422 Unprocessable Entity

### 🚨 Respostas 5xx — Erros do lado do servidor

> 500 — Internal Server Error
> Usado para erros inesperados do servidor.
>
> Exemplos:
>
> erro de conexão com banco
>
> bug no código
>
> erro inesperado
>
> Resposta: 500 Internal Server Error

> 503 — Service Unavailable
> Usado quando um serviço externo está indisponível.
>
> Exemplo:
>
> banco fora do ar
>
> sistema externo indisponível
>
> Resposta: 503 Service Unavailable

### 🗂️ Mapeamento típico em APIs com banco

| Situação                   | Código HTTP |
|----------------------------|-------------|
| Consulta realizada         | 200         |
| Registro criado            | 201         |
| Registro removido          | 204         |
| Dados inválidos            | 400         |
| Não autenticado            | 401         |
| Sem permissão              | 403         |
| Registro não encontrado    | 404         |
| Conflito de dados          | 409         |
| Regra de negócio violada   | 422         |
| Erro interno               | 500         |
| Banco indisponível         | 503         |

## 🔍 Complemento Explicativo

Cada status HTTP acima deve ser associado a regras claras na camada de serviço para evitar respostas inconsistentes. Uma abordagem eficaz é centralizar a tradução de exceções para status dentro de um handler global, garantindo que erros de validação (400), autenticação (401), autorização (403) e domínio (409/422) sejam tratados de maneira previsível. Além disso, monitore a frequência de respostas 5xx: picos indicam problemas estruturais como timeouts ou indisponibilidade de dependências externas que podem ser mitigados com circuit breakers, retries exponenciais e métricas específicas por endpoint.

Outra boa prática é padronizar o corpo das respostas de erro (por exemplo, `{ "codigo": 422, "mensagem": "Regra de negócio violada" }`). Isso facilita o consumo por frontends e integrações, amplia a rastreabilidade e reduz ambiguidades na experiência do consumidor da API.

## 💻 Desafios de Código

1. **Handler Centralizado:** Implemente um `@ControllerAdvice` (ou equivalente) que capture exceções específicas de validação, autenticação, autorização, regras de negócio e falhas inesperadas, retornando exatamente os status descritos no catálogo acima com payload JSON padronizado.
2. **Teste de Contrato:** Crie testes de integração (Spring MockMvc, RestAssured ou equivalente) para garantir que cada rota crítica do seu projeto devolva o status correto em cenários de sucesso e erro (200/201/204, 400/401/403/404/409/422, 500/503).
3. **Simulador de Falhas:** Adicione um endpoint de diagnóstico que force condições como indisponibilidade de banco ou erro interno controlado. Use-o para validar observabilidade (logs, métricas e alertas) e confirmar que o sistema responde com 500 ou 503 de acordo com a falha induzida.

