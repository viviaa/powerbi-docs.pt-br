---
title: Criar os novos workspaces (versão prévia) – Power BI
description: Saiba como criar novos workspaces, coleções de dashboards e relatórios criados para oferecer métricas-chave para sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/14/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: cdc406ddd9c086114ca118130bb4973737de3ed1
ms.sourcegitcommit: 1e4fee6d1f4b7803ea285eb879c8d5a4f7ea8b85
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51717885"
---
# <a name="create-the-new-workspaces-preview-in-power-bi"></a>Criar os novos workspaces (versão prévia) no Power BI

O Power BI está apresentando uma nova experiência de workspace como versão prévia. Os workspaces ainda são locais para colaborar com colegas para criar coleções de dashboards e relatórios, que você pode agrupar em *aplicativos* e distribuir para toda a sua organização ou para pessoas ou grupos específicos. 

![Nova versão prévia de workspaces do Power BI](media/service-create-the-new-workspaces/power-bi-new-workspaces-preview.png)

Com a nova versão prévia de workspaces, agora é possível:

- Atribuir funções de workspace a grupos de usuários: grupos de segurança, listas de distribuição, grupos do Office 365 e indivíduos.
- Criar um workspace no Power BI sem criar um grupo do Office 365.
- Usar funções de workspaces mais granulares para obter um gerenciamento de permissões mais flexível em um workspace.
 
