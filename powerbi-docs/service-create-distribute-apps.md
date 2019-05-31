---
title: Publicar um aplicativo no Power BI
description: Saiba como publicar os novos aplicativos são coleções de dashboards e relatórios com navegação interna.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f3f933a3e3af2ef1d7864b379e9b8b5520d505ff
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65941566"
---
# <a name="publish-an-app-in-power-bi"></a>Publicar um aplicativo no Power BI

No Power BI, você pode criar oficial empacotado conteúdo e distribuí-lo para um público amplo como uma *aplicativo*. Crie aplicativos nos *workspaces do aplicativo*, em que é possível colaborar no conteúdo do Power BI com seus colegas. Em seguida, é possível publicar os aplicativos concluídos em grandes grupos de pessoas em sua organização. 

![Aplicativos do Power BI](media/service-create-distribute-apps/power-bi-new-apps.png)

Os usuários empresariais geralmente precisam de vários dashboards e relatórios do Power BI para administrar os negócios. Com os aplicativos do Power BI, crie coleções de dashboards e relatórios e publique esses aplicativos para toda a organização ou para pessoas ou grupos específicos. Para você, como administrador ou criador de relatórios, os aplicativos facilitam o gerenciamento de permissões nessas coleções.

Usuários de negócios obtêm seus aplicativos de algumas maneiras diferentes:

- Eles podem localizar e instalar seu aplicativo no Microsoft AppSource
- Você pode enviar um link direto.
- Você poderá instalá-lo automaticamente nas contas do Power BI de seus colegas, se o administrador do Power BI lhe der permissão.

Você pode criar o aplicativo com sua própria navegação interna, para que seus usuários podem facilmente localizar com o seu conteúdo. Eles não podem modificar o conteúdo do aplicativo. Eles podem interagir com ele no serviço do Power BI ou em um dos aplicativos móveis- – filtrando, realçando e classificando os dados. Eles recebem atualizações automaticamente e você pode controlar a frequência com que os dados são atualizados. Leia mais sobre a [experiência de aplicativo para usuários corporativos](consumer/end-user-apps.md).

## <a name="licenses-for-apps"></a>Licenças para aplicativos
Para criar ou atualizar um aplicativo, você precisa de uma licença do Power BI Pro. Para o aplicativo *consumidores*, há duas opções.

* Opção 1: todos os usuários empresariais precisam de licenças do **Power BI Pro** para exibir seu aplicativo. 
* Opção 2: Se o seu espaço de trabalho reside em uma capacidade do Power BI Premium, usuários gratuitos de sua organização podem exibir o conteúdo do aplicativo. Leia [O que é o Power BI Premium?](service-premium.md) para obter detalhes.

## <a name="publish-your-app"></a>Publicar seu aplicativo
Quando os dashboards e relatórios em seu workspace estiverem prontos, escolha quais dashboards e relatórios você deseja publicar e publique-os como um aplicativo. 

