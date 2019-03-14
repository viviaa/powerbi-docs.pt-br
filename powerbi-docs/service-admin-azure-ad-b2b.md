---
title: Distribuir conteúdos para usuários convidados externos com o Azure AD B2B
description: O Power BI integra-se ao Azure Active Directory Business-to-business (Azure AD B2B) para permitir distribuição segura do conteúdo do Power BI aos usuários convidados fora da organização.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 0eba54212ff9349ed75d9d9fb18878b39d5cd29a
ms.sourcegitcommit: 378265939126fd7c96cb9334dac587fc80291e97
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/07/2019
ms.locfileid: "57580187"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuir o conteúdo do Power BI para usuários convidados externo com o Azure AD B2B

O Power BI integra-se ao Azure AD B2B (Azure Active Directory business-to-business) para permitir distribuição segura do conteúdo do Power BI aos usuários convidados fora da sua organização, enquanto ainda mantém controle sobre os dados internos.  

Além disso, você pode permitir que usuários convidados fora da sua organização editem e gerenciem o conteúdo dentro de sua organização.

## <a name="enable-access"></a>Habilitar acesso

Habilite o recurso de [Compartilhar conteúdo com usuários externos](service-admin-portal.md#export-and-sharing-settings) no portal de administração do Power BI antes de convidar usuários.

Além disso, o recurso [Permitir que os usuários externos convidados editem e gerenciem o conteúdo da organização](service-admin-portal.md#export-and-sharing-settings) permite que você selecione qual usuário convidado pode ver e criar conteúdo em workspaces, incluindo a navegação pelo Power BI da sua organização.

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

O usuário convidado precisa ter a licença correta em vigor para ver o conteúdo compartilhado. Há três opções para fazer isso: usar o Power BI Premium; atribuir uma licença do Power BI Pro; ou usar a licença do Power BI Pro do convidado.

Ao usar o recurso [Permitir que os usuários externos convidados editem e gerenciem o conteúdo da organização](service-admin-portal.md#export-and-sharing-settings), usuários convidados que contribuem com conteúdo para os workspaces ou compartilham conteúdo com outras pessoas exigem uma licença do Power BI Pro.

### <a name="use-power-bi-premium"></a>Usar o Power BI Premium

A atribuição do espaço de trabalho do aplicativo à [capacidade do Power BI Premium](service-premium.md) permite que o usuário convidado use o aplicativo sem precisar de uma licença do Power BI Pro. O Power BI Premium também permite que aplicativos aproveitem outros recursos, como taxas mais altas de atualização, capacidade dedicada e tamanhos grandes de modelos.

![Usar o Power BI Premium](media/service-admin-azure-ad-b2b/license-approach1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Atribuir uma licença do Power BI Pro ao usuário convidado

A atribuição de uma licença do Power BI Pro ao usuário convidado, dentro do locatário, permite que o usuário convidado veja o conteúdo no locatário.

![Atribuir licença Pro do locatário](media/service-admin-azure-ad-b2b/license-approach2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>O usuário convidado traz a própria licença do Power BI Pro

O usuário convidado já tem uma licença do Power BI Pro atribuída em seu locatário.

![O usuário convidado traz a própria licença](media/service-admin-azure-ad-b2b/license-approach3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Usuários convidados que podem editar e gerenciar conteúdo 

Ao usar o recurso [Permitir que os usuários externos convidados editem e gerenciem o conteúdo da organização](service-admin-portal.md#export-and-sharing-settings), os usuários convidados especificados obtêm acesso ao Power BI da sua organização e veem todo o conteúdo para o qual têm permissão. Eles podem acessar a página inicial, navegar por workspaces, instalar aplicativos que estão na lista de acesso e contribuir com conteúdo para os workspaces. Eles podem ser administradores de workspaces que usam a nova experiência de workspace e até mesmo criar tais workspaces. Algumas limitações se aplicam e são listadas na seção Considerações e limitações.

Para ajudar esses usuários a fazerem logon no Power BI, forneça a eles a URL do locatário. Para localizar a URL do locatário, siga estas etapas.

1. No serviço do Power BI, no menu superior, selecione a Ajuda (**?**), em seguida, **Sobre o Power BI**.

2. Procure o valor ao lado de **URL do locatário**. Essa é a URL do locatário que você pode compartilhar com os usuários convidados.

![URL do locatário de usuários convidados](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Por padrão, convidados de B2B externos são limitados somente para consumo de conteúdo. Convidados de B2B externos podem exibir aplicativos, dashboards, relatórios, exportar dados e criar assinaturas de email para dashboards e relatórios. Eles não podem acessar os workspaces ou publicar seu próprio conteúdo. No entanto, essas restrições não se aplicam a usuários convidados que são permitidos por meio da configuração de locatário [Permitir que os usuários externos convidados editem e gerenciem o conteúdo da organização](service-admin-portal.md#export-and-sharing-settings).

* Algumas experiências não estão disponíveis a usuários convidados habilitados por usuários por meio da configuração de locatário [Permitir que os usuários externos convidados editem e gerenciem o conteúdo da organização](service-admin-portal.md#export-and-sharing-settings). Para atualizar ou publicar relatórios, eles precisarão usar a interface do usuário da Web do serviço do Power BI, incluindo Obter Dados para carregar arquivos do Power BI Desktop.  As seguintes experiências não são compatíveis:
    * Publicação direta do Power BI Desktop para o serviço do Power BI
    * Usuários convidados não podem usar o Power BI Desktop para se conectar a conjuntos de dados de serviço no serviço do Power BI
    * Workspaces clássicos associados a Grupos do Office 365: Um usuário convidado não é capaz de criar ou ser administradores desses workspaces. Eles podem ser membros.
    * O envio de convites ad-hoc para listas de acesso do workspace não é uma ação compatível
    * O Power BI Publisher para Excel não é compatível com usuários convidados
    * Usuários convidados não podem instalar um Power BI Gateway e conectá-lo à sua organização
    * Usuários convidados não podem instalar aplicativos e publicá-los para toda a organização
    * Usuários convidados não podem usar, criar, atualizar ou instalar pacotes de conteúdo organizacional
    * Usuários convidados não podem usar o Analisar no Excel
    * Usuários convidados não podem ser @mentioned em comentários
    * Usuários convidados não podem usar assinaturas
    * Usuários convidados que usam essa funcionalidade devem ter uma conta corporativa ou de estudante. Usuários convidados usando contas pessoais terão mais limitações devido a restrições de entrada.

* Este recurso não está disponível atualmente com a web part de relatório do Power BI para o SharePoint Online.

* Há configurações do Active Directory que podem limitar o que os usuários convidados externos podem fazer dentro de sua organização em geral e que também se aplicam ao seu ambiente do Power BI. A documentação a seguir descreve as configurações:
    * [Gerenciar configurações de colaboração externa](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations#control-who-can-invite)
    * [Permitir ou bloquear convites para usuários B2B de organizações específicas](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações, incluindo sobre como funciona a segurança de linha, confira o white paper: [Distribuir o conteúdo do Power BI para usuários convidados externo com o Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper).

Para saber mais sobre o Azure AD B2B, confira [O que é a colaboração do Azure AD B2B?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
