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
ms.openlocfilehash: 50fbb175640e38431db62df34276417f1080e42a
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55430340"
---
# <a name="power-bi-embedded-performance-best-practices"></a>Práticas recomendadas de desempenho do Power BI Embedded

Este artigo fornece recomendações para renderização mais rápido de relatórios, dashboards e blocos em seu aplicativo

## <a name="embed-parameters"></a>Inserir parâmetros

O método Powerbi.embed() recebe poucos parâmetros para inserir um relatório, um dashboard ou um bloco. Esses parâmetros têm implicações de desempenho.

### <a name="embed-url"></a>URL de inserção

Evite gerar a URL de inserção sozinho. Em vez disso, certifique-se de obter a URL de inserção chamando a API [Obter relatórios](/rest/api/power-bi/reports/getreportsingroup), a [Obter dashboards](/rest/api/power-bi/dashboards/getdashboardsingroup) ou a [Obter blocos](/rest/api/power-bi/dashboards/gettilesingroup). Adicionamos um novo parâmetro à URL chamado **_config_**, usado para aprimoramentos de desempenho.

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

* Use sempre a versão mais recente do [Power BI Desktop](https://powerbi.microsoft.com/desktop/).

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
