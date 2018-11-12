---
title: Workspace Arquivado do Power BI
description: Workspace Arquivado do Power BI depois de gerenciar locatários do Office 365
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: 8636ec85cb56e87f28a93f9f1f89989ffcc097bb
ms.sourcegitcommit: d20f74d5300197a0930eeb7db586c6a90403aabc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2018
ms.locfileid: "50973133"
---
# <a name="power-bi-archived-workspace"></a>Workspace Arquivado do Power BI

Com o Power BI, qualquer pessoa pode inscrever-se e começar a usar o serviço em alguns minutos.  Posteriormente, o departamento de TI da sua organização pode optar por assumir o gerenciamento do Power BI para usuários em sua organização.  Se esse controle ocorrer, você se beneficia do gerenciamento central de usuários e permissões em sua organização. Você também poderá aproveitar a entrada simplificada usando o mesmo nome de usuário e senha utilizados para outros serviços em sua organização.

Qualquer conteúdo que tenha sido criado antes do início do gerenciamento do Power BI por seu departamento de TI será colocado em um Workspace Arquivado do Power BI, que pode ser acessado na barra de navegação à esquerda do [Power BI](https://app.powerbi.com). Você deve começar a criação de conteúdo novo Power BI em Meu Workspace, que é protegido e gerenciado pelo departamento de TI da sua organização.  O workspace arquivado continuará a existir, mas há restrições sobre as ações que podem ser executadas no conteúdo do Workspace Arquivado.  Para remover essas restrições, você precisará migrar o conteúdo do seu Workspace Arquivado para o Meu Workspace, gerenciado pelo departamento de TI.

## <a name="restrictions-in-your-archived-workspace"></a>Restrições em seu Workspace Arquivado

O Power BI não exclui o conteúdo do Workspace arquivado. Você pode continuar a obter dados, criar relatórios e painéis e atualizar conjuntos de dados. Usuários existentes com os quais você compartilhou conteúdo ainda poderão exibir o conteúdo em seu Workspace Arquivado. No entanto, há algumas restrições sobre o conteúdo em seu Workspace Arquivado:

* **OneDrive for Business**: para conjunto de dados em seu Workspace Arquivado, você não poderá obter dados ou atualizá-los pelo OneDrive for Business.  Se você tentar se conectar a essa fonte, você receberá um aviso.

* **Painéis de compartilhamento**: você não pode compartilhar painéis com outros usuários do Workspace Arquivado.  Todos os usuários que já têm acesso continuarão a exibir painéis compartilhados, acessando seu Workspace Arquivado.

* **Criando grupos**: você não pode criar grupos no Workspace Arquivado.

* **Access em aplicativos móveis do Power BI**: embora você ainda possa exibir o conteúdo na web no Workspace Arquivado, esse conteúdo não aparecerá mais nos aplicativos móveis do Power BI.

## <a name="migrating-content-in-your-archived-workspace"></a>Migração de conteúdo no Workspace Arquivado

Para continuar usando o Power BI, você deverá criar novo conteúdo em Meu Workspace. Você também deve planejar migrar qualquer conteúdo em seu Workspace Arquivado para o Meu Workspace.  Como migrar o conteúdo depende do tipo de conteúdo:

* **Conjuntos de dados do Power BI Desktop ou Excel**: migre esses conjuntos de dados alternando do Workspace Arquivado para Meu Workspace e recarregue o arquivo do Excel ou do Power BI Desktop selecionando o botão **Meus dados**.  Se você configurar a atualização agendada, você precisará reconfigurar as configurações para o novo conjunto de dados no Meu Workspace.

* **Outros conjuntos de dados**: alterne para o Meu Workspace e, em seguida, clique no botão **Obter Dados** para reconectar-se a quaisquer outros conjuntos de dados criados em seu Workspace Arquivado.  Talvez seja necessário inserir novamente as informações de conexão ou segurança.

* **Relatórios**: os relatórios contidos nos arquivos do Excel ou Power BI Desktop serão recriados automaticamente depois que você carregar novamente o arquivo do Excel ou Power BI Desktop correspondente. Os relatórios instalados como parte de um pacote de conteúdo também serão recriados quando você se reconectar ao pacote de conteúdo. Se você criar seus próprios relatórios por meio do serviço Power BI, recrie esses relatórios no Meu Workspace.

* **Painéis**: painéis instalados como parte dos pacotes de conteúdo são recriados automaticamente quando você se reconectar ao pacote de conteúdo no Meu Workspace. Se você criar seus próprios painéis por meio do serviço Power BI, recrie esses painéis no Meu Workspace.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

