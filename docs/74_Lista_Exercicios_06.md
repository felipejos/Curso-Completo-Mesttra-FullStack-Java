# Lista de Exercícios 6 — Estruturas de Decisão

---

> Resolver os exercícios que constam nesta lista. **Não precisa ser entregue.**

---

## 📌 Material (Lista de Exercícios)

- **Autor:** PROF. JONATHAN PAULO P. PEREIRA  
- **Link da lista:** https://docentes.ifrn.edu.br/jonathanpereira/disciplinas/algoritmos/lista-de-exercicios-2/at_download/file

---

## ✅ Como estudar essa lista (recomendação rápida)

1. **Leia o enunciado com calma** e destaque:
   - Entradas (o que o usuário vai digitar)
   - Processamento (o que precisa calcular/decidir)
   - Saída (o que deve imprimir)

2. **Modele a condição do if/else**:
   - Use operadores de comparação (`>`, `<`, `>=`, `<=`, `==`, `!=`)
   - Combine com operadores lógicos (`&&`, `||`, `!`) quando necessário

3. **Teste cenários diferentes**:
   - Valores mínimos
   - Valores máximos
   - Casos que caem no `else`

4. **Organize o código com indentação** e mensagens claras no console.

---

# Complemento da Lição

---

## 🎯 Objetivo prático (o que você treina de verdade aqui)
- Transformar texto em **condições** (`if/else/else if`)
- Evitar “buracos” em faixas (ex.: `>= 10` e `< 20`)
- Praticar **validação de entrada** (não quebrar com letras)
- Criar o hábito de **testar limites** (igualdade, mínimo e máximo)

---

## 🧠 Método “E.P.S.” (Entrada → Processamento → Saída)
Para cada exercício, escreva 3 linhas antes do código:

- **Entrada:** quais variáveis vou ler?
- **Processamento:** quais contas e quais decisões vou fazer?
- **Saída:** o que imprimir e em qual formato?

Isso evita travar no meio.

---

## ✅ Checklist de condições (para não errar faixas)
Quando o enunciado falar “entre X e Y”:

- **Incluso** → use `>=` ou `<=`
- **Não incluso** → use `<` ou `>`

Exemplo: “30 (incluso) e 60 (não incluso)”
- `valor >= 30 && valor < 60`

---

## 🧯 Padrão de leitura segura (Scanner + try/catch + repetição)
Use este padrão sempre que o enunciado envolver números, para não quebrar quando digitarem letras.

### Ler inteiro com segurança
    import java.util.InputMismatchException;
    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            int numero = lerInt(teclado, "Digite um número inteiro: ");

            System.out.println("Você digitou: " + numero);

            teclado.close();
        }

        static int lerInt(Scanner teclado, String msg) {
            while (true) {
                try {
                    System.out.print(msg);
                    return teclado.nextInt();
                } catch (InputMismatchException e) {
                    System.out.println("Entrada inválida. Digite apenas números inteiros.");
                    teclado.nextLine(); // limpa o valor inválido do buffer
                }
            }
        }
    }

### Ler double com segurança
    static double lerDouble(Scanner teclado, String msg) {
        while (true) {
            try {
                System.out.print(msg);
                return teclado.nextDouble();
            } catch (InputMismatchException e) {
                System.out.println("Entrada inválida. Digite um número (ex.: 10.5).");
                teclado.nextLine(); // limpa o valor inválido do buffer
            }
        }
    }

---

## 🧪 Como testar (sempre 3 cenários)
Para cada exercício, teste pelo menos:

1) **Caso normal** (um valor “do meio”)  
2) **Caso limite** (ex.: exatamente o valor de corte: 10, 20, 60, etc.)  
3) **Caso do else / inválido** (para cair no caminho alternativo)

---

## 🧭 Decisão rápida: quando usar cada estrutura
- `if` → uma condição simples
- `if/else` → dois caminhos (verdadeiro/falso)
- `if/else if/else` → várias faixas/alternativas
- `switch` → comparar uma variável com **valores fixos** (1, 2, 3…)
- ternário `cond ? a : b` → **escolher um valor** (não para várias ações)

---

## 🧱 Modelo de arquivo (para manter padrão)
Sugestão de organização (um exercício por classe):

- `Ex01.java`
- `Ex02.java`
- `Ex03.java`
- ...

Cada arquivo:
- lê entradas
- processa
- imprime resultado

---

## ✅ Registro de progresso (marque conforme for fazendo)
- [ ] Ex 01
- [ ] Ex 02
- [ ] Ex 03
- [ ] Ex 04
- [ ] Ex 05
- [ ] Ex 06
- [ ] Ex 07
- [ ] Ex 08
- [ ] Ex 09
- [ ] Ex 10

---

## 🎯 Primeiro passo (para começar sem travar)
1) Abra o PDF da lista e escolha **o exercício 1**  
2) Escreva **Entrada / Processamento / Saída** em 3 linhas  
3) Só depois comece o código

---

Qual exercício você vai fazer primeiro (número/título)?

---

<!-- nav_start -->
---
Anterior: [73 Lista Exercicios 05](../docs/73_Lista_Exercicios_05.md) | Proximo: [75 Resposta Lista Exercicios 06](../docs/75_Resposta_Lista_Exercicios_06.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
