---
title: Introdução a dashboards para designers do Power BI
description: Os dashboards são um recurso chave do serviço do Power BI. Eles são uma única página, geralmente chamada de tela, que conta uma história por meio de visualizações.
author: maggieMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/10/2018
ms.author: maggies
LocalizationGroup: Dashboards
ms.openlocfilehash: 7a1187373304387ac511053d241e5cfb31f7fcd9
ms.sourcegitcommit: cd85d88fba0d9cc3c7a4dc03d2f35d2bd096759b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/12/2018
ms.locfileid: "53280571"
---
# <a name="intro-to-dashboards-for-power-bi-designers"></a>Introdução a dashboards para designers do Power BI

Um ***dashboard*** do Power BI é uma página única, geralmente chamada de tela, que conta uma história por meio de visualizações. Por ser limitado a uma única página, um dashboard bem projetado contém apenas os elementos mais importantes da história. Os leitores podem exibir relatórios relacionados para obter detalhes.

![dashboard](media/service-dashboards/power-bi-dashboard2.png)

Dashboards são um recurso do serviço do Power BI. Eles não estão disponíveis no Power BI Desktop. Você não pode criar dashboards em dispositivos móveis, mas pode [exibir e compartilhar](mobile-apps-view-dashboard.md) os dashboards lá.

## <a name="dashboard-basics"></a>Noções básicas de dashboard 

As visualizações que você vê no dashboard são chamadas de *blocos*. Você *fixa* blocos em um painel de relatórios. Se for novo no Power BI, você poderá obter uma boa base lendo [Conceitos básicos do Power BI](service-basic-concepts.md).

> [!IMPORTANT]
> Você precisa de uma licença do [Power BI Pro](service-free-vs-pro.md) para criar dashboards.

As visualizações em um dashboard vêm de relatórios e cada relatório é baseado em um conjunto de dados. Uma maneira de pensar em um dashboard é como uma porta de entrada para os relatórios e os conjuntos de dados subjacentes. Selecionar uma visualização leva você para o relatório (e o conjunto de dados) em que ela é baseada.

![diagrama mostrando a relação entre dashboards, relatórios, conjuntos de dados](media/service-dashboards/power-bi-diagram.png)

## <a name="advantages-of-dashboards"></a>Vantagens dos dashboards
Os dashboards são uma ótima maneira de monitorar seus negócios e ver todas as suas métricas mais importantes rapidamente. As visualizações em um dashboard podem vir de um conjunto de dados subjacente, ou de muitos, e de um relatório subjacente, ou de muitos. Um dashboard combina dados locais e na nuvem, proporcionando uma exibição consolidada independentemente do local em que os dados residem.

Dashboards não são apenas uma bela imagem. É altamente interativo e os blocos são atualizados conforme os dados subjacentes mudam.

## <a name="dashboards-versus-reports"></a>Dashboards versus relatórios
[Relatórios](service-reports.md) e painéis parecem semelhantes, pois são ambos são telas preenchidas com visualizações. Porém, existem diferenças importantes.

| **Funcionalidade** | **Dashboards** | **Relatórios** |
| --- | --- | --- |
| Páginas |Uma página |Uma ou mais páginas |
| Fontes de dados |Um ou mais relatórios e um ou mais conjuntos de dados por dashboard |Um único conjunto de dados por relatório |
| Disponível no Power BI Desktop |Não | Pode criar e exibir relatórios no Power BI Desktop |
| Assinar |Pode assinar um dashboard |É possível assinar páginas de relatório |
| Filtragem |Não é possível filtrar ou fatiar |Diferentes maneiras de filtrar, realçar e fatiar |
| Em destaque |Pode definir um dashboard como o dashboard "em destaque" |Não é possível criar um relatório em destaque |
| Favorito | Pode definir dashboards como *favoritos* | Pode definir relatórios como *favoritos*
| Definir alertas |Disponível para blocos de dashboard em determinadas circunstâncias |Não está disponível nos relatórios |
| Consultas de linguagem natural (P e R) |Disponível em painéis | Disponível em relatórios |
| Pode ver campos e tabelas do conjunto de dados subjacentes |Não. Pode exportar dados, mas não consegue ver tabelas e campos no dashboard de controle em si. |Sim. Pode ver as tabelas de conjunto de dados e os campos e valores. |


## <a name="next-steps"></a>Próximas etapas
* Fique à vontade com os dashboards fazendo um tour em um dos nossos [dashboards de exemplo](sample-tutorial-connect-to-the-samples.md).
* Aprenda sobre [blocos de dashboard](service-dashboard-tiles.md).
* Deseja acompanhar um bloco de dashboard individual e receber um email quando ele alcançar um certo limite? [Criar alertas em blocos](service-set-data-alerts.md).
* Aprenda como usar o [Power BI Q&A](power-bi-tutorial-q-and-a.md) para fazer perguntas sobre os dados e receba uma resposta na forma de uma visualização.
