Instalação do MySQL Server


Vídeo:

https://youtu.be/BqIQKlkmJVc



Procedimento de Instalação em PDF:

https://drive.google.com/file/d/1NSbUe6CiD2KgFs3W-5GDGM3AX346s_jX/view?usp=drive_link

---

## Opção melhorada

# Instalação do MySQL Server (guia prático)

> **Objetivo:** instalar o **MySQL Server** (e, se necessário, o **MySQL Workbench**) e sair com tudo funcionando: serviço ativo + conexão testada.

---

## Materiais do conteúdo
- 🎥 **Vídeo**: use como referência para acompanhar o passo a passo visual (link acima).
- 📄 **PDF**: siga como “roteiro oficial” do procedimento (link acima).

> Dica: se o vídeo e o PDF divergirem em algum detalhe, priorize o **PDF** por ser o procedimento documentado.

---

## Antes de começar (checklist rápido)
- ✅ Você tem permissão de **administrador** no computador (instalação de serviços geralmente exige isso).
- ✅ Feche programas que possam usar recursos de rede/serviços (se estiver tudo ok, ignore).
- ✅ Defina uma **senha segura** para o usuário administrador (root) e guarde.

---

## Passo a passo da instalação (visão geral)
A forma mais comum no Windows é usar o **MySQL Installer**, que guia a instalação + configuração do servidor e dos componentes. :contentReference[oaicite:0]{index=0}

### 1) Baixar e executar o instalador
- Baixe o instalador recomendado (via vídeo/PDF).
- Execute o instalador com permissões adequadas.

### 2) Escolher o tipo de instalação
Em geral você vai ver opções de “tipo de setup” (ex.: instalar só servidor, instalar completo, instalar para desenvolvimento, etc.).  
Escolha o que fizer sentido para o seu cenário (o PDF normalmente diz qual usar). :contentReference[oaicite:1]{index=1}

### 3) Selecionar componentes (se aparecer)
Normalmente, você vai instalar:
- **MySQL Server**
- (Opcional, mas recomendado para iniciantes) **MySQL Workbench** para gerenciar e testar conexões

> Observação útil: o Workbench é testado principalmente com **MySQL Server 8.0**; ele pode conectar em versões mais novas, mas alguns recursos podem variar conforme a versão do servidor. :contentReference[oaicite:2]{index=2}

### 4) Configurar o MySQL Server (parte mais importante)
Quando o instalador entrar na etapa de **configuração**, atenção nestes pontos (o PDF costuma orientar um a um): :contentReference[oaicite:3]{index=3}
- **Senha do root** (defina e anote)
- **Inicialização do serviço** (habilitar para iniciar com o sistema, se essa opção existir)
- **Aplicar configurações** e concluir

### 5) Finalizar e testar
Após concluir:
- Abra o **MySQL Workbench** (se instalou) e crie uma conexão local
- Teste conectando com o usuário e senha que você definiu

---

## Checklist de validação (pra saber se deu tudo certo)
- ✅ O servidor está rodando (o instalador normalmente confirma isso ao final) :contentReference[oaicite:4]{index=4}
- ✅ Você consegue abrir o Workbench e **conectar** no servidor
- ✅ Você consegue executar uma consulta simples (ex.: ver se a conexão responde)

Exemplo de teste no Workbench (conceito):
    - conectar
    - abrir uma aba de query
    - executar uma consulta simples de verificação

---

## Problemas comuns (e como destravar)
- **Erro ao digitar idade/peso/etc. (tipo texto em campo numérico):**  
  Isso acontece bastante em aplicações com `Scanner`. A solução padrão é **repetir a leitura até vir um valor válido**, tratando exceções e limpando buffer (exatamente o padrão “Do While + try/catch” que vocês já usaram nos exercícios).
- **Não consigo conectar no Workbench:**  
  Confirme se o servidor foi realmente instalado e configurado (etapa “Apply/Finish”) e tente recriar a conexão no Workbench.

---

## Mini-resumo (pra memorizar)
- Instala → Configura (senha/serviço) → Testa (conexão)
- Se algo falhar: volte na parte de **configuração** e confirme os dados definidos. :contentReference[oaicite:5]{index=5}

<!-- nav_start -->
---
Anterior: [139 Introducao Banco de Dados](../docs/139_Introducao_Banco_de_Dados.md) | Proximo: [141 Resumo SELECT](../docs/141_Resumo_SELECT.md) | [Voltar ao Indice](../README.md)
<!-- nav_end -->
