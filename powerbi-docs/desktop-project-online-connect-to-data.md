---
title: 'Project Online: conectar-se aos dados por meio do Power BI Desktop'
description: 'Project Online: conectar-se aos dados por meio do Power BI Desktop'
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/08/2019
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: b0dc84d7b2d8da0df8a9e61a43f35898d197c188
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65513710"
---
# <a name="project-online-connect-to-data-through-power-bi-desktop"></a>Project Online: conectar-se aos dados por meio do Power BI Desktop
Você pode conectar-se a dados no Project Online por meio do Power BI Desktop.

## <a name="step-1-download-power-bi-desktop"></a>Etapa 1: Baixe o Power BI Desktop
1. [Baixar o Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521662) e, em seguida, execute o instalador para obter o **Power BI Desktop** em seu computador.

## <a name="step-2-connect-to-project-online-with-odata"></a>Etapa 2: Conectar-se ao Project Online com o OData
1. Abra o **Power BI Desktop**.
2. Na tela de *Boas-vindas*, selecione **Obter dados**.
3. Escolha **feed OData** e selecione **Conectar**.
4. Insira o endereço para o feed OData na caixa URL e, em seguida, clique em OK.
   
   Se o endereço do seu site do Project Web App semelhante *https://\<tenantname\>.sharepoint.com/sites/pwa*, em seguida, o endereço que você vai inserir para o OData Feed é *https://\<tenantname\>.sharepoint.com/sites/pwa/\_api/Projectdata*.
   
   Para nosso exemplo, estamos usando https://contoso.sharepoint.com/sites/pwa/default.aspx
5. O Power BI Desktop solicitará que você se autentique com sua conta do Office 365. Selecione Conta organizacional e, em seguida, insira suas credenciais.
   
   ![](media/desktop-project-online-connect-to-data/image.png)

A conta usada para conectar-se ao OData feed deve ter pelo menos acessar o Visualizador de portfólio para o site do Project Web App. 

Aqui, você pode escolher a quais tabelas deseja se conectar e criar uma consulta.  Quer uma ideia de como começar?  A seguinte postagem de blog mostra como criar um gráfico de seus dados do Project Online de progresso.  A postagem de blog refere-se ao uso do Power Query para se conectar ao Project Online, mas isso se aplica também ao Power BI Desktop.

[Criando gráficos de progresso para o projeto usando o Power Pivot e Power Query](http://blogs.office.com/2014/03/24/creating-burndown-charts-for-project-using-power-pivot-and-power-query/)

