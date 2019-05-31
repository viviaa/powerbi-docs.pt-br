---
title: Otimizar um visual do Power BI para qualquer tamanho
description: Aprenda a otimizar os visuais em relatórios existentes no Power BI Desktop e no serviço do Power BI para os aplicativos de telefone do Power BI.
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/13/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: 4372f37cf6afc8fe51d6650ddd888bd41d3ea678
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61394860"
---
# <a name="optimize-a-power-bi-visual-for-any-size"></a>Otimizar um visual do Power BI para qualquer tamanho
Por padrão, quando você cria um novo relatório, os visuais são *responsivos*, isto é, eles podem mudar dinamicamente para exibir o máximo de dados e insights, independentemente do tamanho da tela. Para relatórios mais antigos, você também pode definir os elementos visuais para serem redimensionados dinamicamente.

Como um visual muda de tamanho, o Power BI prioriza a exibição de dados, por exemplo, removendo o preenchimento e movendo a legenda para a parte superior do visual automaticamente, para que ele continue informativo mesmo quando fica menor. A capacidade de resposta é especialmente útil em visuais no aplicativo móvel do Power BI em telefones.

![Redimensionamento do visual responsivo](media/desktop-create-responsive-visuals/power-bi-responsive-visual.gif)

Qualquer visual com eixos X e Y e segmentações podem ser redimensionados de maneira responsiva.

## <a name="turn-on-responsiveness-in-power-bi-desktop"></a>Ativar a capacidade de resposta no Power BI Desktop
1. Em um relatório mais antigo no Power BI Desktop, na guia **Exibir**, certifique-se de que você está no **Layout da área de trabalho**.
   
    ![Ícone de Layout da Área de Trabalho](media/desktop-create-responsive-visuals/power-bi-desktop-layout.png)
2. Selecione um visual e no painel **Visualizações**, selecione a seção **Formatar**.
3. Expanda **Geral** > deslize a opção **Responsivo** para a posição **Ativo**.
   
    ![Responsivo ativado](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Agora quando você [criar um relatório otimizado para o telefone](../desktop-create-phone-report.md) e adicionar esse visual, ele será redimensionado com sutileza.

## <a name="turn-on-responsiveness-in-the-power-bi-service"></a>Ativar a capacidade de resposta no serviço do Power BI
Você pode ativar a capacidade de resposta de um visual em um relatório mais antigo do serviço do Power BI. Você precisa ser capaz de editar o relatório.

1. Em um relatório no serviço do Power BI ([https://powerbi.com](https://powerbi.com)), selecione **Editar Relatório**.
2. Selecione um visual e no painel **Visualizações**, selecione a seção **Formatar**.
3. Expanda **Geral** > deslize a opção **Responsivo** para a posição **Ativo**.
   
    ![Responsivo ativado](media/desktop-create-responsive-visuals/power-bi-turn-responsive-on.png)
   
     Agora quando você [criar uma exibição para telefone deste relatório](../desktop-create-phone-report.md) e adicionar esse visual, ele será redimensionado com sutileza.

## <a name="next-steps"></a>Próximas etapas
* [Criar relatórios otimizados para os aplicativos de telefone do Power BI](../desktop-create-phone-report.md)
* [Exibir relatórios do Power BI otimizados para seu telefone](../consumer/mobile/mobile-apps-view-phone-report.md)
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

