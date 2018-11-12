---
title: Adicionar um filtro a um visual, página, detalhamento ou relatório no Power BI
description: Adicionar um filtro de página, um filtro de visualização, um filtro de relatório ou um filtro de detalhamento a um relatório no Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 09/28/2018
ms.author: maggies
LocalizationGroup: Reports
ms.openlocfilehash: c70e29bf7dcd5a307cbcb4762595716595dfa523
ms.sourcegitcommit: d20f74d5300197a0930eeb7db586c6a90403aabc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2018
ms.locfileid: "50973271"
---
# <a name="add-a-filter-to-a-power-bi-service-report-in-editing-view"></a>Adicionar um filtro a um relatório do serviço do Power BI (na exibição Edição)

Este artigo explica como adicionar um filtro de página, um filtro de visualização, um filtro de relatório ou um filtro de detalhamento a um relatório no Power BI. Os exemplos neste artigo estão no serviço do Power BI. As etapas são quase idênticas no Power BI Desktop.

## <a name="filters-in-editing-view-or-reading-view"></a>Filtros no modo de exibição de Edição ou no modo de exibição de Leitura
Você pode interagir com relatórios em dois modos de exibição diferentes: Leitura e Edição. Os recursos de filtragem disponíveis dependem de qual modo você está. Leia tudo [sobre filtros e realce em relatórios do Power BI](power-bi-reports-filters-and-highlighting.md) para obter detalhes.

Este artigo descreve como criar filtros no **modo de exibição de Edição** de relatório.  Para saber mais sobre filtros no modo de exibição de Leitura, confira [Interagir com filtros no modo de exibição de Leitura de relatórios](consumer/end-user-reading-view.md).

## <a name="filter-types-in-the-filters-pane"></a>Tipos de filtro no painel Filtros
Independentemente de você estar usando o Power BI Desktop ou o serviço do Power BI, o painel Filtros é exibido no lado direito da tela do relatório. Caso não veja o painel Filtros, selecione o ícone ">" no canto superior direito para expandi-lo.

Há quatro tipos de filtros: **filtro de página**, **filtro de visual**, **filtro de detalhamento** e **filtro de relatório**.

![Painel Filtros no Modo de exibição de leitura](media/power-bi-report-add-filter/power-bi-add-filter-reading-view.png)

Como os filtros *persistem*, quando você sai do relatório, o Power BI mantém o filtro, a segmentação e outras alteração de exibição de dados que você realizou. Portanto, você pode continuar onde parou quando retornar ao relatório. Se não quiser que as alterações do filtro persistam, selecione **Redefinir para padrão** na barra de menus superior.

![botão de filtro persistente](media/power-bi-report-add-filter/power-bi-reset-to-default.png)

## <a name="add-a-filter-to-a-visual"></a>Adicionar um filtro a um visual
Você pode adicionar um filtro a um visual específico de duas maneiras diferentes (também conhecido como um "filtro de visual"). 

* Filtre um campo que já está sendo usado pela visualização.
* Identifique um campo que ainda não esteja sendo usado pela visualização e adicione esse campo diretamente ao bucket **Filtros no nível do visual**.

A propósito, esse procedimento usa o exemplo de Análise de Varejo, caso você queira baixá-lo para acompanhar. Faça o download do [Exemplo de Análise de Varejo](sample-retail-analysis.md).

### <a name="filter-the-fields-in-the-visual"></a>Filtrar os campos no visual


1. Abra seu [relatório no modo de exibição de Edição](service-the-report-editor-take-a-tour.md).
   
   ![](media/power-bi-report-add-filter/power-bi-edit-view.png)
2. Abra o painel de visualizações e filtros e o painel Campos (se ainda não estiverem abertos).
   
   ![](media/power-bi-report-add-filter/power-bi-display-panes.png)
3. Selecione um visual para ativá-lo. Todos os campos que estiverem sendo usados pelo visual serão identificados no painel **Campos** e também listados no painel **Filtros**, sob o cabeçalho **Filtros no nível do visual**.
   
   ![](media/power-bi-report-add-filter/power-bi-default-visual-filter.png)
