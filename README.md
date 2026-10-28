# Dashboards de Gestão Pública em Power BI
### Orçamento, Execução Financeira e Custo Per Capita da Saúde no Sistema Prisional

Portfólio de dois dashboards em Power BI criados para apoiar a gestão orçamentária e o controle de custos da saúde no sistema prisional do Estado de Pernambuco. Os projetos nasceram de um problema real de gestão: os dados estavam espalhados em sistemas independentes e não havia uma visão única de planejado, executado e custo por unidade.

> **Nota sobre os dados:** todos os dados deste repositório são **fictícios**. A estrutura do modelo, as regras de negócio e a lógica dos cálculos refletem o processo real, mas nomes, documentos, números de processos e valores foram substituídos por dados gerados para fins de demonstração. Nenhuma informação pessoal ou identificador real está presente.

| Projeto | Pergunta que responde | Principais ferramentas |
|---|---|---|
| [1. Orçamentário e Financeiro](#1-dashboard-orçamentário-e-financeiro) | Quanto planejamos, quanto executamos e quanto ainda temos de saldo? | Power BI, DAX, Excel |
| [2. Custo Per Capita](#2-dashboard-custo-per-capita-por-unidade-prisional) | Quanto custa a saúde de cada pessoa privada de liberdade, por unidade e por tipo de despesa? | Power BI, DAX, Excel |

---

## Conteúdo do repositório

```
dashboard_gestao/
├── README.md
├── pbix/
│   ├── Dashboard_Financeiro.pbix
│   └── Dashboard_Per_Capita.pbix
├── data/
│   ├── Base_Orcamentaria_Financeiro_FICTICIA.xlsx
│   └── Base_Dados_Per_Capita_FICTICIA.xlsx
└── docs/
    ├── Relatório - Custo PerCapita.pdf
    ├── Relatório Orçamentário Financeiro.pdf
    └── img/            (capturas de tela)
```

---

## 1. Dashboard Orçamentário e Financeiro

[Ver relatório em PDF](https://github.com/tonyacaa/dashboard_gestao/blob/6255c6feb750ba44762bacb42cb39d38e657ad9b/Dash.%20Financeiro%20.pdf)

[Ver vídeo com funcionalidades](https://github.com/tonyacaa/dashboard_gestao/blob/6255c6feb750ba44762bacb42cb39d38e657ad9b/V%C3%ADdeo%20Demonstrativo%20(Financeiro).mp4)

<!-- Descomente depois de adicionar a imagem em docs/img/
![Visão geral do dashboard financeiro](docs/img/financeiro_visao_geral.png)
-->

### Contexto e desafio
Para controlar os gastos com saúde no sistema prisional, é preciso comparar o que foi planejado com o que foi executado, mês a mês. Essas informações ficavam em sistemas diferentes, e consolidá-las manualmente era lento e sujeito a erro.

### O que o dashboard mostra
- **Orçamento previsto x execução financeira**, por mês.
- **Saldo orçamentário** (planejado menos executado) e **saldo financeiro** (recursos disponíveis menos executado).
- **Fluxo de caixa mensal**, com repasses recebidos e valores executados.
- **Detalhamento por tipo de despesa**: página dedicada com a distribuição entre pessoal, medicamentos e insumos, contratos de pessoa jurídica e diárias de servidores.
- **Data da última atualização** da base, para dar transparência ao usuário.

### Fontes de dados e consolidação
Os dados vêm de quatro sistemas independentes e são consolidados em uma base paralela mantida em Excel, que alimenta o modelo do Power BI.

| Fonte | O que fornece |
|---|---|
| **SIPAE** (Sistema Integrado de Planejamento, Administração e Execução Orçamentária) | Orçamento planejado da diretoria |
| **e-Fisco (SEFAZ-PE)** | Relatório de liquidações da fonte orçamentária, que mostra o que foi de fato executado |
| **CEOS** (SAP de gestão de suprimentos) | Gastos com compra e expedição de medicamentos e insumos hospitalares |
| **PE-Integrado** | Contratos ativos de pessoa jurídica |

### Modelo de dados
Base consolidada em Excel, com tabelas formatadas e relacionadas no Power BI:

- `Fato_Liquidacoes`: uma linha por liquidação (tabela fato), com tipo de despesa, fonte de recurso, valores liquidados, estornados e líquidos.
- `Orcamento_Mensal`: planejado, repasses, saldo remanescente, executado por fonte e saldos, por mês.
- `Classificação CNPJ`: regra que classifica cada credor em um tipo de despesa (medicamentos, veículos, TI, motoristas, manutenção etc.). Pessoas físicas entram automaticamente como pessoal.
- `Dim_Fonte`: dimensão das fontes de recurso.
- `Calendario`: dimensão de datas.
- `Controle`: data da última liquidação carregada.

### Regra de negócio importante
O saldo financeiro costuma ficar **acima do valor orçado**. Isso acontece porque ele reúne os repasses mensais do Ministério da Saúde, pagos com base na política nacional, **mais o saldo remanescente de exercícios anteriores**, que entra em janeiro. Por isso, o dashboard separa saldo orçamentário e saldo financeiro, evitando leituras erradas.

### Como apoia a tomada de decisão
- Acompanhar a execução contra o planejado e antecipar meses de pressão sobre o orçamento.
- Identificar quais tipos de despesa mais pesam no orçamento.
- Dar previsibilidade ao fluxo de caixa para a continuidade dos serviços de saúde.
- Reduzir o tempo gasto consolidando relatórios de sistemas diferentes em uma única visão.

---

## 2. Dashboard Custo Per Capita por Unidade Prisional

[Ver relatório em PDF](https://github.com/tonyacaa/dashboard_gestao/blob/main/Relat%C3%B3rio%20-%20Custo%20PerCapita.pdf)

[Ver vídeo com funcionalidades](https://github.com/tonyacaa/dashboard_gestao/blob/6255c6feb750ba44762bacb42cb39d38e657ad9b/V%C3%ADdeo%20Demonstrativo%20(Per%20Capita).mp4)

<!-- Descomente depois de adicionar a imagem em docs/img/
![Visão geral do dashboard per capita](docs/img/percapita_visao_geral.png)
-->

### Contexto e desafio
Saber o gasto total não basta: unidades com populações muito diferentes não podem ser comparadas pelo valor absoluto. Era preciso medir o **custo por pessoa privada de liberdade (PPL)** em cada unidade e entender de qual tipo de despesa ele vem.

### O que o dashboard mostra
- **Evolução mensal do custo total**.
- **Custo médio por PPL em cada unidade**, para comparar unidades de tamanhos diferentes.
- **Detalhamento de custos por tipo de despesa**, em tabela interativa.
- Filtros de período e de unidade, com os valores somados conforme a seleção.

### Fontes de dados e cálculo
- Os gastos da diretoria, já consolidados no projeto financeiro, são **distribuídos por unidade prisional** e classificados por tipo de despesa.
- A **população carcerária** de cada unidade é informada pela Secretaria de Justiça e Direitos Humanos do Estado.

```
Custo per capita = Custo total da unidade ÷ População carcerária da unidade
```

Os 14 itens de despesa detalhados (pessoal, medicamentos e insumos, locação de veículos, motoristas, diárias, manutenção de equipamentos e outros) são agrupados em 10 categorias para a análise.

### Modelo de dados
- `Base_Dados_Depen`: visão detalhada, com uma linha por unidade e mês.
- `Por Atributo`: mesma informação em formato longo, por categoria de despesa, usada nos visuais.
- Tabela de correspondência entre cada item de despesa e sua categoria.

### Como apoia a tomada de decisão
- Identificar quais unidades têm o maior custo de saúde por pessoa e **qual tipo de despesa explica** essa diferença.
- Apoiar discussões sobre alocação de recursos, comparando unidades em bases equivalentes.
- Perceber efeitos de custo fixo em unidades com população pequena.


## Ferramentas e competências demonstradas

- **Business Intelligence:** Power BI (modelagem relacional, DAX, dashboards interativos, navegação entre páginas).
- **Tratamento de dados:** Excel avançado (tabelas, PROCV, regras de classificação, consolidação de múltiplos relatórios).
- **Domínio de negócio:** Supply Chain público, controladoria orçamentária, gestão de custos, análise de eficiência logística.

## Próximos passos
- Automatizar a consolidação das quatro fontes, hoje manual (Power Query e/ou scripts).
- Consultar as bases diretamente via SQL, quando houver acesso.
- Publicar a documentação das principais medidas DAX.

---

## English summary

Two Power BI dashboards built for public-sector healthcare supply chain management in the Brazilian prison system (state of Pernambuco):

1. **Budget & Financial Execution:** consolidates four independent systems (budget planning, state accounting, SAP-based supply, and contracts) into one model to compare planned vs. executed spending, budget balance vs. cash balance, and cost drivers by expense type.
2. **Per Capita Health Cost:** allocates spending by facility and divides it by inmate population to compare cost per person across facilities and expense categories.

All data in this repository is **fictitious**; model structure and business logic mirror the real process. Tools: Power BI (DAX, data modeling), advanced Excel.

---

## Contato

Antônio Aca · Supply Chain & Procurement | Power BI
[LinkedIn](https://www.linkedin.com/in/ant%C3%B4nio-a-b755461b7/)
