# Lista 9 - Algoritmos de Seleção

---

## Conteúdo original

Lista 9 - Algoritmos de Seleção


Os exercícios abaixo no beecrowd são possíveis de resolver apenas com comandos de entrada e saída, operadores aritméticos/comparação/lógicos e estruturas de decisão, ou seja, não é necessário estruturas de repetição e vetores/matrizes.

### ✅ Organização sugerida (checklist)

- [ ] 1035 — https://judge.beecrowd.com/pt/problems/view/1035  
- [ ] 1036 — https://judge.beecrowd.com/pt/problems/view/1036  
- [ ] 1037 — https://judge.beecrowd.com/pt/problems/view/1037  
- [ ] 1038 — https://judge.beecrowd.com/pt/problems/view/1038  
- [ ] 1040 — https://judge.beecrowd.com/pt/problems/view/1040  
- [ ] 1041 — https://judge.beecrowd.com/pt/problems/view/1041  
- [ ] 1042 — https://judge.beecrowd.com/pt/problems/view/1042  
- [ ] 1043 — https://judge.beecrowd.com/pt/problems/view/1043  
- [ ] 1044 — https://judge.beecrowd.com/pt/problems/view/1044  
- [ ] 1045 — https://judge.beecrowd.com/pt/problems/view/1045  
- [ ] 1046 — https://judge.beecrowd.com/pt/problems/view/1046  
- [ ] 1047 — https://judge.beecrowd.com/pt/problems/view/1047  
- [ ] 1048 — https://judge.beecrowd.com/pt/problems/view/1048  
- [ ] 1049 — https://judge.beecrowd.com/pt/problems/view/1049  
- [ ] 1050 — https://judge.beecrowd.com/pt/problems/view/1050  
- [ ] 1051 — https://judge.beecrowd.com/pt/problems/view/1051  
- [ ] 1052 — https://judge.beecrowd.com/pt/problems/view/1052  
- [ ] 2057 — https://judge.beecrowd.com/pt/problems/view/2057  
- [ ] 2059 — https://judge.beecrowd.com/pt/problems/view/2059  
- [ ] 1061 — https://judge.beecrowd.com/pt/problems/view/1061  
- [ ] 2313 — https://judge.beecrowd.com/pt/problems/view/2313  
- [ ] 2670 — https://judge.beecrowd.com/pt/problems/view/2670  
- [ ] 2702 — https://judge.beecrowd.com/pt/problems/view/2702  
- [ ] 2717 — https://judge.beecrowd.com/pt/problems/view/2717  
- [ ] 2780 — https://judge.beecrowd.com/pt/problems/view/2780  
- [ ] 2787 — https://judge.beecrowd.com/pt/problems/view/2787  

---

### 📌 Dicas rápidas (if/else no beecrowd)

- **Se o enunciado pede intervalos**, preste atenção em:
  - `>=` (incluso)
  - `>`  (não incluso)
- **Double/float e formatação**:
  - Use `Locale.US` para garantir `.` nas casas decimais.
  - Use `System.out.printf(Locale.US, "... %.2f%n", valor);`
- **Comparação de double**:
  - Evite `==` com decimais (quando não for exigido explicitamente).
- **Ordem das condições importa**:
  - Comece do caso mais específico para o mais genérico (ou do maior para o menor), para não “engolir” condições.

---

### 🧱 Template Java (com if/else) — base para usar na Lista 9

    import java.io.BufferedReader;
    import java.io.InputStreamReader;
    import java.util.Locale;
    import java.util.StringTokenizer;

    public class Main {
        public static void main(String[] args) throws Exception {
            Locale.setDefault(Locale.US);

            BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

            // Exemplo: ler linha e quebrar em tokens
            // StringTokenizer st = new StringTokenizer(br.readLine());
            // int a = Integer.parseInt(st.nextToken());
            // int b = Integer.parseInt(st.nextToken());

            // Aqui você faz as condições com if / else if / else
            // e imprime exatamente como o beecrowd pede.
        }
    }

<!-- nav_start -->
---
Anterior: [Lista 8 - Algoritmos SequÃªnciais](../docs/98_Lista_08.md) | Próximo: [Conceito de Classe e Objeto](../docs/100_Classe_e_Objeto.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

