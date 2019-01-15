---
title: Introdução à P e R do Power BI
description: Introdução às P e R do serviço do Power BI usando o exemplo de Análise de Varejo
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 11/21/2018
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 87783b928fdec1cadf5318ae184858c37daa4acc
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54279241"
---
# <a name="get-started-with-power-bi-qa"></a>Introdução à P e R do Power BI

Às vezes, a maneira mais rápida de obter uma resposta de seus dados é fazer uma pergunta usando o idioma natural.  Neste início rápido, examinaremos duas formas diferentes de criar a mesma visualização: primeira, compilá-la em um relatório e, segunda, fazer uma pergunta com P e R. Usaremos um serviço do Power BI, mas o processo é quase idêntico usando o Power BI Desktop.

Para acompanhar, você deve usar um relatório que você possa editar, então usaremos um dos exemplos disponíveis com o Power BI.

## <a name="create-a-visual-in-the-report-editor"></a>Criar um visual no editor de relatório

1. Em seu workspace do Power BI, selecione **Obter Dados**\>**Amostras**\>**Amostra de Análise de Varejo** > **Conectar**.
   
2. O painel contém um bloco de gráfico de área para "Vendas do último ano e vendas deste ano”.  Selecione este bloco. Se este bloco foi criado com perguntas e respostas, selecionar o bloco vai abrir o P e R. Mas esse bloco foi criado em um relatório, portanto o relatório é aberto para a página que contém esta visualização.

    ![Dashboard de exemplo de Análise de Varejo](media/power-bi-visualization-introduction-to-q-and-a/power-bi-dashboard.png)

1. Abra o relatório no modo Exibir Edição selecionado **Editar Relatório**.  Se você não for proprietário de um relatório, não terá a opção de abri-lo na exibição de Edição.
   
    ![Botão Editar relatório](media/power-bi-visualization-introduction-to-q-and-a/power-bi-edit-report.png)
4. Selecione o gráfico de área e examinar as configurações do painel **Campos** .  O criador do relatório criou esse gráfico selecionando esses três valores (**Hora > FiscalMonth**, **Vendas > Vendas Deste Ano**, **Vendas > Vendas do Ano Passado > Valor**) e organizando-os nas seções **Eixo** e **Valores**.
   
    ![Painel Visualizações](media/power-bi-visualization-introduction-to-q-and-a/gnatutorial_3-new.png)

## <a name="create-the-same-visual-with-qa"></a>Criar o mesmo visual com P e R

Como podemos criar esse mesmo gráfico de linha usando perguntas e respostas?

![Caixa Fazer uma pergunta](media/power-bi-visualization-introduction-to-q-and-a/power-bi-qna.png)

1. Navegue de volta para o dashboard de exemplo Análise de Varejo.
2. Use a linguagem natural, digite algo semelhante a esta pergunta na caixa de pergunta:
   
   **quais foram as vendas deste ano e as vendas do ano passado por mês como um gráfico de área**
   
   Ao digitar uma pergunta, o P e R do Power BI escolhe a melhor visualização para exibir sua resposta, e a visualização muda dinamicamente, na medida em que você modifica a pergunta. Além disso, P e R e ajuda a formatar sua pergunta com sugestões, preenchimento automático e a correção ortográfica.
   
   Quando você terminar de digitar sua pergunta, o resultado será exatamente o mesmo gráfico que vimos no relatório.  Mas criá-lo dessa maneira era muito mais rápido!
   
   ![Exemplo de pergunta](media/power-bi-visualization-introduction-to-q-and-a/powerbi-qna-areachart.png)
3. De modo semelhante ao trabalho com relatórios, na P e R, você tem acesso aos painéis Visualizações, Filtros e Campos.  Abra esses painéis para explorar e modificar ainda mais seu visual.
4. Para fixar o gráfico no dashboard, selecione o ícone de marcador ![Ícone de Fixar](media/power-bi-visualization-introduction-to-q-and-a/pinnooutline.png).

## <a name="next-steps"></a>Próximas etapas
[P e R no Power BI](consumer/end-user-q-and-a.md)

[Faça seus dados funcionarem bem com P e R no Power BI](service-prepare-data-for-q-and-a.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

