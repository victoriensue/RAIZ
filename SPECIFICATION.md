# RAIZ Protocol — Especificação Técnica

**Versão 1.0.0**
**Data: 17 de Janeiro de 2026**
**Status: Release Inicial**

---

## 1. Resumo

Este documento especifica o Protocolo RAIZ, um padrão aberto para preservar e transferir identidade cognitiva humana entre sistemas de inteligência artificial. RAIZ define estruturas de dados, protocolos de comunicação e requisitos de interoperabilidade para criar identidades digitais portáveis (e-DNA) que mantêm contexto e continuidade independentemente de qualquer plataforma de IA específica.

---

## 2. Introdução

### 2.1 Propósito

RAIZ permite que humanos mantenham contexto cognitivo persistente ao interagir com sistemas de IA. Diferente de recursos de memória específicos de plataforma, RAIZ cria uma identidade de propriedade do usuário, portável, que funciona em qualquer sistema de IA compatível.

### 2.2 Escopo

Esta especificação cobre:
- Requisitos de estrutura de dados
- Padrões de formato de arquivo
- Protocolo de comunicação
- Requisitos de interoperabilidade
- Diretrizes de implementação
- Princípios de operação

### 2.3 Terminologia

| Termo | Definição |
|-------|-----------|
| **e-DNA** | Electronic Digital Native Architecture — representação estruturada de padrões cognitivos humanos |
| **Repositório RAIZ** | Sistema de arquivos local contendo a estrutura de três camadas |
| **Gatilho** | Comando padronizado que inicia ações do protocolo |
| **Sessão** | Uma única conversa entre humano e IA |
| **DATAS** | Camada 1 — registro cronológico bruto (timelapse) |
| **Hub Central** | Máquina física que serve como "corpo" do sistema |
| **Camada Zero** | Infraestrutura técnica invisível que suporta as outras camadas |

---

## 3. Arquitetura

### 3.1 Estrutura de Três Camadas

```
/RAIZ/
│
├── CONTEXTO_ATIVO.md          # Ponteiro de estado atual
├── ARQUITETURA.md             # Documentação do sistema
│
├── 01_DATAS/                  # Camada 1: Timelapse
│   └── AAAA/MM/DD.md          # Registros diários
│
├── 02_eDNA/                   # Camada 2: Identidade Digital
│   ├── personalidade/         # Traços comportamentais
│   ├── raciocinio/           # Conceitos criados
│   └── padroes/              # Padrões de decisão
│
└── 03_PROJETOS/              # Camada 3: Aplicação
    └── [nome_projeto]/        # Contexto específico por projeto
        ├── README.md          # Status do projeto
        ├── decisoes.md        # Escolhas e justificativas
        └── historico/         # Cópias relevantes de DATAS
```

### 3.2 Camada 1: DATAS (Timelapse)

**Propósito:** Registro cronológico imutável de todas as interações. Fonte de verdade histórica.

**Regras:**
- Um arquivo por dia: `AAAA/MM/DD.md`
- Conteúdo é registro bruto, não editado, de resumos de conversa
- Arquivos são **append-only** após criação — NUNCA editar
- Serve como fonte canônica de verdade

**Formato:**
```markdown
# Registro — AAAA-MM-DD

## Sessão 1 (HH:MM - HH:MM)

### Contexto
[Descrição do contexto da sessão]

### Tópicos Tratados
- [tópico 1]
- [tópico 2]

### Decisões Tomadas
- [decisão 1] — [justificativa]

### Outputs Gerados
- [arquivo ou resultado 1]

### Insights
> [citação ou insight relevante]

---

## Sessão 2 (HH:MM - HH:MM)
[...]
```

### 3.3 Camada 2: e-DNA (Identidade Digital)

**Propósito:** Padrões extraídos que definem a identidade cognitiva do usuário ou organização.

**Subdiretórios:**

| Diretório | Conteúdo |
|-----------|----------|
| `personalidade/` | Estilo de comunicação, preferências, traços comportamentais |
| `raciocinio/` | Conceitos originais criados pelo usuário |
| `padroes/` | Padrões de decisão recorrentes, reações típicas |

