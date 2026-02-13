Sorteio único de valores
Algoritmo para sortear 10 valores aleatorios entre 0 e 100 garantindo que um número não seja sorteado mais de uma vez.

Nesta implementação, estamos utilizando vetores, funções para estruturar e reaproveitar o código.

As funções implementadas, podem até fazer parte de uma classe estática utilizada para organizar o código e reaproveitar ele em outros projetos.

import java.util.Random;

public class App {
    public static void main(String[] args) {
        // criar uma estrutura para guardar 10 valores
        int ValoresSorteados[] = new int[10];

        // sorteia 10 valores e preenche no vetor
        for (int posicao = 0; posicao < ValoresSorteados.length; posicao++) { 
            ValoresSorteados[posicao] = obterNumeroAleatorioUnico( 0, 100, ValoresSorteados, posicao);
        }

        // exibe 10 valores na tela
        for (int valor : ValoresSorteados) {
            System.out.println(valor);
        }
    }

    public static boolean esteValorEstaVetor(int valores[], int ultimaPosicao, int valorSorteado){
        
        for (int i = 0; i < ultimaPosicao; i++) {
            // verifica se o valor sorteado já existe no vetor, se existir retorna true
            if (valores[i] == valorSorteado)
                return true;
        }

        // se chegar aqui é pq o valor não foi encontrado dentro do laco
        // caracterizando que o valor é unico, e nao foi sorteado ainda
        return false;
    }

    public static int obterNumeroAleatorioUnico(int minimo, int maximo, int valoresSorteados[], int ultimaPosicao){
        // estamos criando exceções customizadas pelo proprio desenvolvedor
        // na programação chamamos isto de "exceção de negócio"
        
        // impede que o valor maximo do sorteio seja menor ou igual ao valor minimo
        if (maximo <= minimo) { 
            throw new IllegalArgumentException("O valor máximo deve ser maior que o mínimo!");
        // impede que o intervalo de numeros a serem sorteados seja menor que a quantidade de valores únicos solicitados
        } else if ((maximo - minimo) < (valoresSorteados.length -1)){ 
            throw new IllegalArgumentException("Intervalo muito pequeno para a quantidade de valores únicos solicitados!");
        } 

        int valorSorteadoUnico;

        do {
            // obtém um valor aleatório
            valorSorteadoUnico = obterNumeroAleatorio(minimo, maximo);

            // garantir que o zero possa ser sorteado na primeira posição
            // como o vetor inicia com todos os valores zerados, se não fizermos esta verificação
            // o zero nunca será sorteado no primeiro sorteio
            if (ultimaPosicao == 0 && valorSorteadoUnico == 0 ) {   
               return 0;
            }
        
        // repete até que o valor sorteado seja único
        } while (esteValorEstaVetor(valoresSorteados, ultimaPosicao, valorSorteadoUnico));

        return valorSorteadoUnico;
    }

    public static int obterNumeroAleatorio(int minimo, int maximo){
        Random random = new Random();

        // + 1 é util pois o nextInt sempre sorteia de 0 até o numero informado -1
        // entao fazems +1 pra deixar mais simples para quem for usar esta funcao
        int valor = random.nextInt(maximo + 1) + minimo;
        //System.out.println("Valor sorteado: " + valor);

        return valor;
    }

}


O código a seguir é a mesma versão do anterior, no entanto não utilize funções para organizar o código. Compare os dois códigos para entender o benefício do uso de funções. Veja que nesta versão do código, é muito mais dificil entender como o código funciona.


import java.util.Random;

public class App {
    public static void main(String[] args) {
        Random random = new Random();
        int ValoresSorteados[] = new int[10];

        int minimo = 0;
        int maximo = 100;         

        // laço para repetir o sorteio de 10 valores únicos
        for (int posicao = 0; posicao < ValoresSorteados.length; posicao++) {

            int ultimaPosicao = posicao;
            int valorSorteadoUnico;

            // validações (antes eram do método obterNumeroAleatorioUnico)
            if (maximo <= minimo) {
                throw new IllegalArgumentException("O valor máximo deve ser maior que o mínimo!");
            } else if ((maximo - minimo) < (ValoresSorteados.length - 1)) {
                throw new IllegalArgumentException("Intervalo muito pequeno para a quantidade de valores únicos!");
            }

            do {
                // gerar número aleatório (antes era do método obterNumeroAleatorio)
                valorSorteadoUnico = random.nextInt(maximo + 1) + minimo;

                // permitir zero na primeira posição
                if (ultimaPosicao == 0 && valorSorteadoUnico == 0) {
                    break;
                }

                // verificar se o número já foi sorteado (antes era do método esteValorEstaVetor)
                boolean existe = false;
                for (int i = 0; i < ultimaPosicao; i++) {
                    if (ValoresSorteados[i] == valorSorteadoUnico) {
                        existe = true;
                        break;
                    }
                }

                // repetir enquanto o valor já existir
                if (!existe) {
                    break;
                }

            } while (true);

            ValoresSorteados[posicao] = valorSorteadoUnico;
        }

        // exibir valores
        for (int valor : ValoresSorteados) {
            System.out.println(valor);
        }
    }
}

---

**Complementos (mais completo e fácil de entender)**

### 1) Qual é a ideia do “sorteio único”?
Você quer preencher um vetor com **10 números aleatórios**, mas com uma regra:

- **não pode repetir** nenhum número já sorteado.

