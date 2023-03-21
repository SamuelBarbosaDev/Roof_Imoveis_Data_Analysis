# Roof Imóveis:
## Overview:
Primeiramente, definimos o público-alvo como casais com filhos. Em seguida, determinamos as métricas, como localização, preço, condições do imóvel, entre outros.

Com tudo isso em mente, iniciamos as análises e concluímos quais os cinco imóveis que deveriam ser investidos e por quê, e quais cinco não recomendaríamos o investimento de jeito nenhum.

## Os 5 imóveis que deveriam ser investidos:
1. > O imóvel de ID: 2144800146 está localizado em Seattle, o mesmo está sendo vendido por 257500.0 é o valor do pé quadrado é 27.587315191772017, o tamanho do terreno é 9334, ele tem 3 quarto(s) e 2 banheiro(s), por fim sua área habitável é de 1300.
2. > O imóvel de ID: 3348401382 está localizado em Seattle, o mesmo está sendo vendido por 318000.0 é o valor do pé quadrado é 25.11451587426947, o tamanho do terreno é 12662, ele tem 3 quarto(s) e 2 banheiro(s), por fim sua área habitável é de 1690.
3. > O imóvel de ID: 2826049260 está localizado em Seattle, o mesmo está sendo vendido por 482500.0 é o valor do pé quadrado é 63.270390768423816, o tamanho do terreno é 7626, ele tem 4 quarto(s) e 3 banheiro(s), por fim sua área habitável é de 1630.
4. > O imóvel de ID: 4022902715 está localizado em Seattle, o mesmo está sendo vendido por 525000.0 é o valor do pé quadrado é 51.08494696895981, o tamanho do terreno é 10277, ele tem 5 quarto(s) e 3 banheiro(s), por fim sua área habitável é de 2480.
5. > O imóvel de ID: 5067400032 está localizado em Seattle, o mesmo está sendo vendido por 550000.0 é o valor do pé quadrado é 38.19444444444444, o tamanho do terreno é 14400, ele tem 3 quarto(s) e 2 banheiro(s), por fim sua área habitável é de 3070.

## Os 5 imóveis que NÃO deveriam ser investidos:
1. > O imóvel de ID: 3523029059 está localizado em Vashon, o mesmo está sendo vendido por 181000.0 é o valor do pé quadrado é 16.748403812343852, o tamanho do terreno é 10807, ele tem 2 quarto(s) e 1 banheiro(s), por fim sua área habitável é de 1560.
2. > O imóvel de ID: 913000340 está localizado em Seattle, o mesmo está sendo vendido por 252000.0 é o valor do pé quadrado é 153.84615384615384, o tamanho do terreno é 1638, ele tem 1 quarto(s) e 1 banheiro(s), por fim sua área habitável é de 680.
3. > O imóvel de ID: 9407110710 está localizado em North Bend, o mesmo está sendo vendido por 322000.0 é o valor do pé quadrado é 38.333333333333336, o tamanho do terreno é 8400, ele tem 3 quarto(s) e 1 banheiro(s), por fim sua área habitável é de 1510.
4. > O imóvel de ID: 2028700265 está localizado em Seattle, o mesmo está sendo vendido por 505000.0 é o valor do pé quadrado é 132.33752620545073, o tamanho do terreno é 3816, ele tem 2 quarto(s) e 1 banheiro(s), por fim sua área habitável é de 1310.
5. > O imóvel de ID: 4083802195 está localizado em Seattle, o mesmo está sendo vendido por 578888.0 é o valor do pé quadrado é 144.722, o tamanho do terreno é 4000, ele tem 2 quarto(s) e 2 banheiro(s), por fim sua área habitável é de 1060.

## Observações:
Para obtermos uma análise mais precisa, é necessário definir qual é o objetivo da compra do imóvel: revenda, aluguel ou uso próprio. Além disso, é importante identificar o público-alvo, como casais sem filhos, casais com filhos, solteiros ou estudantes. Também é necessário definir o tipo de imóvel desejado, se é de alto padrão ou popular, e qual o valor máximo do investimento.

