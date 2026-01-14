# Fintech-de-Pagamentos-B2C-
Fintech de Pagamentos (B2C)
# 📊 Case de Probabilidade e Distribuições — Fintech

Este repositório contém um **exercício prático e realista** de probabilidade e distribuições estatísticas aplicado a um **contexto de fintech**, no nível esperado para **Business Analyst, Product Analyst ou Data Analyst**.

O objetivo é demonstrar **raciocínio estatístico correto**, interpretação de resultados e conexão com **decisões de negócio**.

---

## 🏦 Contexto do Negócio

A **PayFlex** é uma fintech B2C que oferece conta digital e cartão. O funil principal de aquisição é:

**Cadastro → KYC aprovado → Primeira transação → Cliente ativo em 30 dias**

Além disso, a empresa monitora **eventos de fraude**, que ocorrem de forma rara, mas recorrente.

---

## 📌 Dados Utilizados

### Funil mensal

* Cadastros mensais: **10.000**
* Taxa média de aprovação no KYC: **72%**
* Taxa de primeira transação após KYC: **55%**
* Taxa de cliente ativo 30 dias após 1ª transação: **65%**

### Fraude

* Média histórica: **2,3 tentativas de fraude por dia**

---

## 1️⃣ Distribuição Binomial — Aprovação de KYC

Cada cadastro tem duas possibilidades mutuamente exclusivas:

* **Aprovado no KYC**
* **Reprovado no KYC**

Assumindo independência entre usuários, o número de aprovações segue uma **Distribuição Binomial**.

### Parâmetros

* ( n = 10.000 )
* ( p = 0,72 )

### Valor esperado

[
E[X] = n \cdot p = 10.000 \cdot 0,72 = 7.200
]

➡️ Em média, **7.200 usuários** são aprovados no KYC por mês.

---

## 2️⃣ Aproximação Normal — Variabilidade do KYC

Como ( np ) e ( n(1-p) ) são muito maiores que 5, a Binomial pode ser aproximada por uma **Distribuição Normal**.

### Parâmetros da Normal

* Média:
  [ \mu = np = 7.200 ]

* Desvio padrão:
  [
  \sigma = \sqrt{np(1-p)} = \sqrt{10.000 \cdot 0,72 \cdot 0,28} \approx 44,9
  ]

### Probabilidade de mais de 7.400 aprovações

[
Z = \frac{7.400 - 7.200}{44,9} \approx 4,46
]

➡️ Probabilidade ≈ **0,0004%** (evento extremamente raro)

### Probabilidade entre 7.000 e 7.400 aprovações

[
P(7.000 < X < 7.400) = P(-4,46 < Z < 4,46) \approx 99,9992%
]

➡️ Quase todos os meses caem nesse intervalo.

---

## 3️⃣ Probabilidade Condicional — Conversão do Funil

As etapas do funil são condicionais:

* ( P(KYC) = 0,72 )
* ( P(1ª\ Transação \mid KYC) = 0,55 )
* ( P(Ativo \mid 1ª\ Transação) = 0,65 )

### Probabilidade total de ativação

[
P(Ativo) = 0,72 \cdot 0,55 \cdot 0,65 = 0,2574
]

➡️ **25,74%** dos usuários cadastrados se tornam ativos em 30 dias.

### Número esperado de clientes ativos

[
10.000 \cdot 0,2574 = 2.574
]

➡️ Aproximadamente **2.574 clientes ativos** por mês.

---

## 4️⃣ Distribuição de Poisson — Eventos de Fraude

Eventos de fraude são:

* raros
* independentes
* contados em um intervalo fixo de tempo

➡️ O modelo adequado é a **Distribuição de Poisson**.

### Parâmetro

[
\lambda = 2,3 \quad (fraudes/dia)
]

### Nenhuma fraude em um dia

[
P(X=0) = e^{-2,3} \approx 10,03%
]

### Exatamente 5 fraudes em um dia

[
P(X=5) = \frac{e^{-2,3} \cdot 2,3^5}{5!} \approx 5,37%
]

### Cinco ou mais fraudes em um dia

[
P(X \ge 5) = 1 - P(X \le 4) \approx 8,34%
]

➡️ Aproximadamente **1 em cada 12 dias** apresenta um pico relevante de fraude, justificando alertas e capacidade operacional.

---

📌 *Os próximos itens do estudo avançam para tempo até evento (Distribuição Exponencial) e análise de decisão de negócio.*
