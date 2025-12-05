# Dashboard NBA: A Revolução da Bola de 3 (2015–2025)

## Sobre o Projeto

### Título e Tema
Dashboard interativo em Streamlit que analisa a evolução das bolas de 3 pontos na NBA, focando nas temporadas de 2014–15 a 2023–24.

### Justificativa da Escolha do Tema
A análise da bola de 3 pontos na NBA evidencia a transformação estratégica e estatística do jogo nas últimas décadas. O uso crescente dessa jogada tem impacto direto no estilo de jogo, resultados e campeonatos. Este dashboard permite entender essa evolução, destacando tendências e o desempenho dos times campeões.

## Fonte de Dados

### API Utilizada
NBA API via biblioteca `nba_api`  
- Endpoint: `LeagueDashTeamStats`  
- Dados coletados por time e temporada da temporada regular  
- Os dados são armazenados localmente em arquivos CSV para evitar requisições repetidas

### Atualização e Armazenamento  
- Arquivo consolidado de estatísticas das temporadas: `data/processed_team_stats_2015_2025.csv`  
- Arquivo com os campeões de cada temporada: `data/champions.csv`

## Descrição dos Dados

O dataset contém informações detalhadas das temporadas:  
- Temporada, time, jogos, vitórias, derrotas  
- Bolas de 3 convertidas, tentadas, aproveitamento e pontos  
- Métricas calculadas:  
  - Bolas de 3 por jogo (THREES_PER_GAME)  
  - Tentativas de 3 por jogo (THREES_ATT_PER_GAME)  
  - Pontos vindos de 3 (POINTS_FROM_3)  
  - Percentual dos pontos totais vindos de 3 (PERCENT_POINTS_3)

## Perguntas-Chave

- Como a dependência da bola de 3 evoluiu na NBA entre 2015 e 2025?  
- Qual o desempenho da liga e dos times campeões em aproveitamento e tentativas de 3 pontos?  
- Quais times têm maior volume e eficiência nas bolas de 3 por temporada?  
- Como essas métricas mudaram historicamente ao longo das temporadas?

## Como Rodar o Projeto Localmente

### Pré-requisitos

- Python 3.8 ou superior  
- pip (gerenciador de pacotes Python)

### Instruções

1. Clone ou copie o projeto para sua máquina  
2. Crie e ative ambiente virtual (opcional, recomendado)  
   - Windows: `venv\Scripts\activate`  
   - Linux/Mac: `source venv/bin/activate`  
3. Instale as dependências
   pip install -r requirements.txt
4. Execute o app Streamlit
   streamlit run projeto.py  
5. Acesse o dashboard pelo endereço local informado, normalmente [http://localhost:8501](http://localhost:8501/)

### Primeira execução (coleta dos dados)
- Pode demorar mais, pois o app coletará dados da API da NBA para todas as temporadas do intervalo  
- Os dados serão armazenados localmente para uso rápido em execuções posteriores  

## Funcionalidades

- Coleta automática de dados da NBA e armazenamento local em CSV  
- Processamento e criação de métricas relacionadas à bola de 3  
- Cache inteligente para evitar novas requisições desnecessárias (`@st.cache_data`)  
- Filtros interativos na sidebar para temporada, times e aproveitamento mínimo de 3 pontos  
- Métricas de destaque para liga e campeões por temporada  
- Visualizações:  
- Gráfico de barras: ranking de times por bolas de 3 convertidas por jogo  
- Gráfico de linhas histórico para evolução das tentativas de 3 na liga e campeões  
- Tabela interativa para visualização detalhada e exportação para CSV  

## Estrutura do Projeto
Dashboard NBA/
├── projeto.py
├── data/
│ ├── processed_team_stats_2015_2025.csv # Estatísticas consolidadas
│ └── champions.csv # Lista de campeões por temporada
├── requirements.txt # Dependências do projeto
└── README.md # Documentação do projeto


### Funções Principais do Código

- `get_team_stats_for_season(season)`: coleta dados para uma temporada específica  
- `generate_csv_files()`: gera arquivos CSV com estatísticas e campeões  
- `ensure_data_files()`: checa existência dos arquivos CSV, gera-os se necessário  
- `load_data()`: carrega os dados processados em DataFrames cacheados  

## Usando o Dashboard

- Escolha a temporada desejada na sidebar
  ![Sidebar - Temporada](/images/img1.png)  
- Selecione um ou mais times da temporada
  ![Sidebar - Times](images/img2.png)  
- Ajuste o filtro mínimo de aproveitamento de bolas de 3
  ![Sidebar - Bolas de 3](images/img3.png)  
- Veja métricas do campeonato e da liga, gráficos e tabelas detalhadas
  ![Gráfico - Colunas](images/img4.png)
  ![Gráfico - Linhas](images/img5.png)
  ![Tabela](images/img6.png)
- Exporte os dados filtrados em CSV pelo botão dedicado
  ![Exportar Dados - Botão](images/img7.png)

## Participantes

- Felipe Pinheiro Bahia Putti  
- Marcos Vinicius Paschoalin Ambrozio  

**Turma:** 2º Semestre - Ciência de Dados
