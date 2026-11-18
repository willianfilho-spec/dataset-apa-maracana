# Instruções do projeto

Repositório público de dados de pesquisa: documentação do dataset da pesquisa quantitativa com residentes da APA do Maracanã (São Luís/MA). Hoje contém só `README.md` e `readme_dataset_apa_maracana_github.md`. Os arquivos descritos neste último (`data/`, `docs/`, `analysis/`, `LICENSE`) ainda não estão no repositório.

## Regras do dataset

- Não gere, altere, complete nem "corrija" dados brutos. Dado novo só entra se o usuário fornecer o arquivo.
- Não invente estatística, p-valor, DOI, citação, licença ou metadado. Lacuna vira pendência.
- O repositório é público: nada que identifique respondentes (nome, endereço, telefone, documento, coordenada de residência).
- Afirmações metodológicas (amostra, coleta, teste estatístico) só mudam com pedido explícito do usuário.

## Política de execução e delegação

Atualizada em 2026-11-18. Princípio: usar a menor complexidade operacional capaz de entregar uma solução correta, verificável e fácil de manter. **Não criar subagentes por padrão.** Delegar é decisão técnica, baseada em independência, custo, risco e benefício verificável, nunca obrigação.

### 1. Inspeção inicial

Antes de qualquer tarefa: identificar o repositório e seu objetivo; inspecionar a estrutura que realmente existe (`git ls-files`, `git status`); identificar os arquivos que podem ser alterados; ler as instruções e os testes disponíveis; mapear dependências, conflitos e riscos. **Não presumir que existem os arquivos descritos no README.** Demanda em branco: peça a descrição. Critérios de aceitação em branco: derive-os da demanda e registre as suposições.

### 2. Seleção da estratégia

| Estratégia | Quando usar |
|---|---|
| **Direta** (sessão principal, sem subagente) | correção pequena e localizada, mudança simples em um arquivo, ajuste de documentação, tarefa com baixo custo de análise |
| **Sequencial** | tarefas interdependentes, alterações concentradas no mesmo arquivo, etapas que dependem do resultado anterior, refatoração com risco de regressão |
| **Paralela** | só quando **todas** valem: tarefas de fato independentes; interfaces e responsabilidades definidas; arquivos ou áreas de escrita isolados; custo de integração aceitável; ganho provável maior que o custo extra de contexto |

Registre a estratégia escolhida e o motivo antes de executar.

### 3. Controle de subagentes (só quando a estratégia justificar)

- Perfis do projeto em `.claude/agents/`: `tela`, `testes` e `documentacao` (`model: sonnet`). Haiku só para inventário ou conferência simples, com `model: "haiku"` na chamada do `Agent`. A sessão principal (Opus, quando disponível) coordena e integra; informe o modelo só quando puder confirmá-lo (por exemplo, com `get_session`).
- Envie só o contexto necessário: objetivo, escopo, arquivos autorizados e critérios de aceitação. Não duplique análises já feitas.
- Um único responsável por arquivo; nunca edições concorrentes no mesmo arquivo.
- Paralelo com risco de conflito: `Agent` com `isolation: "worktree"`. O worktree nasce do último commit e não leva alterações não commitadas; se a subtarefa depende delas, rode em sequência. Integre com `git merge` ou `git cherry-pick`.
- **Sessão com vários repositórios:** perfis de mesmo nome colidem e só uma versão é carregada. Confira se a descrição do perfil carregado cita este repositório; se não citar, não o use. Execute direto ou passe ao `general-purpose` o texto do perfil correto (`.claude/agents/<perfil>.md`).
- Sem a ferramenta `Agent`: execute em sequência na sessão principal e informe.

Subtarefas de referência, para planejar quando houver mais de uma frente (ative só as necessárias; um mesmo agente pode acumular várias):

| ID | Frente | Entrega de referência |
|---|---|---|
| T1 / T2 / T3 | Tela | mapear fluxo e componentes / implementar / verificar estados e acessibilidade |
| Q1 / Q2 / Q3 | Testes | critérios em cenários verificáveis / criar ou ajustar testes / executar e registrar |
| D1 / D2 / D3 | Documentação | identificar trechos afetados / atualizar instruções e exemplos / conferir com o código integrado |

### 4. Validação

Depois das alterações: revisar o diff; executar os testes relevantes disponíveis; verificar regressões quando aplicável; identificar alterações fora do escopo; registrar os testes não executados e o motivo. Teste que falha: corrigir a causa, nunca enfraquecer o teste. **Não declarar sucesso sem evidência.**

### 5. Relatório final

1. O que foi alterado.
2. Quais arquivos foram modificados.
3. Qual estratégia foi usada e por quê (e, se houve subagentes, quais e com que modelo, quando confirmado).
4. Quais testes foram executados, com resultado; quais não foram e por quê.
5. Riscos e pendências, incluindo critérios de aceitação ainda sem evidência.

Se houve subtarefas, informe o progresso em verificadas sobre ativadas (por exemplo, `3 de 4`).

### Regras deste repositório (dataset)

- Inspecione o conteúdo existente antes de propor estrutura.
- Documente objetivos, formatos e validações do dataset.
- Corrija divergências **verificadas** entre o README e o repositório (por exemplo, arquivos descritos que não existem), sem inventar o conteúdo que falta.
- Não gere código sem requisitos minimamente definidos (o que verificar, sobre quais arquivos, com que resultado esperado).

### Comandos de verificação deste repositório

Não há código, build, lint nem testes. Verificações disponíveis hoje:

| O quê | Como |
|---|---|
| Arquivos citados existem | comparar a árvore descrita no README com `git ls-files` |
| Links e âncoras internas | conferir cada link relativo do Markdown contra os arquivos do repositório |
| Coerência numérica | quando o CSV existir: linhas e colunas iguais às declaradas (383 × 6) e colunas iguais ao dicionário de dados |

A frente Testes só transforma essas conferências em script (por exemplo, `scripts/verificar_dataset.py`) quando uma demanda trouxer requisitos minimamente definidos.

### Mapeamento das frentes neste repositório

- **Tela** = apresentação no GitHub: renderização do Markdown, tabelas, árvore de diretórios e, se um dia houver, gráficos. É a frente menos usada aqui; ative só quando a demanda mexer na apresentação.
- **Testes** = conferências de consistência entre documentação e arquivos.
- **Documentação** = `README.md` e `readme_dataset_apa_maracana_github.md`.
