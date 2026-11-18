# Instruções do projeto

Repositório público de dados de pesquisa: documentação do dataset da pesquisa quantitativa com residentes da APA do Maracanã (São Luís/MA). Hoje contém só `README.md` e `readme_dataset_apa_maracana_github.md`. Os arquivos descritos neste último (`data/`, `docs/`, `analysis/`, `LICENSE`) ainda não estão no repositório.

## Regras do dataset

- Não gere, altere, complete nem "corrija" dados brutos. Dado novo só entra se o usuário fornecer o arquivo.
- Não invente estatística, p-valor, DOI, citação, licença ou metadado. Lacuna vira pendência.
- O repositório é público: nada que identifique respondentes (nome, endereço, telefone, documento, coordenada de residência).
- Afirmações metodológicas (amostra, coleta, teste estatístico) só mudam com pedido explícito do usuário.

## Orquestração: Opus coordena, subagentes executam

Implantado em 2026-11-18. Vale para demandas no **modo EXECUTAR** ou que toquem mais de uma frente (tela, testes, documentação). Ajuste pequeno em um arquivo só: faça direto, sem delegar, porque cada subagente começa do zero e consome contexto.

### Papéis e modelos

- **Sessão principal (coordenador):** Opus quando disponível. Planeja, decide o que é compartilhado, integra e verifica. Só informe o modelo efetivamente usado quando puder confirmá-lo (por exemplo, com `get_session`).
- **Subagentes do projeto** em `.claude/agents/`: `tela`, `testes` e `documentacao`, todos com `model: sonnet`.
- **Haiku:** apenas para inventário ou conferência simples e bem delimitada, passando `model: "haiku"` na chamada do `Agent`.

### Procedimento (modo EXECUTAR)

1. **Inspecione.** Leia as instruções, rode `git status`, identifique os comandos de verificação (seção abaixo) e os arquivos afetados. Demanda em branco: peça a descrição antes de começar. Critérios em branco: derive-os da demanda e registre as suposições.
2. **Planeje** numa tabela com ID, frente, entrega, dependências, arquivos sob responsabilidade, modelo e critério de conclusão. Ative só as subtarefas necessárias; um agente pode acumular subtarefas que compartilham contexto.

   | ID | Frente | Entrega de referência |
   |---|---|---|
   | T1 | Tela | Mapear o fluxo do usuário e os componentes afetados |
   | T2 | Tela | Implementar o comportamento solicitado na interface |
   | T3 | Tela | Verificar os estados relevantes e a acessibilidade |
   | Q1 | Testes | Traduzir os critérios de aceitação em cenários verificáveis |
   | Q2 | Testes | Criar ou ajustar testes para as regressões pertinentes |
   | Q3 | Testes | Executar as verificações e registrar o resultado |
   | D1 | Documentação | Identificar os trechos afetados pela mudança |
   | D2 | Documentação | Atualizar instruções e exemplos de uso |
   | D3 | Documentação | Conferir exemplos e instruções com o código integrado |

3. **Delegue por dependência** com a ferramenta `Agent`.
   - Mande a cada agente só o necessário: ID, objetivo, arquivos autorizados, dependências, resultado esperado e como validar. Peça a devolução no formato do perfil.
   - Paralelo só para o que é independente: T1, Q1 e D1 podem começar juntos; Q3 e D3 esperam a implementação correspondente.
   - Um único responsável por arquivo em cada rodada.
   - **Worktrees:** em edições paralelas com risco de conflito, chame o `Agent` com `isolation: "worktree"`. O worktree nasce do último commit, então não leva alterações não commitadas: se a subtarefa depende delas, commite antes (com o aval do usuário) ou rode em sequência. Bases divergentes ou mesmos arquivos: sequência. O resultado devolve caminho e branch do worktree; integre com `git merge` ou `git cherry-pick`.
   - Sem a ferramenta `Agent`: execute as frentes em sequência na sessão principal e informe que a delegação estava indisponível. Sem seleção de modelo: registre o modelo usado quando conhecido.
4. **Integre e verifique.** Revise os diffs, incorpore na ordem das dependências, preserve o trabalho local do usuário e limite as mudanças ao escopo. Rode as verificações no estado integrado; se falharem, corrija a causa (nunca enfraqueça o teste) e rode de novo. Confirme cada critério de aceitação com evidência observável.
5. **Entregue** o que mudou, os agentes e modelos usados (quando confirmados), as verificações executadas e seus resultados, as pendências e os critérios ainda sem evidência, e o progresso em tarefas verificadas sobre ativadas (por exemplo, `6 de 7`). `9 de 9` só com as nove verificadas.

### Comandos de verificação deste repositório

Não há código, build, lint nem testes. Verificações disponíveis hoje:

| O quê | Como |
|---|---|
| Arquivos citados existem | comparar a árvore descrita no README com `git ls-files` |
| Links e âncoras internas | conferir cada link relativo do Markdown contra os arquivos do repositório |
| Coerência numérica | quando o CSV existir: linhas e colunas iguais às declaradas (383 × 6) e colunas iguais ao dicionário de dados |

A frente Testes pode transformar essas conferências em script (por exemplo, `scripts/verificar_dataset.py`) quando uma demanda pedir.

### Mapeamento das frentes neste repositório

- **Tela** = apresentação no GitHub: renderização do Markdown, tabelas, árvore de diretórios e, se um dia houver, gráficos. É a frente menos usada aqui; ative só quando a demanda mexer na apresentação.
- **Testes** = conferências de consistência entre documentação e arquivos.
- **Documentação** = `README.md` e `readme_dataset_apa_maracana_github.md`.
