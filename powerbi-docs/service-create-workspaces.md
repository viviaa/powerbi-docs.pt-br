---
title: Criar espaços de trabalho com seus colegas no Power BI
description: Saiba como criar espaços de trabalho, coleções de dashboards e relatórios criados para oferecer métricas-chave para sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/06/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 9a22889da87af91f3b5ea996961ec9e9538fe31b
ms.sourcegitcommit: 52ac456bf2ac025b22ea634c28482f22e1cc19ac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2018
ms.locfileid: "48909097"
---
# <a name="create-workspaces-with-your-colleagues-in-power-bi"></a>Criar espaços de trabalho com seus colegas no Power BI

No Power BI, é possível criar *espaços de trabalho*, lugares para colaborar com colegas para criar e refinar coleções de dashboards e de relatórios. Em seguida, agrupe-os em *aplicativos* que podem ser distribuídos para toda a sua organização ou para pessoas ou grupos específicos. 

![Aplicativos do Power BI](media/service-create-workspaces/power-bi-apps-left-nav.png)

Quando você cria um espaço de trabalho, você está criando um grupo do Office 365 associado e subjacente. Toda a administração do espaço de trabalho está no Office 365. Você pode adicionar colegas a esses espaços de trabalho como membros ou administradores. No espaço de trabalho, todos podem colaborar em dashboards, relatórios e outros artigos que queiram distribuir para um público maior. Todos que você adicionar a um espaço de trabalho de aplicativo precisam de uma licença do Power BI Pro. 

**Você sabia?** O Power BI está com uma nova experiência de espaço de trabalho em versão prévia. Leia [Criar os novos espaços de trabalho (versão prévia)](service-create-the-new-workspaces.md) para ver como os espaços de trabalho mudarão no futuro. 

## <a name="video-apps-and-app-workspaces"></a>Vídeo: Aplicativos e espaços de trabalho de aplicativo
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="create-an-app-workspace-based-on-an-office-365-group"></a>Criar um espaço de trabalho de aplicativo com base em um grupo do Office 365

Quando você cria um espaço de trabalho de aplicativo, ele é criado em um grupo do Office 365.

[!INCLUDE [powerbi-service-create-app-workspace](./includes/powerbi-service-create-app-workspace.md)]

Ao criá-lo pela primeira vez, talvez seja necessário aguardar uma hora ou mais para que o espaço de trabalho seja propagado para o Office 365. 

### <a name="add-an-image-to-your-office-365-app-workspace-optional"></a>Adicionar uma imagem ao seu espaço de trabalho de aplicativo do Office 365 (opcional)
Por padrão, o Power BI cria um pequeno círculo colorido com as iniciais do seu aplicativo. Mas talvez você queira personalizá-lo com uma imagem. Para adicionar uma imagem, você precisa de uma licença do Exchange Online.

1. Selecione **Espaços de Trabalho**, selecione as reticências (...) ao lado do nome do espaço de trabalho e, em seguida, **Membros**. 
   
     ![Selecionar Membros do Espaço de Trabalho](media/service-create-distribute-apps/power-bi-apps-workspace-members.png)
   
    A conta do Office 365 Outlook do espaço de trabalho é aberta em uma nova janela do navegador.
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

## <a name="add-content-to-your-app-workspace"></a>Adicionar conteúdo ao seu espaço de trabalho de aplicativo

Após criar um espaço de trabalho de aplicativo, será hora de adicionar conteúdo a ele. É tão simples quanto adicionar conteúdo ao Meu espaço de trabalho, exceto que outras pessoas também podem ver e trabalhar no espaço de trabalho. Uma grande diferença é que, quando terminar, você poderá publicar o conteúdo como um aplicativo. Quando você exibe conteúdo na lista de conteúdo de um espaço de trabalho de aplicativo, o nome do espaço de trabalho de aplicativo é listado como o proprietário.

### <a name="connect-to-third-party-services-in-app-workspaces"></a>Conectar-se a serviços de terceiros em espaços de trabalho de aplicativo

Os aplicativos são fornecidos para todos os serviços de terceiros com os quais o Power BI é compatível, tornando fácil para você obter dados dos serviços usados, como o Microsoft Dynamics CRM, Salesforce ou Google Analytics. É possível publicar aplicativos organizacionais para dar aos seus usuários os dados de que precisam.

Nos espaços de trabalho atuais, também é possível conectar usando pacotes de conteúdo organizacional e pacotes de conteúdo de terceiros, como o Microsoft Dynamics CRM, Salesforce ou Google Analytics. Considere migrar seus pacotes de conteúdo organizacional para aplicativos.

## <a name="distribute-an-app"></a>Distribuir um aplicativo

Quando o conteúdo estiver pronto, escolha quais dashboards e relatórios você deseja publicar e, em seguida, publique-o como um *aplicativo*. Seus colegas podem obter seus aplicativos de diferentes maneiras. Você poderá instalá-los automaticamente nas contas do Power BI dos seus colegas se o administrador do Power BI der permissão. Caso contrário, eles podem localizar e instalar seus aplicativos no Microsoft AppSource ou você pode enviar um link direto. Eles recebem atualizações automaticamente e você pode controlar a frequência com que os dados são atualizados. Consulte [Publicar aplicativos com dashboards e relatórios no Power BI](service-create-distribute-apps.md) para obter detalhes.

## <a name="power-bi-apps-faq"></a>Perguntas frequentes sobre os aplicativos do Power BI

### <a name="how-are-apps-different-from-organizational-content-packs"></a>Qual a diferença entre os aplicativos e os pacotes de conteúdo organizacional?
Os aplicativos são a evolução dos pacotes de conteúdo organizacional. Se você já tem pacotes de conteúdo organizacional, eles continuarão a funcionar lado a lado com os aplicativos. Aplicativos e pacotes de conteúdo têm poucas diferenças importantes. 

* Depois que os usuários corporativos instalam um pacote de conteúdo, ele perde sua identidade agrupada: transforma-se apenas em uma lista de dashboards e relatórios intercalados com outros dashboards e relatórios. Os aplicativos, por outro lado, mantêm o agrupamento e a identidade, mesmo após a instalação. Isso facilita para que os usuários corporativos continuem a acessá-los ao longo do tempo.
* Você pode criar vários pacotes de conteúdo de qualquer espaço de trabalho, mas um aplicativo tem uma relação de 1:1 com seu espaço de trabalho. 
* Ao longo do tempo, pretendemos descontinuar os pacotes de conteúdo organizacional, portanto, é recomendável que você crie aplicativos de agora em diante.  
* Com a nova versão prévia de experiência de espaço de trabalho, seguiremos as primeiras etapas para preterir os pacotes de conteúdo organizacional. Não é possível consumi-los ou criá-los nos espaços de trabalho de versão prévia.

Consulte [How are the new app workspaces different from existing app workspaces?](service-create-the-new-workspaces.md#how-are-the-new-app-workspaces-different-from-current-app-workspaces) (Como os novos espaços de trabalho de aplicativo são diferentes dos espaços de trabalho de aplicativo existentes?) para comparar os espaços de trabalho de aplicativo atuais e novos. 

## <a name="next-steps"></a>Próximas etapas
* [Instalar e usar aplicativos no Power BI](service-create-distribute-apps.md)
- [Criar os novos espaços de trabalho (versão prévia)](service-create-the-new-workspaces.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
