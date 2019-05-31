---
title: Instalação automática aplicativos do Power BI durante a inserção para sua organização
description: Saiba como automaticamente os aplicativos de instalação do Power BI durante a inserção para sua organização.
ms.subservice: powerbi-developer
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.topic: how-to
ms.service: powerbi
ms.custom: ''
ms.date: 04/16/2019
ms.openlocfilehash: bb9ba5531c2a23f15ccbf98261e246ab7080aecb
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61376186"
---
# <a name="auto-install-power-bi-apps-when-embedding-for-your-organization"></a>Instalar automaticamente aplicativos do Power BI durante a inserção para sua organização

Para inserir o conteúdo de um aplicativo, o usuário que está inserindo deve ter [acesso ao aplicativo](../service-create-distribute-apps.md). Se o aplicativo é instalado para o usuário, em seguida, inserindo funciona sem problemas. Para obter mais informações, consulte [inserir relatórios ou painéis do aplicativo](embed-from-apps.md). É possível definir no PowerBI.com que todos os aplicativos podem ser [instalados automaticamente](https://powerbi.microsoft.com/blog/automatically-install-apps/). No entanto, essa ação é feita no nível do locatário e se aplica a todos os aplicativos.

## <a name="auto-install-app-on-embedding"></a>Aplicativo de instalação automática na inserção

Se um usuário tem acesso a um aplicativo, mas o aplicativo não estiver instalado, e, em seguida, inserindo falhar. Para que você possa evitar essas falhas durante a inserção de um aplicativo, você pode permitir que a instalação automática do aplicativo após a inserção. Essa ação significa que, se o aplicativo que o usuário tentar inserir não estiver instalado, ele será instalado automaticamente para você. Portanto, o conteúdo que você deseja obtém inserido imediatamente, resultando em uma experiência positiva do usuário.

## <a name="embed-for-power-bi-users-user-owns-data"></a>Inserir para usuários do Power BI (o usuário possui dados)

Para permitir que a instalação automática de aplicativos para seus usuários, você precisa dar ao seu aplicativo a permissão 'Criar conteúdo' quando [Registrando seu aplicativo](register-app.md#register-with-the-power-bi-application-registration-tool), ou adicioná-lo se você já registrou seu aplicativo.

![Registrar aplicativo cria conteúdo](media/embed-auto-install-app/register-app-create-content.png)

Em seguida, você precisa fornecer a ID do aplicativo na URL de inserção. Para fornecer a ID do aplicativo, o criador do aplicativo primeiro precisa instalar o aplicativo, em seguida, usar um com suporte [API Rest do Power BI](https://docs.microsoft.com/rest/api/power-bi/) chamadas - [obter relatórios](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) ou [obter painéis](https://docs.microsoft.com/rest/api/power-bi/dashboards/getdashboards). Em seguida, o criador do aplicativo precisa levar a Url de inserção da resposta da API REST. A ID do aplicativo aparece na URL se o conteúdo é proveniente de um aplicativo.  Depois de ter a URL de inserção, você pode usá-lo incorporar regularmente.

## <a name="secure-embed"></a>Proteger incorporar

Para usar a instalação automática de aplicativos, o criador do aplicativo precisa primeiro instalar o aplicativo e em seguida, vá para o aplicativo no PowerBI.com, navegue até o relatório e obter o link de maneira usual. Todos os outros usuários com acesso ao aplicativo que pode usar o link podem inserir o relatório.

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Você só pode inserir relatórios e painéis para esse cenário.

* Esse recurso atualmente não há suporte para o aplicativo possui dados e cenários de inserção do SharePoint.