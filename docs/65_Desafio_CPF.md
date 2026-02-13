# Desafio: Algoritmo para Validação de CPF

---

## O que é o CPF?
O CPF (Cadastro de Pessoas Físicas) é composto por **11 dígitos**.  
Em determinados sistemas é necessário identificar se um CPF informado não foi digitado incorretamente. Para isto, o CPF possui um conjunto de **dois dígitos** conhecidos como **dígito verificador**. Esses dois dígitos podem ser calculados através de um algoritmo para identificar erros de digitação.

**Exemplo:** `123.456.789-09`  
- Os **9 primeiros dígitos** (`123456789`) são o **número base**.  
- Os **2 últimos dígitos** (`09`) são os **dígitos verificadores**. Eles servem para verificar se os 9 primeiros números foram digitados corretamente.

---

## Objetivo da validação
Verificar se os **2 últimos dígitos (verificadores)** estão corretos com base nos **9 primeiros**.

---

## Como calcular os dígitos verificadores?
Vamos dividir isso em **2 etapas**, uma para cada dígito verificador.

---

## ✅ Etapa 1: Calcular o primeiro dígito verificador

### Passo a passo:
1. Pegue os **9 primeiros dígitos** do CPF.  
   Exemplo: `123456789`

2. Multiplique cada dígito por um **peso que vai de 10 a 2**:  
   Pesos: `10, 9, 8, 7, 6, 5, 4, 3, 2`

   (1 * 10) + (2 * 9) + (3 * 8) + (4 * 7) + (5 * 6) + (6 * 5) + (7 * 4) + (8 * 3) + (9 * 2)

3. Some os resultados:  
   Soma = 210

4. Pegue o resultado e faça **módulo 11** (resto da divisão por 11):  
   210 % 11 = resto 1

5. Aplique a regra:
   - Se o resto for **menor que 2**, o dígito verificador é **0**
   - Se for **2 ou mais**, o dígito verificador é **(11 - resto)**

   Como o resto foi 1 (menor que 2):  
   ✅ Resultado: **o primeiro dígito verificador é 0**

---

## ✅ Etapa 2: Calcular o segundo dígito verificador

Agora usamos os **9 dígitos originais + o primeiro dígito verificador** (agora são 10 dígitos):  
Exemplo: `1234567890`  
(Os dígitos “verdes” seriam os do CPF e o `0` “vermelho” é o resultado do primeiro dígito verificador.)

### Passo a passo:
1. Multiplique cada dígito por um **peso que vai de 11 a 2**:  
   Pesos: `11, 10, 9, 8, 7, 6, 5, 4, 3, 2`

   (1 * 11) + (2 * 10) + (3 * 9) + (4 * 8) + (5 * 7) + (6 * 6) + (7 * 5) + (8 * 4) + (9 * 3) + (0 * 2)

2. Some os resultados:  
   Soma = 255

3. Faça **módulo 11**:  
   255 % 11 = resto 2

4. Aplique a regra:
   - Se o resto < 2 → dígito = 0
   - Se resto ≥ 2 → dígito = (11 - resto)

   Como o resto foi 2:  
   dígito = 11 - 2 = 9

✅ Resultado: **o segundo dígito verificador é 9**

---

## ✅ Resultado Final
Se o CPF for `12345678909`, acabamos de ver que os dois dígitos verificadores (**0 e 9**) batem com os calculados.

✅ Isso significa que esse CPF é **válido**.

---

## Validações extras (muito importantes)
Antes de fazer os cálculos, é importante verificar:

- Se o CPF tem **11 dígitos** (sem pontos ou traços).
- Se não é uma sequência repetida como:
  - `00000000000`, `11111111111`, `22222222222`, ... `99999999999`  
  (todas são inválidas)

---

## ✅ Resumo da lógica
- Multiplica os dígitos por pesos decrescentes.
- Soma os resultados.
- Divide por 11 e pega o resto.
- Calcula os dois dígitos verificadores.
- Compara com os dígitos informados.

---

## Trecho de código base (para obter os dígitos do CPF)
A seguir temos um trecho de código de exemplo de como obter cada um dos dígitos do CPF para a realização do cálculo.

