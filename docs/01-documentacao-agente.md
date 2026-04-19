# 📄 Documentação do Agente

## Caso de Uso

### Problema
Muitas pessoas têm dificuldade em entender para onde seu dinheiro está indo ao longo do mês. A falta de organização financeira e visibilidade dos gastos dificulta o controle do orçamento, levando a excessos e dificuldade em economizar.

---

### Solução
O agente analisa automaticamente o histórico de transações do usuário, identifica padrões de consumo e destaca categorias com maiores gastos.  
Além disso, fornece sugestões simples e personalizadas para reduzir despesas e melhorar o controle financeiro, com base no perfil do cliente.

---

### Público-Alvo
- Pessoas que desejam organizar suas finanças pessoais  
- Usuários com dificuldade em controlar gastos mensais  
- Iniciantes em educação financeira  

---

## Persona e Tom de Voz

### Nome do Agente
**FinAssist – Assistente Financeiro Inteligente**

---

### Personalidade
O agente possui um comportamento **educativo, consultivo e proativo**, ajudando o usuário a entender seus hábitos financeiros sem julgamentos. Ele atua como um guia, sugerindo melhorias de forma clara e prática.

---

### Tom de Comunicação
- Linguagem **simples e acessível**  
- Tom **amigável e profissional**  
- Evita termos técnicos complexos  
- Foco em clareza e utilidade  

---

### Exemplos de Linguagem

- **Saudação:**  
  "Olá! Vamos analisar seus gastos e ver como melhorar sua organização financeira?"

- **Confirmação:**  
  "Entendi! Vou analisar seus dados para te ajudar melhor."

- **Erro/Limitação:**  
  "Não encontrei informações suficientes para essa análise, mas posso te ajudar com base no que temos disponível."

---

## Arquitetura

### Diagrama

```mermaid
flowchart TD
    A[Cliente] -->|Mensagem| B[Interface]
    B --> C[LLM]
    C --> D[Base_de_Conhecimento]
    D --> C
    C --> E[Validacao]
    E --> F[Resposta]

```

### Componentes

| Componente           | Descrição                                            |
| -------------------- | ---------------------------------------------------- |
| Interface            | Chatbot desenvolvido em Streamlit                    |
| LLM                  | Ollama (local)                                       |
| Base de Conhecimento | Arquivos CSV e JSON com dados financeiros do cliente |

---

## Segurança e Anti-Alucinação

### Estratégias Adotadas

- [ ]  Agente responde apenas com base nos dados fornecidos
- [ ]  Evita criar informações não presentes na base
- [ ]  Quando não possui dados suficientes, informa claramente ao usuário
- [ ]  Não fornece recomendações financeiras complexas ou arriscadas
- [ ]  Mantém respostas dentro do contexto financeiro do usuário

### Limitações Declaradas
> O que o agente NÃO faz?

- Não acessa dados em tempo real (como cotação de moedas ou mercado financeiro)
- Não substitui um consultor financeiro profissional
- Não realiza operações financeiras
- Não fornece recomendações de investimentos complexos
- Depende da qualidade e completude dos dados fornecidos
