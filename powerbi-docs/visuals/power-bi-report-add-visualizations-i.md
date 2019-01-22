---
title: 'Parte I: Adicionar visualizações a um relatório do Power BI'
description: 'Parte I: Adicionar visualizações a um relatório do Power BI'
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 08/23/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 52c0211aea0462e0bf79d7a48808f1f826c09fb6
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54296077"
---
# <a name="part-i-add-visualizations-to-a-power-bi-report"></a>Parte I: Adicionar visualizações a um relatório do Power BI
Este artigo apresenta uma breve introdução à criação de uma visualização em um relatório usando o serviço do Power BI ou Power BI Desktop.  Para obter um conteúdo mais avançado, [veja a Parte II](power-bi-report-add-visualizations-ii.md). Assista à Amanda demonstrando algumas maneiras diferentes de criar, editar e formatar visuais na tela do relatório. Em seguida, experimente você mesmo, usando o [exemplo Vendas e Marketing](../sample-datasets.md) para criar seu próprio relatório.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>


## <a name="open-a-report-and-add-a-new-page"></a>Abrir um relatório e adicionar uma nova página
1. Abra um [relatório no Modo de Exibição de Edição](../consumer/end-user-reading-view.md). Este tutorial use o [exemplo de Vendas e Marketing](../sample-datasets.md).
2. Se o painel Campos não estiver visível, selecione o ícone de seta para abri-lo. 
   
   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)
3. Adicione uma página em branco ao relatório.

## <a name="add-visualizations-to-the-report"></a>Adicionar visualizações ao relatório
1. Crie uma visualização selecionando um campo no painel **Campos** .  
   
   **Comece com um campo numérico** como SalesFact > Vendas $. O Power BI cria um gráfico de colunas com uma coluna.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)
   
   **Ou comece com um campo de categoria**, como Nome ou Produto: o Power BI cria uma Tabela e adiciona esse campo ao contêiner **Valores**.
   
   ![](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)
   
   Ou **comece com um campo com informações geográficas**, como Área Geográfica > Cidade. O Power BI e o Bing Mapas criam uma visualização de mapa.
   
   ![](media/power-bi-report-add-visualizations-i/power-bi-map.png)
2. Crie uma visualização e, em seguida, alterar o tipo. Selecione **Produto > Categoria** e **Produto > Contagem do Produto** para adicioná-los aos **Valores**.
   
   ![](media/power-bi-report-add-visualizations-i/part1table1.png)
3. Altere a visualização em um gráfico de colunas selecionando o ícone de gráfico de coluna.
   
   ![](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)
4. Quando você cria visualizações no relatório, é possível [fixá-las no dashboard](../service-dashboard-pin-tile-from-report.md). Para fixar a visualização, selecione o ícone de pino ![](media/power-bi-report-add-visualizations-i/pinnooutline.png).
   
   ![](media/power-bi-report-add-visualizations-i/part1pin1.png)
  

## <a name="next-steps"></a>Próximas etapas
 Continue em [Parte 2: Adicionar visualizações a um relatório do Power BI](power-bi-report-add-visualizations-ii.md)
   
   [Interaja com as visualizações](../consumer/end-user-reading-view.md) no relatório.
   
   [Faça ainda mais com as visualizações](power-bi-report-visualizations.md).
   
   [Salve seu relatório](../service-report-save.md).
