# Engenharia de Prompts

## 1. Introdução

A engenharia de prompts foi utilizada neste projeto para orientar o NotebookLM na exploração das fontes selecionadas e na construção progressiva do conhecimento sobre **Linux e Administração de Sistemas**.

O processo começou com perguntas mais gerais e, conforme os resultados eram analisados, os prompts foram sendo aprimorados para obter respostas mais específicas, práticas e adequadas ao objetivo do estudo.

Além de buscar informações, os prompts também foram utilizados para identificar **limitações das fontes**, gerar exercícios, criar um glossário e transformar o conteúdo pesquisado em material reutilizável para estudos futuros.

---

## 2. Evolução dos Prompts

### Prompt 1 — Conceitos fundamentais

**Pergunta:**

> O que é Linux e quais são suas principais características?

**Objetivo:**

Obter uma visão inicial sobre Linux e identificar suas principais características.

**Resultado:**

O NotebookLM apresentou conceitos relacionados ao Linux, incluindo características como código aberto, multitarefa, multiusuário, portabilidade, estabilidade, segurança e arquitetura do kernel.

---

### Prompt 2 — Diferenciando conceitos

**Pergunta:**

> Explique a diferença entre Linux, kernel Linux e uma distribuição Linux.

**Objetivo:**

Evitar a utilização dos termos Linux, kernel e distribuição como se fossem sinônimos.

**Resultado:**

A resposta permitiu organizar os conceitos em três níveis:

* **Kernel Linux:** núcleo responsável pelo gerenciamento dos recursos do sistema;
* **GNU/Linux:** combinação do kernel Linux com ferramentas e componentes necessários para formar um sistema operacional completo;
* **Distribuição Linux:** conjunto de componentes, ferramentas, gerenciadores de pacotes e outros softwares organizados para oferecer um sistema utilizável.

---

### Prompt 3 — Organização do sistema de arquivos

**Pergunta:**

> Quais são os principais diretórios do sistema Linux e qual a função de cada um?

**Objetivo:**

Compreender como o sistema de arquivos Linux é organizado.

**Resultado:**

As fontes permitiram explorar diretórios como `/dev`, `/proc`, `/sys` e `/usr/share/doc`.

Durante a análise, foi identificado que as fontes não apresentavam informações suficientemente detalhadas sobre diversos diretórios tradicionalmente encontrados em sistemas Linux, como `/etc`, `/home`, `/var`, `/tmp`, `/boot`, `/mnt` e `/opt`.

**Aprendizado:**

Quando as fontes não possuem informações suficientes, é importante reconhecer essa limitação em vez de assumir que a resposta está completamente fundamentada nelas.

---

### Prompt 4 — Permissões de arquivos

**Pergunta:**

> Explique como funcionam permissões de arquivos no Linux.

**Objetivo:**

Entender o modelo básico de controle de acesso utilizado pelo Linux.

**Resultado:**

O NotebookLM explicou a relação entre usuários, grupos e permissões, além da utilização do comando `ls -l` para visualizar informações sobre arquivos.

**Limitação identificada:**

As fontes inicialmente não apresentavam detalhes suficientes sobre:

* permissões `r`, `w` e `x`;
* valores numéricos das permissões;
* representação octal;
* exemplos práticos utilizando `chmod`.

Essa limitação levou à criação de prompts mais específicos.

---

### Prompt 5 — Administração de permissões

**Pergunta:**

> Como um administrador de sistemas pode utilizar os comandos chmod, chown e sudo no gerenciamento de permissões?

**Objetivo:**

Relacionar os conceitos de permissões com tarefas práticas de administração.

**Resultado:**

O NotebookLM apresentou as funções gerais dos comandos:

* `chmod` — alteração de permissões;
* `chown` — alteração do proprietário e/ou grupo;
* `sudo` — execução de comandos com privilégios elevados;
* `chgrp` — alteração do grupo associado ao arquivo.

**Limitação identificada:**

As fontes não apresentavam exemplos práticos e detalhados de sintaxe para todos os comandos.

---

## 3. Refinamento dos Prompts

Após identificar as limitações das respostas anteriores, o prompt foi ampliado para especificar exatamente o nível de profundidade esperado.

### Prompt 6 — Explicação didática

**Prompt utilizado:**

> Explique as permissões de arquivos no Linux para uma pessoa que já possui conhecimentos básicos de informática. Apresente os conceitos de leitura, escrita e execução, explique os valores 4, 2 e 1 e mostre exemplos práticos utilizando chmod.

**Objetivo:**

Transformar uma explicação conceitual em um conteúdo mais didático e prático.

**Resultado:**

A resposta passou a abordar:

* usuário, grupo e outros;
* permissões de leitura, escrita e execução;
* valores `4`, `2` e `1`;
* combinações como `7`, `6`, `5` e `4`;
* utilização do `chmod`;
* exemplos práticos de permissões.

---

### Prompt 7 — Simulação de instrutor

**Prompt utilizado:**

> Atue como um instrutor de Linux. Explique permissões de arquivos de forma didática, utilizando exemplos práticos de um ambiente corporativo. Ao final, crie 5 perguntas para testar meu conhecimento e forneça o gabarito separado.

**Objetivo:**

Transformar o conteúdo em uma experiência de aprendizagem ativa.

