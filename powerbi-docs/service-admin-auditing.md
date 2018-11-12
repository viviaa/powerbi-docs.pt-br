---
title: Usando a auditoria dentro da sua organização
description: Saiba como você pode usar a auditoria com o Power BI para monitorar e investigar as ações executadas. Você pode usar a Central de segurança e conformidade ou usar o PowerShell.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 294fb3a0142908ce0ab068e075ce39f950a0b124
ms.sourcegitcommit: d20f74d5300197a0930eeb7db586c6a90403aabc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2018
ms.locfileid: "50973340"
---
# <a name="using-auditing-within-your-organization"></a>Usando a auditoria dentro da sua organização

Saber quem está executando uma ação em qual item em seu locatário do Power BI pode ser essencial para ajudar a organização a atender seus requisitos, como gerenciamento de registros e conformidade regulamentar. Use a auditoria do Power BI para auditar as ações executadas pelos usuários, como "Exibir Relatório" e "Exibir Dashboard". Você não pode usar a auditoria para auditar permissões.

Trabalhe com a auditoria no Centro de Conformidade e Segurança do Office 365 ou use o PowerShell. Abordaremos as duas opções neste artigo. Você pode filtrar os dados de auditoria por intervalo de datas, usuário, dashboard, tipo de relatório, conjunto de dados e tipo de atividade. Você também pode baixar as atividades em um arquivo csv (valores separados por vírgula) para analisar offline.

## <a name="requirements"></a>Requisitos

Você deve atender a esses requisitos para acessar logs de auditoria:

- Para acessar a seção de auditoria do Centro de Conformidade e Segurança do Office 365, você deve ter uma licença do Exchange Online (incluída nas assinaturas do Office 365 Enterprise E3 e E5).

- Você deve ser um administrador global ou ter uma função de administrador do Exchange que fornece acesso ao log de auditoria. As funções de administrador do Exchange são controladas por meio do centro de administração do Exchange. Para obter mais informações, veja [Permissões no Exchange Online](/exchange/permissions-exo/permissions-exo/).

