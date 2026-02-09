# 🛒 Projeto ETL - Análise de Vendas de Supermercado

![Status](https://img.shields.io/badge/Status-Concluído-success.svg)
![Python](https://img.shields.io/badge/Python-3.12-blue.svg)
![Pandas](https://img.shields.io/badge/Pandas-2.3.2-green.svg)
![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)

##  Arquitetura do Pipeline
<p align="center">
  <img src="imagens/arquitetura_projeto.png" alt="Arquitetura do Projeto" width="850">
</p>

##  Objetivo do Projeto

O objetivo central deste projeto é transformar dados brutos de transações de uma rede de supermercados em uma base de dados inteligente e higienizada. 

Muitas vezes, dados transacionais vêm em formatos brutos (como strings ou formatos internacionais) que dificultam a análise imediata. Este projeto resolve esse problema ao:

1.  **Padronizar** a comunicação (tradução para PT-BR).
2.  **Enriquecer** os dados com colunas temporais (períodos, quinzenas, dias úteis).
3.  **Garantir a Integridade** através de uma auditoria de qualidade (limpeza de duplicatas e nulos).

O resultado final é um dataset pronto para alimentar Dashboards de BI, permitindo que gestores tomem decisões baseadas em fatos, como "qual o melhor horário para promoções relâmpago".

---

##  Etapas de Desenvolvimento (Workflow)

O projeto foi dividido em três marcos principais para garantir a organização e a reprodutibilidade da análise:

### Fase 1: Auditoria e Qualidade (Data Discovery)
Realizada no notebook `Final.ipynb`, esta etapa focou em entender a "saúde" dos dados:

* **Análise Exploratória Inicial (EDA):** Verificação de tipos de dados e estatísticas descritivas.
* **Sanitização:** Localização de valores ausentes (NaN) e remoção de registros duplicados que poderiam inflar os resultados financeiros.
* **Check de Consistência:** Verificação de outliers e inconsistências em colunas categóricas.

### Fase 2: Transformação e Feature Engineering (Data Wrangling)
No notebook `Tratamento.ipynb`, foi aplicado as regras de negócio para gerar valor:

* **Normalização de Schema:** Tradução completa de colunas e categorias para facilitar o uso por times locais.
* **Criação de Inteligência Temporal:** Desenvolvimento de funções em Python para extrair períodos do dia e classificar dias da semana.
* **Otimização de Tipagem:** Conversão de formatos de data e hora para objetos `datetime`, permitindo cálculos de séries temporais.

### Fase 3: Exportação e Preparação para Visualização

* **Geração do Dataset de Saída:** Consolidação de todas as transformações em um único arquivo `supermarket_sales_tratado.csv`.
* **Preparação para o Dashboard:** Organização dos dados para que ferramentas de visualização consigam ler as métricas de tempo sem necessidade de novos tratamentos.

---

##  Principais Métricas Criadas (KPIs)

O Dashboard visa fornecer uma visão 360º da saúde financeira e operacional, permitindo identificar:

* **Perfil de Consumo e Faturamento:** 
Dominância do Perfil Econômico: O perfil "Econômico" representa a maior fatia das vendas (440 unidades), sugerindo que a estratégia de preço baixo ou produtos de entrada é o motor do volume da empresa.

Potencial do Segmento Premium: Apesar de ter o menor volume (60), o segmento "Premium" é uma oportunidade de aumento de margem se houver conversão dos clientes "Padrão" (260).

Ticket Médio Estável: O ticket médio de R$ 322,97 serve como métrica de controle para futuras campanhas de upselling.

* **Comportamento Temporal de Vendas:** 
Pico Semanal aos Sábados: O maior volume de vendas ocorre no Sábado (164), seguido pela Terça-feira (158). Isso indica uma oportunidade para campanhas de marketing direcionadas para o final de semana.

Sazonalidade Quinzenal: No gráfico de faturamento por quinzena, nota-se uma queda significativa na 2ª quinzena de fevereiro (40 Mil) em comparação à 2ª quinzena de janeiro (64 Mil), o que pode estar relacionado ao período de Carnaval ou menor número de dias úteis.

* **Satisfação e Experiência do Cliente:** A
lerta de Insatisfação: O gráfico de "Volume de Vendas por Avaliação" mostra que o grupo "Insatisfeito" (174) é relevante. Embora a média de avaliação seja 7, existe um volume considerável de clientes "Neutros" (345) que podem ser convertidos em promotores com melhorias no pós-venda.

Conversão de Feedback: A soma de clientes "Satisfeitos" e "Muito Satisfeitos" (481) supera os insatisfeitos, mas a margem bruta média de 4,76 sugere que o custo de aquisição ou operação pode estar alto para manter esse nível de serviço.

##  Resultado Final da Análise
<p align="center">
  <img src="imagens/Dashboard.png" alt="Dashboard do Projeto" width="850">
</p>
