# Desafio Extra — Introdução ao Data Science

**Projeto:** Análise Exploratória de Dados — Sample Superstore  
**Autor:** Daniel Quiteque  
**Dataset:** Sample Superstore

## 1. Objetivo

Este projeto realiza uma Análise Exploratória de Dados (AED) sobre o dataset público Sample Superstore. O objetivo é compreender o desempenho comercial de uma rede varejista a partir de vendas, lucro, desconto, categorias, subcategorias, segmentos de clientes, regiões e evolução temporal. O desenvolvimento foi realizado em Python utilizando Pandas, NumPy e Matplotlib.

## 2. Compreensão e tratamento dos dados

A base possui **9,994 registros e 21 colunas**. Não foram encontrados valores nulos nem linhas totalmente duplicadas. Os nomes das colunas foram padronizados para o formato `snake_case`, e `order_date` e `ship_date` foram convertidas para `datetime`.

Os possíveis outliers foram identificados pelo método IQR nas variáveis `sales`, `profit`, `quantity` e `discount`. Como valores extremos de vendas e lucro podem representar transações legítimas de grande porte, eles foram preservados nos indicadores e agrupamentos. Para reduzir distorções em gráficos, foram criadas colunas auxiliares winsorizadas somente para visualização. Dessa forma, os KPIs permanecem baseados nos valores reais.

## 3. KPIs gerais

- **Vendas totais:** US$ 2,297,200.86
- **Lucro total:** US$ 286,397.02
- **Margem de lucro:** 12.47%
- **Pedidos únicos:** 5,009
- **Clientes únicos:** 793
- **Ticket médio por pedido:** US$ 458.61

## 4. Principais análises e insights

A categoria **Technology** apresentou o maior volume de vendas, com aproximadamente US$ 836,154.03, e também o maior lucro, de aproximadamente US$ 145,454.95. **Office Supplies** apresentou lucro relevante, enquanto **Furniture**, apesar do alto volume de vendas, apresentou lucro de apenas US$ 18,451.27, indicando margem muito menor.

Na análise por subcategoria, **Tables** apresentou lucro acumulado de US$ -17,725.48 e **Bookcases** de US$ -3,472.56, ambos negativos. Isso mostra que alto faturamento não garante rentabilidade.

A relação entre desconto e lucro apresentou correlação de **-0.219**, indicando associação negativa. O agrupamento por nível de desconto mostra que descontos elevados frequentemente estão relacionados a redução de lucro e, em determinados níveis, prejuízo.

O segmento **Consumer** liderou as vendas, com aproximadamente US$ 1,161,401.34, seguido por Corporate e Home Office. Regionalmente, a região **West** apresentou o melhor desempenho, com vendas de US$ 725,457.82 e lucro de US$ 108,418.45.

A análise temporal mostrou crescimento ao longo do período. Em 2017, as vendas atingiram aproximadamente US$ 733,215.26, o maior valor anual da base, acompanhadas de lucro de US$ 93,439.27.

## 5. Decisões tomadas

1. Preservação das transações reais mesmo quando classificadas como outliers pelo IQR.
2. Winsorização utilizada somente em visualizações que poderiam ser dominadas por valores extremos.
3. Conversão de datas para permitir análise temporal.
4. Criação de `year`, `month`, `profit_margin` e `shipping_days` como variáveis derivadas.
5. Uso de filtros, ordenações e `GroupBy` para sintetizar o desempenho comercial.
6. Análise conjunta de vendas e lucro para evitar conclusões baseadas apenas em faturamento.

## 6. Estrutura do projeto

- `desafio_data_science_superstore.ipynb`: notebook principal.
- `Sample - Superstore.csv`: dataset original.
- `graficos/`: visualizações geradas.
- `metricas.json`: KPIs gerais.
- `relatorio_outliers.csv`: análise de possíveis outliers.
- `resumo_categoria.csv`: vendas e lucro por categoria.
- `resumo_subcategoria.csv`: análise por subcategoria.
- `resumo_segmento.csv`: análise por segmento.
- `resumo_regiao.csv`: análise regional.
- `resumo_estado.csv`: resultados por estado.
- `resumo_desconto.csv`: impacto dos descontos.
- `resumo_anual.csv`: evolução anual.
- `requirements.txt`: dependências do projeto.

## 7. Como executar

1. Instale Python 3.
2. Instale as dependências com `pip install -r requirements.txt`.
3. Abra `desafio_data_science_superstore.ipynb` no Jupyter Notebook, JupyterLab ou Google Colab.
4. Mantenha `Sample - Superstore.csv` na mesma pasta do notebook.
5. Execute todas as células em sequência.

## 8. Conclusão

A análise demonstra que a empresa apresenta desempenho geral lucrativo, porém existem diferenças importantes entre categorias, subcategorias, segmentos e regiões. O principal risco identificado está na rentabilidade de determinados produtos e no impacto dos descontos. A categoria Furniture exige atenção especial, principalmente pelas perdas em Tables e Bookcases. Ao mesmo tempo, Technology e Office Supplies demonstram forte contribuição para o resultado.

O projeto evidencia a importância da Análise Exploratória de Dados na transformação de registros transacionais em informações úteis para tomada de decisão. Como evolução futura, os resultados podem ser integrados a um dashboard interativo no Looker Studio ou usados como base para modelos preditivos.
