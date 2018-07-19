---
title: Inserir conteúdo do Power BI em um aplicativo para sua organização
description: Aprenda a integrar, ou inserir, um relatório, um dashboard ou um bloco em um aplicativo Web usando as APIs do Power BI para sua organização.
author: markingmyname
ms.author: maghan
ms.date: 07/13/2018
ms.topic: tutorial
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: cfc450216202f332f518955d28cb71df6aa0b800
ms.sourcegitcommit: f2b106b5eb338a64f903e8ce6793bccb07f9440a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/18/2018
ms.locfileid: "39105259"
---
# <a name="tutorial-embed-a-power-bi-report-dashboard-or-tile-into-an-application-for-your-organization"></a>Tutorial: inserir um relatório, um dashboard ou um bloco do Power BI em um aplicativo para sua organização
Este tutorial demonstra como integrar um relatório em um aplicativo usando o **SDK do .NET do Power BI** juntamente com a **API JavaScript do Power BI** ao inserir o **Power BI** em um aplicativo para sua organização. Com o **Power BI**, você pode inserir relatórios, dashboards e blocos em um aplicativo usando **user owns data**. O **user owns data** permite que o aplicativo estenda o serviço do Power BI.

![Exibir o aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-035.png)

Neste tutorial, você aprenderá a:
>[!div class="checklist"]
>* Registrar um aplicativo no Azure.
>* Insira um relatório do Power BI em um aplicativo.

## <a name="prerequisites"></a>Pré-requisitos
Para começar, você precisa de uma conta **Power BI Pro** e uma assinatura do **Microsoft Azure**.

