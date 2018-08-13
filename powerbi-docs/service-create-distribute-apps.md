---
title: Publicar aplicativos com dashboards e relatórios no Power BI
description: Saiba como publicar aplicativos, que são coleções de dashboards e relatórios criados para fornecer métricas-chave à sua organização.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 18189948e0873824feea781d2b6b6523bc968592
ms.sourcegitcommit: 2356dc8e5488438a43ba7f0ba9a55a2372669b47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39624127"
---
# <a name="publish-apps-with-dashboards-and-reports-in-power-bi"></a>Publicar aplicativos com dashboards e relatórios no Power BI

No Power BI, é possível publicar *aplicativos* com coleções de dashboards e relatórios relacionados. Crie aplicativos nos *espaços de trabalho do aplicativo*, em que é possível colaborar no conteúdo do Power BI com seus colegas. Em seguida, é possível publicar os aplicativos concluídos em grandes grupos de pessoas em sua organização. Leia mais sobre [como criar espaços de trabalho do aplicativo](service-create-workspaces.md).

![Aplicativos do Power BI](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

Os usuários empresariais geralmente precisam de vários dashboards e relatórios do Power BI para administrar os negócios. Com os aplicativos do Power BI, crie coleções de dashboards e relatórios e publique esses aplicativos para toda a organização ou para pessoas ou grupos específicos. Para você, como administrador ou criador de relatórios, os aplicativos facilitam o gerenciamento de permissões nessas coleções.

Usuários de negócios obtêm seus aplicativos de algumas maneiras diferentes. Se o administrador do Power BI der permissão, você poderá instalar os aplicativos automaticamente nas contas do Power BI dos seus colegas. Caso contrário, eles podem instalar seus aplicativos no Microsoft AppSource, ou você pode enviar um link direto. Eles podem facilmente localizar e retornar ao seu conteúdo, porque ele estará em um só lugar. Eles não podem modificar o conteúdo do aplicativo, mas podem interagir com ele no serviço do Power BI ou em um dos aplicativos móveis, filtrando, realçando e classificando os dados. Eles recebem atualizações automaticamente e você pode controlar a frequência com que os dados são atualizados. Leia mais sobre a [experiência de aplicativo para usuários corporativos](service-install-use-apps.md).

**Você sabia?** O Power BI está com uma nova experiência de espaço de trabalho em versão prévia. Leia [Criar os novos espaços de trabalho (versão prévia)](service-create-the-new-workspaces.md) para ver como os espaços de trabalho mudarão no futuro. 

## <a name="apps-and-organizational-content-packs"></a>Aplicativos e pacotes de conteúdo organizacional
Os aplicativos são a evolução dos pacotes de conteúdo organizacional. Os pacotes de conteúdo não estão disponíveis na nova versão prévia de experiências de espaço de trabalho. Após a nova experiência de espaço de trabalho ficar disponível para o público geral, não será possível usar pacotes de conteúdo em espaços de trabalho recém-criados. Se você ainda não fez isso, comece a migrar seus pacotes de conteúdo para aplicativos.

## <a name="video-apps-and-app-workspaces"></a>Vídeo: Aplicativos e espaços de trabalho de aplicativo
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="licenses-for-apps"></a>Licenças para aplicativos
Cada membro de um espaço de trabalho de aplicativo precisa de uma licença do Power BI Pro. Para os usuários do aplicativo, há duas opções.

* Opção 1: todos os usuários empresariais precisam de licenças do **Power BI Pro** para exibir seu aplicativo. 
* Opção 2: se seu aplicativo residir em uma capacidade Premium do Power BI, os usuários gratuitos em sua organização poderão exibir o conteúdo do aplicativo. Leia [O que é o Power BI Premium?](service-premium.md) para obter detalhes.

## <a name="publish-your-app"></a>Publicar seu aplicativo
Quando os dashboards e relatórios em seu espaço de trabalho estiverem prontos, escolha quais dashboards e relatórios você deseja publicar e publique-os como um aplicativo. Você pode enviar um link direto para esse público mais amplo ou eles podem encontrar seu aplicativo na guia Aplicativos acessando **Baixar e explorar mais aplicativos no AppSource**. 

1. Na exibição da lista no espaço de trabalho, decida quais dashboards e relatórios você quer incluir no aplicativo.

     ![Selecionar o dashboard a ser publicado](media/service-create-distribute-apps/power-bi-apps-incude-dashboard.png)

     Se você optar por não publicar um relatório, verá um aviso ao lado do relatório e seu dashboard relacionado. Você ainda pode publicar o aplicativo, mas no dashboard relacionado faltarão blocos do relatório.

     ![Aviso sobre dashboard relacionado](media/service-create-distribute-apps/power-bi-apps-report-warning.png)

2. Selecione o botão **Publicar aplicativo** no canto superior direito para iniciar o processo de compartilhamento de todo o conteúdo desse espaço de trabalho.
   
     ![Publicar aplicativo](media/service-create-distribute-apps/power-bi-apps-publish-button.png)

3. Em **Detalhes**, preencha a descrição para ajudar as pessoas a localizar o aplicativo. Você pode definir uma cor da tela de fundo para personalizá-la.
   
     ![Detalhes do aplicativo](media/service-create-distribute-apps/power-bi-apps-details.png)

4. Em **Conteúdo**, você vê o conteúdo que será publicado como parte do aplicativo, ou seja, tudo o que você selecionou nesse espaço de trabalho. Você também pode definir a página de aterrissagem do aplicativo – que é o dashboard ou relatório que as pessoas verão primeiro ao acessarem o aplicativo. Você pode escolher **Nenhuma**. Então, as pessoas entrarão em uma lista de todo o conteúdo do aplicativo. 
   
     ![Conteúdo do aplicativo](media/service-create-distribute-apps/power-bi-apps-content.png)

5. Em **Acesso**, decida quem tem acesso ao aplicativo: todos em sua organização, pessoas específicas, grupos de segurança do Active Directory. Se você tiver permissões, instale o aplicativo automaticamente para os destinatários. É possível habilitar essa configuração no [Portal de Administração do Power BI](#how-to-enable-pushing-apps). É possível saber mais considerações para [enviar um aplicativo por push](#how-to-enable-pushing-apps).

    ![Acesso ao aplicativo](media/service-create-distribute-apps/power-bi-apps-access.png)

6. Ao selecionar **Concluir**, você verá uma mensagem confirmando que ele está pronto para publicar. Na caixa de diálogo de êxito, você pode copiar a URL, que é um link direto para esse aplicativo e enviá-la para as pessoas com as quais você compartilhou.
   
     ![Término do aplicativo](media/service-create-distribute-apps/power-bi-apps-success.png)

Leia mais sobre a [experiência de aplicativo para usuários corporativos](service-install-use-apps.md).

## <a name="change-your-published-app"></a>Alterar o aplicativo publicado
Depois de publicar seu aplicativo, você talvez queira alterá-lo ou atualizá-lo. Será fácil atualizá-lo se você for administrador ou membro do espaço de trabalho de aplicativo ou um colaborador em um novo espaço de trabalho de aplicativo. 

1. Abra o espaço de trabalho de aplicativo que corresponde ao aplicativo. 
   
     ![Abrir espaço de trabalho](media/service-create-distribute-apps/power-bi-apps-open-workspace.png)
2. Abra o dashboard ou o relatório. Você percebe que agora pode fazer as alterações que desejar.
   
     O espaço de trabalho de aplicativo é sua área de preparo, portanto, suas alterações não entrarão em vigor no aplicativo até que você publique novamente. Isso permite que você faça alterações sem afetar os aplicativos publicados.  
 
3. Volte para a lista de conteúdo do espaço de trabalho do aplicativo e selecione **Atualizar aplicativo**.
   
     ![Botão Atualizar aplicativo](media/service-create-distribute-apps/power-bi-app-update-button.png)

4. Atualize **Detalhes**, **Conteúdo** e **Acesso**, se necessário, e selecione **Atualizar aplicativo**.
   
     ![Botão Atualizar aplicativo](media/service-create-distribute-apps/power-bi-app-update-complete.png)

As pessoas para as quais você publicou o aplicativo verão automaticamente a versão atualizada do aplicativo. 

## <a name="automatically-install-apps-for-end-users"></a>Instalar aplicativos automaticamente para usuários finais
Os aplicativos entregam dados de que seus usuários finais precisam para realizar seus trabalhos. Se um administrador der permissões, você poderá instalar automaticamente aplicativos para usuários finais, facilitando a distribuição dos aplicativos certos para as pessoas ou grupos certos. Seu aplicativo será exibido automaticamente na lista de conteúdo de aplicativos dos seus usuários finais. Eles não precisarão localizá-lo no Microsoft AppSource ne seguir um link de instalação. Isso torna mais fácil para você distribuir conteúdo padrão do Power BI para seus usuários.

### <a name="how-to-install-an-app-automatically-for-end-users"></a>Como instalar um aplicativo automaticamente para usuários finais
Depois que o administrador tiver atribuído permissões a você, você terá uma nova opção para **instalar o aplicativo automaticamente**. Quando você marcar a caixa e selecionar **Concluir** (ou **Atualizar aplicativo**, para aplicativos existentes), o aplicativo será enviado por push a todos os usuários ou grupos definidos na seção **Permissões** do aplicativo na guia **Acesso**.

![Habilitar envio de aplicativos por push](media/service-create-distribute-apps/power-bi-apps-access.png)

### <a name="how-users-get-the-apps-that-were-pushed-to-them"></a>Como os usuários obtêm os aplicativos que foram enviados por push a eles
Depois de enviar um aplicativo por push, ele será exibido na Lista de aplicativos automaticamente. É possível coletar os aplicativos que usuários ou funções de trabalho específicos em sua organização precisam ter na ponta dos dedos.

![Habilitar envio de aplicativos por push](media/service-create-distribute-apps/power-bi-apps-left-nav.png)

### <a name="considerations-for-automatically-installing-apps"></a>Considerações para instalar aplicativos automaticamente
Aqui estão algumas coisas para se ter em mente ao enviar aplicativos por push para usuários finais:

* Instalar um aplicativo automaticamente para usuários pode levar tempo. A maioria dos aplicativos será instalada imediatamente para usuários, mas enviar aplicativos por push pode levar tempo.  Isso depende do número de itens no aplicativo e do número de pessoas que receberam acesso. É recomendável enviar aplicativos por push durante horas vagas em que haja muito tempo antes de os usuários precisarem deles. Verifique com vários usuários antes de enviar comunicação abrangentes sobre a disponibilidade de aplicativos.

* Atualize seu navegador. Antes de ver o aplicativo enviado por push na Lista de aplicativos, talvez o usuário precise atualizar ou fechar e reabrir seu navegador.

* Se o usuário não vir imediatamente o aplicativo na Lista de aplicativos, ele deverá atualizar ou fechar e reabrir seu navegador.

* Tente não sobrecarregar os usuários. Tenha cuidado para não enviar muitos aplicativos por push para que seus usuários entendam que os aplicativos pré-instalados são úteis para eles. É melhor controlar quem pode enviar aplicativos por push para os usuários finais para coordenar o tempo. É possível estabelecer um ponto de contato para obter aplicativos em sua organização enviados por push para usuários finais.

* Os aplicativos não serão instalados automaticamente para os usuários convidados que não aceitarem um convite.  

## <a name="unpublish-an-app"></a>Cancelar a publicação de um aplicativo
Qualquer membro de um espaço de trabalho do aplicativo pode cancelar a publicação do aplicativo.

* No espaço de trabalho do aplicativo, selecione as reticências (**...**) no canto superior direito > **Cancelar a publicação do aplicativo**.
  
     ![Cancelar a publicação do aplicativo](media/service-create-distribute-apps/power-bi-app-unpublish.png)

Essa ação desinstala o aplicativo em todos para os quais você o distribuiu e eles não terão mais acesso ao aplicativo. Ela não exclui o espaço de trabalho do aplicativo ou seu conteúdo.

## <a name="next-steps"></a>Próximas etapas
* [Criar um espaço de trabalho de aplicativo](service-create-workspaces.md)
* [Instalar e usar aplicativos no Power BI](service-install-use-apps.md)
* [Aplicativos do Power BI para serviços externos](service-connect-to-services.md)
* [Portal de administração do Power BI](https://docs.microsoft.com/power-bi/service-admin-portal)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
