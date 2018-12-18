---
title: Gerenciar o armazenamento de dados em espaços de trabalho
description: Saiba como você pode gerenciar seu armazenamento de dados em seu espaço de trabalho individual ou do aplicativo para garantir que possa continuar publicando relatórios e conjuntos de dados.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: maggies
LocalizationGroup: Administration
ms.openlocfilehash: 239cc7e0574c9c6a4d76cdff83e14cf6af742689
ms.sourcegitcommit: f25464d5cae46691130eb7b02c33f42404011357
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53180451"
---
# <a name="manage-data-storage-in-power-bi-workspaces"></a>Gerenciar o armazenamento de dados em workspaces do Power BI

Saiba como você pode gerenciar seu armazenamento de dados em seu espaço de trabalho individual ou do aplicativo para garantir que possa continuar publicando relatórios e conjuntos de dados.

Os usuários e os espaços de trabalho do aplicativo têm suas próprias capacidades de dados:

* Todos os usuários têm um armazenamento de dados máximo de 10 GB.
* Os usuários com uma licença do Power BI Pro podem criar workspaces do aplicativo, com um armazenamento de dados máximo de 10 GB cada um.

No nível do locatário, o uso total não pode exceder 10 GB por usuário Pro em todos os usuários Pro e workspaces do aplicativo no locatário.

Leia sobre outros recursos do [modelo de preços do Power BI](https://powerbi.microsoft.com/pricing).

No armazenamento de dados estão incluídos seus próprios conjuntos de dados e relatórios do Excel e aqueles que alguém compartilhou com você. Os conjuntos de dados são qualquer uma das fontes de dados que você carregou ou com as quais está conectado, inclusive os arquivos do Power BI Desktop e as pastas de trabalho do Excel que você está usando. O exemplo a seguir também está incluído em sua capacidade de dados.

* Intervalos do Excel fixados no painel.
* Visualizações locais do Reporting Services fixadas em um painel do Power BI.
* Imagens carregadas.

O tamanho de um dashboard que você compartilhar varia dependendo do que é fixado a ele. Por exemplo, se você fixar itens de dois relatórios que fazem parte de dois conjuntos de dados diferentes, o tamanho incluirá os dois conjuntos de dados.

<a name="manage"/>

## <a name="manage-items-owned-by-you"></a>Gerenciar itens pertencentes a você
Veja a quantidade de armazenamento de dados que você está usando em sua conta do Power BI e gerencie sua conta.

1. Para gerenciar seu próprio armazenamento, acesse **Meu Workspace** no painel de navegação à esquerda.
   
    ![Meu Workspace](media/service-admin-manage-your-data-storage-in-power-bi/pbi_myworkspace.png)
2. Selecione o ícone de engrenagem ![Ícone de Engrenagem](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) no canto superior direito \> **Gerenciar armazenamento pessoal**.
   
    A barra superior mostra o limite de armazenamento que você usou.
   
    ![Gerenciar limite de armazenamento](media/service-admin-manage-your-data-storage-in-power-bi/pbi_persnlstorage.png)
   
    Os conjuntos de dados e os relatórios são separados em duas guias:
   
    **Pertencente a mim:** São relatórios e conjuntos de dados que você carregou na sua conta do Power BI, inclusive conjuntos de dados de serviço, como Salesforce e Dynamics CRM.  
    **Pertencente a outros:** Outras pessoas compartilharam esses relatórios e conjuntos de dados com você.
3. Para excluir um conjunto de dados ou um relatório, selecione o ícone de lixeira ![ícone de lixeira](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).

Tenha em mente que você ou outra pessoa pode ter relatórios e painéis com base em um conjunto de dados. Se você excluir o conjunto de dados, os relatórios e painéis de controle não funcionarão mais.

## <a name="manage-your-app-workspace"></a>Gerenciar o workspace do aplicativo
1. Selecione a seta ao lado de **Workspaces**\> selecione o nome do workspace do aplicativo.
   
    ![Selecionar um espaço de trabalho de aplicativo](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupworkspaces.png)
2. Selecione o ícone de engrenagem ![ícone de engrenagem](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png) no canto superior direito \> **Gerenciar armazenamento de grupo**.
   
    A barra superior mostra o limite de armazenamento de grupo que você usou.
   
    ![Gerenciar armazenamento de um espaço de trabalho de aplicativo](media/service-admin-manage-your-data-storage-in-power-bi/pbi_groupstorage.png)
   
    Os conjuntos de dados e os relatórios são separados em duas guias:
   
    **Pertencente a nós:** São relatórios e conjuntos de dados que você ou outra pessoa carregou na conta do Power BI do grupo, inclusive conjuntos de dados de serviço, como Salesforce e Dynamics CRM.
    **Pertencente a outros:** Outras pessoas compartilharam esses relatórios e conjuntos de dados com seu grupo.
3. Para excluir um conjunto de dados ou um relatório, selecione o ícone de lixeira ![ícone de lixeira](media/service-admin-manage-your-data-storage-in-power-bi/pbi_deleteicon.png).
   
   > [!NOTE]
   > Qualquer membro, com permissões de edição, de um workspace do aplicativo tem permissões para excluir conjuntos de dados e relatórios do workspace do aplicativo.
   > 
   > 

Tenha em mente que você ou outra pessoa do grupo pode ter relatórios e painéis com base em um conjunto de dados. Se você excluir o conjunto de dados, os relatórios e painéis de controle não funcionarão mais.

## <a name="dataset-limits"></a>Limites de conjunto de dados
Há um limite de 1 GB por conjunto de dados que é importado para o Power BI. Se você optou por manter a experiência do Excel, em vez de importar os dados, você será limitado até 250 MB para o conjunto de dados.

## <a name="what-happens-when-you-hit-a-limit"></a>O que acontece quando você atinge um limite
Quando você atinge o limite da capacidade de dados do que você pode fazer, você verá avisos dentro do serviço. 

Ao selecionar o ícone de engrenagem ![ícone de engrenagem](media/service-admin-manage-your-data-storage-in-power-bi/pbi_gearicon.png), você verá uma barra vermelha indicando que você está acima do limite da capacidade de dados.

! [Limite de armazenamento atingido]] (media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit.png)

Você também verá isso indicado em **Gerenciar armazenamento pessoal**.

 ![Gerenciar armazenamento pessoal, limite de armazenamento atingido](media/service-admin-manage-your-data-storage-in-power-bi/manage-storage-limit2.png)

 Quando você tenta executar uma ação que atingirá um dos limites, você verá um aviso indicando que você está acima do limite. Você poderá [gerenciar](#manage) seu armazenamento para reduzir a quantidade de armazenamento e ultrapassar o limite.

 ![Acima do seu limite de armazenamento](media/service-admin-manage-your-data-storage-in-power-bi/powerbi-pro-over-limit.png)

 Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

