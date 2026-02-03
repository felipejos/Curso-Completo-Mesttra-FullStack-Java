# âœ… Conceito Switch Case

O **switch case** Ã© uma estrutura de controle de fluxo usada em linguagens como **Java**, **C** e **JavaScript** para executar **blocos diferentes de cÃ³digo** conforme o valor de uma variÃ¡vel.

Ele Ã© uma alternativa mais **organizada e legÃ­vel** ao uso de muitos `if` e `else if`, principalmente quando vocÃª faz vÃ¡rias comparaÃ§Ãµes do tipo:

- `numero == 1`
- `numero == 2`
- `numero == 3`
- etc...

---

## ðŸŽ¯ Exemplo com if / else if

Imagine um cÃ³digo para converter um nÃºmero para sua escrita por extenso:

if (numero == 1) {
   System.out.print("um")
} else if (numero == 2) {
   System.out.print("dois")
} else if (numero == 3) {
   System.out.print("trÃªs")
} else if (numero == 4) {
   System.out.print("quatro")
} else if (numero == 5) {
   System.out.print("cinco")
} else if (numero == 6) {
   System.out.print("seis")
} else if (numero == 7) {
   System.out.print("sete")
} else if (numero == 8) {
   System.out.print("oito")
} else if (numero == 9) {
   System.out.print("9")
}

âœ… Note que nesse cÃ³digo estamos sempre comparando a variÃ¡vel **numero** com igualdade `==`.

Quando isso acontece, podemos usar o **switch case**, evitando repetir `numero == ...` vÃ¡rias vezes.

---

## âœ… Mesmo exemplo (trecho) com if / else if

if (numero == 1) {
            System.out.print("um");
         } else if (numero == 2) {
            System.out.print("dois");
         } else if (numero == 3) {
            System.out.print("trÃªs");
         } else if (numero == 4) {
            System.out.print("quatro");
         } else if (numero == 5) {
            System.out.print("cinco");
         } else if (numero == 6) {
            System.out.print("seis");
         } else if (numero == 7) {
            System.out.print("sete");
         } else if (numero == 8) {
            System.out.print("oito");
         } else if (numero == 9) {
            System.out.print("9");
         }

---

## â­ O papel do `default` (como se fosse um else)
![OnlineGDB - exemplo](../images/switch.png)

O **switch case** tambÃ©m pode ter um comportamento igual ao `else`.  
Ou seja, se o valor **nÃ£o se encaixar em nenhum case**, vocÃª define um padrÃ£o com `default` (normalmente a Ãºltima opÃ§Ã£o).

---

## âœ… Exemplo de agrupamento de condiÃ§Ãµes

Caso vocÃª tenha um trecho equivalente a este:

if (numero == 1 || numero == 2) {
      //execute algo
} else if (numero >= 3 && numero <= 6 ) {
      //execute isto
}

Podemos atingir o mesmo resultado usando:

switch (numero) {
    case 1:
    case 2:
        // Execute algo
        break;

    case 3:
    case 4:
    case 5:
    case 6:
        // Execute isto
        break;
}

ðŸ“Œ **Como funciona aqui?**
- Como nÃ£o temos nada logo depois de `case 1`, ele â€œcaiâ€ para o prÃ³ximo (`case 2`) e executa o bloco.
- EntÃ£o esse bloco serÃ¡ executado se `numero` for **1 ou 2**.

O mesmo ocorre com **3, 4, 5 e 6**:
- Como nÃ£o hÃ¡ cÃ³digo individual nesses `case`, todos executam o mesmo bloco `"// Execute isto"`.

---

<!-- nav_start -->
---
Anterior: [Lista de ExercÃ­cios 03 - Estruturas de DecisÃ£o](../docs/59_Lista_Exercicios_03.md) | Próximo: [VÃ­deo Switch Case](../docs/61_Video_Switch_Case.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

