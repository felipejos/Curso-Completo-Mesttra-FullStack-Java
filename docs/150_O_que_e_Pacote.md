O que é um pacote em Java
No Java, um pacote (ou package em inglês) é uma maneira de organizar e agrupar classes e interfaces de forma lógica e estruturada. Pacotes ajudam a modularizar o código, facilitando a manutenção e evitando conflitos de nomes entre classes diferentes. Vamos detalhar os principais conceitos relacionados a pacotesem  Java:

1. Organização do Código
Pacotes são usados para agrupar classes que têm funcionalidades semelhantes ou que fazem parte de um mesmo domínio da aplicação.
Por exemplo, você pode ter um pacote para as classes de acesso a banco de dados (com.minhaempresa.dao), outro para classes de interface gráfica (com.minhaempresa.ui), e assim por diante.
2. Sintaxe para Declarar um Pacote
No início de cada arquivo de código-fonte em Java, você pode declarar a qual pacote a classe pertence utilizando a palavra-chave package. Exemplo:
package com.minhaempresa.modelo;

public class Produto {
    // código da classe
}
O exemplo acima define que a classe Produto faz parte do pacote com.minhaempresa.modelo.
3. Estrutura de Diretórios
A estrutura de pacotes no código reflete a estrutura de diretórios no sistema de arquivos.
Se você tiver o pacote com.minhaempresa.modelo, isso significa que dentro do diretório do seu projeto, você deve ter uma estrutura de pastas como:
/com/minhaempresa/modelo/Produto.java
4. Pacotes Importados
Para usar classes de outros pacotes, é necessário importá-las utilizando a palavra-chave import. Exemplo:
import com.minhaempresa.modelo.Produto;

public class Main {
    public static void main(String[] args) {
        Produto p = new Produto();
    }
}

Você também pode importar todas as classes de um pacote com o *:
import com.minhaempresa.modelo.*;

---

## Opção melhorada

# Pacotes (packages) em Java

Um **pacote** é uma forma de **organizar classes e interfaces** em “pastas lógicas”, como se fosse um **endereço** do código. Isso deixa o projeto mais limpo, facilita manutenção e evita conflitos de nomes (ex.: duas classes chamadas `Produto` em partes diferentes do sistema).

---

## 1) Para que servem pacotes?

- **Organização**: separa por contexto (ex.: `dao`, `service`, `controller`, `ui`).
- **Evita conflito de nomes**: você pode ter `com.loja.Produto` e `com.estoque.Produto` sem colisão.
- **Modularização e manutenção**: fica mais fácil encontrar e evoluir o código.
- **Controle de acesso**: pacotes também influenciam visibilidade (ex.: acesso *package-private*).

Exemplos de pacotes comuns:
- `com.minhaempresa.dao` (acesso a dados)
- `com.minhaempresa.service` (regras de negócio)
- `com.minhaempresa.ui` (interface)
- `com.minhaempresa.model` / `modelo` (entidades / classes de domínio)

---

## 2) Como declarar um pacote (package)

A declaração de pacote **deve ser a primeira linha** do arquivo (antes de `import` e da classe).

Exemplo:

    package com.minhaempresa.modelo;

    public class Produto {
        // código da classe
    }

---

## 3) Pacote x pastas do projeto (estrutura de diretórios)

O nome do pacote **reflete a estrutura de pastas**.

Se a classe está em:

    package com.minhaempresa.modelo;

Então o arquivo deve ficar em algo como:

    /src
      /com
        /minhaempresa
          /modelo
            Produto.java

---

## 4) Como importar classes de outros pacotes (import)

Quando você usa uma classe que está em outro pacote, você **importa**:

    import com.minhaempresa.modelo.Produto;

    public class Main {
        public static void main(String[] args) {
            Produto p = new Produto();
        }
    }

Também existe o “import com *”:

    import com.minhaempresa.modelo.*;

Mas, em projetos reais, costuma-se preferir **imports explícitos** (classe por classe) para manter o código mais claro.

---

## 5) Boas práticas rápidas

- **Nomeie pacotes em minúsculo**: `com.minhaempresa.app`.
- **Use um “prefixo” único** (geralmente o domínio invertido): `br.com.suaempresa...` ou `com.suaempresa...`.
- **Evite o “default package”** (classe sem `package;`) em projetos maiores — bagunça organização e atrapalha builds.
- **Mantenha pacotes por responsabilidade**:
  - `model` / `entity`
  - `repository` / `dao`
  - `service`
  - `controller`
  - `view` / `ui`

---

## Exercícios (para fixar)

1) Crie 3 pacotes e distribua classes:
- `com.seuprojeto.model` → `Aluno`, `Curso`
- `com.seuprojeto.service` → `AlunoService`
- `com.seuprojeto.app` → `Main`

2) Faça o `Main` instanciar um `Aluno` e chamar um método do `AlunoService`.

3) Crie duas classes com o mesmo nome `Produto`, uma em:
- `com.loja.produtos.Produto`
- `com.estoque.produtos.Produto`
E, no `Main`, use as duas (importando uma e referenciando a outra pelo nome completo do pacote).
<!-- nav_start -->
---
Anterior: [Bibliotecas de Terceiros no Java](../docs/149_Bibliotecas_Terceiros.md) | Próximo: [Criando o seu prÃ³prio pacote](../docs/151_Criando_Pacote.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

