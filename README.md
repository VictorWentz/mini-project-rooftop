# Projeto RoofTop 
<sub>Disclaimer: Este é um projeto fictício, apenas para aprendizado, os resultados deste projeto, não devem ser levados em consideração em nenhuma hipotese.</sub>

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

|  **Região** 	| **Q°** 	| **Valorização** 	|
|:-----------:	|:------:	|:---------------:	|
|   SEATTLE   	|   86   	|     0.472714    	|
|    RENTON   	|   17   	|     0.499191    	|
| FEDERAL WAY 	|   11   	|     0.519285    	|
|   BELLEVUE  	|   11   	|     0.207804    	|
|     KENT    	|    8   	|     0.611788    	|

# Métricas de escolha
1. Valor das casas não pode passar de um milhão de dólares.
2. Investir em casas com `_grade_` acima de 6.
3. Investir em casas que estão nas regiões mais bem valorizadas.
4. Investir em casas novas, ou reformadas recentemente (a partir de 2005)

# Rank
Depois de todo processo de analise e limpeza dos dados, nosso dataset reduziu para 1834 moradias para investir, e para nos ajudar a escolher, utilizamos uma função da biblioteca pandas chamada rank[^rank], ela nos permite definir regras de negocios para cada atributo do dataset, i.e, casas com o preço menor, terão um rank maior.

# Conclusão
Ao final do processo, escolhemos 5 casas mais bem rankeadas, 5 casas piores rankedas e as 5 casas com os menores preços.
Em todo investimento, é fundamental não colocar todo o dinheiro em um único lugar, portanto é preciso diversificar. Notamos que as casas com menores preços, possuem o rank melhor que as piores rankeadas. Portanto nossa escolha de investimento, vai ser entre 2 casas melhores rankeadas, e 3 casas baratas.

Já as 5 casas para não investir, são aquelas casas que são caras, e possuem uma pessima qualidade de material, e de condição. Além das casas que ficam em regiões desvalorizadas.

## 5 Casas para investir

- id: 9320900610: 169th Place Southeast, Bellevue, King County
- id: 722059020: 9420, South 218th Street, Kent, King County
- id: 9320900610: 33266, 22nd Court Southwest, Twin Lakes, Federal Way
- id: 6056100165: 4065, Martin Luther King Junior Way South, Rainier Vista, Seattle
- id: 6056100160: 4055, Martin Luther King Junior Way South, Rainier Vista, Seattle

## 5 Casas para não investir

- id: 7167000040: 26719, Southeast 271st Street, Ravensdale, King County
- id: 742000060: 16929, Northeast 82nd Street, Redmond, King County
- id: 6613000935: 4437, 55th Avenue Northeast, Laurelhurst, Seattle
- id: 9808700025: 3873, 95th Avenue Northeast, Yarrow Point, King County
- id: 7237550310: 25005, Northeast Patterson Way, Union Hill-Novelty Hill, King County







[^bath]: [What does 2.5 bathrooms mean?](https://www.quora.com/What-does-2-5-bathrooms-mean)
[^floors]: [What is a 1.5 Storey House?](https://www.gimme-shelter.com/what-is-a-1-5-storey-house-50104/#:~:text=A%20one-and-a-,a%20%E2%80%9Chalf%20storey%20house%E2%80%9D)
[^rank]: [Rank](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.rank.html)
