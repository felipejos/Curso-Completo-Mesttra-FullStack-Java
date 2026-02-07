Exemplo de Classe Utilitária: Validador
Exemplo de classe de validação: 

public class Validador {

    // Valida CPF
    public static boolean validarCPF(String cpf) {
        if (cpf == null) return false;

        // Remove caracteres que não são números
        StringBuilder sb = new StringBuilder();
        for (char c : cpf.toCharArray()) {
            if (c >= '0' && c <= '9') {
                sb.append(c);
            }
        }
        cpf = sb.toString();

        if (cpf.length() != 11 || allDigitsSame(cpf)) {
            return false;
        }

        // Calcula primeiro dígito verificador
        int soma1 = 0;
        for (int i = 0; i < 9; i++) {
            soma1 += (cpf.charAt(i) - '0') * (10 - i);
        }
        int digito1 = (soma1 * 10) % 11;
        if (digito1 == 10) digito1 = 0;

        // Calcula segundo dígito verificador
        int soma2 = 0;
        for (int i = 0; i < 10; i++) {
            soma2 += (cpf.charAt(i) - '0') * (11 - i);
        }
        int digito2 = (soma2 * 10) % 11;
        if (digito2 == 10) digito2 = 0;

        return digito1 == (cpf.charAt(9) - '0') &&
               digito2 == (cpf.charAt(10) - '0');
    }

    // Valida CNPJ
    public static boolean validarCNPJ(String cnpj) {
        if (cnpj == null) return false;

        // Remove caracteres que não são números
        StringBuilder sb = new StringBuilder();
        for (char c : cnpj.toCharArray()) {
            if (c >= '0' && c <= '9') {
                sb.append(c);
            }
        }
        cnpj = sb.toString();

        if (cnpj.length() != 14 || allDigitsSame(cnpj)) {
            return false;
        }

        int[] pesos1 = {5, 4, 3, 2, 9, 8, 7, 6, 5, 4, 3, 2};
        int[] pesos2 = {6, 5, 4, 3, 2, 9, 8, 7, 6, 5, 4, 3, 2};

        int soma1 = 0;
        for (int i = 0; i < 12; i++) {
            soma1 += (cnpj.charAt(i) - '0') * pesos1[i];
        }
        int digito1 = soma1 % 11;
        digito1 = (digito1 < 2) ? 0 : 11 - digito1;

        int soma2 = 0;
        for (int i = 0; i < 13; i++) {
            soma2 += (cnpj.charAt(i) - '0') * pesos2[i];
        }
        int digito2 = soma2 % 11;
        digito2 = (digito2 < 2) ? 0 : 11 - digito2;

        return digito1 == (cnpj.charAt(12) - '0') &&
               digito2 == (cnpj.charAt(13) - '0');
    }

    // Valida e-mail
    public static boolean validarEmail(String email) {
        if (email == null) return false;

        int atIndex = email.indexOf('@');
        if (atIndex <= 0 || atIndex == email.length() - 1) {
            return false; // precisa ter '@' no meio
        }

        String local = email.substring(0, atIndex);
        String dominio = email.substring(atIndex + 1);

        if (local.isEmpty() || dominio.isEmpty()) {
            return false;
        }

        // Verifica se domínio contém pelo menos um ponto
        if (!dominio.contains(".")) {
            return false;
        }

        // Verifica caracteres válidos (simplificado: letras, números, '.', '-', '_')
        for (char c : email.toCharArray()) {
            if (!isValidEmailChar(c)) {
                return false;
            }
        }

        return true;
    }

    // Função auxiliar: todos os dígitos iguais
    private static boolean allDigitsSame(String s) {
        char first = s.charAt(0);
        for (char c : s.toCharArray()) {
            if (c != first) return false;
        }
        return true;
    }

    // Função auxiliar: caracteres válidos para email
    private static boolean isValidEmailChar(char c) {
        return (c >= 'a' && c <= 'z') ||
               (c >= 'A' && c <= 'Z') ||
               (c >= '0' && c <= '9') ||
               c == '.' || c == '-' || c == '_' || c == '@';
    }

