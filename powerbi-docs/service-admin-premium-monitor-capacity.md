---
title: Monitorar as capacidades do Power BI Premium em sua organização
description: Usar o portal de administração do Power BI e o aplicativo de Métricas de Capacidade do Power BI Premium
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 08/29/2018
LocalizationGroup: Premium
ms.openlocfilehash: 8e19bc596bef3862dca79ac92ffbd74954a9c756
ms.sourcegitcommit: 6be2c54f2703f307457360baef32aee16f338067
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43300151"
---
# <a name="monitor-power-bi-premium-capacities-in-your-organization"></a>Monitorar as capacidades do Power BI Premium em sua organização

Este artigo fornece uma visão geral do monitoramento de métricas para suas capacidades do Power BI Premium. O monitoramento do uso da capacidade permite que você adote uma abordagem embasada para gerenciar suas capacidades. 

Você pode monitorar a capacidade com o aplicativo de Métricas de Capacidade do Power BI Premium ou no portal de administração. É recomendável usar o aplicativo, pois ele fornece muito mais detalhes, mas este artigo aborda as duas opções.

## <a name="install-the-premium-capacity-metrics-app"></a>Instalar o aplicativo de Métricas de Capacidade Premium

Você pode ir diretamente para o [aplicativo de Métricas de Capacidade Premium](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) ou instalá-lo como faz com outros aplicativos no Power BI.

> [!IMPORTANT]
> Para instalar e usar este aplicativo, você deve ser um administrador de capacidade para pelo menos uma capacidade. Ser um administrador do Power BI não é suficiente. 

1. No Power BI, clique em **Aplicativos**.

    ![Ir para Aplicativos](media/service-admin-premium-monitor-capacity/apps.png)

2. No lado direito, clique em **Obter aplicativos**.

3. Na categoria **Aplicativos**, pesquise por **Aplicativo de Métricas de Capacidade do Power BI Premium**.

4. Inscreva-se para instalar o aplicativo.

Agora que você instalou o aplicativo, pode ver as métricas sobre as capacidades em sua organização. Vamos conferir algumas das principais métricas que estão disponíveis.

## <a name="use-the-metrics-app"></a>Usar o aplicativo de métricas 
Quando você abre o aplicativo, primeiro ele mostra um painel com um resumo de todas as capacidades para as quais você tem direitos de administrador.

![Visão geral do relatório Premium](media/service-admin-premium-monitor-capacity/app-dashboard.png)

### <a name="filtering"></a>Filtragem

A guia **Filtros aplicados a todas as páginas** permite que você selecione uma capacidade, um conjunto de dados e/ou um intervalo de datas nos últimos sete dias. Esses filtros aplicam a seleção a todas as páginas e blocos relevantes neste relatório. Se nada estiver selecionado, por padrão, o relatório mostrará métricas da semana passada de cada capacidade que você possui.

![Visão geral do relatório Premium](media/service-admin-premium-monitor-capacity/premium-report-overview.png)

### <a name="summary-tab"></a>Guia Resumo

A guia **Resumo** mostra uma exibição da capacidade com base em entidades, sistema e conjuntos de dados.

![Filtros que se aplicam a todas as páginas](media/service-admin-premium-monitor-capacity/premium-summary-report.png)

| **Área** | **Métricas** |
| --- | --- |
| **Entidades** | * O número das capacidades que você possui<br> * O número distinto de conjuntos de dados em sua capacidade<br> * O número distinto de espaços de trabalho em sua capacidade |
| **Sistema** | * O uso médio da memória em GB nos últimos sete dias<br> * Mais alto consumo de memória em GB nos últimos sete dias e a hora local em que ele ocorreu<br> * O número de vezes que a CPU excedeu 80% dos limites nos últimos sete dias, divididas em buckets de três minutos<br> * A maioria das vezes em que a CPU excedeu 80% nos últimos sete dias, divididas em buckets de uma hora e a hora local em que isso ocorreu<br> * O número de vezes que as conexões de Consulta direta/dinâmica excederam 80% dos limites nos últimos sete dias, divididas em buckets três minutos<br> * A maioria das vezes em que as conexões de Consulta direta/dinâmicas excederam 80% nos últimos sete dias, divididas em buckets de uma hora, e a hora local em que isso ocorreu |
| **Cargas de trabalho do conjunto de dados** | * Número total de atualizações nos últimos sete dias<br> * Número total de atualizações com êxito nos últimos sete dias<br> * Número total de atualizações com falha nos últimos sete dias<br> * Número total de atualizações com falha devido à falta de memória<br> * A duração média da atualização é medida em minutos, o tempo necessário para concluir a operação<br> * O tempo de espera médio da atualização é medido em minutos, a latência média entre o horário agendado e o início da operação<br> * Número total de consultas executadas nos últimos sete dias<br> * Número total de consultas com êxito nos últimos sete dias<br> * Número total de consultas com falha nos últimos sete dias<br> * A duração média da consulta é medida em minutos, o tempo necessário para concluir a operação<br> * Número total de modelos removidos devido à pressão da memória |
|  |  |

### <a name="refreshes-tab"></a>Atualiza a guia

