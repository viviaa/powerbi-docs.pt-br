---
title: Como configurar cargas de trabalho no Power BI Premium
description: Saiba como configurar cargas de trabalho em uma capacidade Premium do Power BI.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/15/2019
LocalizationGroup: Premium
ms.openlocfilehash: c84bebef5589ec391e3640ff3be674b1fb5a0ebd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564875"
---
# <a name="configure-workloads-in-a-premium-capacity"></a>Configurar cargas de trabalho em uma capacidade Premium

Este artigo descreve como habilitar e configurar cargas de trabalho para as capacidades Premium do Power BI. Por padrão, as capacidades dão suporte apenas à carga de trabalho associada à execução de consultas do Power BI. Habilite e configure também as cargas de trabalho adicionais para **[IA (Serviços Cognitivos)](service-cognitive-services.md)** , **[Fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium)** e **[Relatórios paginados](paginated-reports-save-to-power-bi-service.md)** .

## <a name="default-memory-settings"></a>Configurações de memória padrão

As cargas de trabalho de consulta são otimizadas para os recursos determinados pelo SKU da capacidade Premium e limitadas por esses recursos. As capacidades Premium também dão suporte a cargas de trabalho adicionais que podem usar seus recursos de capacidade. Os valores de memória padrão para essas cargas de trabalho se baseiam nos nós de capacidade disponíveis para o SKU. As configurações de memória máxima não são cumulativas. A memória até o valor máximo especificado é alocada dinamicamente para IA e fluxos de dados, mas é alocada estaticamente para relatórios paginados. 

### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>SKUs do Microsoft Office para cenários SaaS (Software como Serviço)

|                     | EM2                      | EM3                       | P1                      | P2                       | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|--------------------------|
| AI | N/D | N/D | padrão de 20%; 20% (mínimo) | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% |
| Fluxos de dados | N/D |Padrão de 20%; mínimo de 12%  | Padrão de 20%; mínimo de 5%  | Padrão de 20%; mínimo de 3% | Padrão de 20%; mínimo de 2%  |
| Relatórios paginados | N/D |N/D | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% | Padrão de 20%; mínimo de 2,5% |
| | | | | | |

### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>SKUs do Microsoft Azure para cenários PaaS (Plataforma como Serviço)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| AI | N/D                      | padrão de 20%; 100% (mínimo)                     | padrão de 20%; 50% (mínimo)                     | padrão de 20%; 20% (mínimo) | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% |
| Fluxos de dados         | Padrão de 40%; mínimo de 40% | Padrão de 24%; mínimo de 24% | Padrão de 20%; mínimo de 12% | Padrão de 20%; mínimo de 5%  | Padrão de 20%; mínimo de 3% | Padrão de 20%; mínimo de 2%   |
| Relatórios paginados | N/D                      | Não aplicável                      | N/D                     | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% | Padrão de 20%; mínimo de 2,5% |
| | | | | | |

## <a name="workload-settings"></a>Configurações de carga de trabalho

### <a name="ai-preview"></a>IA (versão prévia)

Além de **Max Memory** definir, a carga de trabalho de AI tem uma configuração adicional, **permitir o uso do Power BI Desktop**. O padrão é **desativar**. Essa configuração é reservada para uso futuro e não pode aparecer em todos os locatários.

### <a name="datasets-preview"></a>Conjuntos de dados (visualização)

Por padrão, a carga de trabalho de conjuntos de dados está habilitada e não pode ser desabilitada. Essa carga de trabalho contém uma configuração adicional, **ponto de extremidade XMLA**. O padrão é **1**, que significa habilitada. Essa configuração especifica que as conexões de aplicativos de cliente honrar a associação de grupo de segurança definida nos níveis de aplicativo e o espaço de trabalho. Para obter mais informações, consulte [conectar-se a conjuntos de dados com ferramentas e aplicativos cliente](service-premium-connect-tools.md).

### <a name="dataflows"></a>Fluxos de dados

Além de **Max Memory** definir, a carga de trabalho de fluxos de dados tem uma configuração adicional, **tamanho do contêiner**. Essa configuração permite otimizar o desempenho da carga de trabalho de fluxo de dados para o processamento de fluxos de dados mais complexos, com uso intenso de computação.

