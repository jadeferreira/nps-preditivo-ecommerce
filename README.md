# NPS Preditivo para E-Commerce

**Tech Challenge — Fase 1 | Pós Tech FIAP — AI Scientist**  
**Aluna:** Jade Ferreira — RM 373208

---

## Objetivo do Projeto

Uma empresa de e-commerce em crescimento acelerado enfrenta um problema crítico: o NPS (Net Promoter Score) só é medido *depois* que toda a jornada de compra já aconteceu. Quando a insatisfação é descoberta, já é tarde demais para agir.

Este projeto usa dados operacionais históricos — logística, atendimento e comportamento do cliente — para entender **o que causa a insatisfação** e propor uma estratégia de ação preventiva, antes que o cliente se torne um detrator.

> *"Os dados não mentem — mas só fazem diferença quando alguém age sobre eles."*

---

## 📁 Estrutura do Repositório

```
nps-preditivo-ecommerce/
├── data/
│   └── desafio_nps_fase_1.csv       # Base de dados com 2.500 pedidos
├── notebooks/
│   └── jadeFerreira_rm373208_nps_fase1.ipynb  # Análise completa
├── reports/
│   └── nps_preditivo_jade_ferreira_2.pptx     # Apresentação executiva
└── README.md
```

---

## 🗂️ Descrição da Base de Dados

**Arquivo:** `data/desafio_nps_fase_1.csv`  
**Linhas:** 2.500 | **Colunas:** 19 | **Nulos:** 0 | **Duplicados:** 0

| Coluna | Descrição |
|--------|-----------|
| `customer_id` | Identificador único do cliente |
| `order_id` | Identificador único do pedido |
| `customer_age` | Idade do cliente |
| `customer_region` | Região geográfica do cliente |
| `customer_tenure_months` | Tempo de relacionamento com a empresa (meses) |
| `order_value` | Valor total do pedido |
| `items_quantity` | Quantidade de itens no pedido |
| `discount_value` | Valor de desconto aplicado |
| `payment_installments` | Número de parcelas do pagamento |
| `delivery_time_days` | Tempo total de entrega (dias) |
| `delivery_delay_days` | Dias de atraso na entrega |
| `freight_value` | Valor do frete |
| `delivery_attempts` | Número de tentativas de entrega |
| `customer_service_contacts` | Contatos do cliente com o SAC |
| `resolution_time_days` | Tempo para resolução de problemas (dias) |
| `complaints_count` | Número de reclamações registradas |
| `repeat_purchase_30d` | Recompra em até 30 dias (0 = não, 1 = sim) |
| `csat_internal_score` | Score interno de satisfação |
| `nps_score` | Nota NPS do cliente (0 a 10) — **variável-alvo** |

---

## 🔬 Metodologia

O projeto está organizado em 7 seções no notebook:

### 1. Entendimento do Negócio
Análise do problema, importância do NPS para e-commerce, áreas beneficiadas pelos insights e benchmarks de mercado.

### 2. Definição da Variável-Alvo
Justificativa para uso do `nps_score` como target, riscos de uso inadequado e identificação de variáveis com *data leakage* (`csat_internal_score` e `repeat_purchase_30d`).

### 3. Análise Exploratória de Dados (EDA)
- Distribuição do NPS: **74% detratores, 18% neutros, 8% promotores → NPS = –66%**
- Correlação entre variáveis operacionais e NPS
- Identificação do **ponto de ruptura**: atraso ≥ 3 dias dispara 92% de detratores; ≥ 6 dias = 100%
- Comparação de perfis: clientes "blindados" (nota 9–10) vs. "perdidos" (nota 0–1)
- Análise do efeito cascata: atraso → reclamações → contatos SAC → NPS despenca

### 4. Proposta de Modelo Preditivo
Reflexão sobre abordagens de regressão vs. classificação, justificativa para **classificação binária (Detrator vs. Não-Detrator)**, seleção de variáveis e estratégia de uso na operação.

### 5. Recomendações Práticas
Ações prioritárias baseadas nos insights da EDA, com foco em SLA logístico, SAC proativo e dashboard de risco.

### 6. Limitações e Riscos
Análise honesta dos limites dos dados e riscos de interpretação.

### 7. Conclusão Executiva
Síntese dos principais achados e próximos passos.

---

## 💡 Principais Insights

- **NPS de –66%**: a empresa está 106 pontos abaixo do mínimo esperado para o setor (+40 a +60)
- **Vilão principal**: atraso na entrega (correlação de –0,60 com o NPS)
- **Ponto de ruptura**: a partir de 3 dias de atraso, 92% dos clientes viram detratores — sem recuperação possível
- **Efeito cascata**: atraso gera reclamações, que geram contatos com SAC, que derrubam ainda mais o NPS
- **Perfil irrelevante**: valor do pedido, idade e região não explicam a insatisfação — a operação explica

---

## ✅ Recomendações

1. **SLA logístico**: alerta automático aos 2 dias de atraso, antes de cruzar o ponto de ruptura
2. **SAC preditivo**: contato proativo com o cliente antes que ele reclame
3. **Dashboard de risco**: painel em tempo real para gestores acompanharem pedidos críticos

---

## ▶️ Como Reproduzir a Análise

### Pré-requisitos

- Python 3.8+
- Jupyter Notebook ou JupyterLab

### Instalação das dependências

```bash
pip install pandas numpy matplotlib seaborn
```

### Executando o notebook

```bash
# Clone o repositório
git clone https://github.com/seu-usuario/nps-preditivo-ecommerce.git
cd nps-preditivo-ecommerce

# Abra o Jupyter
jupyter notebook notebooks/jadeFerreira_rm373208_nps_fase1.ipynb
```

> **Atenção:** certifique-se de que o arquivo `data/desafio_nps_fase_1.csv` está na pasta correta antes de executar. O notebook lê o arquivo diretamente por nome — se necessário, ajuste o caminho na célula de carregamento dos dados.

---

## 🛠️ Tecnologias Utilizadas

| Biblioteca | Uso |
|------------|-----|
| `pandas` | Manipulação e análise dos dados |
| `numpy` | Cálculos estatísticos |
| `matplotlib` | Visualizações gráficas |
| `seaborn` | Visualizações estatísticas |

---
