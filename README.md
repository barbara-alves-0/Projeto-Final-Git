
# Análise de Internamento Hospitalar em Portugal

Projeto Final - Data Science & Analytics · CESAE Digital
Pipeline: dados → exploração → limpeza e transformação → análise → dashboard.


## 1. Contexto do projeto

Análise de internamentos de Hospitais Portugueses, entre **janeiro de 2015 e março de 2026**.
O objetivo é avaliar como varia a duração dos internamentos, a partir dos registos hospitalares das informações inerentes ao internamento.

## 2. Pergunta de negócio

**Como varia o tempo de internamento hospitalar em Portugal em função da região, periodo temporal, especialidade, diagnóstico, faixa etária e sexo?**

User stories do dashboard:
- *Como gestor de uma unidade hospitalar, quero ver a demora média de internamento da minha região comparada com as restantes regiões de saúde.*
- *Como responsável de planeamento da ACSS, quero ver a evolução dos dias de internamento ao longo do tempo (2015–2026), para perceber o impacto de eventos como a pandemia na capacidade hospitalar.*
- *Como responsável clínico, quero ver a demora média por diagnóstico, faixa etária, sexo e especialidade, para perceber que perfil de doente ocupa mais dias de internamento.*

## 3. Fonte dos dados

**Ficheiro 1: Atividade de Internamento Hospitalar**
- **Fonte:** ACSS Dados.gov.pt -  https://dados.gov.pt/pages/datasets/atividade-de-internamento-hospitalar-2
- **Ficheiro:** `atividade-de-internamento-hospitalar_fich1.csv` 
- **Dimensão:** 17617 linhas · 7 colunas (Período, Região, Instituição, Localização Geográfica, Tipo de Especialidade, Doentes Saídos, Dias de Internamento)

**Ficheiro 2: Morbilidade e Mortalidade Hospitalar**
- **Fonte:** SNS Transparência -  https://transparencia.sns.gov.pt/explore/assets/morbilidade_mortalidade_hospit/
- **Ficheiro:** `morbilidade_mortalidade_hospit_fich2.csv` 
- **Dimensão:** 524407 linhas · 11 colunas (Período, Região, Instituição, Código Capítulo Diagnóstico Principal, Descrição Capítulo Diagnóstico Principal, Faixa Etária, Sexo, Internamentos, Dias de Internamento, Ambulatório, Óbitos)

## 4. Tecnologias usadas

- **Linguagem de análise:** Python (pandas, matplotlib)
- **Base de dados:** SQLite (consultas SQL)
- **Dashboard:** Power BI
- **Controlo de versões:** Git + GitHub

## 5. Estrutura do repositório

```
data/
  raw/         
    atividade-de-internamento-hospitalar_fich1.csv
    morbilidade_mortalidade_hospit_fich2.csv
  processed/ 
    atividade_de_internamento_tratado.csv 
    internamento-hospital.db 
    morbilidade_mortalidade_tratado.csv 
    morbilidade-hospital.db 

src/
  1_preparar.ipynb   ler CSV -> exploração -> limpeza e transformação-> exportar
  1_analise.ipynb   ler CSV -> Análise (SQL + Pandas + Matplotlib)
  2_preparar.ipynb   ler CSV -> exploração -> limpeza e transformação-> exportar
  1_analise.ipynb   ler CSV -> Análise (SQL + Pandas)
reports/        relatorio.md
dashboard/      ficheiro do Power BI (.pbix)
README.md
requirements.txt

```

## 6. Como executar o projeto

1. Instalar dependências: `pip install -r requirements.txt`
2. Preparar os dados do ficheiro 1: `src/1_preparar.ipynb`
3. Preparar os dados do ficheiro 2: `src/2_preparar.ipynb`
4. Analisar o ficheiro 1: `src/1_analise.ipynb`
5. Analisar o ficheiro 2: `src/2_analise.ipynb`
6. Dashboard: abrir `data/processed/atividade_de_internamento_tratado.csv` e `data/processed/morbilidade_mortalidade_tratado.csv` no Power BI (ver `reports/relatorio.md`).

## 7. Principais conclusões

*(Resultados reais obtidos com o dataset.)*

- **Receita total:** ≈ **20,5 milhões GBP** em ~25 meses · **5.878** clientes · **4.917** produtos.
- **Forte concentração no Reino Unido:** ≈ **85%** da receita. Os maiores mercados internacionais são **EIRE, Países Baixos, Alemanha e França** — onde está a maior oportunidade de crescimento.
- **Sazonalidade pré-Natal muito marcada:** a receita dispara de **setembro a novembro** (máximo em **novembro de 2011, ≈ 1,5 M GBP**). Reforçar stock e campanhas nesses meses.
- **Receita concentrada em poucos clientes e produtos:** os 10 maiores clientes representam uma fatia muito significativa → justifica um programa de fidelização.

## 8. Limitações do trabalho

sexo indeterminado
não tem todos os hospitais
nem todos os hospitais têm registos completos - valores em falta por coluna
diferentes numeros de hospitais nos dois ficheiros


- ~243 mil linhas sem **Customer ID** — excluídas da análise por cliente (não da global).
- Alguns "produtos" são na verdade ajustes/serviços (`Manual`, `DOTCOM POSTAGE`) — inflacionam o top de produtos; numa próxima iteração, separar serviços de produtos.
- Devoluções e cancelamentos foram **removidos** para focar nas vendas; uma análise de devoluções seria trabalho futuro.

## 9. Equipa e responsabilidades

| Bárbara Alves | Aquisição de dados; Limpeza e transformação |
| Inês Fernandes | Exploração de dados; Análise de dados |
| Margarida Oliveira | Exploração de dados; Dashboard |


---

