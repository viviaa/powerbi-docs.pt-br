---
title: Faça com que os dados do Excel funcionarem bem com p e r no Power BI
description: Como fazer os dados funcionarem bem com P e R no Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: 7ed8eb8e205c05582d2cfd93030ab056be77912a
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65624975"
---
# <a name="make-excel-data-work-well-with-qa-in-power-bi"></a>Faça com que os dados do Excel funcionarem bem com p e r no Power BI
Se você for uma pessoa que cria modelos de dados ou cria pastas de trabalho do Excel que serão usadas com o Power BI, continue lendo...

No Power BI, perguntas e respostas podem pesquisar dados estruturados e escolher a visualização certa para a pergunta, que é o que torna uma ferramenta interessante para uso.   

A P e R pode trabalhar em qualquer arquivo Excel carregado que tem tabelas, intervalos ou que contém um modelo do PowerPivot, porém, quanto mais otimizações e limpeza de dados você fizer, mais robusto será o desempenho da P e R.  Se você planeja compartilhar relatórios e dashboards com base em seu conjunto de dados, você vai querer facilitar para que seus colegas façam perguntas e obtenham respostas de qualidade.

## <a name="how-qa-works-with-excel"></a>Como a P e R funciona com o Excel
Perguntas e respostas tem um conjunto de habilidades de compreensão de linguagem natural principal que funcionam em seus dados. Possui a pesquisa de palavra-chave dependente de contexto para sua tabela, coluna e nomes de campos calculados do Excel. Esse recurso também tem conhecimento interno sobre como filtrar, classificar, agregar, agrupar e exibir dados. 

Por exemplo, em uma tabela do Excel com o nome "Vendas", com colunas "Produto", "Mês", "Unidades vendidas", "Vendas brutas" e "Lucro", você pode fazer perguntas sobre qualquer uma dessas entidades.  Você pode pedir para mostrar as vendas, ganho total por mês, classificar os produtos por unidades vendidas e muitas outras opções. Leia mais sobre [usando p e r em painéis e relatórios](power-bi-tutorial-q-and-a.md), e [tipos de visualização que você pode especificar em uma consulta de p e r](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md).

## <a name="prepare-an-excel-dataset-for-qa"></a>Preparar um conjunto de dados do Excel para P e R
Perguntas e respostas baseia-se nos nomes das tabelas, colunas e campos calculados para responder a perguntas específicas de dados, o que significa que você chamar as entidades na pasta de trabalho é importante!

Aqui estão algumas dicas para aproveitar ao máximo de perguntas e respostas em sua pasta de trabalho.

* Verifique se os dados estão em uma tabela do Excel. Veja [como criar uma tabela do Excel](https://support.office.com/article/Create-an-Excel-table-in-a-worksheet-e81aa349-b006-4f8a-9806-5af9df0ac664).
* Verifique se os nomes das tabelas, das colunas e dos campos calculados fazem sentido em fala natural.
  
  Por exemplo, se você tiver uma tabela com dados de vendas, colo que o nome da tabela de "Vendas". Nomes de coluna como "Ano", "Produto", "Representante de vendas" e "Valor" funcionaram bem com perguntas e respostas.

* Se sua pasta de trabalho tiver um modelo de dados do Power Pivot, você poderá fazer ainda mais otimizações. Leia mais em [Desmistificando a P e R do Power BI, parte 2](http://blogs.msdn.com/b/powerbi/archive/2014/02/27/demystifying-power-bi-q-amp-a-part-2.aspx) de nossa equipe interna de especialistas em linguagem natural.

* Abra o conjunto de dados no Power BI Desktop e crie novas colunas, crie medidas calculadas, concatene campos para criar valores exclusivos, classifique dados por tipo (por exemplo, datas, cadeias de caracteres, geografia, imagens, URLs) e muito mais.

## <a name="next-steps"></a>Próximas etapas

- [P e r para consumidores](consumer/end-user-q-and-a.md)  
- [Usar p e r em painéis e relatórios](power-bi-tutorial-q-and-a.md)
- [Preparar os conjuntos de dados local para p e r](service-q-and-a-direct-query.md)   
- [Obter dados (para o Power BI)](service-get-data.md)  

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

