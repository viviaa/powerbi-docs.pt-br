---
title: Fazer um tour pelo painel Filtros do relatório
description: Como adicionar um filtro a um relatório no serviço do Power BI para consumidores
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-consumer
ms.topic: conceptual
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ef7e4f556832f1323043a80cf219678a16511c9e
ms.sourcegitcommit: e67bacbfc5638ee97e3d2e0e7f5bd2d9aac78f9c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67532878"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Faça um tour pelo painel Filtros do relatório

Este artigo oferece uma visão geral do painel **Filtros** do relatório no serviço do Power BI. Use os filtros para descobrir novos insights em seus dados.

Há muitas maneiras diferentes para filtrar os dados no Power BI. Para obter mais informações sobre filtros, consulte [Filtros e realce em relatórios do Power BI](../power-bi-reports-filters-and-highlighting.md).

![Captura de tela de um relatório no navegador com uma seta apontando para a opção Filtros.](media/end-user-report-filter/power-bi-browser-new2.png)

## <a name="working-with-the-report-filters-pane"></a>Trabalhar com o painel de Filtros do relatório

Quando um colega compartilhar um relatório com você, não se esqueça de examinar o painel **Filtros**. Às vezes, ele está recolhido na borda direita do relatório. Selecione-o para expandi-lo.

![Captura de tela do relatório com o painel Filtros expandido.](media/end-user-report-filter/power-bi-filter-pane.png)

O painel **Filtros** contém os filtros que o *designer* de relatórios adicionou ao relatório. *Consumidores* como você podem interagir com os filtros existentes e salvar as alterações, mas não podem adicionar novos filtros ao relatório. Por exemplo, na captura de tela acima, o designer adicionou dois filtros de nível de página: **Segmento** e **Ano**. Você pode interagir e alterar esses filtros, mas não pode adicionar um terceiro filtro no nível de página.

No serviço do Power BI, os relatórios de mantêm as alterações feitas no painel **Filtros**. O serviço realiza essas alterações por meio da versão móvel do relatório.

Para redefinir o painel **Filtros** para os padrões do designer, selecione ![Captura de tela da opção Redefinir para padrão](media/end-user-report-filter/power-bi-reset.png). na barra de menus superior.

## <a name="view-all-the-filters-for-a-report-page"></a>Exibir todos os filtros para uma página de relatório

O painel **Filtros** exibe todos os filtros adicionados pelo designer ao relatório. O painel **Filtros** também é a área em que você pode exibir informações sobre os filtros e interagir com eles. É possível salvar as alterações que você criar ou usar **Redefinir para padrão** para reverter para as configurações originais do filtro.

Se houver alterações que você gostaria de salvar, também será possível criar um indicador pessoal.  Para obter mais informações, consulte [O que são indicadores?](end-user-bookmarks.md).

O painel **Filtros** exibe e gerencia vários tipos de filtros de relatório. Eles podem ser aplicados a um visual, a uma página de relatório e ao relatório inteiro.

Neste exemplo, selecionamos um visual que tem dois filtros. A página de relatório também tem filtros, listados sob o título **Filtros nesta página**. Além disso, todo o relatório tem um filtro para **Data**.

![Captura de tela de um relatório com uma visualização e seus filtros relacionados destacados.](media/end-user-report-filter/power-bi-all-filters2.png)

Alguns filtros têm a opção **(Tudo)** ao lado deles. **(Tudo)** significa que todos os valores serão incluídos no filtro. Na captura de tela acima, **Segment(All)** informa que essa página do relatório inclui dados sobre todos os segmentos de produtos. Se você selecionar o filtro de nível de página **A Região é Oeste**, a página do relatório incluirá apenas os dados para a região Oeste.

Qualquer pessoa que exibir este relatório pode interagir com esses filtros.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Exibir apenas estes filtros aplicados a um visual

Para obter uma análise aprofundada dos filtros aplicados a um visual específico, passe o mouse sobre o visual para revelar o ícone de filtro ![Captura de tela do ícone de filtro](media/end-user-report-filter/power-bi-filter-icon.png). Selecione esse filtro para ver um pop-up com todos os filtros, segmentações etc., que afetam esse visual. Os filtros no pop-up são os mesmos filtros exibidos no painel **Filtros**.

![Captura de tela de uma lista de filtros com setas apontando para onde esses filtros estão no painel de filtros.](media/end-user-report-filter/power-bi-hover-visual-filter.png)

Estes são os tipos de filtros que essa exibição pode mostrar:

- Filtros básicos

- Segmentações

- Realce cruzado

- Filtragem cruzada

- Filtros avançados

- Primeiros N filtros

