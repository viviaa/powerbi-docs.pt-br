---
title: Criar um relatório com base em um conjunto de dados
description: Crie um relatório do Power BI de um conjunto de dados.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: 6b69c2b1fa811d395a26403de852c44af33491c7
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770239"
---
# <a name="create-a-report-in-the-power-bi-service-by-importing-a-dataset"></a>Criar um relatório no serviço do Power BI importando um conjunto de dados
Você já leu [Relatórios no Power BI](consumer/end-user-reports.md) e agora deseja criar o seu próprio relatório. Há diferentes maneiras de criar um relatório. Neste artigo, vamos começar criando um relatório básico no serviço do Power BI de um conjunto de dados do Excel. Depois de compreender os fundamentos da criação de um relatório, confira a [próximas etapas](#next-steps) no final para obter mais informações avançadas tópicos de relatório.  

## <a name="prerequisites"></a>Pré-requisitos
- [Inscreva-se no serviço do Power BI](service-self-service-signup-for-power-bi.md). Para criar relatórios usando o Power BI Desktop, confira [exibição de relatório da área de trabalho](desktop-report-view.md). 
- [Baixe o conjunto de dados do Excel de exemplo análise de varejo](http://go.microsoft.com/fwlink/?LinkId=529778) e salve-o para o OneDrive for Business ou localmente.

## <a name="import-the-dataset"></a>Importar o conjunto de dados
Esse método para a criação de um relatório começa com um conjunto de dados e uma tela de relatório em branco. Você pode acompanhar o conjunto de dados do Excel de exemplo análise de varejo.

1. Devemos criar o relatório em um espaço de trabalho de serviço do Power BI, então, selecione um espaço de trabalho existente ou criar uma um.
   
   ![lista de workspaces do aplicativo](media/service-report-create-new/power-bi-workspaces2.png)
2. Na parte inferior do painel de navegação esquerdo, selecione **obter dados**.
   
   ![Obter dados](media/service-report-create-new/power-bi-get-data3.png)
3. Selecione **Arquivos** e navegue até o local em que você salvou o exemplo Análise de Varejo.
   
    ![selecionar Arquivos](media/service-report-create-new/power-bi-select-files.png)
4. Para este exercício, selecione **Importar**.
   
   ![selecionar Importar](media/service-report-create-new/power-bi-import.png)
5. Depois que o conjunto de dados for importado, selecione **Exibir conjunto de dados**.
   
   ![selecionar Exibir conjunto de dados](media/service-report-create-new/power-bi-view-dataset.png)
6. Na verdade, exibir um conjunto de dados abre o editor de relatório.  Você verá uma tela em branco e as ferramentas de edição do relatório.
   
   ![editor de relatório](media/service-report-create-new/power-bi-blank-report.png)

> [!TIP]
> Se você não estiver familiarizado com a tela de edição de relatório ou precisar de um lembrete [faça um tour pelo editor de relatório](service-the-report-editor-take-a-tour.md) antes de continuar. > 
> 

## <a name="add-a-radial-gauge-to-the-report"></a>Adicionar um Medidor Radial ao relatório
Agora que nosso conjunto de dados foi importado, vamos começar respondendo algumas perguntas.  Nossa CMO (Diretora de Marketing) quer saber se estamos próximos de alcançar as metas de vendas deste ano. Um Medidor é uma [boa opção de visualização](visuals/power-bi-report-visualizations.md) para exibir esse tipo de informação.

1. No painel Campos, selecione **Vendas** > **Vendas Deste Ano** > **Valor**.
   
    ![gráfico de barras no editor de relatório](media/service-report-create-new/power-bi-report-step1.png)
2. Converta o visual em um Medidor selecionando o modelo de Medidor ![ícone de Medidor](media/service-report-create-new/powerbi-gauge-icon.png) no painel **Visualizações**.
   
    ![Visual de medidor no editor de relatório](media/service-report-create-new/power-bi-report-step2.png)
3. Arraste **Vendas** > **Vendas Deste Ano** > **Meta** para a seção **Valor de Destino**. Parece que estamos muito perto de alcançar a nossa meta.
   
    ![Visual de medidor com valor Meta como destino](media/service-report-create-new/power-bi-report-step3.png)
4. Agora seria um bom momento para salvar seu relatório.
   
   ![Menu Arquivo](media/service-report-create-new/powerbi-save.png)

## <a name="add-an-area-chart-and-slicer-to-the-report"></a>Adicionar um gráfico de área e uma segmentação de dados ao relatório
Nossa CMO tem algumas perguntas adicionais para respondermos. Ela gostaria de ver a comparação das vendas deste ano com as vendas do ano passado. E também desejaria ver os resultados por distrito.

1. Primeiro, vamos criar espaço em nossa tela. Selecione o Medidor e mova-o para o canto superior direito. Em seguida, pegue e arraste um dos cantos e torne-o menor.
2. Desmarque o medidor. No painel Campos, selecione **Vendas** > **Vendas Deste Ano** > **Valor** e selecione **Vendas** > **Vendas do Ano Passado**.
   
    ![editor de relatório com medidor e gráfico de barras](media/service-report-create-new/power-bi-report-step4.png)
3. Converta o visual em um gráfico de Área selecionando o modelo de Gráfico de áreas ![ícone de gráfico](media/service-report-create-new/power-bi-areachart-icon.png) no painel **Visualizações**.
4. Selecione **Tempo** > **Período** para adicionar ao **Eixo** também.
   
    ![editor de relatório com gráfico de área ativo](media/service-report-create-new/power-bi-report-step5.png)
5. Para classificar a visualização por período de tempo, selecione as reticências e escolha **Classificar por Período**.
6. Agora vamos adicionar a segmentação de dados. Selecione uma área vazia na tela e escolha a segmentação ![Modelo de ícone](media/service-report-create-new/power-bi-slicer-icon.png) de segmentação. Agora temos uma segmentação de dados vazia em nossa tela.
   
    ![tela de relatório](media/service-report-create-new/power-bi-report-step6.png)    
7. No painel Campos, selecione **Distrito** > **Distrito**. Mova e redimensione a segmentação de dados.
   
    ![Editor de relatório, adicionar Distrito](media/service-report-create-new/power-bi-report-step7.png)  
8. Use a segmentação de dados para procurar por padrões e insights por Distrito.
   
   ![vídeo de como usar a segmentação](media/service-report-create-new/power-bi-slicer-video2.gif)  

Continue explorando seus dados e adicionando visualizações. Quando você encontrar insights especialmente interessantes, [fixe-os em um painel](service-dashboard-pin-tile-from-report.md).

## <a name="next-steps"></a>Próximas etapas

* Saiba como [fixar visualizações em um dashboard](service-dashboard-pin-tile-from-report.md)   
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

