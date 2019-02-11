---
title: Monitorar as capacidades do Power BI Premium por meio do portal de administração
description: Use o portal de administração do Power BI para monitorar suas capacidades Premium.
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: 59097c07719e4bb8db188e8a86db377076aea7a9
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794116"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Monitorar capacidades no portal de administração

Este artigo descreve como você pode usar a área de configurações de Capacidade no portal de administração para obter uma exibição rápida do desempenho da sua capacidade.  Para obter as métricas mais profundas sobre a sua capacidade, é melhor usar o aplicativo [Métricas de Capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md).

## <a name="capacity-metrics"></a>Métricas de capacidade

A área **Configurações de capacidade** do portal do administrador fornece quatro medidores que indicam as cargas adotadas e os recursos utilizados pela capacidade nos últimos sete dias. Esses quatro blocos funcionam em uma janela de tempo por hora que indica o número de horas nos últimos sete dias em que a métrica correspondente ficou acima de 80%. Essa métrica indica uma degradação potencial para a experiência do usuário final.

![Uso em sete dias](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **Métrica** | **Descrição** |
| --- | --- |
| CPU |O número de vezes que a CPU excedeu 80% de utilização. |
| Thrashing de memória |Representa a pressão de memória em seus núcleos de back-end. Especificamente, essa é uma métrica de quantas vezes os conjuntos de dados são removidos da memória devido à pressão de memória do uso de vários conjuntos de dados. |
| Uso de memória |Uso médio de memória, representado em gigabytes (GB). |
| DQ/s | Número de vezes em que a consulta direta e as conexões dinâmicas excederam 80% do limite. <br>  O número total de consultas DirectQuery e de conexão dinâmica por segundo é limitado. Os limites são 30/s para P1, 60/s para P2 e 120/s para P3.  A contagem de consultas diretas e de consultas de conexão somam-se à limitação acima. Por exemplo, se houver 15 DirectQueries e 15 conexões dinâmicas em um segundo, você atingirá a restrição<br> Isso se aplica igualmente a conexões locais e de nuvem. |
|  |  |

As métricas refletem o uso na semana passada.  Se você quiser ver uma exibição mais detalhada das métricas, faça isso clicando em um dos blocos de resumo.  Você acessará gráficos detalhados para cada uma das métricas de capacidade Premium. O gráfico a seguir mostra os detalhes para a métrica da CPU.

![Gráfico detalhado de uso da CPU](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

Esses gráficos são resumidos por hora para a semana passada e podem ajudar a isolar quando eventos relacionados ao desempenho específicos que possam ter ocorrido na semana passada em sua capacidade premium.

Você também pode exportar os dados subjacentes de qualquer métrica para um arquivo csv.  Essa exportação fornecerá informações detalhadas em intervalos de três minutos para cada dia da semana passada.

## <a name="next-steps"></a>Próximas etapas

Agora que você entende como monitorar as capacidades do Power BI Premium, saiba mais sobre como otimizar as capacidades.

> [!div class="nextstepaction"]
> [Otimização e gerenciamento de recursos da capacidade do Power BI Premium](service-premium-understand-how-it-works.md)
