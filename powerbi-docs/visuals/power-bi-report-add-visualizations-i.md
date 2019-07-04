---
title: Parte 1, Adicionar visualizações a um relatório do Power BI
description: Parte 1, Adicionar visualizações a um relatório do Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: IkJda4O7oGs
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/17/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: c5838d12351c06d0a76a975c9c473b1c00856d97
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299147"
---
# <a name="part-1-add-visualizations-to-a-power-bi-report"></a>Parte 1, Adicionar visualizações a um relatório do Power BI

Este artigo apresenta uma breve introdução à criação de uma visualização em um relatório. Ele se aplica ao serviço do Power BI e ao Power BI Desktop. Para ver conteúdo mais avançado, [veja a Parte 2](power-bi-report-add-visualizations-ii.md) desta série. Assista à Amanda demonstrando algumas maneiras diferentes de criar, editar e formatar visuais na tela do relatório. Em seguida, experimente você mesmo, usando o [exemplo Vendas e Marketing](../sample-datasets.md) para criar seu próprio relatório.

<iframe width="560" height="315" src="https://www.youtube.com/embed/IkJda4O7oGs" frameborder="0" allowfullscreen></iframe>

## <a name="open-a-report-and-add-a-new-page"></a>Abrir um relatório e adicionar uma nova página

1. Abra um [relatório no Modo de Exibição de Edição](../service-interact-with-a-report-in-editing-view.md).

    Este tutorial use o [exemplo de Vendas e Marketing](../sample-datasets.md).

1. Se o painel **Campos** não estiver visível, selecione o ícone de seta para abri-lo.

   ![](media/power-bi-report-add-visualizations-i/pbi_nancy_fieldsfiltersarrow.png)

1. Adicione uma página em branco ao relatório.

## <a name="add-visualizations-to-the-report"></a>Adicionar visualizações ao relatório

1. Crie uma visualização selecionando um campo no painel **Campos** .

    Comece com um campo numérico como **SalesFact** > **Vendas $** . O Power BI cria um gráfico de colunas com uma coluna.

    ![Captura de tela de um gráfico de colunas com uma única coluna.](media/power-bi-report-add-visualizations-i/pbi_onecolchart.png)

    Ou comece com um campo de categoria, como **Nome** ou **Produto**. O Power BI cria uma tabela e adiciona esse campo ao espaço **Valores**.

    ![GIF de uma pessoa selecionando Produto e, em seguida, categoria para criar uma tabela.](media/power-bi-report-add-visualizations-i/pbi_agif_createchart3.gif)

    Ou, comece com um campo com informações geográficas, como **Área Geográfica** > **Cidade**. O Power BI e o Bing Mapas criam uma visualização de mapa.

    ![Captura de tela de uma visualização de mapa.](media/power-bi-report-add-visualizations-i/power-bi-map.png)

1. Crie uma visualização e, em seguida, alterar o tipo. Selecione **Produto** > **Categoria** e **Produto** > **Contagem do Produto** para adicioná-los ao espaço **Valores**.

   ![Captura de tela do painel Campos com o espaço Valores destacado.](media/power-bi-report-add-visualizations-i/part1table1.png)

1. Altere a visualização para um gráfico de colunas selecionando o ícone de **gráfico de colunas empilhadas**.

   ![Captura de tela do painel Visualizações com o ícone do gráfico de colunas empilhadas destacado.](media/power-bi-report-add-visualizations-i/part1converttocolumn.png)

1. Quando você cria visualizações no relatório, é possível [fixá-las no dashboard](../service-dashboard-pin-tile-from-report.md). Para fixar a visualização, selecione o ícone de pino ![Captura de tela do ícone de pino.](media/power-bi-report-add-visualizations-i/pinnooutline.png).

   ![Captura de tela da visualização de um gráfico de colunas com o ícone de pino destacado.](media/power-bi-report-add-visualizations-i/part1pin1.png)
  
## <a name="next-steps"></a>Próximas etapas

 Continue em:

* [Parte 2: Adicionar visualizações a um relatório do Power BI](power-bi-report-add-visualizations-ii.md)

* [Interaja com as visualizações](../consumer/end-user-reading-view.md) no relatório.

* [Faça ainda mais com as visualizações](power-bi-report-visualizations.md).

* [Salve seu relatório](../service-report-save.md).
