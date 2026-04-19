# 📊 Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Utilização no Agente |
|---------|---------|---------------------|
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente, identificar categorias com maior consumo e calcular totais |
| `perfil_investidor.json` | JSON | Personalizar recomendações com base no perfil financeiro e objetivo do cliente |

---

## Adaptações nos Dados

Os dados mockados foram adaptados para focar no controle de gastos pessoais.

No arquivo `transacoes.csv`, foram organizadas informações como:
- Data da transação  
- Descrição (ex: supermercado, aluguel)  
- Categoria (alimentação, moradia, transporte, etc.)  
- Valor  
- Tipo (entrada ou saída)  

Essas informações permitem ao agente realizar análises simples, como:
- Total de gastos no período  
- Identificação de categorias com maior impacto financeiro  
- Comparação entre receitas e despesas  

O arquivo `perfil_investidor.json` foi simplificado para conter:
- Perfil do cliente (ex: conservador)  
- Objetivo financeiro (ex: economizar)  
- Renda mensal  

Esses dados ajudam o agente a adaptar suas respostas de forma mais personalizada.

---

## Estratégia de Integração

### Como os dados são carregados?

Os arquivos CSV e JSON são carregados no início da aplicação utilizando Python.

- O arquivo `transacoes.csv` é carregado com a biblioteca **pandas**  
- O arquivo `perfil_investidor.json` é carregado como um dicionário Python

```python 
import pandas as pd
import json

# CSVs
transacoes = pd.read_csv('data/transacoes.csv')

# JSONs
with open ('data/perfil_investidor.jason', 'r', encoding-'utf-8') as f:
  perfil = json.load(f)

```
---

### Como os dados são usados no prompt?

Os dados não são inseridos diretamente no system prompt.

Eles são:
- Consultados dinamicamente conforme a pergunta do usuário  
- Processados para gerar resumos (ex: total gasto, categorias mais utilizadas)  
- Inseridos no contexto da resposta enviada ao modelo de linguagem  

Isso evita excesso de informação e melhora a precisão das respostas.

---

## Exemplo de Contexto Montado

Dados do Cliente:


**Perfil: Conservador**

Objetivo: Economizar

Renda mensal: R$ 5.000


**Resumo Financeiro:**

Total de entradas: R$ 5.000

Total de saídas: R$ 2.488,90


**Maiores gastos por categoria:**

Moradia: R$ 1.380,00

Alimentação: R$ 570,00

Transporte: R$ 295,00


**Últimas transações:**

01/10: Salário - R$ 5.000

03/10: Supermercado - R$ 450

10/10: Restaurante - R$ 120

---

## Considerações

A base de conhecimento foi mantida simples e objetiva, priorizando clareza e facilidade de integração.

Mesmo com dados reduzidos, o agente consegue:
- Gerar análises úteis  
- Identificar padrões de consumo  
- Fornecer recomendações básicas e personalizadas  

Essa abordagem garante um bom equilíbrio entre simplicidade e eficiência para o contexto do projeto.
