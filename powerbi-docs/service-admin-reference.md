---
title: Cmdlets do PowerShell, APIs REST e SDK do .NET para administradores
description: Saiba mais sobre as maneiras de administrar o Power BI por meio de scripts e APIs de programação.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: overview
ms.date: 06/25/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: f4455fef5a2ed0e7ee23ff8ca3a0b626cd695838
ms.sourcegitcommit: a1b7ca499f4ca7e90421511e9dfa61a33333de35
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51507981"
---
# <a name="powershell-cmdlets-rest-apis-and-net-sdk-for-power-bi-administration"></a>Cmdlets do PowerShell, APIs REST e SDK do .NET para a administração do Power BI
O Power BI permite aos administradores fazer scripts de tarefas comuns com os cmdlets do PowerShell. Ele também expõe as APIs REST e fornece um SDK do .NET para desenvolver soluções administrativas. Este tópico mostra uma lista de cmdlets e o método do SDK correspondente, bem como o ponto de extremidade da API REST. Para obter mais informações, veja:

  - [Download](https://www.powershellgallery.com/packages/MicrosoftPowerBIMgmt/) e [documentação](https://docs.microsoft.com/powershell/power-bi/overview?view=powerbi-ps) do PowerShell
  - [Documentação](https://docs.microsoft.com/rest/api/power-bi/admin) da API REST
  - [Download](https://www.nuget.org/packages/Microsoft.PowerBI.Api/) do SDK do .NET 


| **Nome do cmdlet** | **Método do SDK** | **Ponto de extremidade da API REST** | **Descrição** |
| --- | --- | --- | --- |
| **Get-PowerBIDatasource** | Conjuntos de dados\_GetDataSourcesAsAdmin | /v1.0/myorg/admin/datasets/{datasetkey}/datasources | Obtém as fontes de dados para um determinado conjunto de dados. |
| **Get-PowerBIDataset** | Conjuntos de dados\_GetDatasetsAsAdmin | /v1.0/myorg/admin/datasets | Obtém a lista completa de conjuntos de dados em um locatário do Power BI. |
| **Get-PowerBIWorkspace** | Grupos\_GetGroupsAsAdmin | /v1.0/myorg/admin/groups | Obtém a lista completa de workspaces em um locatário do Power BI. |
| **Add-PowerBIWorkspaceUser** | Grupos\_AddUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users | Adiciona um usuário como um membro a um determinado workspace. |
| **Remove-PowerBIWorkspaceUser** | Grupos\_DeleteUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Remove um usuário da lista de membros de um determinado workspace. |
| **Restore-PowerBIWorkspace** | Grupos\_RestoreDeletedGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId}/restore | Restaura um workspace excluído. |
| **Set-PowerBIWorkspace** | Grupos\_UpdateGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId} | Atualiza as propriedades de um determinado workspace. |
| **Get-PowerBIDataset -WorkspaceId** | Grupos\_GetDatasetsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/datasets | Obtém os conjuntos de dados dentro de um determinado workspace. |
| **Export-PowerBIReport** | Relatórios\_ExportReportAsAdmin | Não aplicável | Exporta um determinado relatório a um arquivo local. |
| **Get-PowerBIReport** | Relatórios\_GetReportsAsAdmin | /v1.0/myorg/admin/reports | Obtém a lista completa de relatórios em um locatário do Power BI. |
| **Get-PowerBIDashboard** | Dashboards\_GetDashboardsAsAdmin | /v1.0/myorg/admin/dashboards | Obtém a lista completa de dashboards em um locatário do Power BI. |
| **Get-PowerBIDashboard -WorkspaceId** | Grupos\_GetDashboardsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Obtém os dashboards dentro de um determinado workspace. |
| **Get-PowerBITile -DashboardId** | Dashboards\_GetTilesAsAdmin | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Obtém os blocos de um determinado dashboard. |
| **Get-PowerBIReport -WorkspaceId** | Grupos\_GetReportsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/reports | Obtém os relatórios dentro de um determinado workspace. |
| **Get-PowerBIImport** | Importações\_GetImportsAsAdmin | /v1.0/myorg/admin/imports | Obtém a lista completa de importações em um locatário do Power BI. |
| **Connect-PowerBIServiceAccount** | Não aplicável | Não aplicável | Faça logon no Power BI e inicie uma sessão. |
| **Disconnect-PowerBIServiceAccount** | Não aplicável | Não aplicável | Faça logoff do Power BI e feche a sessão existente. |
| **Invoke-PowerBIRestMethod** | Não aplicável | Não aplicável | Envie chamadas arbitrárias da API REST ao Power BI. |
| **Get-PowerBIAccessToken** | Não aplicável | Não aplicável | Obtenha o token de acesso do Power BI em uma sessão. |
| **Resolve-PowerBIError** | Não aplicável | Não aplicável | Obtenha informações detalhadas do erro para chamadas de cmdlet sem êxito. |