---
title: Cache de consulta no Power BI Premium
description: Cache de consulta no Power BI Premium
author: maggiesMSFT
manager: kfile
ms.reviewer: bhmerc
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/03/2019
ms.author: maggies
LocalizationGroup: ''
ms.openlocfilehash: fbfd8c98743144e0c9604aca4174d6ef32916e77
ms.sourcegitcommit: de0b72915183a8a784d3227838bd704c1c209422
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2019
ms.locfileid: "58914266"
---
# <a name="query-caching-in-power-bi-premium"></a>Cache de consulta no Power BI Premium

As organizações com o Power BI Premium podem aproveitar o *cache de consulta* para acelerar os relatórios associados a um conjunto de dados. O cache de consulta instrui a capacidade de Premium a usar o seu serviço de cache local para manter os resultados da consulta, evitando fazer com que fonte de dados subjacente calcule esses resultados.

> [!IMPORTANT]
> O Cache de consulta só está disponível no Power BI Premium. Ele não é aplicável a conjuntos de dados LiveConnect que aproveitam o Azure Analysis Services ou SQL Server Analysis Services.

Os resultados da consulta em cache são específicos ao contexto do conjunto de dados e do usuário e sempre respeitam as regras de segurança. No momento, o serviço apenas consulta o cache para a página inicial à qual você é levado. Em outras palavras, consultas não são armazenadas em cache quando você interage com o relatório. O cache reflete indicadores pessoais e filtros persistentes. [Blocos de dashboard](service-dashboard-tiles.md) que são ativados pelas mesmas consultas também são beneficiados quando a consulta é armazenada em cache. O desempenho é especialmente beneficiado quando um conjunto de dados é acessado com frequência e não precisa ser atualizado com frequência. O cache de consulta também pode reduzir a carga em sua capacidade Premium, reduzindo o número total de consultas.

Você controla o comportamento de cache de consulta na página **Configurações** para o conjunto de dados no serviço do Power BI. Ele tem três configurações possíveis:

- **Padrão de Capacidade**: O conjunto de dados herda a configuração da capacidade Premium. O padrão de capacidade é controlado pelo administrador de capacidade do Power BI Premium.

- **Desligado**: Não use cache de consulta para esse conjunto de dados.

- **Ligado**: Use o cache de consulta para esse conjunto de dados.

![Caixa de diálogo de cache de consulta](media/power-bi-query-caching/power-bi-query-caching.png)

> [!NOTE]
> Quando você altera as configurações de cache de **Ligado** para **Desligado**, todos os resultados de consulta salvos anteriormente para o conjunto de dados são removidos do cache de capacidade. Você pode desligar o cache explicitamente ou revertendo a configuração de padrão de capacidade que um administrador definiu como **Desligado**. Desligá-lo pode introduzir um pequeno atraso na próxima vez que qualquer relatório executar consultas nesse conjunto de dados. O atraso é provocado pela execução sob demanda dessas consultas de relatório sem aproveitar os resultados salvos. Além disso, o conjunto de dados necessário talvez precise ser carregado na memória antes que ele possa atender a consultas.


