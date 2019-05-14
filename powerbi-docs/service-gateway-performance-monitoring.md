---
title: Desempenho do gateway de monitoramento (visualização pública)
description: Este artigo fornece informações sobre como monitorar o desempenho das atividades de gateway de dados local.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 05/08/2019
LocalizationGroup: Gateways
ms.openlocfilehash: 8c5f4170383f31ea465ebb7035aebfb53f551982
ms.sourcegitcommit: af2b2238fe77eaa1b2392a19a143a0250b8665cf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/11/2019
ms.locfileid: "65535357"
---
# <a name="gateway-performance-monitoring-public-preview"></a>Desempenho do gateway de monitoramento (visualização pública)

Para monitorar o desempenho, os administradores de gateway têm tradicionalmente dependentes manualmente monitorar contadores de desempenho por meio da ferramenta Monitor de desempenho do Windows. Agora oferecemos o registro em log de consulta adicionais e uma [arquivo de modelo de Gateway desempenho PBI](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) para visualizar os resultados. Esse recurso fornece novas informações sobre o uso do gateway e permite que você solucionar problemas de desempenho de consultas lenta.

> [!NOTE]
> Esse recurso está atualmente disponível apenas para o gateway de dados locais no modo padrão e não para o modo pessoal.

## <a name="enable-performance-logging"></a>Habilitar o log de desempenho

Para habilitar esse recurso, faça as seguintes alterações para o *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config* arquivo o "\Program Files\On-gateway de dados local" pasta:

