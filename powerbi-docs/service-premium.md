---
title: O que é o Microsoft Power BI Premium?
description: O Power BI Premium é a capacidade dedicada para a sua organização ou equipe, oferecendo desempenho mais confiável e maiores volumes de dados sem exigir a compra de licenças por usuário.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/12/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: f327cb95c10756f079778d20e62cba4871b95c02
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964929"
---
# <a name="what-is-microsoft-power-bi-premium"></a>O que é o Microsoft Power BI Premium?

> [!NOTE]
> Este artigo está sendo atualizado no momento para descrever novos recursos, fornecer mais detalhes e melhorar a legibilidade. Para obter as informações mais recentes, confira [Implantando e gerenciando capacidades do Power BI Premium](whitepaper-powerbi-premium-deployment.md).

O Power BI Premium fornece recursos dedicados à execução do serviço do Power BI para sua organização. Ele oferece um desempenho mais confiável e permite maiores volumes de dados. O Premium também habilita a ampla distribuição de conteúdo sem a necessidade de comprar licenças Pro por usuário para consumidores de conteúdo.  

## <a name="premium-capacity-and-shared-capacity"></a>Capacidade Premium e capacidade compartilhada

É possível usar o Power BI Premium atribuindo workspaces a uma *capacidade Premium*. A capacidade Premium é um recurso dedicado para sua organização. Workspaces não atribuídos a uma capacidade premium estão em uma *capacidade compartilhada*. Com a capacidade compartilhada, suas cargas de trabalho são executadas em recursos computacionais compartilhados por outros clientes.

A imagem a seguir mostra a relação entre a capacidade Premium e capacidade compartilhada usando a organização Contoso como exemplo.

![Ilustração do Power BI Premium](media/service-premium/premium-chart.png)

| Área | Descrição |
| --- | --- |
| **(1)** Itens dentro de uma capacidade Premium | <ul><li>Acessar workspaces de aplicativo (como membros ou administradores) e publicar aplicativos requer uma licença Power BI Pro.<li>O compartilhamento de um arquivo exige uma licença Pro, mas isso não é exigido para o uso de um aplicativo.<li>Todos os destinatários do dashboard, independentemente das licenças atribuídas, podem definir alertas de dados.<li>APIs REST para inserção utilizam uma conta de serviço com uma licença Pro em vez de uma conta de usuário.</ul> |
| **(2)** Meu workspace em capacidade compartilhada | <ul><li>Compartilhar e consumir um aplicativo exige uma licença Pro.</ul> |
| **(3)** Workspaces do aplicativo na Capacidade compartilhada | <ul><li>Qualquer uso de aplicativo exige uma licença Pro.</ul>|
| | |

Na capacidade compartilhada, o Power BI coloca mais limites em usuários individuais para garantir a qualidade da experiência para todos os usuários. Por padrão, seu workspace está em uma capacidade compartilhada, incluindo seu *Meu workspace* pessoal e workspaces de aplicativo.

A tabela a seguir fornece um resumo das diferenças entre a capacidade compartilhada e a capacidade Premium:

