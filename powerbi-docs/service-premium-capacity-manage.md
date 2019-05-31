---
title: Gerenciar capacidades do Microsoft Power BI Premium
description: Descreve as tarefas de gerenciamento para as capacidades do Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e4bb907e12d3c0b07408f069d9b238599756e8e0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565236"
---
# <a name="managing-premium-capacities"></a>Gerenciando as capacidades Premium

Gerenciar o Power BI Premium envolve criar, gerenciar e monitorar as capacidades Premium.

## <a name="creating-and-managing-capacities"></a>Criar e gerenciar as capacidades

O **configurações de capacidade** página do portal de administração do Power BI exibe o número de núcleos adquiridos e as capacidades Premium disponíveis. A página permite que os administradores globais do Office 365 ou administradores de serviço do Power BI para criar as capacidades Premium de núcleos virtuais disponíveis, ou para modificar as capacidades de Premium existentes.

Ao criar uma capacidade Premium, os administradores precisam definir:

- Nome da capacidade (exclusivo dentro do Locatário).
- Capacidade admin(s).
- Tamanho da capacidade.
- Região de residência de dados.

Pelo menos um administrador de capacidade deve ser atribuído. Os usuários atribuídos como administradores de capacidade podem:

- Atribua espaços de trabalho à capacidade.
- Gerencie permissões de usuário, para adicionar os usuários com permissões de atribuição (para habilitá-los para atribuir espaços de trabalho à capacidade) ou os administradores de capacidade adicional.
- Gerencie cargas de trabalho, para configurar o uso máximo da memória para cargas de trabalho de fluxos de dados e relatórios paginados.
- Reinicie a capacidade, para redefinir todas as operações devido a uma sobrecarga do sistema.

Os administradores de capacidade não podem acessar o conteúdo do espaço de trabalho, a menos que explicitamente atribuído em permissões de espaço de trabalho. Eles também não tem acesso a todas as áreas de administração do Power BI (a menos que explicitamente atribuído), como as métricas de uso, os logs de auditoria ou as configurações de locatário. É importante, os administradores de capacidade não tem permissões para criar novas capacidades ou dimensionar as capacidades existentes. Os administradores são atribuídos em uma base por capacidade, garantindo que eles podem apenas exibir e gerenciar as capacidades às quais eles estão atribuídos.

Tamanho da capacidade é selecionado de uma lista de opções de SKU disponíveis que é restrito pelo número de núcleos disponíveis no pool. É possível criar várias capacidades do pool, o que poderia ser provenientes de um ou mais adquirido SKUs. Por exemplo, um SKU P3 (32 núcleos) poderia ser usados para criar as capacidades de três: um P2 (16 núcleos) e P1 duas (2 x 8 núcleos virtuais). Melhorar o desempenho e escala podem ser obtidos com a criação de menores porte capacidades, conforme descrito na [otimizando as capacidades do Premium](service-premium-capacity-optimize.md) artigo. A imagem a seguir mostra uma configuração de exemplo para a organização fictícia Contoso consiste em cinco capacidades de Premium (3 x 2 e P1 x P3) com cada contendo espaços de trabalho do aplicativo e vários espaços de trabalho na capacidade compartilhada.

