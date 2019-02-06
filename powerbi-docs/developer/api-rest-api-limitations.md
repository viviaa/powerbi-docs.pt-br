---
title: Limitações da API REST do Power BI
description: A API REST do Power BI tem as seguintes limitações
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-developer
ms.topic: conceptual
ms.date: 06/08/2018
ms.openlocfilehash: ebca3dd6bcdbb831960da111fc167f59b5ab0623
ms.sourcegitcommit: 0abcbc7898463adfa6e50b348747256c4b94e360
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/06/2019
ms.locfileid: "55761997"
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