---
title: Distribuir conteúdos para usuários convidados externos com o Azure AD B2B
description: O Power BI integra-se ao Azure Active Directory Business-to-business (Azure AD B2B) para permitir distribuição segura do conteúdo do Power BI aos usuários convidados fora da organização.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: dee5c14d2ee714872409352b5e42d646e561c271
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507751"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuir o conteúdo do Power BI para usuários convidados externo com o Azure AD B2B

O Power BI integra-se ao Azure AD B2B (Azure Active Directory business-to-business) para permitir distribuição segura do conteúdo do Power BI aos usuários convidados fora da sua organização, enquanto ainda mantém controle sobre os dados internos.

## <a name="enable-access"></a>Habilitar acesso

Habilite o recurso de [configurações de exportação e compartilhamento](service-admin-portal.md#export-and-sharing-settings) no portal de administração do Power BI antes de convidar usuários.

## <a name="who-can-you-invite"></a>Que você pode convidar?

Você pode convidar usuários que usam qualquer endereço de email, incluindo contas pessoais como gmail.com, outlook.com e hotmail.com. No Azure AD B2B, esses endereços são chamados de *identidades sociais*.

## <a name="invite-guest-users"></a>Convidar usuários convidados

É necessário usar convites apenas na primeira vez que um usuário externo é convidado à sua organização. Há duas maneiras de convidar usuários: convites planejados e convites ad-hoc.

### <a name="planned-invites"></a>Convites planejados

Use um convite planejado se souber quais usuários vai convidar. Envie o convite pelo Portal do Azure ou pelo PowerShell. Você deve ser administrador de locatários para convidar pessoas.

Execute estas etapas para enviar um convite no Portal do Azure.

1. No [Portal do Azure](https://portal.azure.com), selecione **Azure Active Directory**.

1. Em **Gerenciar**, acesse **Usuários** > **Todos os usuários** > **Novo usuário convidado**.

    ![Portal do Azure AD – Novo usuário convidado](media/service-admin-azure-ad-b2b/azuread-portal-new-guest-user.png)

1. Insira um **endereço de email** e **mensagem pessoal**.

    ![Portal do Azure AD – mensagem convite ao novo usuário convidado](media/service-admin-azure-ad-b2b/azuread-portal-invite-message.png)

1. Selecione **Convidar**.

Para convidar mais de um usuário convidado, use o PowerShell. Para saber mais, confira [Amostras do código de colaboração e do PowerShell no Azure AD B2B](/azure/active-directory/b2b/code-samples/).

O usuário convidado precisa selecionar **Introdução** no convite que recebeu por email. O usuário convidado é adicionado ao locatário.

![Convite por email ao usuário convidado](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Convites ad hoc

Para fazer um convite em qualquer momento, adicione o usuário externo ao dashboard ou relatório por meio da interface do usuário de compartilhamento, ou em seu aplicativo, por meio da página de acesso. Aqui está um exemplo de como convidar um usuário externo para usar um aplicativo.

![Usuário externo adicionado à lista de acesso do aplicativo](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

O usuário convidado receberá um email indicando que o aplicativo foi compartilhado com ele.

![Email de aplicativo compartilhado com usuário convidado](media/service-admin-azure-ad-b2b/guest-user-invite-email2.png)

O usuário convidado deverá entrar com o endereço de email da organização. Será necessário aceitar o convite depois de entrar. Depois de entrar, o usuário convidado é redirecionado para o conteúdo do aplicativo. Para retornar ao aplicativo, basta marcar o link ou salvar o email.

## <a name="licensing"></a>Licenças

O usuário convidado precisa ter a licença correta em vigor para ver o aplicativo compartilhado. Há três opções para fazer isso: usar o Power BI Premium; atribuir uma licença do Power BI Pro; ou usar a licença do Power BI Pro do convidado.

### <a name="use-power-bi-premium"></a>Usar o Power BI Premium

A atribuição do espaço de trabalho do aplicativo à [capacidade do Power BI Premium](service-premium.md) permite que o usuário convidado use o aplicativo sem precisar de uma licença do Power BI Pro. O Power BI Premium também permite que aplicativos aproveitem outros recursos, como taxas mais altas de atualização, capacidade dedicada e tamanhos grandes de modelos.

![Usar o Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Atribuir uma licença do Power BI Pro ao usuário convidado

A atribuição de uma licença do Power BI Pro ao usuário convidado, dentro do locatário, permite que o usuário convidado veja o conteúdo no locatário.

![Atribuir licença Pro do locatário](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>O usuário convidado traz a própria licença do Power BI Pro

O usuário convidado já tem uma licença do Power BI Pro atribuída em seu locatário.

![O usuário convidado traz a própria licença](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Convidados de B2B externos são limitados somente para consumo de conteúdo. Convidados de B2B externos podem exibir aplicativos, dashboards, relatórios, exportar dados e criar assinaturas de email para dashboards e relatórios. Eles não podem acessar os workspaces ou publicar seu próprio conteúdo.

* Este recurso não está disponível atualmente com os aplicativos móveis do Power BI. Em um dispositivo móvel, é possível exibir o conteúdo do Power BI compartilhado usando B2B do Azure AD em um navegador.

* Este recurso não está disponível atualmente com a web part de relatório do Power BI para o SharePoint Online.

## <a name="next-steps"></a>Próximas etapas

Para saber mais, incluindo como funciona a segurança no nível da linha, confira o white paper: [Distribuir conteúdo do Power BI para usuários externos convidados usando o Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper).

Para saber mais sobre o Azure AD B2B, confira [O que é a colaboração do Azure AD B2B?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
