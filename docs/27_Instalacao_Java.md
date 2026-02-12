# Instalação do Java

---

## Instalação do Java

https://www.youtube.com/watch?v=WNc-uDG88Qk

[![Assistir no YouTube](https://img.youtube.com/vi/WNc-uDG88Qk/hqdefault.jpg)](https://www.youtube.com/watch?v=WNc-uDG88Qk)

---

# Complemento da Lição

## 1) Resultado esperado (o que tem que funcionar no final)
Ao terminar a instalação, você deve conseguir abrir o terminal (Prompt/PowerShell) e executar:

    java -version
    javac -version

Se ambos devolverem versão, está ok:
- `java` = roda programas (JRE/runtime)
- `javac` = compila programas (JDK)

---

## 2) Checklist de validação (Windows)
- [ ] Instalei o **JDK** (não só JRE)
- [ ] Reiniciei o terminal após instalar
- [ ] `java -version` funciona
- [ ] `javac -version` funciona
- [ ] Se não funcionou, conferi variável **PATH** (apontando para `...\bin` do JDK)

---

## 3) Atividade rápida (para garantir que está 100%)
Crie um arquivo `Main.java` com este conteúdo e compile/execute:

    public class Main {
        public static void main(String[] args) {
            System.out.println("Java OK!");
        }
    }

Comandos:

    javac Main.java
    java Main

---

## 4) Pergunta única (para checar que fixou)
Qual comando você usa para confirmar no terminal que o Java está instalado e acessível?

---

<!-- nav_start -->
---
Anterior: [Lista de Exercí­cios 1](../docs/26_Lista_Exercicios_1.md) | Próximo: [JDK, JRE e JVM](../docs/28_JDK_JRE_JVM.md) | [Voltar ao Índice](../README.md)
<!-- nav_end -->

