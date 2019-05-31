---
title: Usar o analisador de desempenho para examinar o desempenho do elemento de relatório no Power BI Desktop
description: Descubra como os elementos visuais e elementos de relatório são executados em termos de capacidade de resposta e o uso de recursos
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/15/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 1851e0a55bf01073a6591f64de43830a72eca89b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65854403"
---
# <a name="use-performance-analyzer-to-examine-report-element-performance"></a>Usar o analisador de desempenho para examinar o desempenho do elemento de relatório

Na **Power BI Desktop** encontre fora como cada um dos elementos do relatório, como elementos visuais e as fórmulas DAX, está o desempenho. Usando o **Performance Analyzer**, você pode ver e registro de logs que medir como cada um dos elementos do relatório executa quando os usuários interagem com eles, e quais aspectos do seu desempenho estão com uso intensivo de recursos de mais (ou menos).

![Analisador de desempenho](media/desktop-performance-analyzer/performance-analyzer-01.png)

Analisador de desempenho inspeciona e exibe durante o tempo necessário para a atualização ou atualização de todos os elementos visuais interações do usuário que iniciar e apresenta as informações para que você pode exibir, fazer uma busca detalhada ou exportar os resultados. Analisador de desempenho pode ajudar a identificar elementos visuais que estão afetando o desempenho de seus relatórios e identificar o motivo do impacto.

## <a name="displaying-the-performance-analyzer-pane"></a>Exibindo o painel do analisador de desempenho

Na **Power BI Desktop** selecionar a **exibição** faixa de opções. No **mostram** área da **exibição** faixa de opções que você pode selecionar a caixa de seleção ao lado de **Performance Analyzer** para exibir o painel do analisador de desempenho.

![Selecione o analisador de desempenho na faixa de opções de exibição](media/desktop-performance-analyzer/performance-analyzer-02.png)

Depois de selecionado, o analisador de desempenho é exibido no seu próprio painel, à direita da tela do relatório.

## <a name="using-performance-analyzer"></a>Usando o analisador de desempenho

Medidas de analisador de desempenho o tempo de processamento (incluindo o tempo para criar ou atualizar um visual) necessárias para atualizar os elementos de relatório iniciados como resultado de qualquer interação do usuário que resulta na execução de uma consulta. Por exemplo, ajustar uma segmentação de dados requer o visual de segmentação de dados a ser modificada, uma consulta a serem enviados para o modelo de dados e os visuais afetados que devem ser atualizados como resultado das novas configurações. 

Para que o analisador de desempenho começar a gravar, simplesmente selecione **iniciar a gravação**

![Iniciar gravação](media/desktop-performance-analyzer/performance-analyzer-03.png)

As ações tomadas no relatório são exibidas e registradas no painel de analisador de desempenho, na ordem em que o visual é carregado pelo Power BI. Por exemplo, talvez você tenha um relatório que os usuários disseram leva muito tempo para atualizar. Ou alguns visuais em um relatório de levar muito tempo para exibir quando um controle deslizante é ajustado. Analisador de desempenho pode informar a você qual visual é o culpado e identifica quais aspectos do visual está levando a duração mais longa para processar. 

Depois que você inicia a gravação, o **inicie a gravação** botão ficará esmaecido out (inativo, uma vez que você já tenha começado a gravação) e o **parar** botão está ativo. 

Analisador de desempenho coleta e exibe as informações de medição de desempenho em tempo real. Para que cada vez que você clicar em um visual, mover uma segmentação de dados ou interaja de qualquer maneira, o analisador de desempenho exibe imediatamente os resultados de desempenho no seu painel.

Se o painel tem mais informações que podem ser exibidos, uma barra de rolagem será exibida navegar para obter informações adicionais.

Cada interação tem um identificador de seção no painel, que descreve a ação que iniciou as entradas de log. Na imagem a seguir, a interação era que os usuários alteraram uma segmentação de dados.

![Seções com base no tipo de interação](media/desktop-performance-analyzer/performance-analyzer-04.png)

Informações de log do cada visual incluem o tempo gasto (duração) para concluir as seguintes categorias de tarefas:

* **Consulta DAX** -se uma consulta DAX era necessária, isso é o tempo entre o visual enviando a consulta e para o Analysis Services retornar os resultados.
* **Exibição visual** -tempo necessário para o visual desenhar na tela, incluindo o tempo necessário para recuperar todas as imagens da web ou geocodificação. 
* **Outros** -tempo necessário para o visual para consultas de preparação, aguardando outros elementos visuais concluir ou executar outros tipos de processamento em segundo plano.

![elementos de informações de log](media/desktop-performance-analyzer/performance-analyzer-06.png)

Depois que você já interagi com elementos do relatório que deseja medir com o analisador de desempenho, você pode selecionar o **parar** botão. As informações de desempenho permanecem no painel depois que você seleciona **parar** para analisar.

Para limpar as informações no painel do analisador de desempenho, selecione **limpar**. Todas as informações são apagadas e não é salvo quando você seleciona **clara**. Consulte a próxima seção para aprender a salvar informações nos logs. 

## <a name="refreshing-visuals"></a>Atualização de visuais

Você pode selecionar **Refresh visuais** no painel de analisador de desempenho para atualizar todos os visuais na página atual do relatório e, portanto, têm o analisador de desempenho coletar informações sobre todos esses visuais.

Você também pode atualizar elementos visuais individuais. Durante a gravação de analisador de desempenho, você pode selecionar **Refresh este visual** localizado no canto superior direito de cada visual, para atualizar esse visual e capturar suas informações de desempenho.

![atualizar um visual individual](media/desktop-performance-analyzer/performance-analyzer-07.png)

## <a name="saving-performance-information"></a>Salvando informações de desempenho

Você pode salvar as informações que cria o analisador de desempenho sobre um relatório selecionando o **exportar** botão. Selecionando **exportar** cria um arquivo. JSON com informações do painel de analisador de desempenho. 

![Salve o arquivo de log para o analisador de desempenho](media/desktop-performance-analyzer/performance-analyzer-05.png)


## <a name="next-steps"></a>Próximas etapas
Para obter mais informações sobre o **Power BI Desktop** e como começar, confira os artigos a seguir.

* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)
* [Visão geral de Consulta com o Power BI Desktop](desktop-query-overview.md)
* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Conectar-se a dados no Power BI Desktop](desktop-connect-to-data.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Tarefas comuns de consulta no Power BI Desktop](desktop-common-query-tasks.md)   

