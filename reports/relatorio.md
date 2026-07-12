# Relatório de Análise — Internamentos Hospitalares em Portugal

**Pergunta de negócio:** Como varia o tempo de internamento hospitalar em Portugal em função da região, periodo temporal, especialidade, diagnóstico, faixa etária e sexo?

**Dados:** 
- Ficheiro 1 (Atividade de Internamento Hospitalar): 88 hospitais de 5 regiões
- Ficheiro 2 (Morbilidade e Mortalidade Hospitalar): 43 hospitais de 5 regiões


## 1. Visão Geral
- **Período analisado:** janeiro de 2015 a março de 2026
- **Hospitais cobertos:** 88 instituições públicas do SNS
- **Demora média nacional:** 9 dias


## 2. Região
O Algarve apresenta a maior demora média de internamento (10 dias), seguido 
de Lisboa e Vale do Tejo (9 dias). As restantes regiões registam uma média de 8 dias, evidenciando desigualdades regionais na duração dos internamentos.


## 3. Evolução Temporal
A demora média aumentou gradualmente ao longo dos anos avaliados. Apesar de 2020 registar o maior aumento anual do período, não é possível atribuir esta variação exclusivamente ao impacto da pandemia COVID-19. O valor de 2026 não é comparável pois contempla apenas 3 meses de registos.

## 4. Especialidade
A categoria "Outras Camas" apresenta a maior demora média, seguida da Especialidade Médica e da Especialidade Cirúrgica. Este resultado pode ser justificado pela natureza dos internamentos que engloba (reabilitação, convalescença, cuidados paliativos, etc), que implicam estadias mais prolongadas.


## 5. Diagnóstico
Os internamentos mais prolongados estão associados a transtornos mentais, 
comportamentais e de neurodesenvolvimento, seguidos de doenças infeciosas e parasitárias.


## 6. Faixa Etária
A faixa etária dos 65-120 anos apresenta a maior demora média de internamento, seguida da faixa dos 45-65 anos. As restantes faixas etárias registam demoras médias de 4-5 dias, sugerindo que 
a complexidade clínica aumenta com a idade.


## 7. Sexo
Os doentes do sexo masculino registam uma maior duração média de internamento comparativamente ao sexo feminino. O grupo "Indeterminado" foi excluído desta comparação por representar apenas 21 internamentos.


## 8. Correlação doentes saidos - dias de internamento
A análise de correlação entre o número de doentes saídos e o total de dias de internamento revelou um coeficiente de Pearson de 0,93, indicando uma relação linear forte e positiva entre as duas variáveis, reforçando a importância de usar a demora média nas comparações.


## Recomendações
1. Investigar os fatores que justificam a maior demora média no Algarve, nomeadamente a disponibilidade de especialidades e a complexidade dos casos tratados.
2. Reforçar os recursos na área de saúde mental, dado que os internamentos psiquiátricos apresentam a maior demora média.
3. Adaptar a capacidade hospitalar ao envelhecimento da população, uma vez que os idosos representam os internamentos mais longos.


## Limitações
- O ficheiro 1 cobre 88 das 111 instituições hospitalares públicas do SNS (79% 
da rede pública).
- O ficheiro 2 contempla apenas 43 dos 88 hospitais do ficheiro 1 (49%), 
representando 39% da totalidade dos hospitais públicos do SNS. A análise do perfil 
do doente está assim limitada a menos de metade da rede hospitalar pública portuguesa.
- Os dados excluem hospitais privados e as regiões autónomas dos Açores e Madeira.