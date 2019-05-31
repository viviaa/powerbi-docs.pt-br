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
ms.date: 05/30/2019
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: dcf62925d8e5eef07fb6295f8d8141413947f8fb
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413056"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Faça um tour pelo painel Filtros do relatório
Este artigo examina o painel de filtros de relatório no serviço do Power BI. Use os filtros para descobrir novas percepções em seus dados.

Há muitas maneiras diferentes de filtrar dados no Power BI. Recomendamos que você leia [Sobre filtros e realce](../power-bi-reports-filters-and-highlighting.md) primeiro.

![relatório no navegador](media/end-user-report-filter/power-bi-browser-new2.png)

## <a name="working-with-the-report-filters-pane"></a>Trabalhar com o painel de Filtros do relatório
Quando um colega compartilhar um relatório com você, não se esqueça de examinar o painel **Filtros**. Às vezes, ele está recolhido na borda direita do relatório. Selecione-o para expandi-lo.   

![relatório no navegador](media/end-user-report-filter/power-bi-filter-pane.png)

O painel Filtros contém os filtros que foram adicionados ao relatório pelo *designer* do relatório. *Os consumidores* como você, pode interagir com os filtros existentes e salve suas alterações, mas não é possível adicionar novos filtros ao relatório. Por exemplo, na captura de tela acima, o designer adicionou dois filtros de nível de página: Segmentar e em execução o ano. Você pode interagir e alterar esses filtros, mas não pode adicionar um terceiro filtro no nível de página.

No serviço do Power BI, relatórios retêm as alterações feitas no painel de filtros e essas alterações são repassadas para a versão móvel do relatório. Para redefinir o painel Filtro para os padrões do designer, selecione **Redefinir para padrão** na barra de menus superior.  

![Redefinir para padrão](media/end-user-report-filter/power-bi-reset-to-default.png)   

## <a name="view-all-the-filters-for-a-report-page"></a>Exibir todos os filtros para uma página de relatório
O painel filtros exibe todos os filtros adicionados ao relatório, o *designer*. O painel filtros também é a área onde você pode exibir informações sobre os filtros e interagir com eles. Você pode salvar as alterações que você fizer ou use **Redefinir para padrão** para reverter para as configurações originais do filtro.

Se houver alterações que você gostaria de salvar, você também pode criar um indicador de pessoal.  Para obter mais informações, consulte [adicionar um indicador a um relatório](end-user-bookmarks.md).

Há vários tipos de filtros de relatório que são exibidos e gerenciados no painel filtros, aquelas aplicadas a um visual, para uma página de relatório e ao relatório inteiro.

Neste exemplo, selecionamos um visual que tem filtros de 2. A página de relatório também tem filtros, listados sob o **filtros nesta página** título. E todo o relatório tem um filtro de data.

![lista de filtros](media/end-user-report-filter/power-bi-all-filters2.png)

Alguns filtros têm a palavra **Todos** ao seu lado, o que significa que todos os valores estão sendo incluído no filtro.  Por exemplo, **Segment(All)** na captura de tela acima informa que essa página de relatório inclui dados sobre todos os segmentos de produto.  Por outro lado, o nível de página filtro de **região Oeste é** informa que a página de relatório inclui somente dados para a região Oeste.

Qualquer pessoa que exibir este relatório pode interagir com esses filtros.

### <a name="view-only-those-filters-applied-to-a-visual"></a>Exibir apenas esses filtros aplicados a um visual
Para obter uma análise aprofundada dos filtros aplicados a um visual específico, passe o mouse sobre o visual para revelar o ícone de filtro ![ícone](media/end-user-report-filter/power-bi-filter-icon.png). Selecione esse ícone de filtro para ver um pop-up com os filtros, segmentações de dados e assim por diante, que afetam esse elemento visual. Os filtros no pop-up são os mesmos filtros exibidos na **filtros** painel. 

![lista de filtros](media/end-user-report-filter/power-bi-hover-visual-filter.png)

 
Aqui estão os tipos de filtros, que essa exibição pode exibir:
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
1. Podemos ver que o gráfico de coluna foi cruzados.
2. **Incluído** informa que o filtro cruzado é para **segmento**, e os três são incluídos. 
3. Uma segmentação de dados foi aplicada para o **trimestre**.
4. **Região** é um filtro aplicado a esta página do relatório, e
5. **isVanArsdel** e **ano** são filtros aplicados a este visual.


![lista de filtros](media/end-user-report-filter/power-bi-visual-pop-up.png)

### <a name="search-in-a-filter"></a>Pesquisar em um filtro
Às vezes, um filtro pode ter uma longa lista de valores. Use a caixa de pesquisa para localizar e selecionar o valor desejado. 

![Pesquisar em um filtro](media/end-user-report-filter/power-bi-fiter-search.png)

### <a name="display-filter-details"></a>Detalhes do filtro de exibição
Para entender um filtro, dê uma olhada em como os valores disponíveis e as contagens.  Exiba os detalhes do filtro focalizando e selecionando a seta ao lado do nome do filtro. 
  
![mostra Lindseys selecionado](media/end-user-report-filter/power-bi-expand-filter.png)

### <a name="change-filter-selections"></a>Alterar as seleções de filtro
É uma maneira de pesquisar informações de dados interagir com os filtros. Você pode alterar as seleções de filtro usando a seta suspensa ao lado do nome do campo.  Dependendo do tipo de dados que está sendo filtrados e filtro, suas opções irá variar de simples seleções em uma lista de intervalos de datas ou números de identificação. O filtro avançado abaixo, alteramos o filtro **Total acumulado no ano de unidades** no mapa de árvore seja entre 2.000 e 3.000. Observe que isso remove Prirum do mapa de árvore. 
  
![mostra Fashions Direct selecionado](media/end-user-report-filter/power-bi-filter-treemap.png)

> [!TIP]
> Para selecionar mais de um valor de filtro por vez, mantenha pressionada a tecla CTRL. A maioria dos filtros dá suporte a seleção múltipla. 

### <a name="reset-filter-to-default"></a>Redefinir filtro para o padrão
Se você quiser reverter todas as alterações feitas aos filtros, selecionados **Redefinir para padrão** na barra de menus superior.  Isso reverterá os filtros para seu estado original, conforme definido pelo relatório *designer*. 

![Redefinir para padrão](media/end-user-report-filter/power-bi-reset-to-default.png)
    
### <a name="clear-a-filter"></a>Limpar um filtro
Se houver apenas um filtro que você deseja definir **(All)** , desmarque-a, selecionando o ícone de borracha ![ ícone de borracha ](media/end-user-report-filter/power-bi-eraser-icon.png) próximo ao nome do filtro.
  
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
[Saiba como e por que os visuais executam filtro cruzado e realce cruzado entre si em uma página de relatório](end-user-interactions.md)