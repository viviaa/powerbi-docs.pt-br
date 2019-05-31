---
title: Usar o detalhamento do relatório no Power BI Desktop
description: Aprenda a analisar em um relatório para outro no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/08/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 45a7cdd3c7b5324f3d618eaba4bdb3968a9549a5
ms.sourcegitcommit: 8bf2419b7cb4bf95fc975d07a329b78db5b19f81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66375207"
---
# <a name="use-cross-report-drillthrough-in-power-bi-desktop"></a>Usar o detalhamento do relatório no Power BI Desktop

Com o recurso de detalhamento do relatório no Power BI Desktop, você poderá saltar contextualmente de um relatório para outro relatório. Isso é verdadeiro desde que os relatórios estão dentro do mesmo espaço de trabalho ou aplicativo no serviço do Microsoft Power BI. Use o detalhamento do relatório entre para conectar-se dois ou mais relatórios que têm conteúdo relacionado e passar o contexto de filtro, juntamente com a conexão cruzada relatório. Neste artigo, você aprenderá como configurar um detalhamento do relatório entre relatórios do Power BI e qual experiência que os usuários quando eles usam o detalhamento do relatório entre por conta própria.

![Opção de detalhamento de captura de tela do Power BI Desktop](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

As definições a seguir são importantes para entender, antes de começarmos como configurar e usar entre-relatório de detalhamento:

* **Origem do visual:** O visual que invoca a ação de detalhamento usando o menu de contexto visual.
* **Relatório de origem:** O relatório que contém o visual de origem cruzada-relatório de detalhamento.
* **Página de destino:** A página que um usuário chegar à após iniciar uma ação de detalhamento.
* **Relatório de destino:** O relatório que contém a página de destino de detalhamento do relatório cruzada.

## <a name="enable-cross-report-drillthrough"></a>Habilitar o detalhamento do relatório cruzada

Para habilitar um relatório para ser o destino de um detalhamento entre relatórios, você deve habilitar o recurso para esse relatório na **opções** janela. Vá para **arquivo** > **opções e configurações** > **opções**e, em seguida, vá para **configurações de relatório** próximo a parte inferior da página à esquerda.

Selecione o **permitir que elementos visuais neste relatório para usar destinos de detalhamento de outros relatórios** caixa de seleção, conforme mostrado na imagem a seguir.

![Janela de captura de tela de opções, com as configurações do relatório realçado](media/desktop-cross-report-drill-through/cross-report-drill-through-02.png)

Detalhamento do relatório entre agora está habilitado.

## <a name="set-up-cross-report-drillthrough"></a>Configurar o detalhamento do relatório cruzada

Configurar o detalhamento do relatório entre é semelhante à configuração de detalhamento em um relatório. Detalhamento está habilitado na página de destino, permitindo que outros elementos visuais para a página habilitada para extração de detalhes de destino. Para obter as etapas criar o detalhamento em um único relatório, consulte [usar o detalhamento no Power BI Desktop](desktop-drillthrough.md).

Para iniciar o processo de instalação, você precisa executar algumas etapas iniciais:

* Configure uma página de destino do detalhamento, em seguida, pode ser acessada de outros relatórios no espaço de trabalho ou aplicativo.
* Permitir que um relatório para ver as páginas de detalhamento de fora do seu próprio relatório.

Encontre opções de detalhamento na **campos** seção o **visualizações** painel, conforme mostrado na imagem a seguir.

![Painel de captura de tela de visualizações, com opções de detalhamento realçado](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Habilitando o detalhamento para uma página a primeira etapa é validar os modelos de dados para os relatórios de origem e destino. Certifique-se de que: 

* Campos que você deseja passar existem em ambos os modelos de dados.
* Os nomes dos campos e os nomes das tabelas às quais eles pertencem, são idênticos (também deve coincidir com as cadeias de caracteres e diferenciam maiusculas de minúsculas).

Por exemplo, se você quiser passar um filtro no campo *país* dentro de tabela *geografia*, ambos os modelos devem ter um *Geography* tabela e um *país* campo dentro dessa tabela. Caso contrário, você deve atualizar o nome do campo ou o nome da tabela no modelo subjacente. Simplesmente atualizar o nome de exibição dos campos não funcionará corretamente para cross-relatório detalhamento. (Observe que os esquemas em cada relatório não precisam ser exatamente o mesmo.)

Para começar a instalação, você precisa preparar a página de destino. No Power BI Desktop, vá para a página e verifique se o **Cross-report** detalhamento alternância está definida como **em**. 

![Captura de tela da alternância entre relatório definida como ativado](media/desktop-cross-report-drill-through/cross-report-drill-through-03.png)

Em seguida, arraste os campos que você deseja usar como o destino de detalhamento para a tela. Selecione se você deseja que o campo a ser usado como uma categoria ou resumidos como uma medida. Neste ponto, você pode selecionar se deseja desabilitar o **manter todos os filtros** alternância para o visual. Se você não quiser passar outros filtros aplicados da fonte de visual para seu destino de detalhamento visual, selecione **desativar**.

> [!NOTE]
> Se você estiver usando a página de detalhamento do relatório entre somente, você deve excluir o **volta** botão que é adicionado automaticamente. O **volta** botão funciona somente para nagivation em um único relatório. 

Depois de configurar o visual, certifique-se de salvar o relatório, se você estiver no serviço do Power BI, ou salvar e publicar o relatório, se você estiver usando o Power BI Desktop.

A seção anterior descreveu como habilitar o detalhamento do relatório cruzada para o Power BI Desktop (na **opções** janela). Se você estiver usando o serviço do Power BI para criar um destino de detalhamento do relatório cruzada, para habilitar o detalhamento do relatório entre faça o seguinte: 

1. Selecione o espaço de trabalho no qual o relatório de destino e o relatório de origem residem.
2. Selecione **relatórios**.
3. Selecione o **configurações** ícone para o relatório de origem.
4. Verifique se a alternância entre-relatório de detalhamento está **em**.
5. Salve seu relatório.

Isso é tudo. Seu relatório estiver pronto para a experiência de cross-relatório de detalhamento. 

Na próxima seção, vamos dar uma olhada a experiência da perspectiva do usuário.

## <a name="cross-report-drillthrough-experience"></a>Experiência de cross-relatório de detalhamento

Quando você configura a experiência de cross-relatório de detalhamento para um relatório, você pode colocar o recurso a ser usado.

Selecione o relatório de origem no serviço do Power BI e, em seguida, selecione um visual que usa o campo ou campos da maneira que você especificou ao configurar a página de destino. Em seguida, clique com botão direito para abrir o menu de contexto visual e selecionar um ponto de dados **detalhamento**.

![Captura de tela do relatório de origem no serviço do Power BI, com detalhamento realçado](media/desktop-cross-report-drill-through/cross-report-drill-through-01.png)

Você verá os resultados na página de detalhamento do relatório cruzada de destino, assim como você configurá-los quando você criou o destino. Os resultados são filtrados de acordo com as configurações de detalhamento.

> [!IMPORTANT]
> Power BI armazena em cache os destinos de detalhamento do relatório cruzada. Se você fizer alterações, certifique-se de que você atualize seu navegador, se você não vir os destinos de detalhamento conforme o esperado. 

Relatório entre destinos são formatados da seguinte forma: 

`Target Page Name [Target Report Name]`

Depois de selecionar a página de destino ao qual você deseja drill-through, o Power BI vai para a página. Ele passa o contexto de filtro com base nas configurações da página de destino. 

Contexto de filtro da origem do visual pode incluir o seguinte: 

* Relatório, página e filtros de nível visual, que afetam o visual de origem. 
* Filtro cruzado e realce cruzado que afetam o visual de origem. 
* Segmentações de dados na página e sincronizar segmentações de dados.
* Parâmetros de URL.

Quando chegar no relatório de destino para detalhamento, o Power BI só se aplica filtros dos campos para o qual ele localiza corresponde à cadeia de caracteres para nome do campo e o nome da tabela. Power BI não se aplica a adesivas filtros do relatório de destino. No entanto, ele, aplicar seu indicador pessoal do padrão se existir um. Por exemplo, se seu indicador de pessoais padrão inclui um filtro de nível de relatório para *país = EUA*, Power BI aplica-se que o filtro primeiro, antes de aplicar o contexto de filtro da origem do visual. 

Para cross-relatório detalhamento, o Power BI passa o contexto de filtro para todas as páginas padrão no relatório de destino. Power BI não passa o contexto de filtro para páginas de dica de ferramenta, porque as páginas de dica de ferramenta são filtradas com base na fonte de visual que invoca a dica de ferramenta.

Se você quiser retornar ao relatório de origem após a ação de detalhamento do relatório entre, use o navegador **volta** botão. 

## <a name="next-steps"></a>Próximas etapas

Você também pode estar interessado nos seguintes artigos:

* [Usando segmentações no Power BI Desktop](visuals/power-bi-visualization-slicers.md)
* [Usar o detalhamento no Power BI Desktop](desktop-drillthrough.md)

