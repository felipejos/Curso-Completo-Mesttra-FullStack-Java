# Conceito Geral: Funções e Procedimentos

---

## Funções e Procedimentos: o coração da organização na programação

Quando você começa a aprender lógica de programação, um dos conceitos mais importantes que vai encontrar são as **funções** e os **procedimentos**. Eles são fundamentais para qualquer linguagem de programação — e no **Java** não é diferente.

Entender **o que são**, **como funcionam** e **por que utilizá-los** vai ajudar você a escrever códigos mais **organizados**, **reutilizáveis** e **fáceis de entender**.

---

## O que são Funções e Procedimentos

De forma simples, tanto as **funções** quanto os **procedimentos** são **blocos de código** criados para executar uma tarefa específica dentro de um programa.

Você pode imaginar uma **função** como uma pequena “máquina” dentro do seu programa:
você dá a ela alguns dados (**entradas**), ela realiza um conjunto de instruções e, no final, pode devolver um resultado (**saída**).

Em termos gerais:

- **Procedimento (ou método `void`, no Java)**  
  É um bloco de código que executa uma tarefa, mas **não devolve um valor**.  
  Exemplo: mostrar uma mensagem na tela, gravar um dado no banco, salvar um arquivo, etc.

- **Função (ou método com retorno)**  
  É um bloco de código que realiza um processamento e **devolve um resultado**.  
  Exemplo: somar dois números e retornar o resultado, calcular a média de notas, converter uma temperatura, etc.

---

## Por que usar Funções e Procedimentos

Imagine que você está criando um programa para calcular o **salário líquido** de um funcionário. Esse cálculo envolve várias etapas:

- obter o salário bruto  
- calcular descontos  
- aplicar impostos  
- mostrar o resultado  

Agora imagine escrever tudo isso em **um único bloco de código** dentro do método `main()`.

O programa ficaria:

- longo  
- confuso  
- difícil de entender  

É aí que entram as **funções e procedimentos**.

Ao dividir o código em partes menores, cada uma responsável por uma tarefa específica, você torna o programa **modular** e **organizado**.

Por exemplo:

- Uma função para calcular o imposto  
- Outra para calcular o salário líquido  
- Um procedimento para exibir o resultado na tela  

Assim, seu código fica mais limpo e fácil de manter.

---

## Vantagens de utilizar Funções e Procedimentos

### 1) Organização e Clareza
Dividir o código em funções faz com que ele fique mais fácil de ler e entender.  
Em vez de um grande bloco confuso, você passa a ter partes com nomes claros e responsabilidades bem definidas.

### 2) Reutilização de Código
Uma vez criada, uma função pode ser usada várias vezes dentro do programa — ou até em outros projetos.

Por exemplo, se você tem uma função que converte temperaturas, pode utilizá-la em qualquer programa que precise dessa conversão, sem precisar reescrever o mesmo código.

### 3) Facilidade de Manutenção
Se algo precisar ser alterado, basta modificar o código da função.  
Todas as partes do programa que a utilizam serão automaticamente atualizadas com o novo comportamento.

### 4) Evita Repetição
Funções ajudam a evitar duplicação de código.  
Isso é importante porque, quanto mais repetido um código, maior a chance de erros e inconsistências.

### 5) Facilita Testes e Depuração
Testar pequenas partes do código separadamente (funções) é muito mais fácil do que testar um programa gigante.  
Se algo não funcionar, você pode verificar apenas a função responsável, isolando o erro.

---

# Complemento da Lição

---

## 🧠 Módulo 1 — Tradução “bem simples” dos nomes (para não confundir)

- **Função**: “faz algo e devolve um resultado”
- **Procedimento**: “faz algo e termina” (não devolve resultado)

No Java, os dois são **métodos**.
A diferença é só uma:

- método com `void` → procedimento  
- método com tipo de retorno (`int`, `double`, `String`, etc.) → função  

---

## 🧩 Módulo 2 — Entradas e Saídas (como pensar do jeito certo)

### ✅ Entrada (parâmetros)
São os dados que você entrega para o método trabalhar.

Exemplo do mundo real:
- você entrega “dois números” para uma calculadora somar.

### ✅ Saída (retorno)
É o resultado que o método devolve com `return`.

Exemplo do mundo real:
- a calculadora devolve “o resultado da soma”.

---

## 🧱 Módulo 3 — Estrutura mental para criar métodos (passo a passo)

Quando você for transformar um trecho em função/procedimento, pergunte:

1) **Qual é a tarefa?**  
   (ex.: calcular imposto)

2) **Quais dados eu preciso receber?**  
   (ex.: salário bruto)

3) **Eu preciso devolver algo?**  
   - Se sim → função (tem retorno)
   - Se não → procedimento (void)

4) **Qual nome descreve bem a tarefa?**  
   (ex.: `calcularImposto`, `mostrarResultado`)

---

## 🧪 Módulo 4 — Mini exemplo mental (sem complicar)

### Procedimento (void)
- Objetivo: “mostrar uma mensagem”

Resultado: não devolve nada, só executa.

### Função (com retorno)
- Objetivo: “somar dois números”

Resultado: devolve um número.

Trade-off (bem direto):
- funções ajudam a reutilizar cálculos
- procedimentos ajudam a organizar ações (prints, menus, logs)

---

## ⚠️ Módulo 5 — Erros comuns de iniciante

1) **Criar tudo no `main`**
- vira um bloco gigante e confuso

2) **Criar função sem retorno**
- declarar `int` mas esquecer `return`

3) **Criar procedimento e tentar usar resultado**
- `void` não devolve nada

4) **Nomes genéricos**
- `funcao1`, `teste`, `metodoX`
- melhor: nomes que dizem o que fazem

---

## ✅ Módulo 6 — Checklist rápido (para revisar seu próprio código)

- [ ] Cada método faz **uma tarefa** (uma responsabilidade)
- [ ] O nome explica a intenção (ex.: `calcularSalarioLiquido`)
- [ ] Entradas (parâmetros) são só o necessário
- [ ] Se retorna valor, existe `return` em todos os caminhos
- [ ] O `main` ficou menor e mais legível

---

## 🧪 Exercícios (para fixar a ideia)

1) Crie um procedimento `mostrarBoasVindas()` que imprime 2 linhas:
- “Bem-vindo!”
- “Escolha uma opção no menu.”

2) Crie uma função `calcularDobro(int n)` que retorna `n * 2`.

3) Crie uma função `calcularMedia(double a, double b, double c)` que retorna a média.

4) No `main`, chame esses métodos e imprima os resultados.

---


<!-- nav_start -->
---
Anterior: [83 Debug Codigo](../docs/83_Debug_Codigo.md) | Proximo: [85 Procedimentos](../docs/85_Procedimentos.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
