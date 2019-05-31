---
title: Otimize as capacidades do Microsoft Power BI Premium
description: Descreve as estratégias de otimização para as capacidades do Power BI Premium.
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
ms.openlocfilehash: 06712b6bcf57ca84ec03d2c7b99b32ea61ad8c71
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565323"
---
# <a name="optimizing-premium-capacities"></a>Otimizando as capacidades Premium

Quando surgem problemas de desempenho de capacidade Premium, uma primeira abordagem comum é otimizar ou ajustar suas soluções para restaurar os tempos de resposta aceitável. O raciocínio é evitar a compra de mais capacidade Premium, a menos que justificado.

Quando a capacidade de Premium adicional for necessária, há duas opções descritas neste artigo:

- Ampliar uma capacidade Premium existente
- Adicionar uma nova capacidade Premium

Por fim, teste as abordagens e dimensionamento de capacidade Premium concluir este artigo.

## <a name="best-practices"></a>Práticas recomendadas

Ao tentar obter o melhor utilização e desempenho, existem algumas práticas recomendadas, incluindo:

- Usando espaços de trabalho do aplicativo em vez de espaços de trabalho pessoas.
- Separação de negócios críticos e BI de autoatendimento (SSBI) em capacidades diferentes.

  ![Separação de negócios críticos e BI de autoatendimento em capacidades diferentes](media/service-premium-capacity-optimize/separate-capacities.png)

- Se o compartilhamento de conteúdo somente com usuários do Power BI Pro, não pode haver nenhuma necessidade de armazenar o conteúdo em uma capacidade dedicada.
- Use as capacidades dedicadas quando procurar para alcançar um tempo de atualização específico, ou quando os recursos específicos são necessários. Por exemplo, com grandes conjuntos de dados ou relatórios paginados.

### <a name="addressing-common-questions"></a>Responder a questões comuns

Otimizar as implantações do Power BI Premium é um assunto complexo que envolve um entendimento dos requisitos de carga de trabalho, recursos disponíveis e seu uso efetivo.

Este artigo aborda as sete perguntas comuns de suporte, que descreve possíveis problemas e explicações e obter informações sobre como identificar e resolvê-los.

### <a name="why-is-the-capacity-slow-and-what-can-i-do"></a>Por que é a capacidade lenta, e o que devo fazer?

Há muitas razões podem contribuir para uma capacidade Premium lenta. Essa questão ainda mais requer informações para entender o que significa lenta. Relatórios são lentos para carregar? Ou eles estão falhando ao carregar? Elementos visuais de relatório são lentas para carregar ou atualizar quando os usuários interagem com o relatório? Quais são atualizadas levando mais tempo para conclusão de que o esperado ou anteriormente experimentado?

Tendo obtido um entendimento do motivo, você pode começar a investigar. As respostas às seguintes seis perguntas ajudará você a resolver mais problemas específicos.

### <a name="what-content-is-using-up-my-capacity"></a>O conteúdo que está usando minha capacidade?

Você pode usar o **métricas de capacidade do Power BI Premium** aplicativo filtrar por capacidade e analisar as métricas de desempenho para o conteúdo do espaço de trabalho. É possível examinar o uso de recursos e as métricas de desempenho por hora nos últimos sete dias para todo o conteúdo armazenado dentro da capacidade Premium. Monitoramento costuma ser a primeira etapa a ser tomada quando a solução de problemas de uma preocupação geral sobre o desempenho de capacidade Premium.

Para monitorar métricas-chave incluem:

- Média de CPU e a contagem de alta utilização.
- Média de memória e contagem de alta utilização e uso de memória para conjuntos de dados específicos, fluxos de dados e relatórios paginados.
- Conjuntos de dados ativos carregados na memória.
- Durações de consulta de média e máxima.
- Tempos de espera médio de consulta.
- Fluxo de dados e o conjunto de dados média atualizar vezes.

No aplicativo de métricas de capacidade do Power BI Premium, a memória ativa mostra a quantidade total de memória fornecida a um relatório que não pode ser removido porque ele está em uso nos últimos três minutos. Um pico alta no tempo de espera de atualização pode estar correlacionado com um conjunto de dados grande e/ou ativo.

