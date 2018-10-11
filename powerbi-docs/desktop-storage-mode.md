---
title: Usar o Modo de armazenamento no Power BI Desktop (versão prévia)
description: Usar o Modo de Armazenamento para controlar se os dados são armazenados em cache na memória para relatórios no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 09/17/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: ce4aab1a477485a30a4166d86d166a4ac289108f
ms.sourcegitcommit: 698b788720282b67d3e22ae5de572b54056f1b6c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45974220"
---
# <a name="storage-mode-in-power-bi-desktop-preview"></a>Modo de armazenamento no Power BI Desktop (versão prévia)

No **Power BI Desktop** é possível especificar o **modo de armazenamento** de tabelas, para que você tenha o controle sobre se os dados da tabela são armazenados em cache na memória para os relatórios. 

![Modo de armazenamento no Power BI Desktop](media/desktop-storage-mode/storage-mode_01.png)

Definir o **modo de armazenamento** oferece muitas vantagens. É possível definir o **modo de armazenamento** para cada tabela individualmente no modelo, permitindo que um único conjunto de dados tire proveito de uma ou muitas das seguintes vantagens:

* **Desempenho de consulta**: conforme os usuários interagem com os elementos visuais nos relatórios do Power BI, as consultas DAX são enviadas para o conjunto de dados. O armazenamento de dados em cache na memória com a configuração adequada do **modo de armazenamento** pode melhorar o desempenho da consulta e a interatividade dos relatórios.
* **Grandes conjuntos de dados**: tabelas que não são armazenados em cache não consomem memória para fins de cache. Você pode habilitar a análise interativa de amplos conjuntos de dados que são muito grandes ou caros para armazenar completamente em cache na memória. É possível escolher quais tabelas valem a pena ser armazenadas em cache e quais não são.
* **Otimização de atualização de dados**: as tabelas que não são armazenadas em cache não precisam ser atualizadas. É possível reduzir os períodos de atualização fazendo o armazenamento em cache apenas dos dados necessários para atender aos contratos de nível de serviço e aos requisitos comerciais.
* **Requisitos quase em tempo real**: as tabelas com requisitos quase em tempo real podem se beneficiar de não serem armazenadas em cache, para reduzir a latência de dados.
* **Write-back**: o write-back permite que os usuários corporativos explorem cenários hipotéticos alterando os valores das células. Aplicativos personalizados podem aplicar as alterações à fonte de dados. As tabelas não armazenadas em cache podem refletir as alterações de imediato, permitindo a análise instantânea dos efeitos.

A definição do **modo de armazenamento** no **Power BI Desktop** é um dos três recursos relacionados:

* **Modelos compostos**: permite que um relatório tenha várias conexões de dados, incluindo conexões DirectQuery ou importação, em qualquer combinação.
* **Relações muitos para muitos**: com **modelos compostos**, você pode estabelecer **relações muitos para muitos** entre tabelas, removendo os requisitos para valores exclusivos nas tabelas e removendo soluções alternativas anteriores, como introduzir novas tabelas apenas para estabelecer relações. 
* **Modo de armazenamento**: agora é possível especificar que elementos visuais exigem uma consulta a fontes de dados de back-end. Os que não exigem são importados, mesmo que baseados no DirectQuery, melhorando o desempenho e reduzindo a carga de back-end. Antes, mesmo elementos visuais simples como as segmentações de dados iniciavam consultas sendo enviadas para fontes de back-end. 

Esta coleção de três recursos relacionados para os **modelos compostos** é descrita em artigos separados:

* Os **modelos compostos** são descritos em detalhes no próprio artigo, [Modelos compostos no Power BI Desktop (prévia)](desktop-composite-models.md).
* As **Relações muitos para muitos** são descritas no próprio artigo [Relações muitos para muitos no Power BI Desktop (prévia)](desktop-many-to-many-relationships.md).
* O **modo de armazenamento** é descrito em detalhes neste artigo.

## <a name="enabling-the-storage-mode-preview-feature"></a>Habilitar o recurso de visualização do modo de armazenamento

