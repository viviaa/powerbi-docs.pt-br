---
title: Solucionando problemas de fonte de dados sem suporte para atualização
description: Solucionando problemas de fonte de dados sem suporte para atualização
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
ms.openlocfilehash: bd0ea66b8caf32e3244ed4e5eef648100fc5169e
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61187999"
---
# <a name="troubleshooting-unsupported-data-source-for-refresh"></a>Solucionando problemas de fonte de dados sem suporte para atualização
Você verá um erro ao tentar configurar um conjunto de dados para atualização agendada.

        You cannot schedule refresh for this dataset because it gets data from sources that currently don’t support refresh.

Isso acontece quando a fonte de dados usada no Power BI Desktop não dá suporte para atualização. Você precisará encontrar a fonte de dados que está usando e compará-la com a lista de fontes de dados com suporte em [Atualizar dados no Power BI](refresh-data.md). 

## <a name="find-the-data-source"></a>Encontrar a fonte de dados
Se você não tiver certeza de qual fonte de dados foi usada, você pode encontrar usando as seguintes etapas no Power BI Desktop.  

1. No Power BI Desktop, tenha certeza de que está no painel **Relatório** .  
   ![Painel de relatório de área de trabalho](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-report-pane.png)
2. Selecione **Editar Consultas** na barra da faixa de opções.  
   ![Editar consultas](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-edit-queries.png)
3. Selecione **Editor Avançado**.  
   ![Editor avançado](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-advanced-editor.png)
4. Anote o provedor listado para a fonte.  Neste exemplo, o provedor é Active Directory.  
   ![Provedor de fonte de dados](media/service-admin-troubleshoot-unsupported-data-source-for-refresh/tshoot-provider.png)
5. Compare o provedor com a lista de fontes de dados com suporte encontrada em [Atualizar dados no Power BI](refresh-data.md).  Você verá que o Active Directory não é uma fonte de dados com suporte para a atualização.  

## <a name="next-steps"></a>Próximas etapas
[Atualização de dados](refresh-data.md)  
[Gateway do Power BI – Pessoal](service-gateway-personal-mode.md)  
[On-premises data gateway (Gateway de dados local)](service-gateway-onprem.md)  
[Solução de problemas do gateway de dados local](service-gateway-onprem-tshoot.md)  
[Solução de problemas do Gateway do Power BI – Pessoal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

