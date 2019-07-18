---
title: Usar conjuntos de dados em workspaces (versão prévia) – Power BI
description: Saiba como você pode compartilhar um conjunto de dados com usuários em toda a organização. Em seguida, eles podem criar relatórios com base no conjunto de dados em seus próprios workspaces.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 07/03/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 17a8e1c9e0d46a56d6b6ff3e46c0fda6da8ffe12
ms.sourcegitcommit: b439ded53bfbbb58be27ecedf93d618f5158df33
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/04/2019
ms.locfileid: "67567839"
---
# <a name="use-datasets-across-workspaces-preview"></a>Usar conjuntos de dados em workspaces (versão prévia)

Business intelligence é uma atividade colaborativa. É importante estabelecer conjuntos de dados padronizados que possam ser a 'única fonte de verdade'. Em seguida, descobrir e reutilizar esses conjuntos de dados padronizados é fundamental. Quando os modeladores de dados especialistas em sua organização criam e compartilham conjuntos de dados otimizados, os criadores de relatórios podem começar com esses conjuntos de dados para criar relatórios precisos. Em seguida, sua organização terá dados consistentes para tomar decisões e uma cultura de dados íntegra.

![Selecionar um conjunto de dados compartilhado](media/service-datasets-across-workspaces/power-bi-select-shared-dataset.png)

No Power BI, os criadores de conjunto de dados podem *certificar* ou *promover* conjuntos de dados para que outras pessoas possam descobri-los. Dessa forma, os autores do relatório sabem quais conjuntos de dados são de alta qualidade e oficiais, e eles podem usar esses conjuntos de dados sempre que criarem no Power BI. Os proprietários de conjunto de dados podem manter o controle de quem tem acesso aos seus dados usando a opção [Permissão Criar](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Os administradores de locatários têm uma nova configuração de locatário para [controlar o uso de conjuntos de dados em workspaces](service-datasets-admin-across-workspaces.md).

## <a name="dataset-sharing-and-the-new-workspace-experience"></a>Compartilhamento de conjuntos de dados e a nova experiência de workspace

A criação de relatórios com base em conjuntos de dados em diferentes workspaces e a cópia de relatórios para diferentes workspaces estão estreitamente ligados à [nova experiência de workspace](service-create-the-new-workspaces.md):

- No serviço, quando você abre o catálogo do conjunto de dados em uma nova experiência de espaço de trabalho, o catálogo do conjunto de dados mostra os conjuntos de dados que estão em Meu Espaço de Trabalho e outros espaço de trabalhos da nova experiência de espaço de trabalho. 
- Quando você abre o catálogo do conjunto de dados em um workspace clássico, você vê apenas os conjuntos de dados desse workspace, não aqueles de outros workspaces.
- No Desktop, você pode publicar relatórios do Live Connect em diferentes workspaces, desde que os conjuntos de dados estejam em workspaces da nova experiência.
- Ao copiar relatórios em workspaces, o workspace de destino precisa ser um workspace da nova experiência.

## <a name="build-permission-for-datasets"></a>Permissão Criar em conjuntos de dados

Com o tipo de permissão Criar, você pode permitir que outras pessoas em sua organização criem um conteúdo, como relatórios, dashboards e blocos fixados de P e R, em um conjunto de dados existente. Elas também podem criar um conteúdo no conjunto de dados fora do Power BI, como planilhas do Excel por meio do recurso Analisar no Excel, XMLA e Exportar. Leia mais sobre a [Permissão Criar](service-datasets-build-permissions.md#build-permissions-for-shared-datasets).

## <a name="discover-datasets-preview"></a>Descobrir conjuntos de dados (versão prévia)

Ao criar um relatório com base em um conjunto de dados existente, a primeira etapa é se conectar ao conjunto de dados, no serviço do Power BI ou no Power BI Desktop. Leia mais sobre [como descobrir conjuntos de dados em diferentes workspaces (versão prévia)](service-datasets-discover-across-workspaces.md)

## <a name="copy-a-report"></a>Copiar um relatório

Quando você encontrar um relatório de seu interesse, em um workspace ou um aplicativo, você poderá fazer uma cópia dele e, em seguida, modificá-lo de acordo com suas necessidades. Você não precisa se preocupar com a criação do modelo de dados. Ele já é criado para você. Além disso, é muito mais fácil modificar um relatório existente do que começar do zero. Leia mais sobre como [copiar relatórios](service-datasets-copy-reports.md).

## <a name="promotion-and-certification"></a>Promoção e certificação

Se você criar conjuntos de dados, crie um com o qual outras pessoas possam se beneficiar e facilite sua descoberta [promovendo seu conjunto de dados](service-datasets-promote.md). Solicite também aos especialistas de sua organização a [certificação do conjunto de dados](service-datasets-certify.md).

## <a name="licensing"></a>Licenças

Os recursos específicos e as experiências criadas com base nas funcionalidades do conjunto de dados compartilhado são licenciados de acordo com os cenários existentes.  Por exemplo:

- Em geral, a descoberta e a conexão a conjuntos de dados compartilhados estão disponíveis para qualquer pessoa. No entanto, os usuários sem uma licença Pro só podem se conectar aos conjuntos de dados que residem no Meu Workspace pessoal ou em workspaces Premium.
- A promoção e a certificação de conjuntos de dados fora de workspaces pessoais exigem uma licença Pro, porque você precisa ter uma licença Pro para ser membro em um workspace do aplicativo.
- A cópia de relatórios entre workspaces exige uma licença Pro, novamente, porque você precisa ter uma licença Pro para ser membro em um workspace do aplicativo.
- A cópia de relatórios por meio de um aplicativo exige uma licença Pro, como era necessário para pacotes de conteúdo organizacional.

## <a name="considerations-and-limitations"></a>Considerações e limitações

- A criação de um relatório com base em um conjunto de dados em outro workspace exige a nova experiência de workspace em ambas as extremidades: O relatório e o conjunto de dados precisam estar em uma nova experiência de workspace.
- Em um workspace clássico, a experiência de descoberta de conjunto de dados mostra apenas os conjuntos de dados desse workspace.
- Você pode criar relatórios em workspaces de aplicativo baseados em conjuntos de dados de outro workspace. No entanto, não é possível criar um aplicativo para um workspace que contém esses conjuntos de dados.
- Os usuários gratuitos do Desktop só veem os conjuntos de dados de Meu Workspace e de workspaces Premium.
- Caso você deseje adicionar um relatório com base em um conjunto de dados compartilhado a um aplicativo, você precisará ser membro do workspace do conjunto de dados. Esse é um problema conhecido.
- O recurso “Publicar na Web” não funciona para um relatório baseado em um conjunto de dados compartilhado. Isso ocorre por design.
- Se duas pessoas forem membros de um workspace que acessa um conjunto de dados compartilhado, talvez apenas uma delas veja o conjunto de dados relacionado no workspace. Somente as pessoas com, pelo menos, acesso de leitura ao conjunto de dados podem ver o conjunto de dados compartilhado. 

## <a name="next-steps"></a>Próximas etapas

- [Promover conjuntos de dados](service-datasets-promote.md)
- [Certificar conjuntos de dados](service-datasets-certify.md)
- [Controlar o uso de conjuntos de dados em workspaces](service-datasets-admin-across-workspaces.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
