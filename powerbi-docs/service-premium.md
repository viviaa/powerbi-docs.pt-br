---
title: Power BI Premium – o que é?
description: O Power BI Premium é a capacidade dedicada para a sua organização ou equipe, oferecendo desempenho mais confiável e maiores volumes de dados sem exigir a compra de licenças por usuário.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 09/11/2018
LocalizationGroup: Premium
ms.openlocfilehash: 87847575d4fff3d3530847246be5bc8f720b5141
ms.sourcegitcommit: c51461690e8faa121a1325957ca79b7a3975e8b8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44512123"
---
# <a name="power-bi-premium---what-is-it"></a>Power BI Premium – o que é?
O Power BI Premium fornece recursos dedicados à execução do serviço do Power BI para sua organização ou equipe. Ele oferece um desempenho mais confiável e permite maiores volumes de dados. O Premium também permite a ampla distribuição de conteúdo sem a necessidade de adquirir licenças de usuário para visualizadores.

É possível usar o Power BI Premium atribuindo workspaces a uma *capacidade Premium*. A capacidade Premium é um recurso dedicado para sua organização. Workspaces não atribuídos a uma capacidade premium estão em uma *capacidade compartilhada*. Com a capacidade compartilhada, suas cargas de trabalho são executadas em recursos computacionais compartilhados por outros clientes. Na capacidade compartilhada, mais limites são colocados em usuários individuais para garantir a qualidade da experiência para todos os usuários.

[!INCLUDE [powerbi-premium-illustration](./includes/powerbi-premium-illustration.md)]

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="capacity-tiers"></a>Níveis de capacidade

Há dois tipos de capacidade dentro do Power BI. Capacidade compartilhada e a capacidade do Power BI Premium. Veja quais são as diferenças entre eles.

|  | Capacidade compartilhada | Capacidade do Power BI Premium |
| --- | --- | --- |
| **Taxa de atualização** |8/dia |48/dia |
| **Isolamento com hardware dedicado** |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível") |
| **Distribuição do Enterprise para** ***todos os usuários*** | | |
| Compartilhamento e aplicativos |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível")<sup>1</sup> |
| API e controles inseridos |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível")<sup>2</sup> |
| **Publicar relatórios locais do Power BI** |![](media/service-premium/not-available.png "Não disponível") |![](media/service-premium/available.png "Disponível") |

*<sup>1</sup> Para obter mais informações, consulte a funcionalidade [Recursos de usuário com o Power BI Pro e o Power BI Premium](service-free-vs-pro.md).*  
*<sup>2</sup> Aprimoramentos futuros chegando no Power BI Premium.*

### <a name="premium-capacity"></a>Capacidade Premium

Para começar a usar a capacidade do Power BI Premium, é necessário atribuir um espaço de trabalho a uma capacidade. Quando uma capacidade premium dá suporte a um workspace, você obtém:

* **Atualizações agendadas**: com a capacidade compartilhada, as atualizações agendadas para conjuntos de dados de modelo importados estão limitadas a 8 vezes por dia. Para conjuntos de dados em workspaces Premium, é possível agendar atualizações até 48 vezes por dia. Maiores atualizações agendadas não se aplicam a configurações de atualização de cache agendadas para DirectQuery, que permanecem as mesmas entre capacidades Premium e Compartilhadas.
* **Isolamento com hardware dedicado**: em função da natureza da capacidade compartilhada, o desempenho dos relatórios e dashboards pode ser afetado pelas demandas de recursos de outras cargas de trabalho na capacidade, apesar de nossas precauções em relação a isso. Por outro lado, a capacidade Premium oferece desempenho mais consistente e confiável para suas cargas de trabalho ao isolá-las de cargas de trabalho não relacionadas.

Se um aplicativo conta com a capacidade Premium (ou seja, ele é publicado com base em um workspace do aplicativo atribuído à Premium, no momento), o aplicativo publicado pode ser usado por qualquer usuário da organização, independentemente da licença que ele tem.

Para saber mais sobre como atribuir workspaces a uma capacidade Premium, consulte [Manage Power BI Premium](service-admin-premium-manage.md) (Gerenciar o Power BI Premium).

### <a name="shared-capacity"></a>Capacidade compartilhada

