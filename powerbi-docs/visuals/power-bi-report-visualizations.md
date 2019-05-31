---
title: Visão geral de visualizações de relatório no serviço do Power BI e Power BI Desktop
description: Visão geral de visualizações (visuais) de relatório no Microsoft Power BI.
author: mihart
ms.author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: SYk_gWrtKvM
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/28/2019
LocalizationGroup: Visualizations
ms.openlocfilehash: d470a262bd8a5e6590746fb07889b1230f5cfc25
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375659"
---
# <a name="visualizations-in-power-bi-reports"></a>Visualizações em relatórios do Power BI

Visualizações (também conhecidas como visuais) exibem informações que foram descobertas nos dados. Um relatório do Power BI pode ter uma única página com um visual ou então páginas repletas de visuais. No serviço do Power BI, os visuais podem ser [fixados de relatórios em dashboards](../service-dashboard-pin-tile-from-report.md).

É importante fazer a distinção entre relatórios *designers* e o relatório *consumidores* se você estiver criando ou modificando o relatório, você é um designer.  Designers de tem permissões de edição para o relatório e seu conjunto de dados subjacente. No Power BI Desktop, isso significa que você pode abrir o conjunto de dados no modo de exibição de dados e criar elementos visuais no modo de exibição de Relatório. No serviço do Power BI, isso significa que você pode abrir o relatório ou conjunto de dados no editor de relatório no [exibição de edição](../consumer/end-user-reading-view.md). Se um relatório ou dashboard foi [compartilhado com você](../consumer/end-user-shared-with-me.md), você é um **consumidor** de relatório. Você poderá exibir e interagir com o relatório e os respectivos visuais, mas você não poderá salvar as alterações principais.

Há muitos tipos de visual diferentes diretamente no painel VISUALIZAÇÕES do Power BI.

![](media/power-bi-report-visualizations/power-bi-templates.png)

E para ainda mais opções, visite o [site da comunidade do Microsoft AppSource](https://appsource.microsoft.com) para localizar e [baixar](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) [ visuais personalizados](../developer/custom-visual-develop-tutorial.md) fornecidos pela Microsoft e pela comunidade.

<iframe width="560" height="315" src="https://www.youtube.com/embed/SYk_gWrtKvM?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>


  Se você não estiver familiarizado com o Power BI ou precisar de um lembrete, use os links abaixo para aprender os fundamentos de visualizações de Power BI.  Como alternativa, use o Sumário (no lado esquerdo deste artigo) para encontrar informações ainda mais úteis.

## <a name="add-a-visualization-in-power-bi"></a>Adicionar uma visualização no Power BI

[Crie visualizações](power-bi-report-add-visualizations-i.md) nas páginas de seus relatórios. Navegue na [lista de visualizações e tutoriais de visualização disponíveis.](power-bi-visualization-types-for-reports-and-q-and-a.md) 

## <a name="upload-a-custom-visualization-and-use-it-in-power-bi"></a>Carregar uma visualização personalizada e usá-la no Power BI

Adicione uma visualização personalizada que você criou ou que encontrou no [site da comunidade do Microsoft AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals). Se sentindo criativo? Aprofunde-se em nosso código-fonte e use nossas [ferramentas para desenvolvedores](../developer/custom-visual-develop-tutorial.md) para criar um novo tipo de visualização e [compartilhá-la com a comunidade](../developer/office-store.md). Para saber mais sobre o desenvolvimento de um visual personalizado, confira [Developing a Power BI custom visual](../developer/custom-visual-develop-tutorial.md) (Desenvolvimento de um visual personalizado do Power BI).

## <a name="change-the-visualization-type"></a>Altere o tipo de visualização

Tente [alterar o tipo de visualização](power-bi-report-change-visualization-type.md) para ver o que funciona melhor com seus dados.

## <a name="pin-the-visualization"></a>Fixe a visualização

No serviço do Power BI, quando a visualização estiver da forma que deseja, é possível [fixá-la em um dashboard](../service-dashboard-pin-tile-from-report.md) como um bloco. Se você alterar a visualização usada no relatório depois de fixá-lo, o bloco no dashboard não será alterado – se fosse um gráfico de linhas, ele permaneceria um gráfico de linhas, mesmo que você o alterasse para um gráfico de rosca no relatório.

## <a name="limitations-and-considerations"></a>Limitações e considerações
- Dependendo da fonte de dados e o número de campos (medidas ou colunas), um visual pode ser carregado lentamente.  É recomendável limitar os visuais para 10 a 20 campos de total, por motivos de desempenho e legibilidade. 

- O limite superior para elementos visuais é de 100 campos (medidas ou colunas). Se seu visual não for carregado, reduza o número de campos.   

## <a name="next-steps"></a>Próximas etapas

* [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)
* [Visuais Personalizados](../power-bi-custom-visuals.md)