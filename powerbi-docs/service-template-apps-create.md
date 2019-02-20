---
title: Criar aplicativos de modelo no Power BI (versão prévia)
description: Como criar aplicativos de modelo no Power BI que podem ser distribuídos para qualquer cliente do Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 02/04/2019
ms.author: maggies
ms.openlocfilehash: c08b7e60777b720aa4fc2489b02c212bdd3e7169
ms.sourcegitcommit: 8207c9269363f0945d8d0332b81f1e78dc2414b0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2019
ms.locfileid: "56249502"
---
# <a name="create-a-template-app-in-power-bi-preview"></a>Criar um aplicativo de modelo no Power BI (versão prévia)

Os novos *aplicativos de modelo* do Power BI permitem que os parceiros do Power BI criem aplicativos do Power BI com pouca ou nenhuma codificação e implante-os para qualquer cliente do Power BI.  Este artigo contém instruções passo a passo para a criação de um aplicativo de modelo do Power BI. 

Se você pode criar relatórios e dashboards do Power BI, pode se tornar um *construtor de aplicativos de modelo* que cria e empacota o conteúdo analítico em um *aplicativo*. Em seguida, você pode implantar o aplicativo para outros locatários do Power BI por meio de qualquer plataforma disponível, como o AppSource, ou usando-o em seu próprio serviço Web. Como construtor, você pode criar um pacote de análise protegido para distribuição. 

Os administradores de locatários do Power BI controlam e administram quem, em suas organizações, pode criar aplicativos de modelo e quem pode instalá-los. Aqueles que estão autorizados podem instalar o aplicativo de modelo e, em seguida, modificá-lo e distribuí-lo para os consumidores do Power BI em suas organizações.

## <a name="prerequisites"></a>Pré-requisitos 

Estes são os requisitos para a criação de um aplicativo de modelo:  

