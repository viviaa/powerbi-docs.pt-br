---
title: 'Tutorial: Criar um modelo de aprendizado de máquina no Power BI (visualização)'
description: Neste tutorial, você cria um modelo de aprendizado de máquina no Power BI.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 03/29/2019
ms.author: davidi
LocalizationGroup: Connect to services
ms.openlocfilehash: 611d6f6c923e6cb68af94840c4266a0b6dee7651
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61406165"
---
# <a name="tutorial-build-a-machine-learning-model-in-power-bi-preview"></a>Tutorial: Criar um modelo de aprendizado de máquina no Power BI (visualização)

Este artigo de tutorial, você usa **automatizada de aprendizado de máquina** para criar e aplicar um modelo de previsão binária no Power BI. O tutorial inclui orientações para a criação de um fluxo de dados do Power BI e usar as entidades definidas no fluxo de dados para treinar e validar um modelo de machine learning diretamente no Power BI. Em seguida, usamos esse modelo de pontuação para gerar previsões.

Primeiro, você criará um modelo, para prever a intenção de compra de compradores online com base em um conjunto de seus atributos de sessão online de aprendizado de máquina de previsão binária. Um conjunto de dados do aprendizado de máquina do parâmetro de comparação é usado para este exercício. Depois que um modelo é treinado, o Power BI gerará automaticamente um relatório de validação, explicando os resultados do modelo. Você pode, em seguida, examine o relatório de validação e aplicar o modelo para seus dados para pontuação.

Neste tutorial consiste as seguintes etapas:

> [!div class="checklist"]
> * Criar um fluxo de dados com os dados de entrada
> * Crie e treine um modelo de aprendizado de máquina
> * Examine o relatório de validação de modelo
> * Aplicar o modelo a uma entidade de fluxo de dados
> * Usando a saída de pontuação do modelo em um relatório do Power BI

## <a name="create-a-dataflow-with-the-input-data"></a>Criar um fluxo de dados com os dados de entrada

A primeira parte deste tutorial é criar um fluxo de dados com dados de entrada. Esse processo demora algumas etapas, conforme mostrado nas seções a seguir, começando com a obtenção de dados.

### <a name="get-data"></a>Obter dados

A primeira etapa na criação de um fluxo de dados é ter suas fontes de dados prontos. Em nosso caso, usamos um conjunto de dados de aprendizado de máquina de um conjunto de sessões online, alguns dos quais culminou em uma compra. O conjunto de dados contém um conjunto de atributos sobre essas sessões, que usaremos para treinar nosso modelo.

Você pode baixar o conjunto de dados do site do UC Irvine.  Também temos isso está disponível, para fins deste tutorial, do seguinte link: [online_shoppers_intention.csv](https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv).

### <a name="create-the-entities"></a>Criar as entidades

Para criar as entidades em seu fluxo de dados, entre no serviço do Power BI e navegue até um workspace na capacidade dedicada que tenha a versão prévia de IA habilitada.

Se você ainda não tiver um espaço de trabalho, você pode criar uma selecionando **espaços de trabalho** no menu de navegação à esquerda no serviço do Power BI e selecione **criar espaço de trabalho do aplicativo** na parte inferior do painel que é exibida. Isso abre um painel à direita para inserir os detalhes do espaço de trabalho. Insira um nome de espaço de trabalho e selecione **avançado**. Confirme que o espaço de trabalho usa a capacidade dedicada usando o botão de opção e que é atribuído a uma instância de uma capacidade dedicada que tem a versão prévia da IA ativada. Depois, selecione **Salvar**.

![Criar um workspace](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-01.png)

Depois que o espaço de trabalho é criado, você pode selecionar **Skip** no canto inferior direito da tela de boas-vinda, conforme mostrado na imagem a seguir.

![Ignore se você tiver um espaço de trabalho](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-02.png)

Selecione o **fluxos de dados (visualização)** guia. Selecione o **Create** botão na parte superior direita do espaço de trabalho e, em seguida, selecione **fluxo de dados**.

![Criar um fluxo de dados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-03.png)

Selecione **Adicionar novas entidades**. Isso inicia um **Power Query** editor no navegador.

![Adicionar nova entidade](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-04.png)

Selecione **arquivo de texto/CSV** como uma fonte de dados, mostrado na imagem a seguir.

![Arquivo de texto/CSF selecionado](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-05.png)

No **conectar-se a uma fonte de dados** que aparece em seguida, cole o link a seguir para o *online_shoppers_intention.csv* para o **URL ou caminho do arquivo** caixa e, em seguida, selecione  **Próxima**.

`https://raw.githubusercontent.com/santoshc1/PowerBI-AI-samples/master/Tutorial_AutomatedML/online_shoppers_intention.csv`

![Caminho do arquivo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-06.png)

