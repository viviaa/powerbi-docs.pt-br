---
title: Filtros e realce em relatórios do Power BI
description: Sobre filtros e realce em relatórios do Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 8084b8dbbc27c856633d84c6628727dcd426964d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66187551"
---
# <a name="filters-and-highlighting-in-power-bi-reports"></a>Filtros e realce em relatórios do Power BI
 Este artigo apresenta a filtragem e realce no serviço do Power BI. A experiência é quase exatamente igual no Power BI Desktop. Os *Filtros* removem tudo, menos os dados que você deseja se concentrar. *Realce* não está filtrando. Ele não remove dados, mas em vez disso, realça um subconjunto dos dados visíveis; os dados que não são realçados permanecem visíveis, mas esmaecidos.

Há muitas maneiras diferentes de filtrar e realçar relatórios no Power BI. Colocar todas essas informações em um artigo seria confuso, portanto, nós as dividimos nessas seções:

* Introdução aos filtros e realce, o artigo que está lendo agora.
* Como [criar e usar filtros no modo de exibição de edição](power-bi-report-add-filter.md) em relatórios no Power BI Desktop e o serviço do Power BI. Quando você tem permissões de edição para um relatório, pode criar, modificar e excluir filtros em relatórios.
* Como elementos visuais [filtre e realce em um relatório compartilhado com você](consumer/end-user-interactions.md), na exibição de leitura no serviço do Power BI de relatório. O que você pode fazer é mais limitado, mas ainda tem uma ampla variedade de opções de filtragem e realce.  
* Um tour detalhado a [filtro e realce disponíveis no modo de exibição de edição de controles](power-bi-report-add-filter.md) no Power BI Desktop e o serviço do Power BI. O artigo usa um olhar detalhado sobre tipos de filtros, como a data e hora, numérica e o texto. Ele também aborda as diferenças entre as opções básicas e avançadas.
* Agora que você aprendeu como filtros e realce funcionam por padrão, [saiba como alterar a maneira pela qual as visualizações em uma página filtram e realçam umas às outras](service-reports-visual-interactions.md)

**Você sabia?** O Power BI tem uma nova experiência de filtro, atualmente em versão prévia. Leia mais sobre [a nova experiência de filtro em relatórios do Power BI](power-bi-report-filter-preview.md).

![Nova experiência de filtro](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading.png)


## <a name="intro-to-the-filters-pane"></a>Introdução ao painel Filtros

Você pode aplicar filtros no painel **Filtros** ou [fazendo seleções na segmentação de dados](visuals/power-bi-visualization-slicers.md) diretamente no próprio relatório. O painel Filtros mostra as tabelas e os campos usados no relatório e os filtros aplicados, caso haja algum. 

![O painel Filtros](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-reading-view.png)

Há quatro tipos de filtros.

- Um **filtro de página** se aplica a todos os visuais da página do relatório     
- Um **filtro de visual** se aplica a um único visual da página do relatório. Você só verá filtros no nível visual se tiver selecionado um visual na tela de relatório.    
- Um **filtro de relatório** se aplica a todas as páginas no relatório    
- Um **filtro de detalhamento** se aplica a uma única entidade em um relatório    

Você pode pesquisar na página, no elemento visual e nos filtros de relatório, no Modo de Exibição de Leitura ou de Edição, para localizar e selecionar o valor desejado. 

![Pesquisar em um filtro](media/power-bi-reports-filters-and-highlighting/power-bi-search-filter.png)

Se o filtro tiver a palavra **All** ao lado, isso significará que todos os valores no campo serão incluídos no filtro.  Por exemplo, **Chain(All)** na captura de tela abaixo informa que essa página de relatório inclui dados sobre cadeias de armazenamento.  Por outro lado, o filtro de nível de relatório ou **FiscalYear é 2013 ou 2014** informa que o relatório inclui somente dados para os anos fiscais de 2013 e 2014.

