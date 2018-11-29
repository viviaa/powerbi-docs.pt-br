---
title: Criar workspaces com seus colegas no Power BI
description: Saiba como criar workspaces, coleções de dashboards e relatórios criados para oferecer métricas-chave para sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: f12974d4e53217fc6c29ad172153ec9c51ecc44e
ms.sourcegitcommit: fdb54145f9bc93b312409c15c603749f3a4a876e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52452627"
---
# <a name="create-workspaces-with-your-colleagues-in-power-bi"></a>Criar workspaces com seus colegas no Power BI

No Power BI, é possível criar *workspaces*, lugares para colaborar com colegas para criar e refinar coleções de dashboards e de relatórios. Em seguida, agrupe-os em *aplicativos* que podem ser distribuídos para toda a sua organização ou para pessoas ou grupos específicos. 

![Aplicativos do Power BI](media/service-create-workspaces/power-bi-apps-left-nav.png)

Quando você cria um workspace, você está criando um grupo do Office 365 associado e subjacente. Toda a administração do espaço de trabalho é feita no Office 365. Você pode adicionar colegas a esses workspaces como membros ou administradores. No workspace, todos podem colaborar em dashboards, relatórios e outros artigos que queiram distribuir para um público maior. Todos que você adicionar a um workspace de aplicativo precisam de uma licença do Power BI Pro. 

**Você sabia?** O Power BI está com uma nova experiência de workspace em versão prévia. Leia [Criar os novos workspaces (versão prévia)](service-create-the-new-workspaces.md) para ver como os workspaces mudarão no futuro. 

## <a name="video-apps-and-app-workspaces"></a>Vídeo: Aplicativos e workspaces de aplicativo
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="create-an-app-workspace-based-on-an-office-365-group"></a>Criar um workspace de aplicativo com base em um grupo do Office 365

Quando você cria um workspace de aplicativo, ele é criado em um grupo do Office 365.

[!INCLUDE [powerbi-service-create-app-workspace](./includes/powerbi-service-create-app-workspace.md)]

Ao criá-lo pela primeira vez, talvez seja necessário aguardar uma hora ou mais para que o workspace seja propagado para o Office 365. 

### <a name="add-an-image-to-your-office-365-app-workspace-optional"></a>Adicionar uma imagem ao seu workspace de aplicativo do Office 365 (opcional)
Por padrão, o Power BI cria um pequeno círculo colorido com as iniciais do seu aplicativo. Mas talvez você queira personalizá-lo com uma imagem. Para adicionar uma imagem, você precisa de uma licença do Exchange Online.

1. Selecione **Workspaces**, selecione as reticências (...) ao lado do nome do workspace e, em seguida, **Membros**. 
   
     ![Selecionar Membros do Workspace](media/service-create-distribute-apps/power-bi-apps-workspace-members.png)
   
    A conta do Office 365 Outlook do workspace é aberta em uma nova janela do navegador.
2. Quando você focaliza sobre o círculo colorido na parte superior esquerda, ele se transforma em um ícone de lápis. Selecione-a.
   
     ![Ícone de lápis do Office 365](media/service-create-distribute-apps/power-bi-apps-workspace-edit-image.png)
3. Selecione o ícone de lápis novamente e localize a imagem que você deseja usar.
   
     ![Selecionar o lápis novamente](media/service-create-distribute-apps/power-bi-apps-workspace-edit-group.png)

4. Selecione **Salvar**.
   
     ![Selecionar Salvar](media/service-create-distribute-apps/power-bi-apps-workspace-save-image.png)
   
    A imagem substitui o círculo colorido na janela do Office 365 Outlook. 
   
     ![Imagem personalizada](media/service-create-distribute-apps/power-bi-apps-workspace-image-in-office-365.png)
   
    Em alguns minutos, ela também será exibida no aplicativo do Power BI.
   
     ![Imagem personalizada](media/service-create-distribute-apps/power-bi-apps-image.png)

