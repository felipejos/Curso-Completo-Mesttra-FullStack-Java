# Vídeos: Gerenciando Contatos V2

---

## Orientações (conteúdo fornecido)

Vídeos: Gerenciando Contatos V2
Gerenciando contatos com o banco de dados v2. Assista os vídeos na sequência, nesta versão criamos uma classe telefone para representar a possibilidade do usuário possui vários telefones. Em todos os vídeos,implemente o seu código junto com o vídeo. Não vá  para o próximo vídeo sem fazer a sua própria implementação. Faça as anotações dos pontos de dúvidas para discutirmosposteriormente.

---

## Sequência de vídeos (conteúdo fornecido)

Gerenciador Contatos V2: 1 - Criando a classe Telefone

https://youtu.be/uOY6FzDe3ik

[![Gerenciador Contatos V2: 1 - Criando a classe Telefone](https://img.youtube.com/vi/uOY6FzDe3ik/hqdefault.jpg)](https://youtu.be/uOY6FzDe3ik)

---

Gerenciador Contatos V2: 1 - Criando a classe TelefoneDAO e método de consulta

https://youtu.be/JT7KTnAYQLw

[![Gerenciador Contatos V2: 1 - Criando a classe TelefoneDAO e método de consulta](https://img.youtube.com/vi/JT7KTnAYQLw/hqdefault.jpg)](https://youtu.be/JT7KTnAYQLw)

---

Gerenciador Contatos V2: 3 - TelefoneDAO, método de inserção

https://youtu.be/xwj-Z3ANNK4

[![Gerenciador Contatos V2: 3 - TelefoneDAO, método de inserção](https://img.youtube.com/vi/xwj-Z3ANNK4/hqdefault.jpg)](https://youtu.be/xwj-Z3ANNK4)

---

Gerenciador Contatos V2: 4 - Trabalhando com Transações

https://youtu.be/w6cyvdyy4Wk

[![Gerenciador Contatos V2: 4 - Trabalhando com Transações](https://img.youtube.com/vi/w6cyvdyy4Wk/hqdefault.jpg)](https://youtu.be/w6cyvdyy4Wk)

---

Gerenciador Contatos V2: 5 - TelefoneDAO, método de exclusão

https://youtu.be/Ce11ev62nxA

[![Gerenciador Contatos V2: 5 - TelefoneDAO, método de exclusão](https://img.youtube.com/vi/Ce11ev62nxA/hqdefault.jpg)](https://youtu.be/Ce11ev62nxA)

---
# Complemento da Lição

## 1) O que muda do V1 para o V2 (no banco)
Nesta versão, o sistema evolui de “um contato com um telefone” para:

- **Contato** (ou Pessoa) continua sendo a entidade principal
- **Telefone** vira uma entidade separada (uma tabela separada no banco)
- Um contato pode ter **vários telefones** (relação 1 para N)

📌 Exemplo simples:
- Pessoa ID 10
  - Telefone ID 1: (11) 99999-9999
  - Telefone ID 2: (11) 98888-8888

---

## 2) O que você deve ter ao final (resultado esperado)
Depois desses vídeos, você deve conseguir:

- Criar a classe `Telefone` (Model)
- Criar um `TelefoneDAO` para:
  - consultar telefones
  - inserir telefones
  - excluir telefones
- Entender e aplicar **transações** quando precisa salvar/remover coisas relacionadas sem “quebrar” o banco

---

## 3) Checklist por vídeo (para não avançar sem finalizar)

### Vídeo 1 — Criando a classe Telefone
- [ ] Classe `Telefone` criada com atributos (ex.: id, ddd, numero, idContato)
- [ ] `toString()` pronto para imprimir no console
- [ ] Rodou e imprimiu um objeto exemplo sem erro

### Vídeo 2 — TelefoneDAO e método de consulta
- [ ] `TelefoneDAO` criado
- [ ] SELECT por contato (ou por id) funcionando
- [ ] ResultSet convertido para objetos `Telefone`
- [ ] Testou com 2+ telefones no banco

### Vídeo 3 — TelefoneDAO, método de inserção
- [ ] INSERT com PreparedStatement
- [ ] Inseriu telefone e confirmou no MySQL
- [ ] Validou retorno (ex.: linhas afetadas)

### Vídeo 4 — Trabalhando com Transações
- [ ] Entendeu quando usar transação (operações “dependentes”)
- [ ] Usou commit/rollback
- [ ] Simulou erro e viu rollback funcionando

### Vídeo 5 — TelefoneDAO, método de exclusão
- [ ] DELETE por id funcionando
- [ ] Tentou excluir id inexistente e tratou mensagem
- [ ] Confirmou no banco que o registro sumiu

---

## 4) Conceitos (simples + exemplo do mundo real)

### DAO
**O que é:** classe que “fala com o banco” (faz SELECT/INSERT/UPDATE/DELETE).  
**Exemplo do mundo real:** atendente que pega/põe informações no arquivo físico (banco).

### Transação
**O que é:** um “pacote” de operações que deve dar certo por completo ou desfazer tudo.  
**Exemplo do mundo real:** compra no cartão: ou aprova tudo e conclui, ou cancela e não cobra nada.

---

## 5) Onde transações costumam entrar nesse projeto
Transações são úteis quando:
- você salva **Pessoa + Telefones** juntos
- ou remove uma pessoa e precisa remover os telefones dela (dependendo do desenho do banco)

A ideia é evitar estado “quebrado”, tipo:
- pessoa salva, mas telefones não
- telefones inseridos, mas pessoa não

---

## 6) Exercícios rápidos (fixação)
1) Liste todos os telefones de um contato por ID.
2) Impeça inserir telefone com DDD vazio.
3) Faça exclusão de telefone por ID e depois liste para confirmar.
4) Simule uma falha no meio de uma transação e confirme que nada foi salvo.

---
<!-- nav_start -->
---
Anterior: [VÃ­deo: Primeira AplicaÃ§Ã£o de Console com o Banco de Dados](../docs/162_Video_Primeira_App_BD.md) | Próximo: [VÃ­deos: PreparaÃ§Ã£o para aplicaÃ§Ã£o backend no formato de API HTTP](../docs/164_Preparacao_API_HTTP.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

