---
title: Entender a RLS (segurança em nível de linha) com o Power BI Desktop
description: Como configurar a segurança em nível de linha de conjuntos de dados importados e o DirectQuery no Power BI Desktop.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/03/2018
LocalizationGroup: Create reports
ms.openlocfilehash: 7cdbb86bafa2d5a532a4ceeeef9f28f5ba22e204
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54280138"
---
# <a name="row-level-security-rls-with-power-bi-desktop"></a>RLS (segurança em nível de linha) com o Power BI Desktop

A RLS (Segurança em Nível de Linha) com o Power BI Desktop restringe o acesso a dados para determinados usuários. Os filtros restringem os dados no nível da linha. É possível definir filtros nas funções.

Agora é possível configurar a RLS de modelos de dados importados para o Power BI com o Power BI Desktop. Você também pode configurar RLS em conjuntos de dados que estão usando DirectQuery, como o SQL Server. Anteriormente, você conseguia apenas implementar a RLS nos modelos do Analysis Services local fora do Power BI. Para as conexões dinâmicas do Analysis Services, configure a Segurança em nível de linha no modelo local. A opção de segurança não é exibida para conjuntos de dados com conexão dinâmica.

> [!IMPORTANT]
> Se você tiver definido funções e regras no serviço do Power BI, será necessário recriar essas funções no Power BI Desktop e publicar o relatório no serviço.

Saiba mais sobre as opções para a [RLS no serviço do Power BI](service-admin-rls.md).

[!INCLUDE [include-short-name](./includes/rls-desktop-define-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-desktop-view-as-roles.md)]

[!INCLUDE [include-short-name](./includes/rls-limitations.md)]

[!INCLUDE [include-short-name](./includes/rls-faq.md)]

## <a name="next-steps"></a>Próximas etapas

[RLS (segurança em nível de linha) com o serviço do Power BI](service-admin-rls.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)