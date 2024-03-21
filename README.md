# Logistic_Facilities_Distribution_Analysis

Uma análise da distribuição espacial das instalações logísticas do Distrito Federal em relação à disponibilidade de infraestrutura de transporte na região.

## Índice
- [Visão geral](#item-one)
- [Procedimentos de coleta de dados](#item-two)
- [Procedimentos de análise de dados](#item-three)
- [Ferramentas utilizadas](#item-four)
- [Resultados](#item-five)
- [Conclusões e recomendações](#item-six)
- [Referências](#item-seven)

<!-- headings -->
<a id='item-one'></a>
## Visão geral

O transporte é uma das principais atividades na logística, sendo essencial para o funcionamento de atividades comerciais. A infraestrutura física é um dos componentes da estrutura de transporte de carga, dando suporte à essa atividade e exercendo 
influência na localização de instalações logísticas, como armazéns e instalações de transporte de mercadorias. Nesse contexto, o objetivo geral deste projeto foi **analisar a distribuição espacial das instalações logísticas do Distrito Federal (DF) em relação à disponibilidade de infraestrutura de transporte na região**. <br>

Os procedimentos para análise de dados envolveram a utilização de gráficos, mapas temáticos e o cálculo de métricas de distância e medidas de associação espacial entre variáveis.

Este projeto é uma "adaptação" do meu trabalho final de graduação em Administração pela Universidade de Brasília. 

<!-- headings -->
<a id='item-two'></a>
## Procedimentos de coleta de dados

Os dados foram coletados de fontes secundárias disponíveis online em bases de dados públicas. Foram coletados **quatro conjuntos de dados**: empresas, regiões administrativas, zoneamento e sistema viário. Com esses dados foi possível identificar as empresas do setor de transporte e armazenamento no DF, bem como suas localizações por regiões administrativas e zonas. Além disso, os dados do sistema viário, que englobam tanto as rodovias distritais quanto as federais, permitiram analisar a disponibilidade de infraestrutura de transporte na região.

Os dados sobre empresas foram coletados da base da *Receita Federal*, publicada no *Portal Brasileiro de Dados Abertos*, enquando os dados sobre Regiões Administrativas (RA) e Zoneamento foram obtidos através do site da *Infraestrutura de Dados Espaciais do Distrito Federal (IDE/DF)*, publicados pela *Secretaria de Estado de Desenvolvimento Urbano e Habitação (SEDUH)* do DF.

Para o sistema viário, foram coletados dados sobre sistema viário nacional no catálogo de metadados da *Infraestrutura Nacional de Dados Espaciais (INDE)*. As bases geoespaciais de rodovias federais e estaduais são disponibilizadas no site da INDE pela Coordenação-Geral de Planejamento e Programação de Investimentos (CGPLAN) e pela Coordenação de Levantamentos para Planejamento (COLEP), ambas vinculadas ao *Departamento Nacional de Infraestrutura de Transportes (DNIT)*.

**Links:**
* Cadastro Nacional da Pessoa Jurídica - CNPJ: https://dados.gov.br/dados/conjuntos-dados/cadastro-nacional-da-pessoa-juridica---cnpj
* Infraestrutura de Dados Espaciais do Distrito Federal: https://www.ide.df.gov.br/#home
* Infraestrutura Nacional de Dados Espaciais - Catálogo de Metadados: https://metadados.inde.gov.br/geonetwork/srv/por/catalog.search#/home

<!-- headings -->
<a id='item-three'></a>
## Procedimentos de análise de dados

Os procedimentos de análise dos dados utilizados nesta pesquisa vão desde a utilização de representações visuais como **gráficos e mapas temáticos** até o cálculo de **métricas de distância e medidas de associação espacial entre variáveis**. 

Essas ferramentas analíticas são cruciais para entender e explorar a distribuição espacial das instalações logísticas do Distrito Federal e adicionalmente, possibilitaram uma análise aprofundada das interações entre as localizações das empresas e a infraestrutura de transporte disponível na região.

<!-- headings -->
<a id='item-four'></a>
## Ferramentas utilizadas

- Google Colaboratory
- Python
- Matplotlib
- Pandas
- Geopandas
- PySAL

<!-- headings -->
<a id='item-five'></a>
## Resultados

Ao todo, foram identificadas 8327 empresas, presentes em todas as 35 regiões administrativas do DF. A figura abaixo demonstra as localizações das empresas do setor de transporte e armazenamento do DF, destacando as cinco regiões com maior ocorrência de empresas (*Top Five*) e cinco regiões com menor ocorrência de empresas (*Bottom Five*). 

![image](https://github.com/manoel-nto/Logistic_Facilities_Distribution_Analysis/assets/72640326/e96536d3-f123-4a27-b870-583bdea08ade)

Para analisar a dispersão e a concentração das empresas na região do DF, foram calculados o centro médio dos pontos que identificam essas empresas (coordenadas geográficas) e a SDE (Standard Deviational Ellipse). Em seguida, foram identificados quais os pontos estão dentro da SDE e qual é a sua área.

![image](https://github.com/manoel-nto/Logistic_Facilities_Distribution_Analysis/assets/72640326/6f84a42b-0ab7-44d5-b8e8-2d357c5ee658)

Ao todo, são 5162 pontos dentro da SDE, o que representa 61,99% do total dos pontos analisados (Tabela 2), ou seja, a maioria das empresas está dentro da SDE.

![image](https://github.com/manoel-nto/Logistic_Facilities_Distribution_Analysis/assets/72640326/3d4b1261-fc9d-41ae-89eb-64d8b18094b1)

A SDE descreve bem a localização média dos pontos, que estão concentrados em algumas regiões administrativas que representam uma parte minoritária da área total do DF.

![image](https://github.com/manoel-nto/Logistic_Facilities_Distribution_Analysis/assets/72640326/1f0f07da-535e-420a-ba4a-525e1599a5b6)

O Moran's I calculado para a densidade de empresas (quantidade de empresas por $km^2$ de área da região) foi de 0.33 e estatisticamente significativo ($\alpha = 0.05$). 

![image](https://github.com/manoel-nto/Logistic_Facilities_Distribution_Analysis/assets/72640326/34351d2d-5505-453e-b9b1-246aa1d45212)

Os índices de Moran locais para a variável Densidade de empresas revelaram a presença de dois clusters estatisticamente significativos. Um HH, no qual as regiões com atributos com valores altos estão cercadas por outras regiões com atributos com valores altos, e um LL, no qual as regiões com atributos com valores baixos estão cercadas por outras regiões com atributos com valores baixos.

![image](https://github.com/manoel-nto/Logistic_Facilities_Distribution_Analysis/assets/72640326/50b334f5-a97a-43a2-a42b-8738e090a253)

Para investigar a relação entre a localização das empresas e a infraestrutura de transporte foram realizadas duas análises. Primeiramente, foi analisada a distribuição das empresas em relação às rodovias, com objetivo de entender a influência da 
proximidade das rodovias na localização. Em seguida, com as variáveis Densidade de empresas e Densidade da rede viária, foi feita a análise com os índices de Moran (global e locais).

A maioria das empresas está localizada a até 1 km de uma rodovia.

![image](https://github.com/manoel-nto/Logistic_Facilities_Distribution_Analysis/assets/72640326/7964b805-45c5-4206-a5ca-da2a8ee2d2ec)

A análise do Moran’s I bivariado para as variáveis Densidade de empresas e Densidade da rede viária revelou um grau baixo de associação espacial, próximo de zero. O índice global foi de -0,01 com p-valor > 0.05, indicando que não há evidências suficientes para rejeitar a hipótese nula de aleatoriedade espacial.

![image](https://github.com/manoel-nto/Logistic_Facilities_Distribution_Analysis/assets/72640326/08a71ede-f9e3-46a5-928d-dfcc4781638c)

Nos índices locais, destaca-se o cluster LL, no qual as regiões com valores baixos da primeira variável (Densidade da rede viária) estão cercadas por outras regiões com valores baixos da segunda variável (Densidade de empresas).

![image](https://github.com/manoel-nto/Logistic_Facilities_Distribution_Analysis/assets/72640326/376de9e4-4a2f-466c-9f71-1c271108e70c)

A análise dos pontos que identificam as empresas do setor de transporte e armazenamento do DF evidencia a concentração desses pontos em áreas ao sudoeste da região. Uma explicação possível para isso é o zoneamento do DF, no qual as zonas urbanas, destinadas à atividade comercial e de prestação de serviços, estão localizadas majoritariamente ao sudoeste do DF:

![image](https://github.com/manoel-nto/Logistic_Facilities_Distribution_Analysis/assets/72640326/0fd9b7ea-3bee-46e7-a5a2-8578273c5d57)

<!-- headings -->
<a id='item-six'></a>
## Conclusões e recomendações

A análise trouxe elementos importantes que contribuem para gestores de empresas logísticas e formuladores de políticas públicas, que são: 
1) A identificação de uma área de concentração logística no DF
2) A proximidade dos estabelecimentos logísticos em relação às rodovias
3) A zoneamento como um possível fator de influência na localização das instalações

Projetos futuros podem ser conduzidos de modo a melhorar a identificação das instalações logísticas no DF, como o uso de imagens de satélite para verificar visualmente a existência das instalações. 

Além disso, a adição de outras variáveis relacionadas às características das instalações, como porte e tipo de instalação, pode fornecer outros insights, assim como outras características da região de estudo, como níveis menores de zoneamento e categorias de uso de solo nas regiões administrativas.

<!-- headings -->
<a id='item-seven'></a>
## Referências

ANSELIN, Luc. Local indicators of spatial association—LISA. Geographical analysis, [s. l.], v. 27, n. 2, p. 93–115, 1995.

ANSELIN, Luc; REY, Sergio J. Modern spatial econometrics in practice: A guide to GeoDa, GeoDaSpace and PySAL 2014. 

GUERIN, Leonardo et al. The geography of warehouses in the São Paulo Metropolitan Region and contributing factors to this spatial distribution. Journal of Transport Geography, [s. l.], v. 91, 2021. 

HEITZ, Adeline et al. Spatial patterns of logistics facilities in Gothenburg, Sweden. Journal of Transport Geography, [s. l.], v. 88, 2020. 

DE SMITH, M; GOODCHILD, M; LONGLEY, P. Geospatial analysis: a comprehensive guide to principles, techniques and software tools sixth edition. [S. l.]: Troubador Publishing LTD, 2021.    

LONGLEY, Paul A et al. Geographic information science and systems. [S. l.]: John Wiley & Sons, 2015.

YUILL, Robert S. The Standard Deviational Ellipse; an updated tool for spatial description. Geografiska Annaler: Series B, Human Geography, [s. l.], v. 53, n. 1, p. 28–39, 1971. 
