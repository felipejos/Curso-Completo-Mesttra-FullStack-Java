## Operador Ternário

O **operador ternário** é uma forma compacta de escrever uma estrutura condicional `if-else` em Java (e em várias outras linguagens). Ele foi criado para substituir a estrutura `if else` que tem o seguinte comportamento:

### Exemplo usando `if/else`

    double valor;
    double desconto;

    if (valor >= 40.6) {
        desconto = 0.05;
    } else {
        desconto = 0.02;
    }

Note que neste código estamos querendo **atribuir um determinado valor** à variável `desconto` baseado em critério.  
Se o resultado for **verdadeiro** da condição atribuimos o valor `0.05`, caso contrário atribuimos o valor `0.02`.

O operador ternário só poderá ser utilizado em situações como esta, onde queremos **atribuir um valor caso verdadeiro** a uma variável ou **outro valor na mesma variável em caso falso**.

---

### O mesmo exemplo usando operador ternário

    double valor;
    double desconto;

    desconto = (valor > 40.6) ? 0.05 : 0.02;

---

### Sintaxe do operador ternário

    variavel = (expressao_a_ser_avaliada) ? resultado_quando_verdadeiro : resultado_quando_falso;

<!-- nav_start -->
---
Anterior: [VÃ­deo Switch Case](../docs/61_Video_Switch_Case.md) | Próximo: [VÃ­deo Operador TernÃ¡rio](../docs/63_Video_Operador_Ternario.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

