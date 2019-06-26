---
title: Gráfico de área básico
description: Gráfico de área básico.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/11/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: fe1d2a6f086831a4ae6bd78d8669dce9459bffad
ms.sourcegitcommit: 797bb40f691384cb1b23dd08c1634f672b4a82bb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "66839855"
---
# <a name="basic-area-chart"></a>Gráfico de área básico
O gráfico de áreas básico (também conhecido como gráfico de áreas em camadas) baseia-se no gráfico de linhas. A área entre o eixo e a linha é preenchida com cores para indicar o volume. 

Os gráficos de área enfatizam a magnitude da alteração ao longo do tempo e pode ser usado para chamar a atenção para o valor total entre uma tendência. Por exemplo, os dados que representam o lucro ao longo do tempo podem ser plotados em um gráfico de área para enfatizar o lucro total.

![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)

## <a name="when-to-use-a-basic-area-chart"></a>Quando usar um gráfico de áreas básico
Os gráficos de áreas básicos são uma ótima opção:

* para ver e comparar as tendências de volume em série de tempo 
* para as séries individuais representando conjunto contável fisicamente

### <a name="prerequisites"></a>Pré-requisitos
 - Serviço do Power BI
 - Exemplo de análise de varejo

Para acompanhar, entre no Power BI e selecione **Obter Dados \> Exemplos \> Exemplo de Análise de Varejo > Conectar** e escolha **Ir para o dashboard**. 

## <a name="create-a-basic-area-chart"></a>Criar um gráfico de áreas básico
 

1. No painel "Exemplo de análise de varejo", selecione o bloco **Armazenamentos Totais** para abrir o relatório “Exemplo de Análise de Varejo”.
2. Selecione **Editar** para abrir o relatório no Modo de Exibição de Edição.
3. Adicione uma nova página de relatório selecionando o ícone amarelo de mais (+) na parte inferior do relatório.
4. Crie um novo gráfico de área que mostra este ano de vendas e as vendas do ano passado por mês.
   
   a. No painel Campos, selecione **Vendas \> Vendas do Último Ano** e **Vendas deste Ano > Valor**.

   ![](media/power-bi-visualization-basic-area-chart/power-bi-bar-chart.png)

   b.  Converta o gráfico em um gráfico de área básico, selecionando o ícone de Gráfico de área do painel Visualizações.

   ![](media/power-bi-visualization-basic-area-chart/convertchart.png)
   
   c.  Selecione **Hora \> Mês** para adicionar ao **Eixo**.   
   ![](media/power-bi-visualization-basic-area-chart/powerbi-area-chartnew.png)
   
   d.  Para exibir o gráfico por mês, selecione as reticências (canto superior direito do visual) e escolha **Classificar por mês**. Para alterar a ordem de classificação, selecione as reticências novamente e selecione **Classificar em ordem crescente** ou **Classificar em ordem decrescente**.

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como usar o painel Filtros, veja [Adicionar um filtro a um relatório](../power-bi-report-add-filter.md).

Para destacar uma área específica em seu gráfico, selecione essa área ou a respectiva borda superior.  Ao contrário de outros tipos de visualização, se houver outras visualizações na mesma página, destacar um gráfico de área básico não aplicará filtro cruzado às outras visualizações na página do relatório. No entanto, os gráficos de áreas são um alvo de filtragem cruzada acionado por outras visualizações na página do relatório. 

1. Teste-o selecionando seu gráfico de área e copiando-o para outra página de relatório (CTRL-C e CTRL-V).
2. Selecione uma das áreas sombreadas e, em seguida, outra área sombreada. Você não observará nenhum impacto às outras visualizações na página.

    ![Vendas neste ano selecionadas no gráfico de área](media/power-bi-visualization-basic-area-chart/power-bi-select-area.png)

3. Agora selecione um elemento em uma das outras visualizações na página, como uma barra de gráfico de coluna ou um mês em um gráfico de linha. Observe o impacto sobre o gráfico de área – ele é filtrado.  

    ![Barra FT Oglethorpe selecionada](media/power-bi-visualization-basic-area-chart/power-bi-filter.png) 

Para obter mais informações, consulte [Interações visuais em relatórios](../service-reports-visual-interactions.md)


## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas   
* [Tornar o relatório mais acessível para pessoas com deficiências](../desktop-accessibility.md)
* Gráficos de áreas básicos não são eficazes para comparar os valores devido à oclusão nas áreas em camadas. O Power BI usa transparência para indicar a sobreposição das áreas. No entanto, ele só funciona bem com duas ou três áreas diferentes. Quando você precisa comparar tendência com mais de três medidas, tente usar os gráficos de linhas. Quando você precisa comparar volume com mais de três medidas, tente usar o mapa de árvore.

## <a name="next-step"></a>Próxima etapa
[Relatórios no Power BI](power-bi-visualization-card.md)  

