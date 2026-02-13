# Vídeo: Formatando casas decimais

---

## Vídeo: Formatando casas decimais

https://www.youtube.com/watch?v=QrEYtDnvDoY

[![Assistir no YouTube](https://img.youtube.com/vi/QrEYtDnvDoY/hqdefault.jpg)](https://www.youtube.com/watch?v=QrEYtDnvDoY)

---

# Complemento da Lição

## 1) O objetivo deste vídeo (o que você deve aprender)
Ao final, você deve conseguir:
- imprimir números com **2 casas decimais** (ex.: `19.90`)
- entender por que `double/float` podem imprimir com muitas casas
- controlar o formato com `printf`

---

## 2) O essencial (sem enrolar)
O padrão mais usado para **2 casas decimais** no `printf` é:

    %.2f

Exemplo:

    System.out.printf("Total: %.2f\n", total);

---

## 3) Checklist de prática (faça junto com o vídeo)
- [ ] Criei uma variável `double` (ex.: `total`)
- [ ] Imprimi sem formatação (pra ver o “problema”)
- [ ] Imprimi com `%.2f`
- [ ] Testei com valores como `19.9`, `19.99`, `19.999`
- [ ] Entendi que a quebra de linha vem do `\n`

---

## 4) Exercício rápido (fixação)
Crie 3 variáveis:
- `double preco = 12.5;`
- `int qtd = 3;`
- `double total = preco * qtd;`

Imprima no console:
- `Preço: 12.50`
- `Qtd: 3`
- `Total: 37.50`

---

## 5) Pergunta única (para checar que fixou)
Qual é o formatador do `printf` para mostrar **2 casas decimais**?

---

<!-- nav_start -->
---
Anterior: [31 Comando printf](../docs/31_Comando_printf.md) | Proximo: [33 Uso Try Catch](../docs/33_Uso_Try_Catch.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