![Uma configuração de exemplo para a organização fictícia Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

Uma capacidade Premium pode ser atribuída a uma região diferente de região de residência do locatário do Power BI, conhecido como várias áreas geográficas. Várias áreas geográficas proporciona controle administrativo sobre quais datacenters em regiões geográficas definidas, o conteúdo do Power BI reside. A lógica para uma implantação de várias áreas geográficas é normalmente usada em corporativo ou conformidade do governo, em vez de desempenho e escala. Relatório e o carregamento do painel ainda envolve as solicitações para a região de residência de metadados. Para obter mais informações, consulte [suporte de várias áreas geográficas para o Power BI Premium](service-admin-premium-multi-geo.md).

Os administradores de serviço do Power BI e administradores globais do Office 365 podem modificar as capacidades Premium. Especificamente, eles podem:

- Altere o tamanho da capacidade para escalar verticalmente ou reduzir verticalmente recursos.
- Adicionar ou remover administradores de capacidade.
- Adicionar ou remover usuários que têm permissões de atribuição.
- Adicionar ou remover as cargas de trabalho adicionais.
- Altere as regiões.

São necessárias permissões de atribuição para atribuir um espaço de trabalho a uma capacidade Premium específica. As permissões podem ser concedidas para a organização inteira, usuários específicos ou grupos.

Por padrão, as capacidades Premium dão suporte a cargas de trabalho associadas à execução de consultas no Power BI. Capacidades Premium também dão suporte a cargas de trabalho adicionais: **Inteligência Artificial (Cognitive Services)** , **relatórios paginados**, e **fluxos de dados**. Cada carga de trabalho exige a configuração a memória máxima (como uma porcentagem do total de memória disponível) que pode ser usada pela carga de trabalho. É importante entender que aumentar as alocações de memória máximo pode afetar o número de modelos de Active Directory que pode ser hospedado e a taxa de transferência de atualizações. 

Memória dinamicamente alocada para fluxos de dados, mas é estaticamente alocada para relatórios paginados. O motivo para alocar estaticamente a memória máxima é que os relatórios paginados executado dentro de um espaço protegido de independente da capacidade. Tome cuidado quando configuração paginado relatórios memória, pois reduz a memória disponível para carregar modelos. Para obter mais informações, consulte o [configurações de memória padrão](service-admin-premium-workloads.md#default-memory-settings).

Excluir uma capacidade Premium, é possível e não resultará na exclusão de seus espaços de trabalho e o conteúdo. Em vez disso, ele move nenhum espaço de trabalho atribuído à capacidade compartilhada. Quando a capacidade Premium foi criada em uma região diferente, o espaço de trabalho é movido para uma capacidade compartilhada da região de residência.

### <a name="assigning-workspaces-to-capacities"></a>Atribuir espaços de trabalho para as capacidades

Espaços de trabalho podem ser atribuídos a uma capacidade Premium no portal de administração do Power BI ou, para um espaço de trabalho do aplicativo na **espaço de trabalho** painel.

Os administradores de capacidade, bem como os administradores globais do Office 365 ou administradores de serviço do Power BI, podem atribuir espaços de trabalho no portal de administração do Power BI em massa. Em massa atribuída pode aplicar a:

- **Espaços de trabalho por usuários** -todos os espaços de trabalho pertencentes a esses usuários, incluindo espaços de trabalho pessoas, são atribuídos à capacidade Premium. Isso incluirá a reatribuição de espaços de trabalho quando eles já estão atribuídos a uma capacidade Premium diferente. Além disso, os usuários também recebem permissões de atribuição de espaço de trabalho.

- **Workspaces específicos**
- **Espaços de trabalho de toda a organização** -todos os espaços de trabalho, incluindo espaços de trabalho pessoas, são atribuídos à capacidade Premium. Todos os usuários atuais e futuros recebem permissões de atribuição de espaço de trabalho. Essa abordagem não é recomendada. Uma abordagem mais direcionada é preferencial.

Um espaço de trabalho pode ser adicionado a uma capacidade Premium usando o **espaço de trabalho** painel fornecendo ao usuário é um administrador do espaço de trabalho e tem permissões de atribuição.

![Usando o painel de espaço de trabalho para atribuir um espaço de trabalho a uma capacidade Premium](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Os administradores do espaço de trabalho podem remover um espaço de trabalho de uma capacidade (capacidade compartilhada) sem a necessidade de permissões de atribuição. Remover espaços de trabalho da capacidade dedicada efetivamente Realoca espaço de trabalho para capacidade compartilhada. Observe que a remoção de um espaço de trabalho de uma capacidade Premium pode ter consequências negativas, resultando, por exemplo, conteúdo compartilhado se torne indisponível para o Power BI gratuito licenciado usuários ou a suspensão de atualização agendada quando elas excedem as concessões com suporte por capacidade compartilhada.

No serviço do Power BI, um espaço de trabalho atribuído a uma capacidade Premium será facilmente identificado pelo ícone de losango que adorna o nome do espaço de trabalho.

![Identificando um espaço de trabalho atribuído a uma capacidade Premium](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Capacidades de monitoramento

Monitoramento de capacidades Premium fornece aos administradores uma compreensão de como as capacidades são executados. As capacidades podem ser monitoradas usando o portal de administração do Power BI ou o **métricas de capacidade do Power BI Premium** aplicativo (Power BI).

### <a name="power-bi-admin-portal"></a>Portal de administração do Power BI

No portal de administração, para cada capacidade, o **integridade** guia fornece métricas de resumidas para cada carga de trabalho habilitada e a capacidade. As métricas mostram uma média nos últimos sete dias.  

No nível de capacidade, as métricas são cumulativas de todas as cargas de trabalho habilitadas. as métricas a seguir são fornecidas:

- **UTILIZAÇÃO da CPU** -fornece a utilização média da CPU como uma porcentagem de CPU total disponível para a capacidade.  
- **USO de memória** -fornece a média de utilização de memória (em GB) como um total de memória disponível para a capacidade. 

Para cada carga de trabalho habilitada, utilização da CPU e uso de memória são fornecidos, bem como um número de métricas específicas de carga de trabalho. Por exemplo, para a carga de trabalho do fluxo de dados **Contagem Total** mostra total de atualizações para cada fluxo de dados, e **duração média** mostra a duração média da atualização para o fluxo de dados.

![Guia de integridade de capacidade no portal](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Para saber mais sobre todas as métricas disponíveis para cada carga de trabalho, consulte [monitorar as capacidades no portal de administração](service-admin-premium-monitor-portal.md).

Os recursos de monitoramento no portal de administração do Power BI são projetados para fornecer um resumo rápido das métricas de capacidade de chave. Para obter mais monitoramento, é recomendável usar o **métricas de capacidade do Power BI Premium** aplicativo.

### <a name="power-bi-premium-capacity-metrics-app"></a>Power BI Premium métricas de capacidade de aplicativo

O [aplicativo de métricas de capacidade do Power BI Premium](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) é um aplicativo do Power BI disponíveis para os administradores de capacidade e é instalado como qualquer outro aplicativo do Power BI. Ele contém um painel e relatório.

![Power BI Premium métricas de capacidade de aplicativo](media/service-premium-capacity-manage/capacity-metrics-app.png)

Quando o aplicativo é aberto, o painel é carregado para apresentar vários blocos de expressar uma exibição agregada em todas as capacidades dos quais o usuário é um administrador de capacidade. O layout do painel inclui cinco seções principais:

- **Visão geral** -versão do aplicativo, o número de espaços de trabalho e as capacidades
- **Resumo do sistema** -métricas de memória e CPU
- **Resumo do conjunto de dados** - número de conjuntos de dados, DQ/LC, atualização e métricas de consulta
- **Resumo do fluxo de dados** - número de fluxos de dados e métricas do conjunto de dados
- **Paginado relatório Resumo de** - atualizar e exibir métricas

O relatório subjacente, do qual os blocos do painel foram fixados, pode ser acessado clicando em qualquer bloco do dashboard. Ele fornece uma perspectiva mais detalhada de cada uma das seções do painel e dá suporte a filtragem interativa. 

Filtragem pode ser feita com a configuração de segmentações de dados por intervalo de datas, capacidade, espaço de trabalho e carga de trabalho (relatório, conjunto de dados, fluxo de dados) e selecionando os elementos dentro do relatório visuais cruzar filtrar a página de relatório. Filtragem cruzada é uma técnica poderosa para restringi-lo a períodos de tempo específico, as capacidades, espaços de trabalho, conjuntos de dados, etc. e pode ser muito útil ao executar a análise da causa raiz.

Para obter informações detalhadas sobre as métricas de relatório e painel no aplicativo, consulte [capacidades Premium de Monitor com o aplicativo](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>Interpretando as métricas

As métricas devem ser monitoradas para estabelecer uma compreensão de linha de base de atividade de carga de trabalho e uso do recurso. Se a capacidade de se tornar lento, é importante entender quais métricas para monitorar e as conclusões que você pode fazer.

O ideal é que consultas deverá concluir dentro de um segundo para proporcionar experiências responsivas a usuários de relatório e permitir maior taxa de transferência de consulta. Geralmente é uma preocupação menor quando faz com que os processos em segundo plano – incluindo atualizações - vezes mais tempo para concluir.

Em geral, os relatórios lentos podem ser uma indicação de uma capacidade de superaquecimento. Quando os relatórios de falham ao carregar, isso é uma indicação de uma capacidade em excesso aquecida. Em qualquer situação, a causa raiz pode ser atribuível a muitos fatores, incluindo:

- **Consultas com falha** certamente indicar pressão de memória e um modelo não pôde ser carregado na memória. O serviço do Power BI tentará carregar um modelo por 30 segundos antes de falhar.

- **Tempos de espera de consulta excessiva** pode ser devido a vários motivos:
  - A necessidade de serviço do Power BI, primeiro remova o modelo (s) e, em seguida, carregar o modelo será consultada (Lembre-se que taxas mais altas de conjunto de dados remoção sozinhas não são uma indicação de estresse de capacidade, a menos que acompanhada por consulta tempos de espera longos que indicam a sobrecarga de memória).
  - Modelo tempo de carregamento (especialmente a espera para carregar um modelo grande na memória).
  - Consultas de longa execução.
  - Número excessivo de conexões LC\DQ (excedendo os limites de capacidade).
  - Saturação da CPU.
  - Designs de relatório complexo com um número excessivo de elementos visuais em uma página (Lembre-se que cada elemento visual é uma consulta).

- **As durações de consulta longa** pode indicar que os designs de modelo não são otimizados, especialmente quando vários conjuntos de dados estão ativos em uma capacidade, e apenas um conjunto de dados está produzindo durações de consulta longa. Isso sugere que a capacidade é recursos suficientemente, e se o conjunto de dados em questão está apenas lenta ou abaixo do ideal. Consultas de longa execução pode ser problemático porque pode bloquear o acesso a recursos exigida por outros processos.
- **Atualizar longos tempos de espera** indicar memória insuficiente, devido a muitos modelos de Active Directory, consumindo memória ou uma atualização de um problema está impedindo a outra é atualizada (excedendo limites de atualização paralela).

Uma explicação mais detalhada de como usar as métricas é abordada a [capacidades Premium otimizando](service-premium-capacity-optimize.md) artigo.

## <a name="acknowledgements"></a>Confirmações

Este artigo foi escrito por Peter Myers, MVP de plataforma de dados e independente profissional de BI com [bit a bit soluções](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Otimizando as capacidades Premium](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Configurar cargas de trabalho em uma capacidade Premium](service-admin-premium-workloads.md)   

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||