- Filtros de Data Relativa

- Sincronizar segmentadores

- Incluir/Excluir filtros

- Filtros passados por uma URL

No exemplo a seguir:

1. Podemos ver que o gráfico de coluna foi filtrado.

1. **Incluído** informa que o filtro cruzado é para **Segmento** e os três são incluídos.

1. Uma segmentação foi aplicada para **Trimestre**.

1. **Região** é um filtro aplicado a esta página do relatório, e

1. **isVanArsdel** e **Ano** são filtros aplicados a este visual.

![Captura de tela de um relatório e seus filtros com a lista de filtros numerados para coincidir com a lista numerada acima.](media/end-user-report-filter/power-bi-visual-pop-up.png)

### <a name="search-in-a-filter"></a>Pesquisar em um filtro

Às vezes, um filtro pode ter uma longa lista de valores. Use a caixa de pesquisa para localizar e selecionar o valor desejado.

![Captura de tela de como pesquisar em um filtro.](media/end-user-report-filter/power-bi-fiter-search.png)

### <a name="display-filter-details"></a>Exibir detalhes do filtro

Para entender um filtro, dê uma olhada nos valores e nas contagens disponíveis.  Veja os detalhes do filtro focalizando e selecionando a seta ao lado do nome do filtro.
  
![Captura de tela de um filtro que mostra a região Oeste selecionada.](media/end-user-report-filter/power-bi-expand-filter.png)

### <a name="change-filter-selections"></a>Alterar as seleções do filtro

É uma forma de pesquisar insights de dados é interagir com os filtros. Você pode alterar as seleções do filtro usando a seta suspensa ao lado do nome do campo.  Dependendo do filtro e tipo de dados que o Power BI está filtrando, suas opções variam de simples seleções em uma lista para identificar intervalos de datas ou números. No filtro avançado abaixo, alteramos o filtro **Total de unidades acumulado no ano** no mapa de árvore para ficar entre 2.000 e 3.000. Observe que essa alteração remove Prirum do mapa de árvore.
  
![Captura de tela de um relatório e seus filtros que mostra Fashions Direct selecionado.](media/end-user-report-filter/power-bi-filter-treemap.png)

> [!TIP]
> Para selecionar mais de um valor de filtro por vez, mantenha pressionada a tecla CTRL. A maioria dos filtros dá suporte à seleção múltipla.

### <a name="reset-filter-to-default"></a>Redefinir filtro para o padrão

Se você quiser reverter todas as alterações feitas aos filtros, selecione **Redefinir para padrão** na barra de menus superior.  Essa seleção reverte os filtros para o estado original, conforme definido pelo designer de relatórios.

![Captura de tela da opção Redefinir para padrão.](media/end-user-report-filter/power-bi-reset.png)

### <a name="clear-a-filter"></a>Limpar um filtro

Se houver apenas um filtro que você deseja definir como **(Tudo)** , desmarque-o, selecionando o ícone de borracha ![Captura de tela do ícone de borracha.](media/end-user-report-filter/power-bi-eraser-icon.png) ao lado do nome do filtro.
  
<!--  too much detail for consumers

## Types of filters: text field filters
### List mode
Ticking a checkbox either selects or deselects the value. The **All** checkbox can be used to toggle the state of all checkboxes on or off. The checkboxes represent all the available values for that field.  As you adjust the filter, the restatement updates to reflect your choices. 

![list mode filter](media/end-user-report-filter/power-bi-restatement-new.png)

Note how the restatement now says "is Mar, Apr or May".

### Advanced mode
Select **Advanced Filtering** to switch to advanced mode. Use the dropdown controls and text boxes to identify which fields to include. By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.  

![advanced mode](media/end-user-report-filter/power-bi-advanced.png)

## Types of filters: numeric field filters
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the values are infinite or represent a range, selecting the field name opens the advanced filter mode. Use the dropdown and text boxes to specify a range of values that you want to see. 

![advanced filter](media/end-user-report-filter/power-bi-dropdown-and-text.png)

By choosing between **And** and **Or**, you can build complex filter expressions. Select the **Apply Filter** button when you've set the values you want.

## Types of filters: date and time
### List mode
If the values are finite, selecting the field name displays a list.  See **Text field filters** &gt; **List mode** above for help using checkboxes.   

### Advanced mode
If the field values represent date or time, you can specify a start/end time when using Date/Time filters.  

![datetime filter](media/end-user-report-filter/pbi_date-time-filters.png)

-->

## <a name="next-steps"></a>Próximas etapas

Saiba como e por que os [visuais executam filtro cruzado e realce cruzado entre si em uma página de relatório](end-user-interactions.md)