---
title: Inserção com o Power BI
description: O Power BI oferece APIs para inserir seus dashboards e relatórios em aplicativos.
author: markingmyname
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-developer
ms.topic: overview
ms.date: 07/31/2018
ms.author: maghan
ms.openlocfilehash: 8f200450e5359124ffcc3447c68c6bd755c57896
ms.sourcegitcommit: fecea174721d0eb4e1927c1116d2604a822e4090
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39359853"
---
# <a name="embedding-with-power-bi"></a>Inserção com o Power BI
O serviço do Power BI (SaaS) e o serviço do Power BI Embedded no Azure (PaaS) têm APIs para inserir seus painéis e seus relatórios. Isso significa que você tem um conjunto consistente de recursos e o acesso aos recursos mais recentes do Power BI, tais como painéis, gateways e espaços de trabalho de aplicativo, ao inserir seu conteúdo.

É possível acessar a [Ferramenta de experiência de integração](https://aka.ms/embedsetup) para começar rapidamente e baixar um aplicativo de exemplo.

Escolha a solução certa para você:

* A [inserção para a organização](embedding.md#embedding-for-your-organization) permite que você estenda o serviço do Power BI. Execute a solução [Inserir para a organização](https://aka.ms/embedsetup/UserOwnsData).
* A [inserção para clientes](embedding.md#embedding-for-your-customers) fornece a capacidade de inserir os dashboards e relatórios para usuários que não têm uma conta do Power BI. Execute a solução [Inserir para clientes](https://aka.ms/embedsetup/AppOwnsData).

![Exemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="using-apis"></a>Usando APIs
Há dois cenários principais ao inserir conteúdo do Power BI.  Inserir para usuários em sua organização (que têm a licença para o Power BI) e inserir para seus usuários e clientes sem que estes precisem ter licenças do Power BI. A API REST do Power BI permite os dois cenários.

Para clientes e usuários sem licenças do Power BI, você pode inserir painéis e relatórios em seu aplicativo personalizado, usando a mesma API para atender a organização ou os clientes. Os clientes veem os dados que são gerenciados pelo aplicativo. Além disso, para usuários do Power BI em sua organização, eles possuem as opções adicionais para exibir *seus dados* diretamente no Power BI ou no contexto do aplicativo inserido. Você pode se beneficiar das APIs REST e do JavaScript para suas necessidades de inserção.

Para exibir uma amostra de como a inserção funciona, consulte a [amostra de inserção do JavaScript](https://microsoft.github.io/PowerBI-JavaScript/demo/).

## <a name="embedding-for-your-organization"></a>Inserção para a organização
A **inserção para a organização** permite que você estenda o serviço do Power BI. Isso exige que os usuários do seu aplicativo façam logon no serviço do Power BI quando desejarem exibir os seus respectivos conteúdos. Depois que alguém na organização conectar-se, este usuário só terá acesso aos painéis e relatórios dos quais ele é proprietário ou que foram compartilhados com ele no serviço do Power BI.

*Exemplos de inserção para a organização incluem o aplicativo Web interno, a Web Part do SharePoint Online e a [integração do Microsoft Teams (você tem direitos de administrador)](https://powerbi.microsoft.com/en-us/blog/power-bi-teams-up-with-microsoft-teams/).*

Para inserir para a organização, consulte o seguinte:

* [Integrar um relatório em um aplicativo](embed-sample-for-your-organization.md)

Recursos de autoatendimento, como editar, salvar e muito mais, estão disponíveis por meio de [API JavaScript](https://github.com/Microsoft/PowerBI-JavaScript) ao inserir para usuários do Power BI.

Você pode examinar a [Ferramenta de experiência de integração para inserção para a organização](https://aka.ms/embedsetup/UserOwnsData) para iniciar rapidamente e baixar um aplicativo de exemplo que explica como integrar um relatório para a organização.

## <a name="embedding-for-your-customers"></a>Inserção para os clientes

A **inserção para clientes** fornece a capacidade de inserir os dashboards e relatórios para usuários que não têm uma conta do Power BI. Os clientes não precisam saber nada sobre o Power BI. Pelo menos uma conta do Power BI Pro é necessária para criar um aplicativo inserido. Essa conta do Power BI Pro atua como uma conta mestre do seu aplicativo. Pense nisso como uma conta de proxy. A conta do Power BI Pro também permite a geração de tokens de inserção que fornecem acesso a painéis e relatórios no serviço do Power BI que são de propriedade/gerenciados pelo seu aplicativo.

O [Power BI Embedded](azure-pbie-what-is-power-bi-embedded.md) oferece aos ISVs (fornecedores independentes de software) e aos desenvolvedores a capacidade de inserção para que os clientes adicionem rapidamente relatórios, dashboards e elementos visuais impressionantes nos aplicativos por meio de um modelo medido em horas com base em capacidade.

![Fluxo de inserção ao inserir para os clientes](media/embedding/powerbi-embed-flow.png)

O Power BI Embedded fornece benefícios para um ISV, seus desenvolvedores e clientes. Por exemplo, um ISV pode começar a criar elementos visuais gratuitamente com o Power BI Desktop. Os ISVs podem obter tempo de lançamento mais rápido minimizando os esforços de desenvolvimento de análise visual e se destacando em relação à concorrência com experiências de dados diferenciadas. Os ISVs também podem optar por cobrar uma taxa para o valor adicional criado com a análise integrada.

Os desenvolvedores podem passar o tempo concentrados na criação da competência principal do seu aplicativo em vez de gastar tempo desenvolvendo elementos visuais e análise. Os desenvolvedores podem atender rapidamente as demandas de dashboard e relatório do cliente e podem inserir facilmente com APIs e SDKs totalmente documentadas. Por fim, ao habilitar a exploração de dados fácil de navegar em seus aplicativos, os ISVs permitem que seus clientes tomem decisões rápidas e direcionadas a dados no contexto e com confiança em qualquer dispositivo.

> [!IMPORTANT]
> Embora a inserção seja dependente do serviço do Power BI, não há uma dependência do Power BI para os clientes. Eles não precisa inscrever-se no Power BI para exibir o conteúdo inserido em seu aplicativo.

Quando você está pronto para passar para a produção, sua atribuição de espaço de trabalho de aplicativo para uma capacidade dedicada é necessária. O Power BI Embedded, no Microsoft Azure, oferece recursos dedicados para usar com seus aplicativos.

Para obter detalhes sobre como inserir, consulte [Como inserir seus dashboards, relatórios e blocos do Power BI](embed-sample-for-customers.md).

Você pode examinar a [Ferramenta de experiência de integração](https://aka.ms/embedsetup/AppOwnsData) para iniciar rapidamente e baixar um aplicativo de exemplo que explica como integrar um relatório no aplicativo.

Se você estiver usando o serviço de Coleção de Espaços de Trabalho do Power BI no Azure, consulte [Migrar o conteúdo do serviço de Coleção de Espaços de Trabalho do Power BI do Azure](migrate-from-powerbi-embedded.md) para obter informações sobre como migrar o conteúdo.

## <a name="next-steps"></a>Próximas etapas
Agora você pode tentar inserir o conteúdo do Power BI em um aplicativo ou tentar inserir o conteúdo do Power BI para seus clientes.

> [!div class="nextstepaction"]
> [O que é o Power BI Embedded?](azure-pbie-what-is-power-bi-embedded.md)

> [!div class="nextstepaction"]
> [Inserir para a organização](embed-sample-for-your-organization.md)

> [!div class="nextstepaction"]
>[Inserir para seus clientes](embed-sample-for-customers.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)