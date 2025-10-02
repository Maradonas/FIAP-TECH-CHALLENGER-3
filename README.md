
# 📊 Tech Challenge 3 – ETL e Análise do PNAD-COVID 19 (IBGE)

## 📖 Contexto

A pandemia da COVID-19 trouxe ao Brasil grandes desafios sociais, econômicos e de saúde pública. O **PNAD-COVID 19**, realizado pelo IBGE, foi uma pesquisa domiciliar mensal que coletou dados sobre sintomas, impacto econômico e comportamento da população durante a crise sanitária.

O desafio deste projeto foi **organizar essa base extensa em um processo de ETL em nuvem**, estruturando os dados em camadas e gerando **insights estratégicos** para auxiliar hospitais e gestores em caso de novos surtos.

---

## 🧩 Problema Proposto

O **Head de Dados** da instituição orientou que o PNAD-COVID fosse a base central do estudo, destacando:

- **Limite de até 20 variáveis** da pesquisa.
- **Uso de 3 meses de dados**.
- Foco em 3 grandes dimensões:
  - **Sintomas clínicos da população**
  - **Comportamento social durante a pandemia**
  - **Características econômicas e demográficas**

O objetivo final é **apoiar hospitais** na definição de **planos de contingência e estratégias de resposta** em cenários de crise.

---

## 🏗️ Arquitetura da Solução

O fluxo de dados foi estruturado em camadas, utilizando **AWS S3 como Data Lake** e **Power BI como ferramenta de consumo**.

![Arquitetura do Projeto](ArquiteturaNuvem.drawio.png)

### Etapas do Processo

1. **IBGE – Base de Dados**

   - Fonte oficial dos microdados do PNAD-COVID 19.
   - Uso do dicionário de perguntas para selecionar variáveis relevantes.
2. **Camada Bronze (Raw Data)**

   - Extração dos dados em **formato bruto**.
   - Salvamento direto em buckets no S3.
3. **Camada Prata (Tratamento e Padronização)**

   - Limpeza e padronização dos datasets.
   - Filtro para manter apenas **3 meses de pesquisa**.
   - Normalização de colunas e tratamento de valores nulos.
4. **Camada Ouro (Agregação e KPIs)**

   - Aplicação de regras de negócio.
   - Criação de métricas e KPIs relevantes.
   - Simplificação da base para consumo analítico.
5. **Consumo dos Dados (Power BI)**

   - Conexão direta à Camada Ouro.
   - Dashboards para análise de sintomas, demografia, renda e comportamento.
   - Geração de insights estratégicos para tomada de decisão.

---

## 🔄 Processo ETL em Detalhes

- **Extract:** Coleta dos arquivos parquet fornecidos pelo IBGE.
- **Transform:** Limpeza, padronização e seleção das variáveis-chave.
- **Load:** Armazenamento em buckets S3 organizados em Bronze, Prata e Ouro.

Exemplos de transformações realizadas:

- Agrupamento de sintomas clínicos por indivíduo.
- Criação de campos derivados (faixa etária, grupos regionais).
- Indicadores econômicos simplificados (emprego, renda, informalidade).

---

## 📊 Análises e Gráficos Produzidos

1. **Sintomas mais frequentes** – distribuição por sexo e faixa etária.
2. **Mapa geográfico** – estados mais impactados.
3. **Impacto econômico** – perda de renda, aumento do desemprego.
4. **Comportamento social** – percentual em isolamento e acesso a serviços de saúde.

Esses gráficos permitem identificar:

- Regiões mais vulneráveis.
- Grupos populacionais de maior risco.
- Efeitos econômicos associados ao avanço da doença.

---

## 🎯 Recomendações para Hospitais

Com base nas análises:

- Monitorar **sintomas-chave** para triagem precoce.
- Planejar **capacidade hospitalar** conforme padrões regionais.
- Dar atenção especial a **grupos de baixa renda** e trabalhadores informais.
- Criar **campanhas de comunicação direcionadas** às faixas mais afetadas.

---

## 🛠️ Ferramentas Utilizadas

- **Python (Pandas, Numpy, Matplotlib, Seaborn, Plotly)**
- **Amazon S3 (Data Lake)**
- **Jupyter Notebook**
- **Power BI**

---

## 📌 Conclusão

Este projeto demonstrou como o **PNAD-COVID 19** pode ser transformado em uma base estratégica para análises de saúde pública.

A arquitetura em camadas (Bronze, Prata e Ouro) permitiu estruturar e simplificar os dados, enquanto o consumo via **Power BI** gerou insights claros e objetivos para **tomada de decisão hospitalar em futuros surtos de COVID-19**.
