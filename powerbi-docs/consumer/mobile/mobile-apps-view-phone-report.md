---
title: Exibir relatórios do Power BI otimizados para seu telefone
description: Leia sobre a interação com páginas de relatório otimizadas para exibição em aplicativos do Power BI.
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 04/22/2019
ms.author: mshenhav
ms.openlocfilehash: 79ca47f83bb39ab9d6df141b5a26dcb54e00c72c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100977"
---
# <a name="view-power-bi-reports-optimized-for-your-phone"></a>Exibir relatórios do Power BI otimizados para seu telefone

Aplica-se a:

| ![iPhone](./media/mobile-apps-view-phone-report/ios-logo-40-px.png) | ![Telefone Android](./media/mobile-apps-view-phone-report/android-logo-40-px.png) |
|:--- |:--- |
| iPhones |Telefones Android |

Quando você exibe um relatório do Power BI em seu telefone, o Power BI verifica se o relatório foi otimizado para telefones. Em caso afirmativo, o Power BI abre automaticamente o relatório otimizado no modo de exibição de retrato.

![Relatório no modo retrato](./media/mobile-apps-view-phone-report/07-power-bi-phone-report-portrait.png)

Se um relatório otimizado para telefone não existir, o relatório será aberto, mas no modo de exibição de paisagem não otimizada. Mesmo em um relatório otimizado para telefones, se você mudar a orientação do telefone, o relatório será aberto na exibição não otimizada com o layout original do relatório. Se somente algumas páginas forem otimizadas, você encontrará uma mensagem na exibição de retrato, indicando que o relatório está disponível em paisagem.

![Página de relatório não otimizada](./media/mobile-apps-view-phone-report/06-power-bi-phone-report-page-not-optimized.png)

Todos os outros recursos de relatórios do Power BI ainda funcionam em relatórios otimizados para telefones. Leia mais sobre o que você pode fazer em:

* [Relatórios sobre iPhones](mobile-reports-in-the-mobile-apps.md). 
* [Relatórios sobre telefones Android](mobile-reports-in-the-mobile-apps.md).

## <a name="filter-the-report-page-on-a-phone"></a>Filtrar a página de relatório em um telefone
Se um relatório otimizado para telefone tiver filtros definidos, quando ele for exibido em um telefone, será possível utilizar esses filtros. O relatório é aberto em seu telefone, filtrado para os valores que estão sendo filtrados no relatório na web. Você verá uma mensagem informando que existem filtros ativos na página. É possível alterar os filtros no seu telefone.

1. Toque no ícone de filtro ![Ícone de filtro do telefone](./media/mobile-apps-view-phone-report/power-bi-phone-filter-icon.png) na parte inferior da página. 
2. Use a filtragem básica ou avançada para ver os resultados em que você está interessado.
   
    ![Filtro avançado do relatório de telefone do BI do telefone](./media/mobile-apps-view-phone-report/power-bi-iphone-advanced-filter-toronto.gif)

## <a name="cross-highlight-visuals"></a>Elementos visuais com realce cruzado
Elementos visuais em Retrato de realce cruzado exibição funciona da forma que faz no serviço do Power BI e em telefones no modo paisagem: quando você seleciona dados em um visual, dados relacionados são realçados em outros visuais nessa página.

Leia mais sobre [filtragem e realce no Power BI](../../power-bi-reports-filters-and-highlighting.md).

## <a name="select-visuals"></a>Selecionar elementos visuais
Em relatórios de telefone quando você seleciona um elemento visual, o relatório realça o elemento visual e foca nele, neutralizando gestos da tela.

Com o visual selecionado, você executar ações como rolar no elemento visual. Para cancelar a seleção de um elemento visual, basta tocar em qualquer parte fora da área do elemento visual.

## <a name="open-visuals-in-focus-mode"></a>Abrir elementos visuais em modo de foco
Relatórios de telefone também oferecem um modo de foco: Você pode obter uma exibição maior de um único visual e explorá-lo mais facilmente.

* Em um relatório de telefone, toque no botão de reticências ( **...** ) no canto superior direito de um visual > **Expandir para o modo de foco**.
  
    ![Expandir para o modo de foco](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)

O que fazer no modo de foco é transportado para a tela de relatório e vice-versa. Por exemplo, se você realça um valor em um visual e depois retornar ao relatório inteiro, o relatório é filtrado para o valor realçado no visual.

Algumas ações somente são possíveis no modo de foco, devido às restrições de tamanho de tela:

