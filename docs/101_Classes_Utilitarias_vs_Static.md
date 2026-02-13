# Classes utilitárias versus métodos estáticos

---

Classes utilitárias versus métodos estáticos


Quando precisamos criar classes que não possuem atributos de instância, ou seja, do objeto, como classes utilitárias de validação, é comum implementar seus métodos como estáticos. Dessa forma, para utilizar esses métodos em outras classes, não é necessário instanciar a classe com new NomeDaClasse(),  bastando chamá-los diretamente, por exemplo: Validador.validarEmail(...).



No próximo artigo estamos disponibilizando a classe Leitura que terá como objetivo implementar a leitura dos tipos de dados. Nesta classe você verá que todos os métodos são estáticos. Isto significa que para utilizar esta classe não é necessário realizar criação do objeto com: Leitura leitura = new Leitura(). 



No entanto, não são todas as classes que possuem está caracterísitca. Classes que irão representar atributos de objeto como classes: Carro, Pessoa, Usuario, precisam ser classes que possuem atributos que não sejam estáticos. Pois desejamos que cada objeto (instância da classe), mantenha os seus atributos isolados uns dos outros. Para estes casos, os atributos (variáveis) serão não estáticos, ou seja, não terá a palavra static atrás do tipo de dados como o exemplo abaixo.

---

Complementos (sem substituir o texto acima)

- **Classe utilitária**: normalmente **não guarda estado** (não tem “dados do objeto”). Ela só oferece **ferramentas** (métodos) para outras partes do sistema.
- **Método `static`**: pertence à **classe**, não ao objeto. Por isso você chama assim:
  
    Validador.validarEmail("teste@email.com");

- **Por que não instanciar?**  
  Se a classe não tem atributos que variam por objeto, criar `new` vira só “cerimônia” e não traz benefício.

- **Exemplo rápido de classe utilitária (com construtor privado)**  
  (boa prática para evitar `new` sem necessidade)

    class Validador {
        private Validador() {}

        static boolean validarEmail(String email) {
            return email != null && email.contains("@");
        }
    }

- **Quando NÃO usar `static`**  
  Quando a classe representa algo do mundo real e cada objeto precisa ter **seus próprios valores**, como:
  - `Pessoa` (nome, idade)
  - `Carro` (marca, cor, ano)
  - `Usuario` (login, senha)

- **Resumo prático**
  - `static` → “ferramenta da classe” (utilitários, helpers, validações, conversões)
  - “sem static” → “características do objeto” (cada instância tem seu próprio estado)

---

<!-- nav_start -->
---
Anterior: [100 Classe e Objeto](../docs/100_Classe_e_Objeto.md) | Proximo: [102 Classe Utilitaria Leitura](../docs/102_Classe_Utilitaria_Leitura.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
