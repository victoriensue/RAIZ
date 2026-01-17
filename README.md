# RAIZ Protocol

**Arquitetura Cognitiva para Preservação de Identidade Digital**

*Versão 1.0 — Janeiro 2026*

---

> *"RAIZ não é apenas um sistema de memória. É uma declaração de independência digital."*
> — Victor Iensue, 17 de Janeiro de 2026

---

## O Que é RAIZ?

RAIZ (do português "raiz") é um **protocolo aberto** para preservar e portar identidade cognitiva humana entre sistemas de inteligência artificial.

**Não é uma ferramenta. É um protocolo de preservação da consciência individual e coletiva.**

Assim como a raiz de uma árvore é invisível mas sustenta toda a estrutura, RAIZ é a infraestrutura invisível que sustenta a identidade, o conhecimento e a perpetuidade de pessoas e organizações.

---

## O Problema

Quando você interage com IA hoje:

- ❌ **Cada conversa começa do zero** — você repete contexto infinitamente
- ❌ **Trocar de plataforma perde tudo** — sua identidade está presa
- ❌ **Conhecimento morre com a sessão** — nada é preservado
- ❌ **Lock-in de identidade** — você não é dono dos seus dados cognitivos

> *"Hoje cada IA é como um médico novo — você conta toda sua história de novo. Com RAIZ, você leva seu prontuário completo para qualquer médico."*

---

## A Solução

RAIZ define uma arquitetura de **três camadas operacionais**:

```
┌─────────────────────────────────────────────────────────────┐
│              CAMADA 1: DATAS (Timelapse)                    │
│                                                             │
│   • Registro cronológico bruto — 100% do conteúdo           │
│   • Estrutura: /ano/mês/dia.md                              │
│   • IMUTÁVEL após criação — fonte de verdade histórica      │
│   • Regra: nunca editar, apenas adicionar                   │
├─────────────────────────────────────────────────────────────┤
│              CAMADA 2: e-DNA (Identidade Digital)           │
│                                                             │
│   • Padrões comportamentais EXTRAÍDOS das DATAS             │
│   • Subcategorias: personalidade, raciocínio, padrões       │
│   • ATUALIZADO continuamente por extração                   │
│   • Função: definir "quem é" para personalização            │
├─────────────────────────────────────────────────────────────┤
│              CAMADA 3: PROJETOS (Aplicação)                 │
│                                                             │
│   • Áreas específicas com conhecimento agregado             │
│   • Copia relevantes de DATAS + aplica e-DNA                │
│   • Uma pasta por projeto                                   │
│   • Função: contexto pronto para trabalho focado            │
└─────────────────────────────────────────────────────────────┘

FLUXO: [Conversa] → [DATAS registra] → [e-DNA extrai] → [PROJETOS aplica]
```

---

## Conceitos Fundamentais

### e-DNA (DNA Digital)

O conceito central do RAIZ. **Não é "preferências de usuário"** — é um modelo comportamental completo:

| Dimensão | O que captura |
|----------|---------------|
| **Como você pensa** | Padrões de raciocínio, conexões, análises |
| **Como você comunica** | Estilo, tom, formato preferido |
| **Como você decide** | Critérios, prioridades, vieses conscientes |
| **O que você criou** | Conceitos originais, frameworks, metodologias |

> *"O e-DNA permite que a máquina 'molde' outputs no estilo do humano, acumulando precisão ao longo do tempo."*

### Princípio da Não-Revalidação

**Informações no repositório RAIZ são verdade validada.**

A IA **NÃO DEVE**:
- Questionar a precisão do conteúdo do repositório
- Solicitar confirmação de fatos armazenados
- Sugerir alternativas a decisões documentadas

**Por quê?** O conteúdo foi revisado, validado e confirmado pelo usuário. Revalidação desperdiça tokens e mina a confiança.

> *"Arquivo local é fonte de verdade única. Não possui variáveis, o conteúdo é 100% verdadeiro para busca."*

### Portabilidade de Identidade

**Markdown (.md) é a "língua franca" entre IAs:**

```
Seu e-DNA (em .md)
       │
       ├──► Claude (lê e aplica)
       ├──► GPT (lê e aplica)
       ├──► Gemini (lê e aplica)
       └──► IA futura (lê e aplica)
```

- Não depende de tokenização específica
- Estruturado mas legível por humanos
- Qualquer modelo processa
- Sua identidade é **SUA**, não da plataforma

### Tokenização Semântica (Proposta Inovadora)

> *"Nosso padrão de palavras históricas não podem se transformar em 1 token? Já que é um significado único."*
> — Victor Iensue

