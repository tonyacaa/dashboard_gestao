# Portfólio de Business Intelligence & Controladoria Logística — DGASP / SES-PE

Repositório dedicado à apresentação de dashboards e relatórios de Business Intelligence (Power BI) desenvolvidos para a gestão orçamentária, controle de custos logísticos e análise de eficiência *per capita* da Diretoria Geral de Assistência Prisional.

> **Nota de Privacidade & Governança:** Os dados e indicadores apresentados neste repositório utilizam valores demonstrativos/fictícios exclusivamente para simulação de modelos de BI, análise estratégica e apresentação de portfólio profissional.

---

## 1. Dashboard de Custo Per Capita por Unidade Prisional

[📄 Acessar Relatório em PDF (Custo Per Capita)](https://github.com/tonyacaa/dashboard_gestao/blob/main/Relat%C3%B3rio%20-%20Custo%20PerCapita.pdf)

### 📄 Contexto e Desafio
A gestão logística e de saúde prisional demandava visibilidade granular sobre a distribuição e eficiência dos recursos aplicados nas unidades do Estado de Pernambuco, exigindo a unificação de dados operacionais e populacionais fragmentados em múltiplos sistemas estaduais.

### 🛠️ Arquitetura e Modelagem de Dados
- **Integração de Fontes Multi-Sistema:** Criação de base unificada no Excel cruzando dados extraídos de:
  - **SAP ERP (Módulo Logística):** Consumo de insumos e medicamentos.
  - **Sistema Integrado de Contratos Públicos:** Prestação de serviços e contratos operacionais.
  - **Sistema Integrado de Recursos Humanos:** Custos com folha e pessoal alocado.
  - **Dados Populacionais Prisionais:** População de PPL (Pessoas Privadas de Liberdade) por unidade.
- **Métricas e KPIs:** Cálculo automatizado do **Custo Per Capita por PPL** ($Custo Total \div População Carcerária$), desdobrado por Unidade Prisional e categorizado por tipo de despesa.

### 🎯 Impacto Gerencial e Tomada de Decisão
- **Identificação de Gargalos:** Mapeamento preciso das Unidades Prisionais com maior custo operacional de saúde do Estado e diagnóstico do tipo de despesa de maior impacto.
- **Otimização de Recursos:** Redução e redistribuição estratégica do consumo de medicamentos e pessoal em unidades hiperdimensionadas.
- **Decisões Estratégicas de Reestruturação:** Fornecimento de dados gerenciais que fundamentaram a desativação de Unidades Prisionais com baixa população carcerária e custos fixos elevados, com o remanejamento seguro de PPLs para outras unidades da rede.

---

## 2. Dashboard Orçamentário e Financeiro (Execução & Fluxo de Caixa)

[📄 Acessar Relatório em PDF (Orçamentário & Financeiro)](https://github.com/tonyacaa/dashboard_gestao/blob/main/Relat%C3%B3rio%20Or%C3%A7ament%C3%A1rio%20Financeiro.pdf)

### 📄 Contexto e Desafio
Garantir o rigor fiscal, o acompanhamento do planejamento orçamentário aprovado junto ao Estado e a previsibilidade do fluxo de caixa da Diretoria, evitando sobrecarga em rubricas específicas de despesas.

### 🛠️ Arquitetura e Modelagem de Dados
- **Integração de Dados Financeiros e Fiscais:** Construção de modelo consolidado no Power BI alimentado por dados extraídos de:
  - **e-Fisco (SEFAZ-PE):** Relatórios de liquidação e repasses orçamentários.
  - **SEPLAG-PE:** Teto orçamentário aprovado no Plano Operativo (POAS).
  - **SAP Logística, RH e Contratos Públicos:** Detalhamento gerencial de empenhos e contas a pagar.
- **Gestão de Saldos:** Incorporação do saldo financeiro de exercícios anteriores (Aportes em Janeiro) para cálculo preciso do saldo em caixa vs. saldo orçamentário disponível.

### 🎯 Impacto Gerencial e Tomada de Decisão
- **Conformidade e Regularidade Fiscal:** Acompanhamento contínuo da relação **Orçado (SEPLAG) vs. Executado**, assegurando o cumprimento das metas orçamentárias estaduais.
- **Diagnóstico do Impulsionador de Custos:** Identificação imediata da categoria de despesa que mais impacta a matriz financeira da Diretoria (e.g., Pessoal e Insumos Críticos).
- **Previsibilidade Financeira:** Monitoramento mensal do fluxo de caixa (entradas x saídas), garantindo sustentabilidade orçamentária para a continuidade dos serviços essenciais.

---

### 💻 Tecnologias e Ferramentas Utilizadas
- **Business Intelligence:** Power BI (DAX, Modelagem Relacional, Dashboards Interativos).
- **Tratamento de Dados:** Excel Avançado, Python e Consultas SQL.
- **Sistemas de Origem:** SAP ERP, e-Fisco (SEFAZ-PE), SEPLAG-PE, Sistemas de RH e Contratos Públicos.
- **Domínio de Negócio:** *Supply Chain* Público, Controladoria, Gestão de Custos e Análise de Eficiência Logística.
