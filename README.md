
# Análise Histórica e Preditiva dos Jogos Olímpicos (1896–2022)

O banco de dados utilizado neste projeto declara ser "uma tentativa de criar conjuntos de dados de eventos olímpicos atualizados (de 1896 a 2022)". Portanto, todos os insights fornecidos nesta análise pressupõem a fidedignidade das informações, e a confiabilidade dos resultados está diretamente ligada à qualidade da fonte de dados.

---

## Objetivo

Este projeto tem como objetivo analisar os dados sobre os Jogos Olímpicos, disponibilizados em base pública, buscando traçar um perfil geral dos atletas olímpicos, identificar os países com melhor desempenho ao longo das edições e apresentar um panorama da participação do Brasil nos Jogos Olímpicos.

---

## 1. Coleta de Dados

Foi utilizada a fonte pública *Historical Data from the Olympics*, acessada via BigQuery.

- **Origem**: Plataforma [Base dos Dados](https://basedosdados.org/dataset/2a543ad8-3cdb-4047-9498-efe7fb8ed697?table=df7cf198-4889-4baf-bb77-4e0e28eb90ca)  
- **Fonte original**: Olympic Historical  
- **Acesso**: BigQuery (via SQL)  
- **Tipo de dados**: Estruturados (tabelas padronizadas)  
- **Período abrangido**: 1896 – 2022  

**Tabelas utilizadas**:  
`athlete_bio`, `athlete_event_result`, `game`, `game_medal_tally`

---

## 2. Análise Exploratória

### SQL:
- Seleção de colunas e análise inicial dos dados diretamente no BigQuery.

### Python:
- Geração de gráficos (histograma, mapa de calor, boxplot, linhas, barras)
- Análise de distribuição e correlação entre altura, peso e idade
- Detecção de outliers físicos por tipo de esporte
- Cálculo das médias físicas por edição
- Análise do quadro de medalhas por país

**Principais achados:**
- Atletas com altura entre 170–180 cm, peso entre 60–80 kg e idade entre 22–27 anos são os mais recorrentes.
- Há forte correlação entre altura e peso, e correlação fraca com idade.
- Algumas modalidades, como basquete, concentram atletas mais altos e pesados.
- Diferença de idade entre gêneros varia por esporte: por exemplo, no boxe, mulheres são mais velhas que homens.
- Estados Unidos dominam o ranking histórico de medalhas.

---

## 3. Limpeza e Preparação dos Dados

A limpeza foi realizada em Python (Google Colab), com os seguintes passos:

- Remoção de duplicatas
- Criação das colunas: `ano`, `idade`, `tipo_edicao`
- Padronização de tipos e formatos
- Tratamento de valores ausentes em colunas críticas
- Padronização dos nomes das colunas
- Criação de três bases: uma de atletas enxuta para análises, uma de atletas completa para cálculo de medalhas e uma com informação dos países

---

## 4. Visualização de Dados (Looker Studio)


As visualizações foram criadas no **Looker Studio**, visando uma comunicação clara e interativa dos achados.
**Link para o dashboard:** https://lookerstudio.google.com/reporting/17567be0-251b-4174-bd62-6591a05824b3

**Gráficos incluídos**:
- Proporção de Gênero dos Atletas
- Proporção de Esportes Individuais x Coletivos
- Distribuição de Atletas por Esporte
- Quadro de Medalhas por Atleta e País
- Evolução do Número de Atletas ao Longo dos Anos
- Ranking de Desempenho por País
- Participação Histórica dos Países

---

## 5. Análise Preditiva

Para enriquecer a análise, foram criados dois modelos preditivos:

### Classificação: Previsão de medalhas por perfil de atleta

Foi treinado um modelo de regressão logística para prever a chance de um atleta conquistar medalha, com base em:

- Características físicas: altura, peso, idade
- Sexo, país, tipo de esporte

**Resultados**:
- Acurácia: 66%
- Precisão: 24%
- Recall: 65%

**Aplicação**: identifica perfis com maior probabilidade de sucesso, útil para programas de desenvolvimento esportivo.

---

### Regressão Linear: Previsão da idade média em edições futuras

Baseando-se nas médias históricas por edição, foi treinado um modelo para prever a idade média dos atletas para 2028, 2032 e 2036.

**Aplicação**: auxilia na análise de tendências demográficas e na preparação de atletas por faixa etária.

---

## 6. Considerações Finais

A análise revela a concentração do desempenho olímpico em países com histórico esportivo consolidado, como Estados Unidos, Rússia e China. O Brasil, embora apresente crescimento, ainda está distante do topo e precisa de estratégias que ampliem o investimento em modalidades com tradição em medalhas, como judô, vôlei e vela.

---

##  7. Sugestões Futuras

- Analisar o impacto de investimentos públicos e privados em desempenho olímpico
- Estudar influências culturais e políticas sobre modalidades praticadas por país
- Estender o estudo para os Jogos Paralímpicos

---

## Tecnologias Utilizadas

- **SQL** (BigQuery)
- **Python** (pandas, seaborn, matplotlib, sklearn, numpy)
- **Google Colab**
- **Looker Studio**
- **GitHub**

---

## Autora

**Vanessa Costa**  
Projeto desenvolvido como parte da Formação de Analista de Dados da EBAC  
Abril de 2025