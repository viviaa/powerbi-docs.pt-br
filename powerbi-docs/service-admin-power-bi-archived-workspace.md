---
title: Workspace Arquivado do Power BI
description: Workspace Arquivado do Power BI depois de gerenciar locatários do Office 365
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 11/02/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: d2eeab8241de06f9a4d0e654696173d076e01ad2
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61187044"
---
# <a name="power-bi-archived-workspace"></a>Workspace Arquivado do Power BI

Com o Power BI, qualquer pessoa pode inscrever-se e começar a usar o serviço em alguns minutos.  Posteriormente, o departamento de TI da sua organização pode optar por assumir o gerenciamento do Power BI para usuários em sua organização.  Se esse controle ocorrer, você se beneficia do gerenciamento central de usuários e permissões em sua organização. Você também poderá aproveitar a entrada simplificada usando o mesmo nome de usuário e senha utilizados para outros serviços em sua organização.

Qualquer conteúdo que tenha sido criado antes do início do gerenciamento do Power BI por seu departamento de TI será colocado em um Workspace Arquivado do Power BI, que pode ser acessado na barra de navegação à esquerda do [Power BI](https://app.powerbi.com). Você deve começar a criação de conteúdo novo Power BI em Meu Workspace, que é protegido e gerenciado pelo departamento de TI da sua organização.  O workspace arquivado continuará a existir, mas há restrições sobre as ações que podem ser executadas no conteúdo do Workspace Arquivado.  Para remover essas restrições, você precisará migrar o conteúdo do seu Workspace Arquivado para o Meu Workspace, gerenciado pelo departamento de TI.

## <a name="restrictions-in-your-archived-workspace"></a>Restrições em seu Workspace Arquivado

O Power BI não exclui o conteúdo do Workspace arquivado. Você pode continuar a obter dados, criar relatórios e painéis e atualizar conjuntos de dados. Usuários existentes com os quais você compartilhou conteúdo ainda poderão exibir o conteúdo em seu Workspace Arquivado. No entanto, há algumas restrições sobre o conteúdo em seu Workspace Arquivado:

* **OneDrive for Business**: para conjunto de dados em seu Workspace Arquivado, você não poderá obter dados ou atualizá-los pelo OneDrive for Business.  Se você tentar se conectar a essa fonte, você receberá um aviso.

* **Compartilhando dashboards**: É possível compartilhar dashboards com outros usuários do espaço de trabalho arquivado.  Todos os usuários que já têm acesso continuarão a exibir painéis compartilhados, acessando seu Workspace Arquivado.

* **Criando grupos**: Você não pode criar grupos no espaço de trabalho arquivado.

* **Acesso em aplicativos móveis do Power BI**: embora você ainda possa exibir o conteúdo na Web no Workspace Arquivado, esse conteúdo não aparece mais nos aplicativos móveis do Power BI.

## <a name="migrating-content-in-your-archived-workspace"></a>Migração de conteúdo no Workspace Arquivado

Para continuar usando o Power BI, você deverá criar novo conteúdo em Meu Workspace. Você também deve planejar migrar qualquer conteúdo em seu Workspace Arquivado para o Meu Workspace.  Como migrar o conteúdo depende do tipo de conteúdo:

* **Conjuntos de dados do Excel ou do Power BI Desktop**: migre esses conjuntos de dados alternando do Workspace Arquivado para Meu Workspace e carregue novamente o arquivo do Excel ou do Power BI Desktop selecionando o botão **Meus Dados**.  Se você configurar a atualização agendada, você precisará reconfigurar as configurações para o novo conjunto de dados no Meu Workspace.

* **Outros conjuntos de dados**: alterne para Meu Workspace e clique no botão **Obter Dados** para se reconectar a todos os outros conjuntos de dados criados no Workspace Arquivado.  Talvez seja necessário inserir novamente as informações de conexão ou segurança.

* **Relatórios**: os relatórios contidos nos arquivos do Excel ou Power BI Desktop serão recriados automaticamente depois que você carregar novamente o arquivo do Excel ou Power BI Desktop correspondente. Os relatórios instalados como parte de um pacote de conteúdo também serão recriados quando você se reconectar ao pacote de conteúdo. Se você criar seus próprios relatórios por meio do serviço Power BI, recrie esses relatórios no Meu Workspace.

* **Dashboards**: dashboards instalados como parte dos pacotes de conteúdo são recriados automaticamente quando você se reconectar ao pacote de conteúdo no Meu Workspace. Se você criar seus próprios painéis por meio do serviço Power BI, recrie esses painéis no Meu Workspace.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

