# Dataset: Proibição do Retrocesso Ambiental e Gestão de Unidades de Conservação na APA Maracanã

**DOI do Dataset:** Será gerado pelo SciELO Data após o depósito  
**Data de Geração:** 2026-05-07  
**Autor Principal:** Willian Barbosa Filho (UFMA)  
**ORCID:** 0000-0001-5016-0713

---

# 1. Informações Gerais

## Título do Manuscrito Relacionado

**PROIBIÇÃO DO RETROCESSO AMBIENTAL E GESTÃO DE UNIDADES DE CONSERVAÇÃO: ANÁLISE CONSTITUCIONAL E EMPÍRICA DOS CONFLITOS SOCIOAMBIENTAIS NA APA MARACANÃ**

## Resumo dos Dados

Este repositório contém os dados brutos anonimizados, o dicionário de variáveis e os arquivos de análise estatística utilizados na pesquisa quantitativa realizada com 383 residentes da Área de Proteção Ambiental (APA) do Maracanã, em São Luís/MA.

Os dados subsidiam a análise constitucional da vedação ao retrocesso ambiental, com foco no mínimo existencial ecológico, infraestrutura sanitária e conflitos socioambientais em unidades de conservação.

O conjunto inclui a aplicação do teste Qui-Quadrado de Independência para avaliação da associação entre localização territorial e acesso ao esgotamento sanitário.

## Palavras-chave

- Direito Ambiental
- APA Maracanã
- Saneamento Básico
- Qui-Quadrado
- Ciência Aberta
- Unidades de Conservação
- Retrocesso Ambiental

---

# 2. Estrutura do Repositório

```text
.
├── data/
│   └── Data_Survey_APA_Maracana_Raw.csv
│
├── docs/
│   └── Codebook_Dicionario_Variaveis.docx
│
├── analysis/
│   └── Analysis_Script_ChiSquare.xlsx
│
├── LICENSE
└── README.md
```

---

# 3. Descrição dos Arquivos

## `Data_Survey_APA_Maracana_Raw.csv`

- Tipo: Dados brutos anonimizados
- Formato: CSV delimitado por vírgulas
- Dimensão: 383 linhas × 6 colunas

### Conteúdo

- infraestrutura sanitária
- percepção ambiental
- práticas de descarte
- conhecimento sobre a APA

---

## `Codebook_Dicionario_Variaveis.docx`

Documento contendo:

- descrição completa das variáveis
- codificação binária
- categorias territoriais
- critérios metodológicos utilizados

---

## `Analysis_Script_ChiSquare.xlsx`

Arquivo de análise estatística contendo:

- tabelas de contingência
- cálculo do Qui-Quadrado
- valores de p
- validação estatística apresentada no artigo

---

# 4. Informações Metodológicas

## Coleta de Dados

- **Período:** Outubro de 2024
- **Método:**
  - aplicação presencial
  - formulário digital estruturado

## Amostragem

- Tipo: Probabilística casual simples
- Tamanho da amostra: n = 383
- Margem de erro: 5%
- Nível de confiança: 95%

## Processamento e Ética

Os dados foram anonimizados para remoção de:

- nomes
- contatos
- endereços específicos
- quaisquer identificadores pessoais

A pesquisa observou princípios éticos aplicáveis à pesquisa social e proteção de dados.

## Procedimento Estatístico

Foi aplicado o teste Qui-Quadrado de Independência (`χ²`) para verificar associação entre:

- Zona de localização da APA
- Existência de rede oficial de esgotamento sanitário

---

# 5. Dicionário de Dados

| Variável | Descrição | Código |
|---|---|---|
| ID_RESP | Identificador do respondente | 1–383 |
| ZONA | Zona da APA conforme Plano de Manejo | 1 = Ocupação Intensiva; 2 = Uso Sustentável; 3 = Preservação |
| ESGOTO | Existência de rede de esgoto | 0 = Não possui; 1 = Possui |
| AGUA | Água tratada antes do consumo | 0 = Não; 1 = Sim |
| LIXO | Queima de resíduos no terreno | 0 = Não; 1 = Sim |
| CONHECE | Conhecimento sobre restrições da APA | 0 = Não conhece; 1 = Conhece |

---

# 6. Requisitos de Software

## Arquivo CSV

Compatível com:

- Microsoft Excel
- Google Sheets
- LibreOffice Calc
- R
- Python/Pandas

## Arquivo XLSX

Recomendado:

- Microsoft Excel 2016 ou superior

---

# 7. Licença

Este dataset está licenciado sob:

**Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)**

Licença oficial:

https://creativecommons.org/licenses/by-nc/4.0/

---

# 8. Citação Recomendada

```bibtex
@dataset{barbosa_filho_2026_apa_maracana,
  author       = {Willian Barbosa Filho},
  title        = {Dataset: Proibição do Retrocesso Ambiental e Gestão de Unidades de Conservação na APA Maracanã},
  year         = {2026},
  publisher    = {SciELO Data},
  doi          = {A ser atribuído},
  version      = {1.0}
}
```

---

# 9. Relevância Científica

O conjunto de dados permite:

- replicabilidade científica
- transparência metodológica
- reutilização acadêmica
- validação estatística independente
- estudos comparativos em políticas ambientais urbanas

Também contribui para práticas de Ciência Aberta em pesquisas jurídicas empíricas no Brasil.

---

# 10. Sugestão Estratégica de Melhoria

Seu dataset já está acima da média dos repositórios jurídicos brasileiros em estrutura metodológica. Porém, há alguns pontos que podem elevar significativamente o padrão internacional do material:

## Pontos Fortes

- Estrutura alinhada à Ciência Aberta
- Clareza metodológica
- Variáveis operacionalizadas
- Reprodutibilidade estatística
- Compatibilidade com SciELO Data

## Pontos que Ainda Podem Ser Fortalecidos

### 1. Inserir arquivo `README_EN.md`

Versão integral em inglês aumenta:

- indexação internacional
- reutilização por pesquisadores estrangeiros
- chance de citação
- aderência a periódicos A1

### 2. Adicionar arquivo `metadata.json`

Muitos repositórios internacionais utilizam metadados padronizados em JSON ou Dublin Core.

### 3. Incluir seção “Limitações do Dataset”

Exemplo:

- recorte territorial específico
- dados autorreferidos
- ausência de séries históricas
- limitações de infraestrutura local

Isso aumenta credibilidade científica porque demonstra consciência metodológica.

### 4. Disponibilizar script em R

Mesmo utilizando Excel, disponibilizar:

- `analysis.R`
- `requirements.txt`
- outputs automatizados

aproxima o trabalho de padrões internacionais de ciência reprodutível.

### 5. Adicionar identificador geoespacial

Uma versão futura pode incluir:

- shapefile
- GeoJSON
- mapas de calor
- setores censitários

Isso abre portas para publicações interdisciplinares em:

- políticas públicas
- urbanismo
- geografia jurídica
- justiça ambiental

---

# 11. Estrutura Recomendada Final para Publicação Internacional

```text
repository/
│
├── README.md
├── README_EN.md
├── LICENSE
├── CITATION.cff
├── metadata.json
│
├── data/
│   └── Data_Survey_APA_Maracana_Raw.csv
│
├── docs/
│   └── Codebook_Dicionario_Variaveis.docx
│
├── analysis/
│   ├── Analysis_Script_ChiSquare.xlsx
│   └── analysis.R
│
└── outputs/
    ├── contingency_tables.csv
    └── chi_square_results.csv
```

