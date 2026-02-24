## 🧩 Exemplo de uso do `charAt()`

### 🎯 Objetivo
Escreva um algoritmo que receba uma data no formato **dd/mm/yyyy** e retorne **por extenso** a palavra que representa o mês.

---

### ✅ Código (Java)

    // Escreva um algoritmo que receba uma data informada pelo usuário no formato dd/mm/yyyy
    // e retorne por extenso a palavra que representa o mês.

    import java.util.Scanner;

    public class Main {
        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            String data;
            String mesExtenso = "";

            System.out.print("Digite uma data no formato dd/mm/aaaa: ");
            data = teclado.nextLine();

            // Extrai o mês obtendo o caractere na posicao 3 e 4 da string informada pelo usuário.
            // Exemplo 01/04/2002 --> 04
            //         05/09/2025 --> 09
            String mes = "" + data.charAt(3) + data.charAt(4);

            // Concatenar o caractere "" (vazio) com o resultado retornado pelo charAt() é um
            // macete para forçar a conversão do resultado para String.

            // Existe uma forma mais eficiente de fazer este bloco abaixo, através de vetores.
            // Assim que aprendermos vetores realizaremos o refatoramento deste código.
            switch (mes) {
                // Exemplo de cases com estrutura mais compacta
                case "01": mesExtenso = "janeiro"; break;
                case "02": mesExtenso = "fevereiro"; break;
                case "03": mesExtenso = "março"; break;
                case "04": mesExtenso = "abril"; break;
                case "05": mesExtenso = "maio"; break;
                case "06": mesExtenso = "junho"; break;
                case "07": mesExtenso = "julho"; break;
                case "08": mesExtenso = "agosto"; break;

                // Outra forma de escrever o case usando uma estrutura mais extensa
                case "09":
                    mesExtenso = "setembro";
                    break;
                case "10":
                    mesExtenso = "outubro";
                    break;
                case "11":
                    mesExtenso = "novembro";
                    break;
                case "12":
                    mesExtenso = "dezembro";
                    break;
                default:
                    mesExtenso = "mês inválido";
                    break;
            }

            // Exibe o mês por extenso
            System.out.println("Mês: " + mesExtenso);

            teclado.close();
        }
    }

---

### 📝 Observações importantes

- Em Strings, o índice começa em **0**:
  - `data.charAt(3)` pega o **4º caractere** da String.
  - `data.charAt(4)` pega o **5º caractere** da String.
- No formato `dd/mm/aaaa`:
  - posições `3` e `4` sempre correspondem ao mês.

Exemplo:
- `01/04/2002` → `mes = "04"`
- `05/09/2025` → `mes = "09"`

---

# Complemento da Lição

---

## 📚 Módulo 1 — Entendendo a “posição” na String (passo a passo)

Imagine a data como uma sequência de caracteres:

Data: `01/04/2002`

Posições (índices):

- `0` → `0`
- `1` → `1`
- `2` → `/`
- `3` → `0`  ✅ (primeiro dígito do mês)
- `4` → `4`  ✅ (segundo dígito do mês)
- `5` → `/`
- `6` → `2`
- `7` → `0`
- `8` → `0`
- `9` → `2`

Então:
- `data.charAt(3)` → `'0'`
- `data.charAt(4)` → `'4'`
- juntando os dois → `"04"`

---

## 🧠 Módulo 2 — Por que existe `"" + data.charAt(...)`?

O `charAt()` devolve **char** (um caractere só), não uma String.

- `data.charAt(3)` é `char`
- `data.charAt(4)` é `char`

Quando você faz:

    String mes = "" + data.charAt(3) + data.charAt(4);

O `""` (String vazia) força o Java a **transformar tudo em String**, assim:
- `"" + '0'` vira `"0"`
- `"0" + '4'` vira `"04"`

Exemplo do mundo real:
- `char` é **uma letra solta**.
- `String` é **uma palavra**.
- O `""` é como “colar” as letras para virar uma palavra.

---

## 🛡️ Módulo 3 — Erros comuns e como blindar o código

### ✅ 1) Usuário digitar fora do padrão
Exemplos ruins:
- `1/4/2002` (faltou zero)
- `01-04-2002` (separador diferente)
- `abcd` (texto aleatório)

Problema:
- Se a String for curta, `charAt(3)` e `charAt(4)` podem estourar erro.

### ✅ 2) Validação mínima (sem complicar)

Uma validação simples antes de usar `charAt()`:

- precisa ter **10 caracteres** em `dd/mm/aaaa`
- precisa ter `/` nas posições `2` e `5`

Exemplo (mantendo a ideia do seu algoritmo):

    if (data.length() == 10 && data.charAt(2) == '/' && data.charAt(5) == '/') {
        String mes = "" + data.charAt(3) + data.charAt(4);
        // segue o switch...
    } else {
        System.out.println("Data inválida! Use o formato dd/mm/aaaa.");
    }

---

## ⚙️ Módulo 4 — Uma alternativa mais direta (mesma lógica, sem `charAt`)

Só para entender a diferença de abordagem:

- `charAt()` pega **1 caractere**
- `substring()` pega **um pedaço** (intervalo) da String

No formato `dd/mm/aaaa`, o mês está do índice `3` até `5` (5 não entra):

    String mes = data.substring(3, 5);

Isso também vira `"04"`.

Trade-off (bem direto):
- `charAt()` = bom para aprender **índices e caracteres**
- `substring()` = mais simples quando você quer **pedaços**

---

## 🧪 Exercícios

1) Para a data `31/12/2024`, mostre:
- `data.charAt(0)`
- `data.charAt(1)`
- `data.charAt(3)`
- `data.charAt(4)`

2) Faça o programa imprimir também o **dia** (dd), usando `charAt()`:
- pegue índices `0` e `1`
- junte em uma String `"dd"`

3) Coloque uma validação mínima:
- se não tiver 10 caracteres, imprimir `"Data inválida"`
- se não tiver `/` nas posições `2` e `5`, imprimir `"Data inválida"`

---


<!-- nav_start -->
---
Anterior: [76 charAt](../docs/76_charAt.md) | Proximo: [78 Calculadora Area](../docs/78_Calculadora_Area.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
