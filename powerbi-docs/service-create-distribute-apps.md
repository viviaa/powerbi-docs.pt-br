---
title: Publicar um aplicativo no Power BI
description: Saiba como publicar os novos aplicativos, que são coleções de dashboards e relatórios com navegação interna.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 67678a150b4fce802bef2b287211cf438b832e82
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66459576"
---
# <a name="publish-an-app-in-power-bi"></a>Publicar um aplicativo no Power BI

No Power BI, você pode criar um conteúdo empacotado oficial e, em seguida, distribuí-lo para um público-alvo amplo como um *aplicativo*. Crie aplicativos nos *workspaces do aplicativo*, em que é possível colaborar no conteúdo do Power BI com seus colegas. Em seguida, é possível publicar os aplicativos concluídos em grandes grupos de pessoas em sua organização. 

![Aplicativos do Power BI](media/service-create-distribute-apps/power-bi-new-apps.png)

Os usuários empresariais geralmente precisam de vários dashboards e relatórios do Power BI para administrar os negócios. Com os aplicativos do Power BI, crie coleções de dashboards e relatórios e publique esses aplicativos para toda a organização ou para pessoas ou grupos específicos. Para você, como administrador ou criador de relatórios, os aplicativos facilitam o gerenciamento de permissões nessas coleções.

Os usuários empresariais obtêm seus aplicativos de algumas maneiras diferentes:

- Eles podem encontrar e instalar seus aplicativos no Microsoft AppSource
- Você pode enviar um link direto para eles.
- Você poderá instalá-lo automaticamente nas contas do Power BI de seus colegas, se o administrador do Power BI lhe der permissão.

Você pode criar o aplicativo com sua própria navegação interna, de modo que os usuários possam encontrar o conteúdo com facilidade. Eles não podem modificar o conteúdo do aplicativo. Eles podem interagir com ele no serviço do Power BI ou em um dos aplicativos móveis – filtrando, realçando e classificando os dados por conta própria. Eles recebem atualizações automaticamente e você pode controlar a frequência com que os dados são atualizados. Leia mais sobre a [experiência de aplicativo para usuários corporativos](consumer/end-user-apps.md).

## <a name="licenses-for-apps"></a>Licenças para aplicativos
Para criar ou atualizar um aplicativo, você precisa de uma licença do Power BI Pro. Para os *consumidores* do aplicativo, há duas opções.

* Opção 1: todos os usuários empresariais precisam de licenças do **Power BI Pro** para exibir seu aplicativo. 
* Opção 2: Se o workspace do aplicativo residir em uma capacidade Premium do Power BI, os usuários gratuitos de sua organização poderão ver o conteúdo do aplicativo. Leia [O que é o Power BI Premium?](service-premium.md) para obter detalhes.

## <a name="publish-your-app"></a>Publicar seu aplicativo
Quando os dashboards e relatórios em seu workspace estiverem prontos, escolha quais dashboards e relatórios você deseja publicar e publique-os como um aplicativo. 

