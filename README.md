# 📈 Projeto de Regressão Linear para Previsão de Preços de Imóveis

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.0.2-orange)
![Pandas](https://img.shields.io/badge/Pandas-1.4.0-red)
![Seaborn](https://img.shields.io/badge/Seaborn-0.11.2-lightgrey)

Modelo preditivo para estimativa de preços de imóveis nos EUA baseado em características socioeconômicas e demográficas.

## 🏠 Objetivo do Projeto

Desenvolver um modelo de machine learning para prever valores de imóveis residenciais com base em:
- Indicadores econômicos da região
- Características físicas das propriedades
- Dados demográficos locais

**Aplicações práticas:**
- 💰 Avaliação imobiliária automatizada
- 🔍 Identificação de oportunidades de investimento
- 📊 Análise de mercado para corretores
- 🏦 Suporte a decisões de financiamento bancário

## 📁 Dataset

Dados de propriedades americanas contendo:

| Variável | Descrição | Tipo | Problemas Identificados |
|----------|-----------|------|-------------------------|
| renda_area | Renda média da região | float64 | Outliers |
| idade_imovel | Idade média do imóvel | float64 | - |
| num_quartos | Número médio de cômodos | float64 | Valores extremos |
| num_banheiros | Número médio de banheiros | float64 | - |
| populacao | População da área | float64 | Outliers |
| Price | Preço do imóvel (target) | float64 | Distribuição assimétrica |

## 🔍 Análise Exploratória

### Principais Insights

1. **Distribuição de Preços:**
   - Concentração entre \$500k-\$1.5M
   - Cauda longa até \$2.5M (imóveis de luxo)

2. **Correlações:**
   - Renda da área: maior correlação com preço (0.64)
   - N° banheiros: menor correlação (0.17)

3. **Outliers:**
   - Identificados em renda e população
   - Valores extremos em número de quartos

## 🛠️ Pré-processamento

1. **Limpeza:**
   - Remoção de endereços (dado não estruturado)
   - Renomeação de colunas para padrão snake_case

2. **Transformação:**
   - Normalização com StandardScaler
   - Divisão 70/30 (treino/teste)

3. **Engenharia de Features:**
   - Análise de correlação
   - Verificação de multicolinearidade

## 🤖 Modelagem

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()
model.fit(X_train, y_train)
```
## 📊 Métricas de Performance

| Métrica       | Valor     | Interpretação                     |
|---------------|-----------|-----------------------------------|
| **R²**        | 92.1%     | Excelente poder explicativo       |
| **MAE**       | $82,150   | Erro médio absoluto               |
| **MAPE**      | 6.8%      | Baixo erro percentual             |

## 📈 Gráficos Analíticos

### 1. Distribuição das Variáveis
![Boxplot](https://i.imgur.com/boxplot_distribuicao.png)
*Distribuição das características dos imóveis com identificação de outliers*

### 2. Histogramas das Principais Variáveis
![Histogramas](https://i.imgur.com/histogramas_renda_populacao_preco.png)
*Distribuição de renda, população e preços dos imóveis*

### 3. Matriz de Correlação
![Heatmap](https://i.imgur.com/heatmap_correlacao.png)
*Correlação entre todas as variáveis do dataset*

### 4. Previsões vs Valores Reais
![Scatter Plot](https://i.imgur.com/scatter_previsoes_reais.png)
*Comparação entre valores previstos e reais com linha de perfeita previsão*

## 🔍 Resultados: Impacto das Variáveis

| Variável        | Coeficiente | Interpretação                     |
|-----------------|-------------|-----------------------------------|
| **renda_area**  | $230,464    | +1 unidade → +$230k no preço      |
| **idade_imovel**| $164,159    | Cada ano → +$164k                 |
| **populacao**   | $151,019    | +1 habitante → +$151k             |
| **num_quartos** | $120,514    | +1 quarto → +$120k                |
| **num_banheiros**| $2,913     | +1 banheiro → +$2.9k              |

## 📌 Conclusões

### 💡 Insights Chave
- **Renda da área** é o fator mais determinante nos preços
- **Idade do imóvel** apresenta impacto não-linear
- **Número de banheiros** tem influência significativamente menor que outras variáveis

### 🚀 Próximos Passos
1. Testar modelos alternativos:
   - Random Forest
   - XGBoost
2. Refinar tratamento de outliers para melhorar precisão
3. Desenvolver API REST para predições em tempo real
4. Implementar dashboard de monitoramento contínuo
