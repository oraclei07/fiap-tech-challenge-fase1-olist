# Tech Challenge - Fase 1 | Data Analytics FIAP

![Capa do projeto](imagens/01_capa_v2.png)

## Sobre o projeto

Este projeto foi desenvolvido como parte do **Tech Challenge - Fase 1**
da Pós-Tech em **Data Analytics da FIAP**.

O desafio utiliza o **Brazilian E-Commerce Public Dataset by Olist**,
composto por dados de pedidos realizados no Brasil entre 2016 e 2018.

O objetivo é transformar os dados transacionais em uma narrativa executiva
sobre desempenho comercial, eficiência logística e satisfação dos clientes,
resultando em recomendações baseadas nos dados.

---

## Pergunta norteadora

> **Clientes mais satisfeitos trazem maior receita?**

Essa é a pergunta de negócio que orienta o projeto.

Como o dataset da Olist não informa receita, comissão ou margem da empresa,
a hipótese foi testada utilizando o **valor transacionado em produtos**
como referência analítica.

Assim, a pergunta operacional utilizada na análise foi:

> **Clientes mais satisfeitos estão associados a pedidos de maior valor transacionado?**

Os dados não sustentaram essa hipótese operacional.

Ao avançar para outras dimensões da operação, o desempenho das entregas
apresentou uma associação consideravelmente mais relevante com as avaliações
dos clientes.

---

## Principais achados

### 1. Crescimento da operação

O volume de pedidos e o valor transacionado cresceram ao longo do período
analisado.

A correlação de Spearman entre a quantidade mensal de pedidos e o valor
transacionado foi de aproximadamente **0,97**, indicando uma associação
positiva muito forte entre essas duas medidas.

Os resultados mostram que o crescimento do valor transacionado acompanhou
principalmente o aumento do volume de pedidos.

### 2. Valor transacionado não explica satisfação

A correlação de Spearman entre a nota de satisfação e o valor do pedido
foi de aproximadamente **-0,03**.

O valor mediano dos pedidos também não apresentou crescimento à medida
que as notas de satisfação aumentaram.

Dessa forma, os dados não sustentaram a hipótese de que maior satisfação
estaria associada a maior valor transacionado.

### 3. Atraso na entrega apresenta forte associação com insatisfação

Entre os pedidos entregues sem atraso, aproximadamente **9,2%**
receberam avaliações com nota 1 ou 2.

Entre os pedidos atrasados, esse percentual aumentou para aproximadamente
**62,4%**.

Isso representa uma proporção aproximadamente **6,8 vezes maior**
de avaliações baixas entre os pedidos atrasados.

Ao analisar as diferentes faixas de atraso, foram observados os seguintes
percentuais de avaliações com nota 1 ou 2:

- **1 a 3 dias:** 32,1%
- **4 a 7 dias:** 67,5%
- **8 a 14 dias:** 80,3%
- **15 dias ou mais:** 78,3%

A correlação de Spearman entre a quantidade de dias de atraso e a nota
de satisfação, considerando apenas os pedidos atrasados, foi de
aproximadamente **-0,40**.

Os resultados indicam que a experiência do cliente piora de forma relevante
quando o atraso deixa de ser pequeno.

### 4. Estados apresentam diferentes níveis de exposição

A análise regional mostrou que atraso e avaliações baixas não se distribuem
da mesma forma entre os estados.

Entre os estados de maior volume, o **Rio de Janeiro** apresentou
aproximadamente:

- **11,9% de pedidos atrasados**
- **18,3% de avaliações baixas**

A **Bahia** também apresentou indicadores elevados, com aproximadamente:

- **11,8% de pedidos atrasados**
- **17,0% de avaliações baixas**

Os resultados indicam que a priorização regional deve considerar
conjuntamente volume de pedidos, atraso, satisfação e relevância financeira.

### 5. Sellers podem ser priorizados para investigação

Entre os sellers considerados na análise, foi identificado um grupo de
**22 sellers de atenção**.

Esse grupo concentrou:

- **6.710 pedidos**
- aproximadamente **R$ 933 mil em valor transacionado**
- cerca de **9,1% do valor analisado entre os sellers considerados**

A classificação representa um critério de priorização para investigação
e acompanhamento operacional, e não um ranking definitivo de desempenho.

---

## Recomendações executivas

### 1. Atuar na confiabilidade da entrega

Monitorar SLAs, causas de atraso e ocorrências logísticas, com atenção
especial aos atrasos superiores a quatro dias.

### 2. Priorizar estados mais críticos