Quando você cria um dos novos workspaces, você não está criando um grupo do Office 365 associado e subjacente. Toda a administração do workspace está no Power BI, não no Office 365. Ainda é possível adicionar um grupo do Office 365 ao workspace para continuar gerenciando o acesso do usuário ao conteúdo por meio de grupos do Office 365. No entanto, também é possível usar grupos de segurança e listas de distribuição e adicionar indivíduos diretamente pelo Power BI, dando uma forma flexível de gerenciar o acesso ao workspace. Como agora a administração de workspace está no Power BI, os administradores do Power BI decidem quem em uma organização pode criar workspaces. Saiba mais no [artigo no portal de administração do Power BI, na seção Workspaces](service-admin-portal.md#workspace-settings). 

Adicione grupos de usuários ou indivíduos aos novos workspaces como membros, colaboradores ou administradores. Todos em um grupo de usuários obtêm a função que você definiu. Se um indivíduo estiver em vários grupos de usuário, ele obterá o nível mais alto de permissão fornecido pela função.  Consulte [Roles in the new workspaces](#roles-in-the-new-workspaces) (Funções nos novos workspaces) posteriormente neste artigo para obter uma explicação das diferentes funções.

Todos que você adicionar a um workspace de aplicativo precisam de uma licença do Power BI Pro. No workspace, esses usuários podem colaborar em dashboards e relatórios que você planeja publicar para um público maior ou até mesmo para toda a sua organização. Para distribuir conteúdo a outras pessoas da sua organização, atribua licenças do Power BI Pro a esses usuários ou coloque o workspace em uma capacidade do Power BI Premium.

Com os novos workspaces, estamos recriando alguns recursos. Confira os [recursos do Workspace do aplicativo que funcionam de forma diferente](#app-workspace-features-that-work-differently) posteriormente neste artigo para obter uma explicação das alterações que você pode esperar que se tornem permanentes, juntamente com a versão prévia. Como esse é um recurso de versão prévia, essas são algumas limitações que você deve conhecer. Confira os [Problemas conhecidos](#known-issues) posteriormente neste artigo para obter uma explicação das limitações atuais. 

## <a name="roll-out-new-app-workspaces"></a>Distribuir novos workspaces de aplicativo

Durante o período de versão prévia, workspaces antigos e novos podem coexistir lado a lado, e você pode criar qualquer um deles. Quando a versão prévia para novos workspaces for encerrada e eles estiverem disponíveis para o público geral, workspaces antigos ainda podem existir por um tempo. Não será possível criá-los e será necessário se preparar para migrar seus workspaces para a nova infraestrutura de workspaces. Não se preocupe, você terá vários meses para concluir a migração.

## <a name="create-one-of-the-new-app-workspaces"></a>Criar um dos novos workspaces de aplicativo

1. Comece criando o workspace de aplicativo. Selecione **Workspaces** > **Criar workspace do aplicativo**.
   
     ![Criar workspace do aplicativo](media/service-create-workspaces/power-bi-create-app-workspace.png)

2. Em **Visualizar workspaces aprimorados**, selecione **Experimentar agora**.
   
     ![Visualizar workspaces aprimorados](media/service-create-workspaces/power-bi-preview-improved-workspaces.png)

2. Nomeie o workspace. Se o nome não estiver disponível, edite-o para criar uma ID exclusiva.
   
     O aplicativo terá o mesmo nome que o workspace.
   
1. Adicione uma imagem, se desejar. O tamanho do arquivo deve ter menos de 45 KB.
 
    ![Nomear o workspace e adicionar uma imagem](media/service-create-workspaces/power-bi-name-workspace.png)

1. Selecione **Salvar**.

    Aqui na tela de **boas-vindas** do seu novo workspace, é possível adicionar dados. 

    ![Nova tela de boas-vindas do workspace](media/service-create-workspaces/power-bi-workspace-welcome-screen.png)

1. Por exemplo, selecione **Exemplos** > **Exemplo de rentabilidade do cliente**.

    Agora na lista de conteúdo do workspace, você vê a **Nova versão prévia de workspaces**. Como você é administrador, também vê uma nova ação, **Acessar**.

    ![Lista de conteúdo da versão prévia de workspaces](media/service-create-workspaces/power-bi-workspaces-preview-content-list.png)

1. Selecione **Acessar**.

1. Adicione grupos de segurança, listas de distribuição, grupos do Office 365 ou indivíduos nesses workspaces como membros, colaboradores ou administradores. Consulte [Roles in the new workspaces](#roles-in-the-new-workspaces) (Funções nos novos workspaces) posteriormente neste artigo para obter uma explicação das diferentes funções.

    ![Os workspaces adicionam membros, administradores, colaboradores](media/service-create-workspaces/power-bi-access-add-members.png)

9. Selecione **Adicionar** > **Fechar**.

1. O Power BI cria o workspace e o abre. Ele aparece na lista de workspaces dos quais você é um membro. Como você é um administrador, é possível selecionar as reticências (...) para voltar e fazer alterações nas configurações do workspace, adicionar novos membros ou alterar as permissões deles.

     ![Editar configurações e o acesso para um workspace](media/service-create-workspaces/power-bi-edit-workspace.png)

## <a name="add-content-to-your-app-workspace"></a>Adicionar conteúdo ao seu workspace de aplicativo

Após criar um workspace de aplicativo do novo estilo, será hora de adicionar conteúdo a ele. Adicionar conteúdo é semelhante nos workspaces de estilo novo e antigo, com uma exceção. Enquanto estiver em qualquer um dos workspaces de aplicativo, será possível carregar arquivos ou se conectar a eles, como você faria no seu próprio Meu workspace. Nos novos workspaces, não é possível se conectar a pacotes de conteúdo organizacional ou a pacotes de conteúdo de terceiros como o Microsoft Dynamics CRM, Salesforce ou Google Analytics. Nos workspaces atuais, é possível se conectar a pacotes de conteúdo.

Quando você exibe conteúdo na lista de conteúdo de um workspace de aplicativo, o nome do workspace de aplicativo é listado como o proprietário.

### <a name="connecting-to-third-party-services-in-new-workspaces-preview"></a>Conectando-se aos serviços de terceiros em novos workspaces (versão prévia)

Na nova experiência de workspaces, estamos fazendo uma alteração para nos concentrar em aplicativos. Os aplicativos de serviços de terceiros tornam fácil para os usuários obter dados dos serviços que usam, como o Microsoft Dynamics CRM, Salesforce ou Google Analytics.
Os aplicativos organizacionais dão aos usuários os dados internos de que precisam. Planejamos adicionar recursos aos aplicativos organizacionais para que os usuários possam personalizar o conteúdo que encontrarem dentro dos aplicativos. Isso acabará com a necessidade de pacotes de conteúdo. 

Com a nova versão prévia de workspaces, não é possível criar nem consumir pacotes de conteúdo organizacional. Em vez disso, é possível usar os aplicativos fornecidos para conectar-se aos serviços de terceiros ou pedir para suas equipes internas fornecerem aplicativos para quaisquer pacotes de conteúdo que você está usando no momento. 

## <a name="roles-in-the-new-workspaces"></a>Funções nos novos workspaces

As funções permitem que você gerencie quem pode fazer o que em um workspace para que as equipes possam colaborar. Os novos workspaces permitem que você atribua funções a indivíduos e a grupos de usuários: grupos de segurança, grupos do Office 365 e listas de distribuição. 

Ao atribuir funções a um grupo de usuários, os indivíduos no grupo têm acesso ao conteúdo. Se você aninhar grupos de usuários, todos os usuários contidos terão permissão. Um usuário que está em vários grupos de usuários com diferentes funções obtém o nível mais alto de permissão concedido a eles. 

Os novos workspaces oferecem três funções: administradores, membros e colaboradores.

**Os administradores podem:**

- Atualizar e excluir o workspace. 
- Adicionar/remover pessoas, incluindo outros administradores.
- Fazer tudo que os membros podem fazer.

**Os membros podem:** 

- Adicionar membros ou outras pessoas com permissões inferiores.
- Publicar e atualizar um aplicativo.
- Compartilhar um item ou um aplicativo.
- Permitir que outras pessoas compartilhem novamente os itens.
- Fazer tudo que os colaboradores podem fazer.


**Os colaboradores podem:** 

- Criar, editar e excluir conteúdo no workspace. 
- Publicar relatórios no workspace, excluir conteúdo.
- Não é possível conceder acesso ao conteúdo a novas pessoas; não é possível compartilhar conteúdo novo, mas é possível compartilhar com alguém com quem o workspace, o item ou o aplicativo já é compartilhado. 
- Não é possível modificar os membros do grupo.
 
Estamos criando fluxos de trabalho Solicitar acesso em todo o serviço para que os usuários que não têm acesso poderem solicitá-lo. No momento, os fluxos de trabalho Solicitar acesso existem para dashboards, relatórios e aplicativos.

## <a name="distribute-an-app"></a>Distribuir um aplicativo

Quando o conteúdo estiver pronto, escolha quais dashboards e relatórios você deseja publicar e, em seguida, publique-o como um *aplicativo*. Você pode criar um aplicativo de cada workspace. Seus colegas podem obter seu aplicativo de algumas maneiras diferentes. Você poderá instalá-lo automaticamente nas contas do Power BI de seus colegas, se o administrador do Power BI lhe der permissão. Caso contrário, eles podem localizar e instalar seus aplicativos do Microsoft AppSource ou você pode enviar um link direto. Eles recebem atualizações automaticamente e você pode controlar a frequência com que os dados são atualizados. Consulte [Publicar aplicativos com dashboards e relatórios no Power BI](service-create-distribute-apps.md) para obter detalhes.

## <a name="convert-old-app-workspaces-to-new-app-workspaces"></a>Converter workspaces de aplicativo antigos em novos

Durante o período de versão prévia, não é possível converter automaticamente seus workspaces de aplicativo antigos em novos. No entanto, é possível criar um novo workspace de aplicativo e publicar seu conteúdo no novo local. 

Quando os novos workspaces estiverem disponíveis para o público geral (GA), será possível aceitar migrar os antigos automaticamente. Em algum momento após a disponibilidade geral, será necessário migrá-los.

## <a name="power-bi-apps-faq"></a>Perguntas frequentes sobre os aplicativos do Power BI

### <a name="how-are-the-new-app-workspaces-different-from-current-app-workspaces"></a>Como os novos workspaces de aplicativo são diferentes dos workspaces de aplicativo atuais?
* A criação de workspaces de aplicativo não criará entidades correspondentes no Office 365 como os workspaces de aplicativo atuais fazem. (Ainda é possível adicionar um grupo do Office 365 ao seu workspace atribuindo-lhe uma função). 
* Nos workspaces de aplicativo atuais, é possível apenas adicionar indivíduos aos membros e às listas de administradores. Nos novos workspaces de aplicativo, é possível adicionar vários grupos de segurança do AD, listas de distribuição ou grupos do Office 365 a essas listas para possibilitar um gerenciamento de usuários mais fácil. 
- É possível criar um pacote de conteúdo organizacional com base em um workspace de aplicativo atual. Não é possível criar um com base nos novos workspaces de aplicativo.
- É possível consumir um pacote de conteúdo organizacional com base em um workspace de aplicativo atual. Não é possível consumir um com base nos novos workspaces de aplicativo.
- Durante a versão prévia, alguns recursos ainda não estão habilitados para novos workspaces de aplicativo. Consulte a próxima seção, [Outros novos recursos do workspace de planejados](service-create-the-new-workspaces.md#other-planned-new-app-workspace-preview-features), para obter detalhes.

## <a name="planned-new-app-workspace-preview-features"></a>Novos recursos de versão prévia do workspace de aplicativo planejados

Alguns outros novos recursos de versão prévia do workspace de aplicativo ainda estão sendo desenvolvidos, mas não estão disponíveis ainda enquanto lançamos a versão prévia:

- Nenhum botão **Sair do workspace**.
- Ainda não há suporte para as métricas de uso.
- Como o Premium funciona: é possível atribuir e criar workspaces em uma capacidade Premium, mas, para mover um workspace entre capacidades, acesse as configurações do workspace.
- Ainda não há suporte para a inserção de Web Part do SharePoint.
- Nenhum botão **OneDrive** para grupos do Office 365 em Obter dados/arquivos.

## <a name="app-workspace-features-that-work-differently"></a>Recursos do workspace de aplicativo que funcionam de forma diferente

Alguns recursos funcionam de maneira diferente dos workspaces de aplicativo atuais nos novos workspaces de aplicativo. Essas diferenças são intencionais, com base nos comentários recebidos dos clientes, e permitirão uma abordagem mais flexível para colaboração com workspaces:

- Os membros podem ou não compartilhar novamente: substituídos pela função Colaborador
- Workspaces somente leitura: em vez de permitir aos usuários o acesso somente leitura a um workspace, você atribui os usuários a uma função de visualizador que estará disponível em breve, o que permite o acesso somente leitura semelhante ao conteúdo em um workspace.

## <a name="known-issues"></a>Problemas conhecidos

Os seguintes problemas são conhecidos, e as correções estão em desenvolvimento:

- Usuários ou grupos de usuários gratuitos adicionados como destinatários de assinaturas para emails não podem receber os emails, embora devessem. O problema ocorre quando um dos novos workspaces está em uma capacidade Premium, mas o Meu Workspace do usuário que cria a assinatura não está em uma capacidade Premium. Se o Meu workspace estiver em uma capacidade Premium, os usuários e grupos de usuários gratuitos receberão os emails.
- Depois que um workspace for movido de uma capacidade Premium para uma capacidade compartilhada, em alguns casos, os usuários e grupos de usuários gratuitos continuarão recebendo emails, embora não devessem. O problema ocorre quando o Meu workspace do usuário que cria a assinatura está em uma capacidade Premium.

## <a name="next-steps"></a>Próximas etapas
* [Criar os workspaces atuais](service-create-workspaces.md)
* [Instalar e usar aplicativos no Power BI](service-create-distribute-apps.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
