# Monitoramento de Preços — Web Scraping + Databricks

Projeto: sistema de monitoramento de preços que combina web scraping para coleta de dados e Databricks para armazenamento e processamento em larga escala.

Visão geral
-----------

Este repositório é a base para um sistema que periodicamente coleta preços e metadados de produtos em lojas online, normaliza e persiste o histórico de preços, e permite análises, relatórios e alertas sobre variações.

Componentes principais
---------------------

- Scrapers: módulos que coletam dados (requests + BeautifulSoup, ou Selenium para páginas dinâmicas).
- Ingestão/ETL: pipelines que limpam, normalizam e carregam os dados em um storage compatível (Delta Lake no Databricks).
- Processamento: notebooks e jobs no Databricks para agregações, cálculos de métricas e preparação de dashboards.
- Armazenamento: tabelas históricas (Delta) que guardam snapshots de preço por SKU/produto ao longo do tempo.

Funcionalidades sugeridas
-------------------------

- Coleta agendada de preços por produto/SKU.
- Normalização de nomes, moedas e formatos.
- Detecção de mudanças significativas de preço e alerta por e-mail/Slack.
- Relatórios e dashboards (ex.: variação semanal, produtos com maior queda/alta).

Requisitos básicos
------------------

- Python 3.8+
- Pip
- (Para deploy) Conta Databricks com workspace e permissões para jobs e storage

Instalação local (rápido)
------------------------

1. Clone o repositório:

   git clone <repo-url>

2. Entre na pasta do projeto:

   cd monitoramento_preco_web_scraping_databricks

3. Crie e ative um ambiente virtual Python:

   python -m venv .venv
   source .venv/bin/activate

4. Instale dependências de desenvolvimento (ex.: pytest) se houver `requirements.txt`:

   pip install -r requirements.txt

Estrutura sugerida de pastas
----------------------------

- scrapers/        — código de scraping por site
- pipelines/       — scripts/ETL e orquestração
- notebooks/       — notebooks para Databricks / Jupyter
- tests/           — testes automatizados
- README.md
- requirements.txt

Uso básico
---------

1. Adicione scrapers no diretório `scrapers/` para os sites desejados.
2. Crie pipelines que consolidem os dados e escrevam em Delta/DBFS.
3. Importe/execute notebooks no Databricks para processamento e criação de dashboards.

Testes
------

Adicione testes simples em `tests/` (pytest) para validar a presença e integridade de artefatos, comportamento dos scrapers e transformações.

Databricks — notas rápidas
-------------------------

- Prefira notebooks idempotentes para ingestão e transformação.
- Use Delta Lake para armazenar histórico e permitir updates/merges.
- Agende Jobs para execução periódica das rotinas de ingestão.

Contribuição
------------

Abra issues e pull requests. Inclua testes mínimos nas mudanças e siga padrões de lint/format quando possível.

Licença
-------

Sem licença especificada. Adicione um arquivo `LICENSE` para definir termos de uso.

----

Arquivo gerado em 03/11/2025.
