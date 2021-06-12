# Vacinação no Brasil: O que Aprendemos com o Surto de Sarampo em 2014 <img src="https://img.icons8.com/ios/23/000000/syringe.png"/> <img src="https://img.icons8.com/ios/23/000000/brazil-map.png"/>

[<img src="https://img.shields.io/badge/author-Carolina%20Dias-FB3799?style=flat-square"/>](https://github.com/diascarolina) [<img src="https://img.shields.io/badge/carodias-0A66C2?style=flat-square&logo=linkedin&logoColor=white" />](https://www.linkedin.com/in/carodias/) [![Made withJupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange?style=flat-square&logo=Jupyter)](https://jupyter.org/try) [![GitHub license](https://img.shields.io/github/license/Naereen/StrapDown.js.svg?style=flat-square)](https://github.com/diascarolina/healthcare-analysis/blob/main/LICENSE)
 
![](https://raw.githubusercontent.com/diascarolina/vacinacao-geral-no-brasil/main/other/banner.jpg?token=AH6WME4BOFRN6LIHPSJL6KDAZVPJW)

# Sumário

- Introdução
-
-
-

# Introdução

<a>
	<img align="right" src="https://raw.githubusercontent.com/diascarolina/vacinacao-geral-no-brasil/main/other/syringe.png?token=AH6WMEZBFIPTIFQTPBFZKFDAZQRI6">
</a>

Já é de conhecimento de todos que o principal assunto dos últimos meses, nos quais estamos vivendo em uma pandemia de Covid-19, é a vacinação. Diariamente checamos a quantidade de pessoas já vacinadas e aguardamos ansiosamente o momento em que poderemos dizer "Estou imunizado contra a Covid (com a PIFAIZÊR)". Mas será que já enfrentamos algo parecido? Em uma escala mundial talvez não recentemente, mas em uma escala regional não é a primeira vez que ficamos à mercê de doenças que poderiam ser evitadas com uma vacinação efetiva.

É nesse contexto que torna-se relevante olharmos para o passado e estudarmos casos anteriores de doenças que foram superadas com vacinas, as chamadas doenças imunopreveníveis, para que possamos traçar um paralelo com os dias de hoje, pois, como diria aquela famosa frase atribuída ao filósofo irlandês Edmund Burke, _"Aqueles que não conhecem a história estão fadados a repeti-la."_ Pelo surgimento e avanço de grupos anti-vacina e pelo comportamento de quem deveria estar liderando o país, parece que essa lição não foi aprendida.

Assim, dividimos o projeto em duas partes. Na primeira iniciamos com uma análise geral sobre os imunizantes mais aplicados e utilizados no calendário vacinal brasileiro, como uma forma de panorama geral sobre o [Programa Nacional de Imunização (PNI)](http://pni.datasus.gov.br/apresentacao.asp). Na segunda parte, focaremos nossa atenção no surto de sarampo ocorrido entre 2013 e 2015 nos estados de Pernambuco e no Ceará, buscando um paralelo, com lições e aprendizados que esse momento pode ter trazido para a atual pandemia de Covid-19 (ou, no caso, a falta de "aprendizado").

🟢 [Parte 1: Vacinação Geral no Brasil](https://github.com/diascarolina/vacinacao-geral-no-brasil/blob/main/notebooks/vacinacao_geral_no_brasil.ipynb)

🟢 [Parte 2: Surto de Sarampo no Brasil em 2014](https://github.com/diascarolina/vacinacao-geral-no-brasil/blob/main/notebooks/sarampo.ipynb)

# Dados

<a>
	<img align="right" src="https://raw.githubusercontent.com/diascarolina/vacinacao-geral-no-brasil/main/other/pni.png?token=AH6WME7VQUE662N2BI6F6Q3AZQQRQ">
</a>

Os dados utilizados nas análises foram obtidos através do dados abertos do Sistema Único de Saúde (SUS), mais especificamente os dados do [Programa Nacional de Imunização (PNI)](http://pni.datasus.gov.br/apresentacao.asp). Criado em 1973 pelo Ministério da Saúde, o PNI tem como objetivo coordenar as ações de imunizações em todo o território nacional, traçando diretrizes e prestando serviços integrais de saúde através de sua rede própria. É uma ferramenta essencial para a manutenção da saúde pública brasileira, tendo sido responsável por erradicar ou controlar diversas doenças imunopreveníveis, como o sarampo, a Hepatite B, e a Poliomielite.

Esses dados foram atualizados pela última vez em 04/09/2019. Uma versão mais recente desses dados pode ser encontrada nessa [página do DATASUS](http://tabnet.datasus.gov.br/cgi/tabcgi.exe?pni/cnv/cpniuf.def) que teve última atualização em 10/06/2021. Uma nova análise futura poderá utilizar esses dados mais recentes. Para uma melhor organização, coloquei a parte de limpeza dos dados em um notebook separado, onde os dados brutos eram importados e, após tratados, eram exportados em novos arquivos .csv limpos.

🟢 Os dados estão armazenados na pasta [```dados```](https://github.com/diascarolina/vacinacao-geral-no-brasil/tree/main/dados) desse repositório.

🟢 [Notebook em que foi feita a limpeza dos dados brutos](https://github.com/diascarolina/vacinacao-geral-no-brasil/blob/main/notebooks/limpeza_dados.ipynb)

Também há um documento com as [Notas Técnicas](http://tabnet.datasus.gov.br/cgi/pni/Imun_cobertura_desde_1994.pdf) para os dados. Nele encontramos a **origem** e a **descrição** de algumas variáveis presentes nos dados.

# Análise e Hipóteses

Na **Parte 1**, onde realizamos uma análise geral dos imunizantes no Brasil, foram levantadas as seguintes hipóteses para servirem como um guia para o caminho percorrido na análise:

> **Hipótese 1:** A cobertura vacinal vem crescendo anualmente em todo o país.
 
> **Hipótese 2:** Vacinas que devem ser aplicadas em bebês logo após o nascimento, como a [BCG e da Hepatite B](https://www.unimedlondrina.com.br/noticias/tudo-saude/07/06/2018/vacinas-importantes-recem-nascidos/), principalmente, possuem maior cobertura vacinal e também maior valor absoluto de aplicações.

Para seguirmos esse caminho, avaliamos a cobertura vacinal total no Brasil, no período de 1994 a 2019. Após isso, focamos no ano de 2015 por ser o que possui maior cobertura vacinal dentre esses anos. Ao fim, apresentamos uma linha do tempo de quando cada imunizantes foi introduzido no calendário vacinal brasileiro.

Já para a **Parte 2**, na qual tratamos sobre o surto de sarampo ocorrido entre 2013 e 2015 nos estados de Pernambuco e no Ceará, analisamos três parâmetros para cada um dos dois estados:
- Quantidade de Casos de Sarampo entre 1990 e 2019;
- Cobertura Vacinal entre 1994 e 2019;
- Valor Absoluto da Quantidade de Doses Aplicadas de vacinas contra o Sarampo de 1994 a 2019.

Ao final, fizemos uma comparação entre a quantidade de doses aplicadas de vacinas contra o sarampo e a quantidade de casos confirmados da doença.

Tínhamos como hipóteses para nos guiarem na análise:

> **Hipótese 1:** Antes do surto de sarampo iniciado em 2013, a cobertura vacinal de imunizantes contra o sarampo estava relativamente baixa a vários anos.

> **Hipótese 2:** Durante o surto de sarampo, de 2013 a 2015, a quantidade de vacinas aplicadas contra o sarampo aumentou bastante nos dois estados analisados e, como consequência, os casos diminuíram.
