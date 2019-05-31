---
title: 'Serviço de terceiros: Conector do Facebook para Power BI Desktop'
description: 'Serviço de terceiros: Conector do Facebook para Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 6b02717c49a1207dfec39ebb1529e7e9b222fa62
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65512873"
---
# <a name="facebook-connector-for-power-bi-desktop"></a>Conector do Facebook para Power BI Desktop
O conector do Facebook no **Power BI Desktop** depende da API do Graph do Facebook. Como tal, recursos e disponibilidade podem variar ao longo do tempo.

Você pode ver um [tutorial sobre o Conector do Facebook para o Power BI Desktop](desktop-tutorial-facebook-analytics.md).

Facebook expirou a v1.0 de sua API do Graph em 30 de abril de 2015. O Power BI usa a Graph API nos bastidores para o conector do Facebook, permitindo que você se conecte aos seus dados e os analise.

Consultas que foram criadas antes de 30 de abril de 2015 podem não funcionar ou retornar menos dados. Após 30 de abril de 2015, Power BI usa a v2.8 em todas as chamadas à API do Facebook. Se a consulta foi criada antes de 30 de abril de 2015 e você não a usou, provavelmente precisará autenticar novamente para aprovar o novo conjunto de permissões que solicitaremos.

Podemos tentar lançar atualizações de acordo com as alterações, o API pode ser alterado de forma que afeta os resultados das consultas que gerarmos. Em alguns casos, determinadas consultas podem não ter mais suporte. Devido a essa dependência não podemos garantir os resultados de suas consultas ao usar esse conector.

Mais detalhes sobre a alteração na API do Facebook estão disponíveis [aqui](https://developers.facebook.com/docs/apps/changelog#v2_0).

