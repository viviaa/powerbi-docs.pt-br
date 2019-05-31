---
title: Usar um endereço de email alternativo
description: Usar um endereço de email alternativo
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 88432f55fc8cfeefa07b66ea68437bbb23f12531
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906635"
---
# <a name="use-an-alternate-email-address"></a>Usar um endereço de email alternativo

Quando você se inscreve no Power BI, pode fornecer um endereço de email. Por padrão, o Power BI usa esse endereço para enviar atualizações sobre a atividade no serviço. Por exemplo, quando alguém envia um convite de compartilhamento, ele vai para esse endereço.

Em alguns casos, talvez você queira que esses emails sejam entregues em um endereço de email alternativo, e não naquele com o qual você se inscreveu. Este artigo explica como especificar um endereço alternativo no Office 365 e no PowerShell. O artigo também explica como o Azure Active Directory (Azure AD) resolve um endereço de email.

> [!NOTE]
> Especificar um endereço alternativo não afeta o endereço de email usado pelo Power BI para atualizações de serviço, boletins informativos e outras comunicações promocionais. Essas comunicações sempre são enviadas para o endereço de email usado quando você se inscreveu para o Power BI.

## <a name="use-office-365"></a>Usar o Office 365

Para especificar um endereço alternativo no Office 365, execute estas etapas.

1. Abra a [página de informações pessoais do Office 365](https://portal.office.com/account/#personalinfo). Se o aplicativo solicitará que você, entre com o endereço de email e senha que você usa para o Power BI.

1. No menu à esquerda, selecione **Informações pessoais**.

1. Na seção **Detalhes de contato**, selecione **Editar**.

    Se você não pode editar seus detalhes, isso significa que seu administrador do Office 365 gerencia seu endereço de email. Entre em contato com seu administrador para atualizar seu endereço de email.

    ![Detalhes do contato](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. No **email alternativo** , insira o endereço de email que você gostaria de Office 365 para usar para atualizações do Power BI.

## <a name="use-powershell"></a>Usar o PowerShell

Para especificar um endereço alternativo no PowerShell, use o comando [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/).

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>Resolução de endereço de email no Azure AD

Para capturar um Azure AD o token de inserção para o Power BI, você pode usar um dos três tipos diferentes de endereços de email:

* O endereço de email principal associado a uma conta de usuário do Azure AD

* O endereço de email UPN (UserPrincipalName)

* O atributo de matriz *outro endereço de email*

O Power BI seleciona qual email usar com base na seguinte sequência:

1. Se o atributo de email no objeto de usuário do Azure AD estiver presente, o Power BI usará esse atributo de email para o endereço de email.

1. Se o email UPN *não* for um endereço de email do domínio **\*.onmicrosoft.com** (as informações após o símbolo "\@"), o Power BI usará esse atributo de email para o endereço de email.

1. Se o *outro endereço de email* atributo de matriz no objeto de usuário do Azure AD estiver presente, então o Power BI usa o primeiro email dessa lista (pois pode haver uma lista de emails nesse atributo).

1. Se nenhuma das condições acima estiver presente, o Power BI usa o endereço UPN.

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)