## <a name="add-content-to-your-app-workspace"></a>Adicionar conteúdo ao seu workspace de aplicativo

Após criar um workspace de aplicativo, será hora de adicionar conteúdo a ele. É tão simples quanto adicionar conteúdo ao Meu workspace, exceto que outras pessoas também podem ver e trabalhar no workspace. Uma grande diferença é que, quando terminar, você poderá publicar o conteúdo como um aplicativo. Quando você exibe conteúdo na lista de conteúdo de um workspace de aplicativo, o nome do workspace de aplicativo é listado como o proprietário.

### <a name="connect-to-third-party-services-in-app-workspaces"></a>Conectar-se a serviços de terceiros em workspaces de aplicativo

Os aplicativos são fornecidos para todos os serviços de terceiros com os quais o Power BI é compatível, tornando fácil para você obter dados dos serviços usados, como o Microsoft Dynamics CRM, Salesforce ou Google Analytics. É possível publicar aplicativos organizacionais para dar aos seus usuários os dados de que precisam.

Nos workspaces atuais, também é possível conectar usando pacotes de conteúdo organizacional e pacotes de conteúdo de terceiros, como o Microsoft Dynamics CRM, Salesforce ou Google Analytics. Considere migrar seus pacotes de conteúdo organizacional para aplicativos.

## <a name="distribute-an-app"></a>Distribuir um aplicativo

Quando o conteúdo estiver pronto, escolha quais dashboards e relatórios você deseja publicar e, em seguida, publique-o como um *aplicativo*. Seus colegas podem obter seus aplicativos de diferentes maneiras. Você poderá instalá-los automaticamente nas contas do Power BI dos seus colegas se o administrador do Power BI der permissão. Caso contrário, eles podem localizar e instalar seus aplicativos no Microsoft AppSource ou você pode enviar um link direto. Eles recebem atualizações automaticamente e você pode controlar a frequência com que os dados são atualizados. Consulte [Publicar aplicativos com dashboards e relatórios no Power BI](service-create-distribute-apps.md) para obter detalhes.

## <a name="power-bi-apps-faq"></a>Perguntas frequentes sobre os aplicativos do Power BI

### <a name="how-are-apps-different-from-organizational-content-packs"></a>Qual a diferença entre os aplicativos e os pacotes de conteúdo organizacional?
Os aplicativos são a evolução dos pacotes de conteúdo organizacional. Se você já tem pacotes de conteúdo organizacional, eles continuarão a funcionar lado a lado com os aplicativos. Aplicativos e pacotes de conteúdo têm poucas diferenças importantes. 

* Depois que os usuários corporativos instalam um pacote de conteúdo, ele perde sua identidade agrupada: transforma-se apenas em uma lista de dashboards e relatórios intercalados com outros dashboards e relatórios. Os aplicativos, por outro lado, mantêm o agrupamento e a identidade, mesmo após a instalação. Isso facilita para que os usuários corporativos continuem a acessá-los ao longo do tempo.
* Você pode criar vários pacotes de conteúdo de qualquer workspace, mas um aplicativo tem uma relação de 1:1 com seu workspace. 
* Ao longo do tempo, pretendemos descontinuar os pacotes de conteúdo organizacional, portanto, é recomendável que você crie aplicativos de agora em diante.  
* Com a nova versão prévia de experiência de workspace, seguiremos as primeiras etapas para preterir os pacotes de conteúdo organizacional. Não é possível consumi-los ou criá-los nos workspaces de versão prévia.

Consulte [How are the new app workspaces different from existing app workspaces?](service-create-the-new-workspaces.md#how-are-the-new-app-workspaces-different-from-current-app-workspaces) (Como os novos workspaces de aplicativo são diferentes dos workspaces de aplicativo existentes?) para comparar os workspaces de aplicativo atuais e novos. 

## <a name="next-steps"></a>Próximas etapas
* [Instalar e usar aplicativos no Power BI](service-create-distribute-apps.md)
- [Criar os novos workspaces (versão prévia)](service-create-the-new-workspaces.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
