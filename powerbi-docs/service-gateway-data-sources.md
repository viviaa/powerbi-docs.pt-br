---
title: Gerenciar fontes de dados
description: Saiba como gerenciar fontes de dados no Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 07/15/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Gateways
ms.openlocfilehash: 3a4b343894f23d6f5720d95eb6c92436259befaa
ms.sourcegitcommit: a58461fe7dfa65c751490b52de5fc73f8e69a17f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68352207"
---
# <a name="manage-data-sources"></a>Gerenciar fontes de dados

[!INCLUDE [gateway-rewrite](includes/gateway-rewrite.md)]

O Power BI oferece suporte a várias fontes de dados no local, e cada uma tem seus próprios requisitos. Um gateway pode ser usado para uma única fonte de dados ou para várias fontes de dados. Neste exemplo, mostraremos como adicionar o SQL Server como uma fonte de dados, mas as etapas são semelhantes para outras fontes de dados.

>[!NOTE]
>A maioria das operações de gerenciamento de fontes de dados também pode ser executada usando APIs. Para obter mais informações, confira [APIs REST (Gateways)](/rest/api/power-bi/gateways).

## <a name="add-a-data-source"></a>Adicionar uma fonte de dados

>[!NOTE]
>Os grupos sem um email não podem ser adicionados.

1. No canto superior direito do serviço do Power BI, selecione o ícone de engrenagem ![Configurações](media/service-gateway-data-sources/icon-gear.png)  >  **Gerenciar gateways**.

    ![Gerenciar gateways](media/service-gateway-data-sources/manage-gateways.png)

2. Selecione um gateway > **Adicionar fonte de dados** ou vá para Gateways > **Adicionar fonte de dados**.

    ![Adicionar fonte de dados](media/service-gateway-data-sources/add-data-source.png)

3. Selecione o **tipo de fonte de dados**.

    ![Selecionar SQL Server](media/service-gateway-data-sources/select-sql-server.png)

4. Insira informações para a fonte de dados. Neste exemplo, são **Servidor**, **Banco de dados** e outras informações.  

    ![Configurações da fonte de dados](media/service-gateway-data-sources/data-source-settings.png)

5. Para o SQL Server, você escolheria um **Método de Autenticação** **Windows** ou **Básico** (Autenticação SQL). Se você escolher **Básico**, insira as credenciais para a fonte de dados.

