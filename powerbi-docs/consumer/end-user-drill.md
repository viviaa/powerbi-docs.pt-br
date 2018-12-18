---
title: Fazer drill down e drill up em uma visualização
description: Este documento mostra como fazer drill down em uma visualização no serviço do Microsoft Power BI e no Power BI Desktop.
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: MNAaHw4PxzE
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: b24a58556c35a3213f3360b70d604a0e9b51b074
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53280940"
---
# <a name="drill-mode-in-a-visualization-in-power-bi"></a>Modo de análise em uma visualização do Power BI

## <a name="drill-requires-a-hierarchy"></a>Uma análise exige uma hierarquia
Quando um visual tem uma hierarquia, você pode fazer drill down para revelar detalhes adicionais. Por exemplo, você pode ter uma visualização que examina a contagem de medalhas Olímpicas por uma hierarquia composta de esportes, disciplina e eventos. Por padrão, a visualização mostraria a contagem de medalhas por esporte – ginástica, esqui, esportes aquáticos e assim por diante. Mas como ela tem uma hierarquia, selecionar um dos elementos visuais (como uma barra, linha ou bolhas), exibiria um quadro cada vez mais detalhado. Selecione o elemento **esportes aquáticos** para ver os dados por natação, mergulho e polo aquático.  Selecione o elemento **mergulho** para ver detalhes de trampolim, plataforma e eventos de mergulho sincronizado.

É possível adicionar hierarquias aos seus relatórios, mas não aos relatórios compartilhados com você.
Não sabe quais visualizações do Power BI contém uma hierarquia?  Passe o mouse sobre uma visualização e se você ver esses controles de análise nos cantos superiores, a visualização tem uma hierarquia.

![fazer drill down de um nível](./media/end-user-drill/power-bi-drill-icon4.png)![ativar e desativar drill down](./media/end-user-drill/power-bi-drill-icon2.png)![ícone fazer drill down de todos os campos de uma só vez](./media/end-user-drill/power-bi-drill-icon3.png)
![ícone fazer drill up](./media/end-user-drill/power-bi-drill-icon5.png) ![ícone expandir abaixo](./media/end-user-drill/power-bi-drill-icon6.png)  

As datas são um tipo exclusivo de hierarquia. Quando você adiciona um campo de data a uma visualização, o Power BI adiciona automaticamente uma hierarquia de tempo que contém ano, trimestre, mês e dia. Para saber mais, consulte [Hierarquias de visuais e comportamento de drill down](../guided-learning/visualizations.yml?tutorial-step=18) ou assista ao vídeo abaixo.


  <iframe width="560" height="315" src="https://www.youtube.com/embed/MNAaHw4PxzE?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

