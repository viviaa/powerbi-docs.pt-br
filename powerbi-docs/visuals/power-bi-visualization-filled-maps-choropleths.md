---
title: Mapas coropléticos no Power BI
description: Documentação sobre como criar Mapas coropléticos no Power BI
author: mihart
manager: kvivek
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 06/19/2019
ms.author: mihart
LocalizationGroup: Visualizations
ms.openlocfilehash: 0123d8123170cfa78b3d13a55ed2f367af0447ae
ms.sourcegitcommit: 90aa7ea5fcc7cf0fd7f6c3c1efeff5f27e8ef0dd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67299345"
---
# <a name="filled-maps-choropleths-in-power-bi"></a>Mapas coropléticos no Power BI
Um mapa coroplético usa sombreamento ou tonalidade ou padrões para exibir como um valor difere na proporção em uma localização geográfica ou região.  Exiba rapidamente essas diferenças relativas com sombreamento que varia de claro (menos frequente/inferior) para escuro (mais frequente/mais).    

![Mapa dos EUA](media/power-bi-visualization-filled-maps-choropleths/large-map.png)

## <a name="what-is-sent-to-bing"></a>O que é enviado ao Bing
O Power BI é integrado ao Bing para fornecer as coordenadas de mapa padrão (um processo chamado geocódigo). Quando você cria uma visualização de mapa no serviço do Power BI ou no Power BI Desktop, os dados nos buckets **Local**, **Latitude** e **Longitude** (que estão sendo usados para criar essa visualização) são enviados ao Bing.

Você ou seu administrador talvez precise atualizar o firewall para permitir o acesso às URLs usadas pelo Bing para geocodificação.  Essas URLs são:
- https://dev.virtualearth.net/REST/V1/Locations    
- https://platform.bing.com/geo/spatial/v1/public/Geodata    
- https://www.bing.com/api/maps/mapcontrol

Para obter mais informações sobre os dados enviados ao Bing e ver dicas sobre como aumentar seu sucesso com o geocódigo, confira [Dicas e truques para visualizações de mapa](power-bi-map-tips-and-tricks.md).

## <a name="when-to-use-a-filled-map"></a>Quando usar um mapa coroplético
Mapas coropléticos são uma ótima opção:

* para exibir informações quantitativas em um mapa.
* para mostrar as relações e os padrões espaciais.
* quando seus dados são padronizados.
* ao trabalhar com dados socioeconômicos.
* quando regiões definidas são importantes.
* para obter uma visão geral da distribuição entre os locais geográficos.

### <a name="prerequisites"></a>Pré-requisitos
- Serviço do Power BI ou Power BI Desktop
- Exemplo de Vendas e Marketing

Para acompanhar, o tutorial usa o serviço Power BI, não o Power BI Desktop.

## <a name="create-a-basic-filled-map"></a>Criar um mapa coroplético básico
Neste vídeo, Kim cria um mapa básico e o converte em um mapa coroplético.

<iframe width="560" height="315" src="https://www.youtube.com/embed/ajTPGNpthcg" frameborder="0" allowfullscreen></iframe>

### <a name="get-data-and-add-a-new-blank-page-to-the-report"></a>Obter dados e adicionar uma nova página em branco ao relatório
1. Para criar seu próprio mapa coroplético, [baixe o exemplo Vendas e Marketing](../sample-datasets.md) conectando-se ao Power BI e selecionando **Obter Dados \> Exemplos \> Vendas e Marketing \> Conectar**. Ou obtenha o aplicativo **Vendas e Marketing do Power BI** em appsource.com. 

2. Abra o relatório de Vendas e Marketing.

   ![O relatório de Vendas e Marketing é aberto](media/power-bi-visualization-filled-maps-choropleths/power-bi-report-canvas.png)
3. O Power BI abre o relatório. Selecione **Editar relatório** para abrir o relatório no modo de [Exibição de Edição](../service-interact-with-a-report-in-editing-view.md).

4. Adicione uma nova página selecionando o sinal de adição amarelo na parte inferior da tela do relatório.

    ![Guias de relatório](media/power-bi-visualization-filled-maps-choropleths/power-bi-new-page.png)

### <a name="create-a-filled-map"></a>Criar um mapa coroplético
1. No painel Campos, selecione o campo **Área geográfica** \> **Estado**.    

   ![marca de seleção amarela ao lado de Estado](media/power-bi-visualization-filled-maps-choropleths/power-bi-state.png)
2. [Converta o gráfico](power-bi-report-change-visualization-type.md) em um mapa coroplético. Observe que o **Estado** agora está no contêiner **Local**. O Bing Maps usa o campo no contêiner **Local** para criar o mapa.  O local pode ser uma variedade de locais válidos: países, estados, condados, cidades, CEPs ou outros códigos postais, etc. O Bing Maps fornece formas de mapa coroplético para locais em todo o mundo. Sem uma entrada válida no Local, o Power BI não pode criar o mapa coroplético.  

   ![modelos com o ícone para o mapa coroplético realçado](media/power-bi-visualization-filled-maps-choropleths/img003.png)
3. Filtre o mapa para exibir somente os Estados Unidos.

   a.  Na parte inferior do painel Visualizações, procure a área **Filtros** .

   b.  Passe o mouse sobre **Estado** e clique na divisa de expansão  
   ![Filtros de nível visual mostrando Estado (todos)](media/power-bi-visualization-filled-maps-choropleths/img004.png)

   c.  Coloque uma marca de seleção ao lado de **Todos** e remova a marca de seleção ao lado de **AK**.

   ![Lista suspensa Estado com as opções Todos e AK não selecionadas](media/power-bi-visualization-filled-maps-choropleths/img005.png)
