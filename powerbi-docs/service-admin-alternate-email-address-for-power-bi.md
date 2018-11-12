---
title: Usando um endereço de email alternativo
description: Usando um endereço de email alternativo
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: mblythe
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 41b3a0b1032616045b854e4a4776ba82bffffe47
ms.sourcegitcommit: 0611860a896e636ceeb6e30ce85243bfd8e7b61d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50909401"
---
# <a name="using-an-alternate-email-address"></a>Usar um endereço de email alternativo

Quando você se inscreve no Power BI, pode fornecer um endereço de email. Por padrão, o Power BI usa esse endereço para enviar atualizações sobre a atividade no serviço. Por exemplo, quando alguém envia um convite de compartilhamento, ele vai para esse endereço.

Em alguns casos, talvez você queira que esses emails sejam entregues em um endereço de email alternativo, e não naquele com o qual você se inscreveu. Este artigo explica como especificar um endereço alternativo no Office 365 e no PowerShell. O artigo também explica como um endereço de email é resolvido no Azure Active Directory (Azure AD).

> [!NOTE]
> Especificar um endereço alternativo não afeta o endereço de email usado pelo Power BI para atualizações de serviço, boletins informativos e outras comunicações promocionais.  Essas comunicações são sempre enviadas ao endereço de email usado quando você se inscreveu no Power BI.

## <a name="use-office-365"></a>Usar o Office 365

Para especificar um endereço alternativo no Office 365, execute estas etapas.

1. Abra a [página de informações pessoais do Office 365](https://portal.office.com/account/#personalinfo). Se for solicitado, entre com o endereço de email e senha que você usa no Power BI.

1. No menu à esquerda, selecione **Informações pessoais**.

1. Na seção **Detalhes de contato**, selecione **Editar**.

    Se você não puder editar seus detalhes, significa que seu endereço de email é gerenciado pelo administrador do Office 365. Entre em contato com o administrador para atualizar seu endereço de email.

    ![Detalhes de contato](media/service-admin-alternate-email-address-for-power-bi/contact-details.png)

1. No campo **Email alternativo**, insira o endereço de email para o qual você gostaria que as atualizações do Power BI fossem enviadas.

## <a name="use-powershell"></a>Usar o PowerShell

Para especificar um endereço alternativo no PowerShell, use o comando [Set-AzureADUser](/powershell/module/azuread/set-azureaduser/).

```powershell
Set-AzureADUser -ObjectId john@contoso.com -OtherMails "otheremail@somedomain.com"
```

## <a name="email-address-resolution-in-azure-ad"></a>Resolução de endereço de email no Azure AD

Ao capturar um token de inserção do Azure AD para o Power BI, você pode usar três tipos diferentes de email:

* O endereço de email principal associado a uma conta do Azure AD do usuário

* O endereço de email UPN (UserPrincipalName)

* O atributo de matriz *outro endereço de email*

O Power BI seleciona qual email usar com base na seguinte sequência:

1. Se o atributo de email no objeto de usuário do Azure AD estiver presente, o Power BI usará esse atributo de email para o endereço de email.

1. Se o email UPN *não* for um endereço de email do domínio **\*.onmicrosoft.com** (as informações após o símbolo "@"), o Power BI usará esse atributo de email para o endereço de email.

1. Se o atributo de matriz *outro endereço de email* no objeto de usuário do Azure AD estiver presente, o primeiro email dessa lista será usado (já que poderá haver uma lista de endereços de email nesse atributo).

1. Se nenhuma das condições acima estiver presente, o endereço UPN será usado.

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

