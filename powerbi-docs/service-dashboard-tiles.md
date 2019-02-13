---
title: Introdução aos blocos de dashboard para designers do Power BI
description: Tudo sobre blocos de dashboard no Power BI. Isso inclui blocos que são criados nos relatórios do SSRS (SQL Server Reporting Services).
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: c8b5728c951bc1a25e71da8885997814c5485cd4
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56215977"
---
# <a name="intro-to-dashboard-tiles-for-power-bi-designers"></a>Introdução aos blocos de dashboard para designers do Power BI

Um bloco é um instantâneo dos dados fixados no painel. Um bloco pode ser criado de relatórios, conjuntos de dados, dashboards, caixas de P e R, relatórios do SSRS (SQL Server Reporting Services) e muito mais.  Essa captura de tela mostra vários blocos diferentes fixados a um dashboard.

![Dashboard do Power BI](media/service-dashboard-tiles/power-bi-dashboard.png)

Os dashboards e blocos de dashboard são um recurso do serviço do Power BI e não do Power BI Desktop. Você não pode criar dashboards em dispositivos móveis, mas pode [exibir e compartilhar](mobile-apps-view-dashboard.md) os dashboards lá.

Além da anexação, você pode criar blocos autônomos diretamente no dashboard usando a opção [Adicionar bloco](service-dashboard-add-widget.md). Os blocos autônomos incluem: caixas de texto, imagens, vídeos, dados de streaming e conteúdo da Web.

Precisa de ajuda para compreender os blocos de construção que compõem o Power BI?  Veja [Power BI – Conceitos básicos](service-basic-concepts.md).

> [!NOTE]
> Se a visualização original usada para criar o bloco for alterada, o bloco não será alterado.  Por exemplo, se você fixou um gráfico de linhas de um relatório e, em seguida, você alterar o gráfico de linhas para um gráfico de barras, o bloco do dashboard continuará mostrando um gráfico de linhas. Os dados são atualizados, mas o tipo de visualização não.
> 
> 

## <a name="pin-a-tile-from"></a>Fixe um bloco de...
Há diversas maneiras de adicionar (fixar) um bloco em um dashboard. Os blocos podem ser fixados de:

* [Perguntas e respostas do Power BI](service-dashboard-pin-tile-from-q-and-a.md)
* [um relatório](service-dashboard-pin-tile-from-report.md)
* [outro dashboard](service-pin-tile-to-another-dashboard.md)
* [uma pasta de trabalho do Excel no OneDrive for Business](service-dashboard-pin-tile-from-excel.md)
* [Power BI Publisher para Excel](publisher-for-excel.md)
* [Insights Rápidos](service-insights.md)
* [Reporting Services](https://docs.microsoft.com/sql/reporting-services/pin-reporting-services-items-to-power-bi-dashboards)

Além disso, blocos autônomos para imagens, caixas de texto, vídeos, dados de streaming e o conteúdo da Web podem ser criados diretamente no dashboard usando a opção [Adicionar bloco](service-dashboard-add-widget.md).

  ![Ícone Adicionar bloco](media/service-dashboard-tiles/add_widgetnew.png)

## <a name="interacting-with-tiles-on-a-dashboard"></a>Interagir com blocos em um painel
### <a name="move-and-resize-a-tile"></a>Mover e redimensionar um bloco
Pegue um bloco e [mova-o no dashboard](service-dashboard-edit-tile.md). Passe o mouse e selecione o identificador ![identificador](media/service-dashboard-tiles/resize-handle.jpg) para redimensionar o bloco.

### <a name="hover-over-a-tile-to-change-the-appearance-and-behavior"></a>Passe o mouse sobre um bloco para alterar a aparência e o comportamento
1. Passe o mouse sobre o bloco para exibir as reticências.
   
    ![reticências do bloco](media/service-dashboard-tiles/ellipses_new.png)
2. Selecione as reticências para abrir o menu de ação do bloco.
   
    ![ícone de reticências](media/service-dashboard-tiles/power-bi-tile-menu.png)
   
    A partir daqui, você pode:
   
   * [Abrir o relatório que foi usado para criar este bloco ](service-reports.md) ![ícone de relatório](media/service-dashboard-tiles/chart-icon.jpg)  
   
   * [Abrir a planilha que foi usada para criar este bloco ](service-reports.md) ![ícone de planilha](media/service-dashboard-tiles/power-bi-open-worksheet.png)  
     
    * [Exibir no modo de foco ](service-focus-mode.md) ![ícone de foco](media/service-dashboard-tiles/fullscreen-icon.jpg)  
     * [Exportar os dados usados no bloco](visuals/power-bi-visualization-export-data.md) ![ícone exportar dados](media/service-dashboard-tiles/export-icon.png)
     * [Editar título e subtítulo, adicionar um hiperlink](service-dashboard-edit-tile.md) ![editar ícone](media/service-dashboard-tiles/pencil-icon.jpg)
     * [Executar insights ](service-insights.md) ![ícone de insights](media/service-dashboard-tiles/power-bi-insights.png)
     * [Fixar o bloco em outro dashboard](service-pin-tile-to-another-dashboard.md)
       ![ícone fixar](media/service-dashboard-tiles/pin-icon.jpg)
     * [Remover o bloco](service-dashboard-edit-tile.md)
     ![ícone excluir](media/service-dashboard-tiles/trash-icon.png)
3. Para fechar o menu de ação, selecione uma área em branco na tela.

### <a name="select-click-a-tile"></a>Selecionar (clicar em) um bloco
Quando você seleciona um bloco, o que acontece em seguida depende de como você o criou. Ainda, se ele tiver um [link personalizado](service-dashboard-edit-tile.md), a seleção do bloco levará você para esse link. Caso contrário, selecionar o bloco leva você para o relatório, pasta de trabalho do Excel Online, relatório do Reporting Services local ou pergunta de P & R usada para criar o bloco.

> [!NOTE]
> Os blocos de vídeo criados diretamente no painel usando **Adicionar bloco** são a exceção. Selecionar um bloco de vídeo (que foi criado dessa forma) faz com que o vídeo seja reproduzido diretamente no dashboard.   
> 
> 

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

* Se o relatório usado para criar a visualização não tiver sido salvo, então selecionar um bloco não produzirá nenhuma ação.
* Se o bloco tiver sido criado de uma pasta de trabalho no Excel Online, você precisará de pelo menos permissões de Leitura para essa pasta de trabalho. Caso contrário, a seleção do bloco não abrirá a pasta de trabalho no Excel Online.
* Digamos que você crie um bloco diretamente no dashboard usando **Adicionar bloco** e defina um hiperlink personalizado para ele. Se for o caso, quando você seleciona o título, o subtítulo ou o bloco abre essa URL. Caso contrário, por padrão, quando você seleciona um bloco criado diretamente no dashboard para uma imagem, um código da Web ou uma caixa de texto, nada acontece.
* Se você não tem permissão para o relatório no Reporting Services, a seleção de um bloco criado por um relatório do Reporting Services leva você até uma página indicando que você não tem acesso (rsAccessDenied).
* Se você não tiver acesso à rede na qual o servidor do Reporting Services, a seleção de um bloco criado do Reporting Services levará você até uma página que indica que não é possível localizar o servidor (HTTP 404). O dispositivo precisa ter acesso à rede para o servidor de relatório exibir o relatório.
* Se a visualização original usada para criar o bloco for alterada, o bloco não será alterado.  Por exemplo, se você fixar um gráfico de linhas de um relatório e, em seguida, alterar o gráfico de linhas para um gráfico de barras, o bloco do painel continuará mostrando um gráfico de linhas. Os dados são atualizados, mas o tipo de visualização não.

## <a name="next-steps"></a>Próximas etapas
[Criar um cartão (bloco de número grande) para seu painel](power-bi-visualization-card.md)

[Dashboards no Power BI](service-dashboards.md)  

[Atualização de dados](refresh-data.md)

[Power BI – conceitos básicos](service-basic-concepts.md)

[Exportar um bloco para o Power Point](http://blogs.msdn.com/b/powerbidev/archive/2015/09/28/integrating-power-bi-tiles-into-office-documents.aspx)

[Fixar itens do Reporting Services em Dashboards do Power BI](https://msdn.microsoft.com/library/mt604784.aspx)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

