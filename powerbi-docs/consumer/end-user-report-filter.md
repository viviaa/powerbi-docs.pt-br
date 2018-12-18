---
title: Adicionar um filtro a um relatório
description: Como adicionar um filtro a um relatório no serviço do Power BI para consumidores
author: mihart
manager: kvivek
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: ea219071b475bf5bb9123e1aa3bbaca412507a8e
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53280755"
---
# <a name="take-a-tour-of-the-report-filters-pane"></a>Faça um tour pelo painel Filtros do relatório
Este artigo oferece uma visão geral do painel Filtros do relatório no serviço do Power BI.

Há muitas maneiras diferentes de filtrar dados no Power BI. Recomendamos que você leia [Sobre filtros e realce](../power-bi-reports-filters-and-highlighting.md) primeiro.

![relatório no navegador](media/end-user-report-filter/power-bi-browser.png)

## <a name="working-with-the-report-filters-pane"></a>Trabalhar com o painel de Filtros do relatório
Quando um colega compartilhar um relatório com você, não se esqueça de examinar o painel **Filtros**. Às vezes, ele está recolhido na borda direita do relatório. Selecione-o para expandi-lo.   

![relatório no navegador](media/end-user-report-filter/power-bi-expanded.png)

O painel Filtros contém os filtros que foram adicionados ao relatório pelo *designer* do relatório. *Consumidores* como você podem interagir com os filtros e salvar suas alterações, mas não podem adicionar novos filtros ao relatório. Por exemplo, na captura de tela acima, o designer adicionou dois filtros de nível de página: Segmento e Ano. Você pode interagir e alterar esses filtros, mas não pode adicionar um terceiro filtro no nível de página.

No Serviço do Power BI, relatórios retêm as alterações feitas no painel Filtros e essas alterações são repassadas para a versão móvel do relatório. Para redefinir o painel Filtro para os padrões do designer, selecione **Redefinir para padrão** na barra de menus superior.     

## <a name="open-the-filters-pane"></a>Abrir o painel Filtros
Quando um relatório é aberto, o painel Filtros é exibido no lado direito da tela do relatório. Caso não veja o painel, selecione a seta no canto superior direito para expandi-lo.  

Neste exemplo, selecionamos um visual que tem 6 filtros. A página de relatório também tem filtros, listados sob o título **Filtros de nível de página**. Há um [filtro Detalhamento](../power-bi-report-add-filter.md) e o relatório inteiro também tem um filtro:  **FiscalYear** é 2013 ou 2014.

![lista de filtros](media/end-user-report-filter/power-bi-filter-list.png)

Alguns filtros têm a palavra **Todos** ao seu lado, o que significa que todos os valores estão sendo incluído no filtro.  Por exemplo, **Chain(All)** na captura de tela acima informa que essa página de relatório inclui dados sobre cadeias de armazenamento.  Por outro lado, o filtro de nível de relatório ou **FiscalYear é 2013 ou 2014** informa que o relatório inclui somente dados para os anos fiscais de 2013 e 2014.

Qualquer pessoa que exibir este relatório pode interagir com esses filtros.

- Pesquise na página, no visual, no relatório e em filtros de detalhamento para localizar e selecionar o valor desejado. 

    ![Pesquisar em um filtro](media/end-user-report-filter/power-bi-filter-search.png)

- Veja os detalhes do filtro focalizando e selecionando a seta ao lado do filtro.
  
   ![mostra Lindseys selecionado](media/end-user-report-filter/power-bi-expan-filter.png)
* Altere o filtro, por exemplo, altere **Lindseys** para **Fashions Direct**.
  
     ![mostra Fashions Direct selecionado](media/end-user-report-filter/power-bi-filter-chain.png)

* Redefina os filtros para seu estado original selecionando **Redefinir para padrão** na barra de menus superior.    
    ![redefinir para padrão](media/end-user-report-filter/power-bi-reset-to-default.png)
    
