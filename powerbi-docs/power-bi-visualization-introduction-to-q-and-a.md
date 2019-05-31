---
title: Criar um visual com o Power BI Q & A
description: Aprenda a criar um visual com p e r no serviço do Power BI usando o exemplo de análise de varejo
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 580b387f8c763b0457bd32a71bfbccd90d4040a3
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625200"
---
# <a name="create-a-visual-with-power-bi-qa"></a>Criar um visual com o Power BI Q & A

Às vezes, a maneira mais rápida de obter uma resposta de seus dados é fazer uma pergunta usando o idioma natural.  Neste artigo, examinamos duas maneiras diferentes de criar a mesma visualização: primeiro, fazer uma pergunta com p e r e em segundo lugar, compilá-la em um relatório. Podemos usar o serviço do Power BI para criar o visual no relatório, mas o processo é quase idêntico usando o Power BI Desktop.

![Gráfico do Power BI preenchido](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-visual.png)

Para acompanhar, você deve usar um relatório que você possa editar, então usaremos um dos exemplos disponíveis com o Power BI.

## <a name="create-a-visual-with-qa"></a>Criar um visual com p e r

Como podemos criar esse gráfico de linhas usando p e R?

1. Em seu workspace do Power BI, selecione **Obter Dados**\>**Amostras**\>**Amostra de Análise de Varejo** > **Conectar**.

1. Abra o painel de exemplo de análise de varejo e coloque o cursor em uma caixa, p **faça uma pergunta sobre seus dados**.

    ![Coloque o cursor em uma caixa de p](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-cursor-in-qna-box.png)

2. Na caixa de p uma, digite algo semelhante essa pergunta:
   
    **vendas deste ano e vendas do ano passado por mês como um gráfico de área**
   
    Ao digitar uma pergunta, o P e R do Power BI escolhe a melhor visualização para exibir sua resposta, e a visualização muda dinamicamente, na medida em que você modifica a pergunta. Além disso, P e R e ajuda a formatar sua pergunta com sugestões, preenchimento automático e a correção ortográfica. P e r recomenda uma alteração pequena frase: "vendas deste ano e vendas do ano passado por *mês tempo* como um gráfico de área".  

    ![P e r corrigido de palavras](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-corrected-create-filled-chart.png)

4. Selecione a sentença para aceitar a sugestão. 
   
   Quando você termina de digitar sua pergunta, o resultado é o mesmo gráfico que você vê no painel.
   
   ![Perguntas e respostas em um gráfico de área preenchida](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna-create-filled-chart.png)

4. Para fixar o gráfico no dashboard, selecione o ícone de marcador ![Ícone de Fixar](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png) no canto superior direito.

## <a name="create-a-visual-in-the-report-editor"></a>Criar um visual no editor de relatório

1. Navegue de volta para o dashboard de exemplo Análise de Varejo.
   
2. O painel contém o mesmo bloco de gráfico de área para "Vendas do último ano e vendas neste ano."  Selecione este bloco. Não selecione o bloco que você criou com p e r. Selecioná-lo abre o p e r. O bloco de gráfico de área original foi criado em um relatório, para que o relatório é aberto para a página que contém esta visualização.

    ![Dashboard de exemplo de Análise de Varejo](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Abra o relatório no modo Exibir Edição selecionado **Editar Relatório**.  Se você não for proprietário de um relatório, não terá a opção de abri-lo na exibição de Edição.
   
    ![Botão Editar relatório](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Selecione o gráfico de área e examinar as configurações do painel **Campos** .  O criador do relatório criou este gráfico selecionando esses três valores (**vendas do ano passado** e **vendas deste ano > valor** do **vendas** tabela, e  **Mês fiscal** do **tempo** tabela) e organizando-os no **eixo** e **valores** wells.
   
    ![Painel Visualizações](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

    Você verá que eles terminou com o mesmo elemento visual. Criá-lo dessa maneira não era muito complicada. Mas criá-lo com p e r foi mais fácil!

## <a name="next-steps"></a>Próximas etapas

- [Usar p e r em painéis e relatórios](power-bi-tutorial-q-and-a.md)  
- [P e r para consumidores](consumer/end-user-q-and-a.md)
- [Faça seus dados funcionarem bem com P e R no Power BI](service-prepare-data-for-q-and-a.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

