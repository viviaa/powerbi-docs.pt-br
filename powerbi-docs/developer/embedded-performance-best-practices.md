---
title: Práticas recomendadas de desempenho do Power BI Embedded
description: Este artigo fornece uma orientação para as práticas recomendadas de análise integrada
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-embedded
ms.topic: conceptual
ms.date: 12/12/2018
ms.openlocfilehash: 025d843158795e7c36a5a278f2022349a9b72ca6
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54277148"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Práticas recomendadas de desempenho do Power BI Embedded

Este artigo fornece recomendações para renderização mais rápido de relatórios, dashboards e blocos em seu aplicativo

## <a name="embed-parameters"></a>Inserir parâmetros

O método Powerbi.embed() recebe poucos parâmetros para inserir um relatório, um dashboard ou um bloco. Esses parâmetros têm implicações de desempenho.

### <a name="embed-url"></a>URL de inserção

Evite gerar a URL de inserção sozinho. Em vez disso, certifique-se de obter a URL de inserção chamando a API [Obter relatórios](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Freports%2Fgetreportsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=22lkqRM2w1MQfrM8dooedaPqqIU8PufTq9TT4VDzRo0%3D&reserved=0), a [Obter dashboards](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgetdashboardsingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256168308&sdata=nfWRgbSoXVF42Rg%2Ba9491u19uksXp%2FAyz%2Fa%2Ba7%2FCtdA%3D&reserved=0) ou a [Obter blocos](https://na01.safelinks.protection.outlook.com/?url=https%3A%2F%2Fdocs.microsoft.com%2Fen-us%2Frest%2Fapi%2Fpower-bi%2Fdashboards%2Fgettilesingroup&data=02%7C01%7CMark.Ghanayem%40microsoft.com%7C07ca68ceb37a48e3f3de08d64968707a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C636777110256178318&sdata=LgZ27TynNpqQJDrb3aHWGQXIS%2FzichAO9De5M2uhF1Q%3D&reserved=0). Adicionamos um novo parâmetro à URL chamado **_config_**, usado para aprimoramentos de desempenho.

### <a name="permissions"></a>Permissões

Forneça permissões de **Exibição** se você não pretende inserir um relatório no **Modo de edição**. Dessa forma, o código de inserção não inicializa componentes usados para o Modo de edição.

### <a name="filters-bookmarks-and-slicers"></a>Filtros, indicadores e segmentações

Normalmente, os visuais de relatório são salvos com os dados armazenados em cache. Os dados armazenados em cache são usados para oferecer desempenho percebido. Os relatórios renderizam dados armazenados em cache enquanto as consultas são executadas. Se os filtros, os indicadores ou as segmentações são fornecidos, os dados armazenados em cache não são relevantes. Então, os visuais são renderizados somente após a execução da consulta de visual.

Se você inserir relatórios com os mesmos filtros, para evitar passar uma lista de filtros na configuração de carga, salve o relatório com os filtros já aplicados.

## <a name="preload"></a>Pré-carregamento

Use a API JavaScript de *pré-carregamento* para aprimorar o desempenho do usuário final.
O powerbi.preload() baixa javascript, arquivos css e outros artefatos, que é usado futuramente para inserir em um relatório.

Chame o pré-carregamento se não inserir o relatório imediatamente. Por exemplo, se você inserir um relatório em um clique de botão, será melhor chamar o pré-carregamento quando a página anterior for carregada. Em seguida, quando o usuário do aplicativo clica no botão, a renderização é mais rápida.

## <a name="measure-performance"></a>Medir o desempenho

Para medir o desempenho, use:

1. Carregado: tempo até que o relatório seja inicializado (o usuário não vê nenhum giro).
2. Processado: tempo até que todo o relatório seja renderizado usando dados reais. O evento renderizado é disparado cada vez que o relatório é renderizado novamente (ou seja, após aplicar filtros). Para medir um relatório pela primeira vez, certifique-se de fazer os cálculos no primeiro evento gerado.

Os dados armazenados em cache são renderizados quando disponíveis, mas nós ainda não temos um evento para esses dados.

## <a name="update-tools-and-sdk-packages"></a>Atualizar ferramentas e pacotes SDK

Mantenha as ferramentas e os pacotes SDK atualizados.

* Use sempre a versão mais recente do [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).

* Instale a versão mais recente do [SDK cliente do Power BI](https://github.com/Microsoft/PowerBI-JavaScript). Continuamos lançando mais aprimoramentos, não se esqueça de acompanhar de tempos em tempos.

* Pacotes a serem instalados:
    * Pacote Npm: powerbi-client
    * Pacote NuGet: Microsoft.PowerBI.JavaScript

> [!Note]
> Lembre-se de que o tempo de carregamento depende principalmente dos elementos relevantes para o relatório e os próprios dados. Como o número de visuais, o tamanho dos dados e a complexidade das consultas e as medidas calculadas. Siga as [práticas recomendadas](../power-bi-reports-performance.md) para aprimorar o tempo de carregamento do relatório.

## <a name="next-steps"></a>Próximas etapas

* [Práticas recomendadas de desempenho de relatório do Power BI](../power-bi-reports-performance.md)
* [Como solucionar problemas do Power BI Embedded](embedded-troubleshoot.md)
* [Perguntas frequentes do Power BI Embedded](embedded-faq.md)
