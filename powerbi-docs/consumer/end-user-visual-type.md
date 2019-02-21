---
title: Tipos de visualização no Power BI para consumidores
description: Tipos de visualização no serviço do Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 02/12/2019
ms.author: mihart
LocalizationGroup: Consumer
ms.openlocfilehash: 0118c9b7bb1d00daf1b6baeb7638916b49d8af49
ms.sourcegitcommit: 654fae0af739bd599e029d692f142faeba0a502f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56426759"
---
# <a name="visualization-types-in-power-bi"></a>Tipos de visualização no Power BI
Você encontrará visualizações em relatórios, dashboards, aplicativos e P e R. Alguns desses tipos de visualização são empacotados com o Power BI e alguns são *visuais personalizados*. Visuais personalizados são criados fora do Power BI e de uma maneira que permite a *designers de relatório* adicioná-los a aplicativos, dashboards e relatórios do Power BI. 

Este artigo é uma visão geral de visualizações que são empacotadas com o Power BI.  Estas são as visualizações que você encontrará com mais frequência. 

> [!NOTE]
> Para saber mais sobre visuais personalizados, pesquise-os na seção **Visuais do Power BI** do [Microsoft AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals). Para cada visual, você encontrará uma descrição, informações do criador e capturas de tela ou um vídeo. 