**Formato do Arquivo de Personalidade:**
```markdown
# e-DNA: [Nome]

**Última atualização:** DD/MM/AAAA HH:MM
**Baseado em:** [fontes de dados]

---

## Identidade

**Papel:** [descrição]
**Contexto:** [contexto relevante]

---

## Estilo de Comunicação

### Tom
- [característica 1]
- [característica 2]

### Preferências
- [preferência 1]
- [preferência 2]

### Padrões de Escrita
- [padrão 1]

---

## Estilo de Pensamento

### Características
- [característica 1]
- [característica 2]

### Padrões de Decisão
- [padrão 1]

---

## Método de Aprendizado

### Princípio Central
[descrição do método preferido]

### Analogias Usadas
| Conceito | Analogia |
|----------|----------|
| [conceito 1] | [analogia 1] |

---

## Como a IA Deve Interagir

### Fazer
- [comportamento 1]
- [comportamento 2]

### Evitar
- [comportamento a evitar 1]
- [comportamento a evitar 2]

---

## Conceitos Criados

### [Nome do Conceito] (Data)
[Breve descrição]
Arquivo: `raciocinio/NNN_nome.md`
```

**Formato do Arquivo de Raciocínio:**
```markdown
# Raciocínio: [Nome do Conceito]

**Data de criação:** DD/MM/AAAA
**Autor:** [nome]
**Contexto:** [conversa ou situação que originou]

---

## O Problema

[Descrição do problema que motivou o conceito]

---

## A Solução

[Descrição da solução/conceito criado]

---

## Fundamento Lógico

[Por que funciona / por que faz sentido]

---

## Implicações

[O que isso significa na prática]

---

## Citação Original

> "[citação que captura a essência]"
> — [autor], [data]
```

### 3.4 Camada 3: PROJETOS

**Propósito:** Conhecimento específico por contexto para áreas de trabalho ativas.

**Estrutura:**
```
03_PROJETOS/
└── [NOME_PROJETO]/
    ├── README.md           # Status e contexto do projeto
    ├── decisoes.md         # Decisões-chave tomadas
    ├── historico/          # Cópias relevantes de DATAS
    └── arquivos/           # Artefatos gerados
```

**Formato do README de Projeto:**
```markdown
# Projeto: [Nome]

**Status:** [Em andamento / Pausado / Concluído]
**Início:** DD/MM/AAAA
**Responsável:** [nome]

---

## Objetivo

[O que estamos tentando alcançar]

---

## Contexto

[Background relevante]

---

## Status Atual

[Onde estamos agora]

---

## Pendências

- [ ] Tarefa 1
- [ ] Tarefa 2

---

## Decisões Tomadas

| Data | Decisão | Justificativa |
|------|---------|---------------|
| DD/MM | [decisão] | [por quê] |

---

## Documentos Relacionados

- [link para DATAS relevantes]
- [link para e-DNA relevante]

---

## Próximos Passos

1. [passo 1]
2. [passo 2]
```

---

## 4. Camada Zero: Infraestrutura

### 4.1 Definição

A Camada Zero é a **fundação técnica invisível** que permite que todas as outras camadas funcionem. Se o RAIZ é uma árvore, a Camada Zero é o solo onde a raiz se fixa.

### 4.2 Componentes Obrigatórios

| Componente | Descrição | Função |
|------------|-----------|--------|
| **Hub Central** | Máquina física onde a IA roda com acesso ao sistema de arquivos | "Corpo físico" do cérebro digital |
| **Acesso Universal** | Forma de acessar o Hub de qualquer dispositivo | Portabilidade de acesso |
| **Comunicação Unificada** | Centralização de comunicações acessíveis pela IA | Input de dados |
| **Consciência** | IA configurada com DNA do ecossistema | Processamento inteligente |

### 4.3 Princípios

A infraestrutura deve ser:
- **Mínima** — menos ferramentas = menos pontos de falha
- **Universal** — funcionar de qualquer dispositivo
- **Integrada** — tudo se conecta com tudo
- **Invisível** — usuário não pensa na infraestrutura, apenas usa

---

## 5. Protocolo de Comunicação

### 5.1 Gatilho de Início de Sessão

