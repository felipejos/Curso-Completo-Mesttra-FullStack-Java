# Padrões Arquiteturais e Padrões de Projeto

---

## Visão geral

Cada desenvolvedor pode desenvolver um software utilizando uma organização do código e arquivos da forma que lhe convier.

No entanto, quando um sistema é desenvolvido sem a adoção de um padrão arquitetural ou de padrões de projeto, cada parte do código tende a refletir apenas o estilo pessoal de quem o escreveu. Isso pode parecer prático no início, principalmente em projetos pequenos ou individuais, mas rapidamente se torna um problema quando o software cresce ou quando outras pessoas passam a colaborar. A ausência de organização previsível dificulta a navegação pelo projeto, pois não há um critério claro sobre onde encontrar regras de negócio, acesso a dados ou interfaces com o usuário.

---

## Principais problemas de um sistema sem padrões

### Aumento do tempo de manutenção

Um dos primeiros impactos negativos é o aumento do tempo de manutenção. Imagine um novo desenvolvedor tentando corrigir um erro: em vez de saber que a lógica está concentrada em uma camada específica (como “services” ou “controllers”) que veremos mais adiante, ele precisa vasculhar diversos arquivos espalhados, com responsabilidades misturadas. Essa busca consome tempo e aumenta a chance de modificar o local errado, introduzindo novos defeitos.

### Alto acoplamento

Outro problema comum é o alto acoplamento entre as partes do sistema. Sem padrões de projeto, é frequente que classes dependam diretamente umas das outras, dificultando a substituição ou evolução de componentes. Uma simples mudança em um módulo pode gerar efeitos colaterais inesperados em várias outras partes do código. Isso torna o sistema frágil, onde pequenas alterações exigem grandes retrabalhos.

### Baixa reutilização de código

A falta de padronização também prejudica a reutilização de código. Soluções semelhantes acabam sendo reescritas várias vezes porque não existe uma estrutura clara ou práticas conhecidas para encapsular comportamentos. Além de aumentar o tamanho do código, isso eleva o custo de manutenção, pois bugs corrigidos em um ponto podem continuar existindo em outros trechos duplicados.

### Dificuldade para testar

Além disso, testar o software se torna mais difícil. Quando responsabilidades não estão bem separadas, criar testes unitários é complicado, pois uma classe pode depender de banco de dados, interface gráfica e regras de negócio ao mesmo tempo. Isso leva a testes mais complexos ou até à ausência deles, reduzindo a confiabilidade do sistema.

### Colaboração em equipe prejudicada

Por fim, a colaboração em equipe fica prejudicada. Sem padrões, cada desenvolvedor segue uma lógica própria de organização, gerando inconsistência no estilo do código. O projeto perde legibilidade e previsibilidade, o que dificulta revisões, onboarding de novos membros e a evolução contínua do produto. Em contraste, o uso de padrões arquiteturais e de projeto cria uma linguagem comum entre os desenvolvedores, tornando o código mais compreensível, organizado e sustentável a longo prazo.

---

## Arquitetura de software vs Padrões de projeto

Arquitetura de software e padrões de projeto são conceitos fundamentais para organizar, estruturar e manter sistemas de software de forma eficiente, escalável e sustentável ao longo do tempo. Embora estejam relacionados, eles atuam em níveis diferentes de decisão dentro de um projeto.

### Arquitetura de software

A arquitetura de software define a estrutura macro do sistema. Ela descreve como os principais componentes se organizam, como se comunicam, quais responsabilidades cada parte possui e quais tecnologias ou estilos estruturais serão adotados. Em outras palavras, a arquitetura é o “mapa” do sistema, orientando decisões de alto nível, como separação de camadas, distribuição em serviços, integração com bancos de dados e comunicação entre módulos. Uma boa arquitetura facilita manutenção, testes, evolução do sistema e trabalho em equipe.

### Padrões de projeto (Design Patterns)

Já os padrões de projeto (design patterns) atuam em um nível mais detalhado. Eles são soluções reutilizáveis para problemas recorrentes no desenvolvimento orientado a objetos e na organização de código. Enquanto a arquitetura trata da organização global do sistema, os padrões de projeto ajudam a resolver problemas locais, como criação de objetos, comunicação entre classes e extensão de comportamentos. Eles promovem código mais organizado, flexível e fácil de entender.

De forma simples, pode-se pensar assim:  a arquitetura define “como o sistema é dividido”, e os padrões de projeto definem “como as partes são implementadas internamente”.

---

## Exemplos de arquiteturas de software

- Monolítica
- Cliente-Servidor
- Em Camadas (Layered / N-Tier)
- MVC (Model-View-Controller)
- Microserviços
- SOA (Service-Oriented Architecture)
- Event-Driven (Orientada a Eventos)
- Hexagonal (Ports and Adapters)
- Clean Architecture
- Onion Architecture
- Serverless

---

## Exemplos de padrões de projeto (GoF)

O site abaixo é uma ótima referência para padrões de projeto com exemplo de códigos.

https://refactoring.guru/pt-br/design-patterns 

### Criacionais

- Singleton
- Factory Method
- Abstract Factory
- Builder
- Prototype

### Estruturais

- Adapter
- Bridge
- Composite
- Decorator
- Facade
- Flyweight
- Proxy

### Comportamentais

- Strategy
- Observer
- Command
- State
- Template Method
- Chain of Responsibility
- Mediator
- Memento
- Iterator
- Visitor
- Interpreter

---

## Fechamento

Em resumo, arquitetura e padrões de projeto se complementam: a arquitetura organiza o sistema como um todo, enquanto os padrões ajudam a implementar cada parte de forma mais elegante e reutilizável.

---

# Complemento da Lição

## 1) Mapa rápido para não confundir

- **Arquitetura**: decide “onde cada coisa mora” no sistema (camadas, módulos, fronteiras).
- **Padrões de projeto**: decide “como cada coisa se comporta” por dentro (criação, comunicação, extensão).

---

## 2) Exemplos diretos (para treinar seu olho)

- “Vou separar em Controller / Service / Repository” → Arquitetura
- “Vou criar Strategy para trocar regras de validação” → Padrão de projeto
- “Vou migrar para Clean Architecture” → Arquitetura
- “Vou usar Factory para criar implementações diferentes” → Padrão de projeto

---

## 3) Exercícios (fixação)
1) Pegue seu projeto de contatos e diga qual parte seria **Model**, qual seria **View**, e qual seria **Controller**.
2) Cite 1 problema que você já viu em projeto sem padrão (manutenção, acoplamento, testes, duplicação) e explique em 2 frases.
3) Escolha 1 padrão GoF da lista e descreva (com suas palavras) qual problema ele resolve.

---

---

<!-- nav_start -->
---
Anterior: [164 Preparacao API HTTP](../docs/164_Preparacao_API_HTTP.md) | Proximo: [166 Padrão Arquitetural MVC](../docs/166_Padrão_Arquitetural_MVC.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
