---
title: Cmdlets do PowerShell, APIs REST e SDK do .NET para a administração do Power BI
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
ms.openlocfilehash: ffb2ae077add5756af63f07d8f3da830e075e0b4
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36945218"
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
| **Get-PowerBIWorkspace** | Grupos\_GetGroupsAsAdmin | /v1.0/myorg/admin/groups | Obtém a lista completa de espaços de trabalho em um locatário do Power BI. |
| **Add-PowerBIWorkspaceUser** | Grupos\_AddUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users | Adiciona um usuário como um membro a um determinado espaço de trabalho. |
| **Remove-PowerBIWorkspaceUser** | Grupos\_DeleteUserAsAdmin | /v1.0/myorg/admin/groups/{groupId}/users/{user} | Remove um usuário da lista de membros de um determinado espaço de trabalho. |
| **Restore-PowerBIWorkspace** | Grupos\_RestoreDeletedGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId}/restore | Restaura um espaço de trabalho excluído. |
| **Set-PowerBIWorkspace** | Grupos\_UpdateGroupAsAdmin | /v1.0/myorg/admin/groups/{groupId} | Atualiza as propriedades de um determinado espaço de trabalho. |
| **Get-PowerBIDataset -WorkspaceId** | Grupos\_GetDatasetsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/datasets | Obtém os conjuntos de dados dentro de um determinado espaço de trabalho. |
| **Export-PowerBIReport** | Relatórios\_ExportReportAsAdmin | N/A | Exporta um determinado relatório a um arquivo local. |
| **Get-PowerBIReport** | Relatórios\_GetReportsAsAdmin | /v1.0/myorg/admin/reports | Obtém a lista completa de relatórios em um locatário do Power BI. |
| **Get-PowerBIDashboard** | Dashboards\_GetDashboardsAsAdmin | /v1.0/myorg/admin/dashboards | Obtém a lista completa de dashboards em um locatário do Power BI. |
| **Get-PowerBIDashboard -WorkspaceId** | Grupos\_GetDashboardsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/dashboards | Obtém os dashboards dentro de um determinado espaço de trabalho. |
| **Get-PowerBITile -DashboardId** | Dashboards\_GetTilesAsAdmin | /v1.0/myorg/admin/dashboards/{dashboard\_id}/tiles | Obtém os blocos de um determinado dashboard. |
| **Get-PowerBIReport -WorkspaceId** | Grupos\_GetReportsAsAdmin | /v1.0/myorg/admin/groups/{group\_id}/reports | Obtém os relatórios dentro de um determinado espaço de trabalho. |
| **Get-PowerBIImport** | Importações\_GetImportsAsAdmin | /v1.0/myorg/admin/imports | Obtém a lista completa de importações em um locatário do Power BI. |
| **Connect-PowerBIServiceAccount** | N/A | N/A | Faça logon no Power BI e inicie uma sessão. |
| **Disconnect-PowerBIServiceAccount** | N/A | N/A | Faça logoff do Power BI e feche a sessão existente. |
| **Invoke-PowerBIRestMethod** | N/A | N/A | Envie chamadas arbitrárias da API REST ao Power BI. |
| **Get-PowerBIAccessToken** | N/A | N/A | Obtenha o token de acesso do Power BI em uma sessão. |
| **Resolve-PowerBIError** | N/A | N/A | Obtenha informações detalhadas do erro para chamadas de cmdlet sem êxito. |