- Uma [licença do Power BI Pro](service-self-service-signup-for-power-bi.md)
- Uma [instalação do Power BI Desktop](desktop-get-the-desktop.md) (opcional)
- Familiaridade com os [conceitos básicos do Power BI ](service-basic-concepts.md)
- Permissões para criar um aplicativo de modelo. Confira o [portal de administração do Power BI, configurações de Aplicativo de modelo](service-admin-portal.md#template-apps-settings-preview) para obter mais detalhes.

## <a name="enable-app-developer-mode"></a>Habilitar o modo de desenvolvedor de aplicativos

Para criar um aplicativo de modelo que pode ser distribuído para outros locatários do Power BI, você precisa estar no modo de Desenvolvedor de Aplicativos. Caso contrário, você está apenas criando um aplicativo para os consumidores do Power BI em sua própria organização.
 
1. Abra o serviço do Power BI em um navegador.
2. Acesse **Configurações** > **Geral** > **Desenvolvedor** > **Habilitar modo de desenvolvimento de aplicativos de modelo**.

    ![Habilitar aplicativos de modelo](media/service-template-apps-create/power-bi-dev-template-app.png)

    Se essa opção não for exibida, contate o administrador do Power BI para que ele conceda [permissões de desenvolvimento de aplicativos de modelo](service-admin-portal.md#template-apps-settings-preview) no portal de administração.

3. Selecione **Aplicar**.

## <a name="create-the-template-app-workspace"></a>Criar o workspace do aplicativo de modelo

Para criar um aplicativo de modelo que pode ser distribuído para outros locatários do Power BI, você precisa criá-lo em um dos novos workspaces do aplicativo. 
 
1. No serviço do Power BI, selecione **Workspaces** > **Criar workspace do aplicativo**. 
 
    ![Criar workspace do aplicativo](media/service-template-apps-create/power-bi-new-workspace.png)

3. Em **Criar um workspace do aplicativo**, em **Visualizar workspaces aprimorados**, selecione **Experimentar agora**.

    ![Experimentar os novos workspaces](media/service-template-apps-create/power-bi-try-now-new-workspace.png)

5. Insira um nome, uma descrição (opcional) e a imagem de logotipo (opcional) para o workspace do aplicativo.

4. Selecione **Desenvolver um aplicativo de modelo**.

    ![Desenvolver um aplicativo de modelo](media/service-template-apps-create/power-bi-template-app-develop.png)

5. Selecione **Salvar**.

## <a name="create-the-content-in-your-template-app"></a>Criar o conteúdo no aplicativo de modelo

Assim como ocorre com um workspace comum do aplicativo do Power BI, a próxima etapa é criar o conteúdo no workspace.  Nesta versão prévia dos aplicativos de modelo, damos suporte a apenas um de cada tipo: um conjunto de dados, um relatório e um dashboard.

- [Crie o conteúdo do Power BI](power-bi-creator-landing.md) no workspace do aplicativo.

Caso esteja usando parâmetros no Power Query, verifique se eles têm um tipo bem definido (por exemplo, Texto). Não há suporte para os tipos Qualquer e Binário. 

O artigo [Dicas para a criação de aplicativos de modelo no Power BI (versão prévia)](service-template-apps-tips.md) traz sugestões a serem consideradas ao criar relatórios e dashboards para o aplicativo de modelo.

## <a name="create-the-test-template-app"></a>Criar o aplicativo de modelo de teste

Agora que há algum conteúdo no workspace, você está pronto para empacotá-lo em um aplicativo de modelo. A primeira etapa é criar um aplicativo de modelo de teste, acessível somente na organização do locatário.

1. No workspace do aplicativo de modelo, selecione **Criar aplicativo**. 

    ![Criar aplicativo](media/service-template-apps-create/power-bi-create-app.png)
 
    Aqui, você preencherá os parâmetros adicionais para o aplicativo de modelo, em quatro categorias. 

    **Identidade Visual**

    - Nome do aplicativo 
    - Descrição
    - Logotipo do aplicativo (opcional)
    - Cor do aplicativo 

    **Conteúdo** 

    - Página de aterrissagem do aplicativo (opcional): Defina um relatório ou um dashboard para ser a página de aterrissagem do aplicativo.  
    
    **Controle** 

    Controle várias limitações e restrições que os usuários do aplicativo terão com o conteúdo do aplicativo. Use esse controle para proteger alguns tipos de propriedade intelectual que o aplicativo possa conter.

    **Acesso**

    - Na fase de teste, decida quais outras pessoas em sua organização podem instalar e testar o aplicativo.

    Não se preocupe, pois você sempre poderá voltar e alterar essas configurações posteriormente.  

2. Selecione **Criar aplicativo**. 

    Você verá uma mensagem indicando que o aplicativo de teste está pronto, com um link para copiar e compartilhar com os testadores do aplicativo.

    ![O aplicativo de teste está pronto](media/service-template-apps-create/power-bi-template-app-test-ready.png)

    Você também realizou a primeira etapa do processo de gerenciamento de versão, que é descrita a seguir.

    

## <a name="manage-the-template-app-release"></a>Gerenciar a versão do aplicativo de modelo

Antes de liberar esse aplicativo de modelo publicamente, é recomendável verificar se ele está pronto para liberação. O Power BI criou o painel de gerenciamento de versão, no qual você pode seguir e inspecionar o caminho completo da versão do aplicativo. Você também pode disparar a transição de um estágio a outro. Os estágios comuns são: 

- Gerar um aplicativo de teste: para teste apenas em sua organização. 
- Promover o pacote de teste ao estágio de pré-produção: teste fora de sua organização.
- Promover o pacote de pré-produção à produção: versão de produção. 
- Exclua qualquer pacote ou comece novamente no estágio anterior. 

Vamos percorrer os estágios.

1. No workspace do aplicativo de modelo, selecione **Gerenciamento de Versão**.

    ![Ícone do gerenciamento de versão](media/service-template-apps-create/power-bi-release-management-icon.png)

2. Selecione **Criar aplicativo**. 

    Se você criar o aplicativo de teste em **Criar o aplicativo de modelo de teste** acima, o ponto amarelo ao lado de **Teste** já estará preenchido e você não precisará selecionar **Criar aplicativo** aqui. Se você selecioná-lo, voltará ao processo de criação do aplicativo de modelo.
 
3. Selecione **Obter link**.

    ![Criar aplicativo, obter link](media/service-template-apps-create/power-bi-dev-template-create-app-get-link.png)
 
9. Para testar a experiência de instalação do aplicativo, copie o link na janela de notificação e cole-o em uma nova janela do navegador. 

    Nela, você seguirá o mesmo procedimento que os clientes seguirão. Confira [Instalar e distribuir aplicativos de modelo em sua organização](service-template-apps-install-distribute.md) para a versão deles.
 
10. Na caixa de diálogo, selecione **Instalar**.

    Quando a instalação for bem-sucedida, você verá uma notificação indicando que o novo aplicativo está pronto. 
 
11. Selecione **Ir para o aplicativo**.
 
12. Em **Introdução ao novo aplicativo**, você verá o aplicativo como ele será exibido para os clientes. 

    ![Introdução ao aplicativo](media/service-template-apps-create/power-bi-template-app-get-started.png)

13. Selecione **Explorar Aplicativo** para verificar o aplicativo de teste com os dados de exemplo.

1. Para fazer alterações, volte ao aplicativo no workspace original. Atualize o aplicativo de teste até ficar satisfeito.

9. Quando estiver pronto para promover o aplicativo à pré-produção para testes adicionais fora do locatário, volte ao painel **Gerenciamento de Versão** e selecione **Promover aplicativo** ao lado de **Teste**.
 
    ![Promover aplicativo à pré-produção](media/service-template-apps-create/power-bi-template-app-promote.png)

11. Selecione **Promover** para confirmar sua escolha. 

12. Copie essa nova URL para compartilhamento fora do locatário para teste. Esse link também é aquele que você enviará para iniciar o processo de distribuição do aplicativo no AppSource.

12. Quando o aplicativo estiver pronto para produção ou compartilhamento por meio do AppSource, volte ao painel **Gerenciamento de Versão** e selecione **Promover aplicativo** ao lado de **Pré-produção**.
 
11. Selecione **Promover** para confirmar sua escolha. 

    Agora o aplicativo está em produção e pronto para distribuição.

    ![Aplicativo em produção](media/service-template-apps-create/power-bi-template-app-production.png)

Para disponibilizar o aplicativo amplamente para milhares de usuários do Power BI no mundo, recomendamos que você o envie ao AppSource. Confira a [oferta do Aplicativo do Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) para obter mais detalhes. 

## <a name="update-your-app"></a>Atualizar o aplicativo

Agora que o aplicativo está em produção, você poderá recomeçar na fase de teste, sem interromper o aplicativo em produção. 

1. No painel **Gerenciamento de versão**, selecione **Criar aplicativo**.

1. Volte ao processo de criação do aplicativo. 
2. Depois de definir **Identidade Visual**, **Conteúdo**, **Controle** e **Acesso**, selecione novamente **Criar aplicativo**.
3. Selecione **Fechar** e volte a **Gerenciamento de versão**. 

    Você verá que tem duas versões agora: A versão em produção e uma nova versão em teste. 

    ![Duas versões de um aplicativo de modelo](media/service-template-apps-create/power-bi-template-app-2-versions.png)

## <a name="next-steps"></a>Próximas etapas

Veja como os clientes interagem com o aplicativo de modelo em [Instalar, personalizar e distribuir aplicativos de modelo em sua organização](service-template-apps-install-distribute.md).

Confira a [oferta do Aplicativo do Power BI](https://docs.microsoft.com/azure/marketplace/cloud-partner-portal/power-bi/cpp-power-bi-offer) para obter mais detalhes sobre como distribuir o aplicativo.





