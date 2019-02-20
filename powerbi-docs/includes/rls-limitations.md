---
author: mgblythe
ms.service: powerbi
ms.topic: include
ms.date: 02/15/2019
ms.author: mblythe
ms.openlocfilehash: 44ef0aa9d436f3a8a02f9a6b831847d5c996558a
ms.sourcegitcommit: 91ac6185f7026ddbaa925dc54057bb742b4fa411
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/16/2019
ms.locfileid: "56334041"
---
## <a name="limitations"></a>Limitações

Veja a seguir uma lista com as limitações atuais da Segurança em Nível de Linha nos modelos de nuvem.

* Se você definiu funções e regras anteriormente no serviço do Power BI, deverá criá-las novamente no Power BI Desktop.

* Você pode definir a RLS somente nos conjuntos de dados criados com o Power BI Desktop. Se desejar habilitar a RLS para conjuntos de dados criados com o Excel, deverá primeiro converter os arquivos em arquivos PBIX (Power BI Desktop). [Saiba mais](../desktop-import-excel-workbooks.md)

* Somente há suporte para conexões ETL e DirectQuery. Conexões dinâmicas do Analysis Services são tratadas no modelo local.

* No momento, não há suporte para a RLS na Cortana.

## <a name="known-issues"></a>Problemas conhecidos

Há um problema conhecido em que você obterá uma mensagem de erro se tentar publicar um relatório publicado anteriormente no Power BI Desktop. O cenário é descrito a seguir.

1. Sara tem um conjunto de dados que foi publicado no serviço do Power BI e ela configurou a RLS.

1. Sara atualiza o relatório no Power BI Desktop e o publica novamente.

1. Sara recebe um erro.

**Solução alternativa:** Publique novamente o arquivo do Power BI Desktop por meio do serviço do Power BI até que esse problema seja resolvido. Você pode fazer isso selecionando **Obter Dados** > **Arquivos**.
