# API - Dados geo-referenciados
Dois códigos, no R, para encontrar as coordenadas geográficas de regiões ou pontos. Os códigos são referentes aos sites cepaberto e googlemaps.  

# Código cepaberto

Usar o API do site CEPaberto é simples, vamos precisar apenas de 2 pacotes
  - httr,
  - rjson. 

Além disso, usaremos as funções
  - GET, content (httr), 
  - fromJSON (rjson). 
  
Primeiro defina as seguintes variáveis
 - token: chave de identificação pessoal fornecida pelo cepaberto quando você se cadastra no site.
 - query: endereço do site que especifica o CEP que buscamos obter os dados. 
 
Note que sempre que quiser buscar informações relacionadas a outros CEPs basta alterar o número do CEP na query
- “cep?cep=cep desejado”

Com base nestas variáveis podemos usar a função GET para nos conectar ao site, note que o url que vamos usar é o que está presente na query, além disso precisamos de uma autorização com base no token, por isso utilizamos a opção add_headers(). Assim, obtemos uma requisição do site.

A partir dessa requisição usamos a função content para extrair as informações definidas como texto que estão no formato JSON. Assim, essa retornará um objeto também neste formato e para convertê-lo em um objeto do R (lista) usamos a função fromJSON.

Por fim, retiramos as informações necessárias da lista e as colocamos em um dataframe.

Note que se o CEP for inválido a função fromJSON retornará um erro. Para evitá-lo basta verificarmos o status da busca realizada. De modo que se este for válido   

# Código googlemaps
