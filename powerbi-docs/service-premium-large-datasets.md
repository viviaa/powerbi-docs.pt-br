---
title: Suporte ao Power BI Premium para grandes conjuntos de dados
description: Agora, o Power BI Premium dá suporte a conjuntos de dados de até 10 GB.
author: jocaplan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/18/2018
ms.author: jocaplan
LocalizationGroup: Premium
ms.openlocfilehash: 416f022ee3c413c69650e6f1736cc94edcd58f13
ms.sourcegitcommit: a764e4b9d06b50d9b6173d0fbb7555e3babe6351
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2018
ms.locfileid: "49641242"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Suporte ao Power BI Premium para grandes conjuntos de dados

O Power BI Premium dá suporte a carregamentos de arquivos do Power BI Desktop (.pbix) até 10 GB de tamanho. Uma vez carregado, um conjunto de dados pode ser atualizado para até 12 GB de tamanho. Para usar um conjunto de dados grande, publique-o em um workspace atribuído à capacidade Premium. Este artigo descreve as considerações e práticas recomendadas para trabalhar com grandes conjuntos de dados.

**Modelos grandes podem usar muitos recursos** em sua capacidade. Recomendamos pelo menos uma SKU P1 para modelos maiores que 1 GB. A tabela a seguir descreve os SKUs recomendados para vários tamanhos .pbix:

   |SKU  |Tamanho de .pbix   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | até 10 GB |

**Os arquivos .pbix representam dados em um estado altamente compactado**. Os dados provavelmente expandirão várias vezes quando carregados na memória e, a partir daí, eles podem expandir várias vezes mais durante a atualização de dados.

**A atualização agendada de grandes conjuntos de dados pode demorar muito tempo** e usar muitos recursos. Da mesma forma, não agende muitas atualizações sobrepostas. Observe também que o tempo limite para trabalhos de atualização agendada foi duplicado para quatro horas para todos os conjuntos de dados nesta capacidade. Recomendamos [atualização incremental](service-premium-incremental-refresh.md), pois é mais rápida e confiável e consome menos recursos.

**A carga inicial do relatório de grandes conjuntos de dados pode demorar muito tempo** se um período já transcorreu desde a última vez em que o conjunto de dados foi usado, porque o modelo foi carregado na memória da capacidade Premium. Uma barra de carregamento para relatórios demorados exibe o progresso do carregamento.

**Se você remover o workspace da capacidade Premium**, o modelo e todos os relatórios e painéis associados não funcionarão.

**Embora as restrições de tempo e memória por consulta sejam muito maiores na capacidade Premium**, é altamente recomendável usar filtros e segmentações de dados para limitar os visuais para exibir apenas o que é necessário.

**Próximas etapas**

[O que é o Power BI Premium?](service-premium.md)
[Notas de versão do Power BI Premium](service-premium-release-notes.md)
[White paper do Microsoft Power BI Premium](https://aka.ms/pbipremiumwhitepaper)
[White paper sobre como planejar uma implantação do Power BI Enterprise](https://aka.ms/pbienterprisedeploy)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)
