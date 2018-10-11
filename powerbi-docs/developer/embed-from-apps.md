---
title: Inserir relatórios ou dashboards de aplicativos
description: Aprenda como integrar, ou inserir, um relatório ou dashboard de um aplicativo do Power BI e não de um espaço de trabalho do aplicativo.
author: markingmyname
ms.author: maghan
ms.date: 07/13/2018
ms.topic: how-to
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 53803c77dec8eb35c10db7f19a82f58144f88414
ms.sourcegitcommit: b45134887a452f816a97e384f4333db9e1d8b798
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47237975"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Inserir relatórios ou dashboards de aplicativos

No Power BI, você pode criar aplicativos para reunir relatórios e dashboards relacionados, tudo em um só lugar. Em seguida, você os publica para grandes grupos de pessoas em sua organização. O uso desses aplicativos é relevante quando todos os usuários são usuários do Power BI. Portanto, você pode compartilhar conteúdo com eles por meio de aplicativos do Power BI. Este artigo apresenta algumas etapas rápidas para inserir conteúdo de um aplicativo do Power BI publicado em um aplicativo de terceiros.

## <a name="grab-a-report-embedurl-for-embedding"></a>Pegar uma embedURL do relatório para inserção

1. Criar uma instância do aplicativo em um workspace do usuário, **Meu Workspace**. Compartilhe consigo mesmo ou conduza outro usuário a passar por esse fluxo.

2. Abra o relatório desejado no serviço do Power BI.

3. Acesse **Arquivo** > **Inserir no SharePoint Online** e pegue embedURL do relatório de lá. Ele é mostrado no seguinte instantâneo. Outra opção é chamar a API REST GetReports/GetReport e extrair o campo embedURL do relatório correspondente da resposta. A chamada REST não deve ter um identificador de workspace como parte da URL, uma vez que o aplicativo foi instanciado no workspace do usuário.

4. Use o embedURL recuperado na etapa 3 com o SDK do JavaScript.

    ![Inserir de aplicativos](media/embed-from-apps/embed-from-app.png)

## <a name="grab-a-dashboard-embedurl-for-embedding"></a>Pegar uma embedURL de dashboard para inserção

1. Criar uma instância do aplicativo em um workspace do usuário, **Meu Workspace**. Compartilhe consigo mesmo ou conduza outro usuário a passar por esse fluxo.

2. Chame a API REST de GetDashboards e extraia o campo embedURL do dashboard correspondente da resposta. A chamada REST não deve ter um identificador de workspace como parte da URL, uma vez que o aplicativo foi instanciado no espaço de workspace.

3. Use o embedURL recuperado na etapa 2 com o SDK do JavaScript.

## <a name="next-steps"></a>Próximas etapas

Examine como inserir de workspaces do aplicativo para clientes de terceiros e para a organização:

> [!div class="nextstepaction"]
>[Inserir para clientes de terceiros](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Inserir para a organização](embed-sample-for-your-organization.md)