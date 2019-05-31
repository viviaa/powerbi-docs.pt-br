---
title: Use a auditoria dentro da sua organização
description: Saiba como você pode usar a auditoria com o Power BI para monitorar e investigar as ações executadas. Você pode usar a Central de Segurança e Conformidade ou usar o PowerShell.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/23/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Administration
ms.openlocfilehash: 559ff45974274420e2545228720000359d5fe971
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64906881"
---
# <a name="use-auditing-within-your-organization"></a>Use a auditoria dentro da sua organização

Saber quem está executando uma ação em qual item em seu Power BI locatário pode ser essencial para ajudar sua organização a atender seus requisitos, como gerenciamento de registros e conformidade regulamentar. Use o Power BI a auditoria para auditar as ações realizadas pelos usuários, como "Exibir relatório" e "Modo de exibição de painel". Você não pode usar a auditoria para auditar as permissões.

Trabalhe com a auditoria no Centro de Conformidade e Segurança do Office 365 ou use o PowerShell. A auditoria conta com a funcionalidade no Exchange Online, que é provisionado automaticamente para dar suporte ao Power BI.

Você pode filtrar os dados de auditoria por intervalo de datas, usuário, dashboard, relatório, conjunto de dados e tipo de atividade. Você também pode baixar as atividades em um arquivo csv (valores separados por vírgula) para analisar offline.

## <a name="requirements"></a>Requisitos

Você deve atender a esses requisitos para acessar logs de auditoria:

* Você deve ser um administrador global ou atribuída à função de Logs de auditoria ou Logs de auditoria somente para exibição no Exchange Online para acessar o log de auditoria. Por padrão, os grupos de função de gerenciamento de conformidade e gerenciamento de organização vêm com essas funções atribuídas a **permissões** página no Centro de administração do Exchange.

    Para fornecer contas não-administrador com acesso ao log de auditoria, você deve adicionar o usuário como um membro de um desses grupos de função. Se você quiser fazê-lo outra forma, crie um grupo de função personalizada no Centro de administração do Exchange, atribua a função de Logs de auditoria ou os Logs de auditoria somente para exibição a esse grupo e, em seguida, adicione a conta não administrativa para o novo grupo de funções. Para obter mais informações, veja [Gerenciar grupos de função no Exchange Online](/Exchange/permissions-exo/role-groups).

    Se você não conseguir acessar o Centro de administração do Exchange no Centro de administração do Microsoft 365, vá para https://outlook.office365.com/ecp e entre usando suas credenciais.

