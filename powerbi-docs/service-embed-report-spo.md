---
title: Inserir com Web Part de Relatório no SharePoint Online
description: Com a nova Web Part de Relatório do Power BI para o SharePoint Online, você pode facilmente inserir relatórios interativos do Power BI às páginas do SharePoint Online.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
LocalizationGroup: Share your work
ms.date: 05/16/2019
ms.openlocfilehash: c8789d47ed1b67f9fd6808865514120457a29dfe
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66051277"
---
# <a name="embed-with-report-web-part-in-sharepoint-online"></a>Inserir com Web Part de Relatório no SharePoint Online

Com a nova Web Part de Relatório do Power BI para o SharePoint Online, você pode facilmente inserir relatórios interativos do Power BI às páginas do SharePoint Online.

Ao usar a nova **inserir no SharePoint Online** opção, os relatórios incorporados são totalmente protegidos, portanto, você pode facilmente criar portais internos seguros.

## <a name="requirements"></a>Requisitos

Para **inserir no SharePoint Online** relatórios funcionem, é necessário:

* Uma licença do Power BI Pro ou um [capacidade do Power BI Premium (EME ou SKU P)](service-premium-what-is.md) com uma licença do Power BI.
* A web part do Power BI para o SharePoint Online requer [Páginas Modernas](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b).

## <a name="embed-your-report"></a>Insira seu relatório
Para inserir o relatório ao SharePoint Online, você precisa obter a URL de relatório e usá-lo com o SharePoint Online de nova web part do Power BI.

### <a name="get-a-report-url"></a>Obter uma URL de relatório

1. No Power BI, exiba o relatório.

2. Selecione o **arquivo** menu suspenso, selecione **inserir no SharePoint Online**.

    ![Menu Arquivo](media/service-embed-report-spo/powerbi-file-menu.png)

3. Copie a URL de relatório na caixa de diálogo.

    ![Inserir link](media/service-embed-report-spo/powerbi-embed-link-sharepoint.png)

### <a name="add-the-power-bi-report-to-a-sharepoint-online-page"></a>Adicionar o relatório do Power BI a uma página do SharePoint Online

1. Abra a página de destino no SharePoint Online e selecione **editar**.

    ![Página de edições do SP](media/service-embed-report-spo/powerbi-sharepoint-edit-page.png)

    Ou, no Sharepoint Online, selecione **+ novo** para criar uma nova página de site.

    ![Nova página do SP](media/service-embed-report-spo/powerbi-sharepoint-new-page.png)

2. Selecione o **+** lista suspensa e, em seguida, selecione o **Power BI**.

    ![Nova web part do SP](media/service-embed-report-spo/powerbi-sharepoint-new-web-part.png)

3. Selecione **Adicionar relatório**.

    ![Novo relatório do SP](media/service-embed-report-spo/powerbi-sharepoint-new-report.png)  

4. Cole a URL do relatório copiado anteriormente na **link de relatório do Power BI** painel. O relatório é carregado automaticamente.

    ![Novas propriedades da web part do SP](media/service-embed-report-spo/powerbi-sharepoint-new-web-part-properties.png)

5. Selecione **Publicar** para tornar a alteração visível para os usuários do SharePoint Online.

    ![Relatório do SP carregado](media/service-embed-report-spo/powerbi-sharepoint-report-loaded.png)

## <a name="grant-access-to-reports"></a>Conceder acesso aos relatórios

Inserir um relatório no SharePoint Online não automaticamente aos usuários permissão para exibir o relatório – você precisará definir permissões de exibição no Power BI.

> [!IMPORTANT]
> Certifique-se de examinar quem pode ver o relatório dentro do serviço do Power BI e de conceder acesso aos que não aparecem na lista.

Há duas maneiras de fornecer acesso ao relatório no Power BI. É a primeira maneira, se você estiver usando um grupo do Office 365 para criar seu site de equipe do SharePoint Online, liste o usuário como um membro do **espaço de trabalho de aplicativo no serviço do Power BI** e o **página do SharePoint**. Para obter mais informações, consulte como [gerenciar um espaço de trabalho de aplicativo](service-manage-app-workspace-in-power-bi-and-office-365.md).

A segunda maneira é inserir um relatório dentro de um aplicativo e compartilhá-lo diretamente com os usuários:  

1. O autor (precisa ser um usuário Pro) cria um relatório em um espaço de trabalho do aplicativo. Para compartilhar com **usuários do Power BI gratuito**, o espaço de trabalho do aplicativo precisa ser definido como um **espaço de trabalho Premium**.

2. O autor publica o aplicativo e o instala. O autor precisa certificar-se de instalar o aplicativo para ter acesso à URL de relatório que é usado para inserir no SharePoint Online.

3. Agora todos os usuários finais também precisam instalar o aplicativo. Você também pode usar o **instalar o aplicativo automaticamente** recurso, que pode ser habilitado na [portal de administração do Power BI](service-admin-portal.md), para ter o aplicativo previamente instalado para usuários finais.

   ![Instalar o aplicativo automaticamente](media/service-embed-report-spo/install-app-automatically.png)

4. O autor abre o aplicativo e vai para o relatório.