|  | Capacidade compartilhada | Capacidade do Power BI Premium |
| --- | --- | --- |
| **Taxa de atualização** |8/dia |48/dia |
| Isolamento com hardware dedicado |![Não disponível](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| Distribuição do Enterprise para *todos os usuários* | | |
| Compartilhamento e aplicativos |![Não disponível](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| API e controles inseridos |![Não disponível](media/service-premium/not-available.png) |![](media/service-premium/available.png)<sup>[1](#fnt1)</sup> |
| Publicar relatórios locais do Power BI |![Não disponível](media/service-premium/not-available.png) |![](media/service-premium/available.png) |
| | | |

<a name="fnt1">1</a> Próximos aprimoramentos chegando no Power BI Premium.



### <a name="premium-capacity-nodes"></a>Nós de capacidade Premium

O Power BI Premium está disponível em configurações de nó com diferentes capacidades de v-core. Para obter mais informações sobre custo e ofertas específicas de SKU, confira [Preços do Power BI](https://powerbi.microsoft.com/pricing/). Também está disponível uma [calculadora de custos](https://powerbi.microsoft.com/calculator/). Para obter informações sobre planejamento de capacidade de análise inserida, consulte [Planning a Power BI Enterprise Deployment whitepaper (Planejando um white paper de implantação do Power BI Enterprise)](https://aka.ms/pbienterprisedeploy). Para resumir:

* Os nós P podem ser usados para implantações de serviço ou inseridas.

* Os nós EM podem ser usados apenas para implantações inseridas. Os nós EM não têm acesso a funcionalidades Premium, como o compartilhamento de aplicativos com usuários que não têm uma licença do Power BI Pro.

| Nó de capacidade | Total de núcleos virtuais<br/>*(Back-end+front-end)*  | Núcleos virtuais de back-end <sup>[1](#fn1)</sup> | Núcleos virtuais de front-end<sup>[2](#fn2)</sup> | Limites de conexão dinâmica/DirectQuery | Máximo de atualizações simultâneas |
| --- | --- | --- | --- | --- | --- |
| EM1 (mês a mês) |1 núcleo virtual |0,5 núcleo virtual, 2,5 GB de RAM |0,5 núcleo virtual |3,75 por segundo |  1 |
| EM2 (mês a mês) |2 núcleos virtuais |1 núcleo virtual, 5 GB de RAM |1 núcleo virtual |7,5 por segundo |  2 |
| EM3 (mês a mês) |4 núcleos virtuais |2 núcleos virtuais, 10 GB de RAM |2 núcleos virtuais | 15 | 3 |
| P1 |8 v-cores |4 núcleos virtuais, 25 GB de RAM |4 núcleos virtuais |30 por segundo | 6 |
| P2 |16 v-cores |8 núcleos virtuais, 50 GB de RAM |8 v-cores |60 por segundo | 12 |
| P3 |32 v-cores |16 núcleos virtuais, 100 GB de RAM |16 v-cores |120 por segundo | 24 |
| | | | | | |

<a name="fn1">1</a>: Os núcleos virtuais de front-end são responsáveis pelo serviço Web. Por exemplo, gerenciamento de painéis e documentos de relatórios, gerenciamento de direitos de acesso, agendamento, APIs, carregamentos e downloads, e geralmente por tudo o que está relacionado à experiência do usuário. 

<a name="fn2">2</a>: Os núcleos virtuais de back-end são responsáveis pelo trabalho pesado, como processamento de consultas, gerenciamento de cache, execução de servidores R, atualização de dados, processamento de linguagem natural, feeds em tempo real, renderizações de relatórios e imagens do lado do servidor. Com os núcleos virtuais de back-end, também é reservada uma determinada quantidade de memória. Ter memória suficiente se tornar especialmente importante ao lidar com grandes modelos de dados ou com um grande número de conjuntos de dados ativos.

## <a name="workloads-in-premium-capacity"></a>Cargas de trabalho na capacidade Premium

Por padrão, as capacidades do Power BI Premium e do Power BI Embedded só são compatíveis com a carga de trabalho associada à execução de consultas no Power BI na nuvem. O Premium também dá suporte a cargas de trabalho adicionais para **IA**, **Fluxos de dados** e **Relatórios paginados**. Para que as cargas de trabalho possam usar os recursos da capacidade, elas devem ser ativadas no portal de administração do Power BI ou por meio da API REST do Power BI. Cada carga de trabalho tem configurações padrão para a quantidade máxima de memória que cada carga de trabalho pode consumir. No entanto, pode-se definir diferentes configurações de consumo de memória para determinar como as cargas de trabalho afetam umas às outras e consomem seus recursos de capacidade. Para saber mais, confira [Configurar cargas de trabalho](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Servidor de Relatórios do Power BI

O Power BI Premium também inclui a capacidade de execução local do Servidor de Relatórios do Power BI na sua organização. Para saber mais, consulte [Get started with Power BI Report Server](report-server/get-started.md) (Introdução ao Servidor de Relatórios do Power BI).

## <a name="next-steps"></a>Próximas etapas

[Implantando e gerenciando capacidades do Power BI Premium](whitepaper-powerbi-premium-deployment.md)   
[Como comprar o Power BI Premium](service-admin-premium-purchase.md)   
[Perguntas Frequentes do Power BI Premium](service-premium-faq.md)   



Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
