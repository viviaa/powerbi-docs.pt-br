---
title: Inserir um relatório em um site ou portal seguro
description: O Power BI insere o recurso permite que os usuários facilmente e com segurança incorporar relatórios em portais da web interno.
author: rkarlin
ms.author: rkarlin
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/20/2019
LocalizationGroup: Share your work
ms.openlocfilehash: bf9d7bcdf6ddaf7d0063843a5314233989b2dadd
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222254"
---
# <a name="embed-a-report-in-a-secure-portal-or-website"></a>Inserir um relatório em um site ou portal seguro

Com o novo **inserção** relatórios de opção para o Power BI, você pode facilmente e com segurança incorporar relatórios em portais da web interno. Esses portais podem ser **baseado em nuvem** ou **hospedados no local**, como o SharePoint 2019. Relatórios inseridos respeitarem todas as permissões e dados de segurança dos itens por meio [RLS (segurança) de nível de linha](service-admin-rls.md). Eles fornecem sem código de inserção em qualquer portal que aceita uma URL ou um iFrame. 

O **Embed** opção dá suporte a [filtros de URL](service-url-filters.md) e configurações de URL. Ele permite a integração com portais usando uma abordagem pouco código exigir apenas conhecimento básico de HTML e JavaScript.

## <a name="how-to-embed-power-bi-reports-into-portals"></a>Como **Inserir** relatórios do Power BI em portais

1. A nova opção **Inserir** está disponível no menu **Arquivo** para relatórios no serviço do Power BI.

    ![Opção da lista suspensa da opção Inserir segura](media/service-embed-secure/secure-embed-drop-down-menu.png)

2. Selecione o **inserção** opção para abrir uma caixa de diálogo que fornece um link e um iFrame, você pode usar para inserir o relatório de forma segura.

    ![Caixa de diálogo da opção Inserir](media/service-embed-secure/secure-embed-code-dialog.png)

3. Se um usuário abre uma URL de relatório diretamente, ou um inserido em um portal da web, o acesso ao relatório exige autenticação. A tela a seguir será exibida se um usuário não entrou no Power BI em sua sessão do navegador. Quando eles selecionam **entrar**, foi possível abrir uma nova janela ou guia. Peça para verificar os bloqueadores de pop-up se eles não solicitados a entrar.

    ![Entrar para exibir este relatório](media/service-embed-secure/secure-embed-sign-in.png)

4. Depois que o usuário tiver entrado, o relatório é aberto, mostrando os dados e permitindo a navegação de página e a configuração de filtro. Somente os usuários que têm permissão de exibição podem ver o relatório no Power BI. Todos os [RLS (segurança) de nível de linha](service-admin-rls.md) regras também são aplicadas. Por último, o usuário precisa estar licenciado corretamente, ou precisa de uma licença do Power BI Pro ou o relatório deve estar em um espaço de trabalho que esteja em uma capacidade do Power BI Premium. O usuário precisa entrar em cada vez que abrirem uma nova janela do navegador. No entanto, depois de conectado, outros relatórios de carga automaticamente.

    ![Inserir relatório](media/service-embed-secure/secure-embed-report.png)

5. Ao usar um iFrame, talvez você precise editar o **altura** e **largura** para que ele se ajustar na página de web do seu portal.

    ![Definir altura e largura](media/service-embed-secure/secure-embed-size.png)

## <a name="granting-report-access"></a>Concedendo acesso ao relatório

O **inserção** opção automaticamente não permite que os usuários para exibir o relatório. Exibir permissões são definidas no serviço do Power BI.

No serviço do Power BI, você pode compartilhar relatórios incorporados com usuários que precisam de acesso. Se você estiver usando um grupo do Office 365, você pode listar o usuário como um membro do espaço de trabalho de aplicativo. Para obter mais informações, consulte como [gerenciar seu espaço de trabalho no Power BI e Office 365](service-manage-app-workspace-in-power-bi-and-office-365.md).

## <a name="licensing"></a>Licenças

Para exibir o relatório inserido, os usuários precisam de uma licença de Power BI Pro ou o conteúdo precisa estar em um espaço de trabalho que está em um [capacidade do Power BI Premium (EME ou SKU P)](service-admin-premium-purchase.md).

