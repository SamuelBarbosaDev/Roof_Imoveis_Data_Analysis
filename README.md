# Roof Imóveis:
### Índice

- [Contextualização](#contextualização)
- [Metodologia Aplicada](#metodologia-aplicada)
- [Entendimento do Negócio Aplicada](#metodologia-aplicada)
  - [Metricas](#metricas)
- [Entendimento dos Dados](#entendimento-dos-dados)
  - [Variáveis](#variáveis)
  - [Variáveis Escolhidas](#variáveis-Escolhidas)
- [Preparação dos Dados](#preparação-dos-dados)
  - [Alterando para int a coluna bathrooms](#alterando-para-int-a-coluna-bathrooms)
  - [Alterando para int a coluna floors](#alterando-para-int-a-coluna-floors)
  - [IDs repetidos](#ids-repetidos)
  - [As 5 cidades com a maior concentração de imóveis](#as-5-cidades-com-a-maior-concentração-de-imóveis)
  - [As 5 cidades com o ft2 mais caro](#as-5-cidades-com-o-ft2-mais-caro)
  - [As 5 cidades com os maiores terrenos](#as-5-cidades-com-os-maiores-terrenos)
- [Modelagem](#modelagem)
    - [Ranqueamento das lojas](#ranqueamento-das-lojas)
- [Avaliação](#avaliação)
- [Implantação](#implantação)
- [Conclusão](conclusão)
    - [Os 5 recomendados](#os-5-recomendados)
    - [Os 5 que **NÃO** recomendados](#os-5-que-não-recomendados)
- [Ambiente virtual e Dependências](#ambiente-virtual-e-dependências)


### Contextualização:
Roof Imóveis é uma das maiores empresas do ramo imobiliário Brasileiro
e quer expandir sua área de atuação fazendo um investimento internacional,
com isso, ela contratou você para uma consultoria estratégica.
A empresa irá investir em imóveis no Condado de County, nos Estados
Unidos. 

### Metodologia Aplicada:
A análise foi realizada utilizando o modelo CRISP-DM, o CRISP-DM (Cross Industry Standard Process for Data Mining) é um modelo padrão de processo para projetos de mineração de dados que define um conjunto de fases e tarefas que devem ser executadas para desenvolver soluções de mineração de dados efetivas.

![CRISP-DM](/core/img/CRISP-DM.png)

O modelo CRISP-DM é uma abordagem sistemática e estruturada para a mineração de dados que ajuda as empresas a desenvolver soluções de mineração de dados de maneira eficiente e eficaz, reduzindo o tempo e os custos do projeto.

### Entendimento do Negócio:
A Roof Imóveis busca expandir sua atuação
no mercado imobiliário internacional e
contratou uma consultoria estratégica para
investir em imóveis no Condado de King, nos
Estados Unidos. 

### Metricas:
1. **Localização**: o imóvel deve estar em uma das 10 cidades mais populosas de Washington.
2. **Valor do metro quadrado**: deve ser menor que a média da cidade.
3. **Preço**: deve ser menor que a média da cidade.
4. **Condição do imóvel**: a condição do imóvel deve ser igual a 5.
5. **Tamanho do terreno**: deve ser maior que a média da cidade.
6. **Quantidade de quartos**: deve ser maior que a média da cidade.
7. **Quantidade de banheiros**: deve ser maior que a média da cidade.
8. **Ano de construção**: deve ser maior que 1980.

## Entendimento dos Dados:
### Variáveis:
![Data Frame](/core/img/descrição_do_df.png)

### Variáveis Escolhidas:
![Data Frame](/core/img/variáveis_escolhidas.png)

## Preparação dos Dados:
### Alterando para int a coluna bathrooms:
1. Ao iniciar a análise dos dados, deparei-me com a
coluna "bathrooms" e percebi que havia informações
referentes a casas com, por exemplo, 2.25, 4.50, 1.75
banheiros. Esses valores não faziam sentido para a
minha análise. Então, optei por convertê-los em
números inteiros. Lembrando que pesquisei e
descobri que esses dados significam que o banheiro
em questão não é completo, ou seja, possui todos os
itens que um banheiro normalmente tem, exceto
pelo chuveiro, a pia ou o vaso sanitário. Apesar
disso, concluí que esses dados não eram relevantes
para a minha análise.

### Alterando para int a coluna floors:
2. Posteriormente, encontrei uma situação
semelhante na coluna "floors", onde havia
informações referentes a casas com 1.5, 2.5, 3.5
andares. Como essa coluna indicava o número de
andares da casa, optei por convertê-los em números
inteiros também.

### IDs repetidos:
3. Ao analisar o data frame, identifiquei 353 imóveis
que haviam sido vendidos mais de uma vez. Uma das
métricas sugeridas foi a valorização desses imóveis.
No entanto, optei por ignorar essa métrica por dois
motivos. Primeiramente, uma valorização passada
não necessariamente indica uma valorização futura.
Além disso, dos 21613 imóveis analisados, apenas
353 haviam sido vendidos mais de uma vez.
Portanto, optei por remover os IDs duplicados.

### As 5 cidades com a maior concentração de imóveis:
![Data Frame](/core/img/as_5_cidades_com_a_maior_concentração_de_imóveis.png)

### As 5 cidades com o ft2 mais caro:
![Data Frame](/core/img/as_5_cidades_com_a_maior_o_valor_do_ft2_por_cidade.png)

### As 5 cidades com os maiores terrenos:
![Data Frame](/core/img/as_5_cidades_com_a_maior_o_tamanho_do_terreno_por_cidade.png)


## Modelagem:
### Ranqueamento das lojas:
Por fim, mas não menos importante, criei um algoritmo de ranqueamento de imóveis. Esse algoritmo consiste em atribuir notas aos imóveis filtrados previamente. Cada critério estipulado tem um peso maior ou menor dependendo do caso, sendo que a nota máxima que um imóvel pode receber é 100.

Antes de atribuirmos notas aos imóveis, precisamos filtrar os dados. Como temos mais de 21 mil linhas, utilizei os seguintes filtros: condição mínima igual a 5, ano de construção maior ou igual a 1980, número de quartos maior ou igual a 1, número de banheiros maior ou igual a 1 e preço máximo menor ou igual a 1 milhão. Após a filtragem, chegou o momento de ranquear os imóveis.

Os critérios utilizados para ranqueá-los foram:
- **A Localização**, se o imóvel está dentro das 10 cidades mais populosas, ele ganha 30 pontos;
- **O valor do ft2**, se o imóvel estiver com um valor do ft2 abaixo da média da cidade, concluo que
ele está subvalorizado e ganhará mais 30 pontos;
- **O tamanho do terreno**, se o imóvel for maior que a média da cidade, ganhará mais 20 pontos;
- **O número de quartos**, se o imóvel tiver mais quartos que a média da cidade, ganhará mais 10
pontos;
- **O número de banheiros**, se o imóvel tiver mais banheiros que a média da cidade, ganhará mais
10 pontos.

Critérios  | Notas
--------- | ----
Cidade    | 30
Valor do ft2    | 30
Tamanho do terreno    | 20
Quartos    | 10
Banheiros    | 10

## Avaliação:
Para escolher os imóveis recomendados e não recomendados, utilizei os critérios definidos acima, como localização, valor do ft2, tamanho do terreno, número de quartos e número de banheiros.

No caso dos imóveis recomendados, escolhi aqueles com valores do pé quadrado abaixo da média da cidade e que estão localizados em Seattle, que é uma das 10 cidades mais populosas dos Estados Unidos. Além disso, todos os imóveis possuem tamanho do terreno maior que a média da cidade, número de quartos maior que a média da cidade e número de banheiros maior que a média da cidade, o que contribuiu para que esses imóveis recebessem notas altas no algoritmo de ranqueamento.

Já para os imóveis não recomendados, escolhi aqueles com valores do pé quadrado muito acima da média da cidade ou que estão localizados em cidades que não estão entre as 10 mais populosas dos Estados Unidos, como Vashon e North Bend. Além disso, esses imóveis possuem tamanho do terreno menor que a média da cidade, número de quartos menor que a média da cidade e número de banheiros menor que a média da cidade, o que contribuiu para que esses imóveis recebessem notas baixas no algoritmo de ranqueamento.

## Implantação:
Para obtermos uma análise mais precisa, é necessário definir qual é o objetivo da compra do imóvel: revenda, aluguel ou uso próprio. Além disso, é importante identificar o público-alvo, como casais sem filhos, casais com filhos, solteiros ou estudantes. Também é necessário definir o tipo de imóvel desejado, se é de alto padrão ou popular, e qual o valor máximo do investimento.

Em relação aos dados, seria mais simples se tivéssemos acesso ao valor do metro quadrado por cidade. É importante observar se os imóveis recomendados estão bem localizados, por exemplo, se há escolas próximas e se estão próximos ao centro da cidade, entre outros fatores.

## Conclusão:
### Os 5 recomendados:
1. > **O imóvel de ID: 2144800146** está localizado em Seattle, sendo vendido por $257500.0 com valor do pé quadrado de $27.587315191772017, tamanho do terreno de 9334, 3 quarto(s) e 2 banheiro(s), com área habitável de 1300.
2. > **O imóvel de ID: 3348401382** está localizado em Seattle, sendo vendido por $318000.0 com valor do pé quadrado de $25.11451587426947, tamanho do terreno de 12662, 3 quarto(s) e 2 banheiro(s), com área habitável de 1690.
3. > **O imóvel de ID: 2826049260** está localizado em Seattle, sendo vendido por $482500.0 com valor do pé quadrado de $63.270390768423816, tamanho do terreno de 7626, 4 quarto(s) e 3 banheiro(s), com área habitável de 1630.
4. > **O imóvel de ID: 4022902715** está localizado em Seattle, sendo vendido por $525000.0 com valor do pé quadrado de $51.08494696895981, tamanho do terreno de 10277, 5 quarto(s) e 3 banheiro(s), com área habitável de 2480.
5. > **O imóvel de ID: 5067400032** está localizado em Seattle, sendo vendido por $550000.0 com valor do pé quadrado de $38.19444444444444, tamanho do terreno de 14400, 3 quarto(s) e 2 banheiro(s), com área habitável de 3070.

### Os 5 que **NÃO** recomendados:
1. > **O imóvel de ID: 3523029059** está localizado em Vashon, sendo vendido por $181000.0 com valor do pé quadrado de $16.748403812343852, tamanho do terreno de 10807, 2 quarto(s) e 1 banheiro(s), com área habitável de 1560.
2. > **O imóvel de ID: 913000340** está localizado em Seattle, sendo vendido por $252000.0 com valor do pé quadrado de $153.84615384615384, tamanho do terreno de 1638, 1 quarto(s) e 1 banheiro(s), com área habitável de 680.
3. > **O imóvel de ID: 9407110710** está localizado em North Bend, sendo vendido por $322000.0 com valor do pé quadrado de $38.333333333333336, tamanho do terreno de 8400, 3 quarto(s) e 1 banheiro(s), com área habitável de 1510.
4. > **O imóvel de ID: 2028700265** está localizado em Seattle, sendo vendido por $505000.0 com valor do pé quadrado de $132.33752620545073, tamanho do terreno de 3816, 2 quarto(s) e 1 banheiro(s), com área habitável de 1310.
5. > **O imóvel de ID: 4083802195** está localizado em Seattle, sendo vendido por $578888.0 com valor do pé quadrado de $144.722, tamanho do terreno de 4000, 2 quarto(s) e 2 banheiro(s), com área habitável de 1060.


## Ambiente virtual e Dependências:
Criando ambiente virtual:
```
python3 -m venv core/.venv
```

Entrando no ambiente virtual:
```
source core/.venv/bin/activate
```

Instale as dependências:
```
pip install -r core/requirements.txt
```
---
Linkedin: <https://www.linkedin.com/in/samuel-barbosa-dev/> 

E-mail: <samueloficial@protonmail.com>