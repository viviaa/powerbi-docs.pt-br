---
title: Conectar-se à Segurança do Microsoft Graph no Power BI Desktop
description: Conecte-se com facilidade à API de Segurança do Microsoft Graph no Power BI Desktop
author: preetikr
manager: kfile
ms.reviewer: ''
ms.custom: seojan19
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: preetikr
LocalizationGroup: Connect to data
ms.openlocfilehash: 2187a24820ef8ea3db9fdd1b7a881dc9cfb6393f
ms.sourcegitcommit: f07520591db6c3f27ab6490612cc56384abc6633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56298881"
---
# <a name="connect-to-microsoft-graph-security-in-power-bi-desktop"></a>Conectar-se à Segurança do Microsoft Graph no Power BI Desktop

Use o Power BI Desktop para se conectar à API de Segurança do Microsoft Graph usando o conector do Power BI para Segurança do Microsoft Graph. Isso permitirá que você crie dashboards e relatórios, a fim de obter insights sobre [alertas](https://docs.microsoft.com/graph/api/resources/alert?view=graph-rest-1.0) relacionados à segurança e o [Secure Score](https://docs.microsoft.com/graph/api/resources/securescores?view=graph-rest-beta). A [API de Segurança do Microsoft Graph](https://aka.ms/graphsecuritydocs) conecta [várias soluções de segurança](https://aka.ms/graphsecurityalerts) da Microsoft e do ecossistema de parceiros para proporcionar uma correlação mais fácil de alertas, fornecer acesso a informações contextuais sofisticadas e simplificar a automação. Isso capacita as organizações a obter insights rapidamente e executar ações em todos os seus produtos de segurança, reduzindo o custo e a complexidade da criação e da manutenção de várias integrações.

## <a name="prerequisites-to-connect-with-the-microsoft-graph-security-connector"></a>Pré-requisitos de conexão com o conector de Segurança do Microsoft Graph

* Para usar o conector de Segurança do Microsoft Graph, você precisa ter *recebido explicitamente* o consentimento de administrador de locatários do Azure AD (Active Directory), que faz parte dos [requisitos de Autenticação de Segurança do Microsoft Graph](https://aka.ms/graphsecurityauth). Esse consentimento exige o nome e a ID do aplicativo do conector do Power BI para Segurança do Microsoft Graph, que também podem ser encontrados no [portal do Azure](https://portal.azure.com):

   | Propriedade | Valor |
   |----------|-------|
   | **Nome do Aplicativo** | `MicrosoftGraphSecurityPowerBIConnector` |
   | **ID do Aplicativo** | `cab163b7-247d-4cb9-be32-39b6056d4189` |
   |||

   Para fornecer consentimento ao conector, o administrador de locatários do Azure AD poderá seguir uma destas etapas:

   * [Fornecer consentimento do administrador de locatários para aplicativos do Azure AD](https://docs.microsoft.com/azure/active-directory/develop/v2-permissions-and-consent).

   * Durante a primeira execução da lógica do aplicativo, o aplicativo poderá solicitar consentimento do administrador de locatários do Azure AD por meio da [experiência de consentimento do aplicativo](https://docs.microsoft.com/azure/active-directory/develop/application-consent-experience).
   
* A conta de usuário usada para entrar e se conectar ao conector do Power BI para Segurança do Microsoft Graph precisa ser membro da função Administrador limitado Leitor de segurança no Azure AD (Leitor de segurança ou Administrador de Segurança). Siga as etapas da seção [Atribuir funções do Azure AD aos usuários](https://docs.microsoft.com/graph/security-authorization#assign-azure-ad-roles-to-users). 

## <a name="using-the-microsoft-graph-security-connector"></a>Usando o conector de Segurança do Microsoft Graph

Siga estas etapas para usar o conector de **Segurança do Microsoft Graph**:

1. Selecione **Obter Dados -> Mais…** na faixa de opções **Página Inicial** do Power BI Desktop.
2. Selecione **Serviços Online** nas categorias à esquerda.
3. Clique em **Segurança do Microsoft Graph (Beta)**.

    ![Obter Dados](media/desktop-connect-graph-security/GetData.PNG)
    
4. Na janela **Segurança do Microsoft Graph** exibida, selecione a versão da API do Microsoft Graph a ser consultada. As opções são v1.0 e beta.

    ![Selecionar a versão](media/desktop-connect-graph-security/selectVersion.PNG)
    
5. Entre em sua conta do Azure Active Directory, quando solicitado. Essa conta precisa ter a função **Leitor de segurança**, conforme mencionado na seção de pré-requisitos acima.

    ![Entrar](media/desktop-connect-graph-security/SignIn.PNG)
    
6. Se você for o administrador de locatários **e** ainda não tiver fornecido consentimento ao conector (aplicativo) do Power BI para Segurança do Microsoft Graph de acordo com os pré-requisitos, você verá a caixa de diálogo a seguir. Lembre-se de selecionar "**Consentimento em nome de sua organização**".

    ![Consentimento do administrador](media/desktop-connect-graph-security/AdminConsent.PNG)
    
7. Depois que estiver conectado, você verá a janela a seguir indicando que você foi autenticado. Selecione **Conectar**.

    ![Conectado](media/desktop-connect-graph-security/SignedIn.PNG)
    
8. Depois que você se conectar com êxito, uma janela **Navegador** será exibida, conforme mostrado a seguir, e apresentará as entidades, como alertas, entre outros, disponíveis na [API de Segurança do Microsoft Graph](https://aka.ms/graphsecuritydocs) para a versão selecionada nas etapas anteriores. Selecione uma ou várias entidades para importação e uso no **Power BI Desktop**. Clique em **Carregar** para obter a exibição de resultados descrita na etapa 10.

   ![Tabela de navegação](media/desktop-connect-graph-security/NavTable.PNG)
    
9. Caso deseje fazer uma consulta avançada na API de Segurança do Microsoft Graph, selecione a função **Especificar uma URL personalizada de Segurança do Microsoft Graph para filtrar os resultados**. Isso permitirá que você faça uma consulta [OData.Feed](https://docs.microsoft.com/power-bi/desktop-connect-odata) na API de Segurança do Microsoft Graph com as permissões necessárias para acessar a API.

   > [!NOTE]
   > O serviceUri de exemplo usado abaixo é `https://graph.microsoft.com/v1.0/security/alerts?$filter=Severity eq 'High'`. Consulte os [parâmetros de consulta OData compatíveis com o Graph](https://docs.microsoft.com/graph/query-parameters) para criar consultas para filtrar, ordenar ou recuperar os resultados mais recentes.

   ![Feed OData](media/desktop-connect-graph-security/ODataFeed.PNG)
    
   Quando você seleciona **Invoke**, a função OData.Feed faz uma chamada à API, que abre o Editor de Consultas, para filtrar e refinar o conjunto de dados que você deseja usar e, em seguida, carregar esse conjunto de dados refinado no Power BI Desktop.

10. A imagem a seguir ilustra a janela de resultados para as entidades de Segurança do Microsoft Graph consultadas.

   ![Resultado](media/desktop-connect-graph-security/Result.PNG)
    

Agora você está pronto para usar os dados importados do conector de Segurança do Microsoft Graph no Power BI Desktop para criar visuais e relatórios ou interagir com outros dados aos quais deseje se conectar e que deseje importar, como outras pastas de trabalho do Excel, bancos de dados ou qualquer outra fonte de dados.

## <a name="next-steps"></a>Próximas etapas
* Confira as amostras e os modelos do Power BI que usam esse conector no [repositório de amostras do Power BI no GitHub para Segurança do Microsoft Graph](https://aka.ms/graphsecuritypowerbiconnectorsamples).

* Confira alguns cenários de usuário e mais informações na [postagem no blog sobre o Conector do Power BI para Segurança do Microsoft Graph](https://aka.ms/graphsecuritypowerbiconnectorblogpost).

* Há todos os tipos de dados aos quais você pode se conectar usando o Power BI Desktop. Para obter mais informações sobre fontes de dados, confira os seguintes recursos:

    * [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
    * [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
    * [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
    * [Conectar-se a pastas de trabalho do Excel no Power BI Desktop](desktop-connect-excel.md)
    * [Inserir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)
