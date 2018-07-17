---
title: Exibir e editar as configurações de parâmetros de conjunto de dados no serviço do Power BI
description: Os parâmetros de consulta são criados no Power BI Desktop, mas podem ser examinados e atualizados no serviço do Power BI
author: mihart
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 06/26/2018
ms.author: mihart
LocalizationGroup: Create reports
ms.openlocfilehash: ac271e8013bce5824931153351a651644a716a2f
ms.sourcegitcommit: 5eb8632f653b9ea4f33a780fd360e75bbdf53b13
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965149"
---
# <a name="what-is-a-query-parameter"></a>O que é um parâmetro de consulta?
Os parâmetros de consulta são adicionados no Power BI Desktop por criadores de relatório. Os parâmetros permitem que eles façam que partes dos relatórios dependam de um ou mais *valores* de parâmetro. Por exemplo, um criador de relatórios pode criar um parâmetro que restringe os dados a um único countryregion ou um parâmetro que define os formatos aceitáveis para campos como datas, hora e texto.

![Guia Início mostrando a opção Gerenciar parâmetros no Desktop](media/service-parameters/power-bi-manage-parameters.png)


## <a name="review-and-edit-parameters-in-power-bi-service"></a>Revisar e editar parâmetros no serviço do Power BI

Assim que os parâmetros são definidos no Desktop, quando o [relatório é publicado no serviço do Power BI](desktop-upload-desktop-files.md), as seleções e as configurações do parâmetro vão junto com o relatório. Algumas configurações de parâmetro podem ser examinadas e editas no serviço do Power BI, não os parâmetros que restringem os dados disponíveis, mas os parâmetros que definem e descrevem os valores aceitáveis.

1. No serviço do Power BI, selecione o ícone de engrenagem ![ícone de engrenagem](media/service-parameters/power-bi-cog.png) e escolha **Configurações**.

2. Selecione a guia para os **Conjuntos de dados** e destaque um conjunto de dados na lista. 
    
    ![Janela Configurações com a guia Conjuntos de dados selecionada](media/service-parameters/power-bi-select-dataset2.png)

3. Expanda **Parâmetros**.  Se o conjunto de dados selecionado não tiver parâmetros, você verá uma mensagem com um link para Saiba mais sobre os parâmetros de consulta. No entanto, se o conjunto de dados tiver parâmetros, expandir **Parâmetros** revelará esses parâmetros. 

    ![Janela Configurações com a guia Parâmetros expandida](media/service-parameters/power-bi-settings.png)

    Examine as configurações do parâmetro e faça alterações, se necessário. Os campos em cinza não são editáveis. 


## <a name="next-steps"></a>Próximas etapas
Um modo específico para adicionar parâmetros simples é [modificando a URL](service-url-filters.md).