4. Agora vamos adicionar um filtro a um campo que já está sendo usado pela visualização. 
   
    Role para baixo até a área de **Filtros de nível visual** e selecione a seta para expandir o campo que você deseja filtrar. Neste exemplo, vamos filtrar **StoreNumberName**.
     
    ![](media/power-bi-report-add-filter/power-bi-visual-level-filter.png) 
    
    Defina os controles de filtro **Básico**, **Avançado** ou **N superior**. Neste exemplo, pesquisaremos na filtragem Básica por **cha** e selecionaremos esses cinco armazenamentos.
     
    ![](media/power-bi-report-add-filter/power-bi-search-filter.png) 
   
    O visual é alterado para refletir o novo filtro. Se você salvar o relatório com o filtro, os leitores do relatório verão o visual filtrado a princípio, e poderão interagir com o filtro no modo de exibição de Leitura, marcando ou desmarcando valores.
     
    ![](media/power-bi-report-add-filter/power-bi-search-visual-filter-results.png)

### <a name="filter-with-a-field-thats-not-in-the-visual"></a>Filtrar com um campo que não está no visual

Agora, vamos adicionar um campo novo à nossa visualização como um filtro no nível do visual.
   
1. No painel Campos, selecione o campo que você deseja adicionar como um novo filtro no nível do visual e arraste-o até a **área de Filtros no nível do visual**.  Neste exemplo, arrastaremos **Gerente Regional** para o bucket **Filtros no nível do visual**, pesquisaremos por **an** e selecionaremos os três gerentes. 
     
    ![](media/power-bi-report-add-filter/power-bi-search-add-visual-filter.png)

    Observe que o **Gerente Regional** *não* é adicionado à visualização em si. A visualização ainda é composta por **StoreNumberName** como o eixo e **Vendas Deste Ano** como o valor.  
     
    ![](media/power-bi-report-add-filter/power-bi-visualization.png)

    E a própria visualização agora é filtrada para mostrar apenas as vendas desses gerentes neste ano para as lojas especificadas.
     
    ![](media/power-bi-report-add-filter/power-bi-search-visual-filter-results-2.png)

    Se você salvar o relatório com o filtro, os leitores do relatório poderão interagir com o filtro **Gerente regional** no modo de exibição de Leitura, marcando ou desmarcando valores.

## <a name="add-a-filter-to-an-entire-page"></a>Adicionar um filtro a uma página inteira

Também é possível adicionar um filtro a uma página inteira (também conhecido como filtro no modo de exibição de página)
1. Abra seu [relatório no modo de exibição de Edição](service-the-report-editor-take-a-tour.md).
2. Abra o painel de visualizações e filtros e o painel Campos (se ainda não estiverem abertos).
3. No painel Campos, selecione o campo que você deseja adicionar como um novo filtro de nível de página e arraste-o para a área **Filtros no nível da página**.  
4. Selecione os valores que você deseja filtrar e defina os controles de filtragem **Básico** ou **Avançado**.
   
   Todas as visualizações na página, afetadas por esse filtro, serão redesenhadas para refletir a alteração. 
   
   ![](media/power-bi-report-add-filter/filterpage.gif)

    Se você salvar o relatório com o filtro, os leitores do relatório poderão interagir com o filtro no modo de exibição de Leitura, marcando ou desmarcando valores.

## <a name="add-a-drillthrough-filter"></a>Adicionar um filtro de detalhamento
Com o detalhamento no serviço do Power BI Desktop e do Power BI Desktop, você pode criar uma página de relatório de *destino* que tem como foco uma entidade específica, como um fornecedor, cliente ou fabricante. Agora, de outras páginas de relatório, os usuários podem clicar com o botão direito do mouse em um ponto de dados da entidade em questão e executar uma consulta drill-through na página focalizada.

### <a name="create-a-drillthrough-filter"></a>Criar um filtro de detalhamento
Para acompanhar, abra o exemplo Rentabilidade do Cliente no Modo de Edição de Exibição. Vamos supor que você deseja uma página concentrada em áreas de negócios executivos.   

