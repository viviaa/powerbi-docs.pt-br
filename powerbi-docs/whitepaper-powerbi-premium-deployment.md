---
title: Implantando e gerenciando capacidades de Power BI Premium
description: Entenda o potencial do Power BI Premium e aprenda a projetar, implantar, monitorar e solucionar problemas de soluções escalonáveis.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 03/06/2019
LocalizationGroup: Premium
ms.openlocfilehash: 783f82ecd5c6dea5c26b096b8b1bfcffe388864b
ms.sourcegitcommit: 012f05efc4e97aeb6178fb2fc820b73bcc1ce920
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68391458"
---
# <a name="deploying-and-managing-power-bi-premium-capacities"></a>Implantando e gerenciando capacidades de Power BI Premium

**Resumo:** O Power BI Premium fornece um desempenho mais consistente, suporte para grandes volumes de dados e a flexibilidade de um autoatendimento unificado e plataforma de BI empresarial para todos em sua organização. Este white paper técnico de nível 300 foi escrito especificamente para administradores de Power BI, além de autores e editores de conteúdo. Ele visa ajudá-los a entender o potencial do Power BI Premium e explicar como projetar, implantar, monitorar e solucionar problemas de soluções escalonáveis.

**Autorização** [Peter Myers](https://www.linkedin.com/in/peterjsmyers) (MVP de plataforma de dados e especialista independente de BI com soluções bit a bit)

**Revisores técnicos:** Adam Saxton, Akshai Mirchandani, Bhavik comerciante, David Magar, Josh Caplan, Michael Blythe, Nimrod Shalit, Olivier Matrat, Swati Gupta

**Aplica-se a:** Serviço do Power BI, Power BI Premium e capacidades de Power BI Embedded do Azure

> [!NOTE]
> Você pode salvar ou imprimir este whitepaper selecionando **Imprimir** no seu navegador e, em seguida, selecionando **Salvar como PDF**.

## <a name="introducing-power-bi"></a>Apresentando o Power BI

O Power BI é um serviço de análise de negócios projetado para fornecer informações que permitem decisões rápidas e informadas. Desde seu lançamento no 2015, ele se tornou rapidamente um serviço popular usado para fornecer soluções para o menor das organizações para as maiores empresas.

Ele é disponibilizado de duas maneiras: Como um serviço de nuvem e como uma solução de relatório local chamada **servidor de relatórios do Power bi**. \[[uma](#endnote-01)\]

Power BI como um serviço de nuvem é o software como um serviço (SaaS) \[ [2](#endnote-02)\]. Ele representa um conjunto de serviços e aplicativos que permitem que as organizações desenvolvam, implantem, gerenciem, compartilhem soluções para monitorar seus negócios.

Não é a intenção deste White Paper fornecer uma descrição abrangente do serviço do Power BI. Em vez disso, ele se concentra em tópicos relevantes ao assunto de Power BI Premium. Para obter informações gerais sobre Power BI, consulte a documentação abrangente do [Power bi](service-admin-premium-multi-geo.md). Para obter uma explicação mais detalhada do serviço do Power BI com foco na obtenção de implantações empresariais com bom desempenho, consulte o White paper sobre [planejamento abrangente de uma Power bi de implantação empresarial](https://aka.ms/pbienterprisedeploy) .

No contexto do assunto deste whitepaper, esta seção apresenta e descreve as capacidades, Power BI tipos de conteúdo, modos de armazenamento de modelo e licenciamento. Uma compreensão desses tópicos é essencial para implantar e gerenciar com êxito Power BI Premium.

### <a name="capacities"></a>Capacidades

As **capacidades** são um conceito de Power bi básica que representa um conjunto de recursos (armazenamento, processador e memória) usados para hospedar e entregar Power bi conteúdo. As capacidades são compartilhadas ou dedicadas. Uma **capacidade compartilhada** é compartilhada com outros clientes da Microsoft, enquanto uma **capacidade dedicada** é totalmente comprometida com um único cliente. As capacidades dedicadas são introduzidas no tópico [capacidades Premium](#premium-capacities) .

Na capacidade compartilhada, as cargas de trabalho são executadas em recursos computacionais compartilhados com outros clientes. Como a capacidade deve compartilhar recursos, as limitações são impostas para garantir a "atividade justa", como o tamanho máximo do modelo (1 GB) e a frequência máxima de atualização diária (oito vezes por dia).

### <a name="workspaces"></a>Workspaces

Os espaços de trabalho Power BI residem em capacidades e representam contêineres de segurança, colaboração e implantação. Cada usuário do Power BI tem um workspace pessoal, conhecido como **Meu workspace**. Workspaces adicionais podem ser criados para habilitar a colaboração e a implantação. Eles são conhecidos como **Workspaces do Aplicativo**. Por padrão, espaços de trabalho-incluindo espaços de trabalho pessoais – são criados na capacidade compartilhada.

### <a name="power-bi-content-types"></a>Tipos de conteúdo de Power BI

Para apresentar Power BI Premium tópicos, é importante começar com uma discussão completa sobre a arquitetura de Power BI, incluindo tipos de conteúdo fundamentais.

Todo o conteúdo de Power BI é armazenado e gerenciado em espaços de trabalho que são contêineres para Power BI conteúdo. Cada usuário Power BI tem seu próprio espaço de trabalho pessoal, mas a prática recomendada geral é criar espaços de trabalho de aplicativo. Os espaços de trabalho de aplicativo permitem a copropriedade de conteúdo e a capacidade de colaborar com o conteúdo. Eles também fornecem a capacidade de preparar e distribuir conteúdo para grandes audiências como aplicativos.

O conteúdo de Power BI a seguir é armazenado em espaços de trabalho:

- Fluxos de dados
- Conjuntos de dados
- Pastas de trabalho
- Relatórios
- Dashboards

#### <a name="dataflows"></a>Fluxos de dados

Power BI Dataflows ajudam as organizações a unificarem dados de fontes diferentes. Eles podem ser considerados como dados preparados e preparado para uso em modelos, no entanto, não podem ser usados diretamente como uma fonte para relatórios. Eles aproveitam a ampla coleção de conectores de dados da Microsoft, permitindo a ingestão de dados de fontes de dados locais e baseadas em nuvem.

Os fluxos de dados só podem ser criados e gerenciados em espaços de trabalho de aplicativo e são armazenados como entidades no Common Data Service (CDM) no Azure Data Lake Storage Gen2. Normalmente, eles são agendados para atualização em uma base recorrente para armazenar dados atualizados.

Para obter mais informações, consulte a [preparação de dados de autoatendimento no documento Power bi (versão prévia)](service-dataflows-overview.md) .

#### <a name="datasets"></a>Conjuntos de dados

Power BI DataSets representam uma fonte de dados prontos para relatórios e visualização. Há muitos tipos de conjuntos de valores, criados por:

- Conectando-se a um modelo de dados existente que não está hospedado em uma capacidade de Power BI
- Carregando um arquivo de Power BI Desktop que contém um modelo
- Carregando uma pasta de trabalho do Excel (contendo uma ou mais tabelas do Excel e/ou um modelo de dados de pasta de trabalho) ou carregando um arquivo CSV (valores separados por vírgulas)
- Usando o serviço do Power BI para criar um conjunto de fluxos de transmissão por push, streaming ou híbrido

Exceto para os conjuntos \[de dados de streaming [3](#endnote-03)\], o DataSet representa um modelo que aproveita as tecnologias de modelagem maduras do Analysis Services.

Observe que na documentação, às vezes as terminologias e os modelos de conjuntos de valores são intercambiáveis. Em geral, de um serviço do Power BI perspectiva, ele é conhecido como um **conjunto** de uma perspectiva de desenvolvimento, que é conhecido como um **modelo**. No contexto deste White Paper, eles significam muito a mesma coisa.

##### <a name="externally-hosted-models"></a>Modelos hospedados externamente

Conectar-se a um modelo hospedado externamente envolve a instalação do [Gateway de dados local](service-gateway-onprem.md) para se conectar ao SQL Server Analysis Services, seja no local ou na infraestrutura como serviço (IaaS) hospedada pela VM. Azure Analysis Services não requer um gateway. Esse cenário geralmente faz sentido quando existem investimentos de modelo existentes, normalmente formando parte do data warehouse empresarial (EDW). Ele permite que Power BI execute uma **conexão dinâmica** (LC) para Analysis Services e faz isso impondo permissões de dados usando a identidade do usuário de relatório Power bi. Por SQL Server Analysis Services, há suporte para modelos multidimensionais (cubos) e modelos de tabela. Conforme mostrado na imagem a seguir, um conjunto de ativos de conexão dinâmica passa consultas para modelos hospedados externamente.

![Um conjunto de ativos de conexão dinâmica passa consultas para modelos hospedados externamente](media/whitepaper-premium-deployment/live-connection-dataset.png)

##### <a name="power-bi-desktop-developed-models"></a>Modelos desenvolvidos pelo Power BI Desktop

Power BI Desktop-um aplicativo cliente destinado ao desenvolvimento de Power BI-pode ser usado para desenvolver um modelo que é efetivamente um modelo de tabela de Analysis Services. Os modelos podem ser desenvolvidos importando dados de fluxos de dados, que podem ser integrados a outras fontes. Embora as informações específicas sobre como a modelagem possa ser obtida estejam fora do escopo deste White Paper, é importante entender que há três tipos ou modos diferentes de modelos que podem ser desenvolvidos usando Power BI Desktop. Esses modos determinam se os dados são importados para o modelo ou se eles permanecem na fonte de dados. Os três modos são: Importar, DirectQuery e composto. Uma discussão completa de cada modo será abordada no tópico [modos de armazenamento de modelo](#model-storage-modes) .

Modelos e modelos hospedados externamente desenvolvidos em Power BI área de trabalho podem impor a RLS (segurança em nível de linha) para limitar os dados que podem ser recuperados para um determinado usuário. Por exemplo, os usuários atribuídos ao grupo de segurança vendedores só podem exibir dados de relatório para as regiões de vendas às quais eles são atribuídos. As funções RLS podem ser dinâmicas ou estáticas. As **funções dinâmicas** são filtradas pelo usuário do relatório, enquanto as **funções estáticas** aplicam os mesmos filtros para todos os usuários atribuídos à função.

##### <a name="excel-workbook-models"></a>Modelos de pasta de trabalho do Excel

Criar conjuntos de resultados com base em pastas de trabalho do Excel ou arquivos CSV resultará na criação automática de um modelo. As tabelas do Excel e os dados CSV serão importados para criar tabelas de modelo, enquanto um modelo de dados de pasta de trabalho do Excel será transpodo para criar um modelo de Power BI. Em todos os casos, os dados de arquivo são importados para um modelo.

As distinções, em seguida, podem ser feitas sobre Power BI conjuntos de valores que representam modelos:

- Eles são hospedados na serviço do Power BI ou são hospedados externamente pelo Analysis Services
- Eles podem armazenar dados importados ou podem emitir solicitações de consulta de passagem para fontes de dados subjacentes ou uma combinação de ambos

Aqui está um resumo dos fatos importantes sobre Power BI conjuntos de valores que representam modelos:

- SQL Server Analysis Services modelos hospedados exigem um gateway para executar consultas de LC
- Modelos hospedados Power BI que importam dados
  - Deve ser totalmente carregado na memória para que possa ser consultado
  - Exigir atualização para manter os dados atuais e deve envolver gateways quando os dados de origem não estiverem acessíveis diretamente pela Internet
- Os modelos hospedados Power BI que usam o modo de armazenamento do DirectQuery (DQ) exigem conectividade com os dados de origem. Quando o modelo é consultado, Power BI emite consultas para os dados de origem para recuperar os dados atuais. Esse modo deve envolver gateways quando os dados de origem não estão acessíveis diretamente pela Internet.
- Os modelos podem impor regras RLS, impondo filtros para limitar o acesso a dados a determinados usuários

Para implantar e gerenciar com êxito Power BI Premium, é importante entender onde os modelos são hospedados, seu modo de armazenamento, quaisquer dependências em gateways, o tamanho dos dados importados e o tipo de atualização e a frequência. Todos eles podem ter um impacto significativo sobre os recursos de Power BI Premium. Além disso, o próprio design do modelo, incluindo suas consultas de preparação de dados e cálculos, pode ser adicionado à combinação de considerações.

Também é importante entender que os modelos de importação hospedados pelo Power BI podem ser atualizados de acordo com o agendamento ou ser disparados sob demanda por um usuário na serviço do Power BI.

A criação de modelos otimizados é discutida posteriormente neste documento técnico no tópico [otimizando modelos](#optimizing-models) .

#### <a name="workbooks"></a>Pastas de trabalho

Power bi pastas de trabalho são um tipo \[de conteúdo de Power bi [4](#endnote-04)\]. Elas são pastas de trabalho do Excel que foram carregadas no serviço do Power BI e não devem ser confundidas com pastas de trabalho do Excel carregadas que criam conjuntos de os (modelos). O tipo de conteúdo da pasta de trabalho representa uma conexão com uma pasta de trabalho, que pode ser carregada para a serviço do Power BI ou permanecer no armazenamento em nuvem no OneDrive ou no SharePoint Online.

É importante entender que esse tipo de conteúdo não está disponível como uma fonte de dados para Power BI visualizações de dados. Em vez disso, ele pode ser aberto como uma pasta de trabalho no serviço do Power BI usando o Excel online. A principal intenção desse tipo de conteúdo é permitir que os relatórios herdados da pasta de trabalho do Excel sejam acessíveis no serviço do Power BI e para permitir que suas visualizações de dados sejam fixadas em painéis de Power BI.

Para obter mais informações, consulte o documento [obter dados de arquivos de pasta de trabalho do Excel](service-excel-workbook-files.md) .

#### <a name="reports"></a>Relatórios

Há dois tipos de relatórios: Power BI relatórios e relatórios paginados.

Os **relatórios de Power bi** fornecem uma experiência de visualização de dados interativa que se conecta a apenas um único conjunto. Geralmente, os relatórios são projetados para incentivar a participação do usuário, permitindo que eles interajam com uma variedade extraordinária de recursos, incluindo filtragem, divisão, filtragem cruzada e realce, Drill up, busca detalhada, detalhamento, p & um natural questionamento de idioma, foco, navegação de página, destaque, indicadores de exibição e muito mais.

No contexto deste White Paper, é importante entender como a arquitetura de Power BI, Power BI design de relatório e as interações de usuário podem afetar os recursos de serviço do Power BI:

- Para carregar e interagir com relatórios com base em modelos de importação, o modelo deve ser totalmente carregado na memória (se hospedado no serviço do Power BI ou hospedado externamente)
- Cada visual de relatório emite uma consulta para recuperar dados consultando o modelo
- Em geral, as interações de filtro e segmentação envolvem consultar o modelo. Por exemplo, alterar uma seleção de segmentação de texto – por padrão, exigirá o recarregamento de cada \[Visual na página [5](#endnote-05)\]
- Power BI relatórios não garantem a exibição dos dados atuais e podem exigir que o usuário atualize o relatório para recarregar a página de relatório e seus visuais
- Os usuários podem se envolver com o Q & um recurso de linguagem natural para fazer perguntas, fornecendo ao design de relatório de Power BI permite que ele e o conjunto de dados representem um modelo de importação de dado hospedado por Power BI ou um conjunto de dados LC configurado para habilitar a p & A

**Relatórios** paginados que permitem a publicação e renderização de relatórios do SQL Server Reporting Services (\*SSRS) (formato. RDL). Como o nome sugere, os relatórios paginados são normalmente usados quando os requisitos determinam a necessidade de impressão em um tamanho de página fixo ou quando há listas de dados variáveis que devem ser totalmente expandidas. Por exemplo, uma fatura criada para renderização de várias páginas (em vez de rolagem dentro de um Visual) e impressão.

Os dois tipos de relatório com suporte fornecem opções para autores de relatório, permitindo que eles selecionem o tipo com base nos requisitos e no uso pretendido. Em geral, Power BI relatórios são ideais para experiências interativas, permitindo que o usuário Explore e descubra informações de dados, enquanto os relatórios paginados são mais adequados para layouts de página controlados por parâmetros.

Independentemente do tipo de relatório, a obtenção de atualizações de dados e de carga de relatório responsivas (quando filtros ou parâmetros são alterados) é imperativa para fornecer uma experiência de usuário confiável e de bom desempenho.

#### <a name="dashboards"></a>Dashboards

Os painéis de Power BI destinam-se a fornecer experiências de monitoramento e são conceitualmente muito diferentes dos relatórios Power BI. Os painéis são projetados para exibição em um único painel para valores expressos e visualizações de dados em blocos. Geralmente, os painéis oferecem menos experiências de interação do que Power BI relatórios, com alguns designs de Dashboard que não esperam nenhuma interação. Por exemplo, um painel autônomo apresentado em uma tela não sensível ao toque em uma sala de servidor. Outra diferença significativa é que os painéis podem apresentar blocos que são dados de origem de vários conjuntos, enquanto um relatório de Power BI só pode ser baseado em um único conjunto.

É importante entender que um painel foi projetado para carregar rapidamente e expressar os dados mais atuais (conhecidos para o serviço do Power BI) em todos os momentos. Ele consegue isso armazenando em cache os resultados da consulta de bloco e faz isso para cada painel. Na verdade, ele deve fazer isso para cada usuário que tem acesso a um Dashboard baseado em modelos que impõem a RLS dinâmica.

O serviço do Power BI atualiza automaticamente os caches de consulta do painel imediatamente após a atualização de modelos de importação hospedados pelo Power BI. No caso dos modelos LC e DQ, o proprietário do conjunto de um tem um grau de controle sobre a frequência com que o serviço do Power BI atualiza o cache, que pode ser configurado com a frequência a cada 15 minutos ou com pouca frequência como uma semana. Observe que as atualizações de cache de consulta LC primeiro consultarão os metadados do modelo para determinar se uma atualização do modelo ocorreu desde a última atualização do cache e não continuará atualizando o cache quando uma atualização não tiver ocorrido. Essa verificação não é possível para modelos do DQ e, portanto, as atualizações de cache ocorrerão independentemente de os dados de origem terem sido alterados ou não.

As atualizações de cache de consulta de painel baseadas em modelos de DQ e de LC podem impactar significativamente em serviço do Power BI recursos e fontes de dados externas. Considere um painel com 20 blocos, tudo com base em um modelo de Azure Analysis Services que impõe a RLS dinâmica e que é atualizado a cada hora e que esse painel é compartilhado com 100 usuários. Se o conjunto de resultados estiver configurado para atualizar a cada hora, isso resultaria em pelo menos 2000 (20 x 100) consultas de LC. Isso pode fazer uma enorme carga no serviço do Power BI e nas fontes de dados externas e também pode exceder os limites impostos sobre os recursos disponíveis. Os limites e recursos de capacidade são descritos no tópico [nós de capacidade](#capacity-nodes) .

Os usuários podem interagir com um painel de várias maneiras, o que exige serviço do Power BI recursos. Especificamente, eles podem:

- Disparar uma atualização de blocos de painéis, o que pode resultar em uma atualização sob demanda de todos os modelos de importação de dados relacionados ao Power BI hospedados
- Entre em contato com o p & um recurso de linguagem natural para fazer perguntas (fornecendo ao design do painel permite que ele e o conjunto de dados seja um modelo de importação de dado Power BI hospedado ou um conjunto de dados LC configurado para habilitar a p & A)
- Use o recurso Insights Rápidos para que Power BI descubra informações de um conjunto de dados subjacente e responda com elementos visuais que exibem e os descrevem (fornecendo que o bloco se baseia em um conjunto de dados que é um modelo de importação de dado Power BI hospedado)
- Configure alertas em blocos de painel, exigindo que os serviço do Power BI comparam os limites com valores de bloco, possivelmente com frequência de cada hora e para notificar os usuários quando os limites forem excedidos (desde que o bloco exiba um único valor numérico e seja baseado em um DataSet Power BI modelo de importação de dados hospedado)

### <a name="model-storage-modes"></a>Modos de armazenamento de modelo

Lembre-se de que Power BI Desktop permite desenvolver um modelo em um dos três modos. É importante entender a lógica para cada modo de armazenamento de modelo de dados e possíveis impactos sobre serviço do Power BI recursos. Esta seção apresenta todos os três modos. Eles serão discutidos em mais detalhes posteriormente neste white paper no tópico otimizando modelos.

#### <a name="import-mode"></a>Modo de importação

O modo de importação é o modo mais comum usado para desenvolver modelos devido ao desempenho extremamente rápido associado à consulta na memória, à flexibilidade de design disponível aos modeladores e ao suporte a recursos específicos de serviço do Power BI (Q & A, Insights Rápidos , etc.). É o modo padrão ao criar uma nova solução de Power BI Desktop.

É importante entender que os dados importados são sempre armazenados em disco e devem ser totalmente carregados na memória para serem consultados ou atualizados. Uma vez na memória, os modelos de importação obtêm resultados de consulta incrivelmente rápidos. Também é importante entender que não há nenhum conceito de um modelo de importação sendo parcialmente carregado na memória.

Quando atualizados, os dados são compactados e otimizados e armazenados em disco pelo mecanismo de armazenamento VertiPaq. Quando carregado do disco na memória, é possível ver a compactação de 10 vezes e, portanto, é razoável esperar que 10 GB de dados de origem possam ser compactados em aproximadamente 1 GB de tamanho. O tamanho do armazenamento no disco pode atingir uma redução de 20% sobre isso. \[[6](#endnote-06)\]

A flexibilidade de design pode ser Obtida de três maneiras. Os modeladores de dados podem:

- Integre dados armazenando dados em cache de várias fontes de dados – independentemente do tipo e do formato da fonte de dados
- Aproveite o conjunto inteiro de Power Query linguagem de fórmula (informalmente chamado de M) ao criar consultas de preparação de dados
- Aproveite o conjunto inteiro de funções DAX (Data Analysis Expressions) ao aprimorar o modelo com a lógica de negócios, obtida com colunas calculadas, tabelas e medidas calculadas

Conforme mostrado na imagem a seguir, um modelo de importação pode integrar dados de qualquer número de tipos de fonte de dados com suporte.

![Um modelo de importação pode integrar dados de qualquer número de tipos de fonte de dados com suporte](media/whitepaper-premium-deployment/import-model.png)

No entanto, embora haja vantagens atraentes associadas a modelos de importação, também há desvantagens:

- Todo o modelo deve ser carregado na memória antes que Power BI possa consultar o modelo, o que pode fazer a pressão nos recursos disponíveis à medida que o número e o tamanho dos modelos crescem
- Os dados de modelo são apenas o atual como a atualização mais recente e, portanto, os modelos de importação precisam ser atualizados, preferencialmente de forma programada
- Uma atualização completa removerá todos os dados de todas as tabelas e os recarregará da fonte de dados. Isso pode ser muito caro em termos de tempo e recursos para o serviço do Power BI e as fontes de dados. O Power BI tem suporte para atualização incremental, o que pode evitar truncar e recarregar tabelas inteiras, e isso é abordado no tópico [otimizando modelos hospedados Power bi](#optimizing-power-bi-hosted-models) .

Da perspectiva de um recurso serviço do Power BI, os modelos de importação exigem:

- Memória suficiente para carregar o modelo quando ele é consultado ou atualizado
- Processamento de recursos e recursos de memória adicionais para atualizar dados

#### <a name="directquery-mode"></a>Modo DirectQuery

Modelos desenvolvidos no modo DirectQuery (DQ) não importam dados. Em vez disso, eles consistem apenas em metadados que, quando consultado, emite consultas nativas para a fonte de dados subjacente.

![Um modelo DirectQuery emite consultas nativas para a fonte de dados subjacente](media/whitepaper-premium-deployment/direct-query-model.png)

Há dois motivos principais para considerar o desenvolvimento de um modelo do DQ. O primeiro motivo é quando os volumes de dados são muito grandes-mesmo quando os métodos de redução de dados são aplicados – para carregar em um modelo ou praticamente atualizar. A segunda razão é quando relatórios e painéis precisam fornecer dados "quase em tempo real", além do que pode ser obtido dentro dos limites de atualização agendada (48 vezes por dia para uma capacidade dedicada).

Há várias vantagens associadas aos modelos do DQ:

- Os limites de tamanho do modelo de importação não se aplicam
- Os modelos não exigem atualização
- Os usuários de relatório verão os dados mais recentes ao interagir com segmentações e filtros de relatório e poderão atualizar o relatório inteiro para recuperar os dados atuais
- Os blocos de painel, quando baseados em modelos do DQ, podem ser atualizados automaticamente com a frequência a cada 15 minutos

No entanto, há várias desvantagens e limitações associadas aos modelos do DQ:

- O modelo deve ser baseado em uma única fonte de dados com suporte e, portanto, qualquer integração de dados já deve ser obtida na fonte de dados. As fontes de dados com suporte são sistemas relacionais e analíticos, com suporte para \[muitos armazenamentos de dados populares [7](#endnote-07)\].
- O desempenho pode ser lento, causando impacto negativo no serviço do Power BI (as consultas podem ser com uso intensivo de CPU) e na fonte de dados (que pode não ser otimizada para consultas analíticas)
- Power Query consultas não podem ser excessivamente complexas e são limitadas a expressões e funções M que podem ser transpostas a consultas nativas compreendidas pela fonte de dados
- As funções DAX são limitadas àquelas que podem ser transpostas a consultas nativas compreendidas pela fonte de dados, e não há suporte para tabelas calculadas ou funcionalidades de inteligência de tempo internas
- Por padrão, as consultas de modelo que exigem a recuperação de mais de 1 milhão linhas falharão
- Relatórios e painéis com vários visuais podem exibir resultados inconsistentes, especialmente quando a fonte de dados é volátil
- P & A e Insights Rápidos não têm suporte

Da perspectiva de um recurso serviço do Power BI, os modelos do DQ exigem:

- Memória mínima para carregar o modelo (somente metadados) quando ele é consultado
- Às vezes, os recursos significativos do processador para gerar e processar consultas enviadas à fonte de dados

Para obter mais informações, consulte o documento [usar a consulta direta no Power bi desktop](desktop-use-directquery.md) .

#### <a name="composite-mode"></a>Modo composto

Modelos desenvolvidos no modo composto permitem configurar o modo de armazenamento para tabelas de modelo individuais. Portanto, ele dá suporte a uma combinação de tabelas de importação e DQ. Ele também dá suporte a tabelas calculadas (definidas com DAX) e várias fontes de dados do DQ.

O modo de armazenamento de tabela pode ser configurado como importação, DirectQuery ou duplo. Uma tabela configurada como modo de armazenamento duplo é tanto importação quanto DirectQuery, e isso permite que o serviço do Power BI determine o modo mais eficiente a ser usado em uma consulta por consulta.

![Um modelo composto é uma combinação de modos de importação e de armazenamento do DQ, configurados em nível de tabela](media/whitepaper-premium-deployment/composite-model.png)

Os modelos compostos se esforçam para fornecer o melhor dos modos de importação e DirectQuery. Quando configurados adequadamente, eles podem combinar alto desempenho de consulta de modelos na memória com a capacidade de recuperar dados quase em tempo real de fontes de dados.

Os modeladores de dados que desenvolvem modelos compostos provavelmente configuram tabelas de tipo de dimensão no modo de importação ou de armazenamento duplo e em tabelas de tipo de fato no modo DirectQuery. Por exemplo, considere um modelo com uma tabela de tipo de dimensão de produto em modo duplo e uma tabela de tipo de fato de vendas no modo DirectQuery. A tabela Product pode ser eficiente e rapidamente consultada da na memória para renderizar uma segmentação de relatório. Em seguida, a tabela Sales pode ser consultada no modo DirectQuery Unido à tabela Product relacionada. A última consulta pode habilitar a geração de uma única consulta nativa eficiente para unir tabelas de produtos e vendas e filtrar pelos valores de segmentação.

Em geral, as vantagens e desvantagens, associadas a cada modo de modelo, podem ser consideradas para serem aplicadas ao modo de armazenamento de tabela em modelos compostos.

Para obter mais informações, consulte o documento [usar modelos compostos no Power bi desktop](desktop-composite-models.md) .

### <a name="licensing"></a>Licenciamento

Power BI tem três licenças:

- Power BI Gratuito
- Power BI Pro
- Power BI Premium

O **Power bi licença gratuita** permite que um indivíduo entre no serviço do Power bi e trabalhe em seu espaço de trabalho pessoal publicando modelos e relatórios. É importante entender que não é possível compartilhar Power BI conteúdo usando essa licença. Essa licença, como seu nome sugere, é gratuita.

A licença de **Power bi pro** permite que um indivíduo crie e colabore em espaços de trabalho de aplicativo e Compartilhe e distribua Power bi conteúdo. Eles também podem configurar a atualização para seus conjuntos de dados para manter automaticamente o data atual, incluindo as fontes de dados locais. Além disso, eles podem auditar e determinar como os dados são acessados e usados. Essa licença é necessária para receber conteúdo compartilhado de outras pessoas, a menos que o usuário esteja associado a uma Power BI Premium capacidade dedicada.

A licença de **Power bi Premium** é uma licença de nível de locatário e é discutida na seção [introdução Power bi Premium](#introducing-power-bi-premium) .

Para obter mais informações sobre o licenciamento do Power BI, consulte a página de [preços do Power bi](https://powerbi.microsoft.com/pricing/) .

## <a name="introducing-power-bi-premium"></a>Introdução ao Power BI Premium

O Power BI Premium fornece uma plataforma unificada de BI e de autoatendimento com escala, desempenho confiável e custos previsíveis. Ele, principalmente, realiza isso fornecendo recursos dedicados para executar o serviço do Power BI para sua organização.

Além disso, Power BI Premium fornece muitos recursos corporativos:

- Distribuição de conteúdo econômica, permitindo o compartilhamento de conteúdo de Power BI para usuários ilimitados Power BI gratuitos, incluindo usuários externos
- Suporte para tamanhos \[maiores de DataSet [8](#endnote-08)\]
- Taxas de atualização mais altas de fluxos de data e conjuntos de data (até 48 vezes por dia)
- Atualização incremental de fluxos de os e conjuntos de os
- Entidades vinculadas de Dataflow e execução paralela de transformações
- Relatórios paginados
- Servidor de Relatórios do Power BI, para relatórios locais
- Capacidade de inserir conteúdo em aplicativos em nome dos usuários do aplicativo (PaaS)

Muitos desses recursos podem ser aproveitados para fornecer soluções corporativas eficientes e escalonáveis e são abordados na seção [otimizando capacidades Premium](#optimizing-premium-capacities) .

### <a name="subscriptions-and-licensing"></a>Assinaturas e licenciamento

O Power BI Premium é uma assinatura do Office 365 de nível de locatário disponível em duas famílias de SKU (Unidade de Manutenção de Estoque):

- Em SKUs (EM1-EM3) para inserção, exigindo um compromisso anual, cobrado mensalmente
- **P** SKUs (P1-P3) para inserção e recursos empresariais, exigindo um compromisso mensal ou anual, cobrado mensalmente e inclui uma licença para instalar servidor de relatórios do Power bi local

Uma abordagem alternativa é comprar uma assinatura de Power BI Embedded do Azure que tenha uma única família de SKUs: **SKUs (** a1-a6) para inserção e somente para fins de teste de capacidade.

Todos os SKUs fornecem núcleos de v para criar \[capacidades [9](#endnote-09)\], mas os SKUs em são restritos para inserção de escala menor. Embora o foco deste White Paper seja nas SKUs do P, grande parte do que é discutido também é relevante também para as SKUs.

Em contraste com os SKUs da assinatura Premium, os SKUs do Azure não exigem nenhum compromisso de tempo e são cobrados por hora. Eles oferecem elasticidade total que permite aumentar e reduzir, pausar, retomar e excluir.

O Azure Power BI Embedded está basicamente fora do escopo deste White Paper, mas é discutido no tópico abordagens de teste como uma opção prática e econômica para testar e medir cargas de trabalho.

Para obter mais informações sobre os SKUs do Azure, consulte a [documentação de Power bi Embedded do Azure](/azure/power-bi-embedded/).

As assinaturas do Power BI Premium são compradas por administradores no centro de administração do Microsoft 365. Especificamente, somente os administradores globais do Office 365 ou os administradores de cobrança podem comprar SKUs.

Depois de adquirido, o locatário recebe um número correspondente de núcleos virtuais para atribuir às capacidades – isso é conhecido como **pool de núcleos de v**. Por exemplo, adquirir um SKU P3 fornece ao locatário 32 núcleos virtuais.

Para obter mais informações, consulte o documento [como comprar Power bi Premium](service-admin-premium-purchase.md) .

### <a name="premium-capacities"></a>Capacidades Premium

Ao contrário de uma capacidade compartilhada em que as cargas de trabalho são executadas em recursos computacionais compartilhados com outros clientes, uma **capacidade dedicada** é para uso exclusivo de uma organização. Ele é isolado com recursos computacionais dedicados que fornecem desempenho confiável e consistente para conteúdo hospedado.

O foco deste White Paper é a **capacidade Premium** , o que significa que ele está associado a qualquer SKU de ou P.

#### <a name="capacity-nodes"></a>Nós de Capacidade

Conforme descrito no tópico assinaturas e licenciamento, há duas famílias Power BI Premium SKU: Em e P. Todas as SKUs de Power BI Premium estão disponíveis como nós de capacidade, cada uma representando uma quantidade definida de recursos que consistem em processador, memória e armazenamento. Além dos recursos, cada SKU tem limites operacionais sobre o número de conexões do (DQ) e de conexão dinâmica (LC) por segundo e o número de atualizações de modelo paralelas.

O processamento é realizado por um número definido de núcleos virtuais, dividido igualmente entre o back-end e o front-end.

Os **núcleos virtuais de back-end** são responsáveis pela funcionalidade básica do Power BI, incluindo o processamento de consultas, o gerenciamento de cache, a execução de serviços R, a atualização de modelo, o processamento de idioma natural (P e R) e a renderização de relatórios e imagens do servidor. Os núcleos virtuais de back-end recebem uma quantidade fixa de memória que é primária usada para hospedar modelos que também são chamados de conjuntos de ativos.

Os núcleos virtuais de **front-end** são responsáveis pelo gerenciamento de documentos do serviço Web, Dashboard e relatório, gerenciamento de direitos de acesso, agendamento, APIs, uploads e downloads e, em geral, para tudo relacionado às experiências do usuário.

O armazenamento é definido como 100 TB por nó de capacidade.

Os recursos e limites de cada SKU Premium (e um SKU de tamanho equivalente) são descritos na tabela a seguir.

| Nós de Capacidade | Total de núcleos virtuais | Núcleos virtuais de back-end | RAM (GB) | Núcleos virtuais de front-end | DQ/LC (por segundo) | Paralelismo de atualização de modelo |
| --- | --- | --- | --- | --- | --- | --- |
| EM1/A1 | 1 | 0,5 | 2.5 | 0,5 | 3,75 | 1 |
| EM2/A2 | 2 | 1 | 5 | 1 | 7,5 | 2 |
| EM3/A3 | 4 | 2 | 10 | 2 | 15 | 3 |
| P1/A4 | 8 | 4 | 25 | 4 | 30 | 6 |
| P2/A5 | 16 | 8 | 50 | 8 | 60 | 12 |
| P3/A6 | 32 | 16 | 100 | 16 | 120 | 24 |
| | | | | | | |

#### <a name="capacity-workloads"></a>Cargas de trabalho de capacidade

Cargas de trabalho de capacidade são serviços disponibilizados aos usuários. Por padrão, as capacidades Premium e Azure dão suporte apenas a uma carga de trabalho de conjunto de cargas associada à execução de Power BI consultas que não podem ser desabilitadas.

As cargas de trabalho adicionais podem ser habilitadas para relatórios paginados, fluxos de os e para o ia. Cada carga de trabalho adicional requer a configuração da memória máxima (como uma porcentagem da memória total disponível) que pode ser usada pela carga de trabalho.

#### <a name="how-capacities-function"></a>Como a função capacidades

Em todos os momentos, a serviço do Power BI se esforça para fazer o melhor uso dos recursos de capacidade, sem exceder os limites impostos sobre a capacidade.

As operações de capacidade são classificadas como interativas ou em segundo plano. Operações interativas incluem a renderização de solicitações e a resposta às interações do usuário (filtragem, perguntas e respostas, consultas etc.). Em geral, a consulta de modelo de importação tem uso intensivo de recursos de memória, enquanto a consulta de modelos de LC/DQ tem uso intensivo de CPU. As operações em segundo plano incluem o fluxo de dados e as atualizações de modelo de importação, além de armazenamento em cache de consultas de dashboard.

É importante entender que as operações interativas sempre são priorizadas em operações em segundo plano para garantir a melhor experiência possível do usuário. Se houver recursos insuficientes, serão adicionadas operações em segundo plano a uma fila para processamento quando os recursos forem liberados. Operações em segundo plano, como atualizações de conjunto de informações e funções de ia, podem ser interrompidas por meio do serviço do Power BI e adicionadas a uma fila.

Os modelos de importação devem ser totalmente carregados na memória para que possam ser consultados ou atualizados. O serviço do Power BI gerencia o uso de memória usando algoritmos sofisticados para garantir o uso máximo da memória disponível e pode obter excesso de comprometimento da capacidade: Embora seja possível que uma capacidade armazene vários modelos de importação (até 100 TB por capacidade Premium), quando o armazenamento em disco combinado excede a memória com suporte (e memória adicional é necessária para consulta e atualização), elas não podem ser carregadas na memória em ao mesmo tempo.

Os modelos de importação, portanto, são carregados em-e removidos da memória de acordo com o uso. Um modelo de importação é carregado quando é consultado (operação interativa) e ainda não está na memória, ou quando é necessário atualizá-lo (operação em segundo plano).

A remoção de um modelo da memória é conhecida como **remoção** , e é uma operação que Power bi pode executar rapidamente, dependendo do tamanho dos modelos. Se a capacidade não estiver enfrentando nenhuma pressão de memória, os modelos serão simplesmente carregados na memória e permanecerão lá. \[[](#endnote-10)10\] no entanto, quando memória insuficiente estiver disponível para carregar um modelo, a serviço do Power bi precisará primeiro liberar memória. Ele libera memória detectando modelos que se tornaram inativos procurando modelos que não foram usados nos últimos três minutos \[ [11](#endnote-11)\]e, em seguida, removendo-os. Se não houver nenhum modelo inativo para remover, o serviço do Power BI buscará remover modelos carregados para operações em segundo plano. Isso pode incluir a remoção de cargas de trabalho em segundo plano, como a carga de trabalho de ia. Um último recurso, após 30 segundos de tentativas \[com falha [11](#endnote-11)\], é a falha da operação interativa. Nesse caso, o usuário de relatório é normalmente notificado de falha com uma sugestão para tentar novamente em breve.

É importante enfatizar que a remoção do conjunto de tráfego é um comportamento normal e esperado. Ela busca maximizar o uso de memória carregando e descarregando modelos cujos tamanhos combinados podem exceder a memória disponível. Isso ocorre por design e é completamente transparente para os usuários de relatório. Altas taxas de remoção não necessariamente significam que a capacidade tem recursos insuficientes. Elas poderão, contudo, tornar-se uma preocupação se a capacidade de resposta da consulta ou da atualização estiver apresentando problemas devido a altas taxas de remoção.

As atualizações dos modelos de importação são sempre intensivas de memória, pois os modelos devem ser carregados na memória e é necessária memória adicional para o processamento. Uma atualização completa pode usar aproximadamente o dobro da quantidade de memória exigida pelo modelo. Isso garante que o modelo possa ser consultado mesmo quando processado (as consultas são enviadas para o modelo existente, até que a atualização seja concluída e os novos dados de modelo estejam disponíveis). Observe que a atualização incremental exigirá menos memória e poderá ser concluída mais rapidamente e, assim, poderá reduzir substancialmente a pressão dos recursos de capacidade. As atualizações também podem fazer uso intensivo da CPU para modelos, principalmente aqueles com transformações complexas de Power Query ou colunas/tabelas calculadas que são complexas ou baseadas em grandes tabelas.

Consultas do tipo atualizações – exigem que o modelo seja carregado na memória. Se não houver memória suficiente, o serviço do Power BI tentará remover modelos inativos e, se não for possível (pois todos os modelos estão ativos), o trabalho de atualização será enfileirado. As atualizações normalmente são muito intensivas da CPU, ainda mais do que as consultas. Por esse motivo, há limites de capacidade sobre o número de atualizações simultâneas, definidos como 1,5x o número de núcleos virtuais de back-end, arredondados para cima. Se houver atualizações simultâneas demais, uma atualização agendada será enfileirada. Quando essas situações ocorrem, demora mais para a atualização ser concluída. Observe que as atualizações sob demanda (disparadas por uma solicitação de usuário ou chamada à API) serão repetidas \[ [três vezes](#endnote-11)\]e, em seguida, falharão se ainda não houver recursos suficientes.

## <a name="managing-power-bi-premium"></a>Gerenciando Power BI Premium

O gerenciamento de Power BI Premium envolve a compra de assinaturas e a criação, o gerenciamento e o monitoramento de capacidades Premium.

### <a name="creating-and-managing-capacities"></a>Criando e gerenciando capacidades

A página **configurações de capacidade** do portal de administração do **Power bi** exibe o número de núcleos virtuais adquiridos e disponíveis (ou seja, que ainda deve ser atribuído a uma capacidade) e lista as capacidades Premium. A página permite que os administradores globais do Office 365 ou administradores de serviço do Power BI criem capacidades Premium de núcleos virtuais disponíveis ou modifiquem as capacidades Premium existentes.

Ao criar uma capacidade Premium, o administrador precisa definir:

- Nome da capacidade (exclusivo dentro do locatário)
- Administrador (es) de capacidade
- Tamanho da capacidade
- Região para residência \[de dados [12](#endnote-12)\]

Pelo menos um administrador de capacidade deve ser atribuído. Os usuários atribuídos como administradores de capacidade podem:

- Atribuir espaços de trabalho à capacidade
- Gerenciar permissões de usuário para adicionar administradores de capacidade ou usuários adicionais com permissões de atribuição (para permitir que eles atribuam espaços de trabalho à capacidade)
- Gerenciar cargas de trabalho para configurar o uso máximo de memória para cargas de trabalho de relatórios paginados e fluxos de
- Reiniciar a capacidade, para redefinir todas as operações no caso de sobrecarga \[do sistema [13](#endnote-13)\]

Os administradores de capacidade não podem acessar o conteúdo do espaço de trabalho (a menos que explicitamente atribuídas permissões de espaço de trabalho) e eles não têm acesso a todas as áreas de administração de Power BI (a menos que explicitamente atribuídas), como métricas de uso, logs de auditoria É importante que os administradores de capacidade não tenham permissões para criar novas capacidades ou dimensionar as capacidades existentes. Além disso, eles são atribuídos por uma base de capacidade, garantindo que eles só possam exibir e gerenciar capacidades às quais eles são atribuídos.

O tamanho da capacidade deve ser selecionado em uma lista disponível de opções de SKU que é restrita pelo número de núcleos v disponíveis no pool. É possível criar várias capacidades do pool que podem ser originadas de uma ou mais SKUs adquiridas. Por exemplo, um SKU P3 (32 v-cores) pode ser usado para criar três capacidades: um P2 (16 núcleos) e dois P1 (2 x 8 núcleos de v). O desempenho e a escala aprimorados podem ser obtidos com a criação de capacidades de tamanho menor, e este tópico é discutido na seção [otimizando capacidades Premium](#optimizing-premium-capacities) . A imagem a seguir mostra um exemplo de configuração para a organização fictícia da Contoso que consiste em cinco capacidades Premium (3 x P1 e 2 x P3) com cada um contendo espaços de trabalho de aplicativo e vários espaços de trabalho na capacidade compartilhada.

![Um exemplo de configuração para a organização fictícia da contoso](media/whitepaper-premium-deployment/contoso-organization-example.png)

Uma capacidade Premium pode ser atribuída a uma região que não seja a região de residência do locatário do Power BI, fornecendo controle administrativo sobre quais data centers (em regiões geográficas definidas) Power BI conteúdo reside. \[[12](#endnote-12)\]

Os administradores do serviço do Power BI e os administradores globais do Office 365 podem modificar as capacidades Premium. Especificamente, eles podem:

- Altere o tamanho da capacidade para escalar verticalmente ou reduzir os recursos. No entanto, não é possível fazer downgrade de uma SKU P para uma SKU em ou atualizar vice-versa.
- Adicionar ou remover administradores de capacidade
- Adicionar ou remover usuários que têm permissões de atribuição
- Adicionar ou remover cargas de trabalho adicionais
- Alterar regiões

São necessárias permissões de atribuição para atribuir um espaço de trabalho a uma capacidade Premium específica. As permissões podem ser concedidas a toda a organização, a usuários ou grupos específicos.

Por padrão, as capacidades Premium dão suporte a cargas de trabalho associadas à execução de Power BI consultas. Ele também dá suporte a três cargas de trabalho adicionais: **Relatórios**paginados, **fluxos de fluxo**de os e o **ia**. Cada carga de trabalho requer a configuração da memória máxima (como uma porcentagem da memória total disponível) que pode ser usada pela carga de trabalho. É importante entender que o aumento das alocações de memória máximas pode afetar o número de modelos ativos que podem ser hospedados e a taxa de transferência de atualizações.

A memória é dinamicamente alocada para fluxos de dados, mas é alocada estaticamente para relatórios paginados. O motivo da alocação estática da memória máxima é que os relatórios paginados são executados em um espaço independente protegido da capacidade. Deve-se ter cuidado ao definir a memória de relatórios paginados, pois reduz a memória disponível para o carregamento de modelos.

|                     | EM3                      | P1                       | P2                      | P3                       |
|---------------------|--------------------------|--------------------------|-------------------------|--------------------------|
| Relatórios paginados | N/D | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5% | Padrão de 20%; mínimo de 2,5% |
| Fluxos de dados | Padrão de 20%; mínimo de 8%  | Padrão de 20%; mínimo de 4%  | Padrão de 20%; mínimo de 2% | Padrão de 20%; mínimo de 1%  |
| IA | N/D | 20% padrão; mínimo de 20%  | Padrão de 20%; mínimo de 10% | Padrão de 20%; mínimo de 5%  |
| | | | | |

A exclusão de uma capacidade Premium é possível e não resultará na exclusão de seus espaços de trabalho e conteúdo. Em vez disso, ele moverá quaisquer espaços de trabalho atribuídos para a capacidade compartilhada. Quando a capacidade Premium foi criada em uma região diferente, o espaço de trabalho será movido para a capacidade compartilhada da região de residência.

### <a name="assigning-workspaces-to-capacities"></a>Atribuindo espaços de trabalho a capacidades

Os espaços de trabalho podem ser atribuídos a uma capacidade Premium no**portal** de **Administração do Power bi**ou-para um espaço de trabalho de aplicativo-no painel **espaço de trabalho** .

Os administradores de capacidade, bem como administradores globais do Office 365 ou administradores de serviço do Power BI, podem atribuir espaços de trabalho em massa no**portal**de **Administração do Power bi**. A atribuição em massa pode se aplicar a:

- **Espaços de trabalho por usuários** : Todos os espaços de trabalho pertencentes a esses usuários, incluindo espaços de trabalho pessoais, são atribuídos à capacidade Premium. Isso incluirá a reatribuição de espaços de trabalho quando eles já estiverem atribuídos a uma capacidade Premium diferente. Além disso, os usuários também recebem permissões de atribuição de espaço de trabalho.

- **Workspaces específicos**
- **Os espaços de trabalho de toda a organização** : Todos os espaços de trabalho, incluindo espaços de trabalho pessoais, são atribuídos à capacidade Premium. Além disso, todos os usuários atuais e futuros recebem permissões de atribuição de espaço de trabalho. \[[140](#endnote-14)\]

Um espaço de trabalho pode ser adicionado a uma capacidade Premium usando o painel **espaço de trabalho** que fornece ao usuário um administrador de espaço de trabalho e tem permissões de atribuição.

![Usando o painel de espaço de trabalho para atribuir um espaço de trabalho a uma capacidade Premium](media/whitepaper-premium-deployment/assign-workspace-capacity.png)

Os administradores de espaço de trabalho podem remover um espaço de trabalho de uma capacidade (para capacidade compartilhada) sem a necessidade de permissão de atribuição. A remoção de espaços de trabalho de capacidades dedicadas efetivamente realoca o espaço de trabalho para a capacidade compartilhada. Observe que a remoção de um espaço de trabalho de uma capacidade Premium pode ter consequências negativas resultantes, por exemplo, no conteúdo compartilhado ficando indisponível para Power BI usuários licenciados gratuitos ou a suspensão da atualização agendada quando elas excederem as concessões com suporte por capacidades compartilhadas.

Na serviço do Power BI, um espaço de trabalho atribuído a uma capacidade Premium é facilmente identificado pelo ícone de losango que adorna o nome do espaço de trabalho.

![Identificando um espaço de trabalho atribuído a uma capacidade Premium](media/whitepaper-premium-deployment/premium-diamond-icon.png)

### <a name="monitoring-capacities"></a>Capacidades de monitoramento

O monitoramento de capacidades Premium fornece aos administradores uma compreensão de como as capacidades estão sendo executadas. As capacidades podem ser monitoradas usando o aplicativo de métricas de [capacidade Power bi Premium](service-admin-premium-monitor-capacity.md) ou o [portal de administração Power bi](service-admin-premium-monitor-portal.md).

#### <a name="interpreting-metrics"></a>Interpretando métricas

As métricas devem ser monitoradas para estabelecer uma compreensão de linha de base do uso de recursos e da atividade de carga de trabalho. Se a capacidade se tornar lenta, é importante entender quais métricas monitorar e as conclusões que você pode fazer.

O ideal é que as consultas sejam concluídas em um segundo para fornecer experiências responsivas aos usuários de relatório e permitir uma maior taxa de transferência de consulta. Normalmente, é de menor preocupação quando processos em segundo plano-incluindo atualizações-demoram mais tempo para serem concluídos.

Em geral, relatórios lentos podem ser uma indicação de uma capacidade de excesso de aquecimento. Quando os relatórios falham ao serem carregados, essa é uma indicação de uma capacidade superaquecido. Em qualquer situação, a causa raiz pode ser atribuível a muitos fatores, incluindo:

- **Consultas com falha** certamente indicam pressão de memória e que um modelo não pôde ser carregado na memória. O serviço do Power BI tentará carregar um modelo por 30 segundos antes de falhar.

- **Tempos de espera de consulta excessivos** podem ser devido a vários motivos:
  - A necessidade do serviço do Power BI primeiro remover modelo (s) e, em seguida, carregar o modelo a ser consultado (Lembre-se de que as taxas de remoção de conjunto de mais altas sozinhos não são uma indicação de sobrecarga de capacidade, a menos que acompanhado por tempos de espera de consulta longos que indicam a memória ultrapaginação)
  - Tempos de carregamento de modelo (especialmente a espera para carregar um modelo grande na memória)
  - Consultas de longa execução
  - Muitas conexões LC\DQ (excedendo os limites de capacidade)
  - Saturação da CPU
  - Designs de relatório complexos com um número excessivo de visuais em uma página (Lembre-se de que cada visual é uma consulta)
- As **durações de consulta longas** podem indicar que os designs de modelo não são otimizados, especialmente quando vários conjuntos de valores estão ativos em uma capacidade, e apenas um conjunto de um DataSet está produzindo durações de consulta longas. Isso sugere que a capacidade seja de origem suficiente e que o conjunto de espaço em questão seja abaixo do ideal ou que seja apenas lento. As consultas de longa execução podem ser problemáticas, pois podem bloquear o acesso aos recursos exigidos por outros processos.
- **Tempos de espera de atualização longos ou tempos de espera de chamada de ia** indicam memória insuficiente devido a muitos modelos ativos consumindo memória ou que uma atualização problemática está bloqueando outras atualizações (excedendo os limites de atualização paralela).

Uma explicação mais detalhada de como usar as métricas é abordada em seguida na seção [otimizando capacidades Premium](#optimizing-premium-capacities) .

## <a name="optimizing-premium-capacities"></a>Otimizando as capacidades Premium

Quando surgem problemas de desempenho de capacidade Premium, uma primeira abordagem comum é otimizar ou ajustar soluções já implantadas para restaurar tempos de resposta aceitáveis. A lógica de substituição é evitar a compra de capacidade Premium adicional, a menos que possa ser justificada.

Quando a capacidade Premium adicional é necessária, há duas opções que serão discutidas posteriormente nesta seção:

- Escalar verticalmente a capacidade Premium
- Adicionar uma nova capacidade Premium

Por fim, as abordagens de teste e o dimensionamento da capacidade Premium concluirão esta seção.

### <a name="general-best-practices"></a>Práticas recomendadas gerais

Ao se empenhar em obter melhor utilização e desempenho, há algumas práticas recomendadas que podem ser tomadas no quadro como recomendações gerais. Elas incluem:

- Usando espaços de trabalho de aplicativo em vez de espaços de trabalho pessoais
- Separação de SSBI (BI crítico e de autoatendimento) para diferentes capacidades

  ![Separando o BI comercialmente crítico e de autoatendimento em diferentes capacidades](media/whitepaper-premium-deployment/separate-capacities.png)

- Se estiver compartilhando conteúdo apenas com Power BI Pro usuários, talvez não seja necessário armazenar o conteúdo em uma capacidade dedicada
- Use capacidades dedicadas ao procurar atingir um tempo de atualização específico ou quando recursos específicos forem necessários, por exemplo, grandes conjuntos de data ou relatórios paginados

### <a name="addressing-common-questions"></a>Endereçando perguntas comuns

A otimização de implantações Power BI Premium é um tópico complexo que envolve uma compreensão dos requisitos de carga de trabalho, recursos disponíveis e seu uso efetivo.

Este tópico aborda sete perguntas de suporte comuns, descrevendo possíveis problemas e explicações e informações sobre como identificá-las e resolvê-las.

#### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Por que a capacidade está lenta e o que posso fazer?

Há muitas razões que podem contribuir para uma capacidade Premium lenta. Essa pergunta requer mais informações para entender o que significa lentidão. Os relatórios estão lentos para carregar? Ou eles estão falhando ao carregar? Os visuais de relatório são lentos para carregar ou atualizar quando os usuários interagem com o relatório? As atualizações estão demorando mais para serem concluídas do que o esperado, ou anteriormente experimentadas?

Tendo obtido uma compreensão do motivo, você pode começar a investigar. As respostas às seis perguntas a seguir ajudarão você a resolver problemas mais específicos.

#### <a name="what-content-is-using-up-my-capacity"></a>Qual conteúdo está usando minha capacidade?

Você pode usar o **Power bi Premium** aplicativo de métricas de capacidade para filtrar por capacidade e examinar as métricas de desempenho do conteúdo do espaço de trabalho. É possível examinar as métricas de desempenho e o uso de recursos por hora nos últimos sete dias para todo o conteúdo armazenado em uma capacidade Premium. Geralmente, essa é a primeira etapa a ser tomada ao solucionar uma preocupação geral sobre o desempenho da capacidade Premium.

As principais métricas a serem monitoradas incluem:

- Média de CPU e contagem de alta utilização
- Memória média e contagem de alta utilização e uso de memória para conjuntos de valores específicos, fluxos de itens e relatórios paginados
- Conjuntos de itens ativos carregados na memória
- Média e máximo de durações de consulta
- Tempos médios de espera de consulta
- Média de tempos de atualização de conjunto de fluxo e Dataflow
- Tempos médios de chamada de AI e tempos de espera

Além disso, no aplicativo de métricas de capacidade Power BI Premium, memória ativa mostra a quantidade total de memória alocada para um relatório que não pode ser removida porque está em uso nos últimos três minutos. Um alto pico no tempo de espera de atualização pode ser correlacionado com um conjunto de um grande e/ou ativo.

O gráfico "5 principais por duração média" realça os cinco principais conjuntos de valores, relatórios paginados, fluxos de tabela e chamadas de ia que consomem recursos de capacidade. O conteúdo nas cinco listas principais são candidatos para investigação e possível otimização.

#### <a name="why-are-reports-slow"></a>Por que os relatórios são lentos?

As tabelas a seguir mostram possíveis problemas e maneiras de identificá-los e tratá-los.

##### <a name="insufficient-capacity-resources"></a>Recursos de capacidade insuficientes

| Explicações possíveis | Como identificar | Como resolver |
| --- | --- | --- |
| Memória ativa total alta (o modelo não pode ser removido porque está em uso nos últimos três minutos)<br><br> Vários picos altos nos tempos de espera da consulta<br><br> Vários picos altos em tempos de espera de atualização | Monitorar as métricas \[de memória [18](#endnote-18)\]e as contagens \[de remoção [19](#endnote-19)\] | Diminuir o tamanho do modelo ou converter para o modo DirectQuery-consulte o tópico [otimizando modelos](#optimizing-models) nesta seção<br><br> Escalar verticalmente a capacidade<br><br> Atribuir o conteúdo a uma capacidade diferente |

##### <a name="inefficient-report-designs"></a>Designs de relatório ineficientes

| Explicações possíveis | Como identificar | Como resolver |
| --- | --- | --- |
| As páginas de relatório contêm vários visuais (a filtragem interativa pode disparar pelo menos uma consulta por Visual)<br><br> Os visuais recuperam mais dados do que o necessário | Examinar designs de relatório<br><br> Usuários de relatório de entrevistas para entender como eles interagem com os relatórios<br><br> Monitorar métricas \[de consulta de conjunto de conjuntos [20](#endnote-20)\] | Reprojetar relatórios com menos visuais por página |

##### <a name="dataset-slow-especially-when-reports-have-previously-performed-well"></a>DataSet lento (especialmente quando os relatórios tiverem sido bem executados)

| Explicações possíveis | Como identificar | Como resolver |
| --- | --- | --- |
| Volumes cada vez maiores de dados de importação<br><br> Lógica de cálculo complexa ou ineficiente, incluindo as funções RLS<br><br> Modelo não totalmente otimizado<br><br> (DQ/LC) Latência do gateway<br><br> Tempos de resposta de consulta de origem do DQ lento | Revisar designs de modelo<br><br> Monitorar contadores de desempenho do gateway | Consulte o tópico [otimizando modelos](#optimizing-models) nesta seção |

##### <a name="high-concurrent-report-usage"></a>Alto uso de relatório simultâneo

| Explicações possíveis | Como identificar | Como resolver |
| --- | --- | --- |
| Tempos de espera de consulta alta<br><br> Saturação da CPU<br><br> Limites de conexão do DQ/LC excedidos | Monitorar a utilização \[da CPU [21](#endnote-21)\], os tempos de espera da consulta e \[a utilização do DQ/LC [22](#endnote-22) \] métricas + durações da consulta – se a flutuação puder indicar problemas de simultaneidade | Escalar verticalmente a capacidade ou atribuir o conteúdo a uma capacidade diferente<br><br> Reprojetar relatórios com menos visuais por página |

#### <a name="why-are-reports-not-loading"></a>Por que os relatórios não estão carregando?

Quando os relatórios não conseguem carregá-lo é um cenário de pior caso e um sinal de que a capacidade tem memória insuficiente e é superaquecido. Isso pode ocorrer quando todos os modelos carregados estão sendo consultados ativamente e, portanto, não podem ser removidos, e todas as operações de atualização foram pausadas ou atrasadas. O serviço do Power BI tentará carregar o conjunto de um por 30 segundos, e o usuário será notificado normalmente sobre a falha com uma sugestão para tentar novamente em breve.

Atualmente, não há métrica para monitorar falhas de carregamento de relatório. Você pode identificar o potencial desse problema monitorando a memória do sistema, especificamente a maior utilização e o tempo de utilização mais alta. As remoções altas de conjunto de grandes e o tempo de espera médio de atualização de conjunto de grandes podem sugerir que esse problema está ocorrendo.

Se isso ocorrer apenas algumas vezes, isso pode não ser considerado um problema de prioridade. Os usuários de relatório são informados de que o serviço está ocupado e que eles devem tentar novamente após um curto período de tempo. Se isso ocorrer com muita frequência, o problema poderá ser resolvido expandindo a capacidade Premium ou atribuindo o conteúdo a uma capacidade diferente.

Os administradores de capacidade (e administradores de serviço do Power BI) podem monitorar a métrica de **falhas de consulta** para determinar quando isso acontece. Eles também podem reiniciar a capacidade, redefinindo todas as operações em caso de sobrecarga do sistema.

#### <a name="why-are-refreshes-not-starting-on-schedule"></a>Por que as atualizações não são iniciadas na agenda?

Os horários de início da atualização agendada não são garantidos. Lembre-se de que a serviço do Power BI sempre priorizará operações interativas em operações em segundo plano. A atualização é uma operação em segundo plano que pode ocorrer quando duas condições são atendidas:

- Há memória suficiente
- O número de atualizações simultâneas com suporte para a capacidade Premium não é excedido

Quando as condições não forem atendidas, a atualização será enfileirada até que as condições sejam favoráveis.

Para uma atualização completa, lembre-se de que, pelo menos, o tamanho da memória do conjunto de tempo atual é necessário. Se não houver memória suficiente disponível, a atualização não poderá ser iniciada até que a remoção do modelo Libere memória – isso significa atrasos até que um ou mais conjuntos de valores se tornem inativos e possam ser removidos.

Lembre-se de que o número com suporte de atualizações simultâneas máximas é definido como 1,5 vezes os núcleos virtuais de back-end, arredondados.

Uma atualização agendada falhará quando não for possível começar antes da próxima atualização agendada devido ao início. Uma atualização sob demanda disparada manualmente da interface do usuário tentará executar até três vezes antes de falhar.

O administrador de capacidade (e os administradores de serviço do Power BI) pode monitorar a métrica **tempo médio de espera de atualização (minutos)** para determinar o atraso médio entre a hora agendada e o início da operação.

Embora normalmente não seja uma prioridade administrativa, para influenciar as atualizações de dados em tempo, verifique se há memória suficiente disponível. Isso pode envolver o isolamento de conjuntos de valores para capacidades com recursos suficientes conhecidos. Também é possível que os administradores possam coordenar com os proprietários do conjunto de dados para ajudar a escalonar ou reduzir os tempos de atualização agendados para minimizar as colisões. Observe que não é possível que um administrador exiba a fila de atualização ou recupere agendas de conjunto de usuários.

#### <a name="why-are-refreshes-slow"></a>Por que as atualizações são lentas?

As atualizações podem ser lentas ou observadas para serem lentas (como os endereços de pergunta comuns anteriores).

Quando a atualização é, na verdade, lenta, pode ser devido a vários motivos:

- CPU insuficiente (a atualização pode ser de uso intensivo de CPU)
- Memória insuficiente, resultando na pausa da atualização (o que exige que a atualização seja reiniciada quando as condições são favoráveis para reinicializar)
- Motivos de não capacidade, incluindo capacidade de resposta do sistema de fonte de dados, latência de rede, permissões inválidas ou taxa de transferência de gateway
- Volume de dados – um bom motivo para configurar a atualização incremental, conforme discutido abaixo

Os administradores de capacidade (e os administradores de serviço do Power BI) podem monitorar a métrica **média de duração da atualização (minutos)** para determinar um parâmetro de comparação com o tempo e a métrica **tempo médio de espera de atualização (minutos)** para determinar o atraso médio entre o atraso médio entre a hora agendada e o início da operação.

A atualização incremental pode reduzir significativamente a duração da atualização de dados, especialmente para grandes tabelas de modelo. Há quatro benefícios associados à atualização incremental:

- As **atualizações são mais rápidas** : Somente um subconjunto de uma tabela precisa ser carregado, reduzindo o uso de CPU e memória e o paralelismo pode ser maior ao atualizar várias partições
- As **atualizações ocorrem somente quando necessário** : As políticas de atualização incremental podem ser configuradas para carregar somente quando os dados forem alterados
- As **atualizações são mais confiáveis** : Conexões de execução mais curtas para sistemas de fonte de dados voláteis são menos suscetíveis à desconexão
- Os **modelos permanecem cortados** : As políticas de atualização incremental podem ser configuradas para remover automaticamente o histórico além de uma janela deslizante de tempo

Para obter mais informações, consulte a [atualização incremental no documento Power bi Premium](service-premium-incremental-refresh.md) .

#### <a name="why-are-data-refreshes-not-completing"></a>Por que as atualizações de dados não estão sendo concluídas?

Quando a atualização de dados começa, mas não é concluída, pode ser devido a vários motivos:

- Memória insuficiente, mesmo se houver apenas um modelo na capacidade Premium, ou seja, o tamanho do modelo é muito grande
- Motivos de não capacidade, incluindo desconexão do sistema de fonte de dados, permissões inválidas ou erro de gateway

Os administradores de capacidade (e administradores de serviço do Power BI) podem monitorar as **falhas de atualização devido à métrica de memória insuficiente** .

#### <a name="why-are-ai-calls-failing"></a>Por que as chamadas de ia falham?

As chamadas de ia podem falhar por vários motivos. A memória mínima necessária para iniciar a carga de trabalho de ia é de 5 GB, mas isso pode não ser suficiente para alguns conjuntos de dados de entrada. Por exemplo, o treinamento do modelo de aprendizado de máquina automatizado requer pelo menos duas vezes e, às vezes, várias vezes o tamanho do conjunto de dados de entrada. Além disso, uma chamada de ia será encerrada se demorar mais de duas horas para ser concluída. Para as chamadas automatizadas de treinamento de modelo do Machine Learning que não são concluídas em duas horas, o melhor modelo encontrado nessas duas horas é retornado.  As chamadas de ia também podem ser interrompidas por solicitações interativas, que têm precedência.

Os administradores devem monitorar os tempos de espera de ia para sinais de outras solicitações que têm precedência. Os administradores também podem garantir que memória suficiente esteja disponível para a carga de trabalho de ia em relação aos tamanhos de dados de entrada. Isso pode envolver o isolamento de cargas de trabalho de ia para capacidades conhecidas por ter recursos suficientes. Também é possível que os administradores possam coordenar com os proprietários de Dataflow para ajudar a escalonar ou reduzir os tempos de atualização de Dataflow para minimizar as colisões. Observe que não é possível que um administrador exiba a fila de chamadas de ia.

### <a name="optimizing-models"></a>Otimizando modelos

O design de modelo ideal é crucial para a entrega de uma solução eficiente e escalonável. No entanto, está além do escopo deste White Paper para fornecer uma discussão completa. Em vez disso, esta seção fornecerá as principais áreas para consideração ao otimizar modelos.

#### <a name="optimizing-power-bi-hosted-models"></a>Otimizando modelos hospedados Power BI

A otimização de modelos hospedados em uma capacidade Premium pode ser obtida nas fontes de dados e nas camadas do modelo.

Considere as possibilidades de otimização para um modelo de importação:

![Possibilidades de otimização para um modelo de importação](media/whitepaper-premium-deployment/import-model-optimizations.png)

Na camada de fonte de dados:

- As fontes de dados relacionais podem ser otimizadas para garantir a atualização mais rápida possível, aplicando os índices apropriados, definindo as partições de tabela que se alinham aos períodos de atualização incremental e materializando os cálculos (no lugar do calculado modelar tabelas e colunas) ou adicionar lógica de cálculo a exibições
- As fontes de dados não relacionais podem ser previamente integradas a repositórios relacionais
- Verifique se os gateways têm recursos suficientes, preferencialmente em computadores dedicados, com largura de banda de rede suficiente e em proximidade com as fontes de dados

Na camada de modelo:

- Power Query designs de consulta podem minimizar ou remover transformações complexas e, especialmente, aquelas que mesclam diferentes fontes de dados (os data warehouses atingem isso durante o estágio Extract-Transform-Load). Além disso, garantir que os níveis de privacidade apropriados da fonte de dados sejam definidos, isso pode evitar a necessidade de Power BI carregar resultados completos para produzir um resultado combinado entre consultas.
- A estrutura do modelo determina os dados a serem carregados e tem um impacto direto no tamanho do modelo. Ele pode ser projetado para evitar o carregamento de dados desnecessários removendo colunas, removendo linhas (especialmente dados históricos) ou carregando dados resumidos (às custas de carregar dados detalhados). A redução de tamanho drástico pode ser obtida removendo-se colunas de alta cardinalidade (especialmente colunas de texto) que não são armazenadas ou compactadas com muita eficiência.
- O desempenho de consulta de modelo pode ser melhorado Configurando relações de direção única, a menos que haja um motivo convincente para permitir a filtragem bidirecional. Considere também usar a função CROSSFILTER em vez de filtragem bidirecional.
- As tabelas de agregação podem obter respostas de consulta rápidas carregando dados previamente resumidos, no entanto, isso aumentará o tamanho do modelo e resultará em tempos de atualização mais longos. Em geral, as tabelas de agregação devem ser reservadas para modelos muito grandes ou designs de modelo composto.
- As tabelas e colunas calculadas aumentam o tamanho do modelo e resultam em tempos de atualização mais longos. Geralmente, um tamanho de armazenamento menor e o tempo de atualização mais rápido podem ser obtidos quando os dados são materializados ou calculados na fonte de dados. Se isso não for possível, usar Power Query colunas personalizadas poderá oferecer uma compactação de armazenamento aprimorada.
- Pode haver oportunidade de ajustar expressões DAX para medidas e regras de RLS, talvez reescrevendo a lógica para evitar fórmulas caras
- A atualização incremental pode reduzir drasticamente o tempo de atualização e conservar a memória e a CPU. A atualização incremental também pode ser configurada para remover os tamanhos de modelo de manutenção de dados históricos.
- Um modelo pode ser reprojetado como dois modelos quando há padrões de consulta diferentes e conflitantes. Por exemplo, alguns relatórios apresentam agregações de alto nível sobre todo o histórico e podem tolerar a latência de 24 horas. Outros relatórios se preocupam com os dados de hoje e precisam de acesso granular a transações individuais. Em vez de criar um único modelo para atender a todos os relatórios, crie dois modelos otimizados para cada requisito.

Considere as possibilidades de otimização para um modelo DirectQuery. Como o modelo emite solicitações de consulta para a fonte de dados subjacente, a otimização da fonte de dados é essencial para fornecer consultas de modelo responsivas.

 ![Possibilidades de otimização para um modelo DirectQuery](media/whitepaper-premium-deployment/direct-query-model-optimizations.png)

Na camada de fonte de dados:

- A fonte de dados pode ser otimizada para garantir a consulta mais rápida possível por meio da integração prévia de dados (o que não é possível na camada do modelo), aplicando índices apropriados, definindo partições de tabela, materializando dados resumidos (com exibições indexadas) e minimizando a quantidade de cálculo. A melhor experiência é obtida quando as consultas de passagem precisam apenas filtrar e executar junções internas entre tabelas ou exibições indexadas.
- Verifique se os gateways têm recursos suficientes, preferencialmente em computadores dedicados, com largura de banda de rede suficiente e em proximidade com a fonte de dados

Na camada de modelo:

- Power Query designs de consulta devem, preferencialmente, aplicar nenhuma transformação – caso contrário, tentar manter as transformações em um mínimo absoluto
- O desempenho de consulta de modelo pode ser melhorado Configurando relações de direção única, a menos que haja um motivo convincente para permitir a filtragem bidirecional. Além disso, as relações de modelo devem ser configuradas para assumir que a integridade referencial é imposta (quando esse for o caso) e resultará em consultas de fonte de dados usando junções internas mais eficientes (em vez de junções externas).
- Evite criar Power Query colunas personalizadas de consulta ou coluna calculada de modelo-materializando-as na fonte de dados, quando possível
- Pode haver oportunidade de ajustar expressões DAX para medidas e regras de RLS, talvez reescrevendo a lógica para evitar fórmulas caras

Considere as possibilidades de otimização para um modelo composto. Lembre-se de que um modelo composto permite uma combinação de tabelas de importação e DirectQuery.

![Possibilidades de otimização para um modelo composto](media/whitepaper-premium-deployment/composite-model-optimizations.png)

- Em geral, os tópicos de otimização para modelos de importação e DirectQuery se aplicam a tabelas de modelo composto que usam esses modos de armazenamento.
- Normalmente, busque obter um design equilibrado Configurando tabelas de tipo de dimensão (representando entidades de negócios) como modo de armazenamento duplo e tabelas de tipo de fato (muitas vezes, tabelas grandes, representando fatos operacionais) como modo de armazenamento DirectQuery. O modo de armazenamento duplo significa ambos os modos de armazenamento de importação e DirectQuery, e isso permite que o serviço do Power BI determine o modo de armazenamento mais eficiente a ser usado ao gerar uma consulta nativa para passagem.
- Verifique se os gateways têm recursos suficientes, preferencialmente em computadores dedicados, com largura de banda de rede suficiente e em proximidade com as fontes de dados
- As tabelas de agregações configuradas como modo de armazenamento de importação podem fornecer melhorias consideráveis de desempenho de consulta quando usadas para resumir as tabelas de tipo de fato do modo de armazenamento DirectQuery. Nesse caso, as tabelas de agregação aumentarão o tamanho do modelo e aumentarão o tempo de atualização e, muitas vezes, essa é uma compensação aceitável para consultas mais rápidas.

#### <a name="optimizing-externally-hosted-models"></a>Otimizando modelos hospedados externamente

Muitas possibilidades de otimização discutidas no tópico [otimizando modelos hospedados Power bi](#optimizing-power-bi-hosted-models) se aplicam também a modelos desenvolvidos com Azure Analysis Services e SQL Server Analysis Services. As exceções claras são determinados recursos que não têm suporte no momento, incluindo modelos compostos e tabelas de agregação.

Uma consideração adicional para conjuntos de dados hospedados externamente é a hospedagem de banco de dados em relação à serviço do Power BI. Por Azure Analysis Services, isso significa criar o recurso do Azure na mesma região que o locatário de Power BI (região de residência). Por SQL Server Analysis Services, para IaaS, isso significa hospedar a VM na mesma região e, para o local, isso significa garantir uma configuração de gateway eficiente.

Além disso, pode ser interessante observar que Azure Analysis Services bancos de dados e SQL Server Analysis Services bancos de dados de tabela exigem que seus modelos sejam carregados totalmente na memória e que permaneçam lá em todos os momentos para dar suporte à consulta. Assim como o serviço do Power BI, precisa haver memória suficiente para atualizar se o modelo deve permanecer online durante a atualização. Ao contrário do serviço do Power BI, não há nenhum conceito de que os modelos sejam automaticamente classificados por e sem memória de acordo com o uso. O Power BI Premium, portanto, oferece uma abordagem mais eficiente para maximizar a consulta de modelo com menor uso de memória.

### <a name="capacity-planning"></a>Planejamento da capacidade

O tamanho de uma capacidade Premium determina sua memória disponível e os limites e recursos de processador impostos sobre a capacidade. O número de capacidades Premium também é uma consideração, pois a criação de várias capacidades Premium pode ajudar a isolar as cargas de trabalho umas das outras. Observe que o armazenamento é de 100 TB por nó de capacidade, e isso provavelmente será mais do que suficiente para qualquer carga de trabalho.

Determinar o tamanho e o número de capacidades Premium pode ser desafiador, especialmente para as capacidades iniciais que você criar. A primeira etapa quando a capacidade de dimensionamento é entender a carga de trabalho média que representa o uso esperado do dia a dia. É importante entender que nem todas as cargas de trabalho são iguais. Por exemplo, em uma extremidade de um espectro, os usuários simultâneos de 100 acessando uma única página de relatório que contém um único Visual é facilmente atingível. No entanto, na outra extremidade do espectro, 100 usuários simultâneos que acessam 100 relatórios diferentes, cada um com 100 visuais na página de relatório, farão demandas muito diferentes dos recursos de capacidade.

Portanto, os administradores de capacidade precisarão considerar muitos fatores específicos ao seu ambiente, conteúdo e uso esperado. O objetivo de substituição é maximizar a utilização da capacidade e, ao mesmo tempo, fornecer tempos de consulta consistentes, tempos de espera aceitáveis e taxas de remoção. Os fatores de consideração podem incluir:

- **Características de dados e tamanho do modelo** : Os modelos de importação devem ser totalmente carregados na memória para permitir a consulta ou a atualização. Os conjuntos de linhas de LC/DQ podem exigir um tempo de processador significativo e possivelmente uma memória significativa para avaliar medidas complexas ou regras de RLS. A memória e o tamanho do processador e a taxa de transferência de consulta LC/DQ são restritos pelo tamanho da capacidade.
- **Modelos ativos simultâneos** : A consulta simultânea de diferentes modelos de importação fornecerá melhor capacidade de resposta e desempenho quando eles permanecerem na memória. Deve haver memória suficiente para hospedar todos os modelos de consulta intensa, com memória adicional para permitir sua atualização.
- **Importar atualização do modelo** : O tipo de atualização (completo ou incremental), a duração e a complexidade de Power Query consultas e a lógica de tabela/coluna calculada podem afetar a memória e, especialmente, o uso do processador. As atualizações simultâneas são restritas pelo tamanho da capacidade (1,5 x back-end v-cores, arredondado).
- **Consultas simultâneas** : Muitas consultas simultâneas podem resultar em relatórios sem resposta quando as conexões de processador ou LC/DQ excedem o limite de capacidade. Isso é especialmente o caso para páginas de relatório que incluem muitos elementos visuais.
- **Funções de fluxo de os, relatórios paginados e ai** : A capacidade pode ser configurada para dar suporte a fluxos de os, relatórios paginados e funções de ia, cada um exigindo um percentual máximo configurável de memória de capacidade. A memória é alocada dinamicamente para fluxos de trabalho, mas é alocada estaticamente para relatórios paginados e a carga de trabalho de ia.

Além desses fatores, os administradores de capacidade podem considerar a criação de várias capacidades. Várias capacidades permitem o isolamento de cargas de trabalho e podem ser configuradas para garantir que as cargas de trabalho de prioridade tenham recursos garantidos. Por exemplo, duas capacidades podem ser criadas para separar cargas de trabalho críticas para os negócios de cargas de trabalho de BI (SSBI) de autoatendimento. A capacidade essencial aos negócios pode ser usada para isolar grandes modelos corporativos, fornecendo a eles recursos garantidos, com o acesso concedido somente ao departamento de ti. A capacidade do SSBI pode ser usada para hospedar um número cada vez maior de modelos menores, com acesso concedido a analistas de negócios. A capacidade SSBI pode às vezes experimentar a consulta ou as esperas de atualização que são tolerantes.

Ao longo do tempo, os administradores de capacidade podem balancear os espaços de trabalho entre as capacidades movendo o conteúdo entre espaços de trabalho ou espaços de trabalho entre as capacidades e dimensionando as capacidades para cima ou para baixo. Em geral, para hospedar modelos maiores, você escala verticalmente e para uma simultaneidade maior, você escala horizontalmente.

Lembre-se de que a compra de uma licença fornece o locatário com núcleos virtuais. A compra de uma assinatura **P3** pode ser usada para criar uma ou até quatro capacidades Premium, ou seja, 1 x P3 ou 2 x P2 ou 4 x P1. Além disso, antes de fazer o upsizing de uma capacidade P2 para uma capacidade P3, a consideração pode ser dada à divisão dos núcleos virtuais para criar duas capacidades P1.

### <a name="testing-approaches"></a>Abordagens de teste

Quando o tamanho da capacidade é decidido, o teste pode ser executado criando um ambiente controlado. Uma opção prática e econômica é criar uma capacidade do Azure (uma SKUs), observando que uma capacidade P1 tem o mesmo tamanho que uma capacidade A4, com as capacidades P2 e P3 do mesmo tamanho que as capacidades a5 e A6, respectivamente. As capacidades do Azure podem ser criadas rapidamente e são cobradas por hora. Assim, quando o teste for concluído, eles poderão ser facilmente excluídos para parar de acumular os custos.

O conteúdo do teste pode ser adicionado aos espaços de trabalho criados na capacidade do Azure e, em seguida, como um único usuário pode executar relatórios para gerar uma carga de trabalho realista e representativa de consultas. Se houver modelos de importação, uma atualização para cada modelo também deverá ser executada. As ferramentas de monitoramento podem ser usadas para revisar todas as métricas para entender a utilização de recursos.

É importante que os testes sejam repetíveis: Os testes devem ser executados várias vezes e devem fornecer aproximadamente o mesmo resultado a cada vez. Uma média desses resultados pode ser usada para extrapolar e estimar uma carga de trabalho em condições de produção verdadeiras.

Se você já tiver uma capacidade e os relatórios para os quais deseja fazer o teste de carga, use a [ferramenta de geração de carga do PowerShell](https://aka.ms/PowerBILoadTestingTool) para gerar rapidamente um teste de carga. A ferramenta permite que você calcule quantas instâncias de cada relatório sua capacidade pode executar em uma hora. Você pode usar a ferramenta para avaliar a capacidade da capacidade de renderização de relatório individual ou para renderizar vários relatórios diferentes em paralelo. Para obter mais informações, consulte o [vídeo Microsoft Power bi: Capacidade](https://www.youtube.com/watch?time_continue=1860&v=C6vk6wk9dcw)Premium.

Para gerar um teste mais complexo, considere desenvolver um aplicativo de teste de carga que simule uma carga de trabalho realista. Para obter mais informações, consulte o teste de carga do webinar [Power bi aplicativos com o teste de carga do Visual Studio](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/).

## <a name="exploring-real-world-scenarios"></a>Explorando cenários do mundo real

Nesta seção, vários cenários do mundo real serão introduzidos para descrever problemas ou desafios comuns, como identificá-los e como ajudar a resolvê-los:

- [Mantendo os conjuntos de dados atualizados](#keeping-datasets-up-to-date)
- [Identificando conjuntos de valores de resposta lenta](#identifying-slow-responding-datasets)
- [Identificando as causas de conjuntos de valores de resposta esporadicamente lentos](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Determinando se há memória suficiente](#determining-whether-there-is-enough-memory)
- [Determinando se há CPU suficiente](#determining-whether-there-is-enough-cpu)

As etapas, juntamente com os exemplos de gráfico e tabela, são do aplicativo de métricas de **capacidade Power bi Premium** (aplicativo) ao qual um administrador de Power bi terá acesso.

### <a name="keeping-datasets-up-to-date"></a>Mantendo os conjuntos de dados atualizados

Nesse cenário, uma investigação foi disparada quando os usuários reclamaram que os dados de relatório às vezes parecem ser antigos ou "obsoletos".

No aplicativo, o administrador interage com o Visual de **atualizações** , classificando conjuntos de itens por estatísticas de **tempo de espera máxima** em ordem decrescente. Isso ajuda a revelar os conjuntos de valores que têm os tempos de espera mais longos, agrupados por nome do espaço de trabalho.

![Atualizações de DataSet classificadas por tempo de espera máximo decrescente, agrupadas por espaço de trabalho](media/whitepaper-premium-deployment/dataset-refreshes.png)

Além disso, no Visual **tempo médio de espera de atualização por hora** , eles observam que o pico de tempos de espera de atualização consistentemente em relação a 16:00 todos os dias.

![Pico de esperas de atualização periodicamente em 16:00](media/whitepaper-premium-deployment/peak-refresh-waits.png)

Há várias explicações possíveis para esses resultados:

- Muitas tentativas de atualização podem estar ocorrendo ao mesmo tempo, excedendo os limites impostos pelo nó de capacidade (seis atualizações simultâneas em um P1 com alocação de memória padrão)

- Os conjuntos de valores a serem atualizados podem ser muito grandes para se ajustar à memória disponível (exigindo pelo menos 2x a memória necessária para a atualização completa)
- A lógica de Power Query ineficiente pode estar resultando em um pico de uso de memória durante a atualização do conjunto de resultados. Em uma capacidade ocupada, ocasionalmente pode atingir o limite físico, falhando na atualização e potencialmente afetando outras operações de exibição de relatório na capacidade.
- Os conjuntos de linhas consultados com frequência que precisam permanecer na memória podem afetar a capacidade de atualização de outros conjuntos de os, devido à memória disponível limitada

Para ajudar a investigar isso, o administrador de Power BI pode procurar:

- Baixa memória disponível no momento da atualização de dados, quando a memória disponível é menor do que o tamanho do DataSet a ser atualizado
- Conjuntos de valores que não estavam sendo atualizados e não estavam na memória antes de uma atualização, mas que começaram a mostrar tráfego interativo durante tempos de atualização pesadas. Para ver quais conjuntos de dados foram carregados na memória a qualquer momento, um administrador de Power BI pode examinar a área conjuntos de dados da guia **conjuntos** de dados no aplicativo e cruzar o filtro para um determinado horário clicando em uma das barras na **contagem**de conjuntos de dados carregados por hora. Um pico local (mostrado na imagem abaixo) indica uma hora em que vários conjuntos de valores foram carregados na memória, o que pode atrasar o início das atualizações agendadas
- As remoções de conjunto de dados aumentam quando as atualizações são agendadas para iniciar, indicando que houve uma alta pressão de memória causada pelo fornecimento de muitos relatórios interativos diferentes antes do momento da atualização. A **remoção de conjunto de e de consumo de memória por hora** pode indicar claramente picos em remoções.

A imagem a seguir mostra um pico local nos conjuntos de valores carregados, que sugere a consulta interativa início de atualizações. A seleção de um período no **conjunto** de tempo de contagem de DataSets carregados por hora irá cruzar o filtro do Visual **dos tamanhos do conjunto** de um.

![Um pico local em conjuntos de datacarregados sugere A consulta interativa o início atrasado de atualizações](media/whitepaper-premium-deployment/hourly-loaded-dataset-counts.png)

O administrador de Power BI pode tentar resolver o problema executando etapas para garantir que memória suficiente esteja disponível para atualizações de dados para serem iniciadas por:

- Entrando em contato com proprietários de conjuntos de dados e pedindo-os a escalonar e espaçar agendamentos de atualização
- Reduzindo a carga de consulta do conjunto de linhas removendo painéis desnecessários ou blocos de painéis, especialmente aqueles que impõem a segurança em nível de linha
- Acelerando as atualizações de dados otimizando Power Query lógica, colunas calculadas de modelo ou tabelas, reduzindo os tamanhos de conjuntos de dados ou configurando conjuntos de dados maiores para executar a atualização de data incremental

### <a name="identifying-slow-responding-datasets"></a>Identificando conjuntos de valores de resposta lenta

Nesse cenário, uma investigação foi disparada quando os usuários reclamaram que determinados relatórios levaram muito tempo para serem abertos e às vezes seriam interrompidos.

No aplicativo, o administrador de Power BI pode usar o Visual **duração da consulta** para determinar os piores conjuntos de valores de desempenho, classificando conjuntos de aplicativos por **duração média**decrescente. Esse visual também mostra as contagens de consulta do conjunto de consultas, para que você possa ver com que frequência os conjuntos de valores são consultados.

![Revelando os piores conjuntos de itens de desempenho](media/whitepaper-premium-deployment/worst-performing-datasets.png)

O administrador de Power BI pode consultar o Visual de **distribuição da duração da consulta** , que mostra uma distribuição geral do desempenho de consulta segmentado (< = 30ms, 0 a 100 ms, etc.) para o período de tempo filtrado. Geralmente, as consultas que levam um segundo ou menos são consideradas responsivas pela maioria dos usuários; as consultas que demoram mais tendem a criar uma percepção do mau desempenho.

O Visual de **distribuição de duração da consulta por hora** permite que o administrador do Power bi identifique períodos de uma hora quando o desempenho da capacidade pode ter sido percebido como insatisfatório. Quanto maiores os segmentos de barras que representam durações de consulta em um segundo, maior será o risco de que os usuários perceberão um desempenho insatisfatório.

O Visual é interativo e, quando um segmento da barra é selecionado, o Visual da tabela **durações da consulta** correspondente na página do relatório é filtrado de forma cruzada para mostrar os conjuntos de valores que ele representa. Essa filtragem cruzada permite que o administrador do Power BI identifique facilmente quais conjuntos de dataestão respondendo lentamente.

A imagem a seguir mostra um Visual filtrado por **horas de distribuição de duração de consulta por hora**, concentrando-se nos piores conjuntos de valores de execução em buckets de uma hora. 

![O Visual de distribuições de duração de consulta filtrada por hora mostra o pior desempenho de conjuntos de os](media/whitepaper-premium-deployment/hourly-query-duration-distributions.png)

Depois que o conjunto de informações de desempenho insatisfatório em um período de 1 hora específico for identificado, o administrador do Power BI poderá investigar se o baixo desempenho é causado por uma capacidade sobrecarregada ou devido a um relatório ou conjunto de informações mal projetado. Para fazer isso, eles podem se referir ao Visual de **tempos de espera de consulta** e classificar conjuntos de valores por tempo médio de espera de consulta. Se um grande percentual de consultas estiver aguardando, é provável que uma demanda alta para o conjunto de um DataSet seja a causa das várias esperas de consulta. Se o tempo médio de espera da consulta for substancial (> 100 ms), pode valer a pena revisar o conjunto de relatórios e o relatório para ver se as otimizações podem ser feitas. Por exemplo, talvez menos visuais em determinadas páginas de relatório ou em uma otimização de expressão DAX.

![O Visual de tempos de espera da consulta ajuda a revelar conjuntos de valores com mau desempenho](media/whitepaper-premium-deployment/query-wait-times.png)

Há várias razões possíveis para o tempo de espera da consulta se acumular nos conjuntos de valores:

- Um design de modelo abaixo do ideal, expressões de medida ou até mesmo design de relatório – todas as circunstâncias que podem contribuir para consultas de longa execução que consomem altos níveis de CPU. Isso força novas consultas a aguardar até que os threads de CPU fiquem disponíveis e possam criar um efeito de comboio (think emperramento de tráfego), normalmente visto durante o horário comercial de pico. A página esperas de **consulta** será o recurso principal para determinar se os conjuntos de valores têm tempos de espera médios de consulta.
- Um alto número de usuários de capacidade simultânea (centenas a milhares) consumindo o mesmo relatório ou conjunto de mesmos. Até mesmo os conjuntos de itens bem projetados podem executar incorretamente um limite de simultaneidade. Isso geralmente é indicado por um único conjunto de um, mostrando um valor consideravelmente mais alto para contagens de consulta do que outros conjuntos de valores mostram (ou seja, consultas 300 mil para um conjunto de um DataSet em comparação com as consultas < 30 mil para todos os outros conjuntos de os). Em algum momento, a consulta aguardará esse conjunto de DataSet começará a ser escalonada, e isso será visto no Visual **duração da consulta** .
- Muitos conjuntos de datadiferentes consultados simultaneamente, que causam ultrapaginação como conjuntos de valores frequentemente percorrerão e esgotarão a memória. Isso faz com que os usuários tenham desempenho lento quando o conjunto de resultados é carregado na memória. Para confirmar isso, o administrador do Power BI pode referir-se ao Visual por **hora de remoção e consumo de memória** , o que pode indicar que um grande número de conjuntos de linhas carregados na memória está sendo removido repetidamente.

### <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identificando as causas de conjuntos de valores de resposta esporadicamente lentos

Nesse cenário, uma investigação foi disparada quando os usuários descreveam que os visuais de relatório às vezes pareciam lentos para responder ou podem não responder, mas em outras ocasiões eles eram responsivos.

Dentro do aplicativo, a seção **duração da consulta** foi usada para encontrar o conjunto de aplicativos culpado da seguinte maneira:

- No, a **consulta** tem como Visual o conjunto de linhas filtradas pelo administrador por conjunto de valores (começando nos conjuntos de os principais consultados) e examinou as barras com filtro cruzado no Visual de distribuições de **consulta por hora** .
- Quando uma única barra de uma hora mostrou alterações significativas na proporção entre todos os grupos de duração da consulta vs. outras barras de uma hora para esse conjunto de um (ou seja, as taxas entre as alterações das cores são drasticamente), isso significa que esse conjunto de DataSet demonstrou uma alteração esporádica no desempenho.
- As barras de uma hora que mostram uma parte irregular das consultas de baixa execução, indicaram um TimeSpan em que esse conjunto de tais foi afetado por um efeito vizinho ruidosa, causado por outras atividades de conjuntos de valores.

A imagem abaixo mostra uma hora em 30 de Janeiro, em que um regressivo significativo no desempenho de um conjunto de um DataSet ocorreu, indicado pelo tamanho do Bucket de duração de execução "(3, 10s]". Clicar nessa barra de uma hora revela todos os conjuntos de valores carregados na memória durante esse tempo e, portanto, identificando os conjuntos de data candidatos ao candidato, causando o efeito vizinho barulhento.

![Barra mostrando o pior desempenho por uma grande parte](media/whitepaper-premium-deployment/worst-performing-queries.png)

Depois que um período de tempo problemático é identificado (ou seja, durante 30 de janeiro na imagem acima), o administrador de Power BI pode remover todos os filtros de conjunto de linhas, em seguida, filtrar somente por esse TimeSpan para determinar quais conjuntos de data foram consultados ativamente durante esse tempo. O conjunto de ativos culpado para o efeito de vizinho com ruído é geralmente o conjunto de grandes consultados ou aquele com a duração média mais longa da consulta.

Uma solução para esse problema pode ser distribuir os conjuntos de dados culpado em diferentes espaços de trabalho em diferentes capacidades Premium ou em capacidade compartilhada se houver suporte para o tamanho do conjunto de dados, os requisitos de consumo e os padrões de atualização.

O inverso também pode ser verdadeiro. O administrador de Power BI pode identificar os horários em que um desempenho de consulta de conjunto de um DataSet melhora drasticamente e, em seguida, procura o que desapareceu. Se determinadas informações estiverem ausentes nesse ponto, isso pode ajudar a apontar para o problema de causa.

### <a name="determining-whether-there-is-enough-memory"></a>Determinando se há memória suficiente

Para determinar se há memória suficiente para a capacidade de concluir suas cargas de trabalho, o administrador de Power BI pode consultar o Visual de **porcentagens de memória** consumidas na guia **conjuntos** de aplicativos do aplicativo. **Todos** (total) a memória representa a memória consumida por conjuntos de valores carregados na memória, independentemente de serem consultadas ou processadas ativamente. A memória **ativa** representa a memória consumida pelos conjuntos de valores que estão sendo processados ativamente.

Em uma capacidade íntegra, o Visual terá esta aparência, mostrando uma lacuna entre todas as (total) e a memória ativa:

![Uma capacidade íntegra mostrará uma lacuna entre todas as (total) e a memória ativa](media/whitepaper-premium-deployment/memory-healthy-capacity.png)

Em uma capacidade que está sofrendo pressão de memória, o mesmo Visual mostrará claramente a memória ativa e a convergente de memória total, o que significa que é impossível carregar conjuntos de os adicionais na memória naquele ponto no tempo. Nesse caso, o administrador de Power BI pode clicar em reinicialização de **capacidade** (em **Opções avançadas** da área configurações de capacidade do portal de administração). Reiniciar os resultados da capacidade em todos os conjuntos de dados sendo liberados da memória e permitir que eles recarreguem na memória conforme necessário (por consultas ou atualização de dados).

![\* * Active * * memória convergente com * * toda a * * memória](media/whitepaper-premium-deployment/memory-unhealthy-capacity.png)

### <a name="determining-whether-there-is-enough-cpu"></a>Determinando se há CPU suficiente

Em geral, a utilização média da CPU de uma capacidade deve permanecer abaixo de 80%. Exceder esse valor significa que a capacidade está se aproximando da saturação da CPU.

Os efeitos da saturação de CPU são expressos por operações que demoram mais do que deveriam devido à capacidade de executar muitas opções de contexto de CPU, uma vez que ele tenta processar todas as operações. Em uma capacidade Premium com um alto número de consultas simultâneas, isso é indicado por tempos de espera de consulta altos. Uma conseqüência de tempos de espera de consulta altos é a capacidade de resposta mais lenta do que o normal. O administrador de Power BI pode identificar facilmente quando a CPU é saturada exibindo o Visual de distribuições de **tempo de espera de consulta por hora** . Picos periódicos de contagens de tempo de espera de consulta indicam saturação de CPU potencial.

![Contagens de tempo de espera de picos periódicos de consulta indicam uma possível saturação da CPU](media/whitepaper-premium-deployment/peak-query-wait-times.png)

Um padrão semelhante pode, às vezes, ser detectado em operações em segundo plano se contribuir para a saturação da CPU. Um administrador de Power BI pode procurar um pico periódico em tempos de atualização para um conjunto de uma específico, o que pode indicar a saturação da CPU no momento (provavelmente devido a outras atualizações de conjunto de informações em andamento e/ou consultas interativas). Nessa instância, fazer referência à exibição do **sistema** no aplicativo pode não revelar necessariamente que a CPU está em 100%. A exibição do **sistema** exibe a média de horas, mas a CPU pode ficar saturada por vários minutos de operações pesadas, que aparecem como picos em tempos de espera.

Há mais nuances para ver o efeito da saturação da CPU. Embora o número de consultas que espera seja importante, o tempo de espera da consulta sempre ocorrerá em alguma medida sem causar degradação de desempenho discernida. Alguns conjuntos de resultados (com tempo médio de consulta de mais demorado, que indica complexidade ou tamanho) são mais propensos aos efeitos da saturação da CPU do que outros. Para identificar facilmente esses conjuntos de data, o administrador do Power BI pode procurar alterações na composição de cores das barras no Visual de **distribuição de tempo de espera por hora** . Depois de encontrar uma barra de exceção, eles podem procurar os conjuntos de os que tinham espera de consulta durante esse período e também examinar o tempo médio de espera da consulta em comparação com a duração média da consulta. Quando essas duas métricas são da mesma magnitude e a carga de trabalho da consulta para o conjunto de um não é trivial, é provável que o conjunto de espaço seja afetado pela CPU insuficiente.

Esse efeito pode ser especialmente aparente quando um conjunto de resultados é consumido em pequenos picos de consultas de alta frequência por vários usuários (ou seja, em uma sessão de treinamento), resultando na saturação da CPU durante cada intermitência. Nesse caso, tempos de espera de consulta significativos nesse conjunto de recursos podem ser experimentados, bem como impactar em outros conjuntos de valores na capacidade (efeito de vizinho ruidosa).

Em alguns casos, os administradores do Power BI podem solicitar que os proprietários do conjunto de relatórios criem uma carga de trabalho de consulta menos volátil criando um painel (que consulta periodicamente com qualquer atualização de conjunto de imagem para blocos armazenados em cache) em vez de um relatório. Isso pode ajudar a evitar picos quando o painel é carregado. Essa solução nem sempre pode ser possível para determinados requisitos de negócios, no entanto, pode ser uma maneira eficaz de evitar a saturação da CPU, sem alterar o conjunto de dados.

## <a name="conclusion"></a>Conclusão

O Power BI Premium fornece um desempenho mais consistente, suporte para grandes volumes de dados e a flexibilidade de um autoatendimento unificado e plataforma de BI empresarial para todos em sua organização. Este white paper técnico de nível 300 foi escrito especificamente para administradores de Power BI, além de autores e editores de conteúdo. Ele visa ajudá-los a entender o potencial do Power BI Premium e explicar como projetar, implantar, monitorar e solucionar problemas de soluções escalonáveis.

Para implantar e gerenciar recursos de Power BI Premium, os administradores e os desenvolvedores de modelo exigirão uma compreensão muito boa de como as capacidades funcionam, como elas podem ser gerenciadas e monitoradas e como os modelos podem ser otimizados, para responder adequadamente a problemas de desempenho e afunilamentos devem surgir.

## <a name="end-notes"></a>Notas finais

<a name="endnote-01"></a>\[1\] este documento técnico se preocupa com Power bi Premium que tem suporte apenas do serviço de nuvem Power bi e, portanto, servidor de relatórios do Power bi não está no escopo, exceto para declarar que a licença necessária para instalar o servidor de relatórios do Power bi está incluída em alguns Power BI Premium SKUs.

<a name="endnote-02"></a>\[2\] Power BI como um serviço de nuvem quando usado para inserir conteúdo em nome dos usuários do aplicativo é a PaaS (plataforma como serviço). Esse tipo de incorporação pode ser obtido com dois produtos diferentes, um dos quais é Power BI Premium.

<a name="endnote-03"></a>\[3\] os conjuntos de linhas de envio por push, transmissão e híbrido não são armazenados em capacidades Premium e, portanto, não são uma consideração ao implantar, gerenciar e monitorar capacidades Premium.

<a name="endnote-04"></a>\[4\] as pastas de trabalho do Excel como um tipo de conteúdo Power bi não são armazenadas em capacidades Premium e, portanto, não são uma consideração ao implantar, gerenciar ou monitorar as capacidades Premium.

<a name="endnote-05"></a>\[5\] os visuais podem ser configurados para ignorar interações com a segmentação de elementos. Para obter mais informações, consulte as [interações de visualização em um documento de relatório Power bi](service-reports-visual-interactions.md) .

<a name="endnote-06"></a>\[6\] a diferença no tamanho pode ser determinada comparando o tamanho do arquivo de Power bi desktop com a memória do Gerenciador de tarefas usando para o arquivo.

<a name="endnote-07"></a>\[7\] o suporte para fontes de dados da Microsoft inclui SQL Server, Bricks de dados do Azure, Azure HDInsight Spark (beta), banco de dados SQL do Azure e Azure SQL data warehouse. Para obter informações sobre fontes adicionais, consulte as [fontes de dados com suporte pela consulta direta no documento Power bi](desktop-directquery-data-sources.md) .

<a name="endnote-08"></a>\[8\] Power bi Premium dá suporte ao carregamento de um arquivo de Power bi desktop (. pbix) de até 10 GB de tamanho. Uma vez carregado, um conjunto de um DataSet pode crescer até 12 GB de tamanho como resultado da atualização. O tamanho máximo de upload varia por SKU. Para obter mais informações, consulte o documento [suporte a Power bi Premium para grandes conjuntos de](service-premium-large-datasets.md) dados.

<a name="endnote-09"></a>\[9\] SKUs com menos de quatro núcleos de v não são executados na infraestrutura dedicada. Isso inclui os SKUs EM1, EM2, a1 e a2.

<a name="endnote-10"></a>\[10\] embora sejam raros, os modelos podem ser descarregados da memória devido a operações de serviço.

<a name="endnote-11"></a>\[11\] esses intervalos estão sujeitos a alterações a qualquer momento.

<a name="endnote-12"></a>\[12\] isso é conhecido como várias regiões geográficas, atualmente em visualização. A lógica para uma implantação de várias regiões é normalmente para conformidade corporativa ou governamental, em vez de desempenho e escala. O carregamento de relatório e de Dashboard ainda envolve solicitações para a região de base para metadados. Para obter mais informações, consulte o [suporte de várias regiões para Power bi Premium (versão prévia)](service-admin-premium-multi-geo.md) do documento.

<a name="endnote-13"></a>\[13\] é possível que os usuários possam causar problemas de desempenho sobrecarregando o serviço do Power bi com trabalhos, escrevendo consultas excessivamente complexas, criando referências circulares, etc.

<a name="endnote-14"></a>\[14\] a opção de atribuir os espaços de trabalho de toda a organização não é recomendada e uma abordagem mais direcionada é preferida. Em geral, não é recomendável usar espaços de trabalho pessoais para conteúdo de produção.

<a name="endnote-15"></a>\[15\] é possível monitorar os SKUs no aplicativo ou no portal do Azure, mas não no portal de administração do Power bi. Para monitorar os SKUs, a atualização do relatório falhará se o aplicativo não tiver sido adicionado à função leitor do recurso. Para obter mais informações, consulte o documento [monitorar Power bi Premium e capacidades de Power bi Embedded](service-admin-premium-monitor-capacity.md) .

<a name="endnote-16"></a>\[16\] atualizações podem esperar quando não há CPU ou memória suficiente para iniciar.

<a name="endnote-17"></a>\[17\] o tamanho do conjunto de espaço na memória pode ser maior do que o tamanho em disco em até 20%.

<a name="endnote-18"></a>\[18\] uso médio de memória (GB) e maior consumo de memória (GB)

<a name="endnote-19"></a>\[19\] remoções de conjunto de

<a name="endnote-20"></a>\[20\] consultas de conjunto de data, duração média da consulta do conjunto de tempo (MS), contagem de espera do conjunto de

<a name="endnote-21"></a>\[21\] contagem de alta utilização de CPU e tempo de CPU de maior utilização (últimos sete dias)

<a name="endnote-22"></a>\[22\] contagem de alta utilização de DQ/LC e tempo de DQ/LC de maior utilização (últimos sete dias)