> [!NOTE]
> Para saber como criar hierarquias usando o Power BI Desktop, assista ao vídeo [Como criar e adicionar hierarquias](https://youtu.be/q8WDUAiTGeU)
> 

## <a name="prerequisites"></a>Pré-requisitos

1. No serviço do Power BI ou no Desktop, a análise exige uma visualização com uma hierarquia. 
   
2. Para acompanhar estas etapas, [abra o Exemplo de Análise de Varejo](../sample-datasets.md) e crie um mapa de árvore que examina o **Total de unidades deste ano** (Valores) por **Território**, **Cidade**, **CEP** e **Nome** (Grupo).  O mapa de árvore tem uma hierarquia composta por território, cidade, CEP e nome de cidade. Cada região tem uma ou mais cidades, cada cidade tem um ou mais códigos postais e assim por diante. Por padrão, a visualização exibe somente os dados da região, porque *Região* aparece em primeiro na lista.
   
   ![Selecionar "Território"](media/end-user-drill/power-bi-hierarcy-list.png)

2. Entender como os diversos ícones de análise funcionam pode ser um desafio, então, filtre o mapa de árvore para que ele mostre somente duas das regiões menores: **KY** e **TN**. Selecione o mapa de árvore em **Filtros de nível visual**, expanda **Território** e selecione **KY** e **TN**.

    ![filtro para KY e TN](./media/end-user-drill/power-bi-filter.png)    

   Agora, apenas duas regiões são exibidas no mapa de árvore.

   ![ícone de análise dupla](./media/end-user-drill/power-bi-territories.png)

## <a name="three-ways-to-access-the-drill-features"></a>Três maneiras de acessar os recursos de análise
Há várias opções para acessar os recursos de drill down, drill up e expansão nas visualizações que têm hierarquias. Este artigo mostra como usar a primeira opção abaixo. Depois de compreender os fundamentos de como fazer drill down e expandir, todos esses métodos farão as mesmas coisas. Teste-os e escolha o que mais gosta.

- Passe o mouse sobre uma visualização para ver e usar os ícones.  

    ![caminho de análise](./media/end-user-drill/power-bi-hover.png)

- Clique com o botão direito do mouse em uma visualização e use o menu.
    
    ![menu contextual](./media/end-user-drill/power-bi-drill-menu.png)

- Na barra de menus do Power BI, clique no botão **Explorar**.

   ![Selecionar Explorar exibe ícones e opções de análise detalhada](media/end-user-drill/power-bi-explore.png)

## <a name="drill-pathways"></a>Caminhos de análise
### <a name="drill-down"></a>Fazer drill down
Existem diversas maneiras de analisar uma visualização. ***Fazer drill down*** leva você ao próximo nível da hierarquia. Então, se você está analisando o nível **Território**, é possível fazer drill down para o nível da cidade, depois, para o nível do CEP e, finalmente, para o nível do nome. Cada etapa do caminho mostra novas informações.

![caminho de análise](./media/end-user-drill/power-bi-drill-path.png)

### <a name="expand"></a>Expandir

***Expandir*** adiciona outro nível de hierarquia à exibição atual. Portanto, se você está analisando o nível **Território**, é possível expandir e adicionar detalhes de cidade, CEP e nome ao mapa de árvore. Cada etapa do caminho mostra as mesmas informações e adiciona um nível de novas informações.

![caminho expandir](./media/end-user-drill/power-bi-expand-path.png)

Também é possível escolher entre fazer drill down ou expandir um campo de cada vez ou todos os campos de uma vez. 

## <a name="drill-down-all-fields-at-a-time"></a>Fazer drill down de todos os campos de uma vez

1. Inicie no nível superior do mapa de árvore que mostra os dados de KY e TN. Amplie o mapa de árvore selecionando uma das alças e arrastando para a direita. 

    ![mapa de árvore mostrando dois estados](./media/end-user-drill/power-bi-drill-down.png) .

2. Para fazer drill down de ***todos os campos de uma só vez***, selecione a seta dupla no canto superior esquerdo da visualização ![ícone de fazer drill down duplo](./media/end-user-drill/power-bi-drill-icon3.png). Agora, o mapa de árvore mostra dados de cidade para Kentucky e Tennessee. 

    ![ícone de análise dupla](./media/end-user-drill/power-bi-drill-down1.png)
   
5. Faça drill down mais uma vez para o nível de CEP da hierarquia.

    ![ícone de análise dupla](./media/end-user-drill/power-bi-drill-down2.png)

3. Para fazer drill up de volta, selecione a seta para cima no canto superior esquerdo da visualização ![ícone fazer drill up de um nível](./media/end-user-drill/power-bi-drill-icon5.png).


## <a name="drill-down-one-field-at-a-time"></a>Fazer drill down de um campo de cada vez
Esse método usa o ícone de fazer drill down que aparece no canto superior direito da própria visualização. 

1. Selecione esse ícone para ativá-lo ![ativar drill down](./media/end-user-drill/power-bi-drill-icon2.png). Agora, você tem a opção de fazer drill down de ***um campo de cada vez***. 
   
   ![seta apontando para o ícone ativar/desativar drill down](media/end-user-drill/power-bi-drill-icon-new.png)

   Se você não ativar o drill down, a seleção de um elemento visual (como uma barra, bolha ou folha) não fará drill down; em vez disso, fará uma filtragem cruzada dos outros gráficos na página do relatório.

2. Selecione a *folha* para **TN**. Agora, o mapa de árvore exibe todas as cidades no Tennessee que têm uma loja. 

    ![mapa de árvore que mostra dados apenas para Tennesee](media/end-user-drill/power-bi-drill-down-one1.png)

2. Agora, você pode continuar fazendo drill down de Tennessee ou de uma cidade específica desse estado. Outra opção é expandir (consulte **Expandir todos os campos de uma vez**, a seguir). Vamos continuar fazendo drill down de um campo de cada vez.  Selecione **Knoxville, TN**. O mapa de árvore agora exibe o CEP da loja em Knoxville. 

   ![mapa de árvore que mostra o CEP 37919](media/end-user-drill/power-bi-drill-down-one2.png)

    Observe que o título se altera conforme você faz drill down e drill up novamente.  

## <a name="expand-all-and-expand-one-field-at-a-time"></a>Expandir tudo e expandir um campo de cada vez
Ter um mapa de árvore que mostra apenas um CEP não é informativo.  Então, expanda para um nível abaixo na hierarquia.  

1. Com o mapa de árvore ativo, selecione o ícone *expandir abaixo* ![expandir abaixo](./media/end-user-drill/power-bi-drill-icon6.png). Agora, o mapa de árvore mostra dois níveis de hierarquia: CEP e nome da loja. 

    ![mostrando o CEP e o nome da loja](./media/end-user-drill/power-bi-expand1.png)

2. Para ver todos os quatro níveis de hierarquia dos dados para Tennessee, clique na seta de drill up até chegar ao segundo nível do mapa de árvore, **Total de unidades deste ano por território e cidade**. 

    ![mapa de árvore que mostra todos os dados de Tennesee](media/end-user-drill/power-bi-drill-down-one1.png)


3. Verifique se o drill down ainda está ativo em ![ativar drill down](./media/end-user-drill/power-bi-drill-icon2.png) e selecione o ícone *expandir abaixo* ![ícone expandir abaixo](./media/end-user-drill/power-bi-drill-icon6.png). Agora, o mapa de árvore mostra detalhes adicionais. Ao invés de exibir apenas a cidade e o estado, ele também mostra o CEP. 

    ![ícone de análise dupla](./media/end-user-drill/power-bi-expand-one3.png)

4. Selecione o ícone *expandir abaixo* mais uma vez para exibir todos os quatro níveis de hierarquia de detalhes para Tennessee no mapa de árvore. Passe o mouse sobre uma folha para ver ainda mais detalhes.

   ![mapa de árvore mostrando dados de Tennessee](./media/end-user-drill/power-bi-expand-all.png)

## <a name="drilling-filters-other-visuals"></a>A exploração filtra outros elementos visuais
Ao trabalhar no modo de análise, você precisa decidir como as ações de fazer drill down e expandir afetam outras visualizações na página. 

Por padrão, a análise não filtra outros visuais em um relatório. Mas esse recurso pode ser habilitado no Power BI Desktop e no serviço do Power BI. 

1. No Desktop, selecione a guia **Formatar** e marque a caixa de seleção **Filtros detalhados de outros elementos visuais**.

    ![configuração no Power BI Desktop](./media/end-user-drill/power-bi-drill-filters-desktop.png)

2. Agora, ao fazer drill down (ou drill up, ou expandir) em um visual com uma hierarquia, essa ação filtrará os outros visuais da página. 

    ![configuração no Desktop](./media/end-user-drill/power-bi-drill-filters.png)

    ![configuração no Desktop](./media/end-user-drill/power-bi-drill-filters2.png)

> [!NOTE]
> Para habilitar esse recurso no serviço do Power BI, na barra de menus superior, selecione **Interações visuais > Filtros detalhados de outros elementos visuais**.
>
> ![configuração no serviço do Power BI](./media/end-user-drill/power-bi-drill-filters-service.png)



## <a name="understanding-the-hierarchy-axis-and-hierarchy-group"></a>Noções básicas de eixo de hierarquia e grupo de hierarquias
É possível pensar no eixo de hierarquia e no grupo de hierarquias como os mecanismos que podem ser usados para aumentar e diminuir a granularidade dos dados que você deseja exibir. Todos os dados que podem ser organizados em categorias e subcategorias são qualificados como tendo uma hierarquia. Isso, obviamente, inclui as datas e horas.

É possível criar uma visualização no Power BI para ter uma hierarquia selecionando um ou mais campos de dados a serem adicionados ao contêiner **Eixo** ou ao contêiner **Grupo**, juntamente com os dados que você deseja examinar como campos de dados no contêiner **Valores**. Você saberá se seus dados são hierárquicos se os ícones de *Modo de análise* são exibidos nos cantos superiores esquerdo e direito de sua visualização. 

Essencialmente, é conveniente pensar em dois tipos de dados hierárquicos:
- Dados de data e hora – se você tiver um campo de dados com um tipo de dados DateTime, já terá os dados hierárquicos. O Power BI cria automaticamente uma hierarquia para qualquer campo de dados cujos valores podem ser analisados em uma estrutura [DateTime](https://msdn.microsoft.com/library/system.datetime.aspx). Só é necessário adicionar um campo DateTime ao contêiner **Eixo** ou **Grupo**.
- Dados categóricos: se os dados forem derivados de coleções que contenham subcoleções ou, caso contrário, tenham linhas de dados que compartilham valores comuns, você terá dados hierárquicos.

O Power BI permite expandir em um subconjunto ou em todos. É possível fazer drill down em seus dados para ver um subconjunto único em cada nível ou para ver todos os subconjuntos simultaneamente em cada nível. Por exemplo, é possível fazer drilldown de um ano específico ou ver todos os resultados de cada ano à medida que você percorre a hierarquia. Por outro lado, é possível fazer drill up da mesma maneira.

As seções a seguir descrevem como fazer drill down do modo de exibição mais alto, médio e mais baixo.

### <a name="hierarchical-data-and-time-data"></a>Dados hierárquicos e dados de tempo
Neste exemplo, acompanhe o [exemplo de Análise de varejo](../sample-datasets.md) e crie uma visualização de gráfico de colunas empilhadas que examina **Mês** (Eixo) por **TotalSales** (Valores).  

Embora o campo de dados Eixo seja **Mês**, ele ainda cria uma categoria **Ano** no contêiner **Eixo**. Isso ocorre, porque o Power BI fornece a estrutura DateTime completa para todos os valores que ela lê. A parte superior da hierarquia mostra os dados do ano.

![Barra única mostrando os dados agrupados por ano](media/end-user-drill/power-bi-hierarchical-axis-datetime-1.png)

Com o modo de análise ativo, clique na barra no gráfico para descer um nível da hierarquia. Você verá três barras para os dados dos trimestres disponíveis. Em seguida, nos ícones do canto superior esquerdo, escolha **Expandir todo o campo um nível abaixo na hierarquia**. Em seguida, faça novamente para obter o nível mais baixo da hierarquia, que mostra os resultados para cada mês.

![gráfico de barras para ver a barra por mês](media/end-user-drill/power-bi-hierarchical-axis-datetime-2.png)

Além da visualização, é possível ver a hierarquia refletida nos dados renderizados para cada relatório. A tabela a seguir mostra os resultados de **Mostrar dados** em um relatório que faz drill down de um único mês ou de todos os meses. 

Observe que os dados são os mesmos para relatórios trimestrais e anuais, mas, depois de fazer drill down para o nível de detalhe especificado para **Valores**, será possível ver como o único relatório fica mais específico e como o relatório de "todos os meses" tem mais dados.


|Modo de expansão|Ano|Trimestre|Mês|Dia|
| ---|:---:|:---:|:---:|---|
|Único|![um ano](./media/end-user-drill/power-bi-hierarchical-year.png)|![um trimestre](media/end-user-drill/power-bi-hierarchical-quarter.png)|![um mês](./media/end-user-drill/power-bi-hierarchical-one-month.png)|![um dia](media/end-user-drill/power-bi-hierarchical-one-day.png)|
|Tudo|![todos os anos](./media/end-user-drill/power-bi-hierarchical-year.png)|![todos os trimestres](media/end-user-drill/power-bi-hierarchical-quarter.png)|![todos os meses](./media/end-user-drill/power-bi-hierarchical-all-month.png)|![todos os dias](media/end-user-drill/power-bi-hierarchical-all-day.png)|


### <a name="hierarchical-category-data"></a>Dados de categoria hierárquica
Os dados que foram modelados de coleções e subcoleções são hierárquicos. Um bom exemplo disso são os dados de localização. Considere uma tabela em uma fonte de dados cujas colunas são País, Estado, Cidade e CEP. Dados que compartilham o mesmo País, Estado e Cidade são hierárquicos.

Neste exemplo, acompanhe o [exemplo de Análise de varejo](../sample-datasets.md). Crie uma exibição de gráfico de colunas empilhadas que examina o **Total de unidades deste ano** (Valores) por **Território**, **Cidade**, **CEP** e **Nome** (Grupo).  

![gráfico de barra mostrando o Total de unidades deste ano por território](media/end-user-drill/power-bi-hierarchical-axis-category-1.png)

Com o modo de análise ativo, nos ícones do canto superior esquerdo, escolha **Expandir todos um nível abaixo na hierarquia** três vezes.
Você deve estar no nível mais baixo da hierarquia, que mostra os resultados de Território, Cidade e CEP.

![gráfico de barras mostrando o nível mais baixo da hierarquia, o mais detalhado](media/end-user-drill/power-bi-hierarchical-axis-category-2.png)

Além da visualização, é possível ver a hierarquia refletida nos dados renderizados para cada relatório. A tabela a seguir mostra os resultados de **Mostrar dados** em um relatório que faz drill down de um único território ou de todos os territórios. À medida que você faz drill down, é possível ver como o único relatório fica mais específico e como o relatório de "todos os territórios" tem mais dado.


| Modo de expansão|Território|Cidade|CEP|Nome|
| ---|:---:|:---:|:---:|---|
|Único|![um território](./media/end-user-drill/power-bi-hierarchical-territory.png)|![uma cidade](media/end-user-drill/power-bi-hierarchical-one-territory-city.png)|![um CEP](./media/end-user-drill/power-bi-hierarchical-one-territory-city-postal.png)|![um nome](media/end-user-drill/power-bi-hierarchical-one-territory-city-postal-name.png)|
|Tudo|![todos os territórios](./media/end-user-drill/power-bi-hierarchical-territory.png)|![todas as cidades](media/end-user-drill/power-bi-hierarchical-all-territory-city.png)|![todos os CEPs](./media/end-user-drill/power-bi-hierarchical-all-territory-city-postal.png)|![todos os nomes](media/end-user-drill/power-bi-hierarchical-all-territory-city-postal-name.png)|


## <a name="considerations-and-limitations"></a>Considerações e limitações
* Se a adição de um campo de data a uma visualização não criar uma hierarquia, pode ser que o campo "data" não esteja realmente salvo como uma data. Se o conjunto de dados for seu, abra-o na exibição de *Dados* do Power BI Desktop, selecione a coluna que contém a data e, na guia de Modelagem, altere o **Tipo de Dados** para **Data** ou **Data/Hora**. Se o relatório foi compartilhado com você, entre em contato com o proprietário para solicitar a alteração.  
  
  ![selecione a exibição de dados e, no canto superior direito, consulte o Tipo de data](media/end-user-drill/power-bi-change-data-type2.png)

## <a name="next-steps"></a>Próximas etapas
[Visualizações em relatórios do Power BI](../visuals/power-bi-report-visualizations.md)

[Relatórios do Power BI](end-user-reports.md)

[Power BI – conceitos básicos](end-user-basic-concepts.md)

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

