---
title: Análise integrada com o Power BI
description: O Power BI oferece APIs para usar análises integradas para seus dashboards e relatórios nos aplicativos. Saiba mais sobre a integração com o Power BI em ambientes de PaaS e SaaS usando software de análise integrada, ferramentas de análise integrada ou ferramentas de business intelligence inseridas.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: overview
helpviewer_keywords:
- embedded analytics
- embedding
- Power BI embedding
- app owns data
- user owns data
- Power BI APIs
ms.custom: seodec18
ms.date: 05/15/2019
ms.openlocfilehash: a212691f2af877e3b86e021a4f48644f4fa6e8e3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051058"
---
# <a name="embedded-analytics-with-power-bi"></a>Análise integrada com o Power BI

O serviço do Power BI (SaaS) e o serviço do Power BI Embedded no Azure (PaaS) têm APIs para inserir seus painéis e seus relatórios. Ao inserir conteúdo, isso fornece acesso aos recursos mais recentes do Power BI como dashboards, gateways e espaços de trabalho do aplicativo.

É possível acessar a [Ferramenta de configuração de inserção](https://aka.ms/embedsetup) para começar rapidamente e baixar um aplicativo de exemplo.

Escolha a solução certa para você:

* A [inserção para a organização](embedding.md#embedding-for-your-organization) permite que você estenda o serviço do Power BI. Para fazer isso, implementar o [inserção para a sua organização](https://aka.ms/embedsetup/UserOwnsData) solução.
* [Inserindo para os clientes](embedding.md#embedding-for-your-customers) permite que você insira dashboards e relatórios para usuários que não têm uma conta do Power BI. Para fazer isso, implementar o [inserção para seus clientes](https://aka.ms/embedsetup/AppOwnsData) solução.

![Exemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="use-apis"></a>Use as APIs

Há dois cenários principais para inserir conteúdo do Power BI:
- Inserindo para usuários da sua organização (que têm licenças do Power BI). 
 
- Inserção para seus usuários e clientes que não precisam ter licenças do Power BI. 

O [API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/) permite que os dois cenários.

Para clientes e usuários sem licenças do Power BI, você pode inserir painéis e relatórios em seu aplicativo personalizado, usando a mesma API para atender a organização ou os clientes. Os clientes veem os dados de aplicativo gerenciado. Além disso, os usuários da organização do Power BI tem opções adicionais para exibir *seus dados* diretamente no Power BI ou no contexto do aplicativo incorporado. Você pode se beneficiar das APIs REST e do JavaScript para suas necessidades de inserção.

Para entender como a inserção funciona, consulte o [exemplo inserido de JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inserção para a organização

A **inserção para a organização** permite que você estenda o serviço do Power BI. Essa inserção requer a entrada de usuários do seu aplicativo no serviço do Power BI para exibir o conteúdo. Depois que alguém na organização se conectar, esse usuário só terá acesso aos dashboards e relatórios dos quais ele é proprietário ou que alguém compartilhou com ele no serviço do Power BI.

Exemplos de incorporação de organização incluem aplicativos internos, como [SharePoint Online](https://powerbi.microsoft.com/blog/integrate-power-bi-reports-in-sharepoint-online/), [(você deve ter direitos de administrador) de integração do Microsoft Teams](https://powerbi.microsoft.com/blog/power-bi-teams-up-with-microsoft-teams/), e [doMicrosoftDynamics](https://docs.microsoft.com/dynamics365/customer-engagement/basics/add-edit-power-bi-visualizations-dashboard).

Para inserir para a sua organização, consulte [Tutorial: Inserir conteúdo do Power BI em um aplicativo para sua organização](embed-sample-for-your-organization.md).

Recursos de autoatendimento, como editar, salvar e muito mais, estão disponíveis por meio de [API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) ao inserir para usuários do Power BI.

Você pode percorrer os [ferramenta de configuração de incorporação](https://aka.ms/embedsetup/UserOwnsData) para começar e baixe um aplicativo de exemplo que orienta você durante a integração de um relatório para a sua organização.

## <a name="embedding-for-your-customers"></a>Inserção para os clientes

**Inserindo para os clientes** permite que você inserir dashboards e relatórios para usuários que não têm uma conta do Power BI. Essa inserção é também conhecido como *Power BI Embedded*.

[Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) é um **Microsoft Azure** serviço que permite que desenvolvedores e fornecedores de software independentes (ISVs) rapidamente inserir elementos visuais, relatórios e painéis em um aplicativo. Esse processo de incorporação é feito por meio de um modelo medido por hora, com base em capacidade.

![Fluxo de inserção ao inserir para os clientes](media/embedding/powerbi-embed-flow.png)

O Power BI Embedded fornece benefícios para um ISV, seus desenvolvedores e clientes. Por exemplo, um ISV pode começar a criar elementos visuais gratuitamente com o Power BI Desktop. Minimizando os esforços de desenvolvimento analítico visual, os ISVs chegar ao mercado mais rapidamente e destaque-se da concorrência com experiências de dados diferentes. Os ISVs também podem optar por cobrar uma taxa para o valor adicional, que eles criam com análise inserida.

Com o Power BI Embedded, seus clientes não precisam saber nada sobre o Power BI. Você pode usar dois métodos diferentes para criar um aplicativo inserido:
- Conta do Power BI Pro 
- Entidade de serviço 

A conta do Power BI Pro atua como conta mestre do seu aplicativo (Imagine isso como uma conta proxy). Essa conta permite que você gerar tokens de inserção que fornecem acesso a relatórios e dashboards do Power BI do seu aplicativo.

[Entidade de serviço](embed-service-principal.md) pode inserir o conteúdo do Power BI em um aplicativo usando um token **somente de aplicativo**. Ele também permite que você gerar tokens de inserção que fornecem acesso a relatórios e dashboards do Power BI do seu aplicativo.

Os desenvolvedores que usam o Power BI Embedded podem gastar tempo concentrados na criação do aplicativo principal funcionalidade em vez de gastos tempo desenvolvendo os objetos visuais e análise. Eles podem atender às demandas de dashboard e relatório de cliente e incorporar facilmente com SDKs e APIs totalmente documentadas rapidamente. Ao habilitar a exploração de dados fácil de navegar em aplicativos, os ISVs permitem que seus clientes tomem decisões rápidas e direcionadas a dados no contexto em qualquer dispositivo.

> [!IMPORTANT]
> Enquanto incorporação exige que o serviço do Power BI, os seus clientes não precisam ter uma conta do Power BI para exibir o conteúdo inserido do seu aplicativo. 

Quando você estiver pronto para passar para a produção, seu espaço de trabalho do aplicativo deverá ser atribuído a uma capacidade dedicada. O Power BI Embedded no Microsoft Azure oferece [capacidades dedicadas](azure-pbie-create-capacity.md) a serem usadas com seus aplicativos.

Para inserir os detalhes, consulte [como inserir conteúdo do Power BI](embed-sample-for-customers.md).

## <a name="next-steps"></a>Próximas etapas

Agora você pode tentar inserir o conteúdo do Power BI em um aplicativo ou tentar inserir o conteúdo do Power BI para seus clientes.

> [!div class="nextstepaction"]
> [Inserir para a organização](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
> [O que é o Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
>[Inserir para seus clientes](embed-sample-for-customers.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
