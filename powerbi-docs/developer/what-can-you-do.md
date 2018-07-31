---
title: O que os desenvolvedores podem fazer com o Power BI?
description: O Power BI oferece uma ampla variedade de opções para desenvolvedores. Isso vai desde a inserção até elementos visuais personalizados e conjuntos de dados de streaming.
author: markingmyname
ms.author: maghan
ms.date: 05/25/2018
ms.topic: overview
ms.service: powerbi
ms.component: powerbi-developer
ms.custom: mvc
manager: kfile
ms.openlocfilehash: 07fb8d365a6fe4a874b057a71a90a99fc8a9e5fa
ms.sourcegitcommit: 80d6b45eb84243e801b60b9038b9bff77c30d5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34564686"
---
# <a name="what-can-developers-do-with-power-bi"></a>O que os desenvolvedores podem fazer com o Power BI?

Os desenvolvedores têm diferentes opções ao tentar incluir o conteúdo do Power BI em aplicativos. Essas opções incluem **inserção com o Power BI**, **visuais personalizados** e **envio de dados por push para o Power BI**.

## <a name="embedding"></a>Inserção
O serviço do Power BI (SaaS) e o serviço do Power BI Embedded no Azure (PaaS) têm APIs para inserir seus painéis e seus relatórios. Isso significa que você terá um conjunto consistente de recursos e o acesso aos recursos mais recentes do Power BI, tais como painéis, gateways e espaços de trabalho de aplicativo, ao inserir seu conteúdo.

É possível acessar a [Ferramenta de experiência de integração](https://aka.ms/embedsetup) para começar rapidamente e baixar um aplicativo de exemplo.

Escolha a solução certa para você:
* A [inserção para clientes](embedding.md#embedding-for-your-customers) fornece a capacidade de inserir os dashboards e relatórios para usuários que não têm uma conta do Power BI. Execute a solução [Inserir para clientes](https://aka.ms/embedsetup/AppOwnsData).
* A [inserção para a organização](embedding.md#embedding-for-your-organization) permite que você estenda o serviço do Power BI. Execute a solução [Inserir para a organização](https://aka.ms/embedsetup/UserOwnsData).

![Exemplo de PBIE](media/what-can-you-do/what-can-you-do-02.png)

## <a name="develop-custom-visuals"></a>Desenvolver visuais personalizados
Os elementos visuais personalizados permitem que você crie seus próprios elementos visuais para uso em relatórios do Power BI. Os visuais personalizados são gravados em TypeScript, que é um superconjunto de JavaScript. O TypeScript oferece suporte a alguns recursos avançados e acesso antecipado à funcionalidade do ES6/ES7. A aplicação de estilo do visual é realizada usando CSS (folhas de estilos em cascata). Para facilitar, usamos o pré-compilador Less que é compatível com alguns recursos avançados, como aninhamento, variáveis, condições, loops, etc. Se não quiser usar esses recursos, escreva apenas o CSS simples no arquivo LESS.

![Exemplo de CV](media/what-can-you-do/powerbi-custom-visual-store.png)

## <a name="push-data-into-power-bi"></a>Enviar dados por push ao Power BI
Você pode usar a API do Power BI para enviar dados por push a um conjunto de dados. Isso permite que você adicione uma linha a uma tabela dentro de um conjunto de dados. Assim, os novos dados podem ser mostrados em blocos em um dashboard e dentro de elementos visuais no seu relatório.

![Exemplo de envio de dados por push](media/what-can-you-do/powerbi-push-data.png)

## <a name="next-steps"></a>Próximas etapas
[Inserindo com o Power BI](embedding.md)  
[Publicar visuais personalizados na Office Store](office-store.md)  
[Enviar dados por push a um dashboard](walkthrough-push-data.md)
