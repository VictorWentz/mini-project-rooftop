# Projeto RoofTop 
<sub>Disclaimer: Este é um projeto fictício, apenas para aprendizado</sub>

**Membros do projeto:**
- [Alan Moraes](https://www.linkedin.com/in/alanrfkmoraes/)
- [Alessandro Schereiber](https://www.linkedin.com/in/alessandro-schereiber-439699228)
- [Felipe Melo](http://linkedin.com/in/felipe-melo-1160b525)
- [Tainá Soares](https://www.linkedin.com/in/tain%C3%A1-soares-a9212a135/)
- [Thales Alencar](https://www.linkedin.com/in/thales-alencar)
- [Victor Wentz](https://www.linkedin.com/in/victor-wentz/)

# Contextualização
A [ROOFTOP](https://www.rooftop.com.br/) é uma das maiores empresas do ramo de investimentos imobiliário brasileiro, e quer expandir sua área de atuação fazendo um ivestimento internacional, com isso, ela contratou nosso time, para uma consultoria estratégica. A empresa irá investir em imóveis no Condado de County, nos Estados Unidos.

# Objetivo
O objetivo desta analise, é identificar os 5 imóveis que a empresa ROOFTOP deve fazer o investimento e o porquê, da mesma forma, devemos elencar os 5 imóveis que não recomendamos o investimento.

# Dataset
O dataset utilizado neste projeto, foi retirado do [geodacenter](https://geodacenter.github.io/data-and-lab/data/kingcounty.zip), e informações de localidade de cada zipcode, e outras tabelas, podem ser encontradas no site [King County GIS Open Data](https://gis-kingcounty.opendata.arcgis.com/), onde é compilado as mais diversas informações sobre o Condado de County.

## Dicionário das variáveis:
|     **Name**    	| **Type** 	|                        **Descripton**                       	|
|:---------------:	|:--------:	|:-----------------------------------------------------------:	|
|       _Id_      	|   int64  	|                Identificador único do imóvel                	|
|      _Date_     	|  object  	|                        Data da venda                        	|
|     _Price_     	|  float64 	|                        Preço da venda                       	|
|    _Bedrooms_   	|   int64  	|                        N° de Quartos                        	|
|   _Bathrooms_   	|  float64 	|                       N° de Banheiros                       	|
|  _Sqft_living_  	|   int64  	|               Tamanho da área habitável em ft²              	|
|    _Sqft_lot_   	|   int64  	|                  Tamanho do terreno em ft²                  	|
|     _Floors_    	|  float64 	|                      Número de andares                      	|
|   _Waterfront_  	|   int64  	|               '1' se é beira-mar, '0' se não.               	|
|      _View_     	|   int64  	|         Grau de quão belo é a vista do imóvel(0 a 4)        	|
|   _Condition_   	|   int64  	|                   Condição da casa (1 a 5)                  	|
|     _Grade_     	|   int64  	|           Classificação por qualidade do material           	|
|   _Sqft_above_  	|   int64  	|                  Área acima do solo em ft²                  	|
| _Sqft_basement_ 	|   int64  	|                  Área abaixo do solo em ft²                 	|
|    _Yr_built_   	|   int64  	|                      Ano de construção                      	|
|  _Yr_renovated_ 	|   int64  	|         Ano de restauração. '0' se nunca restaurada         	|
|    _Zipcode_    	|   int64  	|                           Zipcode                           	|
|      _Lat_      	|  float64 	|                           Latitude                          	|
|      _Long_     	|  float64 	|                          Longitude                          	|
| _Sqft_living15_ 	|   int64  	| Média de área habitável dos 15 imóveis mais póximos, em ft² 	|
|   _Sqft_lot15_  	|   int64  	|  Média da área do lote dos 15 imóveis mais próximos, em ft² 	|
|                 	|          	|                                                             	|

# Insights
1. O atributo `_Id_`, possui duplicatas, isto nos informa que esta casa, ja foi comprada e vendida.
2. Os atributos `_Bathrooms_`[^bath], `_Floors_`[^floors], possui suas razões para serem do tipo `float64`.
3. Utilizando o `_zipcode_` e os _id_ duplicados, é possivel calcular um possivel potencial de valorização das regiões.
4. 




[^bath]: teste
[^floors]: teste2