## <a name="list-of-visualizations-available-in-power-bi"></a>Lista das visualizações disponíveis no Power BI
Todas essas visualizações podem ser encontradas nos relatórios, dashboards e aplicativos do Power BI, bem como [especificadas em P e R](#qna). Para saber como interagir com visualizações, veja [Interagir com visualizações em relatórios, dashboards e aplicativos](end-user-visualizations.md)

### <a name="area-charts-basic-layered-and-stacked"></a>Gráficos de área: básico (em camadas) e empilhado
![gráfico da área](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/basicareamapsmall.png)

O gráfico de área básico baseia-se no gráfico de linhas com a área entre o eixo e a linha preenchida. Os gráficos de área enfatizam a magnitude da alteração ao longo do tempo e pode ser usado para chamar a atenção para o valor total entre uma tendência. Por exemplo, os dados que representam o lucro ao longo do tempo podem ser plotados em um gráfico de área para enfatizar o lucro total.

### <a name="bar-and-column-charts"></a>Gráficos de barras e colunas
![gráfico de colunas](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/pbi_nancy_viz_bar.png)

 ![gráfico de barras](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/pbi_nancy_viz_col.png)

Gráficos de barras são o padrão para observar um valor específico entre categorias diferentes.

### <a name="cards-single-number"></a>Cartões: número único
![cartão de número único](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/pbi_nancy_viz_card.png)

Cartões de número único exibem um único fato, um único ponto de dados. Às vezes, um único número é a coisa mais importante que você deseja acompanhar no seu painel ou relatório do Power BI, como as vendas totais, a fatia de mercado ano após ano ou o total de oportunidades.  

### <a name="cards-multi-row"></a>Cartões: linha múltipla
![cartão com várias linhas](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/multi-row-card.png)

Cartões de múltiplas linhas exibem um ou mais pontos de dados, um por linha.


### <a name="combo-charts"></a>Gráficos de combinação
![gráfico de combinação](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/combosmall.png)

Um gráfico de combinação combina um gráfico de colunas e um gráfico de linhas. Combinar os dois gráficos em um permite você faça uma comparação rápida dos dados. Gráficos de combinação podem ter um ou dois eixos Y, portanto, não deixe de examiná-los cuidadosamente. 

Os gráficos de combinação são uma ótima opção:
- Quando você tem um gráfico de linhas e um gráfico de colunas com o mesmo eixo X.
- para comparar várias medidas com intervalos de valores diferentes
- para ilustrar a correlação entre duas medidas em uma visualização
- para verificar se uma medida atende o destino definido pela outra medida
- para conservar o espaço de tela

### <a name="doughnut-charts"></a>Gráficos de rosca
![gráfico de rosca](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/donutsmall.png)

Gráficos de rosca são semelhantes aos gráficos de pizza.  Eles mostram a relação das partes com um todo. A única diferença é que o centro está em branco e permite o espaço para um rótulo ou ícone.

### <a name="funnel-charts"></a>Gráficos de funil
![gráfico de funil](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/pbi_nancy_viz_funnel.png)

Funis ajudam a visualizar um processo contendo estágios, enquanto os itens seguem uma sequência de um estágio para o próximo.  Um exemplo é um processo de vendas que começa com clientes potenciais e termina com a realização efetiva da compra.

Por exemplo, um funil de vendas que acompanha clientes pelos estágios: Oportunidade > Oportunidade qualificada > Cliente potencial > Contrato > Fechamento. Em um relance, a forma do funil transmite a integridade do processo que você está controlando.
Cada estágio de funil representa um percentual do total. Portanto, na maioria dos casos, um gráfico de funil tem a forma de um funil – com o primeiro estágio sendo o maior, e cada estágio subsequente, menor do que seu antecessor. Um funil em forma de pera também é útil - ele pode identificar um problema no processo. Mas, em geral, o primeiro estágio, o estágio de "entrada", é o maior.

Os gráficos de funil são uma ótima opção:
- Quando os dados são sequenciais e se movimentam em pelo menos 4 estágios.
- Quando o número de "itens" no primeiro for maior que o número no estágio final.
- calcular o potencial (receita de vendas/negociações/etc.) por estágios.
- calcular e controlar as taxas de conversão e retenção.
- revelar afunilamentos em um processo linear.
- controlar o fluxo de trabalho do carrinho de compras.
- rastrear o progresso e o sucesso das campanhas de propaganda/marketing.

### <a name="gauge-charts"></a>Gráficos de medidor
![gráfico de medidor](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/gauge_m.png)

Um gráfico de medidor radial tem um arco circular e exibe um único valor que acompanha o progresso em relação a um objetivo/KPI. A meta, ou o valor de destino, é representada pela linha (agulha). Progresso em relação a esse objetivo é representado pelo sombreamento. E o valor que representa o progresso é mostrado em negrito dentro do arco. Todos os valores possíveis são distribuídos uniformemente ao longo do arco, do mínimo (valor mais à esquerda) para o máximo (valor mais à direita).

No exemplo acima, somos um revendedor de carros, controlando a média de vendas da nossa equipe por mês. Nosso objetivo é 140 e é representado pela agulha preta. A média mínima possível de vendas é 0 e definimos o máximo como 200. O sombreamento azul mostra que temos atualmente uma média de aproximadamente 120 vendas neste mês. Felizmente, ainda temos outra semana para atingir a nossa meta.

Os medidores radiais são uma ótima opção para:
- mostrar o progresso para atingir uma meta
- representar uma medida percentual, como um KPI
- mostrar a integridade de uma única medida
- exibir informações que podem ser examinadas e compreendidas rapidamente

 ### <a name="key-influencers-chart"></a>Gráficos de influenciadores principais
![Influenciador principal](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/power-bi-influencer.png)

Um gráfico de influenciador principal exibe os principais colaboradores para um resultado ou valor selecionado.

Os influenciadores principais são uma ótima opção para ajudar você a entender os fatores que influenciam uma métrica principal. Por exemplo, *o que influencia os clientes a fazer um segundo pedido *ou* por que as vendas foram tão altas em junho passado*. 

### <a name="kpis"></a>KPIs
![kpi](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/power-bi-kpi.png)

Um KPI (Indicador Chave de Desempenho) é uma indicação visual que comunica a quantidade de progresso feito em relação a uma meta mensurável. 

Os KPIs são uma ótima opção:
- para medir o progresso (no que estou adiantado ou atrasado?)
- para medir a distância para uma meta (o quão adiantado ou atrasado eu estou?)

### <a name="line-charts"></a>Gráficos de linhas
![gráfico de linhas](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/pbi_nancy_viz_line.png)

Gráfico de linhas enfatizam o formato geral de uma série inteira de valores, geralmente ao longo do tempo.

### <a name="maps-basic-maps"></a>Mapas: mapas básicos
![mapa básico](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/pbi-nancy_viz_map.png)

Use um mapa básico para associar informações categóricas e quantitativas a locais espaciais.

### <a name="maps-arcgis-maps"></a>Mapas: Mapas ArcGIS
![Mapa ArcGis](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/power-bi-esri-map-theme2.png)

A combinação de mapas do ArcGIS e do Power BI leva o mapeamento para além da apresentação de pontos em um mapa, para um nível totalmente novo. As opções disponíveis para mapas base, tipos de localização, temas, estilos de símbolo e camadas de referência criam visualizações de mapa informativas e impressionantes. A combinação de camadas de dados autoritativas (como dados de censo) em um mapa com análise espacial transmite uma compreensão mais profunda dos dados na visualização.

### <a name="maps-filled-maps-choropleth"></a>Mapas: mapas preenchidos (Coropléticos)
![mapa coroplético](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/pbi_nancy_viz_filledmap.png)

Um mapa coroplético usa sombreamento ou tonalidade ou padrões para exibir como um valor difere na proporção em uma localização geográfica ou região. Exiba rapidamente essas diferenças relativas com sombreamento que varia de claro (menos frequente/inferior) para escuro (mais frequente/mais).

### <a name="maps-shape-maps"></a>Mapas: mapas de formas
![mapa de formas](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/power-bi-shape-map2.png)

Mapas de formas comparam regiões em um mapa usando cores. Ao contrário do visual Mapa, os mapas de formas não conseguem mostrar localizações geográficas precisas de pontos de dados em um mapa. Em vez disso, sua finalidade principal é mostrar comparações relativas de regiões em um mapa colorindo-as de modo diferente.

### <a name="matrix"></a>Matriz
![matriz](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/matrix.png)

O visual de matriz é um tipo de visual de tabela (consulte "Tabela" abaixo) que dá suporte a um layout de nível. Muitas vezes, os designers de relatório incluem matrizes em relatórios e dashboards para permitir que os usuários selecionem um ou mais elementos (linhas, colunas e células) na matriz a fim de aplicar realce cruzado a outros visuais em uma página do relatório.  

### <a name="pie-charts"></a>Gráficos de pizza
![gráfico de pizza](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/pbi_nancy_viz_pie.png)

Gráficos de pizza mostram a relação das partes com um todo. 

### <a name="ribbon-chart"></a>Gráfico da faixa de opções
![gráfico de faixa de opções](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/power-bi-ribbon.png)

Gráficos de faixa de opções cuja categoria de dados tem a classificação mais alta (maior valor). Gráficos de faixa de opções são eficazes para mostrar alterações na classificação, com o maior intervalo (valor) sempre exibido na parte superior de cada período.

### <a name="scatter-bubble-and-dot-plot-charts"></a>Gráficos de dispersão, de bolhas e de pontos


Um gráfico de dispersão sempre tem dois eixos de valor para mostrar um conjunto de dados numéricos em um eixo horizontal e outro conjunto de valores numéricos em um eixo vertical. O gráfico exibe pontos na interseção de um valor numérico de x e y, combinando esses valores em pontos de dados individuais. Esses pontos de dados podem ser distribuídos de maneira uniforme ou não pelo eixo horizontal, dependendo dos dados.

![gráfico de bolhas](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/pbi_nancy_viz_bubble.png)

Um gráfico de bolhas substitui os pontos de dados por bolhas, com o tamanho de bolha representando uma dimensão adicional dos dados.

Um gráfico de pontos é semelhante a um gráfico de bolhas e um gráfico de dispersão, mas pode plotar dados numéricos ou categóricos ao longo do eixo X.

### <a name="scatter-high-density"></a>Dispersão de alta densidade
![dispersão de alta densidade](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/density-scatter.png)

Por definição, os dados de alta densidade são amostrados para criar com uma rapidez razoável visualizações que atendam à interatividade. A amostragem de alta densidade usa um algoritmo que elimina os pontos sobrepostos e garante que todos os pontos no conjunto de dados sejam representados no visual. Ele não apenas plota uma amostra representativa dos dados.  

Isso assegura a melhor combinação de capacidade de resposta, representação e preservação clara de pontos importantes no conjunto de dados geral.

### <a name="slicers"></a>Segmentações
![segmentação de dados](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/pbi_slicer.png)

Uma segmentação de dados é um gráfico autônomo que pode ser usado para filtrar os outros visuais na página. As segmentações de dados são fornecidas em vários formatos diferentes (categoria, intervalo, data etc.) e podem ser formatadas para permitir a seleção de apenas um, muitos ou todos os valores disponíveis. 

As segmentações de dados são uma ótima opção para:
- exibir os filtros mais usados ou importantes na tela do relatório para facilitar o acesso;
- facilitar a exibição do estado atual filtrado sem precisar abrir uma lista suspensa;
- filtrar por colunas que são desnecessárias e que ficam ocultas nas tabelas de dados;
- criar relatórios mais específicos, colocando as segmentações ao lado de visuais importantes.

### <a name="standalone-images"></a>Imagens autônomas
![imagem autônoma](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/pbi_nancy_viz_image.png)

Uma imagem autônoma é um gráfico que foi adicionado a um relatório ou um dashboard. 


### <a name="tables"></a>Tabelas
![gráfico de tabela](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/tabletype.png)

Uma tabela é uma grade que contém dados relacionados em uma série de lógica de linhas e colunas. Ela também pode conter cabeçalhos e linhas de totais. As tabelas funcionam bem com comparações quantitativas em que você observa muitos valores de uma única categoria. Por exemplo, esta tabela exibe cinco medidas diferentes para a Categoria.

As tabelas são uma ótima opção:
- para ver e comparar dados detalhados e valores exatos (em vez de representações visuais)
- para exibir dados em um formato tabular
- para exibir dados numéricos por categorias

### <a name="treemaps"></a>Treemaps
![gráfico de mapa de árvore](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/pbi_nancy_viz_tree.png)

Gráficos de mapa de árvore são gráficos de retângulos coloridos, com um tamanho que representa o valor.  Eles podem ser hierárquicos, com retângulos aninhados nos retângulos principais. O espaço dentro de cada retângulo é alocado com base no valor que está sendo medido. E os retângulos são organizados no tamanho da parte superior esquerda (maior) à parte inferior direita (menor).

Os treemps são uma ótima opção:
- para exibir grandes quantidades de dados hierárquicos;
- quando um gráfico de barras não puder lidar efetivamente com grande número de valores;
- para mostrar as proporções entre cada parte e o todo;
- para mostrar o padrão da distribuição da medida em cada nível das categorias na hierarquia;
- para mostrar atributos usando a codificação de cor e tamanho;
- para identificar padrões, exceções, colaboradores mais importantes e exceções.

### <a name="waterfall-charts"></a>Gráfico de cascata
![gráfico de cascata](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/waterfallsmall.png)

O gráfico de cascata mostram uma duração total conforme os valores são adicionados ou subtraídos. É útil para entender como um valor inicial (por exemplo, a receita líquida) é afetado por uma série de alterações positivas e negativas.

As colunas são codificadas para que você possa rapidamente aumentar e diminuir. As colunas dos valores inicial e final às vezes começam no eixo horizontal, enquanto os valores intermediários são colunas flutuantes. Devido a essa "aparência", os gráficos de cascata também são chamados de gráficos de ponte.

Os gráficos de cascata são uma ótima opção:
- quando houver alterações de medida em uma série de tempo ou categorias diferentes
- para auditar as principais alterações que contribuem para o valor total
- para traçar o lucro anual da empresa, mostrando várias fontes de receita e chegar ao lucro total (ou perda).
- para ilustrar o início e final do número de funcionários de sua empresa em um ano
- para visualizar a quantidade de dinheiro, faça e gaste todo mês e o saldo parcial para sua conta.

## <a name="tell-qa-which-visualization-to-use"></a>Informe à P e R qual visualização deve ser usada
Ao digitar consultas em linguagem natural com a P e R do Power BI, você pode especificar o tipo de visualização em sua consulta.  Por exemplo:

“***vendas por estado como um treemap***”

![sessão de P e R](../visuals/media/power-bi-visualization-types-for-reports-and-q-and-a/qatreemap.png)

## <a name="next-steps"></a>Próximas etapas
[Interagir com as visualizações em relatórios, dashboards e aplicativos](end-user-visualizations.md)    
[A referência visual correta de sqlbi.com](http://www.sqlbi.com/wp-content/uploads/videotrainings/dashboarddesign/visuals-reference-may2017-A3.pdf)