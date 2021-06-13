# Vacinação no Brasil: O que Aprendemos com o Surto de Sarampo em 2014 <img src="https://img.icons8.com/ios/23/000000/syringe.png"/> <img src="https://img.icons8.com/ios/23/000000/brazil-map.png"/>

[<img src="https://img.shields.io/badge/author-Carolina%20Dias-FB3799?style=flat-square"/>](https://github.com/diascarolina) [<img src="https://img.shields.io/badge/carodias-0A66C2?style=flat-square&logo=linkedin&logoColor=white" />](https://www.linkedin.com/in/carodias/) [![Made withJupyter](https://img.shields.io/badge/Made%20with-Jupyter-orange?style=flat-square&logo=Jupyter)](https://jupyter.org/try) [![GitHub license](https://img.shields.io/github/license/Naereen/StrapDown.js.svg?style=flat-square)](https://github.com/diascarolina/healthcare-analysis/blob/main/LICENSE)
 
![](https://raw.githubusercontent.com/diascarolina/vacinacao-geral-no-brasil/main/other/banner.jpg?token=AH6WME4BOFRN6LIHPSJL6KDAZVPJW)

# Sumário

1. [Introdução](#intro)
2. [Dados](#data)
3. [Análise & Hipóteses](#analise)
4. [Conclusões](#conc)
5. [O que aprendemos com isso?](#aprendemos)
6. [Ferramentas & Bibliotecas](#libs)
7. [Referências](#refs)
8. [Observações & Agradecimentos](#agra)
9. [Contatos](#contact)


<a name="intro"></a>
# 1 Introdução

<a>
	<img align="right" src="https://raw.githubusercontent.com/diascarolina/vacinacao-geral-no-brasil/main/other/syringe.png?token=AH6WMEZBFIPTIFQTPBFZKFDAZQRI6">
</a>

Já é de conhecimento de todos que o principal assunto dos últimos meses, nos quais estamos vivendo em uma pandemia de Covid-19, é a vacinação. Diariamente checamos a quantidade de pessoas já vacinadas e aguardamos ansiosamente o momento em que poderemos dizer "Estou imunizado contra a Covid (com a PIFAIZÊR)". Mas será que já enfrentamos algo parecido? Em uma escala mundial talvez não recentemente, mas em uma escala regional não é a primeira vez que ficamos à mercê de doenças que poderiam ser evitadas com uma vacinação efetiva.

É nesse contexto que torna-se relevante olharmos para o passado e estudarmos casos anteriores de doenças que foram superadas com vacinas, as chamadas doenças imunopreveníveis, para que possamos traçar um paralelo com os dias de hoje, pois, como diria aquela famosa frase atribuída ao filósofo irlandês Edmund Burke, _"Aqueles que não conhecem a história estão fadados a repeti-la."_ Pelo surgimento e avanço de grupos anti-vacina e pelo comportamento de quem deveria estar liderando o país, parece que essa lição não foi aprendida.

Assim, dividimos o projeto em duas partes. Na primeira iniciamos com uma análise geral sobre os imunizantes mais aplicados e utilizados no calendário vacinal brasileiro, como uma forma de panorama geral sobre o [Programa Nacional de Imunizações (PNI)](http://pni.datasus.gov.br/apresentacao.asp). Na segunda parte, focaremos nossa atenção no surto de sarampo ocorrido entre 2013 e 2015 nos estados de Pernambuco e no Ceará, buscando um paralelo, com lições e aprendizados que esse momento pode ter trazido para a atual pandemia de Covid-19 (ou, no caso, a falta de "aprendizado").

 
### 🟢 [Parte 1: Vacinação Geral no Brasil](https://github.com/diascarolina/vacinacao-geral-no-brasil/blob/main/notebooks/vacinacao_geral_no_brasil.ipynb)

### 🟢 [Parte 2: Surto de Sarampo no Brasil em 2014](https://github.com/diascarolina/vacinacao-geral-no-brasil/blob/main/notebooks/sarampo.ipynb)

### 🟢 [Análise Completa no Medium](https://carodias.medium.com/vacina%C3%A7%C3%A3o-no-brasil-o-que-aprendemos-com-o-surto-de-sarampo-em-2014-56d8518c3ef0)

<a name="data"></a>
# 2 Dados

<a>
	<img align="right" src="https://raw.githubusercontent.com/diascarolina/vacinacao-geral-no-brasil/main/other/pni.png?token=AH6WME7VQUE662N2BI6F6Q3AZQQRQ">
</a>

Os dados utilizados nas análises foram obtidos através do dados abertos do Sistema Único de Saúde (SUS), mais especificamente os dados do [Programa Nacional de Imunizações (PNI)](http://pni.datasus.gov.br/apresentacao.asp). Criado em 1973 pelo Ministério da Saúde, o PNI tem como objetivo coordenar as ações de imunizações em todo o território nacional, traçando diretrizes e prestando serviços integrais de saúde através de sua rede própria. É uma ferramenta essencial para a manutenção da saúde pública brasileira, tendo sido responsável por erradicar ou controlar diversas doenças imunopreveníveis, como o sarampo, a Hepatite B, e a Poliomielite.

Esses dados foram atualizados pela última vez em 04/09/2019. Uma versão mais recente desses dados pode ser encontrada nessa [página do DATASUS](http://tabnet.datasus.gov.br/cgi/tabcgi.exe?pni/cnv/cpniuf.def) que teve última atualização em 10/06/2021. Uma nova análise futura poderá utilizar esses dados mais recentes. Para uma melhor organização, coloquei a parte de limpeza dos dados em um notebook separado, onde os dados brutos eram importados e, após tratados, eram exportados em novos arquivos .csv limpos.

### 🟢 Os dados estão armazenados na pasta [```dados```](https://github.com/diascarolina/vacinacao-geral-no-brasil/tree/main/dados) desse repositório.

### 🟢 [Notebook em que foi feita a limpeza dos dados brutos](https://github.com/diascarolina/vacinacao-geral-no-brasil/blob/main/notebooks/limpeza_dados.ipynb)

Também há um documento com as [Notas Técnicas](http://tabnet.datasus.gov.br/cgi/pni/Imun_cobertura_desde_1994.pdf) para os dados. Nele encontramos a **origem** e a **descrição** de algumas variáveis presentes nos dados.

<a name="analise"></a>
# 3 Análise & Hipóteses

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

<a name="conc"></a>
# 4 Conclusões

🟢 **Parte 1: Vacinação Geral no Brasil**

Após essa análise, conseguimos obter algumas conclusões relevantes e também relacionadas as nossas hipóteses.

- **Hipótese 1:** A cobertura vacinal vem crescendo anualmente em todo o país.
> Por mais que tenhamos saído de uma média de menos de 40% em 1994 e chegado a quase 100% em 2015, de um ano para o outro também ocorreram diversas quedas nesse número. No geral podemos afirmar que sim, houve um expressivo aumento na cobertura vacinal de 1994 a 2015, mas não anualmente, e sim como um todo.

- **Hipótese 2:** Vacinas que devem ser aplicadas em bebês logo após o nascimento, como a [BCG e da Hepatite B](https://www.unimedlondrina.com.br/noticias/tudo-saude/07/06/2018/vacinas-importantes-recem-nascidos/), principalmente, possuem maior cobertura vacinal e também maior valor absoluto de aplicações.
> Observamos que os imunizantes BCG, Poliomielite e DTP foram os mais aplicados, em valores absolutos, no Brasil, de 1994 a 2019. Esses são, justamente, os aplicados em recém-nascidos. Isso se explica pois, ao serem aplicados já na maternidade, não há o risco de esquecimento ou falta de vontade para a aplicação dessas vacinas, como ocorre frequentemente com outras que são aplicadas em adultos.

Por último, em uma linha do tempo visualizamos quando determinados imunizantes foram introduzidos no calendário vacinal brasileiro e notamos que grande parte dos imunizantes foram introduzidos antes de 1994 (início da contabilização dos dados nessa base) e continuam os mesmos até a data de atualização em 2019. Esses são, por exemplo:
- **BCG** (Contra Tuberculose);
- **FA** (Contra Febre Amarela);
- **HB** (Contra Hepatite B);
- **VOP** (Oral Contra Poliomielite);
- **DTP** (Tríplice Bacteriana).

🟢 **Parte 2: Surto de Sarampo no Brasil em 2014**

Vimos que no período de 2013 a 2015 dois estados brasileiros sofreram com um surto de sarampo após não registrarem nenhum caso a quase 15 anos. Esses estados foram Pernambuco e Ceará. Tivemos a seguintes distribuição de casos:

**Estado** | 2013 | 2014 | 2015
--- | --- | --- | ---
**Pernambuco** | 200 casos | 24 casos | 0 casos
**Ceará** | 1 caso | 695 casos | 32 casos

Nesse período, se intensificaram as ações de combate à doença, aumentando a cobertura vacinal e a quantidade de doses aplicadas de vacinas contra o sarampo.

Em 2014 foram aplicadas 413.394 doses de imunizantes contra o Sarampo em Pernambuco e 503.619 doses no Ceará. A média de doses aplicadas contra o Sarampo entre 1994 e 2019 em Pernambuco foi de 216.214 e no Ceará a média foi de 230.200 doses.

Com essas informações fica claro que o número de doses aplicadas de imunizantes contra o sarampo no ano de 2014, pico no número de doses, foi mais do que duas vezes a média nos dois estados analisados entre 1994 e 2019.

Conseguimos analisar também as hipóteses propostas:

- **Hipótese 1:** Antes do surto de sarampo iniciado em 2013, a cobertura vacinal de imunizantes contra o sarampo estava relativamente baixa a vários anos.
> Isso não é verdade, estávamos com um longo período de cobertura vacinal a 100%, mas bastou um único ano com cobertura vacinal abaixo de 95% para que a doença se alastrasse pelos estados analisados.

- **Hipótese 2:** Durante o surto de sarampo, de 2013 a 2015, a quantidade de vacinas aplicadas contra o sarampo aumentou bastante nos dois estados analisados e, como consequência, os casos diminuíram.
> Verdade, como pode ser visto claramente nos dois gráficos anteriores. Aumentando a quantidade de doses aplicadas e, consequentemente, a cobertura vacina, o surto foi controlado e os dois estados e o Brasil se viu novamente livre da doença.
> 
<a name="aprendemos"></a>
# 5 O que aprendemos com isso?

É indisputável que a imunização é totalmente necessária para superarmos doenças que já possuem vacinas. O surto de sarampo de 2013 a 2015 foi completamente controlado após a aplicação em massa de vacinas em todo o público-alvo no estados de Pernambuco e do Ceará.

Fazendo um paralelo com o momento atual de pandemia da Covid-19, sonhamos com o dia que teremos uma Cobertura Vacinal acima de 95% contra essa doença, pois essa é a única forma de obtermos sucesso no enfrentamento do coronavírus.

<p align="center">
	<strong><img src="https://img.icons8.com/emoji/20/000000/syringe-emoji.png"/> Resumindo: VACINA JÁ! <img src="https://img.icons8.com/emoji/20/000000/syringe-emoji.png"/></strong></p>

<p align="center">
	<img src="https://raw.githubusercontent.com/diascarolina/vacinacao-geral-no-brasil/main/other/gif.gif?token=AH6WME2ADIP7NUVN37NYAOLAZWBQW">
</p>

<a name="libs"></a>
# 6 Ferramentas & Bibliotecas

Os notebooks .ipynb foram produzidos no JupyterLab utilizando o Python 3.8.5, com as seguintes bibliotecas:
- Pandas 1.2.3;
- Numpy 1.20.1;
- Seaborn 0.11.0;
- Matplotlib 3.3.2.

<a name="refs"></a>
# 7 Referências

- [Programa Nacional de Imunização - Apresentação](http://pni.datasus.gov.br/apresentacao.asp)
- [TABNET](http://www2.datasus.gov.br/DATASUS/index.php?area=02)
- [DATASUS](https://datasus.saude.gov.br/)
- [Origem dos Dados](http://tabnet.datasus.gov.br/cgi/tabcgi.exe?pni/cnv/cpniuf.def)
- [Notas Técnicas](http://tabnet.datasus.gov.br/cgi/pni/Imun_cobertura_desde_1994.pdf)
- [As Vacinas Importantes Para Recém-Nascidos](https://www.unimedlondrina.com.br/noticias/tudo-saude/07/06/2018/vacinas-importantes-recem-nascidos/)
- [Posto de Saúde de Fortaleza recebe longas filas após surto de ssarampo](http://g1.globo.com/ceara/noticia/2014/01/posto-de-saude-de-fortaleza-recebe-longas-filas-apos-surto-de-sarampo.html)
- [Aumento de casos de sarampo desperta alerta para os sintomas e a prevenção da doença](http://www.iff.fiocruz.br/index.php/9-noticias/2014/6-aumentosarampo1)
- [O que é sarampo](https://www.saude.pr.gov.br/Pagina/Sarampo)
- [10 perguntas e respostas sobre a vacina do sarampo](https://www.uol.com.br/vivabem/noticias/redacao/2019/07/10/10-perguntas-e-respostas-sobre-a-vacina-do-sarampo.htm)
- [Vacina tríplice viral: para que serve, quando tomar e efeitos colaterais](https://www.tuasaude.com/vacina-triplice-viral/)
- [Notas Técnicas](http://tabnet.datasus.gov.br/cgi/pni/Imun_cobertura_desde_1994.pdf)
- [Boletim Epidemiológico Sarampo](https://sbim.org.br/images/files/boletim_epid_sarampo_13_02_2015.pdf)
- [Casos de sarampo no país ultrapassam recorde de 1999](https://www.folhape.com.br/noticias/casos-de-sarampo-no-pais-ultrapassam-recorde-de-1999/76664/)
- [Estratégias e resultados da vacinação no enfrentamento da epidemia de sarampo no estado do Ceará, 2013-2015](https://www.scielo.br/j/ress/a/7nR8MdMkqYBnVSt6CrkQLfg/?lang=pt)
- [Eliminação do sarampo no Brasil tem anúncio internacional](https://portal.fiocruz.br/noticia/eliminacao-do-sarampo-no-brasil-tem-anuncio-internacional)
- [Alura](https://www.alura.com.br/)
- [Bootcamp Data Science Aplicada](https://www.alura.com.br/bootcamp/data-science-aplicada/matriculas-abertas)
- [Storytelling with Data](https://www.storytellingwithdata.com/)
- [Storytelling with Data in Python](https://github.com/empathy87/storytelling-with-data)
- [Numpy](https://numpy.org/)
- [Pandas](https://pandas.pydata.org/)
- [Matplotlib](https://matplotlib.org/)
- Imagem do banner por [Thirdman](https://www.pexels.com/pt-br/@thirdman) no [Pexels](https://www.pexels.com/pt-br/)


<a name="agra"></a>
# 8 Observações & Agradecimentos

Esse projeto é parte do Módulo 2 do Bootcamp Data Science Aplicada da [Alura](https://www.alura.com.br/).

Agradecimentos aos excelentes instrutores do módulo, Guilherme Silveira e Thiago Gonçalves, sempre com dicas pertinentes durante as aulas.

E um agradecimento especial aos meu amigos _"bootcampers"_ Junior Torres e Valquíria Alencar que trouxeram bom-humor para os momentos mais cansativos do projeto.

<a name="contact"></a>
# 9 Contatos

Dúvidas? Dicas? Sugestões? Ficarei feliz em recebê-las!
- **E-mail:** [carolinadiasw@gmail.com](mailto:carolinadiasw@gmail.com)
- **Linkedin:** https://www.linkedin.com/in/carodias/
- **Github:** https://github.com/diascarolina
- **Discord**: [Carolina Dias#6164](https://discord.com/app)