O recurso de **modo de armazenamento** está em versão prévia e deve ser habilitado no **Power BI Desktop**. Para habilitar o **modo de armazenamento**, selecione **Arquivo > Opções e configurações > Opções > Recursos de visualização**, depois selecione a caixa de seleção **modelos compostos**. 

![habilitando recursos de versão prévia](media/desktop-composite-models/composite-models_02.png)

Será preciso reiniciar o **Power BI Desktop** para que o recurso seja habilitado.

![reinicialização necessária para que as alterações entrem em vigor](media/desktop-composite-models/composite-models_03.png)


## <a name="using-the-storage-mode-property"></a>Usar a propriedade de modo de armazenamento

O **modo de armazenamento** é uma propriedade que pode ser definida em cada tabela do modelo. Para definir o **modo de armazenamento**, selecione a tabela no painel **Campos** e clique com o botão direito do mouse para abrir o menu de contexto. No menu de contexto, selecione **Propriedades**.

![Seleção de Propriedades no menu de contexto](media/desktop-storage-mode/storage-mode_02.png)

A seleção do **modo de armazenamento** aparece no painel **Propriedades do campo**  para a tabela. A partir daí, é possível exibir o **modo de armazenamento** atual ou modificá-lo.

![Definição do modo de armazenamento para uma tabela](media/desktop-storage-mode/storage-mode_03.png)

Há três valores para o **modo de armazenamento**:

* **Importação**: quando definidas para **Importação**, as tabelas importadas são armazenadas em cache. As consultas enviadas para o conjunto de dados do Power BI que retornam dados das tabelas de Importação só podem ser atendidas de dados armazenados em cache.
* **DirectQuery**: com essa configuração, as tabelas DirectQuery não são armazenadas em cache. As consultas enviadas para o conjunto de dados do Power BI (por exemplo, as consultas DAX) que retornam dados das tabelas do DirectQuery só podem ser atendidas por meio da execução de consultas sob demanda à fonte de dados. As consultas enviadas à fonte de dados usam a linguagem de consulta para essa fonte de dados (por exemplo, SQL).
* **Dupla**: as tabelas duplas podem se comportar como armazenadas em cache ou não, dependendo do contexto da consulta enviada para o conjunto de dados do Power BI. Em alguns casos, as consultas são atendidas de dados armazenados em cache; em outros, as consultas são atendidas por meio da execução de uma consulta sob demanda à fonte de dados.

Alterar uma tabela para Importação é uma operação *irreversível*; ela não pode ser revertida para o DirectQuery nem para Dupla.

## <a name="constraints-on-directquery-and-dual-tables"></a>Restrições em tabelas duplas e do DirectQuery