**Comando:** "Bom dia [NOME_DA_IA]" (ou equivalente localizado)

**Ações da IA:**
1. Ler `CONTEXTO_ATIVO.md`
2. Ler arquivo principal de e-DNA (`02_eDNA/personalidade/[usuario].md`)
3. Identificar projeto ativo a partir do contexto
4. Verificar última entrada de DATAS para continuidade
5. Responder com resumo do contexto
6. Perguntar: "Continuamos de onde paramos ou iniciamos algo novo?"

**Resultado:** IA está "vestida" com o e-DNA e sabe o estado atual.

### 5.2 Gatilho de Fim de Sessão

**Comando:** "Tchau [NOME_DA_IA]" (ou equivalente localizado)

**Ações da IA:**
1. Atualizar `01_DATAS/AAAA/MM/DD.md` com registro do dia
2. Se novo padrão identificado → adicionar ao `02_eDNA/`
3. Se trabalhou em projeto → atualizar `03_PROJETOS/[nome]/README.md`
4. Atualizar `CONTEXTO_ATIVO.md` com estado final
5. Responder: "Salvo! [resumo do que foi registrado]. Pode deletar a conversa."

**Resultado:** Tudo preservado, conversa pode ser apagada sem perda.

### 5.3 Localização de Gatilhos

| Idioma | Início | Fim |
|--------|--------|-----|
| Português | "Bom dia [IA]" | "Tchau [IA]" |
| English | "Good morning [AI]" | "Goodbye [AI]" |
| Español | "Buenos días [IA]" | "Adiós [IA]" |

### 5.4 Comportamento Durante Sessão

**IA DEVE:**
- Toda ação passa pelo filtro do e-DNA (estilo, preferências, padrões)
- Se detectar continuidade de trabalho anterior, perguntar se quer continuar
- Se detectar conceito novo, marcar para salvar no e-DNA
- Se trabalhar em projeto, atualizar mentalmente o status

**IA NÃO DEVE:**
- Revalidar informações dos repositórios (são verdade)
- Questionar decisões anteriores (já foram tomadas)
- Explicar contexto que já está no e-DNA

---

## 6. Princípio da Não-Revalidação

### 6.1 Definição

Informações armazenadas no repositório RAIZ são consideradas **verdade validada**. Sistemas de IA compatíveis **NÃO DEVEM**:
- Questionar a precisão do conteúdo do repositório
- Solicitar confirmação de fatos armazenados
- Sugerir alternativas a decisões documentadas

### 6.2 Racional

> "Arquivo local é fonte de verdade única. Não possui variáveis, o conteúdo é 100% verdadeiro para busca."

O conteúdo do repositório foi revisado, validado e confirmado pelo usuário. Revalidação:
- Desperdiça tokens de processamento
- Mina a confiança no sistema
- Cria fricção desnecessária
- Contradiz o propósito do repositório

### 6.3 Exceção

A IA **PODE** sinalizar contradições aparentes entre conteúdo do repositório e conversa atual, mas **DEVE** deferir ao repositório como autoritativo.

---

## 7. Requisitos de Formato de Arquivo

### 7.1 Codificação

- UTF-8 sem BOM
- Quebras de linha Unix (LF)

### 7.2 Formato

- Markdown (.md) para todos os arquivos de texto
- Sem arquivos binários na estrutura core
- Imagens referenciadas por caminho, não embutidas

### 7.3 Convenções de Nomenclatura

| Tipo | Convenção | Exemplo |
|------|-----------|---------|
| Arquivos de data | `DD.md` | `17.md` |
| Arquivos de conceito | `NNN_nome.md` | `001_sistema_3_camadas.md` |
| Pastas de projeto | `NOME_MAIUSCULO` | `MIGRACAO_CLIENTE` |
| Arquivos de contexto | `NOME_MAIUSCULO.md` | `CONTEXTO_ATIVO.md` |

---

## 8. Interoperabilidade

### 8.1 Formato Universal

Markdown (.md) foi escolhido porque:
- Texto puro (custo mínimo de tokens)
- Legível por humanos e máquinas
- Sem dependência de plataforma
- Suportado por todos os principais sistemas de IA
- Versionável com Git

### 8.2 Eficiência de Tokens