O Power Query Editor mostra uma visualização dos dados do arquivo CSV. Selecione **transformar tabela** na faixa de opções de comando e, em seguida, selecione **usar primeira linha como cabeçalhos** no menu que aparece. Isso adiciona o _promovidos a cabeçalhos_ etapa de consulta para o **as etapas aplicadas** seção à direita da tela. Você pode renomear a consulta para um nome mais amigável, alterando o valor na **nome** caixa encontrado no painel direito. Por exemplo, você pode alterar o nome da consulta _visitante Online_.

![Altere para um nome amigável](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-07.png)

Alguns dos tipos de dados de atributo neste conjunto de dados são _numéricos_ ou _booliano_, embora elas poderão ser interpretadas como cadeias de caracteres por **Power Query**. Selecione o ícone de tipo de atributo na parte superior de cada cabeçalho de coluna para alterar as colunas listadas abaixo para os seguintes tipos:

* **Número decimal:** Administrative_Duration; Informational_Duration; ProductRelated_Duration; BounceRates; ExitRates; PageValues; SpecialDay
* **True/False:** Fim de semana; Receita

![Alterar tipo de dados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-08.png)

O **previsão binária** modelo que Treinaremos requer um campo booliano como um rótulo que identifica os resultados da últimas observações. Neste conjunto de dados, o _receita_ atributo indica a compra, e esse atributo já está disponível como um valor booliano. Portanto, não precisamos adicionar uma coluna calculada para o rótulo. Outros conjuntos de dados, talvez você precise transformar atributos do rótulo existente em uma coluna booleana.

Selecione o **feito** botão para fechar o Editor do Power Query. Isso mostra a lista de entidades com o _visitantes Online_ dados que adicionamos. Selecione **salve** no canto superior direito, forneça um nome para o fluxo de dados e, em seguida, selecione **salvar** na caixa de diálogo, conforme mostrado na imagem a seguir.

![Salvar o fluxo de dados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-09.png)

### <a name="refresh-the-dataflow"></a>Atualizar fluxo de dados

Salvando os resultados do fluxo de dados em uma notificação que está sendo exibida, informando que seu fluxo de dados foi salva. Selecione **atualizar agora** para incluir os dados da origem no fluxo de dados.

![Atualizar agora](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-10.png)

Selecione **Fechar** no canto superior direito e aguarde até que a atualização do fluxo de dados termine.

Você também pode atualizar seu fluxo de dados usando o **ações** comandos. O fluxo de dados mostra o carimbo de hora quando a atualização foi concluída.

![Carimbo de hora de atualização](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-11.png)

## <a name="create-and-train-a-machine-learning-model"></a>Crie e treine um modelo de aprendizado de máquina

Selecione o fluxo de dados após a atualização ter sido concluída. Para adicionar um modelo de aprendizado de máquina, selecione a **modelo ML aplicar** botão na **ações** para a entidade básica que contém as informações de rótulo e dados de treinamento e, em seguida, selecione **adicionar um modelo de aprendizado de máquina**.

![Adicionar um modelo de machine learning](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-12.png)

A primeira etapa para a criação de nosso modelo de aprendizado de máquina é identificar os dados históricos, incluindo o campo de rótulo que você deseja prever. O modelo será criado pelo aprendizado desses dados.

No caso do conjunto de dados que estamos usando, esse é o **receita** campo. Selecione **receita** como o valor de 'campo de resultado históricos' e selecione **próxima**.

![Selecione os dados históricos](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-13.png)

Em seguida, podemos deve selecionar o tipo de modelo para criar de aprendizado de máquina. Power BI analisa os valores no campo de resultado históricos que você identificou e sugere os tipos de modelos de aprendizado de máquina que podem ser criados para prever esse campo.

Nesse caso, uma vez que estamos estiver prevendo um resultado binário de se um usuário faça uma compra ou não, selecione **previsão binária** para o tipo de modelo e, em seguida, clicar em Avançar.

![Previsão binária selecionado](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-14.png)

Em seguida, o Power BI faz uma verificação preliminar dos dados e sugere as entradas que o modelo poderia usar. Você tem a opção de personalizar os campos de entrada usados para o modelo. Em nosso conjunto de dados estruturado, para selecionar todos os campos, selecione a caixa de seleção ao lado do nome da entidade. Selecione **próxima** para aceitar as entradas.

![Marque a caixa de seleção próxima](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-15.png)

Na etapa final, podemos deve fornecer um nome para o nosso modelo, bem como os rótulos amigáveis para os resultados a ser usado no relatório gerado automaticamente que resumirá os resultados da validação do modelo. Em seguida, temos que nomear o modelo _previsão de intenção de compra_e os rótulos verdadeiros e falsos como _compra_ e _nenhuma compra_. Depois, selecione **Salvar**.

![Salvar o modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-16.png)

Nosso modelo de machine learning agora está pronto para treinamento. Selecione **atualizar agora** para iniciar o treinamento do modelo.

![Atualizar agora](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-17.png)

Iniciar o processo de treinamento por amostragem e normalizar os dados históricos e dividir seu conjunto de dados em duas novas entidades *dados de treinamento de previsão de intenção de compra* e *teste de previsão de intenção de compra Dados*.

