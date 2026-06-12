# 📚 Análise Exploratória de Empréstimos de Biblioteca (SISBI)

Projeto de Análise de Dados desenvolvido como parte do desafio **7 Days of Code** da Alura, com o objetivo de explorar o comportamento de empréstimos do **Sistema de Bibliotecas (SISBI)** ao longo de uma década, identificando padrões temporais, perfis de usuários e tendências por curso acadêmico.

---

## 📋 Sobre o Projeto

A análise cobre registros de empréstimos de 2010 a 2020, consolidando múltiplas fontes de dados (CSV, Parquet, Excel e JSON) em um pipeline unificado. O resultado final inclui visualizações exploratórias e uma tabela HTML interativa com variação percentual de empréstimos por curso de pós-graduação.

---

## 📂 Fontes de Dados

| Arquivo | Formato | Conteúdo |
|---|---|---|
| `emprestimos-{ano}{semestre}.csv` | CSV (21 arquivos) | Registros de empréstimos por ano/semestre (2010–2020) |
| `dados_exemplares.parquet` | Parquet | Detalhes dos exemplares (título, localização CDU, coleção) |
| `matricula_alunos.xlsx` | Excel (2 abas) | Cadastro de alunos antes e após 2010 |
| `cadastro_alunos.json` | JSON | Cadastro de alunos de graduação e pós-graduação |
| `previsao` | TXT | Previsão de empréstimos para 2022 por curso |

Todos os dados são carregados diretamente de URLs públicas do GitHub da Alura.

---

## 🔍 Estrutura do Projeto

```
├── 1. Importação e Consolidação
│   ├── Leitura de 21 CSVs semestrais
│   ├── Concatenação em DataFrame único
│   └── Remoção de duplicatas
│
├── 2. Enriquecimento dos Dados
│   ├── Merge com dados de exemplares (código de barras)
│   ├── Classificação CDU (Classificação Decimal Universal)
│   └── Tratamento de nulos e tipagem de colunas
│
├── 3. Análise Exploratória (EDA)
│   ├── Empréstimos por ano (linha)
│   ├── Empréstimos por mês — sazonalidade (linha)
│   ├── Empréstimos por faixa horária (barras)
│   ├── Frequência por tipo de vínculo, coleção, biblioteca e CDU
│   └── Boxplot mensal: graduação vs. pós-graduação
│
├── 4. Análise por Curso
│   ├── Integração Excel + JSON (cadastro de usuários)
│   ├── Pivot table: empréstimos por curso e ano (graduação)
│   └── Pivot table: empréstimos por curso e ano (pós-graduação)
│
└── 5. Apresentação em HTML
    ├── Cálculo de variação percentual entre anos
    └── Tabela estilizada com gradiente de cores (RdYlGn)
```

---

## ⚙️ Tecnologias Utilizadas

| Biblioteca | Uso |
|---|---|
| `pandas` | Manipulação, limpeza e agregação de dados |
| `matplotlib` / `seaborn` | Visualizações exploratórias |
| `openpyxl` | Leitura de arquivos Excel |

---

## 📊 Principais Análises

**Padrões temporais** — Gráficos de linha para volume de empréstimos por ano e por mês revelam picos acadêmicos e quedas em períodos de recesso.

**Faixa horária** — Gráfico de barras identifica os horários de maior e menor fluxo ao longo do dia, útil para gestão de equipe.

**Perfil dos usuários** — Alunos de graduação representam ~78% dos empréstimos; o Acervo Circulante responde por 99% dos itens retirados; Ciências Aplicadas é a categoria CDU mais demandada (~69%).

**Distribuição mensal por grupo** — Boxplots comparativos entre graduação e pós-graduação evidenciam diferenças de volume e variabilidade ao longo dos anos.

**Variação percentual por curso** — Tabela pivot com diferença percentual de empréstimos entre 2017, 2018, 2019 e previsão 2022 para cursos de pós-graduação, exportada como HTML estilizado com gradiente de cores.

---

## 🚀 Como Executar

**1. Clone o repositório**
```bash
git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
```

**2. Instale as dependências**
```bash
pip install pandas matplotlib seaborn openpyxl pyarrow
```

**3. Execute o notebook**

Abra o arquivo `.ipynb` no Jupyter Notebook, JupyterLab ou Google Colab. Todos os dados são baixados automaticamente via URL — nenhum arquivo local é necessário.

> **Nota:** A célula final gera um arquivo `teste.html` com a tabela de variação percentual estilizada. Ele será salvo no diretório de execução do notebook.

---

## 📁 Output

Ao final da execução, o notebook gera um arquivo `teste.html` contendo uma tabela formatada com a variação percentual de empréstimos por curso de pós-graduação entre os anos analisados, com destaque visual por gradiente de cores (vermelho → amarelo → verde).

---

## 📄 Créditos

Projeto desenvolvido com base no desafio [7 Days of Code — Python Pandas](https://github.com/FranciscoFoz/7_Days_of_Code_Alura-Python-Pandas) da Alura, criado por Francisco Foz.
