---
title: O que é o Microsoft Power BI Premium?
description: O Power BI Premium fornece capacidade dedicada para sua organização, oferecendo desempenho mais confiável e maiores volumes de dados sem exigir a compra de licenças por usuário.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/22/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e5ffa624bf69cf470aade076c80ac37028a55456
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565276"
---
# <a name="what-is-power-bi-premium"></a>O que é o Power BI Premium?

O Power BI Premium fornece recursos aprimorados e dedicados para executar o serviço do Power BI para sua organização. Por exemplo:

- Maior dimensionamento e desempenho
- Flexibilidade de licença por capacidade
- Unificar o BI corporativo e autoatendimento
- Estenda o BI local com o Power BI Report Server
- Suporte para a residência de dados por região (Multi-Geo)
- Compartilhar dados com qualquer pessoa sem precisar adquirir uma licença por usuário

Este artigo não se destina para fornecer detalhes sobre cada recurso do Power BI Premium – na verdade, ela toca apenas a superfície. Quando for necessário, são fornecidos links para artigos adicionais com informações mais detalhadas.

## <a name="subscriptions-and-licensing"></a>Assinaturas e licenciamento

O Power BI Premium é uma assinatura do Office 365 de nível de locatário disponível em duas famílias SKU (Stock Keeping Unit):

- **EM** SKUs (EM1-EM3) para a inserção, que exigem um compromisso anual, cobrado mensalmente.
- **P** SKUs (P1-P3) para inserir e recursos corporativos, exigindo um compromisso mensal ou anual, cobrado mensalmente e inclui uma licença para instalar o servidor de relatório do Power BI no local.

Uma abordagem alternativa é comprar um **do Azure Power BI Embedded** assinatura, que tem uma única **um** apenas a fins de família SKU (A1-A6) para inserir e testes de capacidade. Todas as SKUs entregar núcleos para criar as capacidades, mas os SKUs EM são restritos para a inserção de menor escala. EM1, EM2, A1 e A2 SKUs com menos de quatro núcleos não são executados em uma infraestrutura dedicada.

Enquanto o foco deste artigo é sobre os SKUs P, grande parte do que está descrito também é relevante para os SKUs. Em contraste com a assinatura Premium SKUs, SKUs do Azure não exigem nenhuma alocação de tempo e são cobradas por hora. Eles fornecem elasticidade completa habilitando a escala de backup, reduzir verticalmente, pausar, retomar e excluam. 