* Se você tem acesso ao log de auditoria, mas não um administrador global ou administrador de serviço do Power BI, você não terá acesso ao portal de administração do Power BI. Nesse caso, você deve usar um link direto para o [Centro de Conformidade e Segurança do Office 365](https://sip.protection.office.com/#/unifiedauditlog).

## <a name="access-your-audit-logs"></a>Acessar seus logs de auditoria

Para acessar os logs, primeiro certifique-se de habilitar o log no Power BI. Para saber mais, confira [Logs de auditoria](service-admin-portal.md#audit-logs) na documentação do portal do administrador. Pode haver um atraso de 48 horas de até entre a hora em que você habilitar a auditoria e quando você pode exibir dados de auditoria. Se os dados não forem exibidos imediatamente, verifique os logs de auditoria mais tarde. Pode haver um atraso semelhante entre a obtenção da permissão para exibir os logs de auditoria e a possibilidade de acessá-los.

Os logs de auditoria do Power BI estão disponíveis diretamente no [Centro de Conformidade e Segurança do Office 365](https://sip.protection.office.com/#/unifiedauditlog). Também há um link no portal de administração do Power BI:

1. No Power BI, selecione a **ícone de engrenagem** no canto superior direito, em seguida, selecione **portal de administração**.

   ![Captura de tela do menu suspenso engrenagem com a opção do portal de administração de chamadas.](media/service-admin-auditing/powerbi-admin.png)

1. Selecione **Logs de Auditoria**.

1. Selecione **Ir para o Centro de Administração do O365**.

   ![Captura de tela do portal de administração com a auditoria registra opção e em qualquer lugar às opções do Centro de administração do O365 Microsoft destacadas.](media/service-admin-auditing/audit-log-o365-admin-center.png)

## <a name="search-only-power-bi-activities"></a>Pesquisar somente as atividades do Power BI

Restrinja os resultados apenas para as atividades do Power BI fazendo o seguinte. Confira uma lista de atividades em [lista de atividades auditadas pelo Power BI](#activities-audited-by-power-bi) mais adiante neste artigo.

1. Sobre o **pesquisa de logs de auditoria** página, em **pesquisa**, selecione na lista suspensa para **atividades**.

2. Selecione **Atividades do Power BI**.

   ![Pesquisa de log de captura de tela de auditoria com atividades do Power BI destacados.](media/service-admin-auditing/audit-log-search-filter-by-powerbi.png)

3. Selecione qualquer lugar fora da caixa de seleção para fechá-la.

As pesquisas retornará apenas as atividades do Power BI.

## <a name="search-the-audit-logs-by-date"></a>Pesquisar os logs de auditoria por data

Você pode pesquisar os logs por intervalo de datas usando os campos **Data de início** e **Data de término**. A seleção padrão é últimos sete dias. A exibição apresenta a data e hora no formato Tempo Universal Coordenado (UTC). O intervalo de datas máximo que você pode especificar é 90 dias. 

Você receberá um erro se o intervalo de datas selecionado for maior que 90 dias. Se você estiver usando o intervalo de datas máximo de 90 dias, selecione a hora atual para a **Data de início**. Caso contrário, você receberá uma mensagem de erro informando que a data de início é anterior à data de término. Se você ativou a auditoria nos últimos 90 dias, o intervalo de datas não poderá começar antes da data na qual a auditoria foi ativada.

![Pesquisa de log de captura de tela de auditoria com data de início e data de término opções indicadas.](media/service-admin-auditing/search-audit-log-by-date.png)

## <a name="search-the-audit-logs-by-users"></a>Pesquisar os logs de auditoria por usuários

Você pode procurar por entradas de log de auditoria para atividades realizadas pelos usuários específicos. Insira um ou mais nomes de usuário na **usuários** campo. O nome de usuário se parece com um endereço de email. É a conta que os usuários fazem logon no Power BI com. Deixe esta caixa em branco para retornar as entradas para todos os usuários (e contas de serviço) em sua organização.

![Pesquisar por usuários](media/service-admin-auditing/search-audit-log-by-user.png)

## <a name="view-search-results"></a>Exibir resultados da pesquisa

Depois de selecionar **pesquisa**, carregar os resultados da pesquisa. Após alguns instantes, elas serão exibidas em **resultados**. Quando a pesquisa for concluída, a exibição mostra o número de resultados encontrados. **Pesquisa de logs de auditoria** exibirá um máximo de 1000 eventos. Se mais de 1000 eventos atendem aos critérios de pesquisa, o aplicativo exibe os 1000 eventos mais recentes.

### <a name="view-the-main-results"></a>Exibir os resultados principais

O **resultados** área tem as seguintes informações para cada evento retornado pela pesquisa. Selecione um cabeçalho de coluna em **Resultados** para classificar os resultados.

| **Coluna** | **Definição** |
| --- | --- |
| Date |A data e a hora (no formato UTC) quando o evento ocorreu. |
| Endereço IP |O endereço IP do dispositivo usado para a atividade registrada. O aplicativo exibe o endereço IP no formato de endereço IPv4 ou IPv6. |
| Usuário |O usuário (ou a conta de serviço) que executou a ação que acionou o evento. |
| Atividade |A atividade executada pelo usuário. Esse valor corresponde às atividades que você selecionou na lista suspensa **Atividades**. Para um evento do log de auditoria de administrador do Exchange, o valor desta coluna é um cmdlet do Exchange. |
| Item |O objeto criado ou modificado devido à atividade correspondente. Por exemplo, o arquivo exibido ou modificado, ou a conta de usuário atualizada. Nem todas as atividades têm um valor nesta coluna. |
| Detalhe |Detalhes adicionais sobre uma atividade. Novamente, nem todas as atividades tem um valor. |

### <a name="view-the-details-for-an-event"></a>Exibir os detalhes de um evento

Para exibir mais detalhes sobre um evento, selecione o registro de evento na lista de resultados da pesquisa. Um **detalhes** página será exibida com as propriedades detalhadas do registro de evento. O **detalhes** página exibe as propriedades de acordo com o serviço do Office 365 na qual o evento ocorre.

Para exibir esses detalhes, selecione **Mais informações**. Todas as entradas do Power BI têm um valor de 20 para a propriedade RecordType. Para saber mais sobre outras propriedades, confira [Propriedades detalhadas no log de auditoria](/office365/securitycompliance/detailed-properties-in-the-office-365-audit-log/).

   ![Captura de tela da caixa de diálogo de detalhes de auditoria com a opção de informações mais destacado.](media/service-admin-auditing/audit-details.png)

## <a name="export-search-results"></a>Exportar resultados da pesquisa

Para exportar o log de auditoria do Power BI para um arquivo CSV, siga estas etapas.

1. Selecione **Exportar resultados**.

1. Selecione **Salvar resultados carregados** ou **Baixar todos os resultados**.

    ![Opção de resultados de captura de tela da exportação.](media/service-admin-auditing/export-auditing-results.png)

## <a name="use-powershell-to-search-audit-logs"></a>Usar o PowerShell para pesquisar logs de auditoria

Você também pode usar o PowerShell para acessar os logs de auditoria com base em seu logon. O exemplo a seguir mostra como conectar-se ao Exchange Online PowerShell e então usar o comando [Search-UnifiedAuditLog](/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog?view=exchange-ps/) para efetuar o pull de entradas de log de auditoria do Power BI. Para executar o script, um administrador deve atribuir a você as permissões apropriadas, conforme descrito na [requisitos](#requirements) seção.

```powershell
Set-ExecutionPolicy RemoteSigned

$UserCredential = Get-Credential

$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection

Import-PSSession $Session
Search-UnifiedAuditLog -StartDate 9/11/2018 -EndDate 9/15/2018 -RecordType PowerBI -ResultSize 1000 | Format-Table | More
```

Para obter mais informações sobre como se conectar ao Exchange Online, consulte [Conectar ao Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell/). Para ver outro exemplo de como usar o PowerShell com os logs de auditoria, confira [Usar o log de auditoria do Power BI e o PowerShell para atribuir licenças do Power BI Pro](https://powerbi.microsoft.com/blog/using-power-bi-audit-log-and-powershell-to-assign-power-bi-pro-licenses/).

## <a name="activities-audited-by-power-bi"></a>Atividades auditadas pelo Power BI

As seguintes atividades são auditadas pelo Power BI:

| Nome amigável                                     | Nome da operação                              | Observações                                  |
|---------------------------------------------------|---------------------------------------------|------------------------------------------|
| Fonte de dados adicionada ao gateway do Power BI             | AddDatasourceToGateway                      |                                          |
| Acesso à pasta do Power BI adicionado                      | AddFolderAccess                             | Atualmente não usado                       |
| Adicionados membros de grupo do Power BI                      | AddGroupMembers                             |                                          |
| Administrador anexou conta de armazenamento de fluxo de dados ao locatário | AdminAttachedDataflowStorageAccountToTenant | Atualmente não usado                       |
| Conjunto de dados do Power BI analisado                         | AnalyzedByExternalApplication               |                                          |
| Relatório do Power BI analisado                          | AnalyzeInExcel                              |                                          |
| Conjunto de dados do Power BI associado ao gateway                | BindToGateway                               |                                          |
| Estado da capacidade alterado                            | ChangeCapacityState                         |                                          |
| Atribuição de usuário da capacidade alterado                  | UpdateCapacityUsersAssignment               |                                          |
| Conexões de conjunto de dados do Power BI alteradas              | SetAllConnections                           |                                          |
| Administradores de gateway do Power BI alterados                   | ChangeGatewayAdministrators                 |                                          |
| Usuários da fonte de dados de gateway do Power BI alterados        | ChangeGatewayDatasourceUsers                |                                          |
| Pacote de conteúdo organizacional do Power BI criado      | CreateOrgApp                                |                                          |
| Aplicativo do Power BI criado                              | CreateApp                                   |                                          |
| Dashboard do Power BI criado                        | CreateDashboard                             |                                          |
| Fluxo de dados do Power BI criado                         | CreateDataflow                              |                                          |
| Conjunto de dados do Power BI criado                          | CreateDataset                               |                                          |
| Assinatura de email do Power BI criada               | CreateEmailSubscription                     |                                          |
| Pasta do Power BI criada                           | CreateFolder                                |                                          |
| Gateway do Power BI criado                          | CreateGateway                               |                                          |
| Grupo do Power BI criado                            | CreateGroup                                 |                                          |
| Relatório do Power BI criado                           | CreateReport                                |                                          |
| Fluxo de dados migrado para conta de armazenamento externa     | DataflowMigratedToExternalStorageAccount    | Atualmente não usado                       |
| Permissões de fluxo de dados adicionadas                        | DataflowPermissionsAdded                    | Atualmente não usado                       |
| Permissões de fluxo de dados removidas                      | DataflowPermissionsRemoved                  | Atualmente não usado                       |
| Pacote de conteúdo organizacional do Power BI excluído      | DeleteOrgApp                                |                                          |
| Comentário do Power BI excluído                          | DeleteComment                               |                                          |
| Dashboard do Power BI excluído                        | DeleteDashboard                             | Atualmente não usado                       |
| Fluxo de dados do Power BI excluído                         | DeleteDataflow                              | Atualmente não usado                       |
| Conjunto de dados do Power BI excluído                          | DeleteDataset                               |                                          |
| Assinatura de email do Power BI excluída               | DeleteEmailSubscription                     |                                          |
| Pasta do Power BI excluída                           | DeleteFolder                                |                                          |
| Acesso à pasta do Power BI excluído                    | DeleteFolderAccess                          | Atualmente não usado                       |
| Gateway do Power BI excluído                          | DeleteGateway                               |                                          |
| Grupo do Power BI excluído                            | DeleteGroup                                 |                                          |
| Relatório do Power BI excluído                           | DeleteReport                                |                                          |
| Fontes de dados de conjunto de dados do Power BI descobertas          | GetDatasources                              |                                          |
| Relatório do Power BI baixado                        | DownloadReport                              |                                          |
| Permissão de certificação do Power BI editada          | EditCertificationPermission                 | Atualmente não usado                       |
| Dashboard do Power BI editado                         | EditDashboard                               | Atualmente não usado                       |
| Conjunto de dados do Power BI editado                           | EditDataset                                 |                                          |
| Propriedades do conjunto de dados do Power BI editadas                | EditDatasetProperties                       | Atualmente não usado                       |
| Relatório do Power BI editado                            | EditReport                                  |                                          |
| Fluxo de dados do Power BI exportado                        | ExportDataflow                              |                                          |
| Dados visuais de relatório do Power BI exportados              | ExportReport                                |                                          |
| Dados de bloco do Power BI exportados                       | ExportTile                                  |                                          |
| Falha ao adicionar permissões de fluxo de dados                | FailedToAddDataflowPermissions              | Atualmente não usado                       |
| Falha ao remover permissões de fluxo de dados             | FailedToRemoveDataflowPermissions           | Atualmente não usado                       |
| Token SAS de fluxo de dados do Power BI gerado             | GenerateDataflowSasToken                    |                                          |
| Token de inserção do Power BI gerado                    | GenerateEmbedToken                          |                                          |
| Arquivo importado para o Power BI                         | Importar                                      |                                          |
| Aplicativo do Power BI instalado                            | InstallApp                                  |                                          |
| Workspace migrado para uma capacidade                  | MigrateWorkspaceIntoCapacity                |                                          |
| Comentário do Power BI postado                           | PostComment                                 |                                          |
| Dashboard do Power BI impresso                        | PrintDashboard                              |                                          |
| Página de relatório do Power BI impressa                      | PrintReport                                 |                                          |
| Relatório do Power BI publicado na Web                  | PublishToWebReport                          |                                          |
| Segredo de fluxo de dados do Power BI recebido do Key Vault  | ReceiveDataflowSecretFromKeyVault           | Atualmente não usado                       |
| Fonte de dados removida do gateway do Power BI         | RemoveDatasourceFromGateway                 |                                          |
| Membros de grupo do Power BI removidos                    | DeleteGroupMembers                          |                                          |
| Workspace removido de uma capacidade                 | RemoveWorkspacesFromCapacity                |                                          |
| Dashboard do Power BI renomeado                        | RenameDashboard                             |                                          |
| Atualização de fluxo de dados do Power BI solicitada               | RequestDataflowRefresh                      | Atualmente não usado                       |
| Atualização de conjunto de dados do Power BI solicitada                | RefreshDataset                              |                                          |
| Workspaces do Power BI recuperados                     | GetWorkspaces                               |                                          |
| Definir atualização agendada no fluxo de dados do Power BI        | SetScheduledRefreshOnDataflow               |                                          |
| Definir atualização agendada no conjunto de dados do Power BI         | SetScheduledRefresh                         |                                          |
| Dashboard do Power BI compartilhado                         | ShareDashboard                              |                                          |
| Relatório do Power BI compartilhado                            | ShareReport                                 |                                          |
| Avaliação estendida do Power BI iniciada                   | OptInForExtendedProTrial                    | Atualmente não usado                       |
| Avaliação do Power BI iniciada                            | OptInForProTrial                            |                                          |
| Assumiu uma fonte de dados do Power BI                   | TakeOverDatasource                          |                                          |
| Assumiu um conjunto de dados do Power BI                        | TakeOverDataset                             |                                          |
| Aplicativo do Power BI não publicado                          | UnpublishApp                                |                                          |
| Atualizar configurações de governança de recursos de capacidade      | UpdateCapacityResourceGovernanceSettings    | Atualmente não está no Centro de administração do Microsoft 365 |
| Administrador de capacidade atualizado                            | UpdateCapacityAdmins                        |                                          |
| Nome de exibição de capacidade atualizado                     | UpdateCapacityDisplayName                   |                                          |
| Configurações do Power BI da organização atualizadas          | UpdatedAdminFeatureSwitch                   |                                          |
| Aplicativo do Power BI atualizado                              | UpdateApp                                   |                                          |
| Fluxo de dados do Power BI atualizado                         | UpdateDataflow                              |                                          |
| Fontes de dados de conjunto de dados do Power BI atualizadas             | UpdateDatasources                           |                                          |
| Parâmetros de conjunto de dados do Power BI atualizados               | UpdateDatasetParameters                     |                                          |
| Assinatura de email do Power BI atualizada               | UpdateEmailSubscription                     |                                          |
| Pasta do Power BI atualizada                           | UpdateFolder                                |                                          |
| Acesso à pasta do Power BI atualizado                    | UpdateFolderAccess                          |                                          |
| Credenciais da fonte de dados de gateway do Power BI atualizadas  | UpdateDatasourceCredentials                 |                                          |
| Dashboard do Power BI exibido                         | ViewDashboard                               |                                          |
| Fluxo de dados do Power BI exibido                          | ViewDataflow                                |                                          |
| Relatório do Power BI exibido                            | ViewReport                                  |                                          |
| Bloco do Power BI exibido                              | ViewTile                                    |                                          |
| Métricas de uso do Power BI exibidas                     | ViewUsageMetrics                            |                                          |
|                                                   |                                             |                                          |

## <a name="next-steps"></a>Próximas etapas

[O que é administração do Power BI?](service-admin-administering-power-bi-in-your-organization.md)  

[Portal de administração do Power BI](service-admin-portal.md)  

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
