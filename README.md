<h1 align="center"> Projeto de Dados: Integração TMDB via API no Databricks </h1> 

Este é um projeto simples que visa proporcionar uma primeira experiência prática no ambiente gratuito Databricks Community Edition, explorando técnicas de extração de dados via API, manipulação de arquivos JSON, utilização de Python, Spark SQL e PySpark, além da implementação de uma Arquitetura Medallion no conceito de Lakehouse para organizar logicamente os dados.

O objetivo principal é extrair uma lista de filmes favoritos e uma lista de gêneros disponíveis do site TMDB (The Movie Database) através de sua API, cruzar esses dados e propagá-los pela arquitetura Medallion do Lakehouse, passando pelas camadas bronze, prata e ouro. O intuito final é permitir o consumo dessas informações por meio de painéis no Power BI.

Devido às limitações do Databricks Community, não foi possível integrar o Apache Airflow para a orquestração do pipeline de dados. Para subir o projeto para o GitHub foi necessário exportar os notebooks no Databricks Community e importar como arquivo *.ipynb.


Abaixo você pode conferir mais detalhes da arquitetura do projeto.

Camada 1:
Nesta fase, ocorre a extração de dados via API do TMDB e o armazenamento dos mesmos em arquivos JSON.

Camada 2:
Os dados brutos contidos nos arquivos JSON são extraídos e gravados em uma tabela bronze.

Camada 3:
Aqui os dados são extraídos da tabela bronze e passam por diversos tratamentos utilizando funções do SparkSQL. Em seguida, são unidos com a tabela de gêneros de filmes e gravados em uma tabela prata.

Camada 4:
Os dados são novamente extraídos, desta vez da tabela prata, e passam por processos de agregação e criação de tabelas ouro com diferentes propósitos.

Camada 5:
Finalmente, os dados são extraídos das tabelas ouro e preparados para o consumo em painéis do Power BI.

Esse projeto visa fornecer uma introdução prática às tecnologias e conceitos fundamentais para o processamento de dados em um ambiente distribuído como o Databricks, além de oferecer uma visão geral sobre a implementação de uma arquitetura de dados simples, facilitando a análise e tomada de decisões baseadas em dados.