1. Adicione uma nova página ao relatório e chame-a de **Equipe Executiva**. Essa será a página de *destino* do detalhamento.
2. Adicione visualizações que acompanham as principais métricas das áreas de negócios executivos da equipe.    
3. Adicione também **Executivo > Nome do Executivo** aos filtros de detalhamento.    
   
    ![](media/power-bi-report-add-filter/power-bi-drillthrough-filter.png)
   
    Observe que o Power BI adiciona uma seta para voltar à página do relatório.  Selecionar essa seta faz com que os usuários retornem à página do relatório de *origem*: a página que eles estavam quando aceitaram o detalhamento. A seta para voltar só funciona no Modo de Exibição de Leitura.
   
     ![](media/power-bi-report-add-filter/power-bi-back-arrow.png)

### <a name="use-the-drillthrough-filter"></a>Usar o filtro de detalhamento
Vejamos como funciona o filtro de detalhamento.

1. Inicie a página do relatório **Scorecard da Equipe**.    
2. Vamos supor que você é Andrew Ma e deseja ver a página do relatório Equipe Executiva filtrada somente com os seus dados.  No gráfico da área superior esquerda, clique com o botão direito do mouse em qualquer ponto de dados verde para abrir a opção de menu Detalhamento.
   
    ![](media/power-bi-report-add-filter/power-bi-drillthrough.png)
3. Selecione **Detalhamento > Equipe Executiva** executar uma consulta drill-through na página de relatório chamada **Equipe Executiva**. A página é filtrada para mostrar informações do ponto de dados no qual você clicou com o botão direito do mouse, nesse caso, Andrew Ma. Apenas o campo que está nos filtros de Detalhamento é passados para a página de relatório de detalhamento.  
   
    ![](media/power-bi-report-add-filter/power-bi-drillthrough-executive.png)

## <a name="add-a-filter-to-an-entire-report-aka-report-filter"></a>Adicione um filtro a um relatório inteiro (também conhecido como filtro de relatório)
1. Abra seu [relatório no modo de exibição de Edição](service-the-report-editor-take-a-tour.md).
2. Abra o painel de visualizações e filtros e o painel Campos (se ainda não estiverem abertos).
3. No painel Campos, selecione o campo que você deseja adicionar como um novo filtro no nível do relatório e arraste-o para a área **Filtros no nível do relatório**.  
4. Selecione os valores que você deseja filtrar.

    Os visuais na página ativa e em todas as páginas do relatório são alterados para refletir o novo filtro. Se você salvar o relatório com o filtro, os leitores do relatório poderão interagir com o filtro no modo de exibição de Leitura, marcando ou desmarcando valores.

1. Selecione a seta para voltar para retornar à página do relatório anterior.

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas

- Há situações nas quais o filtro no nível do visual e o filtro no nível da página podem retornar resultados diferentes.  Por exemplo, quando você adiciona um filtro no nível do visual, o Power BI filtra nos resultados agregados.  A agregação padrão é Soma, mas você pode [alterar o tipo de agregação](service-aggregates.md).  

    Depois, ao adicionar um filtro no nível da página, o Power BI filtra sem agregação.  Ele faz isso, pois uma página pode ter vários visuais, que, individualmente, podem utilizar diferentes tipos de agregação.  Portanto, o filtro é aplicado em cada linha de dados.

- Se você não vir o painel Campos, verifique se você está no [Modo de Exibição de Edição](service-interact-with-a-report-in-editing-view.md) do relatório    
- Se você tiver feito muitas alterações nos filtros e quiser retornar para as configurações padrão do autor do relatório, selecione **Redefinir para padrão** na barra de menus superior.

## <a name="next-steps"></a>Próximas etapas
[Faça um tour pelo painel Filtros do relatório](consumer/end-user-report-filter.md)

[Filtros e realce em relatórios](power-bi-reports-filters-and-highlighting.md)

[Interação com os filtros e realce no modo de exibição de Leitura de relatório](consumer/end-user-reading-view.md)

[Alterar como elementos visuais de relatórios executam filtro cruzado e realce cruzado entre si](consumer/end-user-interactions.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

