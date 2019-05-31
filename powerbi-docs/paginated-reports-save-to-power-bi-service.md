---
title: Publicar um relatório paginado no serviço do Power BI (versão prévia)
description: Neste tutorial, você aprende a publicar um relatório paginado no serviço do Power BI fazendo o upload do computador local.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 11/05/2018
ms.openlocfilehash: 93b712d385b78ea806e57769da72bdf41fbaefc3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61423858"
---
# <a name="publish-a-paginated-report-to-the-power-bi-service-preview"></a>Publicar um relatório paginado no serviço do Power BI (versão prévia)

Neste artigo, você aprende a publicar um relatório paginado no serviço do Power BI fazendo o upload do computador local. Você pode carregar relatórios paginados para o Meu Espaço de Trabalho ou qualquer outro espaço de trabalho, desde que o espaço de trabalho esteja em uma capacidade Premium. Localize o ícone de losango ![Ícone de losango da capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ao lado do nome do espaço de trabalho. 

Se sua fonte de dados de relatório está no local, você precisará [criar um gateway](#create-a-gateway) depois de fazer upload do relatório.

## <a name="add-a-workspace-to-a-premium-capacity"></a>Adicionar um espaço de trabalho a uma capacidade Premium

Se o espaço de trabalho não tem o ícone de losango ![Ícone de losango da capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ao lado do nome, você precisará adicionar o espaço de trabalho a uma capacidade Premium. 

1. Selecione **Espaços de Trabalho**, selecione as reticências ( **...** ) ao lado do nome do espaço de trabalho e, em seguida, selecione **Editar Espaço de Trabalho**.

    ![Selecionar Editar Espaço de Trabalho](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace.png)

1. Na caixa de diálogo **Editar Espaço de Trabalho**, expanda **Avançado** e, em seguida, deslize **Capacidade dedicada** para **Ativado**.

    ![Selecionar Capacidade Dedicada](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-edit-workspace-dialog.png)

   Talvez não seja possível alterá-la. Caso contrário, entre em contato com o administrador da capacidade do Power BI Premium para conceder a você direitos de atribuição para adicionar seu espaço de trabalho a uma capacidade Premium.


## <a name="upload-a-paginated-report"></a>Fazer upload de um relatório paginado

1. Crie seu relatório paginado no Construtor de Relatórios e salve-o em seu computador local.

1. Abra o serviço do Power BI em um navegador e navegue até a área de trabalho Premium onde deseja publicar o relatório. Observe o ícone de losango ![Ícone de losango da capacidade do Power BI Premium](media/paginated-reports-save-to-power-bi-service/premium-diamond.png) ao lado do nome. 

1. Selecione **Obter Dados**.

    ![Obter Dados do Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-get-data.png)

1. Na caixa **Arquivos** , selecione **Obter**.

    ![Obter Arquivos do Power BI](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-files-get.png)

1. Selecione **Arquivo Local** > navegue até o relatório paginado > **Abrir**.

    ![Selecionar Arquivo Local](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-local-file.png)

1. Selecione **Continuar** > **Editar Credenciais**.

    ![Selecionar Editar Credenciais](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-edit-credentials.png)

1. Configure suas credenciais > **Entrar**.

    ![Editar credenciais](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-credentials.png)

   Você vê seu relatório na lista de relatórios.

    ![Relatório paginado na lista Relatórios](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-wwi-report.png)

1. Selecione-o para abri-lo no serviço do Power BI. Se tiver parâmetros, você precisará selecioná-los antes de poder exibir o relatório.
 
    ![Selecionar parâmetros](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-select-parameters.png)

## <a name="create-a-gateway"></a>Criar um gateway

Assim como qualquer outro relatório do Power BI, se a fonte de dados do relatório estiver no local, você precisará criar ou conectar-se a um gateway para acessar os dados.

1. Ao lado do nome do relatório, selecione **Gerenciar**.

   ![Gerenciar um relatório paginado](media/paginated-reports-save-to-power-bi-service/power-bi-paginated-manage.png)

1. Veja o artigo de serviço do Power BI [Instalar um gateway](service-gateway-install.md) para obter detalhes e as próximas etapas.

### <a name="gateway-limitations"></a>Limitações de gateway

Atualmente, os gateways não dão suporte a parâmetros de vários valores.


## <a name="next-steps"></a>Próximas etapas

- [Exibir um relatório paginado no serviço do Power BI](paginated-reports-view-power-bi-service.md)
- [O que são os relatórios paginados no Power BI Premium? (versão prévia)](paginated-reports-report-builder-power-bi.md)

