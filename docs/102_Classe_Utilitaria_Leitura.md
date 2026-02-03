# Classes utilitárias versus métodos estáticos

---

## Conceito

Classes utilitárias versus métodos estáticos


Quando precisamos criar classes que não possuem atributos de instância, ou seja, do objeto, como classes utilitárias de validação, é comum implementar seus métodos como estáticos. Dessa forma, para utilizar esses métodos em outras classes, não é necessário instanciar a classe com new NomeDaClasse(),  bastando chamá-los diretamente, por exemplo: Validador.validarEmail(...).



No próximo artigo estamos disponibilizando a classe Leitura que terá como objetivo implementar a leitura dos tipos de dados. Nesta classe você verá que todos os métodos são estáticos. Isto significa que para utilizar esta classe não é necessário realizar criação do objeto com: Leitura leitura = new Leitura(). 



No entanto, não são todas as classes que possuem está caracterísitca. Classes que irão representar atributos de objeto como classes: Carro, Pessoa, Usuario, precisam ser classes que possuem atributos que não sejam estáticos. Pois desejamos que cada objeto (instância da classe), mantenha os seus atributos isolados uns dos outros. Para estes casos, os atributos (variáveis) serão não estáticos, ou seja, não terá a palavra static atrás do tipo de dados como o exemplo abaixo.

---

### 1) O que é uma classe utilitária?

Uma **classe utilitária** é uma classe criada para **oferecer funções prontas** (métodos) que podem ser usadas em qualquer parte do sistema, sem depender de “estado” (atributos do objeto).

✅ Exemplos comuns de classes utilitárias:
- validações (CPF, e-mail, senha)
- conversões (String → número, km → milhas)
- formatações (datas, valores monetários)
- leitura de dados (ex: `Leitura.lerInt()`, `Leitura.lerDouble()`)

---

### 2) Por que usar `static` em métodos utilitários?

Quando um método é **static**, ele pertence à **classe**, e não a um objeto específico.

Então você pode chamar assim:

    Validador.validarEmail("teste@email.com");
    Leitura.lerInt("Digite um número: ");

Sem precisar fazer:

    Validador v = new Validador();
    Leitura leitura = new Leitura();

✅ Isso faz sentido porque esses métodos normalmente não precisam guardar dados próprios do objeto.

---

### 3) Quando NÃO usar `static`?

Quando a classe representa algo “do mundo real” (um **modelo**), como:

- Carro
- Pessoa
- Usuario
- Produto

Essas classes normalmente têm **atributos diferentes para cada objeto**, então você quer:

- `pessoa1.nome` diferente de `pessoa2.nome`
- `carro1.cor` diferente de `carro2.cor`

Ou seja, você precisa de **instâncias**.

---

### 4) Exemplo rápido: utilitária (static) vs classe de objeto (não static)

#### ✅ Classe utilitária (sem atributos de instância)

    class Validador {
        static boolean validarEmail(String email) {
            return email.contains("@");
        }
    }

Uso:

    boolean ok = Validador.validarEmail("a@b.com");

#### ✅ Classe que representa objeto (com atributos por instância)

    class Pessoa {
        String nome;
        int idade;
    }

Uso:

    Pessoa p1 = new Pessoa();
    p1.nome = "João";

    Pessoa p2 = new Pessoa();
    p2.nome = "Maria";

Cada objeto tem seus próprios valores.

---

### 5) Regra prática (bem simples)

- Se a classe **não precisa guardar estado** (não precisa de atributos por objeto) → use **métodos static** (utilitária).
- Se a classe **representa uma entidade** com dados próprios por instância → use **atributos e métodos não static**.

---

<!-- nav_start -->
---
Anterior: [Classes utilitÃ¡rias versus mÃ©todos estÃ¡ticos](../docs/101_Classes_Utilitarias_vs_Static.md) | Próximo: [Classe para representar data e hora em Java](../docs/103_Data_e_Hora.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->


