<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/header_genie.png">

# Hands-On LAB 02 - Criando o Dashboard AI/BI

Treinamento Hands-on na plataforma Databricks com foco nas funcionalidades de Análise Exploratória e Painéis.
</br></br>

## Objetivos do Exercício

O objetivo desse laboratório é montar um Painel, utilizando os dados de ações das Big Tech da NASDAQ.
</br></br></br>


## Exercício 02.01 - Passo a Passo na criação do Painel

Entre na opção "**Catalog**" no MENU lateral Databricks, </br>
e filtre o catálogo "**academy**" e schema "**genie_aibi**" </br>
e selecione a tabela "**stock_bigtech**". </br>
Clique no botão "**Open in a Dashboard**".
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_01.png" width="800px">
</br></br></br>

O Databricks vai gerar uma primeira versão de painel</br>
e abrir um box para criação do elemento gráfico do painel.</br>
A primeira linha digitável é um **Assistente GenAI**, </br>
onde podemos descrever, em linguagem natural, o que queremos criar.</br>
Reparem que abaixo da linha, já existem algumas sugestões dadas pelo próprio assistente.
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_02.png" width="800px">
</br></br></br>

Na linha digitável, conforme vamos digitando, vão aparecendo opções baseadas no contexto da tabela.</br>
Digite a frase abaixo na linha do assistente:
</br></br>
``` sql
 volume de ações por dia e por empresa 
``` 
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_03.png" width="600px">
</br></br></br>

Vamos melhorar o layout do painel e a disposição dos objetos.</br>
Arraste o gráfico de "Volume de Ações" para o centro do Painel.</br>
Deixe a largura do gráfico ocupando a tela de lado a lado.
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_04.png" width="800px">
</br>
</br>
</br>

## Exercício 02.02 - Segundo elemento gráfico

Vamos criar um novo elemento gráfico.</br>
No menu azul suspenso, que fica na parte inferior do painel, </br>
Clique no segundo botão (com o ícone de um gráfico).</br>
</br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_botao.png" width="200px">

</br></br></br>


Na linha digitável do assistente, escreva:</br>
</br>
``` sql
gráfico de linhas do valor de fechamento por dia e por empresa

``` 
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_05.png" width="800px">
</br></br></br>

## Exercício 02.03 - Adicionando um filtro de página

Organize novamente o layout do Painel, </br>
colocando o novo gráfico alinhado com o gráfico de "Volumes".</br>
Depois clique no menu azul suspenso no ícone de FILTRO.</br>
Escolha o atributo (Field):  "**company**"
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_06.png" width="850px">
</br></br></br>


## Exercício 02.04 - Adicionando uma imagem ao painel

No box de texto do títudo do painel, apague o texto anterior, </br>
e substitua pelo código (markdown) abaixo: </br>
</br>

``` sql
![image](https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/header_painel.png)
```

</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_07.png" width="700px">
</br></br></br>

O Painel ficará com a aparência da imagem abaixo.</br>
Faça o devido alinhamento do gráfico no layout.</br>
Altere o nome do Dashboard na barra superior.</br>
Clique no botão "**Publish**" para publicar o Painel.
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_08.png" width="700px">
</br></br></br>


## (Opcional) Exercício 02.05 - Criando um NOVO contexto de dados

Vamos criar agora um novo contexto de dados.</br>
Para isso, entre na opção "**SQL Editor**" no MENU lateral do Databricks, </br>
selecione o Catálogo e o Schema na barra superior do Editor de Query,</br>
e escreva o texto abaixo:</br>

``` 

Selecione o nome da empresa, stock,
mínimo valor de fechamento, máximo valor de fechamento
e percentual de variação entre o mínimo e o máximo valor de fechamento
da tabela stock_bigtech
agrupando por empresa e stock

```
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_09.png" width="700px">
</br></br></br>

Acrescente ao resultado a linha de concatenação com o nome da ação (STOCK), </br>
com o LINK (URL) de uma imagem. </br>

``` sql

SELECT 
  "https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/" || stock || ".png" AS image,
  company,
  stock,
  MIN(close) AS min_close,
  MAX(close) AS max_close,
  ((MAX(close) - MIN(close)) / MIN(close) * 100) AS percentual_variacao
FROM luis_assuncao.genie_aibi.stock_bigtech
GROUP BY company, stock;

```
</br>
Ao executar a query (botão RUN),</br>
o resultado esperado é o mostrado abaixo:</br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_10.png" width="700px">
</br></br></br>

## (Opcional) Exercício 02.06 - Adicionando o NOVO contexto de dados ao Dashboard

Agora vamos adicionar o novo contexto de dados (calculado na Query);</br>
como mais uma fonte de dados no Painel.</br>
Para isso, volte na opção "**Dashboards**" no menu lateral Databricks,</br>
Escolha o nome do Painel que foi criado,</br>
e Clique no botão (combo box) de "**Published**" para "**Draft**".
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_10b.png" width="700px">
</br></br></br>

Clique na opção "**Data**".</br>
No item "Create another Dataset"</br>
clique no botão "**+Create from SQL**".</br>

</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_11.png" width="700px">
</br></br></br>

Faça o Copy&Paste do código SQL gerado no exercício anterior:

``` sql

SELECT 
  "https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/" || stock || ".png" AS image,
  company,
  stock,
  MIN(close) AS min_close,
  MAX(close) AS max_close,
  ((MAX(close) - MIN(close)) / MIN(close) * 100) AS percentual_variacao
FROM luis_assuncao.genie_aibi.stock_bigtech
GROUP BY company, stock;

```
E depois clique no botão "**RUN**"
</br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_12.png" width="700px">
</br></br></br>

## (Opcional) Exercício 02.07 - Adicionando um novo Gráfico com o contexto novo de dados

Clique no menu azul suspenso na posição inferior do painel, </br>
no botão com o ícone de gráfico, </br>
e na barra de configuração (lateral direita do painel),</br>
escolha o nome do nome Dataset (que veio da Query SQL). 
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_13.png" width="700px">
</br></br></br>

Configure o tipo de Visualização para "Tabela"(Table).</br>
Marque a opção para incluir TODOS os campos na tabela.
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_14.png" width="700px">
</br></br></br>

Na configuração, clique no campo(coluna) com o nome de "**image**".</br>
Na opção de "Display", configure como "image". </br>

</br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_15.png" width="700px">
</br></br></br>

Na opção de "SIZE", coloque o valor de "25" no campo "width".</br>
Na opção de "Default column width", coloque o valor de "150".
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_16.png" width="700px">
</br></br></br>

Como resultado esperado, teremos a figura abaixo.</br>
Salve (Publique) novamente o Painel.
</br></br>
<img src="https://raw.githubusercontent.com/Databricks-BR/genie_ai_bi/main/images/lab2_17.png" width="700px">
</br></br></br>