Utilizando como exemplo o código abaixo, desenvolva o seu algoritmo completo de validação de CPF e submeta o arquivo **Main.java** compactado em zip no final desta página até o dia **23/10/2025**.

    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            String cpf;

            int d1, d2, d3, d4, d5, d6, d7, d8, d9;

            int parte1, parte2;
            int restoDivisao1, restoDivisao2;

            System.out.println("Digite o seu CPF: ");
            cpf = teclado.nextLine();

            // charAt devolve o codigo ascii (decimal) do digito conforme a tabela
            // como os digitos iniciam na posicao decimal 48 (0 = 48), (1 = 49)
            d1 = cpf.charAt(0) - 48; //primeiro digito
            d2 = cpf.charAt(1) - 48; //segundo digito
            d3 = cpf.charAt(2) - 48; //terceiro digito

            parte1 = (d1 * 10) + (d2 * 9) + (d3 * 8);

            restoDivisao1 = parte1 % 11;

            teclado.close();
        }
    }

---

## Complemento da Lição

### 🧩 Plano de implementação (bem objetivo)
1) **Ler o CPF** como `String`.
2) **Normalizar a entrada** (remover `.` e `-`, se você quiser aceitar máscara).
3) **Validações rápidas**
   - tamanho == 11
   - só dígitos
   - não ser sequência repetida (ex.: todos iguais)
4) **Calcular DV1** usando os 9 primeiros dígitos e pesos 10..2
5) **Calcular DV2** usando os 9 primeiros + DV1 e pesos 11..2
6) **Comparar** DV1 e DV2 calculados com os dois últimos do CPF informado
7) Imprimir **“CPF válido”** ou **“CPF inválido”**

---

### ✅ Dica prática para não se perder nos pesos
Você pode fazer um loop que:
- começa com `peso = 10` (ou 11)
- vai diminuindo
- soma `digito * peso`

Exemplo mental:
- 9 dígitos → pesos 10 até 2 (total 9 pesos)
- 10 dígitos → pesos 11 até 2 (total 10 pesos)

---

### 🧠 Estrutura (esqueleto) sem “entregar tudo pronto”
Use esse esqueleto e preencha os `TODO` (isso treina o raciocínio):

    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            System.out.print("Digite o seu CPF: ");
            String cpf = teclado.nextLine();

            // TODO 1) normalizar (se necessário): remover "." e "-"
            // cpf = cpf.replace(".", "").replace("-", "");

            // TODO 2) validar tamanho == 11
            // TODO 3) validar só dígitos (Character.isDigit)
            // TODO 4) validar não ser sequência repetida

            // TODO 5) separar base e dígitos informados
            // String base9 = cpf.substring(0, 9);
            // int dvInformado1 = cpf.charAt(9) - '0';
            // int dvInformado2 = cpf.charAt(10) - '0';

            // TODO 6) calcular dv1 (pesos 10..2)
            // int dv1 = ...

            // TODO 7) calcular dv2 (pesos 11..2 usando base9 + dv1)
            // int dv2 = ...

            // TODO 8) comparar dv1/dv2 com dvInformado1/dvInformado2 e imprimir resultado

            teclado.close();
        }
    }

---

### 🧪 Testes que você deve fazer (mínimo)
- Um CPF válido conhecido (ex.: o do enunciado `12345678909`)
- Um CPF com DV errado (troque o último dígito)
- Sequência repetida: `11111111111`
- Entrada com letras: `123abc78909`
- Entrada com máscara: `123.456.789-09` (se você decidir aceitar)

---

### ✅ Checkpoint (1 passo por vez)
Comece só com a parte de **normalização + validação do tamanho e dígitos**.
Depois você parte para o cálculo do DV1 e DV2.

---

**Pergunta (uma só):** no seu programa, você vai aceitar CPF com máscara (`123.456.789-09`) ou somente números (`12345678909`)?

<!-- nav_start -->
---
Anterior: [63 Video Operador Ternario](../docs/63_Video_Operador_Ternario.md) | Proximo: [69 Solucao Teste1 Q04](../docs/69_Solucao_Teste1_Q04.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
