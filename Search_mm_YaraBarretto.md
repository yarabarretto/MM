---
title: "Avalia��o T�cnica Analista de Dados - MaxMilhas"
author: "Yara Barretto"
date: "7/18/2018"
output: 
  html_document: 
    keep_md: TRUE
---

# An�lises propostas:

###An�lise 1: Tempos de Resposta das Buscas

1) Qual � a an�lise:  
    Analisar o tempo de resposta entre o in�cio e fim da busca e entre fim da busca e recebimento.

2) Motiva��o da an�lise:  
    Verificar se as buscas demoram a trazer resultados.   
    Identificar padr�es de buscas que se mostram mais efetivos, identificar tamb�m quais padr�es de buscas s�o menos efetivos.  
    Identificar pontos onde a busca pode ser melhorada.  

3) Como executar:   
- Verificar outliers e seu volume, como tempo de respostas negativos ou muito longos  
- Criar novo DataFrame com os dados, excluindo os outliers (caso seu volume seja baixo), para obtermos estat�sticas descritivas mais corretas e realistas.    
- Realizar um summary na coluna 'qtd_voos_recebidos', para obtermos resumo simples dos dados, como Min., Max., 1st Qu. Mediana, M�dia, 3st Qu. e quantidade de NAs(dados n�o retornados).  
- Verificar quantidade de 'missing values', caso a quantidade for muito alta, procurar identificar porque o dado - Plotar gr�ficos para verificar correla��es entre as vari�veis dispon�veis para an�lise e o tempo de resposta entre o in�cio e o fim da busca e entre o fim da busca e o recebimento, exemplos:   
      - Tempo de resposta x Qtd de voos recebidos
      - Tempo de resposta x voos nacionais
      - Tempo de resposta x voos internacionais
      - Tempo de resposta x N�mero de passageiros
      - Tempo de resposta x Dias da semana
      - Tempo de resposta x Dias da semana + Hor�rio
      - Tempo de resposta x Usu�rio com id identificado
      - Tempo de resposta x Usu�rio com id n�o identificado
      - Tempo de resposta x Tipo de Voo   
- Verificar quais vari�veis afetam mais o tempo de resposta da busca.  
- Aprofundar a an�lise em alguns pontos mais relevantes.  
- Buscar e propor solu��es para a melhoria do tempo de resposta.  
- Propor novos dados a serem guardados nas buscas para que possa auxiliar em an�lises futuras.   
    
###An�lise 2: Quantidade de Voos Retornados nas Buscas
1) Qual � a an�lise:  
    Analisar a quantidade de voos que s�o retornados nas buscas mais realizadas, analisar tamb�m se h� padr�o de buscas que retornam poucos resultado.

2) Motiva��o da an�lise:  
    Verificar se as buscas mais realizadas trazem quantidade considerada como ideal para o cliente que est� realizando a pesquisa.   
    Identificar padr�es de buscas que retornam mais resultados e padr�es de buscas que retornam menos resultados.

3) Como executar:  
- Verificar outliers e seu volume, como volume de voos retornados negativos ou > 400.
- Criar novo DataFrame com os dados, excluindo os outliers (caso seu volume seja baixo), para obtermos estat�sticas descritivas mais corretas e realistas.
- Realizar um summary na coluna 'qtd_voos_recebidos', para obtermos resumo simples dos dados, como Min., Max., 1st Qu. Mediana, M�dia, 3st Qu. e quantidade de NAs(dados n�o retornados).
- Verificar quantidade de 'missing values', caso a quantidade for muito alta, verificar porque o dado n�o est� sendo armazenado. 
- Plotar gr�ficos para verificar correla��o entre as vari�veis dispon�veis para an�lise e a quantidade de voos recebidos, exemplos: 
      - Qtd de Voos Recebidos x Tipo de Voo
      - Qtd de Voos Recebidos x Classe
      - Qtd de Voos Recebidos x Direção
      - Qtd de Voos Recebidos x Número de passageiros
      - Qtd de Voos Recebidos x Dias da semana
      - Qtd de Voos Recebidos x Dias da semana + Horário
      - Qtd de Voos Recebidos x Usuário com id identificado
      - Qtd de Voos Recebidos x Usuário com id não identificado
      - Qtd de Voos Recebidos x Tempo de resposta 
