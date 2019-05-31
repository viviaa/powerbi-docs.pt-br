---
title: Capturar informações adicionais de diagnóstico
description: Estas instruções fornecem duas opções possíveis para coletar manualmente as informações adicionais de diagnóstico do cliente Web Power BI.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/25/2019
ms.author: mblythe
ms.custom: seodec18
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 710fb4cdcf9efb051434966d47c2eaced17ac9ba
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65100193"
---
# <a name="capture-additional-diagnostic-information-for-power-bi"></a>Capturar informações de diagnóstico adicionais para o Power BI

Este artigo fornece instruções para coletar manualmente as informações adicionais de diagnóstico do cliente web do Power BI.

1. Navegue até [Power BI](https://app.powerbi.com) com Microsoft Edge ou Internet Explorer.

1. Pressione **F12** para abrir as ferramentas de desenvolvedor do Microsoft Edge.

   ![Guia de elementos de ferramentas de captura de tela de desenvolvedor de borda da Microsoft.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-developer-tools.png)

1. Selecione a guia **Rede**. Ele listará o tráfego que já foi capturado.

   ![Guia de rede de ferramentas de captura de tela de desenvolvedor de borda da Microsoft.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab.png)

    Você pode:

    * Navegar na janela e reproduzir qualquer problema que você pode se deparar com.

    * Ocultar e mostrar o desenvolvedor ferramentas janela a qualquer momento durante a sessão pressionando F12.

1. Para interromper a sessão de criação de perfil, você pode selecionar o quadrado vermelho sobre o **rede** área de ferramentas da guia do desenvolvedor.

   ![Guia de rede de ferramentas de captura de tela de desenvolvedor de borda da Microsoft com uma chamada fora do botão Parar.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-stop.png)

1. Selecione o ícone de disquete para exportar os dados como um arquivo do arquivo morto HTTP (HAR).

   ![Guia de rede de ferramentas de captura de tela de desenvolvedor de borda da Microsoft com um balão do ícone de disquete.](media/service-admin-capturing-additional-diagnostic-information-for-power-bi/edge-network-tab-save.png)

1. Forneça um nome de arquivo e salve o arquivo HAR.

    O arquivo HAR contém todas as informações sobre solicitações de rede entre a janela do navegador e incluindo o Power BI:

    * As IDs de atividade para cada solicitação.

    * O carimbo de hora preciso para cada solicitação.

    * Qualquer informação de erro é retornado ao cliente.

    Este rastreamento também conterá os dados usados para preencher os elementos visuais mostrados na tela.

1. Você pode fornecer o arquivo HAR para dar suporte à análise.

Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)