* Se não estiver inscrito no **Power BI Pro**, [inscreva-se para uma avaliação gratuita](https://powerbi.microsoft.com/en-us/pricing/) antes de começar.
* Caso você não tenha uma assinatura do Azure, crie uma [conta gratuita](https://azure.microsoft.com/free/?WT.mc_id=A261C142F) antes de começar.
* Você precisa ter seu próprio [locatário do Azure Active Directory](create-an-azure-active-directory-tenant.md) configurado.
* Você precisa do [Visual Studio](https://www.visualstudio.com/) instalado (versão 2013 ou posterior).

## <a name="setup-your-embedded-analytics-development-environment"></a>Configurar seu ambiente de desenvolvimento de análise integrada

Antes de começar a inserir relatórios, painéis ou blocos em seu aplicativo, você precisará verificar se o ambiente está configurado para permitir a inserção. Como parte da instalação, você precisa fazer o seguinte.

Você pode examinar a [Ferramenta de experiência de integração](https://aka.ms/embedsetup/UserOwnsData) para iniciar rapidamente e baixar um aplicativo de exemplo que ajuda a criar um ambiente e a inserir um relatório.

No entanto, se você optar por configurar o ambiente manualmente, você poderá continuar abaixo.
### <a name="register-an-application-in-azure-active-directory-azure-ad"></a>Registrar um aplicativo no Azure AD (Azure Active Directory)

Registre seu aplicativo no Azure Active Directory para permitir que ele tenha acesso às APIs REST do Power BI. Isso permite que você estabeleça uma identidade para seu aplicativo e especifique permissões para recursos REST do Power BI.

1. Aceite os [Termos da API do Microsoft Power BI](https://powerbi.microsoft.com/api-terms).

2. Entre no [Portal do Azure](https://portal.azure.com).

    ![Página principal do portal do Azure](media/embed-sample-for-your-organization/embed-sample-for-your-organization-002.png)

3. No painel de navegação esquerdo, escolha **Todos os Serviços**, selecione **Registros de Aplicativo** e, em seguida, selecione **Novo registro de aplicativo**.

    ![Pesquisa de registro de aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-003.png)</br>
    ![Registro de novo aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-004.png)

4. Siga os prompts e crie um novo aplicativo. Para **user owns data** você precisará usar o **aplicativo Web/API** para o tipo de aplicativo. Você também precisará fornecer uma **URL de logon**, que o **Azure AD** usará para retornar respostas de token. Insira um valor específico para seu aplicativo (por exemplo, http://localhost:13526/).

    ![Criar Aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-005.png)

### <a name="apply-permissions-to-your-application-within-azure-active-directory"></a>Aplique permissões ao seu aplicativo no Azure Active Directory

Você precisa habilitar permissões adicionais para seu aplicativo além do que foi fornecido na página de registro do aplicativo. Você precisa estar conectado com uma conta de *administrador global* para habilitar as permissões.

### <a name="use-the-azure-active-directory-portal"></a>Use o portal do Azure Active Directory

1. Navegue até [Registros de aplicativo](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ApplicationsListBlade) no Portal do Azure e selecione o aplicativo que você está usando para inserção.

    ![Escolhendo o aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-006.png)

2. Selecione **Configurações** e, em **Acesso à API**, selecione **Permissões necessárias**.

    ![Permissões necessárias](media/embed-sample-for-your-organization/embed-sample-for-your-organization-008.png)

3. Selecione **Microsoft Azure Active Directory** e, em seguida, certifique-se de **Acessar o diretório como o usuário conectado** esteja selecionado. Selecione **Salvar**.

    ![Permissões do Microsoft Azure AD](media/embed-sample-for-your-organization/embed-sample-for-your-organization-011.png)

4. Selecione **Adicionar**.

    ![Adicionar permissões](media/embed-sample-for-your-organization/embed-sample-for-your-organization-012.png)

5. Selecione **Selecionar uma API**.

    ![Adicionar acesso à API](media/embed-sample-for-your-organization/embed-sample-for-your-organization-013.png)

6. Selecione **Serviço do Power BI** e, em seguida, selecione **Selecionar**.

    ![Selecione Serviços do PBI](media/embed-sample-for-your-organization/embed-sample-for-your-organization-014.png)

7. Selecione todas as permissões em **Permissões Delegadas**. É necessário selecionar uma a uma para salvar as seleções. Selecione **Salvar** quando terminar.

    ![Selecione permissões delegadas](media/embed-sample-for-your-organization/embed-sample-for-your-organization-015.png)

## <a name="setup-your-power-bi-environment"></a>Configure seu ambiente do Power BI

### <a name="create-an-app-workspace"></a>Criar um espaço de trabalho de aplicativo

Se estiver inserindo relatórios, dashboards ou blocos para seus clientes, você precisará colocar o conteúdo dentro de um espaço de trabalho do aplicativo.

1. Comece criando o espaço de trabalho. Selecione **espaços de trabalho** > **Criar espaço de trabalho do aplicativo**. Trata-se do local em que é colocado o conteúdo que seu aplicativo precisa acessar.

    ![Criar espaço de trabalho](media/embed-sample-for-your-organization/embed-sample-for-your-organization-020.png)

2. Nomeie o espaço de trabalho. Se a **ID do Espaço de Trabalho** correspondente não estiver disponível, edite-a para criar uma ID exclusiva. Esse também precisa ser o nome do aplicativo.

    ![Nomeie o espaço de trabalho](media/embed-sample-for-your-organization/embed-sample-for-your-organization-021.png)

3. Você tem algumas opções para definir. Se você escolher **Público**, qualquer pessoa na sua organização poderá ver o que está no espaço de trabalho. **Particular**, por outro lado, significará que somente os membros do espaço de trabalho poderão ver o conteúdo.

    ![Particular/Público](media/embed-sample-for-your-organization/embed-sample-for-your-organization-022.png)

    Não é possível alterar a configuração Público/Particular depois de criar o grupo.

4. Também é possível escolher se os membros podem **editar** ou se terão acesso **somente exibição**.

    ![Adicionando membros](media/embed-sample-for-your-organization/embed-sample-for-your-organization-023.png)

5. Adicione os endereços de email das pessoas que você deseja que tenham acesso ao espaço de trabalho e selecione **Adicionar**. Você não pode adicionar aliases de grupos, apenas indivíduos.

6. Decida se cada pessoa será um membro ou um administrador. Os administradores podem editar o espaço de trabalho, incluindo a adição de outros membros. Os membros podem editar o conteúdo no espaço de trabalho, a menos que tenham acesso somente exibição. Os membros e os administradores podem publicar o aplicativo.

    Agora, você pode exibir o novo espaço de trabalho. O Power BI cria o espaço de trabalho e o abre. Ele aparece na lista de espaços de trabalho dos quais você é um membro. Como você é um administrador, você pode selecionar as reticências (...) para voltar e fazer alterações, adicionar novos membros ou alterar as permissões deles.

    ![Criar espaço de trabalho](media/embed-sample-for-your-organization/embed-sample-for-your-organization-025.png)

### <a name="create-and-publish-your-reports"></a>Crie e publique seus relatórios

É possível criar seus relatórios e conjuntos de dados usando o Power BI Desktop e, em seguida, publicar esses relatórios em um espaço de trabalho do aplicativo. O usuário final que publicar os relatórios precisará ter uma licença do Power BI Pro para publicar em um espaço de trabalho do aplicativo.

1. Baixe o exemplo [Blog Demo](https://github.com/Microsoft/powerbi-desktop-samples) do GitHub.

    ![relatório de exemplo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-026-1.png)

2. Abra o relatório de exemplo do PBIX no **Power BI Desktop**

   ![Relatório de área de trabalho do PBI](media/embed-sample-for-your-organization/embed-sample-for-your-organization-027.png)

3. Publique no **espaço de trabalho do aplicativo**

   ![Relatório de área de trabalho do PBI](media/embed-sample-for-your-organization/embed-sample-for-your-organization-028.png)

    Agora, você pode exibir o relatório no serviço do Power BI online.

   ![Relatório de área de trabalho do PBI](media/embed-sample-for-your-organization/embed-sample-for-your-organization-029.png)

## <a name="embed-your-content-using-the-sample-application"></a>Insira o conteúdo usando o aplicativo de exemplo

Execute estas etapas para começar a incorporar o conteúdo usando um aplicativo de exemplo.

1. Baixe o [exemplo User Owns Data](https://github.com/Microsoft/PowerBI-Developer-Samples) do GitHub para começar.  Há três aplicativos de exemplo diferente, um para [relatórios](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-report-web-app), um para [dashboards](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-dashboard-web-app) e outro para [blocos](https://github.com/Microsoft/PowerBI-Developer-Samples/tree/master/User%20Owns%20Data/integrate-tile-web-app).  Este artigo refere-se ao aplicativo de **relatórios** que abordaremos nas etapas abaixo.

    ![Amostra do aplicativo User Owns Data](media/embed-sample-for-your-organization/embed-sample-for-your-organization-026.png)

2. Abra o arquivo Cloud.config no aplicativo de exemplo. Há alguns campos que você precisa preencher para executar o aplicativo com êxito. O **ClientID** e o **ClientSecret**.

    ![Arquivo de configuração de nuvem](media/embed-sample-for-your-organization/embed-sample-for-your-organization-030.png)

    Preencha a informação de **ClientID** com a **ID do aplicativo** do **Azure**. A **ClientID** é usada pelo aplicativo para identificar-se aos usuários para os quais está solicitando permissões.

    Para obter a **ClientID**, siga estas etapas:

    Entre no [Portal do Azure](https://portal.azure.com).

    ![Página principal do portal do Azure](media/embed-sample-for-your-organization/embed-sample-for-your-organization-002.png)

    No painel de navegação esquerdo, escolha **Todos os Serviços** e selecione **Registros de Aplicativo**.

    ![Pesquisa de registro de aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-003.png)

    Selecione o aplicativo que precisa usar a **ClientID**.

    ![Escolhendo o aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-006.png)

    Você deve ver uma **ID do Aplicativo** listada como um GUID. Use essa **ID do aplicativo** como a **ClientID** do aplicativo.

    ![ClientID](media/embed-sample-for-your-organization/embed-sample-for-your-organization-007.png)

    Preencha a informação de **ClientSecret** da seção **Chaves**, na seção **Registros do aplicativo** no **Azure**.

    Para obter o **ClientSecret**, siga estas etapas:

    Entre no [Portal do Azure](https://portal.azure.com).

    ![Página principal do portal do Azure](media/embed-sample-for-your-organization/embed-sample-for-your-organization-002.png)

    No painel de navegação esquerdo, escolha **Todos os Serviços** e selecione **Registros de Aplicativo**.

    ![Pesquisa de registro de aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-003.png)

    Selecione o aplicativo que precisa usar o **ClientSecret**.

    ![Escolhendo o aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-006.png)

    Selecione **Configurações**.

    ![Configurações](media/embed-sample-for-your-organization/embed-sample-for-your-organization-038.png)

    Selecione **Chaves**.

    ![Chaves](media/embed-sample-for-your-organization/embed-sample-for-your-organization-039.png)

    Preencha a **Descrição** com um nome, selecione uma **Duração** e, em seguida, selecione **Salvar** para obter o **Valor** do aplicativo. Quando você fechar a folha **Chaves**, depois de salvar o **valor da chave**, o campo de valor será mostrado apenas como **_Oculto_** e, nesse ponto, não será mais possível recuperar o **valor da chave**. Se você perder o **valor da chave**, será necessário criar um novo no **portal do Azure**.

    ![Chaves](media/embed-sample-for-your-organization/embed-sample-for-your-organization-031.png)

     Preencha as informações de **groupId** com o **GUID de espaço de trabalho do aplicativo** do Power BI.

    ![groupId](media/embed-sample-for-customers/embed-sample-for-customers-031.png)

    Preencha as informações de **reportId** com o **GUID de relatório** do Power BI.

    ![reportId](media/embed-sample-for-customers/embed-sample-for-customers-032.png)

3. Execute o aplicativo!

    Primeiro, selecione **Executar** no **Visual Studio**.

    ![Execute o aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-033.png)

    Em seguida, selecione **Obter Relatório**.

    ![Selecione um conteúdo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-034.png)

    Agora, você pode exibir o relatório no aplicativo de exemplo.

    ![Exibir o aplicativo](media/embed-sample-for-your-organization/embed-sample-for-your-organization-035.png)

## <a name="embed-your-content-within-your-application"></a>Insira o conteúdo dentro de seu aplicativo
Embora as etapas para inserir seu conteúdo possam ser feitas com as [APIs REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/), os códigos de exemplo descritos neste artigo são feitos com o **SDK do .NET**.

Para integrar um relatório em um aplicativo Web, use a **API REST do Power BI** ou o **SDK do C# do Power BI** e um **token de acesso** de autorização do AD (Azure Active Directory) para obter um relatório. Em seguida, carregue o relatório usando o mesmo **token de acesso**. A **API REST do Power BI** fornece acesso programático a recursos específicos do **Power BI**. Para obter mais informações, confira [Visão geral da API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/) e a [API JavaScript do Power BI](https://github.com/Microsoft/PowerBI-JavaScript).

### <a name="get-an-access-token-from-azure-ad"></a>Obter um token de acesso do Azure AD
No aplicativo, primeiro você precisa obter um **token de acesso** do Azure AD para que seja possível fazer chamadas à API REST do Power BI. Para obter mais informações, consulte [Autenticar usuários e obter um token de acesso do Azure AD para o aplicativo do Power BI](get-azuread-access-token.md).

### <a name="get-a-report"></a>Obter um relatório
Para obter um relatório do **Power BI**, use a operação [Obter Relatórios](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) que obtém uma lista de **relatórios do Power BI**. Na lista de relatórios, obtenha uma ID de relatório.

### <a name="get-reports-using-an-access-token"></a>Obter relatórios usando um token de acesso
A operação [Obter Relatórios](https://docs.microsoft.com/rest/api/power-bi/reports/getreports) retorna uma lista de relatórios. É possível obter um relatório individual na lista de relatórios.

Para fazer a chamada à API REST, você deve incluir um cabeçalho *Autorização* no formato *Portador {token de acesso}*.

#### <a name="get-reports-with-the-rest-api"></a>Obter relatórios com a API REST

Aqui está um exemplo de código de como recuperar relatórios com a **API REST**.

*Há um exemplo de como obter um item de conteúdo que você deseja inserir (relatório, dashboard ou bloco) disponível no arquivo **_Default.aspx.cs_** no [aplicativo de exemplo](#embed-your-content-using-the-sample-application).*

```csharp
using Newtonsoft.Json;

//Get a Report. In this sample, you get the first Report.
protected void GetReport(int index)
{
    //Configure Reports request
    System.Net.WebRequest request = System.Net.WebRequest.Create(
        String.Format("{0}/Reports",
        baseUri)) as System.Net.HttpWebRequest;

    request.Method = "GET";
    request.ContentLength = 0;
    request.Headers.Add("Authorization", String.Format("Bearer {0}", accessToken.Value));

    //Get Reports response from request.GetResponse()
    using (var response = request.GetResponse() as System.Net.HttpWebResponse)
    {
        //Get reader from response stream
        using (var reader = new System.IO.StreamReader(response.GetResponseStream()))
        {
            //Deserialize JSON string
            PBIReports Reports = JsonConvert.DeserializeObject<PBIReports>(reader.ReadToEnd());

            //Sample assumes at least one Report.
            //You could write an app that lists all Reports
            if (Reports.value.Length > 0)
            {
                var report = Reports.value[index];

                txtEmbedUrl.Text = report.embedUrl;
                txtReportId.Text = report.id;
                txtReportName.Text = report.name;
            }
        }
    }
}

//Power BI Reports used to deserialize the Get Reports response.
public class PBIReports
{
    public PBIReport[] value { get; set; }
}
public class PBIReport
{
    public string id { get; set; }
    public string name { get; set; }
    public string webUrl { get; set; }
    public string embedUrl { get; set; }
}
```

#### <a name="get-reports-using-the-net-sdk"></a>Obter relatórios usando o SDK do .NET
Use o SDK do .NET para recuperar uma lista de relatórios, em vez de chamar a API REST diretamente. Aqui está um exemplo de código de como listar relatórios.

```csharp
using Microsoft.IdentityModel.Clients.ActiveDirectory;
using Microsoft.PowerBI.Api.V2;
using Microsoft.PowerBI.Api.V2.Models;

var tokenCredentials = new TokenCredentials(<ACCESS TOKEN>, "Bearer");

// Create a Power BI Client object. It is used to call Power BI APIs.
using (var client = new PowerBIClient(new Uri(ApiUrl), tokenCredentials))
{
    // Get the first report all reports in that workspace
    ODataResponseListReport reports = client.Reports.GetReports();

    Report report = reports.Value.FirstOrDefault();

    var embedUrl = report.EmbedUrl;
}
```

### <a name="load-a-report-using-javascript"></a>Carregar um relatório usando JavaScript
Use o JavaScript para carregar um relatório em um elemento div na página da Web.

Aqui está um exemplo de código de como recuperar um relatório de um determinado espaço de trabalho.

*Há um exemplo de como obter um item de conteúdo, seja um dashboard, um relatório ou um bloco que você deseja inserir disponível no arquivo **_Default.aspx_** no [aplicativo de exemplo](#embed-your-content-using-the-sample-application).*

```javascript
<!-- Embed Report-->
<div> 
    <asp:Panel ID="PanelEmbed" runat="server" Visible="true">
        <div>
            <div><b class="step">Step 3</b>: Embed a report</div>

            <div>Enter an embed url for a report from Step 2 (starts with https://):</div>
            <input type="text" id="tb_EmbedURL" style="width: 1024px;" />
            <br />
            <input type="button" id="bEmbedReportAction" value="Embed Report" />
        </div>

        <div id="reportContainer"></div>
    </asp:Panel>
</div>
```

**Site.master**

```javascript
window.onload = function () {
    // client side click to embed a selected report.
    var el = document.getElementById("bEmbedReportAction");
    if (el.addEventListener) {
        el.addEventListener("click", updateEmbedReporte, false);
    } else {
        el.attachEvent('onclick', updateEmbedReport);
    }

    // handle server side post backs, optimize for reload scenarios
    // show embedded report if all fields were filled in.
    var accessTokenElement = document.getElementById('MainContent_accessTokenTextbox');
    if (accessTokenElement !== null) {
        var accessToken = accessTokenElement.value;
        if (accessToken !== "")
            updateEmbedReport();
    }
};

// update embed report
function updateEmbedReport() {

    // check if the embed url was selected
    var embedUrl = document.getElementById('tb_EmbedURL').value;
    if (embedUrl === "")
        return;

    // get the access token.
    accessToken = document.getElementById('MainContent_accessTokenTextbox').value;

    // Embed configuration used to describe the what and how to embed.
    // This object is used when calling powerbi.embed.
    // You can find more information at https://github.com/Microsoft/PowerBI-JavaScript/wiki/Embed-Configuration-Details.
    var config = {
        type: 'report',
        accessToken: accessToken,
        embedUrl: embedUrl
    };

    // Grab the reference to the div HTML element that will host the report.
    var reportContainer = document.getElementById('reportContainer');

    // Embed the report and display it within the div container.
    var report = powerbi.embed(reportContainer, config);

    // report.on will add an event handler which prints to Log window.
    report.on("error", function (event) {
        var logView = document.getElementById('logView');
        logView.innerHTML = logView.innerHTML + "Error<br/>";
        logView.innerHTML = logView.innerHTML + JSON.stringify(event.detail, null, "  ") + "<br/>";
        logView.innerHTML = logView.innerHTML + "---------<br/>";
    }
  );
}
```

## <a name="using-a-power-bi-premium-dedicated-capacity"></a>Usando uma capacidade dedicada do Power BI Premium

Agora que você terminou o desenvolvimento do seu aplicativo, é hora de conferir uma capacidade dedicada ao espaço de trabalho do seu aplicativo.

### <a name="create-a-dedicated-capacity"></a>Criar uma capacidade dedicada
Ao criar uma capacidade dedicada, você pode usufruir de um recurso dedicado ao conteúdo no espaço de trabalho do aplicativo. Quando um espaço de trabalho não está atribuído a uma capacidade dedicada, ele é considerado uma capacidade compartilhada. Você pode criar uma capacidade dedicada usando o [Power BI Premium ](../service-admin-premium-purchase.md).

### <a name="assign-an-app-workspace-to-a-dedicated-capacity"></a>Atribua um espaço de trabalho de aplicativo a uma capacidade dedicada

Depois de criar uma capacidade dedicada, você pode atribuir o espaço de trabalho do aplicativo a ela. Para concluir isso, execute estas etapas.

1. No **serviço do Power BI**, expanda os espaços de trabalho e selecione as reticências do espaço de trabalho que você está usando para inserir seu conteúdo. Depois, selecione **Editar espaços de trabalho**.

    ![Editar Espaço de Trabalho](media/embed-sample-for-your-organization/embed-sample-for-your-organization-036.png)

2. Expanda **Avançado**, habilite **Capacidade dedicada** e selecione a capacidade dedicada criada por você. Depois, selecione **Salvar**.

    ![Atribuir capacidade dedicada](media/embed-sample-for-your-organization/embed-sample-for-your-organization-024.png)

3. Depois que você selecionar **Salvar**, será exibido um **losango** próximo ao nome do espaço de trabalho do aplicativo.

    ![espaço de trabalho do aplicativo vinculado a uma capacidade](media/embed-sample-for-your-organization/embed-sample-for-your-organization-037.png)

## <a name="next-steps"></a>Próximas etapas
Neste tutorial, você aprendeu como inserir conteúdo do Power BI em um aplicativo usando a **conta da organização do Power BI**. Agora, você pode tentar inserir o conteúdo do Power BI em um aplicativo usando aplicativos.  Você também pode tentar inserir o conteúdo do Power BI para clientes de terceiros.

> [!div class="nextstepaction"]
> [Inserir de aplicativos](embed-from-apps.md)

> [!div class="nextstepaction"]
>[Inserir para clientes de terceiros](embed-sample-for-customers.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