- Verificar quais vari�veis mostram afetar o n�mero de voos recebidos.
- Aprofundar a an�lise nos pontos relevantes.
- Buscar e propor solu��es para retornar mais voos onde a quantidade � considerada pequena. Uma solu��o que pode ser buscada � a adi��o de novos fornecesores de voos.  
- Dentro dessa an�lise, pode-se verificar as quantidade de melhores pre�os na MaxMilhas, verificando se tem ou n�o rela��o com o n�mero de voos retornados.
- Propor novos dados a serem guardados nas buscas para que possa auxiliar em an�lises futuras. 
    
###An�lise 3: An�lise de Perfil do Buscador
1) Qual � a an�lise:  
    Usar os dados para encontrar um perfil dominante de buscador, e tamb�m perfis espec�ficos. Exemplo de Perfil: 'Voos nacionais, que saem de SP, com dura��o de 3 a 7 dias, 1 adulto de classe econ�mica com usu�rio n�o identificado'.  

2) Motiva��o da an�lise:  
    Priorizar corre��es e demandas das buscas relacionadas aos Perfis de busca dominantes.
    Cria��o de Campanhas para Perfis espec�ficos, com a possibilidade de an�lise clara dos resultados. 

3) Como executar:  
- Verificar quais dados podem ser usados para montagem do perfil.  
- Transformar dados que poss�veis de serem transformados em fator, para facilitar a visualiza��o dos dados no R.
- Analisar com summary as vari�veis escolhidas e plotar alguns resultados para que possam ser visualizados de forma mais clara.
- Montagem do Perfil com os resultados an�lisados no passo anterior.
- Montagem de Perfil diferente do dominante.
- Propor novos dados a serem guardados nas buscas para que possa auxiliar em an�lises futuras.  


##A an�lise escolhida para ser realizada � a An�lise 3

Preparando os dados para serem analisados:  



###Analisando Vari�veis
#####Usu�rios Identificados
Apenas 12% dos usu�rios que realizam buscam s�o identificados:   

| Buscas com Idusers | Buscas sem Idusers |
| ------------------ | ------------------ |
| *12%*              | *88%*              |

####Companhias A�reas
As companhias a�reas Azul, Gol e Tam retornam volumes semelhantes, j� a Avianca retorna menos resultados:
![](Search_mm_YaraBarretto_files/figure-html/ciasaeras-1.png)<!-- -->

####Tipos de Voo
Nos tipos de Voos buscados, Ida e Volta apresenta volume 6% maior:
![](Search_mm_YaraBarretto_files/figure-html/tipo-1.png)<!-- -->

####Dias Entre Viagens
A m�dia de dias entre viagens � 5, por�m viagens muito compridas puxam a m�dia para cima, a mediana nos apresenta um resultado mais relista, no caso a mediana � 1 e 75% das viagens se concentram em at� 6 dias.

```
##      Min.   1st Qu.    Median      Mean   3rd Qu.      Max. 
##       0.0       0.0       1.0       4.9       6.0 2191460.0
```

![](Search_mm_YaraBarretto_files/figure-html/dias-1.png)<!-- -->

####Quantidade de Adultos
82% dos clientes buscam passagens para apenas uma pessoa, 15% para duas pessoas e apenas 3% para 3 pessoas ou mais.
![](Search_mm_YaraBarretto_files/figure-html/qtdadult-1.png)<!-- -->

####Quantidade de Crian�as e Beb�s
Apenas 6% dos clientes buscam passagens para crian�as, sendo que 4% delas buscam passagem para apenas uma crian�a.
Apenas 2% dos clientes buscam passagens incluindo beb�s.
Podemos ver nos histogramas abaixo que a maioria pesquisa passagem para apenas uma crian�a ou beb�.  
![](Search_mm_YaraBarretto_files/figure-html/qtdcb-1.png)<!-- -->![](Search_mm_YaraBarretto_files/figure-html/qtdcb-2.png)<!-- -->

