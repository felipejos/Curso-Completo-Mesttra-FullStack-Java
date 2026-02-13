# JDK, JRE e JVM

---

## JDK, JRE e JVM

Leia o artigo para para entender as diferenças entre **JDK**, **JRE** e **JVM**.

https://www.alura.com.br/artigos/jvm-conhecendo-processo-execucao-de-codigo

---

# Complemento da Lição

## 1) A ideia em 1 minuto (bem simples)

Pense assim:

- **JVM** = o “motor” que **executa** seu programa Java.
- **JRE** = o “kit para rodar” Java (inclui a JVM + bibliotecas necessárias).
- **JDK** = o “kit para programar” em Java (inclui o JRE + ferramentas como o **javac**).

---

## 2) Exemplo do mundo real (analogia rápida)

- **JVM** → o **motor** de um carro.
- **JRE** → o **carro pronto para dirigir** (motor + peças necessárias).
- **JDK** → a **oficina completa** (carro + ferramentas para construir/ajustar).

---

## 3) Fluxo do que acontece quando você cria um programa Java

1) Você escreve o código em um arquivo **.java**  
2) O **javac** (do JDK) compila e gera um arquivo **.class**  
3) O arquivo **.class** é executado pela **JVM**  

---

## 4) Como conferir no seu computador (check rápido)

No terminal, estes comandos ajudam a validar:

    java -version
    javac -version

- Se `java -version` funciona → você tem ambiente para **rodar** Java.
- Se `javac -version` funciona → você tem ambiente para **programar/compilar** Java (JDK).

---

## 5) Exercícios rápidos (fixação)

1) Marque mentalmente:
- Para **rodar** um programa Java na máquina de alguém: precisa de **JRE** ou **JDK**?
- Para **criar/compilar** um programa Java no seu PC: precisa de **JRE** ou **JDK**?

2) Complete o caminho:
- `.java` → (_____) → `.class` → (_____) → execução

---

## 6) Pergunta única (para checar que fixou)

O `javac` faz parte do JRE ou do JDK?

---

<!-- nav_start -->
---
Anterior: [27 Instalacao Java](../docs/27_Instalacao_Java.md) | Proximo: [29 Instalacao VSCode Plugins](../docs/29_Instalacao_VSCode_Plugins.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
