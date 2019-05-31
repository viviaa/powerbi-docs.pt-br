---
title: Usar gráficos de faixa de opções no Power BI
description: Criar e consumir gráficos de faixa de opções no serviço do Power BI e no Power BI Desktop
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/30/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 08a2de32b092ba24b66ddd9f173be1eaea8819ab
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61394383"
---
# <a name="use-ribbon-charts-in-power-bi"></a>Usar gráficos de faixa de opções no Power BI
Você pode usar gráficos de faixa de opções para visualizar dados e descobrir rapidamente qual categoria de dados tem a classificação mais alta (maior valor). Gráficos de faixa de opções são eficazes para mostrar alterações na classificação, com o maior intervalo (valor) sempre exibido na parte superior de cada período. 

![gráfico de faixa de opções](media/desktop-ribbon-charts/ribbon-charts_01.png)

## <a name="create-a-ribbon-chart"></a>Criar um gráfico de faixa de opções
Para acompanhar, abra o [Relatório de exemplo de análise de varejo](../sample-retail-analysis.md). 

1. Para criar um gráfico de faixa de opções, selecione **Gráfico de faixa de opções** no painel **Visualizações**.

    ![modelos de visualização](media/desktop-ribbon-charts/ribbon-charts_02.png)

    Os gráficos de faixa de opções conectam uma categoria de dados no continuum de tempo visualizado usando faixas de opções, permitindo que você veja como determinada categoria é classificada em todo o intervalo do eixo x do gráfico (geralmente, a linha do tempo).

2. Selecione campos para **Eixo**, **Legenda** e **Valor**.  Neste exemplo, selecionamos: **Data**, **Categoria** e **Vendas deste ano**.  

    ![campos selecionados](media/desktop-ribbon-charts/power-bi-ribbon-values.png)

    Já que o conjunto de dados contém dados para apenas um ano, removemos o campo **Ano** do **Eixo** também. 

3. O gráfico de faixa de opções mostra a classificação a cada dois meses. Observe como a classificação é alterada ao longo do tempo.  Por exemplo, a categoria Inicial passa de terceira para quarta e para terceira novamente. A categoria Juniores passa de terceira para quinta em julho. 

    ![gráfico de faixa de opções](media/desktop-ribbon-charts/power-bi-ribbon.png)

## <a name="format-a-ribbon-chart"></a>Formatar um gráfico de faixa de opções
Quando você cria um gráfico de faixa de opções, você tem opções de formatação disponíveis na seção **Formato** do painel **Visualizações**. As opções de formatação para gráficos de faixa de opções são semelhantes às de um gráfico de colunas empilhadas, com opções de formatação adicionais específicas às faixas de opções.

![modelo de faixa de opções no painel de Visualização](media/desktop-ribbon-charts/power-bi-format-ribbon.png)

Estas opções de formatação para gráficos de faixa de opções permitem que você faça ajustes.

* A opção **Espaçamento** permite ajustar a quantidade de espaço exibida entre as faixas de opções. O número é o percentual da altura máxima da coluna.
* A opção **Corresponder cor da série** permite fazer a correspondência da cor das faixas de opções com a cor da série. Quando definidas como **desligado**, as faixas de opções ficam cinza.
* A opção **Transparência** especifica o grau de transparência das faixas de opções, com o padrão definido como 30.
* A opção **Borda** permite colocar uma borda escura na parte superior e inferior das faixas de opções. Por padrão, as bordas estão desativadas.

Já que o gráfico de faixa de opções não tem rótulos do eixo y, você talvez queira adicionar rótulos de dados. No painel de Formatação, selecione **Rótulos de dados**. 

![opções de formatação para rótulos de dados](media/desktop-ribbon-charts/power-bi-labels.png)

Defina as opções de formatação para seus rótulos de dados.  Neste exemplo, definimos a cor do texto para branco, as casas decimais para zero e unidades de exibição para milhares. 

![modelo de faixa de opções no painel de Visualização](media/desktop-ribbon-charts/power-bi-data-labels.png)

## <a name="next-steps"></a>Próximas etapas

[Gráficos de dispersão e gráficos de bolhas no Power BI](power-bi-visualization-scatter.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)