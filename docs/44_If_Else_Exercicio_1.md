# 🧩 If/Else — Exercício 1 (Terreno com regra de valorização)

Exemplo de um exercício que envolve o uso de uma estrutura de decisão **if/else**.

---

## 📌 Enunciado do exercício

    //Escreva um algoritmo que leia as dimensões de um terreno (frente e lateral). 
    //Leia também o valor do metro quadrado.
    //Após as leituras, calcule a area total do terreno e o valor do terreno com base no valor do metro quadrado.
    //Caso o terreno seja um quadrado perfeito, aumente o valor do terreno em 10% pois este terreno é mais valioso.
    //Caso o terreno não seja um quadrado perfeito, de um desconto no valor total de 2%.

---

## ✅ Solução em Java

    import java.util.Scanner;

    public class App {

        public static void main(String[] args) {
            Scanner teclado = new Scanner(System.in);

            int frenteMts, lateralMts;
            float valorMetroQuadrado, valorTerreno;

            System.out.print("Digite a metragem da frente do terreno: ");
            frenteMts = teclado.nextInt();

            System.out.print("Digite a metragem da lateral do terreno: ");
            lateralMts = teclado.nextInt();

            System.out.print("Digite o valor do metro quadrado: ");
            valorMetroQuadrado = teclado.nextFloat();

            //calculando o valor do terreno
            valorTerreno = frenteMts * lateralMts * valorMetroQuadrado;

            // estrutura de decisão composta
            if (frenteMts == lateralMts) { //condicao para ver se é um quadrado
                //este bloco é executado se a condição (frenteMts == lateralMts) for verdadeira 
                //que o valor do terreno seja acrescido em 10%
                //valorTerreno = (valorTerreno * 0.1f) + valorTerreno;
                valorTerreno = (valorTerreno * 1.1f);
            } else {//se nao for quadrado da um desconto
                //este bloco é executado se a condição (frenteMts == lateralMts) for falsa 
                //valorTerreno = (valorTerreno * 0.02f) - valorTerreno;
                valorTerreno = (valorTerreno * 0.98f);
            }

            System.out.printf("O valor do terreno é: R$ %.2f reais", valorTerreno);
            teclado.close();
        }
    }

---

# Complemento da Lição

## 1) O que este exercício está treinando (bem direto)
Você está treinando 3 coisas ao mesmo tempo:

- **Entrada de dados** (ler valores do usuário com `Scanner`)
- **Cálculo** (área e valor do terreno)
- **Decisão** com `if/else` (aplicar regra diferente dependendo do formato)

---

## 2) Passo a passo do raciocínio do código
1. Ler `frenteMts` e `lateralMts`
2. Ler `valorMetroQuadrado`
3. Calcular o valor base:
   - `valorTerreno = frenteMts * lateralMts * valorMetroQuadrado`
4. Verificar se é quadrado perfeito:
   - se `frenteMts == lateralMts` → **aumenta 10%**
   - senão → **desconta 2%**
5. Mostrar o resultado formatado com 2 casas decimais (`%.2f`)

---

## 3) Por que `frenteMts == lateralMts` indica “quadrado perfeito”
Um terreno é “quadrado” quando:

- frente = lateral

Então, a comparação `frenteMts == lateralMts` é a condição mais simples possível para detectar isso.

---

## 4) Como funciona o aumento de 10% e o desconto de 2% (sem mistério)
### Aumentar 10%
- Aumentar 10% é o mesmo que multiplicar por **1.10**:
  - `valorTerreno = valorTerreno * 1.1f`

### Dar desconto de 2%
- Dar 2% de desconto é o mesmo que ficar com **98%** do valor:
  - `valorTerreno = valorTerreno * 0.98f`

---

## 5) Testes rápidos (valores para você digitar e conferir)
Use esses dados para validar:

### Caso 1: Quadrado (aumenta 10%)
- frente = 10
- lateral = 10
- metro = 50

Valor base: `10 * 10 * 50 = 5000`  
Com 10%: `5000 * 1.1 = 5500`

### Caso 2: Retângulo (desconta 2%)
- frente = 10
- lateral = 20
- metro = 50

Valor base: `10 * 20 * 50 = 10000`  
Com 2% desconto: `10000 * 0.98 = 9800`

---

## 6) Erros comuns de iniciante (para evitar)
- Confundir `==` com `=`  
  - `==` compara
  - `=` atribui valor
- Esquecer de multiplicar tudo antes de aplicar o aumento/desconto
- Ler `float` com `nextInt()` (tem que ser `nextFloat()`)

---

## 7) Exercício extra (fixação)
Altere o programa para imprimir também:

- Área do terreno (`frenteMts * lateralMts`)
- Se foi aplicado **aumento** ou **desconto**

Exemplo de saída:
- `Área: 100 m²`
- `Regra: Aumento de 10% (quadrado)`
- `Valor final: R$ 5500,00`

<!-- nav_start -->
---
Anterior: [Operadores LÃ³gicos](../docs/43_Operadores_Logicos_2.md) | Próximo: [If Else: ExercÃ­cio 2](../docs/45_If_Else_Exercicio_2.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