Combinar volume, taxa de atraso, avaliações baixas e valor transacionado
para direcionar investigações e ações regionais.

### 3. Acompanhar sellers de atenção

Monitorar os sellers priorizados por meio de indicadores de volume,
atraso, avaliações baixas e valor transacionado.

### 4. Instituir monitoramento contínuo

Criar uma rotina periódica de acompanhamento dos principais indicadores
de experiência e desempenho operacional.

---

## Conclusão

A pergunta inicial do projeto foi refinada ao longo da análise.

> **A satisfação não apresentou associação relevante com o valor transacionado.  
> O principal sinal de insatisfação identificado foi a falha na entrega.**

O principal direcionamento identificado pelos dados é que o crescimento
da operação deve ser acompanhado pela capacidade de manter a confiabilidade
das entregas.

---

## Estrutura do repositório

```text
fiap-tech-challenge-fase1-olist/
│
├── README.md
│
├── notebooks/
│   ├── 01_exploracao_dados_olist.ipynb
│   └── 02_storytelling_olist.ipynb
│
├── imagens/
│   ├── 01_capa.png
│   ├── 02_contexto_comercial.png
│   ├── 03_satisfacao_valor.png
│   ├── 04_atraso_entrega.png
│   ├── 05_priorizacao.png
│   └── 06_recomendacoes.png
│
└── apresentacao/
    └── tech_challenge_fase1_olist.pdf
```

---

## Notebooks

### `01_exploracao_dados_olist.ipynb`

Notebook responsável pela preparação, exploração e análise dos dados.

Principais etapas:

- leitura e entendimento das bases
- verificação da qualidade dos dados
- tratamento das avaliações
- consolidação do valor dos pedidos
- análise de satisfação e valor
- análise de atrasos
- análise por estado
- análise por seller
- análise de frete
- evolução comercial

### `02_storytelling_olist.ipynb`

Notebook responsável pela consolidação dos principais resultados
e pela construção da narrativa executiva.

Principais etapas:

- crescimento da operação
- avaliação da hipótese inicial
- identificação do principal achado
- priorização por estados e sellers
- recomendações executivas

---

## Dados utilizados

O projeto utiliza dados do
**Brazilian E-Commerce Public Dataset by Olist**.

As principais bases utilizadas na análise final foram:

- `olist_customers_dataset.csv`
- `olist_order_items_dataset.csv`
- `olist_order_reviews_dataset.csv`
- `olist_orders_dataset.csv`

Os arquivos brutos não são armazenados neste repositório.

### Observação sobre valor transacionado

Neste projeto, **valor transacionado** corresponde à soma do campo `price`
dos produtos associados aos pedidos analisados.

Esse indicador foi utilizado como referência para testar a pergunta de negócio,
mas **não representa receita, comissão ou margem da Olist**.

---

## Tecnologias utilizadas

- Python
- Pandas
- Matplotlib
- Google Colab
- Google Drive
- GitHub

---

## Como reproduzir a análise

### 1. Obtenha os dados

Faça o download do **Brazilian E-Commerce Public Dataset by Olist**.

### 2. Organize os arquivos no Google Drive

Os notebooks foram desenvolvidos considerando a seguinte estrutura:

```text
Tech_Challenge_Fase1/
│
├── data/
│   └── raw/
│       ├── olist_customers_dataset.csv
│       ├── olist_order_items_dataset.csv
│       ├── olist_order_reviews_dataset.csv
│       └── olist_orders_dataset.csv
│
├── outputs/
└── graficos/
```

No Google Colab, essa pasta corresponde a:

```text
/content/drive/MyDrive/Tech_Challenge_Fase1/
```

### 3. Execute o Notebook 01

Abra:

```text
notebooks/01_exploracao_dados_olist.ipynb
```

Execute as células na ordem apresentada.

### 4. Execute o Notebook 02

Após a conclusão do Notebook 01, abra:

```text
notebooks/02_storytelling_olist.ipynb
```

O segundo notebook utiliza os resultados consolidados para organizar
os principais achados e o storytelling executivo.

---

## Entregáveis

### Repositório GitHub

Este repositório contém os códigos e a documentação utilizados no projeto.

### Apresentação executiva

**Link:** será incluído após a publicação da apresentação final.

### Vídeo executivo

**Link:** será incluído após a publicação do vídeo final.

---

## Grupo

**Grupo:** SBSJS.26

**Integrantes:**

- Ariel Felix
- Bruno Dutra
- Thieser Leal

**Data de entrega:** 03/11/2026

---

## FIAP

**Pós-Tech Data Analytics**  
**Tech Challenge - Fase 1**