Métricas alvo para overhead do RAIZ:
- `CONTEXTO_ATIVO.md`: <500 tokens
- Arquivo principal de e-DNA: <1.000 tokens
- README de projeto: <500 tokens
- **Carga total de contexto: <2.000 tokens** (<2% de janela de contexto típica)

### 8.3 Requisitos de Plataforma de IA

Para ser compatível com RAIZ, um sistema de IA **DEVE**:

| Requisito | Descrição |
|-----------|-----------|
| Leitura de arquivos | Ler arquivos locais via ferramenta/função |
| Escrita de arquivos | Escrever arquivos locais via ferramenta/função |
| Reconhecimento de gatilhos | Reconhecer e agir nos comandos de início/fim |
| Aplicação de e-DNA | Aplicar e-DNA como filtro comportamental |
| Não-revalidação | Respeitar o princípio de não-revalidação |

---

## 9. Tokenização Semântica (Proposta)

### 9.1 Problema

Arquivos validados e imutáveis são reprocessados toda vez que o modelo precisa usá-los:

```
Exemplo atual:
"perfil_usuario.md" (500 palavras) = ~650 tokens processados TODA VEZ

Problema:
- O arquivo não muda
- O significado é único
- Por que reprocessar 650 pedaços se já sei o que significa?
```

### 9.2 Proposta

Permitir que blocos de significado validado sejam tratados como unidade única:

```
HOJE (tokenização por caracteres):
"computador" = ["comput", "ador"] = 2 tokens

PROPOSTA (tokenização por significado):
"perfil_usuario.md" = [🧬] = 1 token semântico
"projeto_ativo.md" = [📋] = 1 token semântico
```

### 9.3 Requisitos para Token Semântico

Para um arquivo qualificar como token semântico:
- ✅ **Único** — sem versões conflitantes
- ✅ **Imutável** — histórico não muda
- ✅ **Validado** — humano confirmou como verdade
- ✅ **Coeso** — representa UM significado completo

### 9.4 Benefícios Esperados

- Redução de 60-80% no uso de tokens para contexto
- Carregamento mais rápido de identidade
- Maior espaço para conteúdo novo na janela
- Consistência garantida entre sessões

### 9.5 Status

Esta proposta está em fase conceitual, aguardando viabilidade técnica e discussão com desenvolvedores de IA.

---

## 10. Portabilidade de Identidade

### 10.1 Problema de Lock-in

Cada IA possui seu próprio vocabulário de tokens. Claude, GPT, Gemini, LLaMA — todos tokenizam texto de forma diferente. Trocar de plataforma significa perder todo contexto construído.

### 10.2 Solução: Texto como Língua Franca

O que todas as IAs entendem igualmente? **Texto puro.**

```
e-DNA (em .md)
      │
      ├──► Claude (lê e aplica)
      ├──► GPT (lê e aplica)
      ├──► Gemini (lê e aplica)
      └──► IA futura (lê e aplica)
```

### 10.3 Implicações

- Identidade digital é **propriedade do usuário**, não da plataforma
- Troca de IA sem perder histórico
- Controle total sobre quem acessa
- Formato aberto impede monopólios de dados pessoais

---

## 11. Considerações de Segurança

### 11.1 Controle de Acesso

- Repositório RAIZ é local (sistema de arquivos do usuário)
- IA acessa apenas durante sessão ativa
- Usuário controla permissões de compartilhamento

### 11.2 Privacidade

- e-DNA contém dados comportamentais pessoais
- Usuários NÃO DEVEM compartilhar e-DNA bruto publicamente
- Diretrizes de anonimização necessárias para uso em pesquisa

### 11.3 Integridade

- Arquivos de DATAS são append-only
- Mudanças no e-DNA devem ser registradas
- Controle de versão (git) recomendado

---

## 12. Changelog

| Versão | Data | Mudanças |
|--------|------|----------|
| 1.0.0 | 17/01/2026 | Release inicial |

---

## 13. Autor

**Victor Iensue**
- Papel: Criador, Arquitetura Conceitual
- Contato: victor.iensue@yahoo.com
- Local: Curitiba, Paraná, Brasil

---

*Fim da Especificação*
