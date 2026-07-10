
# Análise de Internamento Hospitalar em Portugal

> Projeto Final — Data Science & Analytics · CESAE Digital
> Pipelina: dados → exploração → limpeza e transformação → SQL → análise → dashboard.

## 1. Contexto do projeto

Análise de internamentos de Hospitais Portugueses, entre **janeiro de 2015 e março de 2026**.
O objetivo é avaliar como varia a duração dos internamentos, a partir dos registos hospitalares das informações inerentes ao internamento.

## 2. Pergunta de negócio

**Como varia o tempo de internamento hospitalar em Portugal em função da região, periodo temporal, especialidade, diagnóstico, faixa etária e sexo?**

User stories do dashboard:
- *Como gestor de uma unidade hospitalar, quero ver a demora média de internamento da minha região comparada com as restantes regiões de saúde, para identificar se o meu hospital está acima ou abaixo da média nacional.*
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
  raw/         online_retail_II.xlsx     (descarregar — ver ponto 6; não vai para o Git)
  processed/   retail_limpo.csv, retail.db (gerados pelo passo 1)
src/
  1_preparar.py   ler Excel -> SQL -> limpeza -> exportar
  2_analise.py    análise + gráficos
reports/        gráficos (.png) + relatorio.md
dashboard/      ficheiro do Power BI (.pbix)
README.md
requirements.txt
.gitignore
```

## 6. Como executar o projeto

1. Descarregar os dados (Kaggle ou UCI) e colocar `online_retail_II.xlsx` em `data/raw/`.
2. Instalar dependências: `pip install -r requirements.txt`
3. Preparar os dados: `python src/1_preparar.py`
4. Analisar: `python src/2_analise.py`
5. Dashboard: abrir `data/processed/retail_limpo.csv` no Power BI (ver `reports/relatorio.md`).

## 7. Principais conclusões

*(Resultados reais obtidos com o dataset.)*

- **Receita total:** ≈ **20,5 milhões GBP** em ~25 meses · **5.878** clientes · **4.917** produtos.
- **Forte concentração no Reino Unido:** ≈ **85%** da receita. Os maiores mercados internacionais são **EIRE, Países Baixos, Alemanha e França** — onde está a maior oportunidade de crescimento.
- **Sazonalidade pré-Natal muito marcada:** a receita dispara de **setembro a novembro** (máximo em **novembro de 2011, ≈ 1,5 M GBP**). Reforçar stock e campanhas nesses meses.
- **Receita concentrada em poucos clientes e produtos:** os 10 maiores clientes representam uma fatia muito significativa → justifica um programa de fidelização.

## 8. Limitações do trabalho

- ~243 mil linhas sem **Customer ID** — excluídas da análise por cliente (não da global).
- Alguns "produtos" são na verdade ajustes/serviços (`Manual`, `DOTCOM POSTAGE`) — inflacionam o top de produtos; numa próxima iteração, separar serviços de produtos.
- Devoluções e cancelamentos foram **removidos** para focar nas vendas; uma análise de devoluções seria trabalho futuro.

## 9. Equipa e responsabilidades

| Elemento | Responsabilidades |
|---|---|
| _(exemplo)_ | Coordenação, preparação de dados |
| _(exemplo)_ | Análise |
| _(exemplo)_ | Dashboard e relatório |

---

