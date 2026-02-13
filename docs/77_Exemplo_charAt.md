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

<!-- nav_start -->
---
Anterior: [76 charAt](../docs/76_charAt.md) | Proximo: [78 Calculadora Area](../docs/78_Calculadora_Area.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