## <a name="filters-in-reading-or-editing-view"></a>Filtros no Modo de Exibição de Leitura ou de Edição
Há dois modos de interagir com relatórios: [Modo de Exibição de Leitura](consumer/end-user-reading-view.md) e Modo de Exibição de Edição. Os recursos de filtragem disponíveis para você dependem do modo no qual você está.

* No Modo de Exibição de Edição é possível adicionar filtros de relatório, de página, de detalhamento e de visual. Quando você salvar o relatório, os filtros serão salvos com o relatório, mesmo se você os abrir em um aplicativo móvel. Pessoas olhando para o relatório no Modo de Exibição de Leitura podem interagir com os filtros que você adicionou, mas não podem adicionar novos filtros.
* No Modo de Exibição de Leitura, você pode interagir com todos os filtros já existentes no relatório e salvar a seleção feita por você. Você não pode adicionar novos filtros.

### <a name="filters-in-reading-view"></a>Filtros no Modo de Exibição de Leitura
Se você só tiver acesso a um relatório no Modo de Exibição de Leitura, o painel Filtros terá uma aparência semelhante a esta:

![Filtros no Modo de Exibição de Leitura](media/power-bi-reports-filters-and-highlighting/power-bi-filter-reading-view.png)

Então, essa página do relatório tem seis filtros de nível de página e um filtro de nível de relatório.

Cada elemento visual pode ter filtros para todos os campos no elemento visual e um autor de relatório pode adicionar mais. Na imagem abaixo, o gráfico de bolhas tem seis filtros.

![Filtro de nível Visual](media/power-bi-reports-filters-and-highlighting/power-bi-filter-visual-level.png)

No Modo de exibição de leitura, explore os dados modificando os filtros existentes. As alterações que você fizer serão salvas com o relatório, mesmo se você abrir o relatório em um aplicativo móvel. Aprenda a [fazer um tour pelo painel Filtros do relatório](consumer/end-user-report-filter.md)

Quando você sair do relatório, seus filtros serão salvos. Para desfazer a filtragem e retornar às definições padrão de filtragem, divisão, análise e classificação configuradas pelo autor do relatório, selecione **Redefinir para padrão** na barra de menus superior.

![Redefinir para o ícone padrão](media/power-bi-reports-filters-and-highlighting/power-bi-reset-to-default.png)

### <a name="filters-in-editing-view"></a>Filtros no Modo de exibição de edição
Quando você tem permissões do proprietário para um relatório e o abre no Modo de exibição de edição, vê que **Filtros** é apenas um dos vários painéis de edição disponíveis.

![Painel de filtros no modo de exibição de edição](media/power-bi-reports-filters-and-highlighting/power-bi-add-filter-editing-view.png)

No Modo de Exibição de Leitura, essa página do relatório tem seis filtros de nível de página e um filtro de nível de relatório. E ao selecionar o gráfico de bolhas, veríamos que ele tem seis filtros de nível de visual aplicados.

Podemos fazer muito mais com filtros e destaque no Modo de Exibição de Edição. Principalmente, podemos adicionar novos filtros. Saiba como [Adicionar um filtro a um relatório](power-bi-report-add-filter.md) e muito mais.

## <a name="ad-hoc-highlighting"></a>Realce ad hoc
Selecione um rótulo de eixo ou valor em um visual para realçar os outros visuais na página. Para remover o realce, selecione o valor novamente ou selecione um espaço vazio no mesmo visual. Realce é divertido maneira de explorar rapidamente os impactos dos dados. Para ajustar como esse tipo de realce cruzado funciona, consulte [Interações visuais](service-reports-visual-interactions.md).

![Realce cruzado](media/power-bi-reports-filters-and-highlighting/power-bi-adhoc-filter.gif)


## <a name="next-steps"></a>Próximas etapas

[A nova experiência de filtro em relatórios do Power BI](power-bi-report-filter-preview.md)

[Adicionar um filtro a um relatório (no Modo de Exibição de Edição)](power-bi-report-add-filter.md)

[Faça um tour pelo painel Filtros do relatório](consumer/end-user-report-filter.md)

[Alterar como elementos visuais de relatórios executam filtro cruzado e realce cruzado entre si](consumer/end-user-interactions.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