4. Selecione o ícone de rolo de tinta para abrir o painel Formatação e escolha **Cores de dados**.

    ![Painel Formatação mostrando a opção Cores de dados](media/power-bi-visualization-filled-maps-choropleths/power-bi-data-color.png)

5. Selecione os três pontos verticais e escolha **Formatação condicional**.

    ![Botão de formatação condicional de cores de dados](media/power-bi-visualization-filled-maps-choropleths/power-bi-conditional-formatting.png)

6. Use a tela **Cor padrão – Cores de dados** para determinar como seu mapa coroplético será sombreado. As opções disponíveis para você incluem em qual campo basear o sombreamento e como aplicar o sombreamento. Neste exemplo, estamos usando o campo **SalesFact** > **Sentimento** e definindo o valor mais baixo para sentimento como vermelho e o valor mais alto como verde. Os valores que ficam entre o máximo e o mínimo serão sombreados de vermelho e verde. A ilustração na parte inferior da tela mostra o intervalo de cores que serão usados. 

    ![Painel Cor padrão com Sentimento selecionado](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment.png)

7. O mapa coroplético é sombreado em verde e vermelho, sendo que vermelho representa os números de sentimento inferiores e verde representando os sentimentos superiores, mais positivos.  Para exibir detalhes adicionais, arraste um campo para o espaço Dicas de ferramenta.  Aqui, adicionei **Lacuna de Sentimento** e destaquei o estado de Idaho (ID), e vi que essa lacuna de sentimento está baixa, em 6.
   ![mapa coroplético mostrando as dicas de ferramenta de Idaho](media/power-bi-visualization-filled-maps-choropleths/power-bi-filled-map-idaho.png)

10. [Salve o relatório](../service-report-save.md).

O Power BI fornece muito controle sobre a aparência de seu mapa coroplético. Familiarize-se com esses controles de cores de dados até obter a aparência desejada. 

## <a name="highlighting-and-cross-filtering"></a>Realce e filtragem cruzada
Para obter informações sobre como usar o painel Filtros, veja [Adicionar um filtro a um relatório](../power-bi-report-add-filter.md).

Realçar um local em um Mapa coroplético faz a filtragem cruzada com outras visualizações na página do relatório, e vice-versa.

1. Para acompanhar, primeiro salve esse relatório selecionando **Arquivo > Salvar**. 

2. Copie o mapa coroplético usando CTRL-C.

3. Na parte inferior da tela do relatório, selecione a guia **Sentimento** para abrir a página de relatório de sentimento.

    ![Guia Sentimento selecionada](media/power-bi-visualization-filled-maps-choropleths/power-bi-sentiment-tab.png)

4. Mova e redimensione as visualizações na página para aumentar o espaço disponível e, em seguida, use CTRL-V para colar o mapa coroplético do relatório anterior.

   ![Mapa coroplético adicionado à página Sentimento](media/power-bi-visualization-filled-maps-choropleths/power-bi-map.png)

5. No mapa coroplético, selecione um estado.  Isso destaca as outras visualizações na página. Selecionar **Texas**, por exemplo, mostra que o sentimento é 74, Texas está no Distrito Central \#23.   
   ![Texas selecionado](media/power-bi-visualization-filled-maps-choropleths/power-bi-texas.png)
2. Selecione um ponto de dados no gráfico de linhas na VanArsdel – Sentimento por Mês. Isso filtra o mapa coroplético para mostrar os dados de Sentimento para VanArsdel, e não a concorrência.  
   ![novo sombreamento](media/power-bi-visualization-filled-maps-choropleths/power-bi-yes.png)

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
Dados de mapa podem ser ambíguos.  Por exemplo, há uma Paris, França, mas também há uma Paris, no Texas. Seus dados geográficos provavelmente são armazenados em colunas separadas – uma coluna de nomes de cidades, uma coluna de nomes de estado ou província, etc. – portanto, o Bing pode não ser capaz de dizer qual Paris é. Se o seu conjunto de dados já contém dados de latitude e longitude, o Power BI tem campos especiais para ajudar a tornar os dados do mapa inequívocos. Basta arrastar o campo que contém os dados de latitude na área Visualizações \> Latitude.  E faça o mesmo para os dados de longitude.    

![Painéis Campos e Visualizações](media/power-bi-visualization-filled-maps-choropleths/pbi-latitude.png)

Se você tiver permissões para editar o conjunto de dados no Power BI Desktop, assista a este vídeo para obter ajuda e resolver a ambiguidade de mapa.

<iframe width="560" height="315" src="https://www.youtube.com/embed/Co2z9b-s_yM" frameborder="0" allowfullscreen></iframe>

Se você não tiver acesso a dados de latitude e longitude, mas tiver acesso de edição ao conjunto de dados, [siga estas instruções para atualizar o conjunto de dados](https://support.office.com/article/Maps-in-Power-View-8A9B2AF3-A055-4131-A327-85CC835271F7).

Para obter mais ajuda com Visualizações de mapa, veja [Tips and tricks for map visualizations](../power-bi-map-tips-and-tricks.md) (Dicas e truques para visualizações de mapa).

## <a name="next-steps"></a>Próximas etapas

[Mapa de formas](desktop-shape-map.md)

[Tipos de visualização no Power BI](power-bi-visualization-types-for-reports-and-q-and-a.md)