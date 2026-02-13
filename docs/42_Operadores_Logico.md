# 🧠 Operadores Lógico

## 🎥 Vídeo (YouTube)

Caso a resolução do vídeo esteja baixa, aumente a resolução do vídeo na barra do YouTube.

https://www.youtube.com/watch?v=SZ1TVuaVPkI

[![Assistir no YouTube](https://img.youtube.com/vi/SZ1TVuaVPkI/hqdefault.jpg)](https://www.youtube.com/watch?v=SZ1TVuaVPkI)

---

# Complemento da Lição

## 1) O que são operadores lógicos?
Operadores lógicos servem para **combinar comparações** e tomar decisões do tipo:

- “isso **E** aquilo”
- “isso **OU** aquilo”
- “**NÃO** isso”

Eles trabalham com valores **booleanos**: `true` e `false`.

---

## 2) Os 3 operadores lógicos mais usados em Java

### ✅ AND (E) — `&&`
Só dá `true` se **as duas partes** forem `true`.

- `true && true`  → `true`
- `true && false` → `false`
- `false && true` → `false`
- `false && false`→ `false`

Exemplo (idade e documento):
    boolean podeEntrar = (idade >= 18) && (temDocumento == true);

---

### ✅ OR (OU) — `||`
Dá `true` se **pelo menos uma parte** for `true`.

- `true || true`  → `true`
- `true || false` → `true`
- `false || true` → `true`
- `false || false`→ `false`

Exemplo (cupom ou assinatura):
    boolean temDesconto = (temCupom == true) || (ehAssinante == true);

---

### ✅ NOT (NÃO) — `!`
Inverte o valor booleano.

- `!true`  → `false`
- `!false` → `true`

Exemplo:
    boolean bloqueado = false;
    boolean podeAcessar = !bloqueado; // true

---

## 3) “Curto-circuito” (muito importante)
Em Java:

- No `&&`: se a **primeira parte** já for `false`, o Java **nem avalia** a segunda parte.
- No `||`: se a **primeira parte** já for `true`, o Java **nem avalia** a segunda parte.

Exemplo (evita erro):
    if (usuario != null && usuario.isAtivo()) {
        System.out.println("Usuário válido e ativo");
    }

Se `usuario` for `null`, a segunda parte (`usuario.isAtivo()`) nem roda, evitando `NullPointerException`.

---

## 4) Exemplo completo com `if`
    int idade = 20;
    boolean temIngresso = true;
    boolean estaComDocumento = false;

    if (idade >= 18 && temIngresso) {
        System.out.println("Pode entrar");
    } else {
        System.out.println("Não pode entrar");
    }

    if (estaComDocumento || idade >= 18) {
        System.out.println("Passou na checagem de documento OU idade");
    }

---

## 5) Exercícios rápidos (fixação)

### Exercício 1
Crie variáveis:
- `int idade`
- `boolean temDocumento`
Imprima no console o resultado de:
- `(idade >= 18) && temDocumento`

### Exercício 2
Crie variáveis:

<!-- nav_start -->
---
Anterior: [Entendendo os Operadores de ComparaÃ§Ã£o](../docs/41_Entendendo_Operadores_Comparacao.md) | Próximo: [Operadores LÃ³gicos](../docs/43_Operadores_Logicos_2.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

