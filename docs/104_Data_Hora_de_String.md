# Criando uma Data ou Hora a partir de uma String

---

Criando uma Data ou Hora a partir de uma String


Para a realização de operações com data e hora como adicionar e subtrair, é necessário que a data esteja no formato de objeto LocalDate ou LocalTime. Para isto, as seguintes operações são necessárias.



Para Data:

    import java.time.LocalDate;
    import java.time.format.DateTimeParseException;

    public class App {
        public static void main(String[] args) {
            String dataString = "2024-12-11"; // String no formato yyyy-MM-dd

            try {
                LocalDate localDate = LocalDate.parse(dataString);

                System.out.println(localDate); // Exemplo: 2024-12-11
            } catch (DateTimeParseException e) {
                System.out.println("Erro ao converter a string para data: " + e.getMessage());
            }
        }
    }

ou quando a data não está no formato americano yyyy-mm-dd é necessário utilizar a classe DateTimeFormatter.
import java.time.LocalDate;
import java.time.format.DateTimeFormatter;
import java.time.format.DateTimeParseException;

public class App {
    public static void main(String[] args) {
        // String no formato dd/MM/yyyy
        String dataString = "11/12/2024"; 
        
        try {
           DateTimeFormatter formatter = DateTimeFormatter.ofPattern("dd/MM/yyyy");
           LocalDate localDate = LocalDate.parse(dataString, formatter);
           System.out.println(localDate); // Exemplo: 2024-12-11
        } catch (DateTimeParseException e) {
            System.out.println("Erro ao converter a string para data: " + e.getMessage());
        }
    }
}

Para Hora:
import java.time.LocalTime;
import java.time.format.DateTimeParseException;

public class App {
    public static void main(String[] args) {
        String horaString = "14h30m"; // Exemplo de string no formato "HH:mm"
        
        try {
            LocalTime hora = LocalTime.parse(horaString);
            System.out.println("Hora: " + hora);
        } catch (DateTimeParseException e) {
            System.out.println("Erro ao fazer o parsing da hora: " + e.getMessage());
        }
    }
}
ou quando a hora estiver no formato am/pm
import java.time.LocalTime;
import java.time.format.DateTimeFormatter;
import java.time.format.DateTimeParseException;

public class App {
    public static void main(String[] args) {
        // Exemplo de string no formato "hh:mm a". O a representa o formato am/pm
        String horaString = "02:30 PM"; 
        
        // Definir o formato do padrão AM/PM
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("hh:mm a");
        
        try {
            // Fazer o parsing da string para LocalTime
            LocalTime hora = LocalTime.parse(horaString, formatter);
            System.out.println("Hora: " + hora);
        } catch (DateTimeParseException e) {
            System.out.println("Erro ao fazer o parsing da hora: " + e.getMessage());
        }
    }
}

Para Data e Hora no formato padrão
import java.time.LocalDateTime;
import java.time.format.DateTimeParseException;

public class App {
    public static void main(String[] args) {
        // Exemplo de string no formato padrão do java "yyyy-MM-dd'T'HH:mm:ss"
        String dataHoraString = "2024-12-11T14:30:00"; 
        
        try {
            LocalDateTime dataHora = LocalDateTime.parse(dataHoraString);
            System.out.println("Data e Hora: " + dataHora);
        } catch (DateTimeParseException e) {
            System.out.println("Erro ao fazer o parsing da data e hora: " + e.getMessage());
        }
    }
}

ou para a data e hora em um formato customizado utilizando o DateTimeFormatter
import java.time.LocalDateTime;
import java.time.format.DateTimeFormatter;
import java.time.format.DateTimeParseException;

public class App {
    public static void main(String[] args) {
        // Exemplo de string no formato customizado "yyyy-MM-dd hh:mm a"
        String dataHoraString = "2024-12-11 02:30 PM"; 

        //String dataHoraString = "2024-12-11 02:30"; 
        
        // Definir o formato de data e hora com AM/PM
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd hh:mm a");

        // Formato de 24 horas
        //DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd hh:mm");
        
        try {
            // Fazer o parsing da string para LocalDateTime
            LocalDateTime dataHora = LocalDateTime.parse(dataHoraString, formatter);
            System.out.println("Data e Hora: " + dataHora);
        } catch (DateTimeParseException e) {
            System.out.println("Erro ao fazer o parsing da data e hora: " + e.getMessage());
        }
    }
}

---

Complementos (sem substituir o conteúdo acima)

## ✅ Atenção: exemplos de hora precisam bater com o formato
No trecho:

- Você escreveu: `String horaString = "14h30m";`
- Mas o `LocalTime.parse(...)` **não entende** `h` e `m` por padrão.

O formato padrão aceito por `LocalTime.parse()` é algo como:
- `HH:mm` → `14:30`
- `HH:mm:ss` → `14:30:00`

Se você quiser aceitar `"14h30m"`, precisa usar `DateTimeFormatter` com o padrão correspondente.

Exemplo para `"14h30m"`:

    import java.time.LocalTime;
    import java.time.format.DateTimeFormatter;
    import java.time.format.DateTimeParseException;

    public class App {
        public static void main(String[] args) {
            String horaString = "14h30m";

            try {
                DateTimeFormatter formatter = DateTimeFormatter.ofPattern("HH'h'mm'm'");
                LocalTime hora = LocalTime.parse(horaString, formatter);

                System.out.println("Hora: " + hora);
            } catch (DateTimeParseException e) {
                System.out.println("Erro ao fazer o parsing da hora: " + e.getMessage());
            }
        }
    }

## ✅ `MM` (mês) vs `mm` (minutos)
Isso derruba muita gente no começo:

- `MM` = **mês**
- `mm` = **minutos**

Exemplos:
- Data: `dd/MM/yyyy`
- Hora: `HH:mm:ss`

## ✅ 24 horas vs 12 horas (AM/PM)
- `HH` = 24 horas (00–23)
- `hh` = 12 horas (01–12) e **precisa** do `a` (AM/PM) quando for o caso

Exemplos:
- `HH:mm` → `18:30`
- `hh:mm a` → `06:30 PM`

## ✅ Boas práticas rápidas
- Quando o usuário digitar data/hora, sempre valide:
  - se o formato está correto
  - se os valores fazem sentido (ex: 31/02/2024 não existe)
- Sempre prefira `DateTimeParseException` para tratar erro de conversão.

## ✅ Dica bônus: parse + format juntos
Se você quer “ler em um formato e exibir em outro”:

    import java.time.LocalDate;
    import java.time.format.DateTimeFormatter;

    public class App {
        public static void main(String[] args) {
            String entrada = "11/12/2024";

            DateTimeFormatter fmtEntrada = DateTimeFormatter.ofPattern("dd/MM/yyyy");
            DateTimeFormatter fmtSaida = DateTimeFormatter.ofPattern("yyyy-MM-dd");

            LocalDate data = LocalDate.parse(entrada, fmtEntrada);

            System.out.println("Data convertida: " + data.format(fmtSaida));
        }
    }

<!-- nav_start -->
---
Anterior: [Classe para representar data e hora em Java](../docs/103_Data_e_Hora.md) | Próximo: [SubtraÃ§Ã£o Entre Datas e Horas](../docs/105_Subtracao_Datas_Horas.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

