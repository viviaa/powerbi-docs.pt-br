---
title: Limitações da API REST do Power BI
description: A API REST do Power BI tem as seguintes limitações
author: markingmyname
manager: kfile
ms.author: maghan
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: df17563d384359fe33123ed87743754bb33bf04d
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54277953"
---
# <a name="power-bi-rest-api-limitations"></a>Limitações da API REST do Power BI  
  
**Para POSTAR linhas**  
  
* máx de colunas 75
* máx de tabelas 75
* Máximo de 10 mil linhas por cada solicitação de linhas POST  
* Um milhão de linhas adicionadas por hora por conjunto de dados  
* No máximo cinco solicitações de linhas de POST pendentes por conjunto de dados  
* 120 solicitações de linhas POST por minuto por conjunto de dados
* Se a tabela tem 250.000 ou mais linhas, 120 solicitações de linhas POST por hora por conjunto de dados    
* Máximo de 200 mil linhas armazenadas por tabelas no conjunto de dados PEPS  
* Máximo de cinco mil linhas armazenadas por tabela no conjunto de dados “sem política de retenção”  
* 4.000 caracteres por valor para coluna de cadeia de caracteres na operação de linhas POST
  
## <a name="see-also"></a>Consulte também

[Restrições e limites de serviço do Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-service-limits-restrictions)   
[Visão geral da API REST do Power BI](https://docs.microsoft.com/rest/api/power-bi/)