* Exclua o filtro selecionando o **x** ao lado do nome do filtro.
  
    ![x realçado](media/end-user-report-filter/power-bi-delete-filter.png)

  A exclusão de um filtro o remove da lista, mas não exclui os dados do relatório.  Por exemplo, se você excluir o filtro **Ano Fiscal é 2013 ou 2014**, os dados do ano fiscal ainda permanecerão no relatório, mas ele não será mais filtrado para mostrar somente 2013 e 2014; mostrará todos os anos fiscais contidos nos dados.  No entanto, depois de excluir o filtro, você não poderá modificá-lo novamente, já que ele é removido da lista. Uma opção melhor é limpar o filtro selecionando o ícone de borracha ![ ícone de borracha ](media/end-user-report-filter/power-bi-eraser-icon.png).
  
  



## <a name="clear-a-filter"></a>Limpar um filtro
 No modo de filtragem avançada ou básica, selecione o ícone de borracha  ![ícone de borracha](media/end-user-report-filter/pbi_erasericon.jpg) para limpar o filtro. 


## <a name="types-of-filters-text-field-filters"></a>Tipos de filtros: filtros de campo de texto
### <a name="list-mode"></a>Modo de lista
Marcar uma caixa de seleção ou selecionar ou demarcar o valor. A caixa de seleção **Todos** pode ser usada para alternar o estado de todas as caixas de seleção ativadas ou desativadas. As caixas de seleção representam todos os valores disponíveis para esse campo.  À medida que você ajusta o filtro, o ajuste é atualizado para refletir suas escolhas. 

![filtro de modo de lista](media/end-user-report-filter/power-bi-restatement-new.png)

Observe como a reformulação agora diz "é Mar, Abr ou Mai".

### <a name="advanced-mode"></a>Modo avançado
Selecione **Filtragem avançada** para alternar para o modo avançado. Use as caixas de texto e controles de lista suspensa para identificar quais campos serão incluídos. Escolhendo entre **E** e **Ou**, você pode criar expressões de filtro complexas. Selecione o botão **Aplicar filtro** ao definir os valores desejados.  

![modo avançado](media/end-user-report-filter/power-bi-advanced.png)

## <a name="types-of-filters-numeric-field-filters"></a>Tipos de filtros: filtros de campo numérico
### <a name="list-mode"></a>Modo de lista
Se os valores são finitos, selecionar o nome do campo exibe uma lista.  Veja **Filtros de campo de texto** &gt; **Modo de lista** acima para obter ajuda sobre como usar caixas de seleção.   

### <a name="advanced-mode"></a>Modo avançado
Se os valores são infinitos ou representam um intervalo, selecionar o nome do campo abre o modo de filtro avançado. Use a lista suspensa e as caixas de texto para especificar um intervalo de valores que você deseja ver. 

![filtro avançado](media/end-user-report-filter/power-bi-dropdown-and-text.png)

Escolhendo entre **E** e **Ou**, você pode criar expressões de filtro complexas. Selecione o botão **Aplicar filtro** ao definir os valores desejados.

## <a name="types-of-filters-date-and-time"></a>Tipos de filtros: data e hora
### <a name="list-mode"></a>Modo de lista
Se os valores são finitos, selecionar o nome do campo exibe uma lista.  Veja **Filtros de campo de texto** &gt; **Modo de lista** acima para obter ajuda sobre como usar caixas de seleção.   

### <a name="advanced-mode"></a>Modo avançado
Se os valores de campo representam a data ou hora, você pode especificar uma hora de início/término quando usar os filtros de data/hora.  

![filtro de datetime](media/end-user-report-filter/pbi_date-time-filters.png)


## <a name="next-steps"></a>Próximas etapas
[Saiba como e por que os visuais executam filtro cruzado e realce cruzado entre si em uma página de relatório](end-user-interactions.md)