**Resultado:**

O NotebookLM apresentou uma explicação contextualizada e criou cinco questões para testar o conhecimento, acompanhadas de um gabarito separado.

Esse prompt demonstrou que especificar **papel, público, contexto, formato e resultado esperado** pode produzir respostas mais adequadas ao objetivo de estudo.

---

## 4. Criação do Glossário

### Prompt 8 — Glossário

**Objetivo:**

Organizar os principais conceitos encontrados durante o estudo em um formato de consulta rápida.

O NotebookLM foi solicitado a elaborar um glossário com 20 conceitos relacionados ao tema.

Entre os conceitos apresentados estão:

* Kernel Linux;
* Projeto GNU;
* Distribuição Linux;
* Kernel Monolítico;
* LKMs;
* User Space;
* Kernel Space;
* System Call;
* Glibc;
* Inode;
* VFS;
* Processo;
* Scheduler;
* Memória Virtual;
* Gerenciador de Pacotes;
* GPL;
* Shell;
* GUI;
* eBPF;
* FHS.

---

## 5. Criação de Prompts Reutilizáveis

### Prompt 9 — Biblioteca de prompts

Após a exploração dos conteúdos, foi solicitado ao NotebookLM que organizasse prompts que pudessem ser reutilizados em estudos futuros.

Os prompts foram organizados nas seguintes categorias:

### Conceitos e arquitetura

* User Space, Kernel Space, System Calls e Glibc;
* Kernel monolítico modular e microkernel;
* eBPF.

### Comandos e linha de comando

* Permissões de arquivos;
* Organização do FHS;
* Análise de logs utilizando ferramentas como `grep`, `sed`, `awk`, `cut`, `sort` e `uniq`.

### Administração e serviços

* Processos e threads;
* Utilização de `ps`, `top`, `htop`, `kill` e `nice`;
* Memória, swap e OOM Killer;
* Gerenciadores de pacotes APT, DNF e Pacman.

### Segurança

* DAC e MAC;
* SELinux e AppArmor;
* `sudoers` e `visudo`;
* Checklist de hardening.

### Troubleshooting

* Diagnóstico de CPU, memória, disco e rede;
* Simulação interativa de problemas;
* Análise de logs com `journalctl`.

---

## 6. Cicatrizes do Processo

Durante a construção do caderno, algumas dificuldades foram identificadas e utilizadas como parte do aprendizado.

### Cicatriz 1 — Fontes insuficientes

**Problema:**

Algumas perguntas exigiam informações que não estavam suficientemente detalhadas nas fontes utilizadas.

**Exemplo:**

As fontes não apresentavam inicialmente uma explicação completa sobre `rwx`, valores octais e exemplos práticos de `chmod`.

**Solução:**

O prompt foi refinado para especificar exatamente quais conceitos deveriam ser explicados e qual nível de conhecimento o leitor possuía.

**Aprendizado:**

Um prompt mais específico ajuda a direcionar a resposta, mas também é importante reconhecer quando uma informação não está presente ou não é suficientemente sustentada pelas fontes.

---

### Cicatriz 2 — Respostas muito conceituais

**Problema:**

Perguntas mais gerais produziram respostas úteis para introdução, mas pouco práticas para quem deseja aplicar o conhecimento.

**Solução:**

Foram adicionados ao prompt:

* exemplos práticos;
* contexto corporativo;
* comandos;
* exercícios;
* gabarito.

**Aprendizado:**

Definir o formato e a aplicação desejada da resposta melhora a utilidade do conteúdo.

---

### Cicatriz 3 — Evolução da abordagem

**Problema:**

Perguntas isoladas geravam respostas individuais, mas não necessariamente formavam um material de estudo estruturado.

**Solução:**

A abordagem evoluiu para a criação de:

1. explicações conceituais;
2. exemplos práticos;
3. exercícios;
4. gabarito;
5. glossário;
6. biblioteca de prompts reutilizáveis.

**Aprendizado:**

O NotebookLM pode ser utilizado não apenas para responder perguntas, mas também para estruturar uma sequência de aprendizagem.

---

## 7. Boas Práticas Utilizadas

Durante o desenvolvimento do caderno, algumas práticas se mostraram importantes:

* Definir claramente o assunto da pergunta;
* Informar o nível de conhecimento do público;
* Especificar o formato esperado da resposta;
* Solicitar exemplos práticos quando necessário;
* Contextualizar os exemplos em situações reais;
* Pedir exercícios para verificar a compreensão;
* Separar perguntas e gabaritos;
* Refinar o prompt quando a resposta não atender ao objetivo;
* Observar as limitações das fontes;
* Utilizar as respostas anteriores para definir novas perguntas.

---

## 8. Conclusão

A utilização de diferentes estratégias de prompt permitiu transformar uma pesquisa inicial sobre Linux em um material de estudo mais estruturado.

O principal aprendizado foi perceber que **a qualidade do resultado não depende apenas da ferramenta ou das fontes utilizadas, mas também da forma como o objetivo é apresentado ao modelo**.

O processo de refinamento dos prompts possibilitou sair de perguntas gerais e chegar a respostas mais didáticas, práticas e orientadas à aplicação, além de gerar exercícios, glossário e prompts reutilizáveis para estudos futuros.