A guia **Atualizações** listas as atualizações completas, as medidas de sucesso, o tempo de espera em média/máx. de atualização e a duração média/máx. de atualização dividida por conjuntos de dados nos últimos sete dias. Os dois gráficos na parte inferior mostram as atualizações versus o consumo de memória em GB e os tempos de espera médios divididos em buckets de uma hora, relatados no horário local. Os gráficos da barra superior listam os conjuntos de dados de cinco principais, o total de tempo máximo necessário para concluir a atualização do conjunto de dados (duração da atualização) e o tempo de espera máximo da atualização. Vários picos elevados de tempo de espera de atualização são uma indicação de que a capacidade de execução está sobrecarregada.

![Relatório de atualização Premium](media/service-admin-premium-monitor-capacity/premium-refresh-report.png)

### <a name="datasets-tab"></a>Guia Conjuntos de dados

A guia **Conjuntos de dados** mostra os conjuntos de dados completos removidos devido à pressão de memória por hora.

![Relatório de conjuntos de dados Premium](media/service-admin-premium-monitor-capacity/premium-datasets-report.png)

### <a name="system-tab"></a>Guia Sistema

A guia **Sistema** mostra a utilização elevada da CPU (número de vezes que excedeu 80% de utilização), alta utilização de conexões de Consulta Direta/Dinâmica e Consumo de Memória.

![Relatório do Sistema Premium](media/service-admin-premium-monitor-capacity/premium-system-report.png)

## <a name="monitor-power-bi-embedded-capacity"></a>Monitorar a capacidade do Power BI Embedded

Você também pode usar o aplicativo de Métricas de Capacidade do Power BI Premium para monitorar capacidades de *SKU A* no Power BI Embedded. Essas capacidades aparecerão no relatório contanto que você seja um administrador de capacidade. No entanto, a atualização do relatório falhará, a menos que você concede determinadas permissões ao Power BI sobre as SKUs A:

1. Abra a capacidade no portal do Azure.
1. Clique em **Controle de acesso (IAM)** e adicione o aplicativo "Power BI Premium" à função de leitor. Se não for possível encontrar o aplicativo por nome, você também poderá adicioná-lo pela Id do cliente: cb4dc29f-0bf4-402a-8b30-7511498ed654.

    ![Permissões para o Power BI Embedded](media/service-admin-premium-monitor-capacity/embedded-permissions.png)

> [!NOTE]
> Você pode monitorar a utilização da capacidade do Power BI Embedded no aplicativo ou no portal do Azure, mas não no portal de administração do Power BI.

## <a name="basic-monitoring-in-the-admin-portal"></a>Monitoramento básico no portal de administração

A área **Configurações de capacidade** do portal do administrador fornece quatro medidores que indicam as cargas adotadas e os recursos utilizados pela capacidade nos últimos sete dias. Esses quatro blocos funcionam em uma janela de tempo por hora que indica o número de horas nos últimos sete dias em que a métrica correspondente ficou acima de 80%. Essa métrica indica uma degradação potencial para a experiência do usuário final.

![Uso em sete dias](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **Métrica** | **Descrição** |
| --- | --- |
| CPU |O número de vezes que a CPU excedeu 80% de utilização. |
| Thrashing de memória |Representa a pressão de memória em seus núcleos de back-end. Especificamente, essa é uma métrica de quantas vezes os conjuntos de dados são removidos da memória devido à pressão de memória do uso de vários conjuntos de dados. |
| Uso de memória |Uso médio de memória, representado em gigabytes (GB). |
| DQ/s | Número de vezes em que a consulta direta e as conexões dinâmicas excederam 80% do limite. <br> * Limitamos o número total de consultas DirectQuery e de conexão dinâmica por segundo. * Os limites são 30/s para P1, 60/s para P2 e 120/s para P3. * A contagem de consultas diretas e de consultas de conexão somam-se à limitação acima. Por exemplo, se houver 15 DirectQueries e 15 conexões dinâmicas em um segundo, você atingirá a restrição<br>* Isso se aplica igualmente a conexões locais e de nuvem. |
|  |  |

As métricas refletem o uso na semana passada.  Se você quiser ver uma exibição mais detalhada das métricas, faça isso clicando em um dos blocos de resumo.  Você acessará gráficos detalhados para cada uma das métricas de capacidade Premium. O gráfico a seguir mostra os detalhes para a métrica da CPU.

![Gráfico detalhado de uso da CPU](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

Esses gráficos são resumidos por hora para a semana passada e podem ajudar a isolar quando eventos relacionados ao desempenho específicos que possam ter ocorrido na semana passada em sua capacidade premium.

Você também pode exportar os dados subjacentes de qualquer métrica para um arquivo csv.  Essa exportação fornecerá informações detalhadas em intervalos de três minutos para cada dia da semana passada.

## <a name="next-steps"></a>Próximas etapas

Agora que você entende como monitorar as capacidades do Power BI Premium, saiba mais sobre como otimizar as capacidades.

> [!div class="nextstepaction"]
> [Otimização e gerenciamento de recursos da capacidade do Power BI Premium](service-premium-understand-how-it-works.md)
