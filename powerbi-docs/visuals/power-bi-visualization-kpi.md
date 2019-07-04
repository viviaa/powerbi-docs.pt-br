---
title: Visuais de KPI (Indicador Chave de Desempenho)
description: Criar visuais de KPI (Indicador Chave de Desempenho) no Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: xmja6EpqaO0
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: tutorial
ms.date: 06/24/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 8fa39c7cc57e24f0c19e1a484c0e925bfeec94f7
ms.sourcegitcommit: 1c96b65a03ec0a0612e851dd58c363f4d56bca38
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2019
ms.locfileid: "67389666"
---
# <a name="key-performance-indicator-kpi-visuals"></a>Visuais de KPI (Indicador Chave de Desempenho)

Um KPI (Indicador Chave de Desempenho) é uma indicação visual que comunica a quantidade de progresso feito em relação a uma meta mensurável. Para saber mais sobre KPIs, confira [KPIs (Indicadores Chave de Desempenho) no PowerPivot](/previous-versions/sql/sql-server-2012/hh272050(v=sql.110)).

Veja Will mostrando como criar elementos visuais de métrica únicos: medidores, cartões e KPIs.

<iframe width="560" height="315" src="https://www.youtube.com/embed/xmja6EpqaO0?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="when-to-use-a-kpi"></a>Quando usar um KPI

Os KPIs são uma ótima opção:

* Para medir o progresso. Responde à pergunta: "Estou à frente ou atrás do quê?"

* Para medir a distância até uma meta. Responde à pergunta: "O quão longe estou?"

## <a name="kpi-requirements"></a>Requisitos de KPI

Um designer baseia um visual de KPI em uma medida específica. A intenção do KPI é ajudar você a avaliar o valor e o status atuais de uma métrica em relação a um alvo definido. Um visual de KPI requer uma medida *base* que é avaliada como um valor, uma medida ou um valor de *destino*, bem como um *limite* ou uma *meta*.

Um conjunto de dados de KPI precisa conter valores de meta referente a um KPI. Se seu conjunto de dados não contiver valores de meta, você poderá criá-los adicionando uma planilha do Excel com as metas ao seu modelo de dados ou ao arquivo PBIX.

## <a name="prerequisites"></a>Pré-requisitos

Se você não estiver inscrito no Power BI, [inscreva-se para uma avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.

* [Power BI Desktop](https://powerbi.microsoft.com/get-started/) – é gratuito!

* [O arquivo PBIX do Exemplo de Análise de Varejo](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix)

## <a name="how-to-create-a-kpi"></a>Como criar um KPI

Para acompanhar, abra o [arquivo .PBIX de Análise de Varejo](http://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) no Power BI Desktop. Você criará um KPI que mede o progresso feito para atingir uma meta de vendas.

1. Abra o **Exemplo de Análise de Varejo** na exibição de relatório ![Captura de tela do ícone de exibição de relatório.](media/power-bi-visualization-kpi/power-bi-report-view.png).

1. Selecionar ![Captura de tela da guia amarela.](media/power-bi-visualization-kpi/power-bi-yellow-tab.png) para adicionar uma nova página.

1. No painel **Campos**, selecione **Vendas > Total de Unidades neste Ano**.  Esse valor será o indicador.

1. Adicione **Hora > FiscalMonth**.  Esse valor representará a tendência.

1. No canto superior direito do visual, selecione as reticências e verifique se o Power BI classificou as colunas em ordem crescente por **FiscalMonth**.

    > [!IMPORTANT]
    > Depois de converter a visualização em um KPI, **não** haverá opção para classificar. Você deve classificá-lo corretamente agora.

    ![Captura de tela do menu de reticências expandido com classificação crescente e FiscalMonth selecionado.](media/power-bi-visualization-kpi/power-bi-ascending-by-fiscal-month.png)

    Uma vez classificado corretamente, o visual terá esta aparência:

    ![Captura de tela do visual classificado corretamente.](media/power-bi-visualization-kpi/power-bi-chart.png)

1. Converta o visual em um KPI selecionando o ícone de **KPI** no painel **Visualização**.

    ![Captura de tela do painel Visualizações com o ícone de KPI destacado.](media/power-bi-visualization-kpi/power-bi-kpi-template.png)

1. Para adicionar uma meta, arraste **Total de Unidades do Ano Passado** para o campo **Metas de destino**.

    ![Captura de tela do visual de KPI concluído e do painel Campos com os valores descritos.](media/power-bi-visualization-kpi/power-bi-kpi-done.png)

1. Opcionalmente, formate o KPI selecionando o ícone de rolo de pintura para abrir o painel Formatação.

    * **Indicador** – controla as unidades de exibição e as casas decimais do indicador.

    * **Eixo de tendência** – quando definido como **Ativado**, o visual mostra o eixo de tendência como o plano de fundo do visual de KPI.  

    * **Metas** – quando definido como **Ativado**, o visual mostra a meta e a distância da meta como um percentual.

    * **Codificação de cor > Direção** – as pessoas consideram alguns KPIs melhores para valores *mais altos* e outros melhores para valores *mais baixos*. Por exemplo, ganhos versus tempo de espera. Normalmente, um valor mais alto de ganhos é melhor em comparação com um valor mais alto de tempo de espera. Selecione **alto é bom** e, opcionalmente, altere as configurações de cor.

Os KPIs também estão disponíveis no serviço do Power BI e nos dispositivos móveis. Assim, você tem a opção de estar sempre conectado à pulsação da sua empresa.

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

Se seu KPI não se parecer com o mostrado acima, talvez seja porque você não classificou por **FiscalMonth**. Os KPIs não têm uma opção de classificação. Você precisará iniciar novamente e classificar por **FiscalMonth** *antes* de converter sua visualização em um KPI.

## <a name="next-steps"></a>Próximas etapas

* [Dicas e truques para visualizações de mapa do Power BI](power-bi-map-tips-and-tricks.md)

* [Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)
