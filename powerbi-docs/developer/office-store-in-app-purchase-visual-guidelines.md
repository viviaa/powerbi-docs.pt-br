---
title: Compra adicional pode ser necessária – Diretrizes de Visuais do Power BI
description: Saiba como você pode publicar seu visual personalizado no AppSource para que outros possam descobrir e usá-lo por meio de uma compra.
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.date: 11/26/2018
ms.openlocfilehash: 4cbd17a08a8cb7c7253f60f29a19341598c9800f
ms.sourcegitcommit: 654fae0af739bd599e029d692f142faeba0a502f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2019
ms.locfileid: "56426529"
---
# <a name="guidelines-for-power-bi-visuals-with-additional-purchases"></a>Diretrizes para visuais do Power BI com compras adicionais

Até recentemente, o **Marketplace (AppSource)** aceitava apenas os visuais gratuitos do Power BI. Essa política está sendo alterada para que os elementos visuais com marca de preço "compra adicional pode ser necessária" também possam ser enviados para o **AppSource**. Compra adicional pode ser necessária; visuais são semelhantes a suplementos de IAP (compra no aplicativo) na Office Store. Os desenvolvedores também podem enviar esses elementos visuais para a certificação após a equipe do **AppSource** aprova-los e depois de verificar se eles estão em conformidade com os requisitos de certificação, conforme descrito no artigo [Visuais personalizados certificados](../power-bi-custom-visuals-certified.md).

> [!Note]
> Para o visual ser certificado, ele não deverá acessar serviços ou recursos externos.

> [!Note]
> Todos os visuais gratuitos devem manter os mesmos recursos gratuitos oferecidos anteriormente. Você pode adicionar recursos pagos avançados opcionais aos recursos gratuitos antigos. Recomendamos o envio dos visuais de IAP com os recursos avançados como novos visuais e a não atualização dos gratuitos antigos.


## <a name="whats-changing-in-the-submission-process"></a>O que está mudando no processo de envio?

Os desenvolvedores carregam seus visuais de IAP para o AppSource por meio do Painel do Vendedor, como eles faziam para visuais gratuitos. Para indicar que o visual enviado tem recursos de IAP, os desenvolvedores devem escrever nas notas do painel do vendedor: "Visual com compra no aplicativo." Além disso, os desenvolvedores precisam fornecer um token ou chave de licença para que a equipe de validação poder validar os recursos de IAP. Depois que o visual tiver sido validado e aprovado, a listagem do AppSource para os visuais do IAP diz "Compra adicional pode ser necessária"' nas opções de preços.

## <a name="what-is-a-power-bi-visual-with-iap-features"></a>O que é um visual do Power BI com recursos de IAP?

Um visual do IAP é um visual gratuito e oferece recursos gratuitos, mas também tem recursos adicionais avançados cuja operação exija encargos adicionais. Os desenvolvedores devem notificar os usuários na descrição do visual quais recursos exigem compras adicionais para operar. Atualmente, a Microsoft não fornece APIs (interfaces de programação de aplicativo) nativas para dar suporte à compra em suplementos e aplicativos. Os desenvolvedores podem usar qualquer sistema de pagamento de terceiros para essas compras. Consulte a [política](https://docs.microsoft.com/office/dev/store/validation-policies#2-apps-or-add-ins-can-display-certain-ads) da nossa loja.

> [!NOTE]
> As marcas d'água não são permitidas nos recursos gratuitos. Os desenvolvedores poderão exibir uma janela pop-up ou a marca-d'água se os recursos pagos avançados forem usados sem uma licença válida.  

## <a name="logo-guidelines"></a>Diretrizes de logotipo

Esta seção descreve as especificações para adicionar logos e logotipos em elementos visuais.

> [!NOTE]
> Logotipos são permitidos apenas no modo de edição. Logotipos não podem ser exibidos no modo de exibição.

![definições](media/office-store-in-app-purchase-visual-guidelines/definitions.png)

![itens-a-manter](media/office-store-in-app-purchase-visual-guidelines/things-to-keep-in-mind.png)

![itens-a](media/office-store-in-app-purchase-visual-guidelines/things-to-avoid.png)

![tamanho-e-formato ](media/office-store-in-app-purchase-visual-guidelines/size-and-format.png)

![margens-e](media/office-store-in-app-purchase-visual-guidelines/margins-and-sizes.png)

![modo-de-edição](media/office-store-in-app-purchase-visual-guidelines/logos-in-edit-mode.png)

## <a name="best-practices"></a>Práticas recomendadas

### <a name="visual-landing-page"></a>Página de aterrissagem de elementos visuais

Use a página de aterrissagem para esclarecer aos usuários como eles podem usar seu visual e em que local comprar a licença. Não inclua vídeos disparados automaticamente. Apenas adicione material que ajude a melhorar a experiência do usuário, como informações ou links sobre detalhes de compra de licença e como usar os recursos de IAP.

### <a name="license-key-and-token"></a>Token e a chave de licença

Para conveniência do usuário, adicione campos relacionados de chave de licença ou token na parte superior do painel de formato para que eles estejam melhor localizados para os usuários.

## <a name="faq"></a>PERGUNTAS FREQUENTES

Para saber mais e solucionar suas dúvidas, acesse [Frequently asked questions about visuals with additional purchases](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-faq#visuals-with-additional-purchases) (Perguntas frequentes sobre os visuais com compras adicionais).

## <a name="next-steps"></a>Próximas etapas

Saiba como você pode publicar seu visual personalizado no [AppSource](office-store.md) para que outros possam descobrir e usá-lo.
