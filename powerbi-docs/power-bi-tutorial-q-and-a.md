---
title: Use o Power BI p e r para explorar e criar elementos visuais
description: Como usar o Power BI p e r para criar novas visualizações em dashboards e relatórios.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 05/13/2019
ms.author: maggies
LocalizationGroup: Ask questions of your data
ms.openlocfilehash: c6fd8967a49515af4d0614653b3d7550c335052f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65625369"
---
# <a name="use-power-bi-qa-to-explore-your-data-and-create-visuals"></a>Usar o Power BI p e r para explorar seus dados e criar elementos visuais

Às vezes, a maneira mais rápida de obter uma resposta de seus dados é fazer uma pergunta usando o idioma natural. O recurso de p e r no Power BI permite que você explore seus dados em suas próprias palavras.  A primeira parte deste artigo mostra como você pode usar p e r em painéis no serviço do Power BI. A segunda parte mostra que você pode fazer com p e r ao criar relatórios no serviço do Power BI ou Power BI Desktop. Para obter mais informações, consulte o [p e r para os consumidores](consumer/end-user-q-and-a.md) artigo. 

[P e r nos aplicativos móveis do Power BI](consumer/mobile/mobile-apps-ios-qna.md) e [p e r com o Power BI Embedded](developer/qanda.md) são abordados em artigos separados. 

P e r é interativo e até mesmo divertida. Geralmente, uma pergunta que leva a outras pessoas conforme as visualizações revelam caminhos interessantes para buscar. Veja Amanda demonstrando o uso de P e R para criar visualizações, aprofundando-se nesses elementos visuais e fixando-os nos dashboards.

<iframe width="560" height="315" src="https://www.youtube.com/embed/qMf7OLJfCz8?list=PL1N57mwBHtN0JFoKSR0n-tBkUJHeMP2cP" frameborder="0" allowfullscreen></iframe>

## <a name="part-1-use-qa-on-a-dashboard-in-the-power-bi-service"></a>Parte 1: Usar p e r em um dashboard no serviço do Power BI

No serviço do Power BI (app.powerbi.com), um dashboard contém blocos fixados de um ou mais conjuntos de dados, portanto, você pode fazer perguntas sobre os dados contidos em qualquer um desses conjuntos de dados. Para ver quais relatórios e conjuntos de dados foram usados para criar o dashboard, selecione **exibir relacionados** na barra de menus.

