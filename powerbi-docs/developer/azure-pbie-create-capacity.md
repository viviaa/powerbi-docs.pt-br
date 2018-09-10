---
title: Criar uma capacidade do Power BI Embedded no portal do Azure | Microsoft Docs
description: Este artigo explica como criar uma capacidade do Power BI Embedded no Microsoft Azure.
author: markingmyname
manager: kfile
ms.author: maghan
ms.service: power-bi-embedded
ms.component: ''
ms.devlang: csharp, javascript
ms.topic: conceptual
ms.reviewer: ''
ms.date: 07/31/2018
ms.openlocfilehash: f364bb725c492c1bffd2493c1e2a48ee8c442a9e
ms.sourcegitcommit: 6be2c54f2703f307457360baef32aee16f338067
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43300036"
---
# <a name="create-power-bi-embedded-capacity-in-the-azure-portal"></a>Criar uma capacidade do Power BI Embedded no portal do Azure

Este artigo explica como criar uma capacidade do Power BI Embedded no Microsoft Azure. O Power BI Embedded simplifica as funcionalidades do Power BI, ajudando você a adicionar rapidamente visuais, relatórios e dashboards impressionantes aos aplicativos.

Se você não tiver uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/) antes de começar.

> [!VIDEO https://www.youtube.com/embed/aXrvFfg_iSk]

## <a name="before-you-begin"></a>Antes de começar

Para concluir este início rápido, você precisa:

* **Assinatura do Azure:** visite a [Avaliação Gratuita do Azure](https://azure.microsoft.com/free/) para criar uma conta.
* **Azure Active Directory:** sua assinatura precisa ser associada a um locatário do AAD (Azure Active Directory). Além disso, ***você precisa estar conectado ao Azure com uma conta nesse locatário***. Não há suporte para contas da Microsoft. Para obter mais informações, confira [Autenticação e permissões de usuário](https://docs.microsoft.com/azure/analysis-services/analysis-services-manage-users).
* **Locatário do Power BI:** pelo menos uma conta no seu locatário do AAD precisa se inscrever no Power BI.
* **Grupo de recursos:** use um grupo de recursos que você já tem ou [crie um](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).

## <a name="create-a-capacity"></a>Criar uma capacidade

1. Entre no [Portal do Azure](https://portal.azure.com/).

2. Selecione **Criar um recurso** > **Dados + análise**.

3. Na caixa de pesquisa, procure *Power BI Embedded*.

4. No Power BI Embedded, selecione **Criar**.

5. Preencha as informações necessárias e, em seguida, selecione **Criar**.

    ![Campos a serem preenchidos para criar uma nova capacidade](media/azure-pbie-create-capacity/azure-portal-create-power-bi-embedded.png)

    |Configuração |Descrição |
    |---------|---------|
    |**Nome do recurso**|Um nome para identificar a capacidade. O nome do recurso é exibido no portal do Azure e também no portal de administração do Power BI.|
    |**Assinatura**|A assinatura na qual você deseja criar a capacidade.|
    |**Grupo de recursos**|O grupo de recursos que contém essa nova capacidade. Escolha um grupo de recursos existente ou crie outro. Para obter mais informações, confira [Visão geral do Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview).|
    |**Administrador de capacidade do Power BI**|Os administradores de capacidade do Power BI podem exibir a capacidade no portal de administração do Power BI e conceder permissões de atribuição a outros usuários. Por padrão, o administrador de capacidade é a sua conta. O administrador de capacidade precisa pertencer ao locatário do Power BI.|
    |**Local**|O local em que o Power BI está hospedado para seu locatário. O local padrão é sua região de residência, mas você pode alterar o local usando [Opções de Multi-Geo](embedded-multi-geo.md).
    |**Tipo de preço**|Selecione o SKU (contagem de núcleos virtuais e tamanho da memória) que atende às suas necessidades.  Para obter detalhes, confira [Preços do Power BI Embedded](https://azure.microsoft.com/pricing/details/power-bi-embedded/)|

6. Selecione **Criar**.

A criação costuma levar menos de um minuto. Geralmente, ela leva apenas alguns segundos. Ao selecionar **Fixar no dashboard**, você poderá navegar até o dashboard para ver a nova capacidade. Como alternativa, você pode navegar para **Todos os serviços** > **Power BI Embedded** para ver se sua capacidade está pronta.

![Dashboard do portal do Azure com a capacidade do Power BI Embedded](media/azure-pbie-create-capacity/azure-portal-dashboard.png)

## <a name="next-steps"></a>Próximas etapas

Para usar a nova capacidade do Power BI Embedded, navegue até o portal de administração do Power BI para atribuir espaços de trabalho. Para obter mais informações, confira [Gerenciar capacidades no Power BI Premium e no Power BI Embedded](https://powerbi.microsoft.com/documentation/powerbi-admin-premium-manage/).

Se você não precisa usar essa capacidade, é possível pausá-la para interromper a cobrança. Para obter mais informações, confira [Pausar e iniciar a capacidade do Power BI Embedded no portal do Azure](azure-pbie-pause-start.md).

Para começar a inserir conteúdo do Power BI em seu aplicativo, confira [Como inserir dashboards, relatórios e blocos do Power BI](https://powerbi.microsoft.com/documentation/powerbi-developer-embedding-content/).

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)