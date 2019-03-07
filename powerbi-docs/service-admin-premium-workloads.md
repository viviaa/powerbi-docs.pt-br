---
title: Como configurar cargas de trabalho no Power BI Premium
description: Saiba como configurar cargas de trabalho em uma capacidade Premium do Power BI.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/26/2019
LocalizationGroup: Premium
ms.openlocfilehash: 5b9bec67fef672d219b11bf3b3750959e72410b6
ms.sourcegitcommit: 364ffa1178cdfb0a20acffc0fd79922ebc892d72
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/02/2019
ms.locfileid: "57226056"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurar cargas de trabalho em uma capacidade Premium

Este artigo descreve como habilitar e configurar cargas de trabalho para as capacidades Premium do Power BI. Por padrão, as capacidades dão suporte apenas à carga de trabalho associada à execução de consultas do Power BI. As cargas de trabalho de consulta são otimizadas para os recursos determinados pelo SKU da capacidade Premium e limitadas por esses recursos. As capacidades Premium também dão suporte a cargas de trabalho adicionais que possam usar recursos de capacidade.

## <a name="configure-workloads"></a>Configurar cargas de trabalho

Habilite e configure cargas de trabalho adicionais para [Fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium) e [Relatórios paginados](paginated-reports-save-to-power-bi-service.md). Os valores de memória padrão para essas cargas de trabalho se baseiam nos nós de capacidade disponíveis para o SKU. As configurações de memória máxima não são cumulativas. A memória até o valor máximo especificado é alocada dinamicamente para fluxos de dados, mas é alocada estaticamente para relatórios paginados. 

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Para configurar cargas de trabalho no portal de administração do Power BI

1. Em **Configurações de capacidade** > **CAPACIDADES PREMIUM**, selecione uma capacidade.

1. Em **MAIS OPÇÕES**, expanda **Cargas de trabalho**.

1. Habilite uma ou mais cargas de trabalho e defina um valor para **Memória Máxima**.   

    
    ![Habilitar cargas de trabalho](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Clique em **Aplicar**.

> [!NOTE]
> Se você habilitar a carga de trabalho de relatórios paginados, os relatórios paginados permitirão executar seu próprio código ao renderizar um relatório (como a alteração dinâmica da cor do texto com base no conteúdo). O Power BI Premium executa relatórios paginados em um espaço contido dentro da capacidade. A memória máxima especificada para esse espaço é usada, independentemente de a carga de trabalho estar ativa. Se você usar relatórios ou fluxos de dados do Power BI na mesma capacidade, defina uma memória baixa o suficiente para relatórios paginados de modo que ela não afete negativamente outras cargas de trabalho. em circunstâncias raras, a carga de trabalho de relatórios paginados pode se tornar indisponível. Nesse caso, a carga de trabalho mostra o estado de erro no Portal de Administração, e os usuários veem tempos limite para renderização de relatório. Para atenuar esse problema, desabilite a carga de trabalho e habilite-a novamente.


### <a name="rest-api"></a>API REST

As cargas de trabalho podem ser habilitadas e atribuídas a uma capacidade usando as APIs REST de [Capacidades](https://docs.microsoft.com/rest/api/power-bi/capacities).


## <a name="next-steps"></a>Próximas etapas

[Gerenciamento otimização de recursos de capacidade do Power BI Premium](service-premium-understand-how-it-works.md)   
[Preparação de dados de autoatendimento no Power BI com Fluxos de dados](service-dataflows-overview.md)   
[O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Mais perguntas? [Perguntar à Comunidade do Power BI](http://community.powerbi.com/)