5. O autor copia a URL do relatório de inserção de relatório o aplicativo instalado. **Não use a URL do relatório original do espaço de trabalho do aplicativo.**

6. Crie um novo site de equipe no SharePoint Online.

7. Adicione a URL do relatório copiado anteriormente para a web part do Power BI.

8. Adicione todos os usuários finais e/ou grupos que consumirão os dados na página do SharePoint Online e no aplicativo do Power BI que você criou.

    > [!NOTE]
    > **Os usuários ou grupos precisam acessar a página do SharePoint Online e o relatório no aplicativo do Power BI para ver o relatório na página do SharePoint.**

Agora o usuário final pode ir para o site de equipe no SharePoint Online e exibir os relatórios na página.

## <a name="multi-factor-authentication"></a>Autenticação multifator

Se o ambiente do Power BI exigir que você entre usando a autenticação multifator, talvez será necessário entrar com um dispositivo de segurança para verificar sua identidade. Isso ocorre se você não tiver assinado no SharePoint Online usando a autenticação multifator, mas seu ambiente do Power BI requer um dispositivo de segurança para validar uma conta.

> [!NOTE]
> Azure Active Directory 2.0 não oferece suporte a autenticação multifator - os usuários verão uma mensagem de erro. Se o usuário entrar novamente no SharePoint Online usando o dispositivo de segurança, o relatório poderá ser exibido.

## <a name="web-part-settings"></a>Configurações de Web Part

Abaixo estão as configurações que você pode ajustar para a web part do Power BI para o SharePoint Online.

![Propriedades da web part do SP](media/service-embed-report-spo/powerbi-sharepoint-web-part-properties.png)

| Propriedade | Descrição |
| --- | --- |
| Nome da página |Define a página de padrão da web part. Selecione um valor na lista suspensa. Se nenhuma página for exibida, o relatório terá uma página ou a URL que você colou conterá um nome de página. Remover a seção de relatório da URL para selecionar uma página específica. |
| Exibir |Ajusta como o relatório se encaixa dentro da página do SharePoint Online. |
| Exibir o Painel de Navegação |Exibe ou oculta o painel de navegação da página. |
| Exibir Painel de Filtro |Exibe ou oculta o painel de filtro. |

## <a name="reports-that-do-not-load"></a>Relatórios que não são carregados

Se o relatório não for carregado na web part do Power BI, você poderá ver a seguinte mensagem:

![Este conteúdo não está disponível mensagem](media/service-embed-report-spo/powerbi-sharepoint-report-not-found.png)

Há duas razões comuns para essa mensagem.

1. Você não tem acesso ao relatório.
2. O relatório foi excluído.

Entre em contato com o proprietário da página do SharePoint Online para ajudar a resolver o problema.

## <a name="licensing"></a>Licenças

Os usuários que exibem um relatório no SharePoint precisam de uma **licença do Power BI Pro** ou o conteúdo precisa estar em um espaço de trabalho que esteja em uma capacidade do **[Power BI Premium (SKU EM ou P)](service-admin-premium-purchase.md)** .

## <a name="known-issues-and-limitations"></a>Limitações e problemas conhecidos

* Erro: "Ocorreu um erro, tente sair, entrar outra vez e visitar esta página novamente. ID da correlação: indefinido, status de resposta http: 400, código de erro do servidor 10001, mensagem: Atualização de token ausente"
  
  Se você receber esse erro, tente uma das etapas de solução de problemas abaixo.
  
  1. Saia do SharePoint e entre novamente. Certifique-se de fechar todas as janelas do navegador antes de entrar novamente.

  2. Se sua conta de usuário exigir autenticação multifator (MFA), em seguida, entre no SharePoint usando seu dispositivo MFA (aplicativo de telefone, cartão inteligente, etc.).
  
  3. Contas de Usuários convidados B2B do Azure não são compatíveis. Os usuários veem o logotipo do Power BI que mostra a parte que está sendo carregada, mas o relatório não é mostrado.

* O Power BI não dá suporte aos mesmos idiomas localizados que o SharePoint Online. Como resultado, você não verá a localização correta no relatório inserido.

* Você pode encontrar problemas se usar o Internet Explorer 10. Você pode examinar o [suporte dos navegadores para o Power BI](consumer/end-user-browsers.md) e para o [Office 365](https://products.office.com/office-system-requirements#Browsers-section).

* A Web part do Power BI não está disponível para [nuvens nacionais](https://powerbi.microsoft.com/clouds/).

* O servidor clássico do SharePoint não é compatível com essa web part.

* [Filtros de URL](service-url-filters.md) não são compatíveis com a Web part do SPO.

## <a name="next-steps"></a>Próximas etapas

* [Permitir ou impedir a criação de páginas de sites modernas pelos usuários finais](https://support.office.com/article/Allow-or-prevent-creation-of-modern-site-pages-by-end-users-c41d9cc8-c5c0-46b4-8b87-ea66abc6e63b)  
* [Criar e distribuir um aplicativo no Power BI](service-create-distribute-apps.md)  
* [Compartilhar um painel com seus colegas e com outras pessoas](service-share-dashboards.md)  
* [O que é o Power BI Premium?](service-premium-what-is.md)
* [Inserir o relatório em um site ou portal seguro](service-embed-secure.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)