Ao atualizar um fluxo de dados, a carga de trabalho do fluxo de dados gera um contêiner para cada entidade no fluxo de dados. Cada contêiner pode pegar a memória até o volume no especificado na configuração de tamanho do contêiner. É o padrão para todos os SKUs **700 MB**. Você talvez queira alterar essa configuração se:

- Fluxos de dados levarem muito tempo para atualizar ou falha de atualização de fluxo de dados em um tempo limite.
- Entidades de fluxo de dados incluem etapas de computação, por exemplo, uma junção.  

É um é recomendável que você use o [métricas de capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) aplicativo para analisar o desempenho da carga de trabalho de fluxo de dados. 

Em alguns casos, aumentar o tamanho do contêiner pode não melhorar o desempenho. Por exemplo, se o fluxo de dados estiver recebendo dados somente de uma fonte sem executar cálculos significativos, alterar o tamanho do contêiner provavelmente não ajudará. Aumentar o tamanho do contêiner pode ajudar se ele permitirá que a carga de trabalho de fluxo de dados alocar mais memória para a entidade operações de atualização. Por ter mais memória alocada, ela pode reduzir o tempo necessário para atualizar entidades intensamente computadas. 

O valor do tamanho do contêiner não pode exceder a memória máxima para a carga de trabalho de fluxos de dados. Por exemplo, uma capacidade de P1 tem 25GB de memória. Se a carga de trabalho do fluxo de dados Max Memory (%) é definido como 20%, o contêiner de tamanho (MB) não pode exceder 5000. Em todos os casos, o tamanho do contêiner não pode exceder Memory máxima, mesmo que você defina um valor mais alto. 

### <a name="paginated-reports-preview"></a>Relatórios paginados (visualização)

Relatórios paginados permitem que o código personalizado ser executado ao renderizar um relatório. Por exemplo, alterar dinamicamente a cor do texto com base no conteúdo, que pode levar mais memória. O Power BI Premium executa relatórios paginados em um espaço contido dentro da capacidade. O Memory máxima especificada será usada *ou não* a carga de trabalho está ativa. Se alterar a configuração de memória máxima padrão, verifique se você defini-la baixa o suficiente que ele não afeta negativamente outras cargas de trabalho.

Em alguns casos, a carga de trabalho relatórios paginados pode se tornar indisponível. Nesse caso, a carga de trabalho mostra o estado de erro no portal de administração e os usuários veem tempos limite para renderização de relatório. Para atenuar esse problema, desabilite a carga de trabalho e, em seguida, habilitá-la novamente.

## <a name="configure-workloads"></a>Configurar cargas de trabalho

Maximize os recursos disponíveis da sua capacidade, habilitando as cargas de trabalho somente se elas forem usadas. Altere as configurações de memória apenas quando tiver determinado que as configurações padrão não estão atendendo aos requisitos de recursos de capacidade.  

### <a name="to-configure-workloads-in-the-power-bi-admin-portal"></a>Para configurar cargas de trabalho no portal de administração do Power BI

1. Em **Configurações de capacidade** > **CAPACIDADES PREMIUM**, selecione uma capacidade.

1. Em **MAIS OPÇÕES**, expanda **Cargas de trabalho**.

1. Habilite uma ou mais cargas de trabalho e defina um valor para **Memória Máxima**.   

    
    ![Habilitar cargas de trabalho](media/service-admin-premium-workloads/admin-portal-workloads.png)

1. Clique em **Aplicar**.

### <a name="rest-api"></a>API REST

As cargas de trabalho podem ser habilitadas e atribuídas a uma capacidade usando as APIs REST de [Capacidades](https://docs.microsoft.com/rest/api/power-bi/capacities).

## <a name="monitoring-workloads"></a>Monitoramento de cargas de trabalho

O [aplicativo de Métricas de capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) fornece o conjunto de dados, os fluxos de dados e as métricas de relatórios paginados para monitorar as cargas de trabalho habilitadas para suas capacidades. 

## <a name="next-steps"></a>Próximas etapas

[Otimizando as capacidades do Power BI Premium](service-premium-capacity-optimize.md)     
[Preparação de dados de autoatendimento no Power BI com Fluxos de dados](service-dataflows-overview.md)   
[O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)   

Mais perguntas? [Perguntar à Comunidade do Power BI](http://community.powerbi.com/)