    public static boolean validarSenha(
            String senha,
            int minMinusculas,
            int minMaiusculas,
            int minDigitos,
            int minEspeciais
    ) {
        if (senha == null) {
            throw new IllegalArgumentException("Senha não pode ser nula.");
        }

        int minusculas = 0;
        int maiusculas = 0;
        int digitos = 0;
        int especiais = 0;

        for (char c : senha.toCharArray()) {
            if (c >= 'a' && c <= 'z') {
                minusculas++;
            } else if (c >= 'A' && c <= 'Z') {
                maiusculas++;
            } else if (c >= '0' && c <= '9') {
                digitos++;
            } else {
                especiais++;
            }
        }

        if (minusculas < minMinusculas) {
            throw new IllegalArgumentException("Senha deve conter pelo menos " + minMinusculas + " letra(s) minúscula(s).");
        }

        if (maiusculas < minMaiusculas) {
            throw new IllegalArgumentException("Senha deve conter pelo menos " + minMaiusculas + " letra(s) maiúscula(s).");
        }

        if (digitos < minDigitos) {
            throw new IllegalArgumentException("Senha deve conter pelo menos " + minDigitos + " dígito(s).");
        }

        if (especiais < minEspeciais) {
            throw new IllegalArgumentException("Senha deve conter pelo menos " + minEspeciais + " caractere(s) especial(is).");
        }

        // Se passou em todos os critérios, senha é válida
        return true;
    }
}

Exemplo de uso dos métodos.

