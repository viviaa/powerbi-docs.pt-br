---
title: Gráficos de dispersão, bolhas e de pontos no Power BI
description: Gráfico de dispersão, gráficos de pontos e gráficos de bolhas no Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: PVcfPoVE3Ys
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 7739dda4647a82b3c9d4b58976db89038428625a
ms.sourcegitcommit: 42475ac398358d2725f98228247b78aedb8cbc4f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003169"
---
# <a name="scatter-charts-bubble-charts-and-dot-plot-charts-in-power-bi"></a>Gráficos de dispersão, gráficos de bolhas e gráficos de pontos no Power BI
Um gráfico de dispersão sempre tem dois eixos de valor para mostrar um conjunto de dados numéricos em um eixo horizontal e outro conjunto de valores numéricos em um eixo vertical. O gráfico exibe pontos na interseção de um valor numérico de x e y, combinando esses valores em pontos de dados individuais. Esses pontos de dados podem ser distribuídos de maneira uniforme ou não pelo eixo horizontal, dependendo dos dados.

Um gráfico de bolhas substitui os pontos de dados por bolhas, com o *tamanho* de bolha representando uma dimensão adicional dos dados.

![exemplo de gráfico de bolhas](media/power-bi-visualization-scatter/power-bi-bubble-chart.png)

Um gráfico de pontos é semelhante a um gráfico de bolhas e um gráfico de dispersão, exceto que você pode plotar dados numéricos ou categóricos ao longo do eixo X. 

![exemplo de gráfico de bolhas](media/power-bi-visualization-scatter/power-bi-dot-plot.png)

Você pode definir o número de pontos de dados até um máximo de 10 mil.  

## <a name="when-to-use-a-scatter-chart-or-bubble-chart"></a>Quando usar um gráfico de dispersão ou de bolhas
### <a name="scatter-charts-are-a-great-choice"></a>Os gráficos de dispersão são uma ótima opção:
* para mostrar as relações entre dois (dispersão) ou três (bolhas) valores **numéricos** .
* para plotar dois grupos de números como uma série de coordenadas xy.
* em vez de um gráfico de linhas quando desejar alterar a escala do eixo horizontal    
* para transformar o eixo horizontal em uma escala logarítmica.
* para exibir os dados da planilha que incluem pares ou conjuntos de valores agrupados. Em um gráfico de dispersão, é possível ajustar as escalas independentes dos eixos para exibir mais informações sobre os valores agrupados.
* para mostrar padrões em grandes conjuntos de dados, por exemplo, mostrando exceções, clusters e tendências lineares ou não lineares.
* para comparar grandes números de pontos de dados sem preocupação com o tempo.  Quanto mais dados você incluir em uma dispersão, melhores serão as comparações que você poderá fazer.

### <a name="bubble-charts-are-a-great-choice"></a>Os gráficos de Bolhas são uma ótima opção:
* Se os dados tiverem três séries de dados que contêm um conjunto de valores cada um.
* para apresentar dados financeiros.  Os diferentes tamanhos de bolha são úteis para destacar visualmente os valores específicos.
* para usar com quadrantes.

### <a name="dot-plot-charts-are-a-great-choice-in-place-of-a-scatter-or-bubble"></a>Gráficos de pontos são uma ótima opção no lugar de um gráfico de dispersão ou bolha:
* se você quiser incluir dados categóricos ao longo do eixo X

## <a name="create-a-scatter-chart"></a>Criar um gráfico de dispersão
Assista a este vídeo para ver Will criar um gráfico de dispersão e, em seguida, siga as etapas abaixo para criar uma.

<iframe width="560" height="315" src="https://www.youtube.com/embed/PVcfPoVE3Ys?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


Essas instruções usam o exemplo de análise de varejo. Para acompanhar, [baixe o exemplo](../sample-datasets.md) do serviço do Power BI (app.powerbi.com) ou do Power BI Desktop.   

1. Abra o relatório no modo de exibição de Edição e selecione o ícone de mais amarelo para criar uma [página de relatório em branco ](../power-bi-report-add-page.md).
 
2. No painel Campos, selecione os campos a seguir:
   - **Vendas** > **Vendas por pé quadrado**
   - **Vendas** > **Percentual de variância total de vendas**
   - **Distrito** > **Distrito**

     ![](media/power-bi-visualization-scatter/power-bi-bar-chart.png)

     Caso esteja usando o serviço do Power BI, certifique-se de abrir o relatório no [Modo de Exibição de Edição](../service-interact-with-a-report-in-editing-view.md).

