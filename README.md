
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
6. Dashboard: abrir `data/processed/atividade_de_internamento_tratado.csv` e `data/processed/morbilidade_mortalidade_tratado.csv` no Power BI (abrir `dashboard/projeto.pbix`).

## 7. Principais conclusões

- **Desigualdades regionais:** O Algarve apresenta a maior demora média de internamento (10 dias), seguido de LVT (9 dias). As restantes regiões registam 8 dias, evidenciando diferenças regionais na duração dos internamentos.
- **Evolução temporal:** A demora média aumentou de 8 para 9 dias em 2018, mantendo-se estável até 2026. Os dados não evidenciam impacto direto da pandemia (COVID-19) na demora média.
- **Especialidade:** A categoria "Outras Camas" apresenta a maior demora média, seguida da Especialidade Médica e Cirúrgica.
- **Correlação doentes/dias:** O coeficiente de Pearson de 0,93 confirma uma relação linear muito forte entre o número de doentes saídos e o total de dias de internamento, reforçando a importância de usar a demora média nas comparações.
- **Diagnóstico:** Os internamentos mais prolongados estão associados a transtornos mentais e de neurodesenvolvimento, seguidos de doenças infeciosas e parasitárias.
- **Faixa etária:** Os doentes com 65 ou mais anos apresentam a maior demora média, sugerindo maior complexidade clínica e processos de recuperação mais prolongados nos idosos.
- **Sexo:** Os doentes do sexo masculino registam uma maior duração média de internamento comparativamente ao sexo feminino.

## 8. Limitações do trabalho

- Existem 111 unidades do Serviço Nacional de Saúde (informação do INE), e no projeto só são avaliadas 88 unidades, sendo o projeto correspondente a apenas 79% da informação da totalidade dos hospitais públicos;
- Existem instituições com registos incompletos (28 registos de doentes saidos e 33 registos de dias de internamento, em falta);
- O ficheiro 2 contempla apenas 43 dos 88 hospitais presentes no ficheiro 1, representando 49% das instituições analisadas no projeto e 39% da totalidade dos hospitais públicos do SNS. 
A análise do perfil do doente está assim limitada a pouco menos de metade da rede hospitalar pública.


## 9. Equipa e responsabilidades

| Bárbara Alves | Aquisição de dados; Limpeza e transformação |
| Inês Fernandes | Exploração de dados; Análise de dados |
| Margarida Oliveira | Exploração de dados; Dashboard |


---