1. Na exibição da lista do workspace, decida quais dashboards e relatórios você deseja **incluir no aplicativo**.

     ![Selecionar o dashboard a ser publicado](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Se optar por não incluir um relatório que tenha um dashboard relacionado, você verá um aviso ao lado do relatório. Você ainda poderá publicar o aplicativo, mas o dashboard relacionado não terá os blocos desse relatório.

     ![Aviso sobre dashboard relacionado](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Selecione o botão **Publicar aplicativo** no canto superior direito para iniciar o processo de criação e publicação de um aplicativo por meio do workspace.
   
     ![Publicar aplicativo](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. Em **Instalação**, preencha o nome e a descrição para ajudar as pessoas a encontrar o aplicativo. Defina uma cor de tema para personalizá-lo. Adicione também um link para um site de suporte.
   
     ![Criar seu aplicativo](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. Em **Navegação**, selecione o conteúdo a ser publicado como parte do aplicativo. Em seguida, você adicionará a navegação do aplicativo para organizar o conteúdo em seções. Confira [Projetar a experiência de navegação para seu aplicativo](#design-the-navigation-experience-for-your-app) neste artigo para obter detalhes.
   
     ![Navegação do aplicativo](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. Em **Permissão**, decida quem tem acesso ao aplicativo e o que ele pode fazer com ele. 
    - Em [workspaces clássicos](service-create-workspaces.md): todos em sua organização, pessoas específicas ou grupos de segurança do AAD (Azure Active Directory).
    - Em [workspaces da nova experiência](service-create-the-new-workspaces.md): pessoas específicas, listas de distribuição e grupos de segurança do AAD e grupos do Office 365.

6. Você poderá instalar o aplicativo automaticamente para os destinatários se o administrador do Power BI tiver habilitado essa configuração para você no Portal de Administração do Power BI. Leia mais sobre como [instalar um aplicativo automaticamente](#automatically-install-apps-for-end-users) neste artigo.

     ![Permissões ao aplicativo](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. Ao selecionar **Publicar aplicativo**, você verá uma mensagem confirmando que ele está pronto para ser publicado. Na caixa de diálogo **Compartilhar este aplicativo**, copie a URL que é um link direto para esse aplicativo.
   
     ![Término do aplicativo](media/service-create-distribute-apps/power-bi-apps-success.png)

Envie esse link direto para as pessoas com quem você o compartilhou ou elas poderão encontrar seu aplicativo na guia Aplicativos acessando **Baixar e explorar mais aplicativos no AppSource**. Leia mais sobre a [experiência de aplicativo para usuários corporativos](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>Alterar o aplicativo publicado
Depois de publicar seu aplicativo, você talvez queira alterá-lo ou atualizá-lo. É fácil atualizá-lo se você é um administrador ou membro do workspace do novo aplicativo. 

1. Abra o workspace de aplicativo que corresponde ao aplicativo. 
   
     ![Abrir workspace](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. Faça as alterações desejadas nos dashboards ou nos relatórios.
 
     O workspace de aplicativo é sua área de preparo, portanto, suas alterações não entrarão em vigor no aplicativo até que você publique novamente. Isso permite que você faça alterações sem afetar os aplicativos publicados.  
 
    > [!IMPORTANT]
    > Caso você remova um relatório e atualize o aplicativo, mesmo que você adicionar o relatório novamente ao aplicativo, os consumidores do aplicativo perderão todas as personalizações, como indicadores, comentários etc.  
 
3. Volte para a lista de conteúdo do workspace do aplicativo e selecione **Atualizar aplicativo** no canto superior direito.
   
1. Atualize **Instalação**, **Navegação** e **Permissões**, se necessário e, em seguida, selecione **Atualizar aplicativo**.
   
As pessoas para as quais você publicou o aplicativo verão automaticamente a versão atualizada do aplicativo. 

## <a name="design-the-navigation-experience-for-your-app"></a>Projetar a experiência de navegação para seu aplicativo
A opção **Novo construtor de navegação** permite que você crie uma navegação personalizada para seu aplicativo. A navegação personalizada facilita para os usuários encontrar e usar o conteúdo no aplicativo. Os aplicativos existentes têm essa opção desativada e os novos aplicativos usam como padrão a opção ativada.

Quando a opção está desativada, você pode selecionar a **Página de aterrissagem do aplicativo** como **Conteúdo específico**, por exemplo, um dashboard ou um relatório, ou selecionar **Nenhum** para mostrar uma lista básica de conteúdo para o usuário.

Ao ativar o **Novo construtor de navegação**, você poderá projetar uma navegação personalizada. Por padrão, todos os relatórios, todos os dashboards e todas as pastas de trabalho do Excel incluídos em seu aplicativo são listados como uma lista plana. 

![Navegação do aplicativo](media/service-create-distribute-apps/power-bi-apps-navigation.png)

Personalize ainda mais a navegação do aplicativo:
* Reordenando os itens usando as setas para cima/para baixo. 
* Renomeando itens em **Detalhes do relatório**, **Detalhes do dashboard** e **Detalhes da pasta de trabalho**.
* Ocultando determinados itens do painel de navegação.
* Usando a opção **Novo** para adicionar **seções** ao conteúdo relacionado ao grupo.
* Usando a opção **Novo** para adicionar um **link** para um recurso externo ao painel de navegação à esquerda. 

Ao adicionar um **link**, em **Detalhes do link**, você poderá escolher em qual página o link será aberto. Por padrão, os links são abertos na **Guia atual**, mas você pode selecionar **Nova guia** ou **Área de conteúdo**. 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>Considerações sobre o uso da opção novo construtor de navegação
Estes são os itens gerais para ter em mente ao usar o novo construtor de navegação:
* As páginas do relatório são mostradas na área de navegação do aplicativo como uma seção expansível
* Se você desligar o novo construtor de navegação e, em seguida, publicar ou atualizar seu aplicativo, você perderá as personalizações feitas. Por exemplo, as seções, a ordenação, os links e os nomes personalizados para itens de navegação são todos perdidos.

Ao adicionar links à navegação do aplicativo e selecionar a opção Área de conteúdo:
* Verifique se o link pode ser inserido. Alguns serviços bloqueiam a inserção de seu conteúdo em sites de terceiros, como o Power BI.
* A inserção de conteúdo do serviço do Power BI, como relatórios ou dashboards em outros workspaces, não é compatível. 
* Insira o conteúdo do Servidor de Relatórios do Power BI por meio de seu conteúdo de URL inserido nativo por meio de uma implantação local. Use as etapas descritas em [Como criar a URL do Servidor de Relatórios do Power BI](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#creating-the-power-bi-report-server-report-url) para obter a URL. Lembre-se de que as regras de autenticação normais se aplicam; portanto, a exibição do conteúdo exige uma conexão VPN com o servidor local. 
* Um aviso de segurança é mostrado na parte superior do conteúdo inserido para indicar que o conteúdo não está no Power BI.



## <a name="automatically-install-apps-for-end-users"></a>Instalar aplicativos automaticamente para usuários finais
Se um administrador conceder permissões a você, você poderá instalar aplicativos automaticamente, *enviando-os por push* aos usuários finais. Essa funcionalidade de push facilita a distribuição dos aplicativos certos para as pessoas ou os grupos certos. Seu aplicativo é exibido automaticamente na lista de conteúdo Aplicativos dos usuários finais. Eles não precisarão encontrá-lo no Microsoft AppSource nem seguir um link de instalação. Veja como os administradores habilitam o [push de aplicativos aos usuários finais](service-admin-portal.md#push-apps-to-end-users) no artigo do portal de administração do Power BI.

### <a name="how-to-push-an-app-automatically-to-end-users"></a>Como enviar por push um aplicativo automaticamente aos usuários finais
Depois que o administrador tiver atribuído permissões a você, você terá uma nova opção para **instalar o aplicativo automaticamente**. Quando você marca a caixa e seleciona **Publicar aplicativo** (ou **Atualizar aplicativo**), o aplicativo é enviado por push a todos os usuários ou grupos definidos na seção **Permissões** do aplicativo na guia **Acesso**.

![Habilitar envio de aplicativos por push](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>Como os usuários obtêm os aplicativos que você envia por push a eles
Depois que você envia um aplicativo por push, ele é exibido na lista Aplicativos automaticamente. Dessa forma, você pode coletar os aplicativos que funções de trabalho ou usuários específicos em sua organização precisam ter ao seu alcance.

![Habilitar envio de aplicativos por push](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Considerações para instalar aplicativos automaticamente
Aqui estão algumas coisas para se ter em mente ao enviar aplicativos por push para usuários finais:

* Instalar um aplicativo automaticamente para usuários pode levar tempo. A maioria dos aplicativos é instalada imediatamente para os usuários, mas o push de aplicativos pode levar algum tempo.  Isso depende do número de itens no aplicativo e do número de pessoas que receberam acesso. É recomendável enviar aplicativos por push durante horas vagas em que haja muito tempo antes de os usuários precisarem deles. Verifique com vários usuários antes de enviar comunicação abrangentes sobre a disponibilidade de aplicativos.

* Atualize o navegador. Antes de ver o aplicativo enviado por push na Lista de aplicativos, talvez o usuário precise atualizar ou fechar e reabrir seu navegador.

* Se os usuários não virem imediatamente o aplicativo na lista Aplicativos, eles deverão atualizar ou fechar e reabrir o navegador.

* Tente não sobrecarregar os usuários. Tenha cuidado para não enviar muitos aplicativos por push para que seus usuários entendam que os aplicativos pré-instalados são úteis para eles. É melhor controlar quem pode enviar aplicativos por push para os usuários finais para coordenar o tempo. Estabeleça um ponto de contato para enviar aplicativos por push em sua organização aos usuários finais.

* Os aplicativos não são instalados automaticamente para os usuários convidados que não aceitaram um convite.  

## <a name="unpublish-an-app"></a>Cancelar a publicação de um aplicativo
Qualquer membro de um workspace do aplicativo pode cancelar a publicação do aplicativo.

>[!IMPORTANT]
>Quando você cancela a publicação de um aplicativo, os usuários do aplicativo perdem as personalizações. Eles perdem todos os indicadores, as assinaturas ou os comentários pessoais associados ao conteúdo do aplicativo. Só cancele a publicação de um aplicativo se você precisar removê-la.
> 
> 

* No workspace do aplicativo, selecione as reticências ( **...** ) no canto superior direito &gt; **Cancelar a publicação do aplicativo**.
  
     ![Cancelar a publicação do aplicativo](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Essa ação desinstala o aplicativo em todos para os quais você o distribuiu e eles não terão mais acesso ao aplicativo. Ela não exclui o workspace do aplicativo ou seu conteúdo.

## <a name="view-your-published-app"></a>Exibir o aplicativo publicado

Quando os consumidores do aplicativo abrem seu aplicativo, eles veem a navegação que você criou, em vez do painel de navegação à esquerda padrão do Power BI. A navegação do aplicativo lista os relatórios e os dashboards nas seções definidas. Ela também lista as páginas individuais em cada relatório, em vez de apenas o nome do relatório.

![Aplicativo com navegação](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="next-steps"></a>Próximas etapas
* [Criar um workspace de aplicativo](service-create-workspaces.md)
* [Instalar e usar aplicativos no Power BI](consumer/end-user-apps.md)
* [Aplicativos do Power BI para serviços externos](service-connect-to-services.md)
* [Portal de administração do Power BI](https://docs.microsoft.com/power-bi/service-admin-portal)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