Em relação aos dados, seria mais simples se tivéssemos acesso ao valor do metro quadrado por cidade. É importante observar se os imóveis recomendados estão bem localizados, por exemplo, se há escolas próximas e se estão próximos ao centro da cidade, entre outros fatores.

## Possíveis públicos-alvo:
- Casais sem filhos
- Casais com filhos
- Solteiros
- Estudantes

## Métricas de avaliação do imóvel:
1. Localização: o imóvel deve estar em uma das 10 cidades mais populosas de Washington.
2. Valor do metro quadrado: deve ser menor que a média da cidade.
3. Preço: deve ser menor que a média da cidade.
4. Condição do imóvel: a condição do imóvel deve ser igual a 5.
5. Tamanho do terreno: deve ser maior que a média da cidade.
6. Quantidade de quartos: deve ser maior que a média da cidade.
7. Quantidade de banheiros: deve ser maior que a média da cidade.
8. Ano de construção: deve ser maior que 1980.

## Insights técnicos da análise:
1. Ao iniciar a análise dos dados, deparei-me com a coluna `bathrooms` e percebi que havia informações referentes a casas com, por exemplo, 2.25, 4.50, 1.75 banheiros. Esses valores não faziam sentido para a minha análise. Então, optei por convertê-los em números inteiros. Lembrando que pesquisei e descobri que esses dados significam que o banheiro em questão não é completo, ou seja, possui todos os itens que um banheiro normalmente tem, exceto pelo chuveiro, a pia ou o vaso sanitário. Apesar disso, concluí que esses dados não eram relevantes para a minha análise.

2. Posteriormente, encontrei uma situação semelhante na coluna `floors`, onde havia informações referentes a casas com 1.5, 2.5, 3.5 andares. Como essa coluna indicava o número de andares da casa, optei por convertê-los em números inteiros também.

3. Ao analisar o dataframe, identifiquei 353 imóveis que haviam sido vendidos mais de uma vez. Uma das métricas sugeridas foi a valorização desses imóveis. No entanto, optei por ignorar essa métrica por dois motivos. Primeiramente, uma valorização passada não necessariamente indica uma valorização futura. Além disso, dos 21613 imóveis analisados, apenas 353 haviam sido vendidos mais de uma vez. Portanto, optei por remover os IDs duplicados.

4. Por fim, mas não menos importante, criei um `algoritmo de ranqueamento de imóveis`. Esse algoritmo consiste em atribuir notas aos imóveis filtrados previamente. Cada critério estipulado tem um peso maior ou menor dependendo do caso, sendo que a nota máxima que um imóvel pode receber é 100. Antes de atribuirmos notas aos imóveis, precisamos filtrar os dados. Como temos mais de 21 mil linhas, utilizei os seguintes filtros: condição mínima igual a 5, ano de construção maior ou igual a 1980, número de quartos maior ou igual a 1, número de banheiros maior ou igual a 1 e preço máximo menor ou igual a 1 milhão. Após a filtragem, chegou o momento de ranquear os imóveis. Os critérios utilizados para ranqueá-los foram: `localização`, se o imóvel está dentro das 10 cidades mais populosas, ele ganha 30 pontos; `valor do ft2`, se o imóvel estiver com um valor do ft2 abaixo da média da cidade, concluo que ele está subvalorizado e ganhará mais 30 pontos; `tamanho do terreno`, se o imóvel for maior que a média da cidade, ganhará mais 20 pontos; `número de quartos`, se o imóvel tiver mais quartos que a média da cidade, ganhará mais 10 pontos; `número de banheiros`, se o imóvel tiver mais banheiros que a média da cidade, ganhará mais 10 pontos.

Critérios  | Notas
--------- | ----
Cidade    | 30
Valor do ft2    | 30
Tamanho do terreno    | 20
Quartos    | 10
Banheiros    | 10

---
Linkedin: <https://www.linkedin.com/in/samuel-barbosa-dev/> 

E-mail: <samueloficial@protonmail.com>