Na prática, isso significa:
1. sortear um número;
2. verificar se ele já existe no vetor nas posições já preenchidas;
3. se já existir, sortear novamente;
4. se não existir, gravar na posição atual.

Esse padrão é um “sorteia e valida” usando repetição (`do...while`).

---

### 2) Por que a versão com funções é mais fácil de entender?
Porque você separou responsabilidades:

- `obterNumeroAleatorio(...)`  
  **só sorteia** um número dentro de um intervalo.

- `esteValorEstaVetor(...)`  
  **só verifica** se o número já existe no vetor.

- `obterNumeroAleatorioUnico(...)`  
  **coordena** as duas coisas (sorteia + verifica) até garantir que é único.

Ou seja: cada função faz **uma coisa só**, então o `main` fica curto e legível.

---

### 3) Como o algoritmo garante que não repete valores?
O ponto central é este trecho:

do {
    valorSorteadoUnico = obterNumeroAleatorio(minimo, maximo);
} while (esteValorEstaVetor(valoresSorteados, ultimaPosicao, valorSorteadoUnico));

- Se o valor **já estiver** no vetor, `esteValorEstaVetor(...)` retorna `true`
- Logo o `do...while` **repete** e sorteia outro número
- Só sai do loop quando a função retornar `false` (valor único)

Isso garante que, ao gravar em `ValoresSorteados[posicao]`, aquele valor ainda não tinha sido usado.

---

### 4) Atenção: existe um problema no seu sorteio (off-by-one)
O seu método:

int valor = random.nextInt(maximo + 1) + minimo;

Quando `minimo = 0` e `maximo = 100`, funciona e gera `0..100`.

Mas se `minimo` for diferente de 0, exemplo `minimo = 10` e `maximo = 100`:
- `random.nextInt(maximo + 1)` gera `0..100`
- depois você soma `+ minimo`, virando `10..110` (passa do máximo)

A fórmula correta (conceito) para sortear entre `minimo` e `maximo` (inclusive) é:

valor = random.nextInt((maximo - minimo) + 1) + minimo;

Isso garante que o resultado fique sempre entre:
- mínimo: `minimo`
- máximo: `maximo`

---

### 5) O “caso especial do zero” (por que você precisou dele)
Você explicou muito bem a pegadinha:

- Em Java, um vetor de `int` nasce com todos os valores `0`.
- No primeiro sorteio (`ultimaPosicao == 0`), você procura repetição no vetor.
- Mas se você comparar com o vetor que está “todo zero”, o `0` parece “já existir”.

Você resolveu com:

if (ultimaPosicao == 0 && valorSorteadoUnico == 0) {   
    return 0;
}

Ou seja: “na primeira posição, se sortear 0, aceita direto”.

**Observação importante (conceito):**
Isso só é necessário porque você usa `0` como valor padrão e está verificando “existência” no vetor sem uma marca de posições “ainda vazias”.
Depois, quando você aprender `boolean[]` ou `Set`, dá pra evitar esse tipo de caso especial com mais elegância.

---

### 6) Validações (“exceções de negócio”) — o que elas protegem
Você criou validações muito boas, porque evitam situações impossíveis:

- `if (maximo <= minimo)`  
  Impede intervalo inválido.

- `else if ((maximo - minimo) < (valoresSorteados.length -1))`  
  Tenta impedir que o intervalo seja pequeno demais para a quantidade de números únicos.

**Pegadinha conceitual:**  
Se o sorteio é “inclusivo” (ex.: 0 a 100 inclui 101 valores), então a quantidade de valores possíveis é:

quantidadePossivel = (maximo - minimo) + 1

Para ser possível sortear `valoresSorteados.length` valores únicos, precisa:

(maximo - minimo) + 1 >= valoresSorteados.length

Ou seja:

(maximo - minimo) >= valoresSorteados.length - 1

A sua verificação está alinhada com isso, mas é importante lembrar que isso depende do “+1” do inclusivo.

---

### 7) Comparando com a versão sem funções (o benefício real)
Na versão sem funções:
- você mistura no `main`: sorteio + validação + busca por repetido + controle do loop
- o código fica longo e difícil de “enxergar” o objetivo

Na versão com funções:
- o `main` explica o programa em português quase que sozinho:

“Para cada posição do vetor, sorteie um número único. Depois imprima.”

É exatamente o tipo de organização que melhora manutenção e reutilização.

---

### 8) Onde essa lógica é usada no mundo real?
Esse mesmo padrão aparece em várias situações:

- gerar **IDs aleatórios** sem repetição
- sortear **ordem de apresentação** de alunos
- criar **cartelas** (bingo, loteria simples)
- embaralhar perguntas de um **quiz**
- gerar **senha temporária** sem repetir caracteres

---

### 9) Próximo passo natural (quando você quiser evoluir)
Você já fez do jeito “didático” (perfeito para aprender).
Depois, o próximo nível é:

- usar uma estrutura para “marcar” rapidamente o que já saiu
  - exemplo: `boolean[] sorteado = new boolean[101];`
- ou usar um `Set<Integer>` (mais avançado, mas muito comum)

Mas por enquanto, seu código está ótimo para fixar vetor + laços + funções + validação.

<!-- nav_start -->
---
Anterior: [132 Codigo Final Forca](../docs/132_Codigo_Final_Forca.md) | Proximo: [134 Gerenciamento Alunos](../docs/134_Gerenciamento_Alunos.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
