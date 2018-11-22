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
ms.openlocfilehash: 0449d7953b5cefb4c76d89f05ec5b3fa70e9c0da
ms.sourcegitcommit: a739a99e1006834a0f56e387c0bd9d945fb8a76b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51679340"
---
# <a name="power-bi-premium-support-for-large-datasets"></a>Suporte ao Power BI Premium para grandes conjuntos de dados

O Power BI Premium dá suporte a carregamentos de arquivos do Power BI Desktop (.pbix) até 10 GB de tamanho. Uma vez carregado, um conjunto de dados pode ser atualizado para até 12 GB de tamanho. Para usar um conjunto de dados grande, publique-o em um workspace atribuído à capacidade Premium.
 
## <a name="best-practices"></a>Práticas recomendadas

Esta seção descreve as práticas recomendadas para trabalhar com grandes conjuntos de dados.

**Modelos grandes podem usar muitos recursos** em sua capacidade. Recomendamos pelo menos uma SKU P1 para modelos maiores que 1 GB. Embora a publicação de grandes modelos em workspaces com suporte de SKUs A até A3 talvez funcione, atualizá-los não funcionará.

A tabela a seguir descreve os SKUs recomendados para vários tamanhos .pbix:

   |SKU  |Tamanho de .pbix   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | até 10 GB   |

O SKU A4 do Power BI Embedded é igual ao SKU P1, o A5 = P2 e o A6 = P3. Observe que a publicação de grandes modelos em SKUs A e EM pode retornar erros que não são específicos para o erro de limitação de tamanho do modelo na capacidade compartilhada. Erros de atualização de modelos grandes em SKUs A e EM provavelmente são resultados de atingimento de tempos limite. Estamos trabalhando para melhorar as mensagens de erro para esses cenários.

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
