# Padrão Arquitetural - MVC

---

## O que é MVC

O padrão MVC (Model–View–Controller) é um padrão arquitetural usado para separar responsabilidades dentro de uma aplicação, organizando o código em três partes independentes:

- **Model (Modelo)** → dados e regras de negócio  
- **View (Visão)** → interface com o usuário  
- **Controller (Controlador)** → coordena as ações entre Model e View  

A ideia central é simples: cada parte cuida de um único tipo de responsabilidade, evitando que a lógica fique toda misturada no mesmo lugar.

---

## Model (Modelo)

É o coração da aplicação.

Responsável por:

- armazenar dados  
- regras de negócio  
- validações  
- acesso ao banco  
- cálculos  
- estados do sistema  

Não deve saber nada sobre interface gráfica ou HTML.

Exemplo:
Em um sistema bancário:

- Conta  
- Cliente  
- Transferência  
- Regra de saldo mínimo  

---

## View (Visão)

É a camada de apresentação.

Responsável por:

- mostrar informações  
- coletar dados do usuário  
- renderizar telas, HTML, relatórios  

Não deve conter regra de negócio.

Exemplos:

- HTML  
- JSP  
- React  
- JavaFX  
- Console (println)  

---

## Controller (Controlador)

É o intermediário entre usuário e sistema.

Responsável por:

- receber ações do usuário  
- chamar o Model  
- escolher qual View será exibida  

---

## Fluxo Típico

1 - Usuário clica botão (View)  
2 - Controller recebe a ação  
3 - Controller chama o Model  
4 - Model executa regra de negócio  
5 - Controller atualiza a View  

---

## Benefícios obtidos com o MVC

- separação de responsabilidades  
- código mais organizado  
- manutenção mais simples  
- testes unitários mais fáceis  
- permite trocar interface sem mexer na lógica  
- facilita trabalho em equipe  

---
# Complemento da Lição

## 1) Como saber “onde colocar” uma coisa (regra prática)
Use estas perguntas rápidas:

- **Isso é dado ou regra?** → vai no **Model**
- **Isso é entrada/saída do usuário?** → vai na **View**
- **Isso é decisão de fluxo (o que chama o quê)?** → vai no **Controller**

---

## 2) Exemplo aplicado ao seu projeto de Contatos (console)
Para um “Gerenciador de Contatos” no console:

- **Model**
  - `Pessoa`, `Telefone`
  - regras: validar nome, impedir telefone vazio, etc.
  - acesso a dados: lista em memória ou DAO (MySQL)

- **View**
  - imprimir menus
  - ler teclado (Scanner)
  - mostrar mensagens (“Contato incluído…”)

- **Controller**
  - interpretar opção do menu
  - chamar o Model/DAO para incluir/alterar/excluir/listar
  - decidir o que mostrar depois (voltar menu, pausar, etc.)

---

## 3) Erro comum (para evitar)
Misturar tudo no `main`:
- menu + regra + banco + validação no mesmo método  
Isso funciona no começo, mas cresce rápido e vira difícil de manter e testar.

---

## 4) Exercícios (fixação rápida)
1) No seu projeto de contatos, escolha 1 funcionalidade (ex.: “incluir contato”) e escreva:
   - o que é View, o que é Controller e o que é Model nesse fluxo.
2) Dê 2 exemplos de “regra de negócio” do seu sistema de contatos.
3) Se você trocar o console por JavaFX, o que deve mudar e o que deve ficar igual no MVC?

---

<!-- nav_start -->
---
Anterior: [165 Padrões Arquiteturais e Padrões de Projeto](../docs/165_Padrões_Arquiteturais_e_Padrões_de_Projeto.md) | Proximo: [167 Desafio](../docs/167_Desafio.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