Dependendo do tamanho do conjunto de dados, o processo de treinamento pode levar de alguns minutos a algumas horas. Neste ponto, você pode ver o modelo na **modelos de aprendizado de máquina** guia de fluxo de dados. O _pronto_ status indica que o modelo foi enfileirado para treinamento ou está em treinamento.

![Pronto para treinamento](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-18.png)

Embora o modelo seja treinamento, você não conseguirá exibir ou editar o fluxo de dados. Você pode confirmar que o modelo está sendo treinado e validado por meio do status do fluxo de dados. Isso é exibido como uma atualização de dados em andamento na **fluxos de dados** guia do espaço de trabalho.

![No processo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-19.png)

Depois que o treinamento do modelo for concluído, o fluxo de dados exibe um tempo de atualização atualizado. Você pode confirmar que o modelo é treinado, navegando até a **modelos de aprendizado de máquina** guia no fluxo de dados. O modelo que você criou deve mostrar o status como **treinados** e o **última treinado** tempo deve ser atualizado.

![Treinado pela última vez em](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-20.png)

## <a name="review-the-model-validation-report"></a>Examine o relatório de validação de modelo

Para examinar o relatório de validação de modelo, na **modelos de aprendizado de máquina, s** eleger o **Exibir relatório de desempenho e aplicar modelo** botão no **ações** coluna do modelo de . Este relatório descreve como o modelo de aprendizado de máquina é tende a ter.

No **desempenho do modelo** página do relatório, selecione **os influenciadores principais** para exibir as previsões principais para o seu modelo. Você pode selecionar uma das previsões para ver como a distribuição de resultado é associado essa previsão.

![Desempenho do modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-21.png)

Você pode usar o **limite de probabilidade** segmentação na página de desempenho do modelo para examinar sua influência sobre a precisão e a recuperação para o modelo.

![Limite de probabilidade](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-22.png)

As outras páginas do relatório descrevem as métricas de desempenho de estatísticas para o modelo.

O relatório também inclui uma página de detalhes de treinamento que descreve as iterações diferentes que foram executadas, como os recursos foram extraídos de entradas e os hiperparâmetros para o modelo final usado.

## <a name="apply-the-model-to-a-dataflow-entity"></a>Aplicar o modelo a uma entidade de fluxo de dados

Selecione o **aplicar modelo** botão na parte superior do relatório para invocar esse modelo quando o fluxo de dados é atualizado. No **aplicar** caixa de diálogo, você pode especificar a entidade de destino que tem os dados de origem para o qual o modelo deve ser aplicado.

![Aplicar o modelo](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-23.png)

Quando solicitado, você deve **Refresh** o fluxo de dados para visualizar os resultados do seu modelo.

Aplicar o modelo criará uma nova entidade, com o sufixo **enriquecida < model_name >** acrescentado à entidade ao qual você aplicou o modelo. Em nosso caso, aplicar o modelo para o **OnlineShoppers** entidade criará **OnlineShoppers enriquecida com a previsão de intenção de compra**, que inclui a saída prevista do modelo.

Aplicar um modelo de previsão binária adiciona três colunas com os influenciadores principais do registro específicas para a previsão, pontuação de probabilidade e o resultado previsto, cada um prefixado com o nome de coluna especificado.

![Três colunas de resultado](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-24.png)

Devido a um problema conhecido, as colunas de saída pontuada na entidade enriquecida só são acessíveis do Power BI Desktop. Para visualizar esses no serviço, você deve usar uma entidade de visualização especial.

Depois que a atualização de fluxo de dados for concluída, você pode selecionar o **OnlineShoppers enriquecida com a visualização de previsão de intenção de compra** entidade para exibir os resultados.

![Exibir os resultados](media/service-tutorial-build-machine-learning-model/tutorial-build-machine-learning-model-25.png)

## <a name="using-the-scored-output-from-the-model-in-a-power-bi-report"></a>Usando a saída de pontuação do modelo em um relatório do Power BI

Para usar a saída pontuada do modelo de aprendizado de máquina, você pode se conectar ao seu fluxo de dados da área de trabalho do Power BI usando o conector de fluxos de dados. O **OnlineShoppers enriquecida com a previsão de intenção de compra** entidade agora pode ser usada para incorporar as previsões de seu modelo em relatórios do Power BI.

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você criou e aplicado a um modelo de previsão binária no Power BI usando as seguintes etapas:

* Criar um fluxo de dados com os dados de entrada
* Crie e treine um modelo de aprendizado de máquina
* Examine o relatório de validação de modelo
* Aplicar o modelo a uma entidade de fluxo de dados
* Usando a saída de pontuação do modelo em um relatório do Power BI

Para obter mais informações sobre a automação de aprendizado de máquina no Power BI, consulte [automatizada de aprendizado de máquina no Power BI (visualização)](service-machine-learning-automated.md).