* **Detalhar** as informações exibidas em um visual. Leia mais sobre como [fazer drill-down e up](mobile-apps-view-phone-report.md#drill-down-in-a-visual) em um relatório de telefone abaixo.
* **Classifique** os valores no elemento visual.
* **Reverter**: desmarque as etapas de exploração que você efetuou em um visual e reverta para a definição estabelecida quando o relatório foi criado.
  
    Para limpar toda a exploração de um visual, toque no botão de reticências ( **...** ) > **Reverter**.
  
    ![Reverter](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)
  
    Reverter está disponível no nível do relatório, limpando a exploração de todos os elementos visuais, ou no nível de visual, limpando a exploração de visual selecionado.   

## <a name="drill-down-in-a-visual"></a>Fazer drill down em um visual
Se os níveis hierárquicos forem definidos em um visual, você poderá fazer drill down nas informações detalhadas exibidas em um visual e, em seguida, fazer backup. [Adicione o drill-down em um visual](../end-user-drill.md) no serviço do Power BI ou no Power BI Desktop.

Há alguns tipos de drill-down:

### <a name="drill-down-on-a-value"></a>Fazer drill down em um valor
1. Toque longa (tap e hold) em um ponto de dados em um visual.
2. Dica de ferramenta será exibida, e se a hierarquia é definida, o rodapé da dica de ferramenta mostrará drill down e seta para cima.
3. Toque na seta para baixo para fazer drill down

    ![Busca detalhada de toque](././media/mobile-apps-view-phone-report/report-drill-down.png)
    
4. Toque na seta para cima para fazer drill-up.

### <a name="drill-to-next-level"></a>Fazer drill para o próximo nível
1. Em um relatório em um telefone, toque no botão de reticências ( **...** ) no canto superior direito > **Expandir para o modo de foco**.
   
    ![Expandir para o modo de foco](././media/mobile-apps-view-phone-report/power-bi-phone-report-focus-mode.png)
   
    Neste exemplo, as barras mostram os valores de estados.
2. Toque no ícone Explorar ![ícone Explorar](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-icon.png) no canto inferior esquerdo.
   
    ![Modo de exploração](./media/mobile-apps-view-phone-report/power-bi-phone-report-explore-mode.png)
3. Toque em **Mostrar o próximo nível** ou em **Expandir para o próximo nível**.
   
    ![Expandir para o próximo nível](./media/mobile-apps-view-phone-report/power-bi-phone-report-expand-levels.png)
   
    Agora as barras mostram os valores para as cidades.
   
    ![Níveis expandidos](./media/mobile-apps-view-phone-report/power-bi-phone-report-expanded-levels.png)
4. Se você tocar na seta no canto superior esquerdo, você voltará ao relatório de telefone com os valores ainda expandidos para um nível inferior.
   
    ![Ainda expandido para um nível inferior](./media/mobile-apps-view-phone-report/power-bi-back-to-phone-report-expanded-levels.png)
5. Para voltar ao nível original, toque no botão de reticências ( **...** ) novamente > **Reverter**.
   
    ![Reverter](././media/mobile-apps-view-phone-report/power-bi-phone-report-revert-levels.png)

## <a name="drill-through-from-a-value"></a>Detalhar de um valor
Drill-through conecta-se valores em uma página de relatório, com outras páginas do relatório. Quando você analisar por meio de um ponto de dados para outra página de relatório, os valores de ponto de dados são usados para filtrar o esburacado por meio da página, ou ele estará no contexto dos dados selecionados.
Os autores de relatório podem [definem o drill-through](https://docs.microsoft.com/power-bi/desktop-drillthrough) quando criam o relatório.

1. Toque longa (tap e hold) em um ponto de dados em um visual.
2. Dica de ferramenta aparecerá e se detalhamento for definido, o rodapé da dica de ferramenta mostrará drill-through seta.
3. Toque na seta para drill-through.

    ![Toque em drill-through.](././media/mobile-apps-view-phone-report/report-drill-through1.png)

4. Escolha qual página de relatório para drill-through

    ![Escolha a página de relatório](././media/mobile-apps-view-phone-report/report-drill-through2.png)

5. Use o botão Voltar, o cabeçalho de aplicativo para voltar para a página a que partir do início.


## <a name="next-steps"></a>Próximas etapas
* [Criar relatórios otimizados para os aplicativos de telefone do Power BI](../../desktop-create-phone-report.md)
* [Criar uma exibição de telefone de um dashboard no Power BI](../../service-create-dashboard-mobile-phone-view.md)
* [Criar visuais responsivos otimizados para qualquer tamanho](../../visuals/desktop-create-responsive-visuals.md)
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)

