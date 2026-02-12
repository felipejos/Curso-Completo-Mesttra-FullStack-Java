# Tipos de Variáveis no Java

---

## Conteúdo

## Tipos de Variáveis no JAVA
https://www.youtube.com/watch?v=ZQxKhfPLiAk

[![Assistir no YouTube](https://img.youtube.com/vi/ZQxKhfPLiAk/hqdefault.jpg)](https://www.youtube.com/watch?v=ZQxKhfPLiAk)

---

# Complemento da Lição

## 1) O que é “tipo” de variável (bem simples)
O **tipo** diz **que tipo de valor** a variável pode guardar.

### Exemplo do mundo real
É como escolher o tipo de recipiente:
- garrafa (líquido)
- caixa (objetos)
- envelope (papel)

Cada um serve melhor para um tipo de coisa.

---

## 2) Tipos mais comuns no Java (iniciante)

### 2.1 Texto
- `String` → guarda textos (nome, email, endereço)

### 2.2 Números inteiros (sem vírgula)
- `int` → idade, quantidade, opções de menu

### 2.3 Números decimais (com vírgula)
- `double` → valores com casas decimais (preço, peso)
- `float` → semelhante ao double (menos comum no dia a dia)

### 2.4 Verdadeiro/Falso
- `boolean` → validações, condições (`true` / `false`)

---

## 3) Onde isso aparece no seu projeto (contatos)
- `String nome`
- `String email`
- `int id`
- `String ddd`
- `String numero`
- `boolean continuar` (ex.: continuar adicionando telefone)

---

## 4) Exemplo prático (de propósito bem direto)
    public class Main {
        public static void main(String[] args) {
            String nome = "Felipe";
            int idade = 34;
            double peso = 64.5;
            boolean ativo = true;

            System.out.println(nome);
            System.out.println(idade);
            System.out.println(peso);
            System.out.println(ativo);
        }
    }

---

## 5) Erro comum que trava iniciante
Tentar colocar um valor do tipo errado:

- `int idade = "34";`  (errado: texto em número)
- `String nome = 10;`  (errado: número em texto)

📌 Regra prática:
- **texto** → `String`
- **número inteiro** → `int`
- **número com decimal** → `double`
- **sim/não** → `boolean`

---

## 6) Exercícios rápidos (fixação)
1) Escolha o tipo certo para cada dado:
   - nome
   - idade
   - preço
   - aprovado (sim/não)
2) Crie variáveis com esses tipos e imprima no console.
3) Faça uma condição simples:
   - se `idade >= 18`, imprimir “Maior de idade”
   - senão, imprimir “Menor de idade”

---

## 7) Pergunta única (para checar que fixou)
Qual tipo você usaria para guardar **um email** e por quê?

---

<!-- nav_start -->
---
Anterior: [VariÃ¡veis](../docs/14_Variaveis.md) | Próximo: [Tipos de Dados e Intervalos de Valores](../docs/16_Tipos_Dados_Intervalos.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