- Se você tiver acesso ao log de auditoria, mas não for um administrador global ou administrador de serviço do Power BI, você não terá acesso ao portal de administração do Power BI. Nesse caso, você deve obter um link direto para o [Centro de Conformidade e Segurança do Office 365](https://sip.protection.office.com/#/unifiedauditlog).

- Para exibir logs de auditoria para o Power BI em seu locatário, você precisará de pelo menos uma licença de caixa de correio do Exchange em seu locatário.

## <a name="accessing-your-audit-logs"></a>Acesso a logs de auditoria

Para acessar os logs, primeiro certifique-se de que o log esteja habilitado no Power BI. Para saber mais, confira [Logs de auditoria](service-admin-portal.md#audit-logs) na documentação do portal do administrador. Pode haver um atraso de até 48 horas entre a habilitação da auditoria e a possibilidade de exibir dados de auditoria. Se os dados não forem exibidos imediatamente, verifique os logs de auditoria mais tarde. Pode haver um atraso semelhante entre a obtenção da permissão para exibir os logs de auditoria e a possibilidade de acessá-los.

Os logs de auditoria do Power BI estão disponíveis diretamente no [Centro de Conformidade e Segurança do Office 365](https://sip.protection.office.com/#/unifiedauditlog). Também há um link no portal de administração do Power BI:

1. No Power BI, selecione o **ícone de engrenagem** no canto superior direito e escolha **Portal de administração**.

   ![Portal de administração](media/service-admin-auditing/powerbi-admin.png)

1. Selecione **Logs de Auditoria**.

1. Selecione **Ir para o Centro de Administração do O365**.

   ![Acessar o Centro de Administração do O365](media/service-admin-auditing/audit-log-o365-admin-center.png)

Para fornecer acesso ao log de auditoria a contas que não são de administrador, atribua permissões no Centro de Administração do Exchange Online. Por exemplo, você pode atribuir um usuário a um grupo de função existente, como o gerenciamento de organização, ou você pode criar um novo grupo de função com a função de Logs de Auditoria. Para obter mais informações, veja [Permissões no Exchange Online](/exchange/permissions-exo/permissions-exo/).

## <a name="search-only-power-bi-activities"></a>Pesquisar somente as atividades do Power BI

Restrinja os resultados apenas para as atividades do Power BI fazendo o seguinte. Para obter uma lista de atividades, confira a [lista de atividades auditadas pelo Power BI](#list-of-activities-audited-by-power-bi) mais adiante neste artigo.

1. Na página **Pesquisa de log de auditoria**, em **Pesquisa**, selecione o menu suspenso para **Atividades**.

2. Selecione **Atividades do Power BI**.

   ![Pesquisa de logs de auditoria](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Selecione qualquer lugar fora da caixa de seleção para fechá-la.

As pesquisas agora serão filtradas para apenas as atividades do Power BI.

## <a name="search-the-audit-logs-by-date"></a>Pesquisar os logs de auditoria por data

Você pode pesquisar os logs por intervalo de datas usando os campos **Data de início** e **Data de término**. Os últimos sete dias são selecionados por padrão. A data e hora são apresentadas no formato UTC (Tempo Universal Coordenado). O intervalo de datas máximo que você pode especificar é 90 dias. 

Um erro será exibido se o intervalo de datas selecionado for maior que 90 dias. Se você estiver usando o intervalo de datas máximo de 90 dias, selecione a hora atual para a **Data de início**. Caso contrário, você receberá uma mensagem de erro informando que a data de início é anterior à data de término. Se você ativou a auditoria nos últimos 90 dias, o intervalo de datas não poderá começar antes da data na qual a auditoria foi ativada.

![](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Pesquisar os logs de auditoria por usuários

Você pode procurar por entradas de log de auditoria de atividades executadas por usuários específicos. Para fazer isso, insira um ou mais nomes de usuário no campo **Usuários**. O nome de usuário se parece com um endereço de email; é a conta com a qual os usuários fazem logon no Power BI. Deixe esta caixa em branco para retornar as entradas para todos os usuários (e contas de serviço) em sua organização.

![Pesquisar por data](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="view-search-results"></a>Exibir resultados da pesquisa

Após a seleção de **Pesquisar**, os resultados da pesquisa são carregados e, após alguns instantes, são exibidos em **Resultados**. Quando a pesquisa é concluída, o número de resultados encontrados é exibido. No máximo 1000 eventos são exibidos; se mais de 1000 eventos atenderem aos critérios da pesquisa, os 1000 eventos mais recentes serão exibidos.

### <a name="view-the-main-results"></a>Exibir os resultados principais

A área **Resultados** contém as seguintes informações sobre cada evento retornado pela pesquisa. Selecione um cabeçalho de coluna em **Resultados** para classificar os resultados.

| **Coluna** | **Definição** |
| --- | --- |
| Date |A data e a hora (no formato UTC) quando o evento ocorreu. |
| Endereço IP |O endereço IP do dispositivo usado quando a atividade foi registrada. O endereço IP é exibido no formato de endereço IPv4 ou IPv6. |
| Usuário |O usuário (ou a conta de serviço) que executou a ação que acionou o evento. |
| Atividade |A atividade executada pelo usuário. Esse valor corresponde às atividades que você selecionou na lista suspensa **Atividades**. Para um evento do log de auditoria de administrador do Exchange, o valor desta coluna é um cmdlet do Exchange. |
| Item |O objeto foi criado ou modificado como resultado da atividade correspondente. Por exemplo, o arquivo que foi exibido ou modificado ou a conta de usuário que foi atualizada. Nem todas as atividades têm um valor nesta coluna. |
| Detalhe |Detalhes adicionais sobre uma atividade. Novamente, nem todas as atividades terão um valor. |

### <a name="view-the-details-for-an-event"></a>Exibir os detalhes de um evento

Você pode exibir mais detalhes sobre um evento clicando no registro do evento na lista de resultados da pesquisa. É exibida uma página **Detalhes** contendo as propriedades detalhadas do registro do evento. As propriedades exibidas dependem do serviço do Office 365 em que o evento ocorre. 

Para exibir esses detalhes, selecione **Mais informações**. Todas as entradas do Power BI têm um valor de 20 para a propriedade RecordType. Para saber mais sobre outras propriedades, confira [Propriedades detalhadas no log de auditoria](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/).

   ![Detalhes da auditoria](media/service-admin-auditing/audit-details.png)

## <a name="export-search-results"></a>Exportar resultados da pesquisa

Para exportar o log de auditoria do Power BI para um arquivo csv, execute estas etapas.

1. Selecione **Exportar resultados**.

1. Selecione **Salvar resultados carregados** ou **Baixar todos os resultados**.

    ![Exportar resultados](media/service-admin-auditing/export-auditing-results.png)

## <a name="use-powershell-to-search-audit-logs"></a>Usar o PowerShell para pesquisar logs de auditoria

Você também pode usar o PowerShell para acessar os logs de auditoria com base em seu logon. O exemplo a seguir mostra como usar o comando [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) para efetuar o pull de entradas de log de auditoria do Power BI.

Para usar o comando [New-PSSession](/powershell/module/microsoft.powershell.core/new-pssession/), sua conta precisa ter uma licença do Exchange Online atribuída, e você precisa ter acesso ao log de auditoria do seu locatário. Para obter mais informações sobre como se conectar ao Exchange Online, consulte [Conectar ao Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/).

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

Para ver outro exemplo de como usar o PowerShell com os logs de auditoria, confira [Usar o log de auditoria do Power BI e o PowerShell para atribuir licenças do Power BI Pro](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/).

## <a name="activities-audited-by-power-bi"></a>Atividades auditadas pelo Power BI

As atividades a seguir são auditadas pelo Power BI.

* AddDatasourceToGateway
* AddGroupMembers
* AnalyzedByExternalApplication
* AnalyzeInExcel
* AttachDataflowStorageAccount
* BindToGateway
* ChangeCapacityState
* ChangeGatewayAdministrators
* ChangeGatewayDatasourceUsers
* CreateApp
* CreateDashboard
* CreateDataflow
* CreateDataset
* CreateEmailSubscription
* CreateFolder
* CreateGateway
* CreateGroup
* CreateOrgApp
* CreateReport
* DeleteComment
* DeleteDashboard
* DeleteDataflow
* DeleteDataset
* DeleteEmailSubscription
* DeleteFolder
* DeleteGateway
* DeleteGroup
* DeleteGroupMembers
* DeleteOrgApp
* DeleteReport
* DownloadReport
* EditDataset
* EditReport
* ExportDataflow
* ExportReport
* ExportTile
* GenerateDataflowSasToken
* GenerateEmbedToken
* GetDatasources
* Importar
* InstallApp
* MigrateWorkspaceIntoCapacity
* OptInForProTrial
* PostComment
* PrintDashboard
* PrintReport
* PublishToWebReport
* RefreshDataset
* RemoveDatasourceFromGateway
* RemoveWorkspacesFromCapacity
* RenameDashboard
* SetAllConnections
* SetScheduledRefresh
* SetScheduledRefreshOnDataflow
* ShareDashboard
* ShareReport
* TakeOverDataset
* TakeOverDatasource
* UnpublishApp
* UpdateApp
* UpdateCapacityAdmins
* UpdateCapacityDisplayName
* UpdateCapacityResourceGovernanceSettings
* UpdateCapacityUsersAssignment
* UpdatedAdminFeatureSwitch
* UpdateDataflow
* UpdateDatasetParameters
* UpdateDatasourceCredentials
* UpdateDatasources
* UpdateEmailSubscription
* UpdateFolder
* UpdateFolderAccess
* ViewDashboard
* ViewDataflow
* ViewReport
* ViewTile
* ViewUsageMetrics

## <a name="next-steps"></a>Próximas etapas

[O que é administração do Power BI?](service-admin-administering-power-bi-in-your-organization.md)  

[Portal de administração do Power BI](service-admin-portal.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
