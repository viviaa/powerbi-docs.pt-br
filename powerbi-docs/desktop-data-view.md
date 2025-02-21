---
title: Exibição de Dados no Power BI Desktop
description: Exibição de Dados no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 567beb29ecdcaf8a07023c8c8c9b32995623534c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65454478"
---
# <a name="data-view-in-power-bi-desktop"></a>Exibição de Dados no Power BI Desktop
A **Exibição de Dados** ajuda a inspecionar, explorar e compreender os dados no modelo do **Power BI Desktop**. É diferente do modo como você exibe tabelas, colunas e dados no **Editor de Consultas**. Com a Exibição de Dados, você está olhando para seus dados *após* eles terem sido carregados no modelo.

Quando você está modelando seus dados, às vezes você deseja ver o que está realmente em uma tabela ou coluna, sem criar um elemento visual na tela de relatório, geralmente imediatamente abaixo do nível de linha. Isso é útil principalmente quando você está criando colunas calculadas e medidas ou quando você precisa identificar um tipo de dados ou uma categoria de dados.

Vamos examinar com mais detalhes alguns dos elementos encontrados na **Exibição de Dados**.

![Exibição de dados no Power BI Desktop](media/desktop-data-view/dataview_fullscreen.png)

1. **Ícone da Exibição de Dados** – selecionar esse ícone para inserir a Exibição de Dados.

2. **Grade de Dados** – mostra a tabela selecionada e todas as colunas e linhas presentes nela. As colunas ocultadas na **Exibição de Relatório** ficam esmaecidas. Clique duas vezes em uma coluna para as opções.

3. **Faixa de opções de modelagem** – aqui você pode gerenciar relações, criar cálculos e alterar o tipo de dados, o formato e a categoria de dados de uma coluna.

4. **Barra de fórmulas** – insira fórmulas DAX para medidas e colunas calculadas.

5. **Pesquisa** – pesquise uma tabela ou coluna no modelo.

6. **Lista de campos** – selecione uma tabela ou coluna a ser exibida na grade de dados.

## <a name="filtering-in-data-view"></a>Filtragem na Exibição de Dados

Você também pode filtrar e classificar dados na **Exibição de Dados**. Cada coluna mostra um ícone que identifica a direção de classificação (se aplicada).

![Classificar e filtrar na Exibição de Dados no Power BI Desktop](media/desktop-data-view/dataview_sort-and-filter.png)

Você pode filtrar valores individuais ou usar a filtragem avançada com base nos dados da coluna. 

> [!NOTE]
> Quando um modelo do Power BI é criado em uma cultura diferente do que a sua interface do usuário atual (por exemplo, o modelo foi criado em inglês dos EUA e você está visualizando-lo em espanhol), a caixa de pesquisa não é exibida na interface do usuário da Exibição de Dados para algo diferente de campos de texto.
