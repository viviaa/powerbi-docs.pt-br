---
title: Copiar relatórios de outros workspaces (versão prévia) – Power BI
description: Saiba como você pode compartilhar um conjunto de dados com usuários em toda a organização. Em seguida, eles podem criar relatórios com base no conjunto de dados em seus próprios workspaces.
author: maggiesMSFT
manager: kfile
ms.reviewer: chbraun
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/31/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 507af4de9d57d2d54fe3e28bca8b1aff7da5cf30
ms.sourcegitcommit: 7c426a5209d4fdd1360fc3d0442d57991be1984d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66461455"
---
# <a name="copy-reports-from-other-workspaces-preview"></a>Copiar relatórios de outros workspaces (versão prévia)

Saiba como você pode copiar um relatório de um workspace e salvá-lo em outro workspace. Em seguida, você pode modificar esse relatório, adicionando ou excluindo visuais e outros elementos.

Quando você encontrar um relatório de seu interesse, em um workspace ou um aplicativo, você poderá fazer uma cópia dele e, em seguida, modificá-lo de acordo com suas necessidades. Você não precisa se preocupar com a criação do modelo de dados. Ele já foi criado para você. Além disso, é muito mais fácil modificar um relatório existente do que começar do zero.

## <a name="save-a-copy-of-a-report"></a>Salvar uma cópia de um relatório

1. Em um aplicativo ou um workspace, acesse a exibição de lista Relatórios.

1. Em **Ações**, selecione **Salvar uma cópia**.

    ![Salvar uma cópia de um relatório](media/service-datasets-copy-reports/power-bi-dataset-save-report-copy.png)

    Você só verá o ícone **Salvar uma cópia** se o relatório estiver em um workspace da nova experiência e você tiver [permissões Criar](service-datasets-build-permissions.md#build-permissions-for-shared-datasets). Mesmo que tiver acesso ao workspace, você precisará ter permissões Criar no conjunto de dados.

3. Em **Salvar uma cópia deste relatório**, dê um nome ao relatório e selecione o workspace de destino.

    ![Caixa de diálogo Salvar uma cópia](media/service-datasets-copy-reports/power-bi-dataset-save-report.png)

    Salve o relatório no workspace atual ou em outro workspace no serviço do Power BI. Você só verá os workspaces que são os workspaces da nova experiência no qual você é membro.
  
4. Selecione **Salvar**.

    Ao salvar uma cópia do relatório, você criará uma conexão dinâmica com o conjunto de dados e poderá abrir a experiência de criação de relatório com o conjunto de dados completo disponível. Você não fez uma cópia do conjunto de dados. O conjunto de dados ainda reside em sua localização original. Você pode usar todas as tabelas e as medidas no conjunto de dados para criar seu próprio relatório. As restrições de RLS (Segurança em Nível de Linha) no conjunto de dados estão em vigor, de modo que você veja apenas os dados que têm permissões de ver de acordo com sua função RLS.

    O Power BI cria automaticamente uma entrada na lista de conjuntos de dados se o relatório é baseado em um conjunto de dados fora do workspace. O ícone para esse conjunto de dados é diferente do ícone para conjuntos de dados no workspace: ![Ícone do conjunto de dados compartilhado](media/service-datasets-discover-across-workspaces/power-bi-shared-dataset-icon.png)


    Dessa forma, os membros do workspace podem saber quais relatórios e dashboards usam conjuntos de dados que estão fora do workspace. A entrada mostra informações sobre o conjunto de dados e algumas ações selecionadas.

    ![Ações do conjunto de dados](media/service-datasets-across-workspaces/power-bi-dataset-actions.png)

## <a name="view-related-datasets"></a>Exibir conjuntos de dados relacionados

Quando você tiver um relatório no workspace, talvez você precise saber em qual conjunto de dados ele se baseia.

1. Na exibição de lista Relatórios, selecione **Exibir relacionados**.

    ![Ícone Exibir relacionados](media/service-datasets-copy-reports/power-bi-dataset-view-related.png)

1. A caixa de diálogo **Conteúdo relacionado** mostra todos os itens relacionados. Nessa lista, o conjunto de dados se parece com qualquer outro. Você não pode saber se ele reside em outro workspace. Esse problema é conhecido.
 
    ![Caixa de diálogo Conteúdo relacionado](media/service-datasets-copy-reports/power-bi-dataset-related.png)


## <a name="next-steps"></a>Próximas etapas

- [Usar conjuntos de dados em workspaces (versão prévia)](service-datasets-across-workspaces.md)
- Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