public class Main {
    public static void main(String[] args) {
        System.out.println(Validador.validarCPF("123.456.789-09"));      // false
        System.out.println(Validador.validarCNPJ("12.345.678/0001-95"));  // false
        System.out.println(Validador.validarEmail("teste@dominio.com"));   // true
        System.out.println(Validador.validarEmail("teste@dominio"));       // false

        try {
            System.out.println(ValidadorSenha.validarSenha("s3gr3d0", 1, 1, 1, 0); // Exception
            System.out.println(ValidadorSenha.validarSenha("S3gr3d0", 1, 1, 1, 0); // true
        } catch (ValidacaoSenhaException e) {
            System.out.println("Senha inválida: " + e.getMessage());
        }

    }
}

---

## Opção melhorada

# Classe utilitária `Validador` (boas práticas + exemplo de uso correto)

## 1) O que caracteriza uma classe utilitária
- **Não precisa de instância** (você não faz `new Validador()`).
- Expõe **métodos `static`** (ex.: `Validador.validarCPF(...)`).
- Normalmente tem **construtor `private`** para impedir instanciamento por acidente.

---

## 2) Ajustes de organização (sem mudar sua lógica)
- **Construtor privado**: bloqueia `new Validador()`.
- **Método de “limpar números”** reutilizado em CPF e CNPJ.
- **Validação de parâmetros** (evitar mínimos negativos na senha).
- **Exemplo de uso corrigido** (na sua amostra, aparecem `ValidadorSenha` e `ValidacaoSenhaException`, mas o código lança `IllegalArgumentException`).

### Versão organizada (mantendo a ideia original)

    public final class Validador {

        private Validador() { }

        private static String apenasDigitos(String s) {
            if (s == null) return null;
            StringBuilder sb = new StringBuilder();
            for (char c : s.toCharArray()) {
                if (c >= '0' && c <= '9') sb.append(c);
            }
            return sb.toString();
        }

        // Função auxiliar: todos os dígitos iguais
        private static boolean allDigitsSame(String s) {
            char first = s.charAt(0);
            for (char c : s.toCharArray()) {
                if (c != first) return false;
            }
            return true;
        }

        // Valida CPF
        public static boolean validarCPF(String cpf) {
            cpf = apenasDigitos(cpf);
            if (cpf == null) return false;

            if (cpf.length() != 11 || allDigitsSame(cpf)) return false;

            int soma1 = 0;
            for (int i = 0; i < 9; i++) soma1 += (cpf.charAt(i) - '0') * (10 - i);
            int digito1 = (soma1 * 10) % 11;
            if (digito1 == 10) digito1 = 0;

            int soma2 = 0;
            for (int i = 0; i < 10; i++) soma2 += (cpf.charAt(i) - '0') * (11 - i);
            int digito2 = (soma2 * 10) % 11;
            if (digito2 == 10) digito2 = 0;

            return digito1 == (cpf.charAt(9) - '0') &&
                   digito2 == (cpf.charAt(10) - '0');
        }

        // Valida CNPJ
        public static boolean validarCNPJ(String cnpj) {
            cnpj = apenasDigitos(cnpj);
            if (cnpj == null) return false;

            if (cnpj.length() != 14 || allDigitsSame(cnpj)) return false;

            int[] pesos1 = {5, 4, 3, 2, 9, 8, 7, 6, 5, 4, 3, 2};
            int[] pesos2 = {6, 5, 4, 3, 2, 9, 8, 7, 6, 5, 4, 3, 2};

            int soma1 = 0;
            for (int i = 0; i < 12; i++) soma1 += (cnpj.charAt(i) - '0') * pesos1[i];
            int digito1 = soma1 % 11;
            digito1 = (digito1 < 2) ? 0 : 11 - digito1;

            int soma2 = 0;
            for (int i = 0; i < 13; i++) soma2 += (cnpj.charAt(i) - '0') * pesos2[i];
            int digito2 = soma2 % 11;
            digito2 = (digito2 < 2) ? 0 : 11 - digito2;

            return digito1 == (cnpj.charAt(12) - '0') &&
                   digito2 == (cnpj.charAt(13) - '0');
        }

        // Função auxiliar: caracteres válidos para email
        private static boolean isValidEmailChar(char c) {
            return (c >= 'a' && c <= 'z') ||
                   (c >= 'A' && c <= 'Z') ||
                   (c >= '0' && c <= '9') ||
                   c == '.' || c == '-' || c == '_' || c == '@';
        }

        // Valida e-mail (simples)
        public static boolean validarEmail(String email) {
            if (email == null) return false;

            int atIndex = email.indexOf('@');
            if (atIndex <= 0 || atIndex == email.length() - 1) return false;

            String local = email.substring(0, atIndex);
            String dominio = email.substring(atIndex + 1);
            if (local.isEmpty() || dominio.isEmpty()) return false;

            if (!dominio.contains(".")) return false;

            for (char c : email.toCharArray()) {
                if (!isValidEmailChar(c)) return false;
            }
            return true;
        }

        public static boolean validarSenha(
                String senha,
                int minMinusculas,
                int minMaiusculas,
                int minDigitos,
                int minEspeciais
        ) {
            if (senha == null) throw new IllegalArgumentException("Senha não pode ser nula.");
            if (minMinusculas < 0 || minMaiusculas < 0 || minDigitos < 0 || minEspeciais < 0) {
                throw new IllegalArgumentException("Os mínimos não podem ser negativos.");
            }

            int minusculas = 0, maiusculas = 0, digitos = 0, especiais = 0;

            for (char c : senha.toCharArray()) {
                if (c >= 'a' && c <= 'z') minusculas++;
                else if (c >= 'A' && c <= 'Z') maiusculas++;
                else if (c >= '0' && c <= '9') digitos++;
                else especiais++;
            }

            if (minusculas < minMinusculas)
                throw new IllegalArgumentException("Senha deve conter pelo menos " + minMinusculas + " letra(s) minúscula(s).");

            if (maiusculas < minMaiusculas)
                throw new IllegalArgumentException("Senha deve conter pelo menos " + minMaiusculas + " letra(s) maiúscula(s).");

            if (digitos < minDigitos)
                throw new IllegalArgumentException("Senha deve conter pelo menos " + minDigitos + " dígito(s).");

            if (especiais < minEspeciais)
                throw new IllegalArgumentException("Senha deve conter pelo menos " + minEspeciais + " caractere(s) especial(is).");

            return true;
        }
    }

---

## 3) Exemplo de uso (corrigido e compilável)

    public class Main {
        public static void main(String[] args) {

            System.out.println(Validador.validarCPF("123.456.789-09"));       // false
            System.out.println(Validador.validarCNPJ("12.345.678/0001-95"));  // false
            System.out.println(Validador.validarEmail("teste@dominio.com"));  // true
            System.out.println(Validador.validarEmail("teste@dominio"));      // false

            try {
                // Falha: não tem maiúscula (minMaiusculas = 1)
                System.out.println(Validador.validarSenha("s3gr3d0", 1, 1, 1, 0));
            } catch (IllegalArgumentException e) {
                System.out.println("Senha inválida: " + e.getMessage());
            }

            try {
                // OK: tem minúscula, maiúscula e dígito
                System.out.println(Validador.validarSenha("S3gr3d0", 1, 1, 1, 0));
            } catch (IllegalArgumentException e) {
                System.out.println("Senha inválida: " + e.getMessage());
            }
        }
    }

---

## Exercícios

1) Implemente `validarTelefone(String telefone)` aceitando:
   - 10 ou 11 dígitos (com DDD),
   - ignorando `() - espaço`.
2) Crie `validarCEP(String cep)` aceitando 8 dígitos (ex.: `01311000`) e também formato `01311-000`.
3) Ajuste `validarEmail` para rejeitar:
   - dois `@`,
   - domínio começando/terminando com `.`,
   - espaços em branco.
4) Faça um `App` que:
   - leia CPF do usuário,
   - valide,
   - repita até ser válido.
<!-- nav_start -->
---
Anterior: [Resumo de Classes e Objetos](../docs/155_Resumo_Classes_Objetos.md) | Próximo: [Conceito de ENUM](../docs/157_ENUM.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