3. Converta em um gráfico de Dispersão. No painel Visualização, selecione o ícone do Gráfico de dispersão.

   ![](media/power-bi-visualization-scatter/power-bi-scatter-new.png).

4. Arraste **Distrito** de **Detalhes** para **Legenda**. Isso exibe um gráfico de dispersão que plota o **% da Variação do Total de Vendas** no eixo Y e as **Vendas por Pé Quadrado** no eixo X. As cores do ponto de dados representam distritos:

    ![](media/power-bi-visualization-scatter/power-bi-scatter2.png)

Agora vamos adicionar uma terceira dimensão.

## <a name="create-a-bubble-chart"></a>Criar um gráfico de bolhas

1. No painel **Campos**, arraste **Vendas** > **Vendas Deste Ano** > **Valor** para a área **Tamanho**. Os pontos de dados são expandidos para volumes proporcionais com o valor de vendas.
   
   ![pontos tornam-se bolhas](media/power-bi-visualization-scatter/power-bi-scatter-chart-size.png)

2. Focalize uma bolha. O tamanho da bolha reflete o valor das **Vendas Deste Ano**.
   
    ![exibição de dicas de ferramenta](media/power-bi-visualization-scatter/pbi_scatter_chart_hover.png)

3. Para definir o número de pontos de dados a serem mostrados em seu gráfico de bolha, na seção **Formatação** do painel **Visualizações**, expanda o cartão **Geral** e ajuste o **Volume de Dados**. É possível definir o volume máximo de dados para qualquer número até 10.000. Para garantir um bom desempenho ao definir os números mais altos, faça um teste antes. 

    ![Volume de Dados](media/power-bi-visualization-scatter/pbi_scatter_data_volume.png) 

   Já que mais pontos de dados podem significar um tempo de carregamento mais longo, se você optar por publicar relatórios com limites na extremidade mais elevada da escala, teste seus relatórios na Web e em dispositivos móveis, além de garantir que o desempenho corresponda às expectativas dos usuários. 

4. É possível [formatar as cores de visualização, os rótulos, os títulos, a tela de fundo e muito mais](service-getting-started-with-color-formatting-and-axis-properties.md). Para [melhorar a acessibilidade](../desktop-accessibility.md), considere adicionar formas de marcador a cada linha. Usar uma Forma de marcador diferente para cada linha torna mais fácil para os consumidores do relatório diferenciar as linhas (ou áreas) umas das outras. Para selecionar a forma do marcador, expanda o cartão **Formas** e, em seguida, selecione uma forma de marcador.

      ![Forma do marcador](media/power-bi-visualization-scatter/pbi_scatter_marker.png)

   Você também pode alterar a forma do marcador para losango, triângulo ou quadrado:

   ![Marcador quadrado](media/power-bi-visualization-scatter/pbi_scatter_chart_hover_square.png)

## <a name="create-a-dot-plot"></a>Criar um gráfico de pontos
Para criar um gráfico de pontos, substitua o campo numérico do eixo X por um campo categórico.

No painel **Eixo X**, remova **Vendas por pé quadrado** e substitua por **Distrito > DM**.
   
![novo gráfico de pontos](media/power-bi-visualization-scatter/power-bi-dot-plot-squares.png)


## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

### <a name="your-scatter-chart-has-only-one-data-point"></a>**O gráfico de dispersão tem apenas um ponto de dados**
O gráfico de dispersão contém apenas um ponto de dados que agrega todos os valores nos eixos X e Y?  Ou talvez ele agrega todos os valores em uma linha horizontal ou vertical?

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot1.png)

Adicione um campo à área **Detalhes** para informar o Power BI como agrupar os valores. O campo deve ser exclusivo para cada ponto em que você deseja plotar, como um número de linha simples ou um campo de ID.

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot.png)

Ou então, se você não tiver isso em seus dados, crie um campo que concatena os valores X e Y juntos em algo exclusivo por ponto:

![](media/power-bi-visualization-scatter/pbi_scatter_tshoot2.png)

Para criar um novo campo, [use o Editor de Consultas do Power BI Desktop para adicionar uma Coluna de Índice](../desktop-add-custom-column.md) ao conjunto de dados.  Em seguida, adicione essa coluna à área **Detalhes** de sua visualização.

## <a name="next-steps"></a>Próximas etapas

[Gráficos de dispersão de alta densidade](desktop-high-density-scatter-charts.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

