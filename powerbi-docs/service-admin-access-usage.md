---
title: Encontrar usuários do Power BI que entraram
description: Se você for um administrador de locatário e quiser ver quem entrou no Power BI, você pode usar os relatórios de acesso e uso do Azure Active Directory para ganhar visibilidade.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: e513607dd89aee15f10145cf62bd461621cc12c0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906738"
---
# <a name="find-power-bi-users-that-have-signed-in"></a>Encontrar usuários do Power BI que entraram

Se você for um administrador de locatário e quiser ver quem entrou no Power BI, use o [relatórios de acesso e uso do Azure Active Directory](/azure/active-directory/reports-monitoring/concept-sign-ins) ganhe visibilidade.

<iframe width="640" height="360" src="https://www.youtube.com/embed/1AVgh9w9VM8?showinfo=0" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> O **entradas** relatório fornece informações úteis, mas ela não identifica o tipo de licença que cada usuário tem. Use o centro de administração do Microsoft 365 para ver as licenças.

## <a name="requirements"></a>Requisitos

Qualquer usuário (inclusive os não administradores) pode ver um relatório de suas próprias entradas, mas você deve atender aos requisitos a seguir para ver um relatório para todos os usuários.

* Seu locatário deve ter uma licença do Azure Active Directory Premium associada a ele.

* Você deve ter uma das seguintes funções: Administrador Global, Administrador de Segurança ou Leitor de Segurança.

## <a name="use-the-azure-portal-to-view-sign-ins"></a>Usar o Portal do Azure para exibir entradas

Para exibir a atividade de entrada, siga estas etapas.

1. No **Portal do Azure**, selecione **Azure Active Directory**.

1. Em **Monitoramento**, selecione **Entradas**.
   
    ![Captura de tela da interface do usuário do Azure com as opções do Azure Active Directory e entradas realçadas.](media/service-admin-access-usage/azure-portal-sign-ins.png)

1. Filtre o aplicativo segundo **Microsoft Power BI** ou **Power BI Gateway** e selecione **Aplicar**.

    **Microsoft Power BI** filtros de atividade de entrada relacionados ao serviço, enquanto **Power BI Gateway** filtros de atividade de entrada específico para o gateway de dados local.
   
    ![Captura de tela do filtro entradas com o campo de aplicativos realçado.](media/service-admin-access-usage/sign-in-filter.png)

## <a name="export-the-data"></a>Exportar os dados

Você pode [baixar um relatório de entrada](/azure/active-directory/reports-monitoring/quickstart-download-sign-in-report) em qualquer um dos dois formatos: um arquivo CSV ou um arquivo JSON.

![Captura de tela do botão de download.](media/service-admin-access-usage/download-sign-in-data-csv.png)

Na parte superior a **entradas** relatório, selecione **baixar** e, em seguida, selecione uma das seguintes opções:

* **CSV** para baixar um arquivo CSV para os dados filtrados no momento.

* **JSON** para baixar um arquivo JSON para os dados filtrados no momento.

## <a name="data-retention"></a>Retenção de dados

Dados relacionados às entradas estão disponíveis por até 30 dias. Para obter mais informações, consulte [políticas de retenção de relatório do Azure Active Directory](/azure/active-directory/reports-monitoring/reference-reports-data-retention).

## <a name="next-steps"></a>Próximas etapas

[Usando a auditoria em sua organização](service-admin-auditing.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)