**O problema:** Arquivos validados e imutáveis são reprocessados toda vez (~650 tokens para 500 palavras).

**A proposta:** Se um arquivo é único, imutável, validado e coeso — tratá-lo como unidade semântica única.

**Requisitos para token semântico:**
- ✅ Único (sem versões conflitantes)
- ✅ Imutável (histórico não muda)
- ✅ Validado (humano confirmou como verdade)
- ✅ Coeso (representa UM significado completo)

---

## Protocolo de Comunicação

### Gatilho de Início: "Bom dia [IA]"

**Ações da IA:**
1. Ler `CONTEXTO_ATIVO.md`
2. Ler arquivo principal de e-DNA
3. Identificar projeto ativo
4. Verificar última entrada de DATAS
5. Responder com resumo de contexto
6. Perguntar: *"Continuamos de onde paramos ou iniciamos algo novo?"*

### Gatilho de Fim: "Tchau [IA]"

**Ações da IA:**
1. Atualizar `01_DATAS/AAAA/MM/DD.md` com registro do dia
2. Se novo padrão identificado → adicionar ao `02_eDNA/`
3. Se trabalhou em projeto → atualizar `03_PROJETOS/[nome]/README.md`
4. Atualizar `CONTEXTO_ATIVO.md` com estado final
5. Responder: *"Salvo! [resumo]. Pode deletar a conversa."*

### Regras de Ouro

1. **Conversa é rascunho, repositório é documento final**
2. **Nunca questionar informação do repositório** — é verdade validada
3. **Sempre salvar antes de liberar para deletar**
4. **e-DNA é filtro, não conteúdo** — molda como fazer, não o que fazer

---

## Estrutura de Arquivos

```
/RAIZ/
│
├── CONTEXTO_ATIVO.md          ← Ler PRIMEIRO em cada sessão
├── ARQUITETURA.md             ← Documentação do sistema
│
├── 01_DATAS/                  ← TIMELAPSE (registro bruto)
│   └── AAAA/MM/DD.md          ← Um arquivo por dia, imutável
│
├── 02_eDNA/                   ← IDENTIDADE DIGITAL
│   ├── personalidade/         ← Quem você é
│   │   └── [nome].md
│   ├── raciocinio/           ← Conceitos que você criou
│   │   └── NNN_nome.md
│   └── padroes/              ← Como você decide
│
└── 03_PROJETOS/              ← TRABALHOS EM ANDAMENTO
    └── [NOME_PROJETO]/
        ├── README.md          ← Status e próximos passos
        ├── decisoes.md        ← Escolhas e justificativas
        └── historico/         ← Cópias relevantes de DATAS
```

---

## Economia de Tokens

| Sem RAIZ | Com RAIZ |
|----------|----------|
| Carregar conversa inteira | Ler só arquivos relevantes |
| Reexplicar contexto | Contexto já está no arquivo |
| Validar informações | Aceitar como verdade |
| Perder histórico ao deletar | Histórico preservado |
| ~50.000 tokens de contexto | ~2.000 tokens de carga |

---

## Documentação

| Documento | Descrição |
|-----------|-----------|
| [SPECIFICATION.md](SPECIFICATION.md) | Especificação técnica completa |
| [WHITEPAPER_PT.md](WHITEPAPER_PT.md) | Whitepaper em português |
| [GENESIS.md](GENESIS.md) | A história de como RAIZ nasceu |
| [LICENSE.md](LICENSE.md) | Licença CC BY 4.0 |
| [AUTHORS.md](AUTHORS.md) | Autoria e atribuição |

---

## Quick Start

1. **Crie a estrutura de pastas** conforme especificado acima
2. **Defina seu perfil e-DNA** em `02_eDNA/personalidade/`
3. **Configure os gatilhos** "Bom dia" e "Tchau" na sua IA
4. **Registre diariamente** em `01_DATAS/`
5. **Sua IA mantém contexto** entre sessões automaticamente

---

## Licença

RAIZ Protocol está sob [Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE.md).

Você é livre para usar, modificar e comercializar — **com atribuição ao autor original**.

---

## Autor

**Victor Iensue**
- Criador e Idealizador
- Curitiba, Paraná, Brasil
- Janeiro 2026

---

## Citação

```
Iensue, V. (2026). RAIZ: Arquitetura Cognitiva para Preservação de Identidade Digital.
Versão 1.0. Curitiba, Brasil.
```

---

## Contato

- Email: victor.iensue@yahoo.com
- GitHub: [este repositório]

---

> *"Criar um marco histórico na conexão humana à inteligência artificial sem perder a verdadeira essência. Buscar reconhecimento não pelo ego, mas pela melhoria da humanidade."*
