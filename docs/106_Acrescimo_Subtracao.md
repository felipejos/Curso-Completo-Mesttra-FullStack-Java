# Operações de Acréscimo e Subtração em Datas e Horas


Para adicionar ou subtrair dias, meses ou anos em uma data, primeiramente a data já deve estar no formato LocalDate. 



    import java.time.LocalDate;

    public class App {
        public static void main(String[] args) {
            // Obtém a data atual, ou você poderia criar a data a partir de uma string ou pelo construtor padrão
            LocalDate dataAtual = LocalDate.now();  

            // LocalDate dataAtual = LocalDate.of(2024, 12, 23); 

            // Adiciona 10 dias
            dataAtual = dataAtual.plusDays(10);  
            System.out.println(dataAtual);  

            // Adiciona 3 meses
            dataAtual = dataAtual.plusMonths(3);
            System.out.println(dataAtual);  

            // Adiciona 2 anos
            dataAtual = dataAtual.plusYears(2); 
            System.out.println(dataAtual);  
        }
    }

Para a subtração basta utilizar os seguintes métodos:

minusDays(dias): Subtrai o número especificado de dias.
minusMonths(meses): Subtrai o número especificado de meses.
minusYears(anos): Subtrai o número especificado de anos.

Para as mesmas operações em uma Hora basta:



    import java.time.LocalTime;

    public class App {
        public static void main(String[] args) {
            LocalTime horaAtual = LocalTime.now();

            // Adiciona 5 horas
            horaAtual = horaAtual.plusHours(5);  
            System.out.println("Hora após adicionar 5 horas: " + horaAtual);
        }
    }

plusHours(horas): Adiciona o número especificado de horas à hora atual.
plusMinutes(minutos): Adiciona o número especificado de minutos à hora atual.
plusSeconds(segundos): Adiciona o número especificado de segundos à hora atual.
minusHours(horas): Subtrai o número especificado de horas da hora atual.
minusMinutes(minutos): Subtrai o número especificado de minutos da hora atual.
minusSeconds(segundos): Subtrai o número especificado de segundos da hora atual.

---

## Complemento: entendendo de um jeito fácil (e sem pegadinhas)

### 1) Ideia principal (muito importante)
No `java.time`, **datas e horas são imutáveis**.

Isso significa:
- `dataAtual.plusDays(10)` **não altera** a data original.
- Ele **cria uma nova data** com o resultado.

Por isso você fez corretamente:
- `dataAtual = dataAtual.plusDays(10);`

✅ Se você esquecer de reatribuir, nada muda:
    LocalDate data = LocalDate.now();
    data.plusDays(10);       // cria outra data, mas você jogou fora
    System.out.println(data); // continua sendo a data de hoje

---

### 2) Exemplo prático com saída esperada (para fixar)
Supondo que hoje seja `2024-12-23` (apenas exemplo):

    LocalDate data = LocalDate.of(2024, 12, 23);

    data = data.plusDays(10);    // 2025-01-02
    data = data.plusMonths(3);   // 2025-04-02
    data = data.plusYears(2);    // 2027-04-02

✅ Saída esperada (aproximada):
- 2025-01-02
- 2025-04-02
- 2027-04-02

---

### 3) Pegadinha comum: mês com “dia que não existe”
Algumas datas “não existem” em certos meses (ex: 31 em fevereiro).

O `LocalDate` resolve isso de forma inteligente:
- Se você somar 1 mês em `31/01`, o Java ajusta para o último dia possível.

Exemplo:
    LocalDate d = LocalDate.of(2024, 1, 31);
    System.out.println(d.plusMonths(1));

✅ Resultado:
- 2024-02-29 (se for ano bissexto)
- 2024-02-28 (se não for)

---

### 4) Dica prática: encadeando operações (mais limpo)
Você pode fazer “em cadeia”, deixando mais curto:

    LocalDate novaData = LocalDate.now()
        .plusDays(10)
        .plusMonths(3)
        .plusYears(2);

    System.out.println(novaData);

Mesma lógica, mais organizado.

---

### 5) Para horas: cuidado com “virar o dia”
`LocalTime` só representa **hora**, sem data.

Então:
- Se for `22:00` e você somar 5 horas → vira `03:00`
- Mas **não existe “amanhã”** no `LocalTime`, ele só gira o relógio.

Exemplo:
    LocalTime t = LocalTime.of(22, 0);
    System.out.println(t.plusHours(5));

✅ Resultado:
- 03:00

Se você precisa controlar “dia + hora”, use `LocalDateTime`.

---

### 6) Quando usar cada tipo (resumo rápido)
- `LocalDate` → quando importa só a **data** (aniversário, vencimento, etc.)
- `LocalTime` → quando importa só a **hora** (horário de aula, alarme, etc.)
- `LocalDateTime` → quando importa **data e hora juntas** (evento, log, agendamento)

---

### 7) Extra útil: adicionar semanas (atalho)
Além de dias/meses/anos, tem:
    dataAtual = dataAtual.plusWeeks(2);  // +2 semanas

E também:
    dataAtual = dataAtual.minusWeeks(1); // -1 semana

---

<!-- nav_start -->
---
Anterior: [105 Subtracao Datas Horas](../docs/105_Subtracao_Datas_Horas.md) | Proximo: [107 Lista 10](../docs/107_Lista_10.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