1. Na exibição de lista de espaço de trabalho, decida quais painéis e relatórios que você deseja **incluído no aplicativo**.

     ![Selecionar o dashboard a ser publicado](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Se você optar por não incluir um relatório que tem um dashboard relacionado, você verá um aviso ao lado do relatório. Você ainda pode publicar o aplicativo, mas no dashboard relacionado não terá os blocos do relatório.

     ![Aviso sobre dashboard relacionado](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Selecione o **aplicativo de publicação** botão no canto superior direito para iniciar o processo de criação e publicação de um aplicativo da área de trabalho.
   
     ![Publicar aplicativo](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. Na **instalação**, preencha o nome e descrição para ajudar as pessoas a localizar o aplicativo. Você pode definir uma cor de tema para personalizá-la. Você também pode adicionar um link para um site de suporte.
   
     ![Crie seu aplicativo](media/service-create-distribute-apps/power-bi-apps-build-your-apps.png)

4. Na **navegação**, selecione o conteúdo a ser publicado como parte do aplicativo. Em seguida, você pode adicionar navegação de aplicativo, para organizar o conteúdo nas seções. Ver [projetar a experiência de navegação para seu aplicativo](#design-the-navigation-experience-for-your-app) neste artigo para obter detalhes.
   
     ![Navegação do aplicativo](media/service-create-distribute-apps/power-bi-apps-navigation.png)

5. Na **acesso**, decida quem tem acesso ao aplicativo. 
    - Na [espaços de trabalho clássicos](service-create-workspaces.md): todos em sua organização, pessoas específicas ou grupos de segurança do Azure Active Directory (AAD).
    - No [novos espaços de trabalho de experiência](service-create-the-new-workspaces.md): pessoas específicas, grupos de segurança do AAD e listas de distribuição e grupos do Office 365.

6. Se você tiver permissões, você pode instalar o aplicativo automaticamente para os destinatários. Um administrador do Power BI pode habilitar essa configuração no Portal de administração do Power BI. Leia mais sobre [instala automaticamente um aplicativo](#automatically-install-apps-for-end-users) neste artigo.

     ![Permissões ao aplicativo](media/service-create-distribute-apps/power-bi-apps-permissions.png)

7. Quando você seleciona **aplicativo de publicação**, você verá uma mensagem confirmando que ele está pronto para publicar. No **compartilhar este aplicativo** caixa de diálogo, você pode copiar a URL que é um link direto para esse aplicativo.
   
     ![Término do aplicativo](media/service-create-distribute-apps/power-bi-apps-success.png)

Você pode enviar que o link direto para as pessoas com quem você compartilhou com, ou eles podem encontrar seu aplicativo na guia aplicativos acessando **baixar e explorar mais aplicativos no AppSource**. Leia mais sobre a [experiência de aplicativo para usuários corporativos](consumer/end-user-apps.md).

## <a name="change-your-published-app"></a>Alterar o aplicativo publicado
Depois de publicar seu aplicativo, você talvez queira alterá-lo ou atualizá-lo. É fácil atualizá-lo se você for um administrador ou membro no novo espaço de trabalho do aplicativo. 

1. Abra o workspace de aplicativo que corresponde ao aplicativo. 
   
     ![Abrir workspace](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)

2. Faça as alterações desejadas na dashboards ou relatórios.
 
     O workspace de aplicativo é sua área de preparo, portanto, suas alterações não entrarão em vigor no aplicativo até que você publique novamente. Isso permite que você faça alterações sem afetar os aplicativos publicados.  
 
    > [!IMPORTANT]
    > Se você remove um relatório e atualiza o aplicativo, mesmo se você adicionar o relatório de volta para o aplicativo, os consumidores perder todas as personalizações como indicadores, comentários, etc.  
 
3. Volte para a lista de espaço de trabalho do aplicativo de conteúdo e selecione **atualizar aplicativo** no canto superior direito.
   
1. Atualização **instalação**, **navegação**, e **permissões**, se necessário, e selecione **atualizar aplicativo**.
   
As pessoas para as quais você publicou o aplicativo verão automaticamente a versão atualizada do aplicativo. 

## <a name="design-the-navigation-experience-for-your-app"></a>A experiência de navegação para seu aplicativo de design
O **novo construtor de navegação** opção permite que você crie uma navegação personalizada para seu aplicativo. A navegação personalizada torna mais fácil para seus usuários localizar e usar o conteúdo no aplicativo. Aplicativos existentes têm essa opção seja desativado e o novo padrão de aplicativos para a opção ligada.

Quando a opção está desativada, você pode selecionar o **página de aterrissagem do aplicativo** seja **conteúdo específico**, por exemplo, um painel ou relatório ou selecione **None** para mostrar uma lista básica de conteúdo para o usuário.

Quando você ligar **novo construtor de navegação**, você pode criar uma navegação personalizada. Por padrão, todos os painéis, relatórios e pastas de trabalho do Excel incluídos em seu aplicativo são listadas como uma lista plana. 

![Navegação do aplicativo](media/service-create-distribute-apps/power-bi-apps-navigation.png)

Você pode personalizar ainda mais a navegação do aplicativo por:
* Reordenação de itens usando cima / para baixo setas. 
* Renomear itens na **reportar os detalhes**, **detalhes do painel**, e **detalhes da pasta de trabalho**.
* Ocultar determinados itens do painel de navegação.
* Usando o **New** permite que você adicione **seções** ao grupo de conteúdo relacionado.
* Usando o **New** opção de adicionar um **link** para um recurso externo para o painel de navegação esquerdo. 

Quando você adiciona uma **link**, na **Link detalhes** você pode escolher em que o link é aberto. Por padrão links são abertos na **guia atual**, mas você pode selecionar **nova guia**, ou **área de conteúdo**. 

### <a name="considerations-for-using-the-new-navigation-builder-option"></a>Considerações para usar a nova opção de construtor de navegação
Aqui estão as opções gerais para ter em mente ao usar o novo construtor de navegação:
* As páginas do relatório são mostradas na área de navegação do aplicativo como uma seção expansível
* Se você desativar o novo construtor de navegação e, em seguida, publica ou atualizar seu aplicativo, você perderá as personalizações que você fez. Por exemplo, seções, ordenação, links e nomes personalizados para itens de navegação são todos perdidos.

Ao adicionar links a navegação de seu aplicativo e selecionando a opção de área de conteúdo:
* Certifique-se de que o link pode ser inserido. Alguns serviços bloqueiam a inserção de seu conteúdo em sites de terceiros como o Power BI.
* Inserir conteúdo do serviço do Power BI, como relatórios ou painéis em outros espaços de trabalho não é suportado. 
* Inserir o servidor de relatório do Power BI conteúdo por meio de seu nativo inserir o conteúdo da URL de uma implantação local. Use as etapas em [criando a URL de servidor de relatório do Power BI](https://docs.microsoft.com/power-bi/report-server/quickstart-embed#creating-the-power-bi-report-server-report-url) para obter a URL. Lembre-se de que se aplicam a regras de autenticação regular, portanto, exibir o conteúdo requer uma conexão de VPN para o servidor local. 
* Um aviso de segurança é mostrado na parte superior do conteúdo incorporado para indicar que o conteúdo não estiver no Power BI.



## <a name="automatically-install-apps-for-end-users"></a>Instalar aplicativos automaticamente para usuários finais
Se um administrador lhe dá permissões, você pode instalar aplicativos automaticamente, *enviando por push* -los para os usuários finais. Essa funcionalidade de envio por push torna mais fácil de distribuir os aplicativos certos para as pessoas ou grupos certos. Seu aplicativo é exibida automaticamente na lista de conteúdo de aplicativos de seus usuários finais. Eles não precisarão encontrá-lo no Microsoft AppSource ou seguir um link de instalação. Veja como permitem que os administradores [enviar aplicativos por push aos usuários finais](service-admin-portal.md#push-apps-to-end-users) no artigo de portal de administração do Power BI.

### <a name="how-to-push-an-app-automatically-to-end-users"></a>Como enviar por push um aplicativo automaticamente para os usuários finais
Depois que o administrador tiver atribuído permissões a você, você terá uma nova opção para **instalar o aplicativo automaticamente**. Quando você marcar a caixa e selecione **aplicativo de publicação** (ou **atualizar aplicativo**), o aplicativo é enviado por push a todos os usuários ou grupos definidos no **permissões** seção do aplicativo em que o **Acesso** guia.

![Habilitar envio de aplicativos por push](media/service-create-distribute-apps//power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-you-push-to-them"></a>Como os usuários obtêm os aplicativos que você enviar por push a eles
Depois que você enviar um aplicativo, ele aparece em sua lista de aplicativos automaticamente. Dessa forma, você pode coletar os aplicativos que usuários específicos ou funções de trabalho em sua organização necessitam para ter na ponta dos dedos.

![Habilitar envio de aplicativos por push](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Considerações para instalar aplicativos automaticamente
Aqui estão algumas coisas para se ter em mente ao enviar aplicativos por push para usuários finais:

* Instalar um aplicativo automaticamente para usuários pode levar tempo. A maioria dos aplicativos de instalação imediatamente para os usuários, mas aplicativos por push pode levar tempo.  Isso depende do número de itens no aplicativo e do número de pessoas que receberam acesso. É recomendável enviar aplicativos por push durante horas vagas em que haja muito tempo antes de os usuários precisarem deles. Verifique com vários usuários antes de enviar comunicação abrangentes sobre a disponibilidade de aplicativos.

* Atualize o navegador. Antes de ver o aplicativo enviado por push na Lista de aplicativos, talvez o usuário precise atualizar ou fechar e reabrir seu navegador.

* Se os usuários não vir imediatamente o aplicativo na lista de aplicativos, deve atualizar ou fechar e reabrir seu navegador.

* Tente não sobrecarregar os usuários. Tenha cuidado para não enviar muitos aplicativos por push para que seus usuários entendam que os aplicativos pré-instalados são úteis para eles. É melhor controlar quem pode enviar aplicativos por push para os usuários finais para coordenar o tempo. Estabelecer um ponto de contato para obter aplicativos em sua organização enviados por push para usuários finais.

* Usuários convidados que ainda não aceitaram um convite não obtém aplicativos automaticamente instalados para eles.  

## <a name="unpublish-an-app"></a>Cancelar a publicação de um aplicativo
Qualquer membro de um workspace do aplicativo pode cancelar a publicação do aplicativo.

>[!IMPORTANT]
>Quando você cancela a publicação de um aplicativo, os usuários do aplicativo perdem as personalizações. Perderá quaisquer indicadores pessoas, comentários ou assinaturas associadas ao conteúdo no aplicativo. Só cancele a publicação de um aplicativo se você precisar removê-la.
> 
> 

* No workspace do aplicativo, selecione as reticências ( **...** ) no canto superior direito &gt; **Cancelar a publicação do aplicativo**.
  
     ![Cancelar a publicação do aplicativo](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Essa ação desinstala o aplicativo em todos para os quais você o distribuiu e eles não terão mais acesso ao aplicativo. Ela não exclui o workspace do aplicativo ou seu conteúdo.

## <a name="view-your-published-app"></a>Exibir o aplicativo publicado

Quando os consumidores abrir seu aplicativo, eles veem a navegação que você criou, em vez do painel de navegação à esquerda do Power BI standard. A navegação do aplicativo lista os relatórios e dashboards nas seções que você definiu. Ela também lista as páginas individuais em cada relatório, em vez disso, que apenas o nome do relatório.

![Aplicativo com navegação](media/service-create-distribute-apps/power-bi-new-apps-navigation.png)

## <a name="next-steps"></a>Próximas etapas
* [Criar um workspace de aplicativo](service-create-workspaces.md)
* [Instalar e usar aplicativos no Power BI](consumer/end-user-apps.md)
* [Aplicativos do Power BI para serviços externos](service-connect-to-services.md)
* [Portal de administração do Power BI](https://docs.microsoft.com/power-bi/service-admin-portal)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
