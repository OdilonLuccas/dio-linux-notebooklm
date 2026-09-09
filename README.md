# 🐧 Miniguia de Estudos: Migração para Linux e Compatibilidade com Ferramentas Windows (WinBoat)

> Projeto desenvolvido para o desafio de projeto da [DIO](https://www.dio.me/) — *"Construindo Conhecimento com IA: Caderno Temático no NotebookLM"*.
> Caderno no NotebookLM: [acessar aqui](https://notebook.google.com/notebook/9d2cba93-4263-4f45-af9d-d16136c6a5d7)

---

## 📌 Sumário

- [Contexto e Objetivos](#-contexto-e-objetivos)
- [Curadoria de Fontes](#-curadoria-de-fontes)
- [Engenharia de Prompts e "Cicatrizes"](#-engenharia-de-prompts-e-cicatrizes)
- [Miniguia de Estudo (Entrega Final)](#-miniguia-de-estudo-entrega-final)
  - [Resumo Estruturado](#resumo-estruturado)
  - [Glossário](#glossário)
  - [Prompts Reutilizáveis](#prompts-reutilizáveis)

---

## 🎯 Contexto e Objetivos

Atuo na área de TI (NTIC) e recentemente busquei — e obtive junto à gerência de infraestrutura — autorização para migrar minha estação de trabalho para **Linux**, mantendo a exigência de continuar acessando as ferramentas Windows homologadas pela organização.

Durante essa pesquisa, conheci a ferramenta **WinBoat**, que promete rodar aplicativos Windows dentro do Linux com integração "seamless" (usando um Windows real em VM/contêiner, e não uma camada de compatibilidade como o Wine). Escolhi esse tema para o meu Caderno Temático porque:

1. É um problema real que estou resolvendo no meu dia a dia profissional;
2. Envolve conceitos técnicos (virtualização, contêineres, protocolos de remoto) que valem a pena consolidar por escrito;
3. O resultado pode virar conteúdo (ex: postagem no LinkedIn) e também uma base de conhecimento reaproveitável no trabalho.

### Objetivos de estudo

- Entender **como o WinBoat funciona por baixo dos panos** (arquitetura, requisitos, protocolo de exibição das janelas).
- Comparar o WinBoat com alternativas de compatibilidade Windows-em-Linux (Wine, Proton, VMs tradicionais).
- Mapear **riscos, limitações e requisitos de segurança** relevantes para um ambiente corporativo antes de recomendar o uso da ferramenta.
- Produzir um material de consulta rápida (glossário + prompts) para revisar o assunto no futuro sem precisar reler tudo do zero.

---

## 📚 Curadoria de Fontes

Fontes abertas selecionadas e carregadas no NotebookLM:

| # | Fonte | Tipo | Link |
|---|-------|------|------|
| 1 | Repositório oficial do WinBoat no GitHub (README, arquitetura, requisitos) | Texto/Markdown | https://github.com/winboat-org/winboat |
| 2 | Notas de release do WinBoat (mudanças recentes, correções, funcionalidades) | Texto/Markdown | https://github.com/winboat-org/winboat/releases |
| 3 | Resenha técnica: "WinBoat: rodando aplicativos Windows no Linux com integração seamless" | Artigo (TabNews) | https://www.tabnews.com.br/N0rd1k0Agent/winboat-rodando-aplicativos-windows-no-linux-com-integracao-seamless-resenha |
| 4 | Matéria sobre WinBoat como alternativa ao Wine/Proton | Artigo | https://ecosistemastartup.com/?p=46911 |
| 5 | *(opcional)* Artigo do Diolinux sobre WinBoat | Artigo | *adicionar o link exato da matéria que você leu no Diolinux* |

> ✏️ **Ajuste antes de publicar:** confirme que estes foram exatamente os arquivos/links que você inseriu no NotebookLM. Se usou outras fontes (ex: documentação do Docker, do KVM/QEMU, do FreeRDP), inclua-as aqui também — o ideal são de 3 a 5 fontes.

---

## 🧪 Engenharia de Prompts e "Cicatrizes"

Aqui documento as perguntas estratégicas feitas ao NotebookLM, as variações testadas e as dificuldades encontradas no caminho.

### Prompt 1 — Entendimento geral
**Prompt usado:**
> "Resuma em até 5 tópicos como o WinBoat funciona tecnicamente, citando as fontes."

**Resposta obtida (resumo):** *descreva aqui, em 2-3 linhas, o que o NotebookLM respondeu.*

**Dificuldade encontrada:** *ex: a primeira resposta ficou genérica demais / faltou citar a fonte correta / precisei pedir mais detalhes técnicos.*

---

### Prompt 2 — Comparação
**Prompt usado:**
> "Compare o WinBoat com o Wine e com uma VM tradicional em termos de desempenho, compatibilidade e complexidade de instalação, em formato de tabela."

**Resposta obtida (resumo):** *descreva aqui.*

**Dificuldade encontrada:** *ex: o NotebookLM não tinha informação suficiente nas fontes sobre desempenho comparado, precisei reformular pedindo para ele apontar isso como limitação da fonte.*

---

### Prompt 3 — Aplicação prática/corporativa
**Prompt usado:**
> "Quais são os requisitos mínimos de hardware e software para instalar o WinBoat, e quais riscos de segurança um administrador de TI deveria considerar antes de adotá-lo em um ambiente corporativo?"

**Resposta obtida (resumo):** *descreva aqui.*

**Dificuldade encontrada / ajuste no prompt:** *ex: a resposta inicial não separou "requisitos" de "riscos" — pedi para reorganizar em duas listas separadas.*

### 🔧 Troubleshooting geral (lições aprendidas)

- *Ex: prompts muito abertos geram respostas genéricas — pedir formato específico (lista, tabela) melhora a objetividade.*
- *Ex: sempre pedir para a IA citar de qual fonte tirou cada informação, para poder validar.*
- *Ex: quando a resposta parecia "inventar" algo que não estava nas fontes, pedir explicitamente "responda apenas com base nas fontes carregadas" resolveu.*

> ✏️ **Ajuste antes de publicar:** substitua os trechos em itálico pelas respostas reais que você obteve no seu Caderno do NotebookLM — isso é o que mostra seu raciocínio para quem avaliar o projeto.

---

## 📖 Miniguia de Estudo (Entrega Final)

### Resumo Estruturado

**1. O que é o WinBoat**
O WinBoat é uma aplicação Electron que roda um Windows real como máquina virtual dentro de um contêiner Docker/Podman (com virtualização KVM), permitindo executar aplicativos Windows como janelas integradas ao ambiente Linux.

**2. Como funciona**
- O Windows guest roda dentro do contêiner;
- Um "guest server" faz a comunicação entre o host Linux e o Windows;
- A exibição das janelas usa FreeRDP/RemoteApp para trazer os aplicativos Windows para o desktop Linux de forma "nativa";
- O diretório home do Linux pode ser montado dentro do Windows, facilitando a troca de arquivos.

**3. Diferencial em relação ao Wine/Proton**
Por rodar um Windows real (e não uma camada de tradução de chamadas de sistema, como o Wine), o WinBoat tende a suportar aplicativos que o Wine não roda bem — ao custo de exigir mais recursos de hardware (RAM, CPU, espaço em disco) e virtualização habilitada.

**4. Requisitos práticos**
- ~4 GB de RAM e 2 threads de CPU;
- Espaço livre em disco (documentado em torno de 32 GB);
- Virtualização KVM habilitada na BIOS/UEFI;
- Docker (não Docker Desktop) instalado.

**5. Pontos de atenção**
- Ferramenta ainda em beta — é esperado encontrar bugs;
- Aplicações que dependem de aceleração de GPU intensiva ou anti-cheat em nível de kernel podem não funcionar bem;
- Em ambiente corporativo, vale avaliar políticas de segurança para VMs/contêineres com privilégios elevados antes de liberar o uso.

---

### Glossário

| Termo | Definição |
|---|---|
| **WinBoat** | Ferramenta open source que executa um Windows real em contêiner para rodar apps Windows integrados ao Linux. |
| **Wine** | Camada de compatibilidade que traduz chamadas de API do Windows para o Linux, sem precisar de uma licença/instalação completa do Windows. |
| **KVM (Kernel-based Virtual Machine)** | Tecnologia de virtualização do kernel Linux que permite rodar máquinas virtuais com desempenho próximo do nativo. |
| **Contêiner (Docker/Podman)** | Ambiente isolado e leve para empacotar e executar aplicações/sistemas, compartilhando o kernel do host. |
| **FreeRDP / RemoteApp** | Protocolo/implementação usada para exibir remotamente janelas de aplicativos Windows como se fossem nativas em outro sistema. |
| **Seamless integration** | Integração em que o aplicativo remoto (Windows) aparece como uma janela comum do sistema operacional host (Linux), sem "moldura" de uma VM completa. |
| **NotebookLM** | Ferramenta de IA do Google que permite fazer perguntas e gerar resumos a partir de um conjunto de fontes (documentos/links) carregadas pelo usuário. |

> ✏️ Adicione aqui outros termos que apareceram no seu Caderno e que você achou relevante guardar.

---

### Prompts Reutilizáveis

Prompts prontos para revisar este assunto (ou adaptar para outros temas técnicos) no futuro:

```
1. "Resuma em até 5 tópicos como [FERRAMENTA/TECNOLOGIA] funciona tecnicamente, citando as fontes."

2. "Compare [FERRAMENTA A] com [FERRAMENTA B] e [FERRAMENTA C] em uma tabela considerando: desempenho, compatibilidade, facilidade de instalação e casos de uso ideais."

3. "Liste os requisitos mínimos de hardware e software para usar [FERRAMENTA], e aponte riscos de segurança relevantes para um ambiente corporativo."

4. "Com base apenas nas fontes carregadas, crie um glossário com os 8 termos técnicos mais importantes sobre [TEMA], com definições em 1 frase cada."

5. "Aja como um revisor técnico cético: aponte quais afirmações nas fontes carregadas são opiniões, quais são fatos verificáveis e onde falta evidência."
```

---

## ✅ Como usar este repositório

1. Acesse o [Caderno no NotebookLM](https://notebook.google.com/notebook/9d2cba93-4263-4f45-af9d-d16136c6a5d7) para ver as fontes originais e o histórico de perguntas.
2. Use os **prompts reutilizáveis** acima para revisar o tema periodicamente.
3. Sinta-se à vontade para adaptar este miniguia para outros assuntos técnicos.

---

*Projeto entregue como parte do desafio de projeto da [Digital Innovation One (DIO)](https://www.dio.me/).*
