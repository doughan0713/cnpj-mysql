# 🚀 cnpj-mysql

<p align="center">
  <img src="https://img.shields.io/badge/status-ativo-00FF41?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/python-3.8+-blue?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/database-MySQL%20%7C%20PostgreSQL-orange?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/data-CNPJ%20Receita%20Federal-green?style=for-the-badge"/>
</p>

---

## 🧠 Visão Geral

Pipeline de ingestão de dados públicos do **Cadastro Nacional da Pessoa Jurídica (CNPJ)** diretamente da Receita Federal, com processamento em larga escala utilizando **Python + Pandas + Dask + SQLAlchemy**.

Este projeto permite:

- 📥 Download automatizado dos dados oficiais
- ⚙️ Processamento eficiente de grandes volumes (big data ready)
- 🗄️ Persistência estruturada em **MySQL** ou **PostgreSQL**
- 🔄 Compatibilidade com layouts atualizados da Receita (≥ 2021)

---

## 📊 Arquitetura do Fluxo de Dados

```mermaid
flowchart LR
    A[Receita Federal] --> B[Download ZIP]
    B --> C[Extração CSV]
    C --> D[Processamento Pandas/Dask]
    D --> E[Transformação SQLAlchemy]
    E --> F[(MySQL/PostgreSQL)]
| Ambiente                         | Tempo Médio  |
| -------------------------------- | ------------ |
| 💻 Notebook i7 8ª Gen            | ~5 horas     |
| 🖥️ VPS otimizada                | ~2 a 4 horas |
| ⚡ Infraestrutura paralela (Dask) | Escalável    |
📡 Fonte Oficial dos Dados
🔗 https://dados.gov.br/dados/conjuntos-dados/cadastro-nacional-da-pessoa-juridica---cnpj
🔗 https://arquivos.receitafederal.gov.br/dados/cnpj/dados_abertos_cnpj/

⚠️ Atualizado automaticamente para a pasta mais recente após mudanças estruturais (desde 14/08/2024)

🧰 Pré-requisitos
Python >= 3.8
📦 Dependências principais
pip install pandas dask sqlalchemy
🐬 MySQL
pip install pymysql
🐘 PostgreSQL
pip install psycopg2-binary
⚙️ Configuração

Edite os parâmetros no início do script:

dbname = 'cnpj'
username = 'root'
password = ''
host = '127.0.0.1'
🚀 Execução
1. Download dos dados
python dados_cnpj_baixa.py

📁 Saída:

/dados-publicos-zip
2. Preparar diretório

Crie manualmente:

/dados-publicos

(⚠️ Deve estar vazio)

3. Importação para banco
MySQL
python dados_cnpj_mysql.py
PostgreSQL
python dados_cnpj_postgres.py
📊 Visualização de Pipeline (Processamento)
graph TD
    A[ZIP Files] --> B[CSV Parsing]
    B --> C[Data Cleaning]
    C --> D[Normalization]
    D --> E[Database Load]
🧪 Estratégias de Otimização
⚡ Uso de Dask para paralelismo
💾 Possibilidade de staging em SQLite
🔄 Migração via pgloader ou DBeaver
📉 Redução de I/O com batch inserts
| Estratégia           | Vantagem               |
| -------------------- | ---------------------- |
| SQLite intermediário | 🚀 Muito mais rápido   |
| pgloader             | 🔄 Migração eficiente  |
| DBeaver              | 🖥️ Interface amigável |
🧩 Projetos Relacionados
🔗 https://github.com/rictom/cnpj-sqlite
🔗 https://github.com/rictom/rede-cnpj
📡 Roadmap Técnico
timeline
    title Evolução do Projeto

    2021 : Versão inicial
    2022 : Compatibilidade SQLAlchemy 2.0
    2024 : Atualização estrutura Receita
    2026 : 🔥 Expansão de integrações
📲 Atualizações Futuras (IMPORTANTE)

🚧 Em breve será disponibilizada uma atualização crítica com:

📱 Inclusão de até 9 números de telefone por entidade
🔄 Mecanismo de atualização incremental de contatos
📡 Normalização e enriquecimento de dados de comunicação
🧠 Preparação para integração com modelos de IA analítica
Arquitetura prevista:
flowchart LR
    A[CNPJ Base] --> B[Enriquecimento]
    B --> C[Telefones]
    C --> D[Atualização Incremental]
    D --> E[Base Inteligente]
🧠 Aplicações Avançadas
🔍 Portais tipo Escavador
📊 Inteligência de mercado
🧬 Análise de redes empresariais
🤖 Integração com LLMs (IA privada)
📦 Versionamento
Versão	Data	Descrição
0.2	Jul/2022	Compatibilidade PostgreSQL
0.2	Jan/2022	SQLAlchemy ≥ 2.0
0.1	Nov/2021	Primeira versão
⚖️ Compliance

✔ Dados públicos oficiais
✔ Compatível com LGPD (uso adequado)
✔ Sem dados sensíveis após sanitização

👨‍💻 Autor

Projeto baseado no trabalho de:
https://github.com/rictom

💡 Contribuições

Pull requests são bem-vindos 🚀
Sugestões de otimização são altamente encorajadas.

<p align="center"> <b style="color:#00FF41;">Infraestrutura de dados é poder.</b><br> <sub>Transformando dados públicos em inteligência operacional.</sub> </p> ```
