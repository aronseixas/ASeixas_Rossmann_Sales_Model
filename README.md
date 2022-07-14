# Rossmann Sales Model
![image](https://user-images.githubusercontent.com/95039795/178862128-c6f3db7a-ac6a-442e-9a58-1ef5e592860e.png)

<b>Aviso:</b> Este projeto foi desenvolvido com premissas e hipóteses fictícias, cujo objetivo foi contextualizar o desenvolvimento da solução.

<h1>1- Business Problem </h1>
O presente projeto foi desenvolvido a partir da necessidade do CFO da drogaria Rossmann em prever as vendas das unidades nas próximas 6 semanas a fim de definir o orçamento necessário para o projeto de renovação das filiais. Dentro deste contexto, um modelo de Machine Learning foi desenvolvido de modo a responder a questão central deste projeto

<h1> 2- Hipóteses de negócio </h1>
<ul style=“list-style-type:circle”>
<li> Remoção dos dias nos quais as lojas estão fechadas.</li>
<li> Somente as lojas abertas e que possuam vendas serão consideradas.</li>
<li> Lojas que não possuem competidor próximo, será adotada uma distância muito maior do que a máxima presente nos dados.</li>
</ul>

<h1> 3-	Lista de Atributos </h1>
<table border="1" align=center>
    <tr>
        <td><b>Atributo</b></td>
        <td><b>Significado</b></td>
    </tr>
    <tr>
        <td>Id</td>
        <td>An Id that represents a (Store, Date) duple within the test set.</td>
    </tr>
    <tr>
        <td>Store</td>
        <td>A unique Id for each store.</td>
    </tr>
    <tr>
        <td>Sales</td>
        <td>The turnover for any given day.</td>
    </tr>
    <tr>
        <td>Customers</td>
        <td>The number of customers on a given day.</td>
    </tr>
    <tr>
        <td>Open</td>
        <td>An indicator for whether the store was open: 0 = closed, 1 = open.</td>
    </tr>
    <tr>
        <td>StateHoliday</td>
        <td>Indicates a state holiday. Normally all stores, with few exceptions, are closed on state holidays. Note that all schools are closed on public holidays and weekends. a = public holiday, b = Easter holiday, c = Christmas, 0 = None.</td>
    </tr>
    <tr>
        <td>SchoolHoliday</td>
        <td>Indicates if the (Store, Date) was affected by the closure of public schools.</td>
    </tr>
    <tr>
        <td>StoreType</td>
        <td>Differentiates between 4 different store models: a, b, c, d.</td>
    </tr>
    <tr>
        <td>Assortment</td>
        <td>Describes an assortment level: a = basic, b = extra, c = extended.</td>
    </tr>
    <tr>
        <td>CompetitionDistance</td>
        <td>Distance in meters to the nearest competitor store.</td>
    </tr>
    <tr>
        <td>CompetitionOpenSince [Month/Year]</td>
        <td>Gives the approximate year and month of the time the nearest competitor was opened.</td>
    </tr>
    <tr>
        <td>Promo</td>
        <td>Indicates whether a store is running a promo on that day.</td>
    </tr>
    <tr>
        <td>Promo2</td>
        <td>Promo2 is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 = store is participating.</td>
    </tr>
    <tr>
        <td>Promo2Since [Year/Week]</td>
        <td>Describes the year and calendar week when the store started participating in Promo2.</td>
    </tr>
    <tr>
        <td>PromoInterval</td>
        <td>Describes the consecutive intervals Promo2 is started, naming the months the promotion is started anew. E.g. "Feb,May,Aug,Nov" means each round starts in February, May, August, November of any given year for that store</td>
    </tr>
</table>

<h1>4- Estratégia para solução </h1>

<p><b>1.	Data Descritpion:</b> O objetivo é o reconhecimento dos dados através de métricas estatísticas tais como: média, mediana, máximo, mínimo, range, skew, kurtosis e desvio padrão. Identificação de outliers no escopo do negócio e tratamento de dados ausentes.<p>  

<p><b>2.	Feature Engineering:</b> O objetivo é a obtenção de novos atributos baseado nas features originais presentes no dataset com o intuito de compreender melhor o fenômeno a ser modelado.</p>

<p><b>3.	Filtering Variables:</b> O objetivo é filtrar e remover linhas e colunas que não são relevantes para o modelo ou que integram o escopo do negócio.</p>

<p><b>4.	EDA:</b> Exploração dos dados para identificar insights sobre o negócio, bem como entender o impacto das variáveis para o modelo de Machine Learning.</p> 

<p><b>5.	Data Preparation:</b> Preparação dos dados para aplicação nos modelos de Machine Learning.</p>

<p><b>6.	Feature Selection:</b> Seleção dos melhores atributos para treinamento do modelo. Nesta seção foi utilizada o algoritmo Boruta.</p>

<p><b>7.	Modelo de Machine Learning:</b> Aplicação de modelos de de Machine Learning nos dados de teste e treinamento, seguido da aplicação do Cross Validation. Os modelos selecionados foram: média, regressão linear, regressão linear regularizada (Lasso), Random Forest e XGBoost.</p>

<p><b>8.	Hyperparameter Fine Tuning:</b> O objetivo é a escolha dos melhores valores para cada um dos parâmetros do modelo selecionado.</p>

<p><b>9.	Conversão da performance do modelo para valores de negócio:</b> Conversão do resultado de performance de modelo para valores de negócio.</p>

<p><b>10.	 Deploy do modelo para produção:</b> Publicação do modelo em uma Cloud (Heroku) de modo que demais pessoas pudessem utilizar os resultados obtidos.</p>

<p><b>11.	Bot. Telegram:</b> Criação de um Bot. no Telegram possibilitando a consulta dos resultados obtidos.</p>

<h1>5-	Top Insights </h1>
<h2><b>H1.</b> Lojas com maior sortimento deveriam vender mais.</h2>
<b>VERDADEIRA:</b> Lojas com maior sortimento vendem, em média, mais. 
<p align="center">
    <img src="https://user-images.githubusercontent.com/95039795/178856776-494693c6-5e9e-4d0c-9e7c-c0f6040dee6c.png" width="500" height="400" />
</p>

<h2><b>H2.</b> Lojas com competidores mais próximos deveriam vender menos.</h2>
<b>FALSA:</b> Lojas com competidores mais próximos vendem mais. 
<p align="center">
    <img src="https://user-images.githubusercontent.com/95039795/178857286-be6ee7fd-1112-41de-acc7-1277b888da4a.png" width="1100" height="500" />
</p>

<h2><b>H3.</b> Lojas deveriam vender mais depois do dia 10 de cada mês.</h2>
<b>FALSA:</b> A venda média das lojas antes do dia 10 é superior à média depois do dia 10. 
<p align="center">
    <img src="https://user-images.githubusercontent.com/95039795/178857299-f799c295-6103-4934-aec0-251e0c82d482.png" width="850" height="550" />
</p>


<h1> 6-	Modelos de Machine Learning utilizados</h1>
<ul style=“list-style-type:circle”>
<li> 1. Média.</li>
<li> 2. Regressão Linear.</li>
<li> 3. Regressão Linear com Regularização (Lasso).</li>
<li> 4. Random Forest Regressor.</li>
<li> 5. XGBoost Regresso.</li>
</ul>

<h1> 7-	Performance</h1>

<p> 7.1 -	Performance dos modelos.<br>
<p align="center">
    <img src="https://user-images.githubusercontent.com/95039795/178858172-837982ca-bc43-4946-a70c-24e4bd0418ce.png" width="500" height="200" />
</p>

<p> 7.2 - Performance com CV.<br>
<p align="center">
    <img src="https://user-images.githubusercontent.com/95039795/178858231-abf74275-bf81-427a-ad6d-0f3d2bd97af1.png" width="700" height="200" />
</p>    
    
<p> 7.3 - Performance após hyperparameter fine Tuning.<br>
<p align="center">
    <img src="https://user-images.githubusercontent.com/95039795/178858251-03c37321-535b-427d-9e4f-887042a87f55.png" width="600" height="110" />
</p>
</p>

<h1> 8-	Performance do modelo em valores de negócio.</h1>
Baseado nos resultados obtidos foi possível prever o valor total <br>
<p align="center">
    <img src="https://user-images.githubusercontent.com/95039795/178858436-f6058c64-24c4-4e29-ad72-60348f82f8b2.png" width="420" height="200" />
</p>

<h1> 9- Conclusão.</h1>
<p> A partir do projeto desenvolvido, foi possível concluir que, dentre os modelos testados, o XGBoost foi o mais indicado para seguir para etapa final do desenvolvimento do projeto. O modelo final obtido apresentou, conforme mostrado anteriormente, um desempenho aceitável, onde o MAPE (Erro médio percentual absoluto) foi de 11,45%.</p>
<p> Considerando que o projeto representa o primeiro ciclo do CRISP-DS, foi possível concluir que o modelo está pronto para ser colocado em produção. O resultado final está apresentado em um Bot. no Telegram, onde ao digitar o número da loja (store) se obtém o valor previsto para as 6 semanas seguintes. </p>

<h1> 10-	Tecnologias </h1>
<ul style=“list-style-type:circle”>
<li> Python.</li>
<li> Jupyter Notebook.</li>
<li> Git e Github.</li>
<li> Heroku Cloud.</li>
<li> Algoritmos de Classificação e Regressão.</li>
<li> Pacotes de Machine Learning Sklearn e Scipy.</li>
<li> Técnicas de Seleção de Atributos e Redução de Dimensionalidade - Boruta.</li>
<li> Flask e Python API's.</li>
</ul>

<h1> 11-	Modelo em produção no Telegram (Bot.) </h1>
<p align="center">
    <img src="https://user-images.githubusercontent.com/95039795/178864454-c8c343ec-417d-49b5-b6ae-8c39a4c34049.jpg" width="200" height="400" />
</p>
