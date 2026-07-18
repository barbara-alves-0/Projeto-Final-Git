
# Analysis of Hospital Admissions in Portugal

Final Project - Data Science & Analytics · CESAE Digital

Pipeline: data → exploration → cleaning and transformation → analysis → dashboard.


## 1. Project Context

Analysis of Hospital Admissions in Portuguese Hospitals, from **January 2015 to March 2026.**
The objective of this study is to evaluate variations in the length of hospital stays based on hospital records and the information associated with each admission.

## 2. Business Question

**How does the length of hospital stay in Portugal vary across regions, over time, and according to medical specialty, diagnosis, age group, and sex?**

Dashboard user stories:
- *As a hospital manager, I want to compare the average length of hospital stay in my health region compared with the other health regions.*
- *As an ACSS planning officer, I want to analyse the evolution of hospital beddays over time (2015–2026) to understand the impact of events such as the COVID-19 pandemic on hospital capacity.*
- *As a clinical manager, I want to analyse the average length of stay by diagnosis, age group, sex, and medical specialty, in order to identify the patient profiles associated with longer hospital stays.*

## 3. Data Source

**File 1: Hospitalisation Activity**
- **Source:** ACSS Dados.gov.pt -  https://dados.gov.pt/pages/datasets/atividade-de-internamento-hospitalar-2
- **File:** `atividade-de-internamento-hospitalar_fich1.csv` 
- **Size:** 17617 lines · 7 columns (Periodo, Região, Instituição, Localização Geográfica, Tipo de Especialidade, Doentes saidos, Dias de Internamento)

**File 2: Hospital Morbidity and Mortality**
- **Source:** SNS Transparência -  https://transparencia.sns.gov.pt/explore/assets/morbilidade_mortalidade_hospit/
- **File:** `morbilidade_mortalidade_hospit_fich2.csv` 
- **Size:** 524407 lines · 11 columns (Período, Região, Instituição, Código Capítulo Diagnóstico Principal, Descrição Capítulo Diagnóstico Principal, Faixa Etária, Sexo, Internamentos, Dias de Internamento, Ambulatório,Óbitos)

## 4. Tecnologies used

- **Data Analysis Language:** Python (pandas, matplotlib)
- **Database:** SQLite
- **Dashboard:** Power BI
- **Versions Control:** Git + GitHub

## 4.1 Use of Artificial Intelligence
Claude AI (Anthropic) was used as support throughout the development of the project, namely for:
- Clarifying technical concepts;
- Discussing and validating methodological decisions;
- Reviewing and simplifying Python/SQL code.
All final analytical decisions, interpretation of results, and implementation were the responsibility of the project's authors.

## 5. Repository Structure
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
  1_preparar.ipynb   Load CSV → Data exploration → Data cleaning and transformation → Export processed data

  1_analise.ipynb   Load CSV → Data analysis (SQL + Pandas + Matplotlib)

  2_preparar.ipynb   Load CSV → Data exploration → Data cleaning and transformation → Export processed data

  2_analise.ipynb   Load CSV → Data analysis (SQL + Pandas)

reports/  
  relatorio.md

dashboard/  
  Power BI file (.pbix)

README.md

requirements.txt

```
## 6. Project Execution

To execute the project, follow the steps below:

1. Install the required dependencies using: `pip install -r requirements.txt`
2. Prepare the dataset from the first file by running: `src/1_preparar.ipynb`
3. Prepare the dataset from the second file by running: `src/2_preparar.ipynb`
4. Perform the analysis of the first dataset using: `src/1_analise.ipynb`
5. Perform the analysis of the second dataset using: `src/2_analise.ipynb`
6. Visualisation dashboard: Import the processed datasets (`atividade_de_internamento_tratado.csv` and `morbilidade_mortalidade_tratado.csv`) from the `data/processed/` directory into Power BI. The final dashboard can be accessed by opening `dashboard/projeto.pbix`.

## 7. Key Findings

- **Regional inequalities:** The Algarve region presents the highest average length of hospital stay (10 days), followed by "Lisboa and Vale do Tejo" (LVT) (9 days). The remaining regions record an average of 8 days, highlighting regional differences in hospitalisation duration.

- **Temporal evolution:** The average length of stay gradually increased throughout the years. Although 2020 recorded the largest annual increase of the period, this variation cannot be exclusively attributed to the impact of the COVID-19 pandemic. The 2026 value is not comparable as it only covers 3 months of records.

- **Medical specialty:** The "Other Beds" category presents the highest average length of stay, followed by Medical and Surgical specialties.

- **Relationship between discharged patients and inpatient days:** The Pearson correlation coefficient of 0.93 confirms a very strong linear relationship between the number of discharged patients and the total number of inpatient days, reinforcing the importance of considering average length of stay when comparing hospital activity.

- **Diagnosis:** The longest hospital stays are associated with mental and neurodevelopmental disorders, followed by infectious and parasitic diseases.

- **Age group:** Patients aged 65 years or older present the highest average length of stay, suggesting greater clinical complexity and longer recovery processes among older patients.

- **Sex:** Male patients present a higher average length of hospital stay compared with female patients.


## 8. Project Limitations

- The Portuguese National Health Service (SNS) comprises 111 healthcare units (according to INE data), while this project analyses only 88 units. Therefore, the analysis covers approximately 79% of the available information regarding the total number of public hospitals.

- Some institutions contain incomplete records, including 28 missing records for discharged patients and 33 missing records for inpatient days.

- The second dataset includes only 43 of the 88 hospitals present in the first dataset, representing 49% of the institutions analysed in the project and 39% of the total number of public hospitals within the SNS. Consequently, the analysis of patient profiles is limited to slightly less than half of the public hospital network.

- Both datasets don't include private institutions nor institutions from autonomous regions from Açores and Madeira.

## 9. Team and Responsibilities

| Bárbara Alves | Data acquisition; Data cleaning and transformation |
| Inês Fernandes | Data exploration; Data analysis |
| Margarida Oliveira | Data exploration; Dashboard development |

---

