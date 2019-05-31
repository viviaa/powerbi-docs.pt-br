---
title: Monitorar as capacidades do Power BI Premium por meio do portal de administração
description: Use o portal de administração do Power BI para monitorar suas capacidades Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
LocalizationGroup: Premium
ms.openlocfilehash: 36b03a67e7c02702a70b6486880cc8eabf93e823
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65564889"
---
# <a name="monitor-capacities-in-the-admin-portal"></a>Monitorar capacidades no portal de administração

O **integridade** guia o **configurações de capacidade** área no portal de administração fornece métricas de resumo sobre suas cargas de trabalho de capacidade e habilitadas.  

![Guia de integridade de capacidade no portal](media/service-admin-premium-monitor-portal/admin-portal-health.png)

Se você precisar métricas mais abrangentes, use o [métricas de capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md) aplicativo. O aplicativo fornece o drill-down e filtragem, e as métricas mais detalhadas para quase todos os aspectos que afetam o desempenho de capacidade. Para obter mais informações, consulte [capacidades Premium de Monitor com o aplicativo](service-admin-premium-monitor-capacity.md).

## <a name="system-metrics"></a>Métricas do sistema

Sobre o **integridade** o nível mais alto, guia de utilização da CPU e uso de memória fornecem uma visão rápida das métricas mais importantes para a capacidade. Essas métricas são cumulativas, incluindo todos habilitados pela capacidade de cargas de trabalho.

| **Métrica** | **Descrição** |
| --- | --- |
| UTILIZAÇÃO DA CPU | Utilização média da CPU, como uma porcentagem de CPU total disponível. |
| USO DE MEMÓRIA | Média de utilização de memória em gigabytes (GB).|

## <a name="workload-metrics"></a>Métricas de carga de trabalho

Para cada carga de trabalho habilitada para a capacidade. Utilização da CPU e uso de memória são mostrados.

| **Métrica** | **Descrição** |
| --- | --- |
| UTILIZAÇÃO DA CPU | Utilização média da CPU, como uma porcentagem de CPU total disponível. |
| USO DE MEMÓRIA | Média de utilização de memória em gigabytes (GB).|

### <a name="detailed-workload-metrics"></a>Métricas de carga de trabalho detalhados

Cada carga de trabalho tem métricas adicionais. O tipo das métricas mostradas dependem da carga de trabalho. Para ver as métricas detalhadas para uma carga de trabalho, clique em Expandir (seta para baixo).

![Expanda de integridade da carga de trabalho](media/service-admin-premium-monitor-portal/admin-portal-health-expand.png)

#### <a name="dataflows"></a>Fluxos de dados

##### <a name="dataflow-operations"></a>Operações de fluxo de dados

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem total | o total é atualizado para cada fluxo de dados. |
| Contagem de Êxito | Total de bem-sucedida é atualizada para cada fluxo de dados.|
| Duração média (min) | a duração média da atualização para o fluxo de dados, em minutos |
| Duração máxima (min) | a duração da atualização de execução mais longa para o fluxo de dados, em minutos. |
| Tempo médio de espera (min) | a latência média entre o horário agendado e o início de uma atualização para o fluxo de dados, em minutos. |
| Tempo máximo de espera (min) | o tempo de espera máximo para o fluxo de dados, em minutos.  |

#### <a name="datasets"></a>Conjuntos de dados

##### <a name="refresh"></a>Atualizar

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem total | o total é atualizado para cada conjunto de dados. |
| Contagem de Êxito | Total de bem-sucedida é atualizada para cada conjunto de dados. |
| Contagem de Falha | Total de atualizações com falha para cada conjunto de dados. |
| Taxa de sucesso  | Número de atualizações bem-sucedidas dividido pelas atualizações para medir as total. Confiabilidade. |
| Duração média (min) | a duração média da atualização para o conjunto de dados, em minutos.  |
| Duração máxima (min) | a duração da atualização de execução mais longa para o conjunto de dados, em minutos. |
| Tempo médio de espera (min) | a latência média entre o horário agendado e o início de uma atualização para o conjunto de dados, em minutos. |
| Tempo máximo de espera (min) | o tempo de espera máximo para o conjunto de dados, em minutos. |

##### <a name="query"></a>Consulta

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem total | o número total de consultas executadas para o conjunto de dados. |
| Duração Média (ms) |a duração média de consulta do conjunto de dados, em milissegundos|
| Duração máxima (ms) |a duração da consulta de execução mais longa no conjunto de dados, em milissegundos. |
| Tempo de Espera Médio (ms) |o tempo médio de espera da consulta para o conjunto de dados, em milissegundos. |
| Tempo máximo de espera (ms) |a duração da consulta de espera mais longa no conjunto de dados, em milissegundos. |

##### <a name="eviction"></a>Remoção

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem de modelo | O número total de remoções de conjunto de dados para essa capacidade. Quando uma capacidade enfrenta a pressão de memória, o nó remove um ou mais conjuntos de dados da memória. Conjuntos de dados que estão inativos (sem nenhuma operação de atualização/consulta em execução no momento) são removidos primeiro. Em seguida, a ordem de remoção se baseia em uma medida de LRU (“menos utilizado recentemente”). |

#### <a name="paginated-reports"></a>Relatórios paginados

##### <a name="report-execution"></a>Execução de relatório

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem de execução  | O número de vezes que o relatório foi foram executado e exibidos pelos usuários.|

##### <a name="report-usage"></a>Uso de relatórios

| **Métrica** | **Descrição** |
| --- | --- |
| Contagem de Êxito | O número de vezes que o relatório foi exibido por um usuário. |
| Contagem de Falha |O número de vezes que o relatório foi exibido por um usuário.|
| Contagem de linhas |o número de linhas de dados no relatório. |
| Duração da recuperação de dados (ms) |a quantidade média de tempo que leva para recuperar dados para o relatório, em milissegundos. Durações longas podem indicar consultas lentas ou outros problemas de fonte de dados.  |
| Duração do processamento (ms) |a quantidade média de tempo que leva para processar os dados para um relatório, em milissegundos. |
| Duração de renderização (ms) |a quantidade média de tempo necessária para renderizar um relatório no navegador, em milissegundos. |

> [!NOTE]
> Detalhado de métricas para o **AI** carga de trabalho ainda não estão disponíveis.

## <a name="next-steps"></a>Próximas etapas

Agora que você entende como monitorar as capacidades do Power BI Premium, saiba mais sobre como otimizar as capacidades.

> [!div class="nextstepaction"]
> [Otimizando as capacidades do Power BI Premium](service-premium-capacity-optimize.md)