As tabelas duplas estão sujeitas às mesmas restrições que as do DirectQuery. Entre elas estão as transformações em M limitadas e as funções restritas do DAX em colunas calculadas. Veja mais informações em [Implicações do uso do DirectQuery](desktop-directquery-about.md#implications-of-using-directquery).

## <a name="relationship-rules-on-tables-with-different-storage-modes"></a>Regras de relação em tabelas com diferentes modos de armazenamento

As relações devem atender às regras baseadas no**modo de armazenamento** das tabelas relacionadas. Esta seção fornece exemplos de combinações válidas. Veja informações completas em [relações muitos para muitos no Power BI Desktop (prévia)](desktop-many-to-many-relationships.md).

Em um conjunto de dados com uma única fonte de dados, são válidas as seguintes combinações de relações **um para muitos**:

| Tabela do lado **muitos** | Tabela do lado **um** |
| ------------- |----------------------| 
| Dupla          | Dupla                 | 
| Importar        | Importar ou Dupla       | 
| DirectQuery   | DirectQuery ou Dupla  | 

## <a name="propagation-of-dual"></a>Propagação de Dupla
Vejamos um exemplo. Considere o seguinte modelo simples, em que todas as tabelas são de uma única fonte que dá suporte à Importação e DirectQuery.

![Exemplo da exibição de relações para o modo de armazenamento](media/desktop-storage-mode/storage-mode_04.png)

Digamos que, de início, todas as tabelas nesse modelo sejam do tipo DirectQuery. Se alterarmos, então, o **modo de armazenamento** da tabela *SurveyResponse* para Importação, o seguinte aviso aparece:

![Caixa de diálogo de aviso do modo de armazenamento](media/desktop-storage-mode/storage-mode_05.png)

As tabelas de dimensões (*Cliente*, *Data* e *Geografia*) devem ser definidas como **Dupla** em conformidade com as regras de relação descritas anteriormente. Em vez de exigir que essas tabelas sejam definidas como **Dupla** antecipadamente, elas podem ser definidas em uma única operação.

A lógica de propagação é projetada para ajudar com os modelos que contêm muitas tabelas. Digamos que você tenha um modelo com 50 tabelas e que apenas determinadas tabelas de fatos (transacionais) precisem ser armazenadas em cache. A lógica no **Power BI Desktop** descobre o conjunto mínimo de tabelas de dimensão que precisa ser definido como **Duplo** para que você não precise fazer isso.

A lógica de propagação percorre somente em direção a um dos lados das relações **um para muitos**.

* Não é permitido alterar a tabela *Cliente* para **Importação** (em vez de alterar *SurveyResponse*) por causa de suas relações com as tabelas DirectQuery *Vendas* e *SurveyResponse*.
* É permitido alterar a tabela *Cliente* para **Dupla** (em vez de alterar *SurveyResponse*). A lógica de propagação define a tabela *Geografia* para também ser **Dupla**.

## <a name="storage-mode-usage-example"></a>Exemplo de uso do modo de armazenamento
Continuemos com o exemplo da seção anterior e imaginemos a aplicação das seguintes configurações de propriedade do **modo de armazenamento**:

| Tabela                   | Modo de armazenamento         |
| ----------------------- |----------------------| 
| *Vendas*                 | DirectQuery          | 
| *SurveyResponse*        | Importar               | 
| *Data*                  | Dupla                 | 
| *Cliente*              | Dupla                 | 
| *Geografia*             | Dupla                 | 


Fazer essas configurações de propriedade do modo de armazenamento resultará nos comportamentos a seguir, supondo que a tabela *Vendas* tenha um volume de dados significativos.
* As tabelas de dimensões (*Data*, *Cliente* e *Geografia*) são armazenadas em cache; portanto, os tempos de carregamento inicial do relatório devem ser rápidos ao recuperar valores de segmentação de dados a ser exibidos.
* Se a tabela *Vendas* não for armazenada em cache, ocorrem os seguintes resultados:
    * Os tempos de atualização de dados são aprimorados e o consumo de memória é reduzido
    * As consultas de relatório com base na tabela *Vendas* são executadas em modo DirectQuery, que podem levar mais tempo, mas estão mais próximas do tempo real já que nenhuma latência de cache é introduzida

* As consultas de relatório com base na tabela *SurveyResponse* são retornadas do cache na memória, e, portanto, devem ser relativamente rápidas.

## <a name="queries-that-hit-or-miss-the-cache"></a>Consultas que acertam ou erram o cache

A conexão do **SQL Profiler** à porta de diagnóstico do **Power BI Desktop** mostra quais consultas acertam ou erram o cache na memória executando um rastreamento com base nos eventos a seguir:

* Eventos de Consultas\Início da Consulta
* Processamento de Consulta\Início da Consulta Vertipaq SE
* Processamento de Consulta\Início de DirectQuery

Para todo evento *Início da Consulta*, verifique outros eventos com a mesma *ActivityID*. Por exemplo, se não houver qualquer evento *Início de DirectQuery*, mas houver um evento *Início da Consulta Vertipaq SE*, então a consulta foi atendida do cache.

As consultas que fizerem referência às tabelas do modo **Duplo** retornarão os dados do cache, se possível; caso contrário, serão revertidas para DirectQuery.

Seguindo com o exemplo anterior, a consulta a seguir se refere apenas a uma coluna da tabela *Data*, que está no modo **Duplo**. Portanto, ela deve ter uma ocorrência no cache.

![Script para diagnóstico do modo de armazenamento](media/desktop-storage-mode/storage-mode_06.png)

A consulta a seguir se refere apenas a uma coluna da tabela *Vendas*, que está no modo **DirectQuery**. Portanto, ela *não* deve ter ocorrência no cache.

![Script para diagnóstico do modo de armazenamento](media/desktop-storage-mode/storage-mode_07.png)

A consulta a seguir é interessante porque combina as duas colunas. Esta consulta não terá ocorrência no cache. Inicialmente, você pode esperar que ela recupere os valores *CalendarYear* do cache e os valores *SalesAmount* da fonte e depois combine os resultados, mas isso seria menos eficiente do que enviar a operação SUM/GROUP BY para o sistema de origem. Se a operação for propagada para a fonte, o número de linhas retornadas provavelmente será muito menor. 

![Script para diagnóstico do modo de armazenamento](media/desktop-storage-mode/storage-mode_08.png)

> [!NOTE]
> Esse comportamento é diferente das [relações muitos para muitos no Power BI Desktop (prévia)](desktop-many-to-many-relationships.md) ao combinar tabelas armazenadas e não armazenadas em cache.

## <a name="caches-should-be-kept-in-sync"></a>Os caches devem ser mantidos em sincronia

As consultas exibidas na seção anterior mostram que as tabelas **Duplas** às vezes acertam o cache e outras não. Por isso, se o cache estiver desatualizado, diferentes valores poderão ser retornados. A execução da consulta não tentará ocultar os problemas de dados, filtrando, por exemplo, os resultados de DirectQuery para coincidir com os valores armazenados em cache. É sua responsabilidade conhecer seus fluxos de dados, e você deve projetar de acordo com isso. Existem técnicas estabelecidas para lidar com tais casos na origem, se necessário.

O modo de armazenamento **Duplo** é uma otimização de desempenho. Ele só deve ser usado de maneira a não comprometer a capacidade de atender aos requisitos comerciais. Para um comportamento alternativo, considere o uso das técnicas descritas no artigo [Relações muitos para muitos no Power BI Desktop (prévia)](desktop-many-to-many-relationships.md).

## <a name="data-view"></a>Exibição de dados
Se pelo menos uma tabela no conjunto de dados tiver o **modo de armazenamento** definido como Importação ou Duplo, a guia **Exibição de dados** será exibida.

![Exibição de dados no Power BI Desktop](media/desktop-storage-mode/storage-mode_09.png)

Quando selecionadas em *Exibição de dados**, as tabelas **Dupla** e **Importação** mostram os dados armazenados em cache. As tabelas DirectQuery não mostram dados, e uma mensagem é exibida informando que as tabelas DirectQuery não podem ser mostradas.


## <a name="limitations-and-considerations"></a>Limitações e considerações

Existem algumas limitações para esta versão do **modo de armazenamento** e sua correlação com os **modelos compostos**.

As seguintes fontes (multidimensionais) do Live Connect não podem ser usadas com os **modelos compostos**:

* SAP HANA
* SAP Business Warehouse
* SQL Server Analysis Services
* Conjuntos de dados do Power BI
* Azure Analysis Services

Ao se conectar a essas fontes multidimensionais usando o DirectQuery, não é possível se conectar também a outra fonte de DirectQuery, nem combinar com dados importados.

As limitações existentes no uso do DirectQuery ainda se aplicam ao serem usados **modelos compostos**. Muitas dessas limitações agora são por tabela, dependendo do **modo de armazenamento** da tabela. Por exemplo, uma coluna calculada em uma tabela importada pode se referir a outras tabelas, mas uma coluna calculada em uma tabela do DirectQuery ainda fica restrita para se referir apenas às colunas na mesma tabela. Outras limitações se aplicam ao modelo como um todo se quaisquer das tabelas no modelo forem DirectQuery. Por exemplo, os recursos **QuickInsights** e **P e R** não estão disponíveis em um modelo se qualquer uma das tabelas nele tiver um **modo de armazenamento** do DirectQuery. 

## <a name="next-steps"></a>Próximas etapas

Os artigos a seguir tratam mais sobre os modelos compostos e também descrevem o DirectQuery em detalhes.

* [Modelos compostos no Power BI Desktop (prévia)](desktop-composite-models.md)
* [Relações muitos para muitos no Power BI Desktop (prévia)](desktop-many-to-many-relationships.md)

Artigos do DirectQuery:

* [Usar o DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery no Power BI](desktop-directquery-data-sources.md)

