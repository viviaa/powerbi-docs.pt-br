---
title: Conectar-se a arquivos CSV no Power BI Desktop
description: Conecte-se facilmente e use dados de arquivos CSV no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f1e02197f36da66a64fac95209fe8fabaa67b6c0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65514170"
---
# <a name="connect-to-csv-files-in-power-bi-desktop"></a>Conectar-se a arquivos CSV no Power BI Desktop
Conectar-se a um arquivo *CSV* (valor separado por vírgula) no Power BI Desktop é muito semelhante à conexão a uma pasta de trabalho do Excel. Ambos são fáceis, e este artigo explica como se conectar a qualquer arquivo CSV ao qual você tem acesso.

Para começar, no Power BI Desktop, selecione **Obter Dados > CSV** na faixa de opções **Página Inicial**.

![](media/desktop-connect-csv/connect-to-csv_1.png)

Selecione o arquivo CSV na caixa de diálogo **Abrir** exibida.

![](media/desktop-connect-csv/connect-to-csv_2.png)

Quando você seleciona **Abrir**, o Power BI Desktop acessa o arquivo e determina alguns atributos de arquivo, como a origem do arquivo, tipo de delimitador e quantas linhas devem ser usadas para detectar os tipo de dados no arquivo.

Esses atributos de arquivo e as opções são mostrados nas seleções suspensas na parte superior da janela da caixa de diálogo **Importação de CSV**, mostrada abaixo. Você pode alterar essas configurações detectadas manualmente, escolhendo outra opção em qualquer um dos seletores suspensos.

![](media/desktop-connect-csv/connect-to-csv_3.png)

Quando estiver satisfeito com as seleções, selecione **Carregar** para importar o arquivo no Power BI Desktop ou **Editar** para abrir o **Editor de Consultas** e formatar ou transformar ainda mais os dados antes de importá-los.

Depois de carregar os dados no Power BI Desktop, você vê a tabela e suas colunas (que são apresentadas como Campos no Power BI Desktop) no painel **Campos** à direita da exibição de Relatório no Power BI Desktop.

![](media/desktop-connect-csv/connect-to-csv_4.png)

Isso é tudo o que você precisa fazer – os dados de seu arquivo CSV agora estão no Power BI Desktop.

Você pode usar esses dados no Power BI Desktop para criar visuais, relatórios, ou para interagir com quaisquer outros dados aos quais você queira se conectar e importar, por exemplo, pastas de trabalho do Excel, bancos de dados ou qualquer outra fonte de dados.

## <a name="next-steps"></a>Próximas etapas
Há todos os tipos de dados aos quais você pode se conectar usando o Power BI Desktop. Para obter mais informações sobre fontes de dados, confira os seguintes recursos:

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Conectar-se a pastas de trabalho do Excel no Power BI Desktop](desktop-connect-excel.md)   
* [Inserir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

