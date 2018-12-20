---
title: Entender a interação de elementos visuais em um relatório
description: Documentação para os usuários finais do Power BI que explica como os visuais interagem em uma página de relatório.
author: mihart
manager: kvivek
ms.custom: seodec18
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: 406f1f6428d5ce26401720220eaffe32314a9bbd
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53280410"
---
# <a name="how-visuals-cross-filter-each-other-in-a-power-bi-report"></a>Como os visuais realizam filtragem cruzada entre si em um relatório do Power BI
Um dos melhores recursos do Power BI é a maneira com que todos os elementos visuais na página de um relatório são interconectados. Se você selecionar um ponto de dados em um dos elementos visuais, todos os outros visuais na página que contêm esses dados serão alterados, com base nessa seleção. 

![vídeo de interação de visuais](media/end-user-interactions/interactions.gif)

Por padrão, as visualizações na página do relatório podem ser usadas para realizar filtragem cruzada, realce cruzado e análise das outras visualizações na página. Por exemplo, selecionar um estado em uma visualização de mapa pode realçar o gráfico de colunas e filtrar o gráfico de linhas para exibir apenas os dados que se aplicam a um estado.

Veja [Sobre filtragem e realce](../power-bi-reports-filters-and-highlighting.md). E se você tiver uma visualização que é compatível com [drill down](../power-bi-visualization-drill-down.md), por padrão, fazer drill down em uma visualização não afeta as outras visualizações na página do relatório. 

A interação exata dos visuais em uma página é definida pelo relatório *designer*. Designers têm opções para ativar e desativar a interações visuais e para alterar o comportamento padrão de filtragem cruzada, realce cruzado e análise.
  
> [!NOTE]
> Os termos *filtro cruzado* e *realce cruzado* são usados para distinguir o comportamento descrito aqui do que acontece quando você usa o painel **Filtros** painel para filtrar e realçar visualizações.  

### <a name="next-steps"></a>Próximas etapas
[Como usar filtros de relatório](../power-bi-how-to-report-filter.md)
