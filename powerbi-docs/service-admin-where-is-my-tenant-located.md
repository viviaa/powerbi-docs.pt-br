---
title: Onde está localizado meu locatário do Power BI?
description: Saiba onde está localizado seu locatário do Power BI e como essa localização é selecionada. É importante entender isso, já que é algo que pode afetar suas interações com o serviço.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 10/31/2018
ms.author: mblythe
LocalizationGroup: Administration
ms.openlocfilehash: b396b55304e468143fe28fb5ed46ed290bfb3812
ms.sourcegitcommit: 0611860a896e636ceeb6e30ce85243bfd8e7b61d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2018
ms.locfileid: "50909515"
---
# <a name="where-is-my-power-bi-tenant-located"></a>Onde está localizado meu locatário do Power BI?

<iframe width="560" height="315" src="https://www.youtube.com/embed/0fOxaHJPvdM?showinfo=0" frameborder="0" allowfullscreen></iframe>

Saiba onde está localizado seu locatário do Power BI e como essa localização é selecionada. É importante entender o local, pois isso pode afetar suas interações com o serviço.

## <a name="how-to-determine-where-your-power-bi-tenant-is-located"></a>Como determinar onde se encontra o seu locatário do Power BI

Para localizar em qual região seu locatário está, execute estas etapas.

1. No serviço do Power BI, no menu superior, selecione a Ajuda (**?**), em seguida, **Sobre o Power BI**.

1. Procure o valor ao lado de **Seus dados são armazenados em**. Essa é a região onde seu locatário está localizado.

    ![Região de dados](media/service-admin-where-is-my-tenant-located/power-bi-data-region.png)

## <a name="how-the-data-region-is-selected"></a>Como a região de dados é selecionada

A região de dados tem base no país selecionado quando você cria o locatário. Isso se aplica à inscrição no Office 365 além do Power BI, pois essas informações são compartilhadas. Se esse for um novo locatário, selecione o país apropriado na lista quando você se inscrever.

![Seleção de país](media/service-admin-where-is-my-tenant-located/sign-up-country-selection.png)

O Power BI seleciona uma região de dados mais próxima desta seleção, o que determina onde os dados são armazenados para o seu locatário.

> [!IMPORTANT]
> Você não pode alterar essa seleção após a criação do locatário.

Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