Power BI Embedded do Azure é amplamente fora do escopo deste artigo, mas ela é descrita a [abordagens do teste](service-premium-capacity-optimize.md#testing-approaches) seção do artigo as capacidades Premium otimizando como uma opção econômica e prático para testar e medir as cargas de trabalho. Para saber mais sobre os SKUs do Azure, consulte [documentação do Azure Power BI Embedded](https://azure.microsoft.com/services/power-bi-embedded/).

### <a name="purchasing"></a>Compra

Power BI Premium são compradas pelos administradores no Centro de administração do Microsoft 365. Especificamente, apenas administradores globais do Office 365 ou administradores de cobrança pode comprar SKUs. Quando adquirido, o locatário recebe um número correspondente de núcleos para atribuir a capacidades, conhecidas como *pool de núcleos virtuais*. Por exemplo, comprar um SKU P3 fornece ao locatário 32 núcleos. Para obter mais informações, consulte [como comprar o Power BI Premium](service-admin-premium-purchase.md).

## <a name="dedicated-capacities"></a>Capacidade dedicada

Com o Power BI Premium, você obtém *dedicado capacidades*. Em contraste com uma capacidade compartilhada em que cargas de trabalho executadas em recursos computacionais compartilhados com outros clientes, uma capacidade dedicada é para uso exclusivo por uma organização. É isolada com recursos computacionais dedicados que oferecem um desempenho confiável e consistente para o conteúdo hospedado. 

Espaços de trabalho residem dentro de capacidades. Cada usuário do Power BI tem um espaço de trabalho pessoal, conhecido como **meu espaço de trabalho**. Espaços de trabalho adicionais podem ser criados para habilitar a colaboração e a implantação, e eles são conhecidos como **espaços de trabalho do aplicativo**. Por padrão, os espaços de trabalho, incluindo espaços de trabalho pessoas, são criados na capacidade compartilhada. Quando você tem as capacidades Premium, os espaços de trabalho de meus espaços de trabalho e de aplicativo podem ser atribuídos a capacidades Premium.

### <a name="capacity-nodes"></a>Nós de capacidade

Conforme descrito na [licenciamento e assinaturas](#subscriptions-and-licensing) seção, há duas famílias de SKU do Power BI Premium: **EME** e **P**. Todas as SKUs do Power BI Premium estão disponíveis como capacidade *nós*, cada um representando uma quantidade definida de recursos compostos por processador, memória e armazenamento. Além de recursos, cada SKU tem limites operacionais no número de conexões do DirectQuery e Conexão ao vivo por segundo e o número de modelo paralelo é atualizada.

Processamento é feito por um determinado número de núcleos, dividido igualmente entre o back-end e front-end.

**Núcleos de back-end** são responsáveis pela funcionalidade do Power BI core, incluindo processamento de consultas, gerenciamento de cache, execução de R services, a atualização do modelo, processamento de linguagem natural (Q & A) e renderização do lado do servidor de relatórios e imagens. Núcleos de back-end são atribuídos a uma quantidade fixa de memória que é usado principalmente para modelos de host, também conhecido como Active Directory conjuntos de dados.

**Núcleos de front-end** é responsável pelo web service, dashboard e relatório de gerenciamento de documentos, gerenciamento de direitos de acesso, agendamento, APIs, carregamentos e downloads e geralmente para tudo relacionado ao usuário experiências.

Armazenamento é definido como **100 TB por nó de capacidade**.

Os recursos e os limites de cada SKU Premium (e dimensionado maneira equivalente um SKU) são descritas na tabela a seguir:

| Nós de capacidade | Total de núcleos virtuais | Núcleos virtuais de back-end | RAM (GB) | Núcleos virtuais de front-end | Conexão dinâmica/DirectQuery (por segundo) | Paralelismo de atualização do modelo |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3.75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7.5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

### <a name="capacity-workloads"></a>Cargas de trabalho de capacidade

Cargas de trabalho de capacidade são disponibilizados aos usuários de serviços. Por padrão, o Premium e as capacidades do Azure dão suporte a apenas uma conjunto de dados carga de trabalho associada à execução de consultas no Power BI. A carga de trabalho do conjunto de dados não pode ser desabilitada. Cargas de trabalho adicionais podem ser habilitadas para [AI (os serviços Cognitivos)](https://powerbi.microsoft.com/blog/easy-access-to-ai-in-power-bi-preview/), [fluxos de dados](service-dataflows-overview.md#dataflow-capabilities-on-power-bi-premium), e [relatórios paginados](paginated-reports-save-to-power-bi-service.md). Essas cargas de trabalho têm suporte somente a assinaturas Premium. 

Cada carga de trabalho adicional permite configurar a memória máxima (como uma porcentagem do total de memória disponível) que pode ser usada pela carga de trabalho. Valores padrão para o máximo de memória são determinados por SKU. Você pode maximizar recursos disponíveis da sua capacidade, permitindo apenas as cargas de trabalho adicionais quando eles são usados. E você pode alterar as configurações somente quando você determinou que as configurações padrão não estão atendendo a seus requisitos de capacidade de recursos de memória. Cargas de trabalho podem ser habilitadas e configuradas para os administradores de um capacidade por capacidade usando **configurações de capacidade** na [portal de administração](service-admin-portal.md) ou usando o [as capacidades de APIs de REST](https://docs.microsoft.com/rest/api/power-bi/capacities).  

![Habilitar cargas de trabalho](media/service-admin-premium-workloads/admin-portal-workloads.png)

Para obter mais informações, consulte [configurar cargas de trabalho em uma capacidade Premium](service-admin-premium-workloads.md). 

### <a name="how-capacities-function"></a>Como função de capacidades

AT todas as vezes, o serviço do Power BI faz o melhor uso de recursos de capacidade ao mesmo tempo em que não exceda os limites impostos na capacidade.

Operações de capacidade são classificadas como uma *interativa* ou *plano de fundo*. Operações interativas incluem solicitações de processamento e responder às interações do usuário (filtragem, consultando a p e R, etc.). Em geral, consulta de modelo de importação é memória intensivo de recursos, enquanto consultando modelos DirectQuery e Conexão ao vivo é intensivo de CPU. Operações em segundo plano incluem o fluxo de dados e importar as atualizações de modelo e o cache de consulta do painel.

É importante entender que as operações interativas sempre sejam priorizadas sobre operações em segundo plano para garantir a experiência melhor possível ao usuário. Se houver recursos insuficientes, operações em segundo plano são adicionadas a uma fila para processamento quando a liberação de recursos. Operações em segundo plano, como atualizações de conjunto de dados, podem ser interrompido no meio do processo pelo serviço do Power BI e adicionada a uma fila.

Modelos de importação devem ser totalmente carregados na memória para que possam ser consultados ou atualizados. O serviço do Power BI gerencia a memória, uso usando algoritmos para garantir o uso máximo da memória disponível sofisticados e pode causar confirmar em excesso de capacidade: Enquanto é possível para uma capacidade armazenar a importação de vários modelos (até 100 TB por capacidade Premium), quando o armazenamento de disco combinado excede a memória com suporte (e a memória adicional é necessária para consultar e atualizar), em seguida, eles não podem ser carregados na memória no o mesmo tempo.

Modelos de importação, portanto, são carregados no e removidos da memória de acordo com o uso. Um modelo de importação é carregado quando é consultada (operação interativa) e ainda não na memória, ou quando ele deve para ser atualizada (operação em segundo plano).

A remoção de um modelo de memória é conhecida como *remoção*. É uma operação que do Power BI pode executar rapidamente, dependendo do tamanho dos modelos. Se a capacidade não está tendo qualquer pressão de memória, os modelos são simplesmente carregados na memória e permanecem lá. No entanto, quando a memória disponível é insuficiente para carregar um modelo, o serviço do Power BI primeiro será necessário para liberar memória. Ele libera memória por meio da detecção modelos que se tornaram inativos por modelos que não foram usados nos últimos três minutos de busca \[ [1](#endnote-1)\]e, em seguida, removê-los. Se não houver nenhum modelo de inativo para remover, o serviço do Power BI procura remover modelos carregados para operações em segundo plano. Um último recurso, após 30 segundos de tentativas com falha \[ [1](#endnote-1)\], é a operação interativa com falha. Nesse caso, o usuário do relatório é notificado da falha com uma sugestão para tentar novamente em breve. Em alguns casos, os modelos podem ser descarregados da memória devido a operações de serviço.

É importante enfatizar que a remoção do conjunto de dados é um comportamento normal e esperado. Ela se esforça para maximizar o uso de memória por carregar e descarregar modelos cujos tamanhos combinados podem exceder a memória disponível. Isso é por design e é completamente transparente para os usuários de relatório. Taxas de remoção alta não significa necessariamente que a capacidade insuficiente é recursos. Eles podem, no entanto, tornam-se uma preocupação se a capacidade de resposta de consulta ou atualização está apresentando problemas devido a taxas de remoção de alta.

Atualizações dos modelos de importação são sempre uso intensivo de memória como modelos devem ser carregados na memória. Memória adicional é necessária para processamento. Uma atualização completa pode usar aproximadamente o dobro da quantidade de memória exigida pelo modelo. Isso garante que o modelo pode ser consultado, mesmo quando está sendo processada, porque as consultas são enviadas para o modelo existente, até que a atualização é concluída e os novos dados de modelo estão disponíveis. Atualização incremental exigirá menos memória e poderia ser concluídas mais rapidamente e então, pode reduzir significativamente a pressão nos recursos de capacidade. As atualizações também podem ser intensivo de CPU para modelos, especialmente aqueles com transformações complexas de Power Query ou tabelas/colunas calculadas que são complexos ou são baseados em tabelas grandes.

As atualizações, como consultas, exigem que o modelo ser carregado na memória. Se não houver memória insuficiente, o serviço do Power BI tentará remover modelos inativos e, se isso não for possível (como todos os modelos são Active Directory), o trabalho de atualização está na fila. As atualizações são normalmente intensivo de CPU, ainda mais assim que as consultas. Por esse motivo, há limites de capacidade no número de atualizações simultâneas, definido como 1,5 vezes o número de back-end núcleos, arredondado para cima. Se houver muitas atualizações simultâneas, uma atualização agendada será enfileirada. Quando ocorrem estas situações, pode demorar mais para a atualização ser concluída. Sob demanda é atualizada, como aqueles disparada por uma solicitação de usuário ou uma chamada à API tentará novamente três vezes \[ [1](#endnote-1)\]. Se ainda não existem recursos suficientes, a atualização, em seguida, irá falhar.

Notas da seção:   
<a name="endnote-1"></a>\[1\] sujeitas a alterações.

### <a name="regional-support"></a>Suporte regional

Ao criar uma nova capacidade, os administradores globais do Office 365 e administradores de serviço do Power BI pode especificar uma região em que os espaços de trabalho atribuídos à capacidade residirá. Isso é conhecido como **Multi-Geo**. Com várias áreas geográficas, empresas podem atender os requisitos de residência de dados ao implantar conteúdo em datacenters em uma região específica, mesmo que ele seja diferente da região na qual reside a assinatura do Office 365. Para obter mais informações, consulte [suporte de várias áreas geográficas para o Power BI Premium](service-admin-premium-multi-geo.md).

### <a name="capacity-management"></a>Gerenciamento de capacidade

Gerenciar as capacidades Premium envolve a criação ou excluindo as capacidades, atribuindo administradores, atribuir espaços de trabalho, a configuração de cargas de trabalho, monitoramento e fazer ajustes para otimizar o desempenho de capacidade. 

Os administradores globais do Office 365 e administradores de serviço do Power BI podem criar capacidades Premium de núcleos virtuais disponíveis, ou modificar as capacidades de Premium existentes. Quando uma capacidade é criada, tamanho da capacidade e a região geográfica são especificados e capacidade de pelo menos um administrador é atribuída. 

Quando as capacidades são criadas, a maioria das tarefas administrativas são concluídas na [portal de administração](service-admin-portal.md).

![Portal de administração](media/service-premium-what-is/premium-admin-portal.png)

Os administradores de capacidade podem atribuir espaços de trabalho à capacidade, gerenciar permissões de usuário e atribuir outros administradores. Os administradores de capacidade também podem configurar cargas de trabalho, ajuste as alocações de memória e se necessário, reinicie uma capacidade, redefinindo as operações no caso de uma sobrecarga de capacidade.

![Portal de administração](media/service-premium-what-is/premium-admin-portal-mgmt.png)

Os administradores de capacidade também podem verificar se que uma capacidade é executado sem problemas. Eles podem monitorar o direito de integridade de capacidade no portal de administração ou usando o aplicativo de métricas de capacidade Premium.

Para saber mais sobre como criar as capacidades, atribuindo administradores e atribuir espaços de trabalho, consulte [capacidades Premium Gerenciando](service-premium-capacity-manage.md). Para saber mais sobre as funções, consulte [funções de administrador relacionado ao Power BI](service-admin-administering-power-bi-in-your-organization.md#administrator-roles-related-to-power-bi).

### <a name="monitoring"></a>Monitoramento

Monitoramento de capacidades Premium fornece aos administradores uma compreensão de como as capacidades são executados. As capacidades podem ser monitoradas usando o portal de administração e o [aplicativo de métricas de capacidade do Power BI Premium](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics).

Monitoramento no portal do fornece uma visão geral com métricas de alto nível que indicam o cargas colocadas e os recursos utilizados por sua capacidade média nos últimos sete dias. 

![Portal de administração](media/service-premium-what-is/premium-admin-portal-health.png)

O **métricas de capacidade do Power BI Premium** aplicativo fornece as informações mais detalhadas como desempenho de suas capacidades. O aplicativo fornece um painel de alto nível e relatórios mais detalhados.

![Dashboard do aplicativo de métricas](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Painel do aplicativo você pode clicar em uma célula de métrica para abrir um relatório aprofundado. Os relatórios fornecem métricas detalhadas e capacidade de filtragem para drill down nas informações mais importantes que você precisam manter suas capacidades funcionando sem problemas.

![Contagens de indicam possíveis saturação da CPU de tempo de espera de picos periódicos de consulta](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Para saber mais sobre as capacidades de monitoramento, consulte [de monitoramento no portal de administração do Power BI](service-admin-premium-monitor-portal.md) e [monitoramento com o aplicativo de métricas de capacidade do Power BI Premium](service-admin-premium-monitor-capacity.md).

### <a name="optimizing-capacities"></a>Otimizando as capacidades

Fazer o melhor uso de suas capacidades é essencial para garantir os usuários a obterem o desempenho e você esteja tirando o máximo de valor para o seu investimento de Premium. Ao monitorar métricas-chave, os administradores podem determinar a melhor maneira solucionar problemas de gargalos e tomar as medidas necessárias. Para obter mais informações, consulte [capacidades Premium otimizando](service-premium-capacity-optimize.md) e [cenários de capacidade Premium](service-premium-capacity-scenarios.md).

### <a name="capacities-rest-apis"></a>Capacidades de APIs REST

As APIs REST do Power BI incluem uma coleção de [as capacidades de APIs](https://docs.microsoft.com/rest/api/power-bi/capacities). Com as APIs, os administradores por meio de programação podem gerenciar muitos aspectos de suas capacidades Premium, incluindo habilitação e desabilitação de cargas de trabalho, atribuir espaços de trabalho para uma capacidade e muito mais.

## <a name="large-datasets"></a>Grandes conjuntos de dados

Dependendo do SKU, o Power BI Premium dá suporte a carregar arquivos de modelo do Power BI Desktop (. pbix) até um máximo de **10GB** de tamanho. Quando carregado, o modelo pode ser publicado para um espaço de trabalho atribuído a uma capacidade Premium. O conjunto de dados pode ser atualizado para até **12 GB** de tamanho.

### <a name="size-considerations"></a>Considerações de tamanho

Modelos grandes podem usar muitos recursos. Você deve ter pelo menos um SKU de P1 para os modelos maiores que 1 GB. Embora publicando modelos grandes em espaços de trabalho de apoio de SKUs a até A3 poderia trabalho, atualizá-los não funcionará.

A tabela a seguir descreve os SKUs recomendados para vários tamanhos .pbix:

   |SKU  |Tamanho de .pbix   |
   |---------|---------|
   |P1    | < 3 GB        |
   |P2    | < 6 GB        |
   |P3, P4, P5    | até 10 GB   |

O SKU A4 do Power BI Embedded é igual ao SKU P1, o A5 = P2 e o A6 = P3. Observe que a publicação de grandes modelos em SKUs A e EM pode retornar erros que não são específicos para o erro de limitação de tamanho do modelo na capacidade compartilhada. Erros de atualização de modelos grandes em SKUs A e EM provavelmente são resultados de atingimento de tempos limite. 

Os arquivos. pbix representam dados em uma *altamente compactados estado*. Os dados provavelmente expandirão várias vezes quando carregados na memória e, a partir daí, eles podem expandir várias vezes mais durante a atualização de dados.

Atualização agendada de grandes conjuntos de dados pode levar muito tempo e consumir muitos recursos. É importante não agende muitas atualizações sobrepostas. É recomendável [atualização incremental](service-premium-incremental-refresh.md) estiver configurado, porque é mais rápida e confiável e consome menos recursos.

A carga inicial do relatório de grandes conjuntos de dados pode levar muito tempo se ele já passou algum tempo desde a última vez em que o conjunto de dados foi usado. Uma barra de carregamento para relatórios demorados exibe o progresso do carregamento.

Enquanto as restrições de tempo e memória por consulta são muito maiores na capacidade Premium, é recomendável que usar filtros e segmentações de dados para limitar os visuais para exibir apenas o que é necessário.

## <a name="incremental-refresh"></a>Atualização incremental

Atualização incremental fornece uma parte integral de ter e manutenção de grandes conjuntos de dados no Power BI Premium. Atualização incremental traz muitos benefícios, por exemplo, as atualizações são mais rápidas porque somente os dados que tenha alterado deve ser atualizada. As atualizações são mais confiáveis porque não é necessário manter as conexões de longa execução a fontes de dados voláteis. Consumo de recursos é reduzido porque menos dados para atualizar reduz o consumo geral de memória e outros recursos. Políticas de atualização incremental são definidas no **Power BI Desktop**e aplicados quando publicados em um espaço de trabalho em uma capacidade Premium. 

![Detalhes da atualização](media/service-premium-incremental-refresh/refresh-details.png)

Para obter mais informações, consulte [Incremental de atualização no Power BI Premium](service-premium-incremental-refresh.md).

## <a name="paginated-reports"></a>Relatórios paginados

Relatórios paginados, tem suportados em P1-P3 A4_A6 SKUs e, se baseiam na tecnologia de linguagem de definição de relatório (RDL) do SQL Server Reporting Services. Embora baseado na tecnologia RDL, não é o mesmo que o servidor de relatório do Power BI, que é uma plataforma de relatório que pode ser baixada, que você pode instalar localmente, também é incluído com o Power BI Premium. Relatórios paginados são formatados para se ajustar bem a uma página que pode ser impresso ou compartilhada. Dados são exibidos em uma tabela, mesmo se a tabela abrange várias páginas. Usando a versão gratuita [ **construtor de relatórios do Power BI** ](https://go.microsoft.com/fwlink/?linkid=2086513) aplicativo de área de trabalho do Windows, autor de usuários paginado relatórios e publicá-los para o serviço.

No Power BI Premium, os relatórios de Paginated são uma carga de trabalho que deve ser habilitada para uma capacidade por meio do portal de administração. Os administradores de capacidade podem habilitar e, em seguida, especifique a quantidade de memória como uma porcentagem geral da capacidade recursos de memória. Ao contrário de outros tipos de cargas de trabalho, o Premium é executado relatórios paginados em um espaço contido dentro da capacidade. O máximo de memória especificado para esse espaço é usado se a carga de trabalho está ativa. O padrão é 20%. 

Para obter mais informações, consulte [relatórios no Power BI Premium paginados](paginated-reports-report-builder-power-bi.md). Para saber mais sobre como habilitar a carga de trabalho Paginated relatórios, consulte [configurar cargas de trabalho](service-admin-premium-workloads.md).

## <a name="power-bi-report-server"></a>Servidor de Relatórios do Power BI
 
Incluído com o com o Power BI Premium, o servidor de relatório do Power BI é um *locais* servidor de relatório com um portal da web. Você pode criar seu BI ambiente local e distribua relatórios protegidos pelo firewall da sua organização. Servidor de relatório fornece aos usuários acesso interativa avançada e recursos de relatório empresarial do SQL Server Reporting Services. Os usuários podem explorar dados visuais e descubram rapidamente padrões para melhor, tomar decisões mais rápidas. Servidor de relatório fornece governança em seus próprios termos. Se e quando chega o momento, o servidor de relatório do Power BI facilita a migração para a nuvem, em que sua organização pode aproveitar ao máximo de todas as funcionalidades do Power BI Premium.

Para obter mais informações, consulte [Power BI Report Server](report-server/get-started.md).

## <a name="unlimited-content-sharing"></a>Compartilhamento de conteúdo ilimitado

Com o Premium, qualquer pessoa, independentemente de estarem dentro ou fora da sua organização pode exibir conteúdo do Power BI, incluindo relatórios paginados e interativos sem precisar adquirir licenças individuais. 

![Compartilhamento de conteúdo](media/service-premium-what-is/premium-sharing.png)

Premium permite que a ampla distribuição de conteúdo por usuários Pro sem a necessidade de licenças Pro para os destinatários que exibam o conteúdo. Licenças Pro são necessárias para criadores de conteúdo. Criadores de se conectar a fontes de dados, dados de modelo e criar relatórios e painéis que são empacotados como aplicativos de espaço de trabalho. 

Para obter mais informações, consulte [licenciamento do Power BI](service-admin-licensing-organization.md).

## <a name="tool-connectivity-preview"></a>Conectividade da ferramenta (versão prévia)

Nos bastidores, a empresa comprovada da Microsoft **mecanismo Vertipaq do Analysis Services** habilita os conjuntos de dados do Power BI. O Analysis Services fornece a capacidade de programação e suportam de ferramenta e aplicativo cliente por meio de bibliotecas de cliente e APIs que dão suporte ao protocolo padrão aberto XMLA. Atualmente, dá suporte a conjuntos de dados do Power BI Premium *somente leitura* operações da Microsoft e aplicativos cliente de terceiros e de ferramentas por meio do **pontos de extremidade XMLA**. 

Ferramentas da Microsoft, como o SQL Server Management Studio e SQL Server Profiler e aplicativos de terceiros, como o Studio de DAX e aplicativos de visualização de dados, podem se conectar e consultar conjuntos de dados Premium usando o XMLA, DAX, MDX, DMVs e rastreamento de eventos. 

![SSMS](media/service-premium-what-is/connect-tools-ssms-dax.png)

Para obter mais informações, consulte [conectar-se a conjuntos de dados com ferramentas e aplicativos cliente](service-premium-connect-tools.md).

## <a name="acknowledgements"></a>Confirmações

Peter Myers, MVP de plataforma de dados e independente profissional de BI com [bit a bit soluções](https://www.bitwisesolutions.com.au/), e o Microsoft Power BI consultoria ao cliente Team (CAT) são os principais colaboradores a este artigo.

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Gerenciando as capacidades Premium](service-premium-capacity-manage.md)

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||
