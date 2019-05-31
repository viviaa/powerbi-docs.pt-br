---
title: Cenários de capacidade do Microsoft Power BI Premium
description: Descreve cenários comuns de capacidade do Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 1d666a6702515a935d93549d026f207848f2bca8
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565344"
---
# <a name="premium-capacity-scenarios"></a>Cenários de capacidade Premium

Este artigo descreve os cenários do mundo real em que as capacidades do Power BI premium foram implementadas. Os problemas e desafios comuns são descritos, também como identificar problemas e ajudar a resolvê-los:

- [Manter conjuntos de dados atualizados](#keeping-datasets-up-to-date)
- [Identificando conjuntos de dados de resposta lenta](#identifying-slow-responding-datasets)
- [Identificando as causas para lento-respondendo esporadicamente conjuntos de dados](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Determinando se há memória suficiente](#determining-whether-there-is-enough-memory)
- [Determinando se há suficiente CPU](#determining-whether-there-is-enough-cpu)

As etapas, junto com exemplos de gráfico e tabela são do **aplicativo de métricas de capacidade do Power BI Premium** que um administrador do Power BI terá acesso ao.

## <a name="keeping-datasets-up-to-date"></a>Manter conjuntos de dados atualizados

Nesse cenário, uma investigação foi acionada quando os usuários reclamam que dados de relatório, às vezes, parecem ser antigos ou "obsoletas".

No aplicativo, o administrador interage com o **atualiza** visual, classificando conjuntos de dados, o **de tempo de espera máximo** estatísticas em ordem decrescente. Este visual ajuda a revelar os conjuntos de dados com os tempos de espera mais longas, agrupados por nome do espaço de trabalho.

![Atualizações de conjunto de dados classificadas por em ordem decrescente de tempo de espera máximo, agrupado por espaço de trabalho](media/service-premium-capacity-scenarios/dataset-refreshes.png)

No **por hora de atualização esperar tempos médios** visual, eles Observe que os tempos de espera de atualização consistentemente pico aproximadamente 16 horas por dia.

![Atualização de esperas de pico periodicamente às 16H](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Há várias possíveis explicações para esses resultados:

- Muitas tentativas de atualização podem estar ocorrendo ao mesmo tempo, excedendo os limites definidos pelo nó de capacidade. Nesse caso, seis atualizações simultâneas em um P1 com alocação de memória padrão.

- Conjuntos de dados a ser atualizado podem ser muito grandes para caber na memória disponível (que exige pelo menos 2 vezes a memória necessária para atualização completa).
- Lógica ineficiente do Power Query pode ser resultando em um pico de uso de memória durante a atualização de conjunto de dados. Em uma capacidade de ocupado, esse pico ocasionalmente pode alcançar o limite físico, fazendo a atualização e potencialmente afetar outras operações do modo de exibição de relatório na capacidade.
- Conjuntos de dados consultados com frequência que precisam para ficar na memória podem afetar a capacidade de outros conjuntos de dados de atualização devido a memória disponível limitada.

Para ajudar a investigar, o administrador do Power BI pode procurar por:

- Memória insuficiente disponível no momento da data será atualizada quando a memória disponível for menor que 2 vezes o tamanho do conjunto de dados a ser atualizado.
- Conjuntos de dados não estão sendo atualizados e não na memória antes de atualizar, começou a mostrar o tráfego interativo durante tempos de atualização pesadas. Para ver quais conjuntos de dados são carregados na memória em um determinado momento, um administrador do Power BI pode examinar a área de conjuntos de dados do **conjuntos de dados** guia no aplicativo. O administrador pode cruzar o filtro para um determinado momento clicando em uma das barras em, em seguida, o **conjunto de dados por hora carregados, contagens**. Um aumento de local, mostrado na imagem abaixo, indica uma hora quando vários conjuntos de dados foram carregados na memória, o que pode atrasar o início de atualizações agendadas.
- Remoções de conjunto de dados maior tomando colocar quando as atualizações de dados estão agendadas para iniciar. Remoções podem indicar lá foi alta pressão de memória causado por que atende a muitos relatórios interativos diferentes antes do tempo de atualização. O **remoções de conjunto de dados por hora e o consumo de memória** visual pode indicar claramente os picos de remoções.

A imagem a seguir mostra um pico de local em conjuntos de dados carregados, que sugere a consulta interativa atraso no início de atualizações. Selecionar um período de tempo na **conjunto de dados por hora carregados, contagens** visual cruzar o filtro a **tamanhos de conjunto de dados** visual.

![Um aumento de local em conjuntos de dados carregados sugere interativo início atrasado consultando de atualizações](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

O administrador do Power BI pode tentar resolver o problema executando as etapas para garantir que a memória suficiente está disponível para as atualizações de dados iniciar por:

- Entrando em contato com o conjunto de dados proprietários e solicitando a escalonar e os dados de espaço agendas de atualização.
- Reduzindo o conjunto de dados de carga da consulta removendo painéis desnecessários ou painel blocos, especialmente aquelas que impor segurança em nível de linha.
- Acelerando as atualizações de dados, otimizando a lógica de consulta de energia. Melhore a modelagem de colunas calculadas ou tabelas. Reduzir os tamanhos de conjunto de dados ou configurar grandes conjuntos de dados para executar a atualização de dados incrementais.

## <a name="identifying-slow-responding-datasets"></a>Identificando conjuntos de dados de resposta lenta

Nesse cenário, uma investigação começou quando os usuários reclamam que certos relatórios demorou muito para abrir e às vezes poderia ser interrompido.

No aplicativo, o administrador do Power BI pode usar o **durações de consulta** visual para determinar os conjuntos de dados de pior desempenho por meio de conjuntos de dados de classificação decrescente **duração média**. Este visual também mostra dataset contagens de consulta, para que você possa ver a frequência com que os conjuntos de dados são consultados.

![Conjuntos de dados de pior desempenho](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

O administrador pode se referir à **distribuição de duração da consulta** visual, que mostra uma distribuição geral de desempenho da consulta em bucket (< = 30ms, 100ms 0) para o período de tempo filtrado. Em geral, as consultas que usam um segundo ou menos são consideradas responsiva pela maioria dos usuários; consultas que demoram mais tendem a criar uma percepção de mau desempenho.

O **distribuição de duração de consulta por hora** visual permite que o administrador do Power BI identificar períodos de uma hora quando o desempenho de capacidade poderia ter sido percebido como insatisfatórios. Quanto maior a barra de segmentos que consultam representam durações em um segundo, o maior o risco de que os usuários passarão a baixo desempenho.

O visual é interativo e quando um segmento da barra for selecionado, o correspondente **durações de consulta** visual na página do relatório de tabela é um filtro para mostrar os conjuntos de dados que ele representa. A filtragem cruzada permite ao administrador do Power BI identificar facilmente quais conjuntos de dados estão respondendo lentamente.

A imagem a seguir mostra um visual filtrado por **distribuições por hora de duração da consulta**, com foco nos conjuntos de dados pior desempenho nos buckets de uma hora. 

![Filtrado por hora consulta duração distribuições visual mostra a pior executar conjuntos de dados](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Depois que o conjunto de dados de desempenho ruim em um período de tempo de uma hora específica é identificado, o administrador do Power BI pode investigar se um desempenho ruim é causado por uma capacidade sobrecarregada ou devido a um mal projetado o conjunto de dados ou relatório. Eles podem consultar o **tempos de espera de consulta** visual e conjuntos de dados de classificação decrescente, de tempo de espera médio de consulta. Se estiver esperando um grande percentual de consultas, uma alta demanda para o conjunto de dados provavelmente é a causa de muitas esperas de consulta. Se a consulta de média de tempo de espera é significativa (> 100 ms), pode ser que vale a pena examinar o conjunto de dados e o relatório para ver se as otimizações podem ser feitas. Por exemplo, menos elementos visuais na considerando as páginas do relatório ou uma otimização de expressão DAX.

![O visual de tempos de espera de consulta ajuda a revelar insatisfatório conjuntos de dados](media/service-premium-capacity-scenarios/query-wait-times.png)

Há vários motivos possíveis para o acúmulo de tempo de espera de consulta em conjuntos de dados:

- Um design de modelo abaixo do ideal, expressões de medida ou design de relatório até mesmo - todas as circunstâncias que podem contribuir para consultas que consomem altos níveis de CPU de longa execução. Isso força a novas consultas para aguardar até que os threads de CPU se tornarem disponíveis e podem criar um efeito de comboio (congestionamento no tráfego raciocínio), geralmente visto durante o horário comercial de pico. O **esperas de consulta** página poderá ser o principal recurso para determinar se os conjuntos de dados têm tempos de espera médio de consulta altas.
- Um grande número de usuários simultâneos de capacidade (centenas a milhares) consumindo o mesmo relatório ou conjunto de dados. Conjuntos de dados até mesmo bem projetados podem executar mal exceder um limite de simultaneidade. Isso geralmente é indicado por um único conjunto de dados mostrando um valor de drasticamente mais alto para a consulta a conta que mostrar outros conjuntos de dados (por exemplo, consultas de 300 K for comparada com um conjunto de dados < 30 mil consultas para todos os outros conjuntos de dados). Em algum ponto, as esperas de consulta para esse conjunto de dados será iniciado escalonar, que pode ser visto na **durações de consulta** visual.
- Muitos diferentes conjuntos de dados consultados ao mesmo tempo, causando ultrapaginação como conjuntos de dados com frequência ciclo dentro e fora de memória. Isso resulta em usuários que estão tendo lentidão no desempenho quando o conjunto de dados é carregado na memória. Para confirmar, o administrador do Power BI pode se referir a **remoções de conjunto de dados por hora e o consumo de memória** visual, que pode indicar que um grande número de conjuntos de dados carregados na memória está sendo removido repetidamente.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identificando as causas para lento-respondendo esporadicamente conjuntos de dados

Nesse cenário, uma investigação começou quando usuários descrito visuais do relatório foram responde lentamente às vezes, ou pode parar de responder, mas em outros momentos eram aceitável responsivos.

Dentro do aplicativo, o **durações de consulta** seção foi usada para localizar o conjunto de dados culpado da seguinte maneira:

- No **durações de consulta** visual o administrador filtrado de conjunto de dados pelo conjunto de dados (começando às principais conjuntos de dados consultados) e examinado cruzadas filtradas barras o **distribuições por hora de consulta** visual.
- Quando uma única barra de uma hora mostrou alterações significativas na taxa entre todos os grupos de duração de consulta vs. outras barras de uma hora para esse conjunto de dados (por exemplo, as taxas entre as cores altera drasticamente), isso significa que esse conjunto de dados demonstrou uma alteração de esporádica no desempenho.
- As barras de uma hora que mostra uma parte de irregular de baixo desempenho de consultas, indicado um intervalo de tempo em que esse conjunto de dados foi afetado por um efeito de vizinho barulhento, causado por atividades de outros conjuntos de dados.

A imagem abaixo mostra uma hora em 30 de janeiro, onde um obstáculo significativo no desempenho de um conjunto de dados ocorreu, indicado pelo tamanho do "(3,10s]"execução duração bucket. Clicando em uma hora barra revela uma todos os conjuntos de dados carregados na memória durante esse tempo, identificando possíveis conjuntos de dados, fazendo com que o efeito de vizinho barulhento.

![Mostrando o pior desempenho por uma grande parte da barra](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Depois de um período de tempo problemático for identificado (por exemplo, durante o dia 30 de janeiro, na imagem acima) o administrador do Power BI pode remover todos os filtros de conjunto de dados e filtrar apenas por esse período de tempo para determinar quais conjuntos de dados foram consultados ativamente durante esse tempo. O conjunto de dados para o efeito de vizinho barulhento culpado geralmente é o conjunto de dados consultado superior ou aquela com a duração média de consulta mais longa.

Uma solução para esse problema pode ser distribuir o culpado conjuntos de dados em espaços de trabalho diferentes em diferentes capacidades Premium ou em capacidade compartilhada, se o tamanho do conjunto de dados, requisitos de consumo e atualização de dados padrões são suportados.

O inverso também poderia ser true. O administrador do Power BI pode identificar quando um conjunto de dados de desempenho de consulta melhora drasticamente e, em seguida, procure o que desapareceu. Se faltam determinadas informações naquele ponto, que pode ajudar para apontar para o causando problema.

## <a name="determining-whether-there-is-enough-memory"></a>Determinando se há memória suficiente

Para determinar se há memória suficiente para a capacidade para concluir suas cargas de trabalho, o administrador do Power BI pode se referir à **percentuais de memória consumida** visual na **conjuntos de dados** guia do aplicativo. **Todos os** memória (total) representa a memória consumida por conjuntos de dados carregados na memória, independentemente se eles são consultados ou processados ativamente. **Active Directory** memória representa a memória consumida por conjuntos de dados que estão sendo processados ativamente.

Em uma capacidade íntegra visual se parecerá com este, mostrando uma lacuna entre todos os (total) e de memória ativa:

![Uma capacidade íntegra mostrará uma lacuna entre todos os (total) e de memória ativa](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

Em uma capacidade sofrendo a pressão de memória, o mesmo elemento visual claramente mostrará memória ativa e convergindo, o que significa que é impossível carregar conjuntos de dados adicionais na memória, em seguida, total de memória. Nesse caso, o administrador do Power BI pode clicar **capacidade reinicie** (no **opções avançadas de** da área de configurações de capacidade do portal de administração). Reiniciando os resultados de capacidade em conjuntos de dados são liberadas da memória e permitindo que eles Recarregar na memória conforme necessário (por consultas ou atualização de dados).

![* Memória ativa * convergindo com * * todos os * * a memória](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Determinando se há suficiente CPU

Em geral, utilização média da CPU de uma capacidade deve permanecer abaixo de 80%. Exceder esse valor significa que a capacidade está se aproximando da saturação da CPU.

Efeitos de saturação da CPU são expressos por operações demorando mais do que deveriam, devido à capacidade de executar muitas alternâncias de contextos de CPU, pois ele tenta processar todas as operações. Em uma capacidade Premium com um grande número de consultas simultâneas, isso é indicado por tempos de espera de consulta altas. Uma consequência de tempos de espera de consulta altas é a capacidade de resposta mais lenta que o normal. O administrador do Power BI pode identificar facilmente quando a CPU está saturada, por meio da exibição de **distribuições de tempo de espera por hora consulta** visual. Contagens de indicam possíveis saturação da CPU de tempo de espera de picos periódicos de consulta.

![Contagens de indicam possíveis saturação da CPU de tempo de espera de picos periódicos de consulta](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Um padrão semelhante, às vezes, pode ser detectado em operações em segundo plano se elas contribuem para a saturação da CPU. Um administrador do Power BI pode procurar um pico periódico em tempos de atualização para um conjunto de dados específico, o que pode indicar a saturação da CPU no momento (provavelmente devido a outras atualizações de conjunto de dados em andamento e/ou consultas interativas). Nessa instância, referindo-se para o **sistema** exibição no aplicativo pode não necessariamente revelar que a CPU está em 100%. O **sistema** modo de exibição exibe as médias de hora em hora, mas a CPU pode se tornar saturada por vários minutos de operações pesadas, que mostra como picos nos tempos de espera.

Há mais nuances para ver o efeito de saturação da CPU. Embora o número de consultas que aguardar seja importante, tempo de espera de consulta sempre acontecerá até certo ponto sem causar degradação de desempenho considerável. Alguns conjuntos de dados (com tempo de média de consulta mais longa, que indica a complexidade ou tamanho) são mais propensos aos efeitos de saturação da CPU que outras pessoas. Para identificar facilmente esses conjuntos de dados, o administrador do Power BI pode observar alterações na composição de cor das barras na **distribuição do tempo de espera por hora** visual. Depois de identificar uma barra de exceções, podem parecer para os conjuntos de dados que teve esperas de consulta durante esse período e examinar também o tempo de espera médio de consulta em comparação à média de duração da consulta. Quando essas duas métricas são da mesma magnitude e a carga de trabalho de consulta do conjunto de dados é não trivial, é provável que o conjunto de dados é afetado por CPU insuficiente.

Esse efeito pode ser especialmente aparente quando um conjunto de dados é consumido em curtos picos de consultas de alta frequência por vários usuários (por exemplo, em uma sessão de treinamento), resultando em saturação da CPU durante cada disparo. Nesse caso, os tempos de espera de consulta significativas nesse conjunto de dados podem ser experimentados, bem como causar impacto em outros conjuntos de dados na capacidade (efeito de vizinho barulhento).

Em alguns casos, os administradores do Power BI podem solicitar que os proprietários de conjunto de dados criam uma menor carga de trabalho de consulta volátil, criando um painel (quais consultas periodicamente com qualquer conjunto de dados de atualização para blocos em cache), em vez de um relatório. Isso pode ajudar a evitar picos quando o painel for carregado. Essa solução talvez nem sempre seja possível para determinada requisitos de negócios, no entanto, ele pode ser uma maneira eficiente para evitar a saturação da CPU, sem fazer a alteração para o conjunto de dados.

## <a name="acknowledgements"></a>Confirmações

Este artigo foi escrito por Peter Myers, MVP de plataforma de dados e independente profissional de BI com [bit a bit soluções](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Monitorar as capacidades Premium com o aplicativo](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Capacidades do monitor no portal de administração](service-admin-premium-monitor-portal.md)   

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||