6. Opcionalmente, em **Configurações avançadas**, configure o [nível de privacidade](https://support.office.com/article/Privacy-levels-Power-Query-CC3EDE4D-359E-4B28-BC72-9BEE7900B540) para sua fonte de dados (não se aplica a [DirectQuery](desktop-directquery-about.md)).

    ![Configurações avançadas](media/service-gateway-data-sources/advanced-settings.png)

7. Selecione **Adicionar**. Você verá *Conexão bem-sucedida* se o processo for bem-sucedido.

    ![Conexão bem-sucedida](media/service-gateway-data-sources/connection-successful.png)

Agora, você pode usar essa fonte de dados para incluir dados do SQL Server em seus relatórios e painéis do Power BI.

## <a name="remove-a-data-source"></a>Remover uma fonte de dados

Você pode remover uma fonte de dados se não a estiver usando. Saiba que a remoção de uma fonte de dados interrompe todos os painéis e relatórios que dependem dessa fonte de dados.

Para remover uma fonte de dados, vá para a fonte de dados e selecione **Remover**.

![Remover uma fonte de dados](media/service-gateway-data-sources/remove-data-source.png)

## <a name="using-the-data-source-for-scheduled-refresh-or-directquery"></a>Usando a fonte de dados para a atualização agendada ou DirectQuery

Depois de criar a fonte de dados, ela estará disponível para uso com as conexões do DirectQuery ou por meio da atualização agendada.

> [!NOTE]
>Os nomes do servidor e do banco de dados devem corresponder entre o Power BI Desktop e a fonte de dados no gateway de dados local.

O vínculo entre o conjunto de dados e a fonte de dados no gateway baseia-se no nome do servidor e no nome do banco de dados. Esses nomes devem corresponder. Por exemplo, se você fornecer um endereço IP para o nome do servidor, no Power BI Desktop, deverá usar o endereço IP para a fonte de dados na configuração do gateway. Se você usar *SERVER\INSTANCE*, no Power BI Desktop, precisará usar o mesmo na fonte de dados configurada para o gateway.

Se estiver listado na guia **Usuários** da fonte de dados configurada no gateway e houver a correspondência entre os nomes do servidor e do banco de dados, você verá o gateway como uma opção a ser usada com a atualização agendada.

![Conexão do gateway](media/service-gateway-data-sources/gateway-connection.png)

> [!WARNING]
> Se seu conjunto de dados contiver várias fontes de dados, cada uma delas deverá ser adicionada ao gateway. Se uma ou mais fontes de dados não forem adicionadas ao gateway, você não o verá como disponível para a atualização agendada.

### <a name="limitations"></a>Limitações

O OAuth é um esquema de autenticação com suporte somente para conectores personalizados com o gateway de dados local. Você não pode adicionar outras fontes de dados que exigem OAuth. Caso seu conjunto de dados tenha uma fonte de dados que exija OAuth e essa fonte de dados não for um conector personalizado, você não poderá usar o gateway para a atualização agendada.

## <a name="manage-users"></a>Gerenciar usuários

Depois de adicionar uma fonte de dados a um gateway, você dá acesso a usuários e grupos de segurança habilitados por email para a fonte de dados específica (não o gateway inteiro). A lista de usuários da fonte de dados controla somente quem tem permissão para publicar relatórios que incluem dados da fonte de dados. Os proprietários de relatório podem criar painéis, pacotes de conteúdo e aplicativos e, em seguida, compartilhá-los com outros usuários.

Você também pode dar acesso administrativo a usuários e grupos de segurança para o gateway.

### <a name="add-users-to-a-data-source"></a>Adicionar usuários a uma fonte de dados

1. No canto superior direito do serviço do Power BI, selecione o ícone de engrenagem ![Configurações](media/service-gateway-data-sources/icon-gear.png)  >  **Gerenciar gateways**.

2. Selecione a fonte de dados à qual deseja adicionar usuários.

3. Selecione **Usuários** e insira um usuário da sua organização ao qual você deseja conceder acesso à fonte de dados selecionada. Por exemplo, na tela a seguir, você está adicionando Maggie e Adam.

    ![Guia Usuários](media/service-gateway-data-sources/users-tab.png)

4. Selecione **Adicionar** e o membro adicionado aparecerá na caixa.

    ![Adicionar usuário](media/service-gateway-data-sources/add-user.png)

E isso é tudo o que é necessário. Lembre-se de que você precisa adicionar usuários a cada fonte de dados às quais deseja permitir acesso. Cada fonte de dados tem uma lista separada de usuários e você deve adicionar usuários para cada fonte de dados separadamente.

### <a name="remove-users-from-a-data-source"></a>Remover usuários de uma fonte de dados

Na guia **Usuários** para a fonte de dados, você pode remover usuários e grupos de segurança que usam essa fonte de dados.

![Remover usuário](media/service-gateway-data-sources/remove-user.png)

## <a name="storing-encrypted-credentials-in-the-cloud"></a>Armazenando credenciais criptografadas na nuvem

Quando você adiciona uma fonte de dados ao gateway, é necessário fornecer credenciais para essa fonte de dados. Todas as consultas à fonte de dados serão executadas com essas credenciais. Antes de serem armazenadas na nuvem, as credenciais são criptografadas com segurança usando a criptografia simétrica para que elas não possam ser descriptografadas na nuvem. As credenciais são enviadas para o computador que executa o gateway, localmente, no qual são descriptografadas quando as fontes de dados são acessadas.

## <a name="list-of-available-data-source-types"></a>Relação dos tipos de fonte de dados disponíveis

O gateway de dados local é compatível com as seguintes fontes de dados para Power BI. Além das fontes de dados locais, as fontes protegidas por um firewall, VPN ou rede virtual também podem precisar de um gateway de dados.

| **Fonte de dados** | **Live/DirectQuery** | **Atualização manual ou agendada configurada pelo usuário** |
| --- | --- | --- |
| ActiveDirectory |Não |Sim |
| Amazon Redshift |Sim |Sim |
| Analysis Services |Sim |Sim |
| Cubos do AtScale |Sim |Sim |
| Armazenamento de Blobs do Azure |Não |Sim |
| Azure DevOps Server |Não |Sim |
| Armazenamento de Tabelas do Azure |Não |Sim |
| Conector do BI |Sim |Sim |
| Denodo |Sim |Sim |
| Dremio |Sim |Sim |
| EmigoDataSourceConnector |Não |Sim |
| Essbase |Sim |Sim |
| Exasol |Sim |Sim |
| Arquivo |Não |Sim |
| Pasta |Não |Sim |
| Paxata |Não |Sim |
| IBM DB2 |Sim |Sim |
| Banco de dados do IBM Informix |Não |Sim |
| IBM Netezza |Sim |Sim |
| Impala |Sim |Sim |
| Jethro ODBC |Sim |Sim |
| Kyligence Enterprise |Sim |Sim |
| MarkLogic ODBC |Sim |Sim |
| Segurança do Microsoft Graph |Não |Sim |
| MySQL |Não |Sim |
| ODBC |Não |Sim |
| OData |Não |Sim |
| OleDb |Não |Sim |
| Oracle |Sim |Sim |
| PostgreSQL |Não |Sim |
| QubolePresto |Sim |Sim |
| Quick Base Connector |Não |Sim |
| Servidor de Mensagens SAP Business Warehouse |Sim |Sim |
| Servidor do SAP Business Warehouse |Sim |Sim |
| SAP HANA |Sim |Sim |
| SQL Server |Sim |Sim |
| SharePoint |Não |Sim |
| Snowflake |Sim |Sim |
| Spark |Sim |Sim |
| SurveyMonkey |Não |Sim |
| Sybase |Não |Sim |
| TeamDesk.Database |Não |Sim |
| Teradata |Sim |Sim |
| Vertica |Sim |Sim |
| Web |Não |Sim |
| Workforce Dimensions |Não |Sim |

## <a name="next-steps"></a>Próximas etapas

* [Gerenciar sua fonte de dados – Analysis Services](service-gateway-enterprise-manage-ssas.md)
* [Gerenciar sua fonte de dados – SAP HANA](service-gateway-enterprise-manage-sap.md)
* [Gerenciar sua fonte de dados – SQL Server](service-gateway-enterprise-manage-sql.md)
* [Gerenciar sua fonte de dados – Oracle](service-gateway-onprem-manage-oracle.md)
* [Gerenciar sua fonte de dados – Importar/Atualização agendada](service-gateway-enterprise-manage-scheduled-refresh.md)
* [Diretrizes para implantar um gateway de dados](service-gateway-deployment-guidance.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
