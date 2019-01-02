---
title: O que é o Microsoft Power BI Premium?
description: O Power BI Premium é a capacidade dedicada para a sua organização ou equipe, oferecendo desempenho mais confiável e maiores volumes de dados sem exigir a compra de licenças por usuário.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/21/2018
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: ea26ba39a9ec06b79330719afd4fb3b3a572d912
ms.sourcegitcommit: 9913c213d40b45ba83c6c3b3a7ef0b757800e3ad
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53301794"
---
# <a name="what-is-microsoft-power-bi-premium"></a>O que é o Microsoft Power BI Premium?

O Microsoft Power BI Premium fornece recursos dedicados à execução do serviço do Power BI para sua organização. Ele oferece um desempenho mais confiável e permite maiores volumes de dados. O Premium também habilita a ampla distribuição de conteúdo sem a necessidade de comprar licenças Pro por usuário para consumidores de conteúdo. Para obter informações sobre compra, confira [Como comprar o Power BI Premium](service-admin-premium-purchase.md).

<iframe width="560" height="315" src="https://www.youtube.com/embed/lNQDkN0GXzU?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

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

A tabela a seguir fornece um resumo das diferenças entre capacidade compartilhada e a capacidade Premium.

|  | Capacidade compartilhada | Capacidade do Power BI Premium |
| --- | --- | --- |
| **Taxa de atualização** |8/dia |48/dia |
| **Isolamento com hardware dedicado** |![Não disponível](media/service-premium/not-available.png) |![Disponível](media/service-premium/available.png) |
| **Distribuição do Enterprise para** _**todos os usuários**_ | | |
| Compartilhamento e aplicativos |![Não disponível](media/service-premium/not-available.png) |![Disponível](media/service-premium/available.png) |
| API e controles inseridos |![Não disponível](media/service-premium/not-available.png) |![Disponível](media/service-premium/available.png)<sup>2</sup> |
| **Publicar relatórios locais do Power BI** |![Não disponível](media/service-premium/not-available.png) |![Disponível](media/service-premium/available.png) |
| | | |

*<sup>1</sup> Para obter mais informações, consulte [Recursos por tipo de licença](service-features-license-type.md).*  
*<sup>2</sup> Aprimoramentos futuros chegando no Power BI Premium.*

Para saber mais sobre como atribuir workspaces a uma capacidade Premium, consulte [Manage Power BI Premium](service-admin-premium-manage.md) (Gerenciar o Power BI Premium).

<a name="premiumskus"/>

### <a name="premium-capacity-nodes"></a>Nós de capacidade Premium

