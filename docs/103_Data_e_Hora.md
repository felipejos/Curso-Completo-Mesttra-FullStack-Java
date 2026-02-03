# Classe para representar data e hora em Java

---

Classe para representar data e hora em Java


O Java disponibiliza uma API (conjunto de classes) para trabalhar com datas e horas. Até a versão 7 era utilizada o pacote java.util . Neste pacote temos as classes Date  e Calendar para o gerenciamento de datas e horas. A partir da versão 8 do java foi introduzido o pacote java.time que traz consigo algumas facilidades em relação ao seu predecessor.



Abaixo temos um exemplo de código 



import java.time.LocalDate;
import java.time.LocalTime;
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;

public class App {
    public static void main(String[] args) {
        // Criando datas e horas
        LocalDate hoje = LocalDate.now(); // Data atual
        LocalTime agora = LocalTime.now(); // Hora atual
        LocalDateTime dataHoraAtual = LocalDateTime.now(); // Data e hora atuais

        // Exibindo as datas e horas
        System.out.println("Data de hoje: " + hoje);
        // O resultado será algo do tipo 2024-12-11
        // O formato yyyy-mm-dd, onde yyyy ano com 4 dígitos, mm o mês e dd o dia

        System.out.println("Hora atual: " + agora);
        // O resultado será algo do tipo 15:18:35.990285900
        // O formato HH:mm:ss.SSSSSSSSS, onde: HH representa as horas, mm representa os minutos,
        // ss representa os segundos, SSSSSSSSS representa os nanosegundos.

        System.out.println("Data e hora atuais: " + dataHoraAtual);
        // O resultado será algo do tipo 2024-12-11T15:18:35.990285900

        // Formatando data
        DateTimeFormatter formato = DateTimeFormatter.ofPattern("dd/MM/yyyy");
        // Apenas à título de informação, no comando acima não foi necessário utilizar o 
        // new DateTimeFormatter pois o método ofPattern é um método estático que utiliza
        // o padrão de projeto factory "fábrica". Mas não se preocupe com isso.

        System.out.println("\nData formatada: " + hoje.format(formato));

        formato = DateTimeFormatter.ofPattern("HH:mm:ss");
        System.out.println("Hora formatada 24horas: " + agora.format(formato));

        formato = DateTimeFormatter.ofPattern("hh:mm:ss a");
        System.out.println("Hora formatada 12horas am/pm: " + agora.format(formato));

        formato = DateTimeFormatter.ofPattern("dd/MM/yyyy HH:mm:ss");
        System.out.println("Data/Hora formatada: " + dataHoraAtual.format(formato));
        
        formato = DateTimeFormatter.ofPattern("dd/MM/yyyy hh:mm:ss a");
        System.out.println("Data/Hora formatada: " + dataHoraAtual.format(formato));
    }
}

---

Complementos (sem substituir o conteúdo acima)

## ✅ Por que o `java.time` é recomendado (Java 8+)
- O pacote `java.time` é mais moderno e mais seguro que `java.util.Date` e `java.util.Calendar`.
- Ele foi inspirado na biblioteca Joda-Time e traz tipos bem definidos:
  - `LocalDate` → **apenas data** (sem hora)
  - `LocalTime` → **apenas hora** (sem data)
  - `LocalDateTime` → **data + hora** (sem fuso)
- Esses tipos são **imutáveis**: você não altera o objeto original, você cria outro com a mudança.

## ✅ Observação importante: fuso horário (timezone)
- `LocalDate/LocalTime/LocalDateTime` **não guardam fuso horário**.
- Se você precisar de fuso (ex: horário do Brasil, UTC, etc.), use:
  - `ZonedDateTime` (data/hora com fuso)
  - `Instant` (momento exato no tempo, em UTC)
  - `ZoneId` (ex: `America/Sao_Paulo`)

Exemplo rápido de fuso:

    import java.time.ZonedDateTime;
    import java.time.ZoneId;

    ZonedDateTime agoraBrasil = ZonedDateTime.now(ZoneId.of("America/Sao_Paulo"));
    System.out.println(agoraBrasil);

## ✅ Como somar/subtrair datas e horas
Você não precisa fazer conta “na mão”. Existem métodos prontos:

    LocalDate hoje = LocalDate.now();
    System.out.println(hoje.plusDays(7));      // +7 dias
    System.out.println(hoje.minusMonths(1));   // -1 mês

    LocalTime agora = LocalTime.now();
    System.out.println(agora.plusHours(2));    // +2 horas

    LocalDateTime dt = LocalDateTime.now();
    System.out.println(dt.plusMinutes(30));    // +30 minutos

## ✅ Como calcular diferença entre datas (Duration e Period)
- `Period` → diferença em **dias/meses/anos** (datas)
- `Duration` → diferença em **horas/minutos/segundos** (tempo)

Exemplo:

    import java.time.LocalDate;
    import java.time.Period;

    LocalDate inicio = LocalDate.of(2025, 10, 23);
    LocalDate fim = LocalDate.now();

    Period p = Period.between(inicio, fim);
    System.out.println("Diferença: " + p.getYears() + " anos, " + p.getMonths() + " meses, " + p.getDays() + " dias");

## ✅ Converter String → Data (parse)
Além de formatar com `format()`, você pode **ler uma data digitada** com `parse()`:

    DateTimeFormatter fmt = DateTimeFormatter.ofPattern("dd/MM/yyyy");
    LocalDate data = LocalDate.parse("23/10/2025", fmt);
    System.out.println(data);

## ✅ Dica rápida de padrões mais comuns (DateTimeFormatter)
- `dd/MM/yyyy` → 23/10/2025
- `HH:mm:ss` → 18:45:10 (24h)
- `hh:mm:ss a` → 06:45:10 PM (12h)
- `dd/MM/yyyy HH:mm:ss` → 23/10/2025 18:45:10

<!-- nav_start -->
---
Anterior: [Classe utilitÃ¡ria para leitura de dados](../docs/102_Classe_Utilitaria_Leitura.md) | Próximo: [Criando uma Data ou Hora a partir de uma String](../docs/104_Data_Hora_de_String.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

