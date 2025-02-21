---
title: Organizar o trabalho em novos espaços de trabalho no Power BI
description: Saiba mais sobre novos espaços de trabalho, coleções de painéis e relatórios criados para oferecer métricas-chave para sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a3982716ac2eb64f7512ba6ef606af299f1c5f46
ms.sourcegitcommit: 8dee40f07d284ec84a8afa0100359f146e1dd88b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2019
ms.locfileid: "67418668"
---
# <a name="organize-work-in-the-new-workspaces-in-power-bi"></a>Organizar o trabalho em novos espaços de trabalho no Power BI

 *Espaços de trabalho* são locais para colaborar com colegas e criar coleções de painéis e relatórios (paginados ou não). A nova experiência com o espaço de trabalho ajuda você a gerenciar melhor o acesso ao conteúdo. Este artigo descreve os novos espaços de trabalho e como eles diferem dos clássicos.  Como ocorre com espaços de trabalho clássicos, você ainda os usa para criar e distribuir aplicativos. Leia sobre como [criar uma nova experiência de espaço de trabalho](service-create-the-new-workspaces.md).

A nova experiência de espaço de trabalho atingiu a disponibilidade geral (GA) e agora é o espaço de trabalho padrão. Você ainda poderá continuar a criar e usar [espaços de trabalho clássicos](service-create-workspaces.md) com base em Grupos do Office 365. 

> [!NOTE]
> Para impor a Segurança em Nível de Linha (RLS) para usuários que procuram conteúdo em um espaço de trabalho, use a função Visualizador. Se a função Visualizador ainda não estiver disponível em seu locatário, continue a usar [espaços de trabalho clássicos](service-create-workspaces.md) e selecione a opção **Membros só podem ver o conteúdo do Power BI**. Como alternativa, publique um aplicativo do Power BI para esses usuários ou use o compartilhamento para distribuir o conteúdo.

Com os novos espaços de trabalho, é possível:

- Atribuir funções de workspace a grupos de usuários: grupos de segurança, listas de distribuição, grupos do Office 365 e indivíduos.
- Criar um workspace no Power BI sem criar um grupo do Office 365.
- Usar funções de workspaces mais granulares para obter um gerenciamento de permissões mais flexível em um workspace.
- O administrador do Power BI pode controlar quem pode criar espaços de trabalho no Power BI.

Quando você cria um dos novos workspaces, você não está criando um grupo do Office 365 associado e subjacente. Toda a administração do workspace está no Power BI, não no Office 365. Com a nova experiência de espaço de trabalho, agora você pode adicionar um grupo do Office 365 à lista de acesso do espaço de trabalho para continuar gerenciando o acesso do usuário ao conteúdo por meio de grupos do Office 365.

## <a name="administering-new-workspace-experience-workspaces"></a>Administrar as novas experiências de espaços de trabalho
A administração das novas experiências de espaços de trabalho está disponível agora no Power BI, ou seja, os administradores do Power BI decidem quem pode criar espaços de trabalho em uma organização. Eles também podem gerenciar e recuperar espaços de trabalho. Para fazer isso, eles precisam usar o portal de administração do Power BI ou os CmdLets do PowerShell. Para espaços de trabalho clássicos com base em grupos do Office 365, a administração continuará a ser feita no portal de administração do Office 365 e no Azure Active Directory.

Em **Configurações de espaços de trabalho**, no portal de administração, os administradores podem usar a configuração Criar espaços de trabalho (nova experiência de espaços de trabalho) para permitir que todas as pessoas ou ninguém em uma organização crie uma nova experiência de espaços de trabalho. Eles também podem limitar a criação de membros de grupos de segurança específicos.

> [!NOTE]
> Por padrão, a configuração Criar espaços de trabalho (nova experiência de espaços de trabalho) permite que somente usuários autorizados a criar grupos do Office 365 possam criar novos espaços de trabalho no Power BI. Certifique-se de definir um valor no portal de administração do Power BI para garantir que os usuários adequados possam criar novas experiências de espaços de trabalho.

![Configurações de workspace no portal de administração](media/service-new-workspaces/power-bi-workspace-admin-settings.png)