O Power BI Premium está disponível em configurações de nó com diferentes capacidades de v-core. Para obter mais informações sobre custo e ofertas específicas de SKU, confira [Preços do Power BI](https://powerbi.microsoft.com/pricing/). Também está disponível uma [calculadora de custos](https://powerbi.microsoft.com/calculator/). Para obter informações sobre planejamento de capacidade de análise inserida, consulte [Planning a Power BI Enterprise Deployment whitepaper (Planejando um white paper de implantação do Power BI Enterprise)](https://aka.ms/pbienterprisedeploy). Para resumir:

* Os nós P podem ser usados para implantações de serviço ou inseridas.

* Os nós EM podem ser usados apenas para implantações inseridas. Os nós EM não têm acesso a funcionalidades Premium, como o compartilhamento de aplicativos com usuários que não têm uma licença do Power BI Pro.

>[!NOTE]
>Links nesta tabela só funcionam corretamente para os usuários que estão na função de Administrador Global do Office 365. Os demais recebem um erro 404.

| Nó de capacidade | Total de núcleos virtuais<br/>*(Back-end + front-end)* | Núcleos virtuais de back-end | Núcleos virtuais de front-end | Limites de conexão dinâmica/DirectQuery | Disponibilidade |
| --- | --- | --- | --- | --- | --- | --- |
| [EM1 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |1 núcleo virtual |0,5 núcleo virtual, 2,5 GB de RAM |0,5 núcleo virtual |3,75 por segundo |Disponível |
| [EM2 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |2 núcleos virtuais |1 núcleo virtual, 5 GB de RAM |1 núcleo virtual |7,5 por segundo |Disponível |
| [EM3 (mês a mês)](https://portal.office.com/SubscriptionDetails?OfferId=4004702D-749C-4F74-BF47-3048F1833780&adminportal=1) |4 núcleos virtuais |2 núcleos virtuais, 10 GB de RAM |2 núcleos virtuais | |Disponível |
| [P1](https://portal.office.com/SubscriptionDetails?OfferId=b3ec5615-cc11-48de-967d-8d79f7cb0af1&adminportal=1) |8 v-cores |4 núcleos virtuais, 25 GB de RAM |4 núcleos virtuais |30 por segundo |Disponível ([mês a mês](https://portal.office.com/SubscriptionDetails?OfferId=E4C8EDD3-74A1-4D42-A738-C647972FBE81&adminportal=1) também está disponível) |
| [P2](https://portal.office.com/SubscriptionDetails?OfferId=062F2AA7-B4BC-4B0E-980F-2072102D8605&adminportal=1) |16 v-cores |8 núcleos virtuais, 50 GB de RAM |8 v-cores |60 por segundo |Disponível |
| [P3](https://portal.office.com/SubscriptionDetails?OfferId=40c7d673-375c-42a1-84ca-f993a524fed0&adminportal=1) |32 v-cores |16 núcleos virtuais, 100 GB de RAM |16 v-cores |120 por segundo |Disponível |
| | | | | | | |

* Os núcleos virtuais de front-end são responsáveis pelo gerenciamento de documentos de relatório, painel e serviço Web, gerenciamento de direitos de acesso, agendamento, APIs, carregamentos e downloads, e geralmente por tudo o que está relacionado à experiência do usuário.

* Os núcleos virtuais de back-end são responsáveis pelo trabalho pesado: processamento de consultas, gerenciamento de cache, execução de servidores R, atualização de dados, processamento de linguagem natural, alimentações em tempo real, renderizações de relatórios e imagens do servidor. Com os núcleos virtuais de back-end, também é reservada uma determinada quantidade de memória. Ter memória suficiente se tornar especialmente importante ao lidar com grandes modelos de dados ou com um grande número de conjuntos de dados ativos.

## <a name="workloads-in-premium-capacity"></a>Cargas de trabalho na capacidade Premium

Considere uma carga de trabalho no Power BI como um dos muitos serviços que você pode expor aos usuários. Por padrão, as capacidades para o **Power BI Premium** e o **Power BI Embedded** são compatíveis apenas com a carga de trabalho associada à execução de consultas no Power BI na nuvem.

Agora oferecemos compatibilidade em versão prévia para duas cargas de trabalho adicionais: **Relatórios paginados** e **Fluxos de dados**. Habilite essas cargas de trabalho no Portal de Administração do Power BI ou por meio da API REST do Power BI. Você também define a memória máxima que cada carga de trabalho pode consumir, a fim de controlar como as diferentes cargas de trabalho afetam umas às outras. Para saber mais, confira [Configurar cargas de trabalho](service-admin-premium-manage.md#configure-workloads).

### <a name="default-memory-settings"></a>Configurações de memória padrão

As tabelas a seguir mostram os valores de memória padrão e mínimo, com base em diferentes [nós de capacidade](#premium-capacity-nodes) disponíveis. A memória é dinamicamente alocada para fluxos de dados, mas é alocada estaticamente para relatórios paginados. Confira mais informações na próxima seção [Considerações sobre relatórios paginados](#considerations-for-paginated-reports).

#### <a name="microsoft-office-skus-for-software-as-a-service-saas-scenarios"></a>SKUs do Microsoft Office para cenários SaaS (Software como Serviço)

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Relatórios paginados | N/A | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% | Padrão de 20%; mínimo de 2,5% |
| Fluxos de dados | Padrão de 20%; mínimo de 8%  | Padrão de 20%; mínimo de 4%  | Padrão de 20%; mínimo de 2% | Padrão de 20%; mínimo de 1%  |
| | | | | |

#### <a name="microsoft-azure-skus-for-platform-as-a-service-paas-scenarios"></a>SKUs do Microsoft Azure para cenários PaaS (Plataforma como Serviço)

|                  | A1                       | A2                       | A3                      | A4                       | A5                      | A6                        |
|-------------------|--------------------------|--------------------------|-------------------------|--------------------------|-------------------------|---------------------------|
| Relatórios paginados | N/A                      | Não aplicável                      | N/A                     | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% | Padrão de 20%; mínimo de 2,5% |
| Fluxos de dados         | Padrão de 27%; mínimo de 27% | Padrão de 20%; mínimo de 16% | Padrão de 20%; mínimo de 8% | Padrão de 20%; mínimo de 4%  | Padrão de 20%; mínimo de 2% | Padrão de 20%; mínimo de 1%   |

### <a name="considerations-for-paginated-reports"></a>Considerações sobre relatórios paginados

Se você usa a carga de trabalho de relatórios paginados, tenha os seguintes pontos em mente.

* **Alocação de memória em relatórios paginados**: os relatórios paginados permitem que você execute seu próprio código ao renderizar um relatório (como alterar dinamicamente a cor do texto com base no conteúdo). Considerando esse fato, protegemos capacidade do Power BI Premium executando relatórios paginados em um espaço definido dentro da capacidade. Atribuímos a esse espaço a memória máxima que você especifica, esteja a carga de trabalho ativa ou não. Se você usar relatórios ou fluxos de dados do Power BI na mesma capacidade, defina uma memória baixa o suficiente para relatórios paginados de modo que ela não afete negativamente outras cargas de trabalho.

* **Relatórios paginados indisponíveis**: em circunstâncias raras, a carga de trabalho de relatórios paginados pode se tornar indisponível. Nesse caso, a carga de trabalho mostra o estado de erro no Portal de Administração, e os usuários veem tempos limite para renderização de relatório. Para atenuar esse problema, desabilite a carga de trabalho e habilite-a novamente.

## <a name="power-bi-report-server"></a>Servidor de Relatórios do Power BI

O Power BI Premium também inclui a capacidade de execução local do Servidor de Relatórios do Power BI na sua organização. Para saber mais, consulte [Get started with Power BI Report Server](report-server/get-started.md) (Introdução ao Servidor de Relatórios do Power BI).

## <a name="next-steps"></a>Próximas etapas

[Perguntas frequentes sobre o Power BI Premium](service-premium-faq.md)
[Como comprar o Power BI Premium](service-admin-premium-purchase.md)
[Gerenciando o Power BI Premium](service-admin-premium-manage.md)
[White paper do Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
[White paper de como planejar uma implantação do Power BI Enterprise](https://aka.ms/pbienterprisedeploy)
[Como administrar o Power BI em sua organização](service-admin-administering-power-bi-in-your-organization.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
