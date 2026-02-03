# 🧠 Operadores Lógicos

Os operadores lógicos representam o recurso que nos permite criar expressões lógicas maiores a partir da junção de duas ou mais expressões. Para isso, aplicamos as operações lógicas:

- **E** (representado por `&&`)
- **OU** (representado por `||`)
- **NÃO / Negação** (representado por `!`)

---

## ✅ Operadores

- `&&`  
  Utilizado quando desejamos que **as duas expressões sejam verdadeiras**.

- `||`  
  Utilizado quando precisamos que **pelo menos uma** das expressões seja verdadeira.

- `!`  
  Utilizado quando precisamos realizar a **negação** de uma expressão ou variável.

---

## 📋 Tabela verdade (resumo)

| A     | B     | A && B | A \|\| B | !A    | !B    |
|------:|------:|:------:|:--------:|:-----:|:-----:|
| true  | true  | true   | true     | false | false |
| true  | false | false  | true     | false | true  |
| false | true  | false  | true     | true  | false |
| false | false | false  | false    | true  | true  |

---

## 🧪 Exemplo em Java (com explicações)

    public class Main{
        public static void main(String[] args) {
            boolean resultado;
            int a;
            int b;

            a = 10;
            b = 4;

            resultado = ((a > b) && (b != 4 ));
            // (a > b) irá produzir o resultado true pois a variável a vale 10 e 10 é maior que 4 
            // (b != 4) irá produzir o resultado false pois b vale 4 e não é diferente de 4
            // (true && false) irá produzir o resultado false pois o operador && só produz true
            // quando os dois lados da expressão forem true 
            System.out.println("Resultado: " + resultado); //Resultado: false

            resultado = ((a > b) || (b != 4 ));
            // (a > b) irá produzir o resultado true pois a variável a vale 10 e 10 é maior que 4 
            // (b != 4) irá produzir o resultado false pois b vale 4 e não é diferente de 4
            // (true || false) irá produzir o resultado true pois o operador || só produz false
            // quando os dois lados da expressão forem false
            System.out.println("Resultado: " + resultado); //Resultado: true

            resultado = !((a > b) || (b != 4 ));
            // o resultado será false pois o operador ! irá inverter o resultado de (a > b) || (b != 4 )
            System.out.println("Resultado: " + resultado); //Resultado: false
        }
    }