####Voo Internacional x Voo Nacional
89% dos clientes buscam voos nacionais, 11% buscam voos internacionais.
![](Search_mm_YaraBarretto_files/figure-html/vooint-1.png)<!-- -->

####Dire��o dos Voos
89% dos clientes buscam voos nacionais, os outros 11% dividem em 9% saindo do Brasil e 2% voltando para o Brasil.
![](Search_mm_YaraBarretto_files/figure-html/dir-1.png)<!-- -->

####Classe
99,7% dos clientes buscam voos de classe econ�mica.
![](Search_mm_YaraBarretto_files/figure-html/classe-1.png)<!-- -->


###Perfil Encontrado
Podemos dizer que o Perfil dominante do buscador �:  
Usu�rios n�o identificados buscando por passagens de ida e volta nacionais para apenas uma pessoa adulta com dura��o de 1 dia e para viajar de classe econ�mica.

###Perfil 2 - Clientes que buscam passagens internacionais
Podemos criar um novo Data Frame contendo somente as buscas internacionais e realizar a mesma an�lise.


#####Usu�rios Identificados
Apenas 12% dos usu�rios que realizam buscam s�o identificados, mesmo resultado apresentado no perfil dominante geral:   

| Buscas com Idusers | Buscas sem Idusers |
| ------------------ | ------------------ |
| *12%*              | *88%*              |

####Companhias A�reas
As companhias a�reas Tam, Gol e Azul, retornam volumes semelhantes, j� a Avianca retorna menos resultados:
![](Search_mm_YaraBarretto_files/figure-html/ciasaerasi-1.png)<!-- -->

####Tipos de Voo
Nos tipos de Voos buscados para viagens internacionais, Ida e Volta apresenta volume de 62%:
![](Search_mm_YaraBarretto_files/figure-html/tipoi-1.png)<!-- -->

####Dias Entre Viagens
A m�dia de dias entre viagens internacionais � 11, por�m viagens muito compridas puxam a m�dia para cima, a mediana nos apresenta um resultado mais relista, no caso a mediana � 5 e 75% das viagens se concentram em at� 11 dias. Temos muitos 0 na base, � um ponto que deve ser verificado.

```
##    Min. 1st Qu.  Median    Mean 3rd Qu.    Max. 
##     0.0     0.0     5.0    10.9    11.0   396.0
```

![](Search_mm_YaraBarretto_files/figure-html/diasi-1.png)<!-- -->

####Quantidade de Adultos
77% dos clientes que buscam passagens internacionais buscam para apenas uma pessoa, 19% para duas pessoas e apenas 3% para 3 pessoas ou mais.  
![](Search_mm_YaraBarretto_files/figure-html/qtdadulti-1.png)<!-- -->

####Quantidade de Crian�as e Beb�s
Apenas 5% dos clientes buscam passagens para crian�as, sendo que 4% delas buscam passagem para apenas uma crian�a.
Apenas 1% dos clientes buscam passagens incluindo beb�s.
Podemos ver nos histogramas abaixo que a maioria pesquisa passagem para apenas uma crian�a ou beb�.  
![](Search_mm_YaraBarretto_files/figure-html/qtdcbi-1.png)<!-- -->![](Search_mm_YaraBarretto_files/figure-html/qtdcbi-2.png)<!-- -->

####Dire��o dos Voos
79% dos Clientes buscam Voos internacionais partindo do Brasil, 18% partindo de outros pa�ses para o Brasil e 3% bucam voos com partidas e destinos internacionais.  
![](Search_mm_YaraBarretto_files/figure-html/diri-1.png)<!-- -->

####Classe
97,3% dos clientes buscam voos de classe econ�mica.
![](Search_mm_YaraBarretto_files/figure-html/classei-1.png)<!-- -->


###Perfil Encontrado
Podemos dizer que o Perfil dominante do buscador de passagens internacional �:  
Usu�rios n�o identificados buscando por passagens de ida e volta para apenas uma pessoa adulta com dura��o de m�dia de 11 dias e para viajar de classe econ�mica.


