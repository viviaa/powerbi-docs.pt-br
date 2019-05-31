---
title: Distribuir conteúdos para usuários convidados externos com o Azure AD B2B
description: O Power BI integra-se ao Azure Active Directory Business-to-business (Azure AD B2B) para permitir distribuição segura do conteúdo do Power BI aos usuários convidados fora da organização.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 2d1e9e32fcec67647bb75ac14ed872e6c51fef96
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65101663"
---
# <a name="distribute-power-bi-content-to-external-guest-users-with-azure-ad-b2b"></a>Distribuir o conteúdo do Power BI para usuários convidados externo com o Azure AD B2B

O Power BI integra-se ao Azure AD B2B (Azure Active Directory business-to-business) para permitir distribuição segura do conteúdo do Power BI aos usuários convidados fora da sua organização, enquanto ainda mantém controle sobre os dados internos.  

Além disso, você pode permitir que usuários convidados fora da sua organização editem e gerenciem o conteúdo dentro de sua organização.

## <a name="enable-access"></a>Habilitar acesso

Certifique-se de habilitar o [compartilhem conteúdo com usuários externos](service-admin-portal.md#export-and-sharing-settings) recurso no portal de administração do Power BI antes de convidar usuários convidados.

Você também pode usar o [permitir que os usuários convidados externo editar e gerenciar o conteúdo da organização](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) recurso. Ele permite que você selecione qual usuário convidado pode ver e criar conteúdo em espaços de trabalho, incluindo a navegação Power BI da sua organização.

## <a name="who-can-you-invite"></a>Que você pode convidar?

Você pode convidar usuários convidados com qualquer endereço de email, incluindo contas pessoais como hotmail.com, outlook.com e gmail.com. B2B do AD do Azure chama esses endereços *identidades sociais*.

## <a name="invite-guest-users"></a>Convidar usuários convidados

Usuários convidados exigem somente convites na primeira vez que você convide-os à sua organização. Há duas maneiras para convidar usuários: planejada convites e convites ad-hoc.

### <a name="planned-invites"></a>Convites planejados

Use um convite planejado se souber quais usuários vai convidar. Envie o convite pelo Portal do Azure ou pelo PowerShell. Você deve ser administrador de locatários para convidar pessoas.

Execute estas etapas para enviar um convite no Portal do Azure.

1. No [Portal do Azure](https://portal.azure.com), selecione **Azure Active Directory**.

1. Sob **Manage**, selecione **usuários** > **todos os usuários** > **novo usuário convidado**.

    ![Captura de tela do portal do Azure com a nova opção de usuário convidado destacadas.](media/service-admin-azure-ad-b2b/azure-ad-portal-new-guest-user.png)

1. Insira um **endereço de email** e **mensagem pessoal**.

    ![Captura de tela da caixa de diálogo do Azure AD Portal novo usuário convidado.](media/service-admin-azure-ad-b2b/azure-ad-portal-invite-message.png)

1. Selecione **Convidar**.

Para convidar mais de um usuário convidado, use o PowerShell. Para saber mais, confira [Amostras do código de colaboração e do PowerShell no Azure AD B2B](/azure/active-directory/b2b/code-samples/).

O usuário convidado precisa selecionar **Introdução** no convite que recebeu por email. O usuário convidado é adicionado ao locatário.

![Convite por email de usuário de captura de tela de convidado.](media/service-admin-azure-ad-b2b/guest-user-invite-email.png)

### <a name="ad-hoc-invites"></a>Convites ad hoc

Para convidar um usuário externo a qualquer momento, adicione-os ao seu dashboard ou relatório por meio do compartilhamento da interface do usuário, ou seu aplicativo por meio da página de acesso. Aqui está um exemplo de como convidar um usuário externo para usar um aplicativo.

![Usuário de captura de tela de externo adicionado à lista de acesso do aplicativo no Power BI.](media/service-admin-azure-ad-b2b/power-bi-app-access.png)

O usuário convidado receberá um email indicando que você compartilhou o aplicativo com eles.

![Captura de tela de Email de aplicativo compartilhado com usuário convidado](media/service-admin-azure-ad-b2b/guest-user-invite-email-2.png)

O usuário convidado deverá entrar com o endereço de email da organização. Eles receberão um prompt para aceitar o convite depois de entrar. Depois de entrar, o aplicativo é aberto para o usuário convidado. Para retornar ao aplicativo, basta marcar o link ou salvar o email.

## <a name="licensing"></a>Licenças

O usuário convidado deve ter o licenciamento correto em vigor para exibir o conteúdo que você compartilhou. Há três maneiras para se certificar de que o usuário tem uma licença apropriada: usar o Power BI Premium, atribuir uma licença do Power BI Pro ou usar a licença do Power BI Pro do convidado.

Ao usar o recurso [Permitir que os usuários externos convidados editem e gerenciem o conteúdo da organização](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization), usuários convidados que contribuem com conteúdo para os workspaces ou compartilham conteúdo com outras pessoas exigem uma licença do Power BI Pro.

### <a name="use-power-bi-premium"></a>Usar o Power BI Premium

O espaço de trabalho de aplicativo para a atribuição [capacidade do Power BI Premium](service-premium-what-is.md) permite que o usuário convidado use o aplicativo sem a necessidade de uma licença do Power BI Pro. O Power BI Premium também permite que os aplicativos aproveitar outros recursos, como taxas de atualização de maior capacidade dedicada e tamanhos grandes de modelos.

![Diagrama da experiência do usuário convidado com o Power BI Premium.](media/service-admin-azure-ad-b2b/license-approach-1.png)

### <a name="assign-a-power-bi-pro-license-to-guest-user"></a>Atribuir uma licença do Power BI Pro ao usuário convidado

Atribuir uma licença do Power BI Pro para o usuário convidado, dentro do seu locatário, permite que esse conteúdo de modo de exibição do usuário convidado no locatário.

![Diagrama da experiência do usuário convidado com licença atribuir Pro do seu locatário.](media/service-admin-azure-ad-b2b/license-approach-2.png)

### <a name="guest-user-brings-their-own-power-bi-pro-license"></a>O usuário convidado traz a própria licença do Power BI Pro

O usuário convidado já tem uma licença do Power BI Pro atribuída em seu locatário.

![Diagrama da experiência do usuário convidado quando eles tragam sua própria licença.](media/service-admin-azure-ad-b2b/license-approach-3.png)

## <a name="guest-users-who-can-edit-and-manage-content"></a>Usuários convidados que podem editar e gerenciar conteúdo 

Ao usar o [permitir que os usuários convidados externo editar e gerenciar o conteúdo da organização](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) recurso, os usuários convidados especificado obtém acesso ao Power BI de sua organização. Eles podem ver qualquer conteúdo ao qual eles têm permissão. Eles podem acessar a página inicial, procurar os espaços de trabalho, instalar aplicativos, consulte onde eles estão na lista de acesso e contribuir com conteúdo para os espaços de trabalho. Eles podem ser administradores de workspaces que usam a nova experiência de workspace e até mesmo criar tais workspaces. Algumas limitações se aplicam. A seção considerações e limitações listar essas restrições.
 
Para ajudar a esses usuários entrar no Power BI, forneça a URL do locatário. Para localizar a URL do locatário, siga estas etapas.

1. No serviço do Power BI, no menu superior, selecione a Ajuda ( **?** ), em seguida, **Sobre o Power BI**.

2. Procure o valor ao lado de **URL do locatário**. O valor é a URL de locatário, você pode compartilhar com os usuários convidados.

    ![Caixa de diálogo de captura de tela de sobre o Power BI com o locatário do usuário convidado que URL destacados.](media/service-admin-azure-ad-b2b/power-bi-about-dialog.png)

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Por padrão, externo B2B de AD do Azure limita convidados para consumo de conteúdo apenas. Convidados de B2B do Azure AD externos podem exibir aplicativos, painéis, relatórios, exportar os dados e criar assinaturas de email para dashboards e relatórios. Eles não podem acessar os workspaces ou publicar seu próprio conteúdo. No entanto, essas restrições não se aplicam a usuários convidados que tem acesso por meio de [permitir que os usuários convidados externo editar e gerenciar o conteúdo da organização](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) recurso.

* Para usuários convidados habilitados por meio de [permitir que os usuários convidados externo editar e gerenciar o conteúdo da organização](service-admin-portal.md#allow-external-guest-users-to-edit-and-manage-content-in-the-organization) recurso, algumas experiências não estão disponíveis a eles. Para atualizar ou publicar relatórios, eles precisarão usar a interface do usuário da Web do serviço do Power BI, incluindo Obter Dados para carregar arquivos do Power BI Desktop.  Não há suporte para as seguintes experiências:
    * Publicação direta do Power BI Desktop para o serviço do Power BI
    * Usuários convidados não podem usar o Power BI desktop para se conectar a conjuntos de dados de serviço no serviço do Power BI
    * Workspaces clássicos associados a Grupos do Office 365:
        * Usuário convidado não é possível criar ou ser administradores desses espaços de trabalho
        * Os usuários convidados podem ser membros
    * Enviar convites ad-hoc não há suporte para listas de acesso do espaço de trabalho
    * Power BI Publisher para Excel não tem suporte para usuários convidados
    * Os usuários convidados não é possível instalar um do Power BI Gateway e conectá-lo à sua organização
    * Usuários convidados não é possível instalar aplicativos de publicação em toda a organização
    * Usuários convidados não podem usar, criar, atualizar ou instalar pacotes de conteúdo organizacional
    * Usuários convidados não podem usar analisar no Excel
    * Usuários convidados não podem ser @mentioned em comentários
    * Usuários convidados não podem usar assinaturas
    * Usuários convidados que usam essa funcionalidade devem ter uma conta corporativa ou de estudante. Usuários convidados usando contas pessoais terão mais limitações devido para entrar nas restrições.

* Esse recurso não está disponível com a web part de relatório do Power BI do SharePoint Online.

* Há configurações do Active Directory que pode limitar o que os usuários convidados externo podem fazer em sua organização geral. Que também se aplica ao seu ambiente do Power BI. A documentação a seguir descreve as configurações:
    * [Gerenciar configurações de colaboração externa](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations#control-who-can-invite)
    * [Permitir ou bloquear convites para usuários B2B de organizações específicas](https://docs.microsoft.com/azure/active-directory/b2b/allow-deny-list)  

## <a name="next-steps"></a>Próximas etapas

Para obter informações mais detalhadas, incluindo trabalhos de segurança de nível de linha como, confira o white paper: [Distribuir o conteúdo do Power BI para usuários convidados externo com o Azure AD B2B](https://aka.ms/powerbi-b2b-whitepaper).

Para obter informações sobre o Azure AD B2B, consulte [o que é colaboração B2B do Azure AD?](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b/).
