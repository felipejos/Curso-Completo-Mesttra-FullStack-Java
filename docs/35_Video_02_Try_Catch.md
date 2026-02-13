# Vídeo 02: Try Catch

---

## Vídeo 02: Try Catch

https://www.youtube.com/watch?v=i9r3Sm23RLM

[![Assistir no YouTube](https://img.youtube.com/vi/i9r3Sm23RLM/hqdefault.jpg)](https://www.youtube.com/watch?v=i9r3Sm23RLM)

---

# Complemento da Lição

## 1) Resultado esperado (ao terminar este vídeo)
Você deve conseguir:
- tratar erro **sem travar** o programa
- entender que o `catch` pode capturar **tipos diferentes** de exceção
- exibir mensagens melhores para o usuário (sem “stack trace” no console)

---

## 2) Um detalhe importante: exceção “genérica” vs exceção “específica”
- `catch (Exception e)` → pega quase tudo (bom no começo, mas menos preciso)
- `catch (ArithmeticException e)` → pega **um erro específico** (mais correto)

Exemplo (mais específico):

    try {
        int r = 10 / 0;
    } catch (ArithmeticException e) {
        System.out.println("Erro: divisão por zero.");
    }

---

## 3) Padrão essencial em console: recuperar de erro de digitação
Quando o usuário digita algo errado (ex.: “abc” em vez de número), seu objetivo é:
- avisar o usuário
- **limpar o buffer**
- permitir tentar novamente

Exemplo de ideia:

    try {
        System.out.print("Digite um número: ");
        int n = teclado.nextInt();
        teclado.nextLine(); // buffer
    } catch (Exception e) {
        System.out.println("Entrada inválida.");
        teclado.nextLine(); // limpa o que sobrou
    }

---

## 4) Checklist enquanto assiste (pra não pular etapa)
- [ ] Rodei o exemplo funcionando (sem erro)
- [ ] Forcei um erro e vi o `catch` rodar
- [ ] Testei com erro de digitação (texto em vez de número)
- [ ] Confirmei que o programa continuou após o tratamento
- [ ] Entendi onde entra o `teclado.nextLine()` para limpar buffer

---

## 5) Exercício rápido (fixação)
Crie um loop que:
1) pede um número inteiro
2) se o usuário errar, mostra mensagem e pede de novo
3) só sai quando o usuário digitar um número válido

---

## 6) Pergunta única (pra fixar)
Qual é a vantagem de usar `catch` com uma exceção **específica** (ex.: `ArithmeticException`) em vez de `Exception`?

---

<!-- nav_start -->
---
Anterior: [VÃ­deo 01: Try Catch](../docs/34_Video_01_Try_Catch.md) | Próximo: [CompilaÃ§Ã£o, InterpretaÃ§Ã£o e HÃ­brido](../docs/36_Compilacao_Interpretacao_Hibrido.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

