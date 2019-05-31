---
title: Criar espaços de trabalho clássicos no Power BI
description: Saiba como criar espaços de trabalho, coleções de dashboards, relatórios e relatórios paginados criados para fornecer métricas importantes para sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/18/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: dcf9b8befabfec98fcae154e6276f8e698b3ddc2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61150735"
---
# <a name="create-classic-workspaces-in-power-bi"></a>Criar espaços de trabalho clássicos no Power BI

No Power BI, você pode criar *espaços de trabalho*, coloca para colaborar com colegas para criar e refinar as coleções de dashboards, relatórios e relatórios paginados. Em seguida, você pode agrupar a coleção em *aplicativos* que você pode distribuir para toda a organização ou para pessoas ou grupos específicos. 

**Você sabia?** Power BI oferece uma nova experiência de espaço de trabalho, que agora é o padrão. Leia [organizar o trabalho em espaços de trabalho novo](service-new-workspaces.md) para obter detalhes sobre os novos espaços de trabalho. 

Quando você cria um espaço de trabalho clássico, você está criando um grupo do Office 365 subjacente, associado. Toda a administração do espaço de trabalho é feita no Office 365. Você pode adicionar colegas a esses workspaces como membros ou administradores. No workspace, todos podem colaborar em dashboards, relatórios e outros artigos que você planeja distribuir para um público-alvo maior. Todos que você adicionar a um workspace de aplicativo precisam de uma licença do Power BI Pro. 

## <a name="video-apps-and-app-workspaces"></a>Vídeo: Aplicativos e workspaces de aplicativo
<iframe width="640" height="360" src="https://www.youtube.com/embed/Ey5pyrr7Lk8?showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="create-a-classic-app-workspace-based-on-an-office-365-group"></a>Criar um espaço de trabalho do aplicativo clássico com base em um grupo do Office 365

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

     Imagens podem ser arquivos. bmp,. jpg ou. PNG. Tamanho do arquivo pode ser grande, backup para 3 MB. 

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

Nos workspaces atuais, também é possível conectar usando pacotes de conteúdo organizacional e pacotes de conteúdo de terceiros, como o Microsoft Dynamics CRM, o Salesforce ou o Google Analytics. Considere migrar seus pacotes de conteúdo organizacional para aplicativos.

## <a name="distribute-an-app"></a>Distribuir um aplicativo

Se você quiser distribuir o conteúdo oficial para um grande público dentro de sua organização, você pode publicar um aplicativo do seu espaço de trabalho.  Quando o conteúdo estiver pronto, escolha quais painéis e relatórios que você deseja publicar e, em seguida, publicá-lo como um *aplicativo*. Você pode criar um aplicativo de cada workspace.

A lista de aplicativos no painel de navegação à esquerda mostra todos os aplicativos que você instalou. Seus colegas podem obter seu aplicativo de algumas maneiras diferentes. 
- Eles podem localizar e instalar seu aplicativo no Microsoft AppSource
- Você pode enviar um link direto. 
- Você poderá instalá-lo automaticamente nas contas do Power BI de seus colegas, se o administrador do Power BI lhe der permissão. 

Os usuários veem o conteúdo de aplicativo atualizado automaticamente depois de publicar uma atualização do espaço de trabalho. Você pode controlar a frequência com que os dados são atualizados, definindo a agenda de atualização nos conjuntos de dados usados pelo conteúdo do aplicativo em seu espaço de trabalho. Ver [publicar um aplicativo de novos espaços de trabalho no Power BI](service-create-distribute-apps.md) para obter detalhes.

## <a name="power-bi-classic-apps-faq"></a>Aplicativos do Power BI clássicos perguntas Frequentes

### <a name="how-are-apps-different-from-organizational-content-packs"></a>Qual a diferença entre os aplicativos e os pacotes de conteúdo organizacional?
Os aplicativos são a evolução dos pacotes de conteúdo organizacional. Se você já tem pacotes de conteúdo organizacional, eles continuarão a funcionar lado a lado com os aplicativos. Aplicativos e pacotes de conteúdo têm poucas diferenças importantes. 

* Depois que os usuários corporativos instalam um pacote de conteúdo, ele perde sua identidade agrupada: transforma-se apenas em uma lista de dashboards e relatórios intercalados com outros dashboards e relatórios. Os aplicativos, por outro lado, mantêm o agrupamento e a identidade, mesmo após a instalação. Esse agrupamento facilita o acesso a eles ao longo do tempo para os usuários empresariais.
* Você pode criar vários pacotes de conteúdo de qualquer workspace, mas um aplicativo tem uma relação de 1:1 com seu workspace. 
* Ao longo do tempo, pretendemos descontinuar os pacotes de conteúdo organizacional, portanto, é recomendável que você crie aplicativos de agora em diante.  
* Com a versão prévia da nova experiência de workspace, estamos dando os primeiros passos para preterir os pacotes de conteúdo organizacional. Não é possível consumi-los ou criá-los nos workspaces de versão prévia.

Confira [Em que aspectos os novos workspaces de aplicativo são diferentes dos workspaces existentes?](service-new-workspaces.md#how-are-the-new-workspaces-different-from-current-workspaces) para comparar os dois. 

## <a name="next-steps"></a>Próximas etapas
* [Instalar e usar aplicativos no Power BI](service-create-distribute-apps.md)
- [Criar os novos workspaces (versão prévia)](service-create-the-new-workspaces.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
