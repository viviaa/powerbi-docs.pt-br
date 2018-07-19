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
ms.openlocfilehash: 2817ccb25fc9aa6d3e8150c776558366dcf0ccb6
ms.sourcegitcommit: 0c870a006e525447497e678484874a2f137b9abd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39088829"
---
# <a name="embed-reports-or-dashboards-from-apps"></a>Inserir relatórios ou dashboards de aplicativos

No **Power BI**, você pode criar aplicativos para reunir **dashboards** e **relatórios** relacionados em um só local e, em seguida, publicá-los para grandes grupos de pessoas em sua organização. O uso desses aplicativos é relevante quando todos os usuários são usuários do Power BI e, assim, você pode compartilhar conteúdo com eles usando os aplicativos do Power BI. Gostaríamos de compartilhar algumas etapas rápidas de como realizar a inserção de conteúdo de um aplicativo do Power BI publicado para um aplicativo de terceiros.

## <a name="how-to-grab-report-embed-url-for-embedding"></a>Como capturar a URL de inserção de relatório

1. Crie uma instância do aplicativo em um espaço de trabalho do usuário ('Meu Espaço de Trabalho') compartilhando com você mesmo ou orientando outro usuário para passar por esse fluxo.

2. Abra o relatório desejado no serviço do Power BI.

3. Acesse Arquivo -> Inserir no SharePoint Online e capture a URL de inserção de relatório nesse local (veja no instantâneo abaixo) ou chame a API REST GetReports/GetReport e extraia da resposta o campo embedURL do relatório correspondente (observe que a chamada à REST não deve ter um identificador de espaço de trabalho como parte da URL porque a instância do aplicativo foi criada no espaço de trabalho do usuário).

4. Use a URL de inserção recuperada na etapa 3 para ser usada com o SDK do JS.

    ![Inserir de Aplicativos](media/embed-from-apps/embed-from-app.png)

## <a name="how-to-grab-dashboard-embed-url-for-embedding"></a>Como capturar a URL de inserção de dashboard

1. Crie uma instância do aplicativo em um espaço de trabalho do usuário ('Meu Espaço de Trabalho') compartilhando com você mesmo ou orientando outro usuário para passar por esse fluxo.

2. Chame a API REST GetDashboards e extraia da resposta o campo embedURL do dashboard correspondente (observe que a chamada à REST não deve ter um identificador de espaço de trabalho como parte da URL porque a instância do aplicativo foi criada no espaço de trabalho do usuário).

3. Use a URL de inserção recuperada na etapa 4 para ser usada com o SDK do JS.

## <a name="next-steps"></a>Próximas etapas

Além disso, examine como inserir de espaços de trabalho do aplicativo para clientes de terceiros e para a organização.

> [!div class="nextstepaction"]
>[Inserir para clientes de terceiros](embed-sample-for-customers.md)

> [!div class="nextstepaction"]
>[Inserir para a organização](embed-sample-for-your-organization.md)