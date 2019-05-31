---
title: Solucionando problemas da atualização agendada para Bancos de Dados SQL do Azure
description: Solucionando problemas em atualização agendada para bancos de dados SQL Azure no Power BI
author: mgblythe
manager: kfile
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2017
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 0c22d005044c0ebddc242eb35908e26689fee597
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61186873"
---
# <a name="troubleshooting-scheduled-refresh-for-azure-sql-databases-in-power-bi"></a>Solucionando problemas em atualização agendada para bancos de dados SQL Azure no Power BI
Para obter etapas detalhadas sobre como configurar a atualização agendada, certifique-se de ver [Atualizar dados no Power BI](refresh-data.md).

Ao configurar a atualização agendada para o banco de dados SQL Azure, se você receber um erro com o código de erro 400 durante a edição de credenciais, tente o seguinte para configurar a regra de firewall apropriada:

1. Entre no Portal de Gerenciamento do Azure
2. Vá ara o servidor SQL Azure no qual você está configurando a atualização
3. Ative “Serviços do Windows Azure” na seção de serviços permitidos

![Serviços permitidos do Azure](media/service-admin-troubleshooting-scheduled-refresh-azure-sql-databases/azurerefresh.png)  

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

