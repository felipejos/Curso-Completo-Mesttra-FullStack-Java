# Vídeo: Gerenciamento de Contatos V1

---

## Orientações

Vídeo: Gerenciamento de Contatos V1


Assista os vídeos em sequência. Enquanto estiver assistindo faça as mesmas implementações.

Revise posteriormente o código para entender os passos envolvidos e anote suas dúvidas.

---

## Sequência de vídeos

1 - Gerenciar Contato: Ajustando aplicação para usar classes utilitárias   https://youtu.be/SZAOQKZXg04 

[![Gerenciar Contato: Ajustando aplicação para usar classes utilitárias](https://img.youtube.com/vi/SZAOQKZXg04/hqdefault.jpg)](https://youtu.be/SZAOQKZXg04)

2 - Gerenciar Contato: Gerando o pacote jar com as classes utilitárias   https://youtu.be/i9eXw5wKm-k   

[![Gerenciar Contato: Gerando o pacote jar com as classes utilitárias](https://img.youtube.com/vi/i9eXw5wKm-k/hqdefault.jpg)](https://youtu.be/i9eXw5wKm-k)

3 - Gerenciar Contato: Entendendo o conceito de classes   https://youtu.be/j1NeEvlBCv4

[![Gerenciar Contato: Entendendo o conceito de classes](https://img.youtube.com/vi/j1NeEvlBCv4/hqdefault.jpg)](https://youtu.be/j1NeEvlBCv4)

---
# Complemento da Lição

## 1) O que você deve conseguir ao final (resultado esperado)
Ao terminar a sequência e repetir as implementações, você deve ser capaz de:

- **Separar responsabilidades** no projeto (cada classe faz “uma coisa bem definida”).
- Criar e usar **classes utilitárias** (funções reutilizáveis).
- **Gerar um arquivo .jar** com código reutilizável e usar esse .jar em outro projeto.
- Explicar o que é **classe**, **objeto**, **método** e **atributo** com exemplos simples.

---

## 2) Checklist prático enquanto assiste (para não se perder)
Use esta lista como “guia de execução” enquanto copia as implementações:

- [ ] Criei/organizei pacotes (packages) para separar partes do sistema.
- [ ] Criei uma classe utilitária (ex.: validação, formatação, helpers).
- [ ] Substituí código repetido do projeto por chamadas às utilitárias.
- [ ] Rodei a aplicação e validei que o comportamento continuou correto.
- [ ] Configurei build/export e gerei o **.jar**.
- [ ] Testei o .jar sendo importado/usado em outro projeto.
- [ ] Revisei o código e escrevi dúvidas específicas (linha/arquivo/erro).

---

## 3) Conceitos (simples + exemplo do mundo real)

### Classe
**O que é:** um “molde” que descreve como algo funciona e quais dados ele tem.  
**Exemplo do mundo real:** a planta de uma casa (não é a casa, é o modelo).

### Objeto
**O que é:** uma “cópia” real daquele molde em funcionamento.  
**Exemplo:** a casa construída a partir da planta.

### Atributo
**O que é:** uma característica (dado) do objeto.  
**Exemplo:** cor da casa, número de quartos.

### Método
**O que é:** uma ação que o objeto sabe fazer.  
**Exemplo:** “abrir porta”, “acender luz”.

---

## 4) Onde “classes utilitárias” entram (na prática)
**Classe utilitária** normalmente é uma classe com funções que ajudam várias partes do sistema.

Exemplos comuns em um sistema de contatos:
- validar telefone/e-mail
- formatar nome (primeira letra maiúscula)
- remover espaços extras
- gerar mensagens padronizadas

📌 Ideia-chave: utilitárias evitam **código repetido** e deixam o projeto mais organizado.

---

## 5) Mini-roteiro de estudo (para revisar depois)
Quando você terminar os vídeos, revise assim:

1) Abra o projeto e identifique:
   - onde ficou a regra de negócio
   - onde ficaram as utilidades
2) Pegue 1 funcionalidade (ex.: “cadastrar contato”) e siga o fluxo:
   - entrada → validação → armazenamento → saída
3) Anote suas dúvidas no formato:
   - **Arquivo + linha**
   - **o que você esperava**
   - **o que aconteceu**

---

## 6) Exercícios rápidos (fixação)
1) Crie uma utilitária chamada `TextoUtils` e adicione uma função que:
   - remove espaços duplicados do texto.
2) Crie uma utilitária chamada `EmailUtils` que:
   - valida se o texto contém “@” e “.” (validação simples).
3) Explique com suas palavras:
   - diferença entre **classe** e **objeto** usando o exemplo “Contato”.

---

<!-- nav_start -->
---
Anterior: [158 ArrayList](../docs/158_ArrayList.md) | Proximo: [160 Contatos V1](../docs/160_Contatos_V1.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
