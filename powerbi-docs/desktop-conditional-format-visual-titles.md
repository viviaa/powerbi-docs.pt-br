---
title: Com base em expressão títulos no Power BI Desktop
description: Criar títulos dinâmicos no Power BI Desktop que alteram com base em expressões programáticas, usando a formatação condicional de programação
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: reference
ms.date: 04/10/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b90ef66d2c118a70f1b18ed4fe302ce1db23e45c
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64769747"
---
# <a name="expression-based-titles-in-power-bi-desktop"></a>Com base em expressão títulos no Power BI Desktop

Você pode criar dinâmico, personalizado títulos de seus visuais do Power BI. Criando expressões DAX (Data Analysis) com base em campos, variáveis ou outros elementos de programação, os títulos de seus elementos visuais podem ajustar automaticamente conforme necessário. Essas alterações são com base em filtros, as seleções, ou outras interações do usuário e configurações.

![Opção de formatação condicional de captura de tela do Power BI Desktop](media/desktop-conditional-formatting-visual-titles/expression-based-title-01.png)

Criação de títulos dinâmicos, às vezes chamado de *baseadas em expressão títulos*, é simples. 

## <a name="create-a-field-for-your-title"></a>Criar um campo do título

A primeira etapa na criação de um título com base em expressão é criar um campo em seu modelo a ser usado para o título. 

Há inúmeras maneiras criativas para ter o título do seu visual refletir o que você deseja que ele faça, ou o que você deseja express. Vamos dar uma olhada em alguns exemplos.

Você pode criar uma expressão que alterações de acordo com o contexto de filtro que recebe de visual para o nome da marca do produto. A imagem a seguir mostra a fórmula DAX para esse campo.

![Fórmula de captura de tela de DAX](media/desktop-conditional-formatting-visual-titles/expression-based-title-02.png)

Outro exemplo é usando um título dinâmico que as alterações com base no idioma ou cultura do usuário. Você pode criar títulos específicos do idioma em uma medida DAX usando o `USERCULTURE()` função. Essa função retorna o código de cultura para o usuário, com base em suas configurações do navegador ou sistema operacional. Você pode usar a seguinte instrução de comutador DAX para selecionar o valor convertido correto. 

```
SWITCH (
  USERCULTURE(),
  "de-DE", “Umsatz nach Produkt”,
  "fr-FR", “Ventes par produit”,
  “Sales by product”
)
```

Ou você pode recuperar a cadeia de caracteres de uma tabela de pesquisa que contém todas as traduções. Você pode colocar essa tabela em seu modelo. 

Esses são apenas alguns exemplos que você pode usar para criar títulos dinâmicos com base em expressão, os visuais no Power BI Desktop. O que você pode fazer com seus títulos são limitados apenas pelo sua imaginação e seu modelo.


## <a name="select-your-field-for-your-title"></a>Selecione o campo do título

Depois de criar a expressão DAX para o campo que você cria no seu modelo, você precisa aplicá-la ao título do seu visual.

Para selecionar o campo e aplicá-lo, vá para o **visualizações** painel. No **formato** área, selecione **título** para mostrar as opções de título para o visual. 

Quando você clique com botão direito **texto do título**, é exibido um menu de contexto que permite que você selecione ***fx* formatação condicional**. Quando você seleciona esse item de menu, um **texto do título** caixa de diálogo é exibida. 

![Caixa de diálogo de texto de captura de tela do título](media/desktop-conditional-formatting-visual-titles/expression-based-title-02b.png)

A partir dessa janela, você pode selecionar o campo que você criou para usar para o título.

## <a name="limitations-and-considerations"></a>Limitações e considerações

Há algumas limitações na implementação atual de baseadas em expressão títulos de visuais:

* Atualmente não tem suporte a formatação com base em expressão no visual os influenciadores principais, os visuais do R ou Python visuais.
* O campo que você criar para o título deve ser um tipo de dados de cadeia de caracteres. Atualmente, não há suporte para medidas que retornem números ou data/hora (ou qualquer outro tipo de dados).

## <a name="next-steps"></a>Próximas etapas

Este artigo descreveu como criar expressões DAX que transformam os títulos dos visuais em campos dinâmicos que podem ser alterados conforme os usuários interagem com seus relatórios. Você pode encontrar os artigos a seguir úteis também.

* [Usar o detalhamento do relatório no Power BI Desktop](desktop-cross-report-drill-through.md)
* [Usar o detalhamento no Power BI Desktop](desktop-drillthrough.md)