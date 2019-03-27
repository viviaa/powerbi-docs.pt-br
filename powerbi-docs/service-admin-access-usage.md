---
title: Encontrar usuários do Power BI que entraram
description: Se for um administrador de locatários e quiser ver quem entrou no Power BI, você poderá usar os relatórios de acesso e uso do Azure Active Directory para ter essa visibilidade.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 26cf9b10d2a7bfffca151fe36cd45626487b6eef
ms.sourcegitcommit: 20ae9e9ffab6328f575833be691073de2061a64d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58383636"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Encontrar usuários do Power BI que entraram

Se for um administrador de locatários e quiser ver quem entrou no Power BI, use os [relatórios de acesso e uso do Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) para ter essa visibilidade.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> O relatório de atividade fornece informações úteis, mas não identifica o tipo de licença que cada usuário tem. Use o centro de administração do Microsoft 365 para ver as licenças.

## <a name="requirements"></a>Requisitos

Qualquer usuário (inclusive os não administradores) pode ver um relatório de suas próprias entradas, mas você deve atender aos requisitos a seguir para ver um relatório para todos os usuários.

* Seu locatário deve ter uma licença do Azure AD Premium associada a ele.

* Você deve ter uma das seguintes funções: Administrador Global, Administrador de Segurança ou Leitor de Segurança.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Usar o Portal do Azure para exibir entradas

Para exibir a atividade de entrada, siga estas etapas.

1. No **Portal do Azure**, selecione **Azure Active Directory**.

1. Em **Monitoramento**, selecione **Entradas**.
   
    ![Entradas do Azure AD](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtre o aplicativo segundo **Microsoft Power BI** ou **Power BI Gateway** e selecione **Aplicar**.

    O **Microsoft Power BI** filtra a atividade de entrada relacionada ao serviço, enquanto o **Power BI Gateway** filtra atividades de entrada específicas para o gateway de dados local.
   
    ![Filtrar entradas](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportar os dados

Você tem duas opções para exportar os dados de entrada: baixe um arquivo csv ou use o PowerShell. Na parte superior do relatório de entrada, selecione uma das seguintes opções:

* **Download** para baixar um arquivo csv com os dados filtrados no momento.

* **Script** para baixar um script do PowerShell para os dados filtrados no momento. Você pode atualizar o filtro no script conforme o necessário.

![Baixar arquivo csv ou script](media/service-admin-access-usage/download-sign-in-data-csv.png)

## <a name="data-retention"></a>Retenção de dados

Dados relacionados às entradas estão disponíveis por até 30 dias. Para obter mais informações, consulte [Políticas de retenção de relatórios do Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Próximas etapas

[Usando a auditoria em sua organização](service-admin-auditing.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