![Exibir conjuntos de dados e relatórios relacionados](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

A caixa de pergunta de p e r está localizada no canto superior esquerdo do painel, você digitará sua pergunta usando idioma natural. Não vê uma caixa de p? Ver [considerações e solução de problemas](consumer/end-user-q-and-a.md#considerations-and-troubleshooting) na **p e r para os consumidores** artigo.  P e r reconhece as palavras que você digita e descobre onde (no conjunto de dados) para encontrar a resposta. P e R também ajuda a sua pergunta com preenchimento automático, ajuste e outros auxílios textuais e visuais.

![Caixa de perguntas de p e r](media/power-bi-tutorial-q-and-a/powerbi-qna.png)

A resposta à sua pergunta é exibida como uma visualização interativa e atualizações como modificar a pergunta.

1. Abra um dashboard e coloque o cursor na caixa de perguntas. No canto superior direito, selecione **nova experiência de p uma**.

    ![P Power BI novo uma experiência](media/power-bi-tutorial-q-and-a/power-bi-qna-new-experience.png)

1. Mesmo antes de começar a digitar, a P e R exibe uma nova tela com sugestões para ajudá-lo a formar sua pergunta. Você vê a frases e perguntas completas que contém os nomes das tabelas de conjuntos de dados subjacentes e pode até mesmo ver perguntas completas listadas se o proprietário do conjunto de dados criou [perguntas em destaque](service-q-and-a-create-featured-questions.md),

   ![Sugestão de perguntas p e r](media/power-bi-tutorial-q-and-a/power-bi-qna-suggested-questions.png)

   Você pode escolher uma dessas perguntas como ponto de partida e continuar a refinar a pergunta para encontrar uma resposta específica. Ou use um nome de tabela para ajudá-lo uma nova pergunta do word.

2. Selecione na lista de perguntas, ou comece a digitar sua própria pergunta e selecione entre as sugestões de lista suspensa.

   ![Selecione uma pergunta na lista](media/power-bi-tutorial-q-and-a/power-bi-qna-select-a-question-how-many-stores.png)

3. Conforme você digita uma pergunta, perguntas e respostas escolhe a melhor visualização para exibir sua resposta.

   ![P e r armazena quantos por estado](media/power-bi-tutorial-q-and-a/power-bi-qna-how-many-stores-by-state.png)

4. A visualização muda dinamicamente à medida que você modifica a pergunta.

   ![P e r armazena quantos por estado como gráfico de barras](media/power-bi-tutorial-q-and-a/power-bi-qna-stores-by-state-bar-chart.png)

1. Quando você digita uma pergunta, o Power BI procura a melhor resposta em qualquer conjunto de dados que tenha um bloco nesse dashboard.  Se todos os blocos forem do *conjuntodedadosA*, sua resposta será proveniente do *conjuntodedadosA*.  Se houver blocos do *Conjuntodedadosa* e *Conjuntodedadosb*, p e r procurará a melhor resposta nesses 2 conjuntos de dados.

   > [!TIP]
   > Por isso, tenha cuidado. Se você tiver apenas um bloco do *datasetA* e removê-lo do dashboard, a P e R deixará de ter acesso ao *datasetA*.
   >

5. Quando estiver satisfeito com o resultado, fixe a visualização em um dashboard, selecionando o ícone de pino no canto superior direito. Se o dashboard tiver sido compartilhado com você ou for parte de um aplicativo, não será possível fixar.

   ![P e r fixar visual](media/power-bi-tutorial-q-and-a/power-bi-qna-pin-visual.png)

## <a name="part-2-use-qa-in-a-report-in-power-bi-service-or-power-bi-desktop"></a>Parte 2: Usar P e R em um relatório no serviço do Power BI ou no Power BI Desktop

Use P e R para explorar o conjunto de dados e adicionar visualizações ao relatório e aos dashboards. Um relatório se baseia em um único conjunto de dados e pode ser totalmente em branco ou conter páginas repletas de visualizações. Mas apenas o fato de um relatório estar em branco não significa que não exista nenhum dado para você explorar – o conjunto de dados é vinculado ao relatório e está esperando que você explore e crie visualizações.  Para ver qual conjunto de dados está sendo usado para criar um relatório, abra o relatório no modo de exibição de Leitura do serviço do Power BI e selecione **Exibir relacionados** na barra de menus.

![Exibir conjuntos de dados relacionados](media/power-bi-tutorial-q-and-a/power-bi-view-related.png)

Para usar p e r em relatórios, você deve ter permissões de edição para o relatório e conjunto de dados subjacente. No [p e r para os consumidores](consumer/end-user-q-and-a.md) artigo, nos referimos a isso como um *criador* cenário. Se em vez disso você estiver *consumindo* um relatório que foi compartilhado com você, p e r não está disponível.

1. Abra um relatório no modo de edição (serviço do Power BI) ou modo de exibição de relatório (Power BI Desktop) e selecione **faça uma pergunta** na barra de menus.

    **Power BI Desktop**    
    ![Selecione uma pergunta no Power BI Desktop](media/power-bi-tutorial-q-and-a/power-bi-desktop-question.png)

    **Serviço**    
    ![Selecione fazer uma pergunta no serviço do Power BI](media/power-bi-tutorial-q-and-a/power-bi-service.png)

2. Uma caixa de perguntas de P e R é exibida na tela do relatório. No exemplo a seguir, a caixa de perguntas é exibida na parte superior de outra visualização. Isso é bom, mas pode ser melhor adicionar uma página em branco ao relatório antes de fazer uma pergunta.

    ![Caixa de perguntas de p e r](media/power-bi-tutorial-q-and-a/power-bi-ask-question.png)

3. Coloque o cursor na caixa de pergunta. Conforme você digita, a P e R exibe sugestões para ajudá-lo a formular a sua pergunta.

   ![Digite em uma caixa de pergunta de p](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-suggestions.png)

4. Ao digitar uma pergunta, o P e R do Power BI escolhe a melhor [visualização ](visuals/power-bi-visualization-types-for-reports-and-q-and-a.md)para exibir sua resposta; e a visualização muda dinamicamente à medida que você modifica a pergunta.

   ![P e r cria uma visualização](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-visual.png)

5. Quando você tiver a visualização que desejar, selecione ENTER. Para salvar a visualização com o relatório, selecione **Arquivo > Salvar**.

6. Interaja com a nova visualização. Não importa como você criou a visualização – a mesma interatividade, formatação e recursos estão disponíveis.

   ![Interagir com a visualização](media/power-bi-tutorial-q-and-a/power-bi-q-and-a-ellipses.png)

   Se você criou a visualização no serviço do Power BI, você pode até mesmo [fixá-la a um dashboard](service-dashboard-pin-tile-from-q-and-a.md).

## <a name="tell-qa-which-visualization-to-use"></a>Informe à P e R qual visualização deve ser usada
Com P e R, você pode não apenas solicitar que seus dados falem por si próprios, mas também dizer ao Power BI como você deseja que a resposta seja exibida. Basta adicionar "como um <visualization type>" ao final da sua pergunta.  Por exemplo, "mostrar o volume de inventário pela fábrica como um mapa" e "mostrar inventário total como um cartão de crédito".  Experimente.

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
- Se você tiver conectado a um conjunto de dados usando uma conexão dinâmica ou um gateway, será necessário [habilitar a P e R para esse conjunto de dados](service-q-and-a-direct-query.md).

- Você abriu um relatório e não viu a opção de P e R. Se você está usando o serviço do Power BI, certifique-se de abrir o relatório no modo de exibição de Edição. Se você não conseguir abrir a exibição de edição, isso significa que você não tem permissões de edição para esse relatório e você pode usar p e r com esse relatório específico.

## <a name="next-steps"></a>Próximas etapas

- [P e r para consumidores](consumer/end-user-q-and-a.md)   
- [Dicas para fazer perguntas nas Perguntas e respostas](consumer/end-user-q-and-a-tips.md)   
- [Preparar uma pasta de trabalho para Perguntas e respostas](service-prepare-data-for-q-and-a.md)  
- [Preparar um conjunto de dados locais para p e r](service-q-and-a-direct-query.md)   
- [Fixar um bloco ao dashboard de Perguntas e respostas](service-dashboard-pin-tile-from-q-and-a.md)