A [lista de espaços de trabalho está disponível](service-admin-portal.md#workspaces) no portal de administração do Power BI. 

![Lista de workspaces](media/service-admin-portal/workspaces-list.png)

## <a name="new-workspaces-side-by-side-with-classic-workspaces"></a>Novos espaços de trabalho lado a lado com espaços de trabalho clássicos

Os espaços de trabalho novos, atualizados e espaços de trabalho clássicos coexistem lado a lado e você pode criar ambos. A nova experiência de espaço de trabalho é o tipo de espaço de trabalho padrão. O Power BI continua a listar todos os grupos do Office 365 do qual o usuário é membro no Power BI para evitar a alteração de fluxos de trabalho existentes. Para saber como criar um novo espaço de trabalho, confira [Criar novos espaços de trabalho](service-create-the-new-workspaces.md). Para saber como criar um espaço de trabalho clássico, confira [Criar espaços de trabalho clássicos](service-create-workspaces.md).

## <a name="roles-in-the-new-workspaces"></a>Funções nos novos workspaces

Para conceder acesso a um novo espaço de trabalho, adicione grupos de usuários ou indivíduos a uma das funções do espaço de trabalho: visualizadores, membros, colaboradores ou administradores. Todos em um grupo de usuários obtêm a função que você definiu. Se um indivíduo estiver em vários grupos de usuários, ele terá o nível mais alto de permissão fornecido pela função que lhe foi atribuída.

As funções permitem que você gerencie quem pode fazer o que em um workspace para que as equipes possam colaborar. Os novos workspaces permitem que você atribua funções a indivíduos e a grupos de usuários: grupos de segurança, grupos do Office 365 e listas de distribuição. 

Ao atribuir funções a um grupo de usuários, os indivíduos no grupo têm acesso ao conteúdo. Se você aninhar grupos de usuários, todos os usuários contidos terão permissão. Um usuário que está em vários grupos de usuários com diferentes funções obtém o nível mais alto de permissão concedido a eles. 

Os novos espaços de trabalho oferecem quatro funções: administradores, membros, colaboradores e visualizadores.

|Funcionalidade   | Administrador  | Membro  | Colaborador  | Visualizador |
|---|---|---|---|---|
| Atualizar e excluir o workspace.  | X  |   |   |   | 
| Adicionar/remover pessoas, incluindo outros administradores.  | X  |   |   |   |
| Adicionar membros ou outras pessoas com permissões inferiores.  |  X | X  |   |   |
| Publicar e atualizar um aplicativo. |  X | X  |   |   |
| Compartilhar um item ou um aplicativo. |  X | X  |   |   |
| Permitir que outras pessoas compartilhem novamente os itens. |  X | X  |   |   |
| Criar, editar e excluir conteúdo no workspace.  |  X | X  | X  |   |
| Publicar relatórios no workspace, excluir conteúdo.  |  X | X  | X  |   |
| Exiba um item. |  X | X  | X  | X  |
 
 
## <a name="licensing"></a>Licenças
Todas as pessoas que você adiciona a um espaço de trabalho na capacidade compartilhada precisam de uma licença do Power BI Pro. No workspace, esses usuários podem colaborar nos dashboards e relatórios que você planeja publicar para um público-alvo maior ou até mesmo para toda a organização. 

Para distribuir conteúdo a outras pessoas da sua organização, atribua licenças do Power BI Pro a esses usuários ou coloque o workspace em uma capacidade do Power BI Premium.

Quando o espaço de trabalho está em uma capacidade do Power BI Premium, os usuários com a função de visualizador podem acessar o espaço de trabalho, mesmo se não tiverem uma licença do Power BI Pro. No entanto, se você atribuir a esses usuários uma função superior como Administrador, Membro ou Colaborador, eles não poderão acessar o espaço de trabalho. Ele serão solicitados a iniciar uma avaliação do Pro ao tentarem acessar o espaço de trabalho. Para aproveitar a capacidade de Visualizador para usuários sem licenças do Pro, verifique se os usuários com a função Visualizador não estão em outras funções do espaço de trabalho, individualmente ou por meio de um grupo de usuários. 

> [!NOTE]
> A publicação de relatórios em uma nova experiência de espaço de trabalho tem a imposição mais rigorosa das regras de licenciamento existentes. Os usuários que tentarem publicar do Power BI Desktop ou de outras ferramentas de cliente sem uma licença do Pro verão o erro "Somente usuários com licenças do Power BI Pro podem publicar neste espaço de trabalho."

## <a name="how-are-the-new-workspaces-different-from-current-workspaces"></a>Em que aspectos os novos workspaces são diferentes dos workspaces atuais?

Com os novos workspaces, estamos reformulando alguns recursos. Aqui estão as alterações que você pode esperar como permanentes. 

* Criar esses espaços de trabalho não criará grupos do Office 365, como os espaços de trabalho clássicos fazem. No entanto, agora você pode usar um grupo do Office 365 para dar aos usuários acesso ao espaço de trabalho, atribuindo a ele uma função. 
* Nos espaços de trabalho clássicos, é possível adicionar apenas indivíduos às listas de membros e administradores. Nos novos workspaces, é possível adicionar vários grupos de segurança do AD, listas de distribuição ou grupos do Office 365 a essas listas para facilitar o gerenciamento de usuários. 
- É possível criar um pacote de conteúdo organizacional de um espaço de trabalho clássico. Não é possível criar um dos novos workspaces.
- É possível consumir um pacote de conteúdo organizacional de um espaço de trabalho clássico. Não é possível consumir um dos novos workspaces.

## <a name="workspace-contact-list"></a>Lista de contatos do espaço de trabalho
O novo recurso **Lista de contatos** permite que você especifique quais usuários recebem a notificação sobre problemas que ocorrem no espaço de trabalho. Por padrão, qualquer usuário ou grupo especificado como um administrador do espaço de trabalho é notificado, mas você pode personalizar a lista. Os usuários ou grupos listados na lista de contatos serão mostrados na interface do usuário (IU) para ajudar os usuários a obter ajuda relacionada ao espaço de trabalho. 

Saiba mais sobre a [configuração da lista de contatos do espaço de trabalho](service-create-the-new-workspaces.md#workspace-contact-list).

## <a name="workspace-onedrive"></a>OneDrive do Workspace
O recurso OneDrive do Workspace permite que você configure um grupo do Office 365 cujo armazenamento de arquivos da Biblioteca de Documentos do SharePoint esteja disponível para usuários do espaço de trabalho. O grupo precisa ser criado fora do Power BI. 

O Power BI não sincroniza as permissões de usuários ou grupos que estão configurados para ter acesso ao espaço de trabalho com a associação ao grupo do Office 365. A prática recomendada é gerenciar o acesso ao espaço de trabalho por meio do mesmo grupo do Office 365 cujo armazenamento de arquivos você define nessa configuração. 

Confira como [definir e acessar o OneDrive do Workspace](service-create-the-new-workspaces.md#workspace-onedrive).  
   
## <a name="auditing"></a>Auditoria
As seguintes atividades são auditadas pelo Power BI para novas experiências de espaços de trabalho.

| Nome amigável |   Nome da operação |
|---|---|
| Pasta do Power BI criada | CreateFolder |
| Pasta do Power BI excluída | DeleteFolder |
| Pasta do Power BI atualizada | UpdateFolder |
| Acesso à pasta do Power BI atualizado| UpdateFolderAccess |

Leia mais sobre [Auditoria do Power BI](service-admin-auditing.md#activities-audited-by-power-bi).

## <a name="limitations-and-considerations"></a>Limitações e considerações

Limitações a serem consideradas:

- Os workspaces podem conter um máximo de mil conjuntos de dados ou mil relatórios por conjunto de dados. 
- Uma pessoa com uma licença do Power BI Pro pode ser membro de um máximo de 1.000 espaços de trabalho.
- O Power BI Publisher para Excel não é compatível.

## <a name="workspace-features-that-work-differently"></a>Recursos do workspace de aplicativo que funcionam de forma diferente

Alguns recursos funcionam de forma diferente dos workspaces atuais nos novos workspaces. Essas diferenças são intencionais, com base nos comentários recebidos dos clientes, e permitem uma abordagem mais flexível para colaboração com espaços de trabalho:

- Imposição de licenciamento: A publicação de relatórios em uma nova experiência de espaço de trabalho impõe regras de licenciamento existentes que exigem uma licença do Power BI Pro para usuários que colaboram em espaços de trabalho ou compartilham conteúdo com outros no serviço do Power BI. Os usuários sem uma licença do Pro veem o erro "Somente usuários com licenças do Power BI Pro podem publicar neste espaço de trabalho."
- Os membros podem ou não compartilhar novamente: substituídos pela função Colaborador
- Workspaces somente leitura: Em vez de conceder aos usuários o acesso somente leitura a um espaço de trabalho, atribua aos usuários uma função de Visualizador que permite acesso somente leitura semelhante ao conteúdo de um espaço de trabalho.
- Os usuários sem uma licença do Pro poderão acessar o espaço de trabalho se ele estiver em uma capacidade Power BI Premium, mesmo se os usuários tiverem somente a função de Visualizador.
- Para permitir que os usuários com a função de Visualizador exportem dados, verifique se eles têm a permissão Criar nos conjuntos de dados no espaço de trabalho. Leia mais sobre a [Permissão Criar em conjuntos de dados](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).
- Nenhum botão **Sair do workspace**.

## <a name="frequently-asked-questions"></a>Perguntas frequentes

**São links para conteúdos existentes afetados pela nova experiência de disponibilidade geral (GA) de espaços de trabalho**

Não. Os links para itens existentes em espaços de trabalho clássicos não são afetados pela nova experiência de espaço de trabalho. A disponibilidade geral (GA) da nova experiência de espaço de trabalho altera o espaço de trabalho padrão que você cria, mas não altera espaços de trabalho existentes. 

**Os espaços de trabalho existentes foram atualizados para a nova experiência de espaço de trabalho com GA?**

Não. A nova experiência de espaço de trabalho com GA altera apenas o tipo de espaço de trabalho padrão para a nova experiência de espaço de trabalho. Os espaços de trabalho clássicos existentes com base em grupos do Office 365 permanecem inalterados.

**Os espaços de trabalho ainda são criados automaticamente para grupos do Office 365?**

Sim. Como damos suporte a ambos os tipos de espaços de trabalho lado a lado, continuamos a listar todos os grupos do Office 365 aos quais o usuário tem acesso na lista de espaços de trabalho.

## <a name="next-steps"></a>Próximas etapas
* [Criar novos espaços de trabalho no Power BI](service-create-the-new-workspaces.md)
* [Criar espaços de trabalho clássicos](service-create-workspaces.md)
* [Instalar e usar aplicativos no Power BI](service-create-distribute-apps.md)
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