Por padrão, o espaço de trabalho está em uma capacidade compartilhada. Isso inclui o *Meu espaço de trabalho* pessoal juntamente com espaços de trabalho do aplicativo. A capacidade compartilhada é a experiência à qual você está acostumado com o Power BI, em que as cargas de trabalho são executadas em recursos computacionais compartilhados por outros clientes.

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Nós de capacidade Premium

O Power BI Premium está disponível em configurações de nó com diferentes capacidades de v-core. Para obter mais informações sobre custo e ofertas específicas de SKU, confira [Preços do Power BI](https://powerbi.microsoft.com/pricing/). Também está disponível uma [calculadora de custos](https://powerbi.microsoft.com/calculator/). Para obter informações sobre planejamento de capacidade de análise inserida, consulte [Planning a Power BI Enterprise Deployment whitepaper (Planejando um white paper de implantação do Power BI Enterprise)](https://aka.ms/pbienterprisedeploy).

* Os nós P podem ser usados para implantações de serviço ou inseridas.
* Os nós EM podem ser usados apenas para implantações inseridas. Os nós EM não têm acesso a funcionalidades Premium, como o compartilhamento de aplicativos com usuários que não têm uma licença do Power BI Pro.

>[!NOTE]
>Os links nesta tabela só funcionam corretamente para os usuários que são administradores globais do Office 365 - os outros usuários recebem um erro 404.

| Nó de capacidade | Total de núcleos virtuais<br/>*(Back-end + front-end)* | Núcleos virtuais de back-end | Núcleos virtuais de front-end | Limites de conexão dinâmica/DirectQuery | Máx. de renderizações de página no horário de pico | Disponibilidade |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 núcleo virtual |0,5 núcleo virtual, 2,5 GB de RAM |0,5 núcleo virtual |3,75 por segundo |150-300 |Disponível |
| [EM2 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 núcleos virtuais |1 núcleo virtual, 5 GB de RAM |1 núcleo virtual |7,5 por segundo |301-600 |Disponível |
| [EM3 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 núcleos virtuais |2 núcleos virtuais, 10 GB de RAM |2 núcleos virtuais | |601-1.200 |Disponível |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 v-cores |4 núcleos virtuais, 25 GB de RAM |4 núcleos virtuais |30 por segundo |1.201-2.400 |Disponível ([mês a mês](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1) também está disponível) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 v-cores |8 núcleos virtuais, 50 GB de RAM |8 v-cores |60 por segundo |2.401-4.800 |Disponível |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 v-cores |16 núcleos virtuais, 100 GB de RAM |16 v-cores |120 por segundo |4.801-9.600 |Disponível |

* Os núcleos virtuais de front-end são responsáveis pelo gerenciamento de documentos de relatório, painel e serviço Web, gerenciamento de direitos de acesso, agendamento, APIs, carregamentos e downloads, e geralmente por tudo o que está relacionado à experiência do usuário.
* Os núcleos virtuais de back-end são responsáveis pelo trabalho pesado: processamento de consultas, gerenciamento de cache, execução de servidores R, atualização de dados, processamento de linguagem natural, alimentações em tempo real, renderizações de relatórios e imagens do servidor. Com os núcleos virtuais de back-end, também é reservada uma determinada quantidade de memória. Ter memória suficiente se tornar especialmente importante ao lidar com grandes modelos de dados ou com um grande número de conjuntos de dados ativos.

## <a name="power-bi-report-server"></a>Servidor de Relatório do Power BI
O Power BI Premium também inclui a capacidade de execução local do Servidor de Relatórios do Power BI em sua organização. Para saber mais, consulte [Get started with Power BI Report Server](report-server/get-started.md) (Introdução ao Servidor de Relatórios do Power BI).

## <a name="next-steps"></a>Próximas etapas
[Perguntas Frequentes do Power BI Premium](service-premium-faq.md)  
[Notas de versão do Power BI Premium](service-premium-release-notes.md)  
[Como comprar o Power BI Premium](service-admin-premium-purchase.md)  
[Gerenciando o Power BI Premium](service-admin-premium-manage.md)  
[White paper do Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)  
[Planejando um white paper de implantação do Power BI Enterprise](https://aka.ms/pbienterprisedeploy)  
[Administração do Power BI em sua organização](service-admin-administering-power-bi-in-your-organization.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
