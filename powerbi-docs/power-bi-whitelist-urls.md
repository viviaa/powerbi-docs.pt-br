---
title: URLs do Power BI
description: Os pontos de extremidade podem ser acessíveis para clientes que usam o Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 08/13/2018
ms.openlocfilehash: 8e29fa0c9471bb865619102247f38776208c3d87
ms.sourcegitcommit: 8990028a348b642ba5c96f001fe3a4280f0166ee
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40101114"
---
# <a name="power-bi-urls"></a>URLs do Power BI

**O serviço online do Power BI**, também conhecido como aplicativo SaaS (Software como serviço) do Power BI, requer conectividade com a Internet. Os pontos de extremidade abaixo devem ser acessíveis para clientes que usam o serviço online do Power BI.

Para usar o serviço online do Power BI, é necessário ter acesso para se conectar aos pontos de extremidade marcados como **necessários** nas tabelas abaixo e quaisquer pontos de extremidade marcados como **necessários** nos sites vinculados. Se o link para um site externo se referir a uma seção específica, será necessário apenas analisar os pontos de extremidade nessa seção.

Os pontos de extremidade marcados como **opcionais** também podem ser adicionados à **lista de permissões** para uma funcionalidade específica funcionar.

O serviço online do Power BI requer apenas que a porta TCP 443 seja aberta para os pontos de extremidade listados.

Caracteres curinga (*) representam todos os níveis sob o domínio raiz, e usaremos N/D quando as informações não estiverem disponíveis. A coluna **Destino(s)** é uma lista com domínios/FQDN e links para sites externos, que contêm mais informações sobre o ponto de extremidade.

>[!Important]
>As informações nas tabelas abaixo não representam a **nuvem do Governo dos EUA**, **a nuvem da Alemanha** e a **nuvem da China**.

## <a name="authentication"></a>Autenticação

O Power BI depende dos pontos de extremidade necessários nas seções de identidade e autenticação do Office 365. Para usar o Power BI, conecte-se aos pontos de extremidade no site vinculado abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obrigatório:** autenticação e identidade | Consulte a [seção de autenticação e identidade do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_identity) no site da lista de permissões do Office 365 | N/A |

## <a name="general-site-usage"></a>Uso geral do site

Para o uso geral do Power BI, conecte-se aos pontos de extremidade na tabela e nos sites vinculados abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obrigatório:** APIs de back-end | *.analysis.windows.net | TCP 443 |
| 2 | **Obrigatório:** integração do Office 365 | Consulte o [portal e a seção compartilhada do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) no site da lista de permissões do Office 365 | N/A |
| 3 | **Obrigatório:** Portal | app.powerbi.com | TCP 443 |
| 4 | **Obrigatório:** telemetria de serviço | dc.services.visualstudio.com | TCP 443 |
| 5 | **Opcional:** mensagens informativas | dynmsg.modpim.com | TCP 443 |
| 6 | **Opcional:** pesquisas NPS | nps.onyx.azure.net | TCP 443 |

## <a name="administration"></a>Administração

Para executar funções administrativas dentro do Power BI, conecte-se aos pontos de extremidade nos sites vinculados abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obrigatório:** para gerenciar usuários e exibir logs de auditoria | Consulte o [portal e a seção compartilhada do Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_portal-identity) no site da lista de permissões do Office 365 | N/A |

## <a name="get-data"></a>Obter Dados

Para conseguir obter dados de fontes de dados específicas como o OneDrive, conecte-se aos pontos de extremidade na tabela abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obrigatório:** AppSource (aplicativos internos ou externos no Power BI) | appsource.microsoft.com | TCP 443 |
| 2 | **Opcional:** importar arquivos do OneDrive pessoal | Consulte o site [URLs e portas necessárias para o OneDrive](https://support.office.com/en-ie/article/required-urls-and-ports-for-onedrive-ce15d2cc-52ef-42cd-b738-d9c6f9b03f3a) | N/A |
| 3 | **Opcional:** vídeo de tutorial do Power BI em 60 segundos | *.doubleclick.net </br> *.ggpht.com </br> *.google.com </br> *.googlevideo.com </br> *.youtube.com </br> *.ytimg.com </br> fonts.gstatic.com | TCP 443 |
| 4 | **Opcional:** fontes de dados de streaming do PubNub | Consulte a [documentação do PubNub](https://support.pubnub.com/support/solutions/articles/14000043522) | N/A |

## <a name="dashboard-and-report-integration"></a>Integração de dashboard e relatório 

O Power BI depende de determinados pontos de extremidade para poder dar suporte aos seus dashboards e relatórios. Você deve poder se conectar aos pontos de extremidade na tabela e nos sites vinculados abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obrigatório:** integração do Excel | Consulte a [seção do Office Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) no site da lista de permissões do Office 365 | N/A |

## <a name="custom-visuals"></a>Visuais personalizados

O Power BI depende de determinados pontos de extremidade para poder exibir e acessar os visuais personalizados. Você deve poder se conectar aos pontos de extremidade na tabela e nos sites vinculados abaixo.

| Linha | Finalidade | Destino(s) | Porta(s) |
|-----|-------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------|--------------|---------------------------------------------|
| 1 | **Obrigatório:** importar um visual personalizado da interface do Marketplace e um arquivo | *.microsoft.com </br> *.bing.com </br> *.msecnd.net </br> *.osi.office.net </br> *.azureedge.net </br> ajax.aspnetcdn.com </br> nexus.ensighten.com </br> store.office.com | TCP 443 |
| 2 | **Opcional:** Bing Mapas | bing.com </br> platform.bing.com </br> *.dynamic.tiles.virtualearth.net </br> *.virtualearth.net | TCP 443 |
| 3 | **Opcional:** PowerApps | Consulte a [seção Serviços necessários](https://docs.microsoft.com/powerapps/maker/canvas-apps/limits-and-config#required-services) no site de requisitos de sistema do PowerApps | N/A |
| 4 | **Opcional:** Visio | Consulte a [seção do Office Online](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#bkmk_officeonline) no site da lista de permissões do Office 365 | N/A |