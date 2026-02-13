# 📝 Sugestão de Exercício: Média de Duas Notas (Java + Try/Catch)

---

## 📌 Enunciado

Você deve desenvolver um pequeno programa em Java que ajude estudantes a calcular a **média de duas notas** de uma disciplina.

---

## ✅ O programa deve

- Solicitar ao usuário que digite **duas notas** (valores decimais) de **0 a 10**.
- Realizar o cálculo da **média aritmética** dessas notas.
- Exibir a média calculada com **duas casas decimais**.
- Utilizar **try-catch** para garantir que:
  - O usuário digitou valores numéricos válidos.
  - Não ocorrerão erros de execução caso ele digite algo inválido (por exemplo, letras em vez de números).

---

## 📌 Regras adicionais

- Caso o usuário insira um valor inválido (como texto não numérico), exiba uma mensagem amigável informando o erro e peça que ele execute o programa novamente.
- Não é necessário validar se a nota está entre **0 e 10** neste exercício (apenas o **tipo do dado**).

---

## ✅ Exemplo do resultado (execução correta)

    Digite a primeira nota: 8.5
    Digite a segunda nota: 7.0
    A média das notas é: 7.75

---

## ❌ Exemplo do resultado (execução incorreta)

    Digite a primeira nota: oito
    Erro: Valor inválido. Por favor, insira um número válido.

---

# Complemento da Lição

## 1) O que você precisa “montar” no programa (em partes)
Pense no programa como 4 bloquinhos:

1. **Entrada**: ler duas notas decimais do teclado  
2. **Processamento**: calcular a média aritmética  
3. **Saída**: imprimir a média com 2 casas decimais  
4. **Segurança**: se o usuário digitar texto, cair no `catch` e mostrar mensagem amigável  

---

## 2) O Try/Catch aqui serve para qual erro, exatamente?
O erro típico é: o usuário digita **texto** quando o programa espera **número**.

Na prática, isso costuma virar uma exceção de “tipo errado na entrada” (entrada incompatível).

---

## 3) Roteiro de implementação (passo a passo)
Siga esta ordem ao codar:

1) Crie o `Scanner`  
2) Mostre a mensagem: “Digite a primeira nota:”  
3) Leia a nota (decimal)  
4) Mostre a mensagem: “Digite a segunda nota:”  
5) Leia a nota (decimal)  
6) Calcule: **média = (nota1 + nota2) / 2**  
7) Imprima com 2 casas decimais  

Depois disso, envolva a parte de leitura/cálculo dentro de `try { ... }` e trate o erro no `catch`.

---

## 4) Modelo mental do código (com lacunas para você preencher)
Use como “mapa”, sem entregar tudo pronto:

    import java.util.Scanner;
    import java.util.InputMismatchException;

    public class App {
        public static void main(String[] args) {

            Scanner teclado = new Scanner(System.in);

            try {
                System.out.print("Digite a primeira nota: ");
                // TODO: ler nota1 como decimal

                System.out.print("Digite a segunda nota: ");
                // TODO: ler nota2 como decimal

                // TODO: calcular media = (nota1 + nota2) / 2

                // TODO: imprimir media com 2 casas decimais
            } catch (InputMismatchException e) {
                System.out.println("Erro: Valor inválido. Por favor, insira um número válido.");
            }
        }
    }

---

## 5) Testes obrigatórios (para você mesmo validar)
- [ ] Digitar: `8.5` e `7.0` → imprime média correta com 2 casas
- [ ] Digitar: `oito` na primeira nota → cai no `catch` com mensagem amigável
- [ ] Digitar: `9` e `3.5` → funciona com mistura de inteiro e decimal

---

## 6) Pergunta única (pra você destravar a implementação)
Qual método do `Scanner` você vai usar para ler **nota decimal**: `nextInt()` ou `nextDouble()`?

<!-- nav_start -->
---
Anterior: [Código de Exemplo para o Try Catch](../docs/37_Codigo_Exemplo_Try_Catch.md) | Próximo: [Solução lista Exercí­cios 1](../docs/39_Solucao_Lista_Exercicios_1.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