O **Top 5 por duração média** gráfico destaca os cinco principais conjuntos de dados, relatórios paginados e consumindo recursos de capacidade de fluxos de dados. Conteúdo os cinco melhores listas é candidatos para otimização de investigação e possíveis.

### <a name="why-are-reports-slow"></a>Por que são relatórios lento?

As tabelas a seguir mostram os possíveis problemas e maneiras de identificar e lidar com eles.

#### <a name="insufficient-capacity-resources"></a>Recursos de capacidade insuficiente

| Possíveis explicações | Como identificar | Como resolver |
| --- | --- | --- |
| Alta memória ativa total (modelo não pode ser removido porque ele está em uso nos últimos três minutos).<br><br> Tempos de espera de vários picos alta na consulta.<br><br> Tempos de espera de vários picos alta na atualização. | Monitorar as métricas de memória \[ [1](#endnote-1)\]e as contagens de remoção \[ [2](#endnote-2)\]. | Diminuir o tamanho do modelo, ou converter para o modo DirectQuery. Consulte a [otimizando modelos](#optimizing-models) seção neste artigo.<br><br> A capacidade de expansão.<br><br> Atribua o conteúdo a uma capacidade diferente. |

#### <a name="inefficient-report-designs"></a>Designs de relatório ineficiente

| Possíveis explicações | Como identificar | Como resolver |
| --- | --- | --- |
| As páginas do relatório contém muitos elementos visuais (filtragem interativa pode disparar pelo menos uma consulta por visual).<br><br> Elementos visuais recuperam mais dados que o necessário. | Examine os designs de relatório.<br><br> Usuários de relatório para entender como eles interagem com os relatórios de entrevista.<br><br> Monitorar as métricas de consulta de conjunto de dados \[ [3](#endnote-3)\]. | Relatórios de reformulação com menos visuais por página. |

#### <a name="dataset-is-slow-especially-when-reports-have-previously-performed-well"></a>Conjunto de dados é lento, especialmente quando os relatórios anteriormente tem executado bem

| Possíveis explicações | Como identificar | Como resolver |
| --- | --- | --- |
| Cada vez mais grandes volumes de dados de importação.<br><br> Lógica de cálculo complexo ou ineficiente, incluindo funções RLS.<br><br> Modelo não totalmente otimizado.<br><br> (DQ/LC) Latência do gateway.<br><br> DQ origem consulta tempos de resposta lentos. | Examine os designs de modelo.<br><br> Monitorar os contadores de desempenho do gateway. | Consulte a [otimizando modelos](#optimizing-models) seção neste artigo. |

#### <a name="high-concurrent-report-usage"></a>Uso de relatórios simultâneas alta

| Possíveis explicações | Como identificar | Como resolver |
| --- | --- | --- |
| Tempos de espera de consulta altas.<br><br> Saturação da CPU.<br><br> Limites de conexão do DQ/LC excedidos. | Monitorar a utilização de CPU \[ [4](#endnote-4)\], tempos de espera de consulta e a utilização de DQ/LC \[ [5](#endnote-5) \] métricas + durações de consulta. Se flutuante, pode indicar problemas de simultaneidade. | A capacidade de escalar verticalmente, ou atribuir o conteúdo a uma capacidade diferente.<br><br> Relatórios de reformulação com menos visuais por página. |

**Observações:**    
<a name="endnote-1"></a>\[1\] média de uso de memória (GB) e o mais alto consumo de memória (GB).   
<a name="endnote-2"></a>\[2\] remoções de conjunto de dados.   
<a name="endnote-3"></a>\[3\] consultas de conjunto de dados, duração da consulta de conjunto de dados média (ms), conjunto de dados aguarde contagem e o tempo de espera médio do conjunto de dados (ms).   
<a name="endnote-4"></a>\[4\] alta contagem de utilização da CPU e tempo de CPU de utilização mais alta (últimos sete dias).   
<a name="endnote-5"></a>\[5\] DQ/LC alta contagem de utilização e a hora DQ/LC da maior utilização (últimos sete dias).   

### <a name="why-are-reports-not-loading"></a>Por que são os relatórios não está carregando?

Quando os relatórios de falham ao carregar, ele é um sinal-se de que a capacidade não tem memória suficiente e é excessivamente aquecida. Isso pode ocorrer quando todos os modelos carregados estão sendo consultados ativamente e portanto não podem ser removidos e qualquer operação de atualização ter sido pausada ou atrasada. O serviço do Power BI tentará carregar o conjunto de dados por 30 segundos e, normalmente, o usuário é notificado da falha com uma sugestão para tentar novamente em breve.

Atualmente, não há nenhuma métrica para monitorar os relatórios de falhas de carregamento. Você pode identificar o potencial para esse problema, memória do sistema de monitoramento, especificamente a mais alta utilização e tempo de utilização mais alta. Remoções de conjunto de dados de alta e longa dataset tempo de espera médio de atualização podem sugerir que esse problema está ocorrendo.

Se isso ocorrer somente ocasionalmente muito, isso pode não ser considerado um problema de prioridade. Os usuários de relatório serão informados que o serviço está ocupado e que deve tentar novamente após alguns instantes. Se isso acontecer com muita frequência, o problema pode ser resolvido pelo aumento da capacidade Premium, ou atribuindo o conteúdo a uma capacidade diferente.

Administradores de capacidade (e os administradores de serviço do Power BI) pode monitorar o **falhas de consulta** métrica para determinar quando isso acontece. Eles também podem reiniciar a capacidade, redefinir todas as operações no caso de sobrecarga do sistema.

### <a name="why-are-refreshes-not-starting-on-schedule"></a>Por que as atualizações não estão iniciando em agendamento?

Não há garantia de horas de início da atualização agendada. Lembre-se de que o serviço do Power BI sempre será priorizar operações interativas sobre operações em segundo plano. A atualização é uma operação em segundo plano que pode ocorrer quando duas condições forem atendidas:

- Não há memória suficiente
- O número de atualizações simultâneas com suporte para a capacidade de Premium não for excedido

Quando as condições não forem atendidas, a atualização está na fila até que as condições forem favoráveis.

Para uma atualização completa, lembre-se de que pelo menos duas vezes o tamanho de memória atual do conjunto de dados é necessária. Se não tiver memória suficiente disponível, a atualização não pode começar até que a remoção do modelo libera memória - isso significa atrasos até que um ou mais conjuntos de dados se torna inativo e podem ser removido.

Lembre-se de que o número de atualizações simultâneas máximo com suporte é definido como 1,5 vezes os back-end núcleos, arredondados para cima.

Uma atualização agendada falhará quando ele só poderá ser iniciado antes da próxima atualização agendada está prestes a começar. Uma atualização sob demanda que disparou manualmente na interface de usuário tentará executar até três vezes antes de falhar.

Administradores de capacidade (e os administradores de serviço do Power BI) pode monitorar o **Refresh tempo de espera médio (minutos)** métrica para determinar a latência média entre o horário agendado e o início da operação.

Enquanto geralmente não atualiza uma prioridade administrativa, para influenciar a dados em tempo, verifique se há memória suficiente disponível. Isso pode envolver a isolar os conjuntos de dados para as capacidades com recursos suficientes conhecidos. Também é possível que os administradores poderiam coordenar com os proprietários de conjunto de dados para ajudar a escalonar ou reduzir os tempos de atualização de dados agendada para minimizar colisões. Observe que não é possível que um administrador exibir a fila de atualização, ou recuperar o conjunto de dados de agenda.

### <a name="why-are-refreshes-slow"></a>Por que são atualizações lentas?

Atualizações podem ser lento - ou percebida lenta (como os endereços de pergunta comum anterior).

Quando na verdade, a atualização estiver lenta, pode ser devido a vários motivos:

- CPU insuficientes (atualização pode ser muito intensivo de CPU).
- Memória insuficiente, resultando em pausa de atualização (que exige a atualização para iniciar novamente quando as condições forem favoráveis recomeçar).
- Capacidade de não motivos, incluindo a capacidade de resposta de sistema de fonte de dados, latência de rede, permissões inválidas ou taxa de transferência de gateway.
- Volume de dados - um bom motivo para configurar incremental atualização, conforme discutido abaixo.

Administradores de capacidade (e os administradores de serviço do Power BI) pode monitorar o **Refresh média duração (minutos)** métrica para determinar um parâmetro de comparação para comparação com o tempo e o **atualização de tempo de espera médio (minutos)** métricas para determinar a latência média entre média de latência entre o horário agendado e o início da operação.

Atualização incremental pode reduzir significativamente a duração da atualização de dados, especialmente para tabelas de modelo grande. Há quatro benefícios associados com a atualização incremental:

- **As atualizações são mais rápidas** - apenas um subconjunto de uma tabela precisa carregar, reduzindo o uso da CPU e memória, e o paralelismo pode ser superior ao atualizar várias partições.
- **As atualizações ocorrem apenas quando necessário** -políticas de atualização Incremental podem ser configuradas para carregar apenas quando os dados foram alterados.
- **As atualizações são mais confiáveis** -conexões em execução mais curtas para sistemas de fonte de dados voláteis são menos suscetíveis a desconexão.
- **Modelos permanecem corte** -políticas de atualização Incremental podem ser configuradas para remover automaticamente o histórico, além de uma janela deslizante de tempo.

Para obter mais informações, consulte [Incremental de atualização no Power BI Premium](service-premium-incremental-refresh.md).

### <a name="why-are-data-refreshes-not-completing"></a>Por que são dados atualiza não concluir?

Quando a atualização de dados começa, mas não for concluída, pode ser devido a vários motivos:

- Memória insuficiente, mesmo se houver apenas um modelo na capacidade Premium, ou seja, o tamanho do modelo é muito grande.
- Motivos de não-capacidade, incluindo a desconexão de sistema de fonte de dados, permissões inválidas ou erro de gateway.

Administradores de capacidade (e os administradores de serviço do Power BI) pode monitorar o **Refresh falhas devido à memória insuficiente** métrica.

## <a name="optimizing-models"></a>Otimizando modelos

Design de modelo ideal é crucial para o fornecimento de uma solução eficiente e escalonável. No entanto, está além do escopo deste artigo para fornecer uma discussão completa. Em vez disso, esta seção fornecerá áreas-chave para consideração durante a otimização de modelos.

### <a name="optimizing-power-bi-hosted-models"></a>Otimizando o Power BI hospedados modelos

Otimizar modelos hospedados em uma capacidade Premium pode ser obtido nas camadas de m e o modelo.

Considere as possibilidades de otimização para um modelo de importação:

![Possibilidades de otimização para um modelo de importação](media/service-premium-capacity-optimize/import-model-optimizations.png)

Na camada de fonte de dados:

- Fontes de dados relacionais podem ser otimizadas para garantir que o mais rápido possível de atualização com pré-integração de dados, aplicando índices apropriados, definindo as partições de tabela que se alinham a atualização incremental períodos e cálculos a materialização (em vez de calculados tabelas e colunas de modelo) ou a adição de lógica de cálculo para modos de exibição.
- Fontes de dados não relacionais podem ser previamente integrados com repositórios relacionais.
- Certifique-se de que os gateways possuem recursos suficientes, preferencialmente em computadores dedicados, com largura de banda suficiente e, em estreita proximidade com as fontes de dados.

Na camada de modelo:

- Design de consulta do Power Query pode minimizar ou remover transformações complexas e especialmente aquelas que diferentes fontes de dados (data warehouse conseguir isso durante sua fase de extração, transformação e carregamento) de mesclagem. Além disso, garantindo níveis de privacidade essa fonte de dados apropriado são definidos, isso pode evitar a necessidade de Power BI para carregar os resultados completos para produzir um resultado combinado em consultas.
- A estrutura do modelo determina os dados a serem carregados e tem um impacto direto sobre o tamanho do modelo. Ele pode ser projetado para evitar o carregamento de dados desnecessários, removendo colunas, remover linhas (especialmente os dados históricos) ou pelo carregamento de dados resumidos (a custa de carregamento de dados detalhados). Redução de tamanho significativo pode ser obtida, removendo colunas de alta cardinalidade (especialmente a colunas de texto) que não armazenar ou compactar com muita eficiência.
- Desempenho de consulta do modelo pode ser melhorado configurando relações de direção única, a menos que haja um motivo convincente para permitir a filtragem bidirecional. Considere também usar o [CROSSFILTER](https://docs.microsoft.com/dax/crossfilter-function) função em vez de filtragem bidirecional.
- Tabelas de agregação podem alcançar consulta rápida respostas Carregando previamente resumidos dados, no entanto, isso aumentará o tamanho do modelo e o resultado em tempos de atualização. Em geral, as tabelas de agregação devem ser reservadas para modelos muito grandes ou projetos de modelo composto.
- Colunas e tabelas calculadas aumentam o tamanho do modelo e resultam em tempos de atualização. Em geral, um tamanho menor de armazenamento e o tempo mais rápido de atualização podem ser obtidos quando os dados são materializados ou calculados na fonte de dados. Se isso não for possível, usar colunas personalizadas do Power Query pode oferecer armazenamento aprimorada de compactação.
- Pode haver uma oportunidade para ajustar expressões DAX para medidas e as regras RLS, talvez reescrever a lógica para evitar a caras fórmulas
- Atualização incremental drasticamente pode reduzir o tempo de atualização e conservar a memória e CPU. A atualização incremental também pode ser configurada para remover dados históricos, mantendo os tamanhos de modelo de corte.
- Um modelo pode ser reprojetado como modelos quando há padrões de consulta diferentes e conflitantes. Por exemplo, alguns relatórios agregados de alto nível presentes em todos os histórico e pode toleram a latência de 24 horas. Outros relatórios estão preocupados com dados atuais e precisam de acesso granular para transações individuais. Em vez de design de um único modelo para atender a todos os relatórios, crie dois modelos otimizados para cada requisito.

Considere as possibilidades de otimização para um modelo DirectQuery. Como o modelo emite solicitações de consulta à fonte de dados subjacente, otimização de fonte de dados é essencial para o fornecimento de consultas de modelo responsivo.

 ![Possibilidades de otimização para um modelo DirectQuery](media/service-premium-capacity-optimize/direct-query-model-optimizations.png)

Na camada de fonte de dados:

- A fonte de dados pode ser otimizada para garantir que a consulta mais rápido possível integrando previamente os dados (que não não possíveis na camada de modelo), a aplicação de índices apropriados, definir as partições de tabela, a materialização resumidos dados (com exibições indexadas), e minimizar a quantidade de cálculo. A melhor experiência é obtida quando consultas passagem precisam apenas de filtro e executar junções internas entre os modos de exibição ou tabelas indexadas.
- Certifique-se de que os gateways possuem recursos suficientes, preferencialmente em computadores dedicados, com largura de banda suficiente e, em estreita proximidade com a fonte de dados.

Na camada de modelo:

- Consulta do Power Query designs preferencialmente devem ser aplicados sem transformações - caso contrário, tente manter as transformações para absoluta mínimo.
- Desempenho de consulta do modelo pode ser melhorado configurando relações de direção única, a menos que haja um motivo convincente para permitir a filtragem bidirecional. Além disso, as relações do modelo devem ser configuradas para assumir a integridade referencial é imposta (quando esse for o caso) e resultará em consultas de fonte de dados usando as junções mais eficientes (em vez de junções externas).
- Evite criar colunas personalizadas de consulta Power Query ou coluna calculada de modelo - materializar essas na fonte de dados, quando possível.
- Talvez haja oportunidade para ajustar expressões DAX para medidas e as regras RLS, talvez reescrever a lógica para evitar a caras fórmulas.

Considere as possibilidades de otimização para um modelo de composição. Lembre-se de que um modelo de composição permite uma combinação de importação e DirectQuery tabelas.

![Possibilidades de otimização para um modelo de composição](media/service-premium-capacity-optimize/composite-model-optimizations.png)

- Em geral, a otimização para modelos de importação e DirectQuery se aplicam às tabelas de modelo composto que usam esses modos de armazenamento.
- Normalmente, se esforçam para chegar a um design equilibrado por meio da configuração de tabelas do tipo de dimensão (que representa as entidades de negócios) como duplo modo e o tipo de fato tabelas de armazenamento (tabelas grandes com frequência, que representam fatos operacionais) como modo de armazenamento DirectQuery. Modo de armazenamento duplo significa que ambos importar e modos de armazenamento do DirectQuery e isso permite que o serviço do Power BI determinar o modo de armazenamento mais eficiente para usar ao gerar uma consulta nativa de passagem.
- Certifique-se de que os gateways possuem recursos suficientes, preferencialmente em computadores dedicados, com largura de banda suficiente e, em estreita proximidade com as fontes de dados
- Tabelas de agregações configurado como modo de armazenamento de importação pode fornecer aprimoramentos de desempenho de consulta dramática quando usados para resumir as tabelas de fatos-tipo de modo de armazenamento DirectQuery. Nesse caso, aumentará o tamanho do modelo e aumentar o tempo de atualização de tabelas de agregação e geralmente é uma compensação aceitável para consultas mais rápidas.

### <a name="optimizing-externally-hosted-models"></a>Otimizando externamente hospedado modelos

Muitas possibilidades de otimização discutidas a [otimizando o Power BI hospedados modelos](#optimizing-power-bi-hosted-models) seção também se aplicam a modelos desenvolvidos com o Azure Analysis Services e o SQL Server Analysis Services. Limpar exceções são determinados recursos que não são atualmente suportados, incluindo modelos de composição e tabelas de agregação.

Uma consideração adicional sobre os conjuntos de dados hospedados externamente é o banco de dados de hospedagem em relação ao serviço do Power BI. Para o Azure Analysis Services, isso significa criar o recurso do Azure na mesma região que o locatário do Power BI (região de residência). Para SQL Server Analysis Services, para IaaS, isso significa que hospeda a VM na mesma região e para o local, isso significa que garantir uma instalação do gateway eficiente.

Como um aparte, é interessante observar que os bancos de dados do Azure Analysis Services e bancos de dados tabulares do SQL Server Analysis Services exigem que seus modelos carregados totalmente na memória e que eles permanecem lá em todos os momentos para dar suporte à consulta. Como o serviço do Power BI, deve haver memória suficiente para se atualizar se o modelo deve permanecer online durante a atualização. Ao contrário do serviço do Power BI, não há nenhum conceito de que os modelos são automaticamente antigos dentro e fora de memória de acordo com o uso. O Power BI Premium, portanto, oferece uma abordagem mais eficiente para maximizar a consulta de modelo com o uso de memória inferior.

## <a name="capacity-planning"></a>Planejamento de capacidade

O tamanho de uma capacidade Premium determina sua memória disponível e os recursos de processador e os limites impostos na capacidade. O número de capacidades Premium também é uma consideração, como criação de vários Premium capacidades podem ajudar a isolar as cargas de trabalho umas das outras. Observe que o armazenamento é 100 TB por nó de capacidade, e isso provavelmente será mais do que suficiente para qualquer carga de trabalho.

Determinar o tamanho e o número de capacidades Premium pode ser desafiador, especialmente para as capacidades inicias que você cria. A primeira etapa ao dimensionamento de capacidade é entender a carga de trabalho média que representa o uso diário esperado. É importante entender que nem todas as cargas de trabalho são iguais. Por exemplo, no fim de um espectro - 100 usuários simultâneos que acessam uma única página de relatório que contém um único visual é facilmente realizável. Ainda - na outra extremidade do espectro - 100 usuários simultâneos acessam 100 relatórios diferentes, cada um com 100 visuais na página do relatório, será muito diferentes demandas de recursos de capacidade de fazer.

Os administradores de capacidade, portanto, serão necessário considerar vários fatores específicos ao seu ambiente, o conteúdo e o uso esperado. O objetivo de substituição é maximizar a utilização da capacidade oferecendo os tempos de consulta consistentes, tempos de espera aceitável e taxas de remoção. Fatores a serem considerados incluem:

- **Características de tamanho e os dados de modelo** -modelos de importação devem ser totalmente carregados na memória para permitir que a atualização ou consulta. LC/DQ conjuntos de dados podem exigir muito tempo do processador e memória significativa, possivelmente, para avaliar medidas complexas ou regras RLS. Taxa de transferência de consulta LC/DQ e tamanho de processador e memória são restritas pelo tamanho da capacidade.
- **Modelos active simultâneos** -a consulta simultâneas dos modelos de importação diferente fornecerá melhor capacidade de resposta e o desempenho quando eles permanecem na memória. Deve haver memória suficiente para hospedar todos os modelos intensamente consultados, com memória adicional para permitir a sua atualização.
- **Atualização do modelo de importação** -o tipo de atualização (completo ou incremental), a duração e a complexidade de consultas do Power Query e a lógica de tabela/coluna calculada podem impactar na memória e uso do processador especialmente. Atualizações simultâneas são restritas pelo tamanho da capacidade (1,5 x backend núcleos, arredondados para cima).
- **Consultas simultâneas** -várias consultas simultâneas podem resultar em relatórios sem resposta quando o processador ou LC/DQ conexões excede o limite de capacidade. Isso é especialmente o caso para páginas de relatório que incluem muitos visuais.
- **Fluxos de dados e relatórios paginados** -a capacidade pode ser configurada para dar suporte a fluxos de dados e relatórios paginados, cada um exigindo uma configurável porcentagem máxima de memória de capacidade. Memória dinamicamente alocada para fluxos de dados, mas é estaticamente alocada para relatórios paginados.

Além desses fatores, os administradores de capacidade podem pensar em criar várias capacidades. Várias capacidades permitem o isolamento de cargas de trabalho e podem ser configuradas para garantir que as cargas de trabalho de prioridade têm a garantia de recursos. Por exemplo, duas capacidades podem ser criadas para separar as cargas de trabalho essenciais aos negócios de cargas de trabalho de Self-service BI (SSBI). A capacidade de críticos de negócios pode ser usada para isolar grandes modelos corporativos, fornecendo a eles com recursos garantidos, com a criação de acesso concedido apenas ao departamento de TI. A capacidade SSBI pode ser usada para hospedar um número crescente de modelos menores, com acesso concedido a analistas de negócios. A capacidade SSBI às vezes pode enfrentar esperas de consulta ou atualização toleráveis.

Ao longo do tempo, os administradores de capacidade pode equilibrar os espaços de trabalho entre as capacidades, movendo o conteúdo entre espaços de trabalho ou espaços de trabalho entre as capacidades e expandindo as capacidades para cima ou para baixo. Em geral, para modelos de host maiores escala vertical e para maior simultaneidade de escalar horizontalmente.

Lembre-se de que a comprar uma licença fornece ao locatário núcleos. A compra de um **P3** assinatura pode ser usada para criar uma ou, até quatro capacidades de Premium, ou seja, 1 x P3, ou 2 vezes P2 ou 4 x P1. Além disso, antes de upsizing uma capacidade de P2 a uma capacidade P3, consideração pode ser fornecida para dividir os núcleos virtuais para criar duas capacidades de P1.

## <a name="testing-approaches"></a>Abordagens de teste

Depois que um tamanho de capacidade é decidido, testes podem ser executadas com a criação de um ambiente controlado. É uma opção econômica e prática criar uma capacidade do Azure (SKUs a), observar que uma capacidade de P1 é o mesmo tamanho de uma capacidade de A4, P2 e P3 capacidades do mesmo tamanho que as capacidades de A5 e A6, respectivamente. As capacidades do Azure podem ser criadas rapidamente e são cobradas por hora. Assim, depois que o teste for concluído, eles podem ser facilmente excluídos para interromper o acúmulo de custos.

O conteúdo de teste pode ser adicionado a espaços de trabalho criados na capacidade do Azure e, em seguida, como um único usuário pode executar relatórios para gerar uma carga de trabalho real e representativa das consultas. Se não houver modelos de importação, uma atualização para cada modelo deve ser realizada também. Ferramentas de monitoramento, em seguida, podem ser usada para examinar todas as métricas para entender a utilização de recursos.

É importante que os testes são repetidos. Testes devem ser executados várias vezes e eles devem fornecer aproximadamente o mesmo resultado cada vez. Uma média desses resultados pode ser usada para extrapolar e estimar uma carga de trabalho sob condições de produção true.

Para gerar um teste de estresse, considere desenvolver uma aplicativo para simular a carga de trabalho real de teste de carga. As especificações de como fazer isso estão fora do escopo deste artigo. Para obter mais informações, incluindo um exemplo de código, consulte o [carregar um teste de aplicativos do Power BI com o teste de carga do Visual Studio](https://blogs.msdn.microsoft.com/charles_sterling/2018/04/04/webinar-load-testing-power-bi-applications-with-visual-studio-load-test/) webinar.

## <a name="acknowledgements"></a>Confirmações

Este artigo foi escrito por Peter Myers, MVP de plataforma de dados e independente profissional de BI com [bit a bit soluções](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Próximas etapas

> [!div class="nextstepaction"]
> [Cenários de capacidade Premium](service-premium-capacity-scenarios.md)   
  
Mais perguntas? [Experimente perguntar à Comunidade do Power BI](https://community.powerbi.com/)

||||||