1. Atualização **QueryExecutionReportOn** à _verdadeiro_ para habilitar o registro em log adicional para consultas executadas usando o gateway. Habilitar essa opção cria o relatório de execução de consulta e os arquivos de relatório de agregação de execução de consulta.

   ``` xml
   <setting name="QueryExecutionReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Atualização **SystemCounterReportOn** à _verdadeiro_ para habilitar o registro em log adicional para a memória e contadores de CPU do sistema. Habilitar essa opção cria o arquivo de relatório de agregação de contador do sistema.

   ```xml
   <setting name="SystemCounterReportOn" serializeAs="String">
     <value>True</value>
   </setting>
   ```

1. Há outros valores no arquivo de configuração que você pode atualizar conforme necessário.

    - **ReportFilePath**: Determina o caminho onde os três arquivos de log são armazenados. Por padrão, esse caminho é "\Users\PBIEgwService\AppData\Local\Microsoft\On-premises dados gateway\Report" ou "local Windows\ServiceProfiles\PBIEgwService\AppData\Local\Microsoft\On dados gateway\Report", dependendo da versão do sistema operacional. Se você usar uma conta de serviço para o gateway diferente de _PBIEgwService_, substitua essa parte do caminho com o nome da conta de serviço.
    - **ReportFileCount**: Determina o número de arquivos de log de cada tipo para manter. O valor padrão é 10.
    - **ReportFileSizeInBytes**: Determina o tamanho do arquivo para manter. O valor padrão é 104857600.
    - **QuerExecutionAggregationTimeInMinutes**: Determina o número de minutos para o qual as informações de execução de consulta são agregadas. O valor padrão é 5.
    - **SystemCounterAggregationTimeInMinutes**: Determina o número de minutos para o qual os contadores do sistema são agregados. O valor padrão é 5.

1. Depois que você fez as alterações ao arquivo de configuração, reinicie o gateway para obter esses valores de configuração entrem em vigor. Você agora começará a ver os arquivos de relatório que está sendo gerados no local especificado para **ReportFilePath**.

    > [!NOTE]
    > Pode levar até 10 minutos e a quantidade de tempo definido para **QuerExecutionAggregationTimeInMinutes** no arquivo de configuração até que arquivos comecem a aparecer na pasta.

## <a name="understand-performance-logs"></a>Compreender os logs de desempenho

Quando você ativa esse recurso, podemos criar três novos arquivos de log:

- O relatório de execução de consulta
- O relatório de agregação de execução de consulta
- O relatório de agregação de contador do sistema

O relatório de execução de consulta contém informações de execução de consulta detalhados. Podemos capturar os seguintes atributos:

|Atributo |Descrição |
| ---- | ---- |
|**GatewayObjectId** |Identificador exclusivo para o gateway. |
|**RequestId** |Identificador exclusivo para uma solicitação de gateway. Ele pode ser o mesmo para várias consultas. |
|**DataSource** |Contém o tipo de fonte de dados e a fonte de dados. |
|**QueryTrackingId** |Identificador exclusivo para uma consulta. |  
|**QueryExecutionEndTimeUTC** |Hora de quando a execução da consulta é concluída. |
|**QueryExecutionDuration**(ms) |Duração de uma execução de consulta. |
|**QueryType** |Tipo de consulta - por exemplo, a consulta passada poderia ser um atualização/DirectQuery do Power BI ou consultas do PowerApps e Microsoft Flow. |
|**DataProcessingEndTimeUTC** |Hora de quando as atividades de processamento de dados, como spool, recuperação de dados, compactação, processamento de dados e assim por diante concluída. |
|**DataProcessingDuration**(ms) |Duração para atividades de processamento de dados, como o spool, recuperação de dados, compactação, processamento de dados e assim por diante. |
|**Sucesso** |Indica se a consulta foi bem-sucedida ou falhou. |
|**ErrorMessage** |Se a consulta falhou, indica a mensagem de erro. |
| | |

O relatório de agregação de execução de consulta contém informações de consulta agregadas em um intervalo de tempo por **GatewayObjectId**, **DataSource**, **sucesso**e **QueryType**. O valor padrão é 5 minutos, mas você pode ajustá-lo conforme descrito abaixo. Podemos capturar os seguintes atributos:

|Atributo |Descrição |
| ---- | ---- |
|**GatewayObjectId** |Identificador exclusivo para o gateway. |
|**AggregationStartTimeUTC** |Início da janela de tempo para o qual consultar os atributos foram agregados. |
|**AggregationEndTimeUTC** |Fim da janela de tempo para o qual consulta os atributos foram agregados. |
|**DataSource** |Contém o tipo de fonte de dados e a fonte de dados. |
|**Sucesso** |Indica se a consulta foi bem-sucedida ou falhou. |
|**AverageQueryExecutionDuration**(ms) |Média de tempo de execução de consulta para a janela de tempo de agregação. |
|**MaxQueryExecutionDuration**(ms) |Tempo de execução de consulta máxima para a janela de tempo de agregação. |
|**MinQueryExecutionDuration**(ms) |Tempo de execução da consulta mínimo para a janela de tempo de agregação. |
|**QueryType** |Tipo de consulta - por exemplo, a consulta passada poderia ser um atualização/DirectQuery do Power BI ou consultas do PowerApps e Microsoft Flow. |
|**AverageDataProcessingDuration**(ms) |Tempo médio para atividades de processamento de dados, como o spool, recuperação de dados, compactação, processamento de dados, e assim por diante para a janela de tempo de agregação. |
|**MaxDataProcessingDuration**(ms) |Tempo máximo para a janela de tempo de agregação para atividades de processamento de dados, como o spool, recuperação de dados, compactação, processamento de dados e assim por diante. |
|**MinDataProcessingDuration**(ms) |Tempo mínimo para a janela de tempo de agregação para atividades de processamento de dados, como o spool, recuperação de dados, compactação, processamento de dados e assim por diante. |
|**Contagem** |Número de consultas. |
| | |

O relatório de agregação de contador do sistema contém valores de contador de sistema agregados em um intervalo de tempo. O valor padrão é 5 minutos, mas você pode ajustá-lo conforme descrito abaixo. Podemos capturar os seguintes atributos:

|Atributo |Descrição |
| ---- | ---- |
|**GatewayObjectId** |Identificador exclusivo para o gateway. |
|**AggregationStartTimeUTC** |Início da janela de tempo para o qual os contadores do sistema foram agregados. |
|**AggregationEndTimeUTC** |Fim da janela de tempo para o sistema no qual os contadores foram agregados. |
|**CounterName** |Contadores do sistema, incluindo o uso da memória e CPU pelo gateway, efetuar mashup e geral por computador hospeda o gateway. |
|**Max** |Valor máximo para o contador de sistema para a janela de tempo de agregação. |
|**Min** |Valor mínimo para o contador de sistema para a janela de tempo de agregação. |
|**Média** |Valor médio do contador de sistema para a janela de tempo de agregação. |
| | |

## <a name="visualize-gateway-performance"></a>Visualize o desempenho do gateway

Agora, você pode visualizar os dados que estão nos arquivos de log.

1. Baixe o [modelo de Gateway desempenho PBI](http://download.microsoft.com/download/D/A/1/DA1FDDB8-6DA8-4F50-B4D0-18019591E182/GatewayPerformanceMonitoring.pbit) e abra-o usando o Power BI desktop.

1. Na caixa de diálogo que é aberta, verifique se o caminho da pasta corresponde ao valor na **ReportFilePath**.

    ![Pop-up para o caminho da pasta](media/service-gateway-performance-monitoring/gateway-folder-path-pop-up.png)

1. Selecione **carga**, e o arquivo de modelo começa a carregar os dados de seus arquivos de log. Todos os elementos visuais, em seguida, devem ser preenchidos usando os dados nos relatórios.

1. Opcionalmente, salvar esse arquivo como um PBIX e publicá-lo em seu serviço para atualizações automáticas.

Além disso, você pode personalizar esse arquivo de modelo para atender às suas necessidades. Para obter mais informações sobre modelos do Power BI, consulte este [postagem de Blog do Microsoft Power BI](https://powerbi.microsoft.com/en-us/blog/deep-dive-into-query-parameters-and-power-bi-templates/).