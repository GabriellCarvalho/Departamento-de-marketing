# Departamento de Marketing – Segmentação de Clientes de Cartão de Crédito

Este repositório contém um estudo de **segmentação de clientes de cartão de crédito** usando o dataset **Credit Card Dataset for Clustering (CC GENERAL)**, com foco em gerar insights acionáveis para um departamento de marketing.

---

## Objetivo do projeto

- Criar **clusters de clientes** a partir de variáveis comportamentais de uso do cartão (gastos, frequência, pagamentos, limite de crédito etc.).
- Identificar perfis distintos de clientes que possam orientar campanhas, retenção, upsell e gestão de risco de forma personalizada.

---

## Dataset

| Campo | Descrição |
|---|---|
| **Nome** | Credit Card Dataset for Clustering (CC GENERAL) |
| **Observações** | ~9.000 clientes ativos de cartão de crédito |
| **Período** | Últimos 6 meses de uso do cartão |
| **Variáveis** | 18 variáveis comportamentais + identificador `CUST_ID` |

### Principais variáveis

- `BALANCE` – Saldo disponível para compras
- `PURCHASES` – Total de compras realizadas
- `ONEOFF_PURCHASES` – Maior compra realizada de uma só vez
- `INSTALLMENTS_PURCHASES` – Compras parceladas
- `CASH_ADVANCE` – Valor de saque/adiantamento em dinheiro
- `PURCHASES_FREQUENCY` – Frequência de compras (0 a 1)
- `CASH_ADVANCE_FREQUENCY` – Frequência de saques (0 a 1)
- `CREDIT_LIMIT` – Limite do cartão de crédito
- `PAYMENTS` – Total pago pelo cliente
- `MINIMUM_PAYMENTS` – Pagamento mínimo realizado
- `PRCFULLPAYMENT` – Percentual de pagamento integral da fatura
- `TENURE` – Tempo de uso do cartão (meses)

> Link do dataset: [Kaggle – Credit Card Dataset for Clustering](https://www.kaggle.com/datasets/arjunbhasin2013/ccdata)

---

## Metodologia

### 1. Exploração inicial dos dados
- Leitura do arquivo `CC GENERAL.csv`
- Verificação de tipos, resumo estatístico e análise das distribuições de cada variável

### 2. Tratamento e preparação dos dados
- Tratamento de valores ausentes (principalmente em `MINIMUM_PAYMENTS`)
- Análise e tratamento de outliers
- Criação de variáveis derivadas relevantes para o negócio

### 3. Preparação para clustering
- Seleção das variáveis mais informativas para a segmentação
- Padronização das features com `StandardScaler`
- Redução de dimensionalidade com **PCA**

### 4. Modelagem de clusters
- Aplicação do algoritmo **K-Means**
- Definição do número ideal de clusters com Elbow Method e Silhouette Score

### 5. Interpretação dos segmentos
- Análise das médias de cada variável por cluster
- Criação de rótulos de negócio para cada segmento identificado

---

## Segmentos identificados

### Grupo 0 — VIP / Prime

> Clientes de alto valor com excelente histórico de pagamento.

| Indicador | Valor |
|---|---|
| Limite do cartão (`CREDIT_LIMIT`) | R$ 15.570 |
| Pagamento integral da fatura (`PRCFULLPAYMENT`) | 47% |

**Estratégia de marketing:**
- Aumentar o limite do cartão como recompensa pela adimplência
- Incentivar o hábito de compras com programas de fidelidade, cashback e benefícios exclusivos
- Ofertas de produtos premium (seguro viagem, sala VIP, cartão black)

---

### Grupo 3 — Conservadores / Cuidadosos

> Clientes cautelosos financeiramente, pouco rentistas para o banco, mas com bom comportamento de pagamento.

| Indicador | Valor |
|---|---|
| Saldo em conta (`BALANCE`) | R$ 104 |
| Saque do limite (`CASH_ADVANCE`) | R$ 302 |
| Pagamento integral da fatura (`PRCFULLPAYMENT`) | 23% |

**Estratégia de marketing:**
- Estimular o uso do cartão com ofertas de parcelamento sem juros
- Campanhas educativas sobre os benefícios do uso consciente do crédito
- Produtos de investimento atrelados ao cartão para aumentar o engajamento

---

### Grupo 5 — Tomadores de Crédito / Setor lucrativo

> Clientes que usam o cartão como fonte de empréstimo — segmento mais rentoso para o banco.

| Indicador | Valor |
|---|---|
| Saldo em conta (`BALANCE`) | R$ 5.119 |
| Saque do limite (`CASH_ADVANCE`) | R$ 5.246 |
| Frequência de compras (`PURCHASES_FREQUENCY`) | 0.30 |
| Frequência de saques (`CASH_ADVANCE_FREQUENCY`) | 0.51 |
| Pagamento integral da fatura (`PRCFULLPAYMENT`) | 3% |

**Estratégia de marketing:**
- Monitoramento ativo do risco de inadimplência
- Ofertas de crédito pessoal com taxas menores como alternativa ao saque do limite
- Programas de educação financeira para migrar o perfil ao longo do tempo
- Negociação de dívidas proativas antes da inadimplência

---

### Grupo 7 — Clientes Novos

> Clientes recém-ingressados, com pouco histórico de uso do cartão.

| Indicador | Valor |
|---|---|
| Tempo de uso do cartão (`TENURE`) | 7,23 meses |
| Saldo em conta (`BALANCE`) | R$ 863 |

**Estratégia de marketing:**
- Onboarding estruturado para criar hábito de uso do cartão
- Ofertas de boas-vindas (cashback no primeiro mês, pontuação dobrada)
- Comunicação frequente para aumentar o engajamento e evitar churn precoce
- Acompanhamento do comportamento nos primeiros meses para direcionar ofertas personalizadas

---

## Resumo dos segmentos

| Grupo | Perfil | Principal característica | Ação prioritária |
|---|---|---|---|
| **0** | VIP / Prime | Alto limite + alta adimplência | Fidelização e upsell |
| **3** | Conservador | Baixo saldo + baixo saque | Estimular uso do cartão |
| **5** | Tomador de crédito | Alto saque + baixa adimplência | Gestão de risco |
| **7** | Cliente novo | Baixo tenure | Onboarding e engajamento |

---