## <a name="customize-your-embed-experience-using-url-settings"></a>Personalizar sua experiência de inserção usando configurações de URL

Você pode personalizar a experiência do usuário usando as configurações de entrada da URL de inserção. No iFrame fornecido, você pode atualizar a URL **src** configurações.

| Propriedade  | Descrição  |  |  |  |
|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|---|---|
| pageName  | Você pode usar o **pageName** parâmetro de cadeia de caracteres para definir qual página de relatório para abrir consulta. Você pode encontrar esse valor no final da URL de relatório ao exibir um relatório no serviço do Power BI, conforme mostrado abaixo. |  |  |  |
| Filtros de URL  | Você pode usar [filtros de URL](service-url-filters.md) na URL de inserção que você recebeu da interface do usuário do Power BI para filtrar o conteúdo de inserção. Dessa forma, você pode criar integrações de código baixo tendo apenas experiências básicas em HTML e JavaScript.  |  |  |  |

## <a name="set-which-page-opens-for-an-embedded-report"></a>Conjunto de qual página é aberta para um relatório inserido 

Você pode encontrar o **pageName** valor final da URL de relatório ao exibir um relatório no serviço do Power BI.

1. Abra o relatório de serviço do Power BI em seu navegador da web e, em seguida, copie a URL da barra de endereço.

    ![Seção de relatório](media/service-embed-secure/secure-embed-report-section.png)

2. Anexe a configuração **pageName** à URL.

    ![Anexar pageName](media/service-embed-secure/secure-embed-append-page-name.png)

## <a name="filter-report-content-using-url-filters"></a>Filtrar o conteúdo do relatório usando filtros de URL 

Você pode usar [filtros de URL](service-url-filters.md) fornecer modos de exibição de relatório diferente. Por exemplo, a URL a seguir filtra o relatório para mostrar dados ao setor de energia.

Usar a combinação de **pageName** e [Filtros de URL](service-url-filters.md) pode ser poderosa. Você pode criar experiências usando HTML e JavaScript básicos.

Por exemplo, aqui está um botão que você pode adicionar a uma página HTML:

```html
<button class="textLarge" onclick='show("ReportSection", "Energy");' style="display: inline-block;">Show Energy</button>
```

Quando selecionada, o botão chama uma função para atualizar o iFrame com uma URL atualizada, que inclui o filtro do setor de energia.

```javascript
function show(pageName, filterValue)

{

var newUrl = baseUrl + "&pageName=" + pageName;

if(null != filterValue && "" != filterValue)

{

newUrl += "&$filter=Industries/Industry eq '" + filterValue + "'";

}

//Assumes there’s an iFrame on the page with id=”iFrame”

var report = document.getElementById("iFrame")

report.src = newUrl;

}
```

![Filtrar](media/service-embed-secure/secure-embed-filter.png)

Você pode adicionar quantos botões desejar para criar uma experiência personalizada de código baixo. 

## <a name="considerations-and-limitations"></a>Considerações e limitações

* Não há suporte a usuários convidados externos com integração entre empresas (B2B) do Azure.

* A inserção segura funciona para relatórios publicados no serviço do Power BI.

* O usuário precisa entrar exibir o relatório sempre que abrir uma nova janela do navegador.

* Alguns navegadores exigem que você atualize a página depois de entrar, especialmente ao usar os modos InPrivate ou anônimo.

* Para obter uma experiência de logon único, use a inserção na opção SharePoint Online ou criar uma integração personalizada usando o [o usuário possui dados](developer/embed-sample-for-your-organization.md) inserindo método. 

* O recurso de autenticação automática fornecido com a opção **Inserir** não funciona com a API JavaScript do Power BI. Para a API de JavaScript do Power BI, use o [o usuário possui dados](developer/embed-sample-for-your-organization.md) inserindo método. 

## <a name="next-steps"></a>Próximas etapas

* [Maneiras de compartilhar seu trabalho no Power BI](service-how-to-collaborate-distribute-dashboards-reports.md)

* [Filtrar um relatório usando parâmetros de cadeia de caracteres de consulta na URL](service-url-filters.md)

* [Inserir com web part de relatório no SharePoint Online](service-embed-report-spo.md)

* [Publicar na Web do Power BI](service-publish-to-web.md)