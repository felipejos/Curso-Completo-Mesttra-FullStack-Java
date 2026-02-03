# Subtração Entre Datas e Horas

---

Subtração Entre Datas e Horas


Para as operações de subtração de Datas e Horas utlizamos a classe Period para diferenças entre objetos LocalDate e a classe Duration para diferenças entre objetos LocalTime e LocalDateTime.



Diferença entre duas datas

    import java.time.LocalDate;
    import java.time.Period;

    public class App {
        public static void main(String[] args) {
            // Definir duas datas usando LocalDate
            LocalDate data1 = LocalDate.of(2024, 1, 1); // 1º de janeiro de 2024
            LocalDate data2 = LocalDate.of(2024, 12, 11); // 11 de dezembro de 2024

            // Calcular a diferença entre as duas datas
            Period periodo = Period.between(data1, data2);

            // Exibir a diferença em anos, meses e dias
            System.out.println("Diferença: " + periodo.getYears() + " anos, " + 
                               periodo.getMonths() + " meses e " + 
                               periodo.getDays() + " dias.");
        }
    }

Diferença entre duas datas com horas

    import java.time.Duration;
    import java.time.LocalDateTime;

    public class App {
        public static void main(String[] args) {
            // Definir duas datas/hora usando LocalDateTime
            LocalDateTime data1 = LocalDateTime.of(2024, 12, 10, 10, 30); // 10 de Dezembro de 2024, 10:30
            LocalDateTime data2 = LocalDateTime.of(2024, 12, 11, 15, 45); // 11 de Dezembro de 2024, 15:45

            // Calcular a diferença entre as duas datas
            Duration duration = Duration.between(data1, data2);

            // Obter a diferença em horas
            long horas = duration.toHours();

            // Exibir a diferença
            System.out.println("Diferença em horas: " + horas);
        }
    }

Diferença entre duas horas

    import java.time.Duration;
    import java.time.LocalTime;

    public class App {
        public static void main(String[] args) {
            // Definir duas horas usando LocalTime
            LocalTime hora1 = LocalTime.of(10, 30); // 10:30
            LocalTime hora2 = LocalTime.of(15, 45); // 15:45

            // Calcular a diferença entre as duas horas
            Duration duration = Duration.between(hora1, hora2);

            // Obter a diferença em horas
            long horas = duration.toHours();
            
            // Obter a diferença em minutos
            long minutos = duration.toMinutes() % 60;

            // Exibir a diferença
            System.out.println("Diferença em horas: " + horas);
            System.out.println("Diferença em minutos: " + minutos);
        }
    }

---

Complementos (sem substituir o conteúdo acima)

## ✅ Quando usar `Period` vs `Duration`
- **`Period`** → diferença “no calendário” (anos/meses/dias) entre **`LocalDate`**
  - Ex.: de 01/01/2024 até 11/12/2024 → *0 anos, 11 meses e 10 dias* (depende do calendário)
- **`Duration`** → diferença “no relógio” (horas/minutos/segundos) entre **`LocalTime`** e **`LocalDateTime`**
  - Ex.: de 10:30 até 15:45 → *5 horas e 15 minutos*

## ✅ Atenção: `Duration.toHours()` “corta” os minutos
No seu exemplo com `LocalDateTime`:
- `toHours()` retorna apenas **as horas inteiras**.
- Se quiser mostrar também minutos/segundos, você pode decompor assim:

    Duration duration = Duration.between(data1, data2);
    long totalMinutos = duration.toMinutes();
    long horas = totalMinutos / 60;
    long minutos = totalMinutos % 60;

    System.out.println("Diferença: " + horas + "h " + minutos + "min");

## ✅ Diferença negativa (quando a segunda data/hora é “antes”)
Se `data2` for anterior a `data1`:
- `Period.between(data1, data2)` pode gerar valores negativos.
- `Duration.between(data1, data2)` também pode ser negativa.

Dica: para evitar sinal negativo na exibição, você pode usar:

    Duration duration = Duration.between(data1, data2).abs();

## ✅ Exibir diferença “completa” em dias/horas/minutos (LocalDateTime)
Se você quer algo mais “humano” do tipo **X dias, Y horas, Z minutos**:

    Duration duration = Duration.between(data1, data2);

    long totalSegundos = duration.getSeconds();
    long dias = totalSegundos / 86400;
    long horas = (totalSegundos % 86400) / 3600;
    long minutos = (totalSegundos % 3600) / 60;

    System.out.println("Diferença: " + dias + " dias, " + horas + " horas e " + minutos + " minutos");

## ✅ Observação importante sobre fuso horário
`LocalDate`, `LocalTime` e `LocalDateTime` **não** carregam fuso horário.
Se você estiver lidando com horários reais de países diferentes (ou horário de verão), aí normalmente entra:
- `ZonedDateTime` / `OffsetDateTime`
- `ZoneId`

Mas para exercícios e cálculos locais, `LocalDateTime` é perfeito.

<!-- nav_start -->
---
Anterior: [Criando uma Data ou Hora a partir de uma String](../docs/104_Data_Hora_de_String.md) | Próximo: [OperaÃ§Ãµes de AcrÃ©scimo e SubtraÃ§Ã£o em Datas e Horas](../docs/106_Acrescimo_Subtracao.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

