---
title: Compartilhar um relatório filtrado do Power BI com colegas de trabalho
description: Saiba como filtrar um relatório do Power BI e compartilhá-lo com colegas de trabalho em sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/21/2018
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d5e05775d310af37b2c96c6e9e255de25fe5effe
ms.sourcegitcommit: 5206651c12f2b91a368f509470b46f3f4c5641e6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53983429"
---
# <a name="share-a-filtered-power-bi-report-with-your-coworkers"></a>Compartilhar um relatório do Power BI filtrado com seus colegas
O *compartilhamento* é uma boa maneira de conceder acesso a algumas pessoas aos dashboards e relatórios. O Power BI também oferece [várias outras maneiras para colaborar e distribuir seus relatórios](service-how-to-collaborate-distribute-dashboards-reports.md).

Com o compartilhamento, você e os destinatários precisarão de uma [licença do Power BI Pro](service-features-license-type.md) ou então o conteúdo precisará estar em uma [capacidade Premium](service-premium.md). 

Você pode compartilhar um relatório com colegas de trabalho no mesmo domínio de email, da maioria dos lugares no serviço Power BI: seus Favoritos, Recentes, Compartilhado comigo (se o proprietário permite isso), Meu Workspace ou outros workspaces. Quando você compartilha um relatório, os colegas de trabalho com quem você o compartilha podem vê-lo e interagir com ele, mas não podem editá-lo. Elas veem os mesmos dados que você no relatório, a menos que a [RLS (segurança em nível de linha)](service-admin-rls.md) seja aplicada. 

Se você deseja compartilhar uma versão filtrada de um relatório? Talvez um relatório que mostre apenas os dados para uma cidade específica, vendedor ou ano. Tente criar uma URL personalizada. O relatório será filtrado quando os destinatários o abrirem pela primeira vez. Eles poderão remover o filtro modificando a URL.

## <a name="filter-and-share-a-report"></a>Filtrar e compartilhar um relatório

1. Abra o relatório no [Modo de Exibição de Edição](consumer/end-user-reading-view.md), aplique o filtro e salve o relatório.
   
   Neste exemplo, estamos filtrando a [amostra de Análise de Varejo](sample-tutorial-connect-to-the-samples.md) para mostrar apenas valores em que o **Território** é igual a **NC**.
   
   ![Painel de filtro do relatório](media/service-share-reports/power-bi-filter-report2.png)
2. Adicione o seguinte ao final da URL da página de relatório:
   
   ?filter=*tablename*/*fieldname* eq *value*
   
    O campo precisa ser do tipo **cadeia de caracteres**. Os valores de *tablename* ou *fieldname* não podem conter espaços.
   
   Em nosso exemplo, o nome da tabela é **Loja**, o nome do campo é **Território** e o valor que desejamos usar para filtrar é **NC**:
   
    ?filter=Store/Territory eq 'NC'
   
   ![URL do relatório filtrado](media/service-share-reports/power-bi-filter-url3.png)
   
   O navegador adiciona caracteres especiais para representar barras, espaços e apóstrofes, portanto, você acabará com:
   
   app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

3. [Compartilhe o relatório](service-share-dashboards.md), mas desmarque a caixa de seleção **Enviar notificação por email para os destinatários**. 

    ![Caixa de diálogo Compartilhar relatório](media/service-share-reports/power-bi-share-report-dialog.png)

4. Envie o link com o filtro que você criou anteriormente.

## <a name="next-steps"></a>Próximas etapas
* Tem comentários? Vá para o [site da comunidade do Power BI](https://community.powerbi.com/) para fazer sugestões.
* [Como devo colaborar e compartilhar relatórios e dashboards?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Compartilhar um dashboard](service-share-dashboards.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).

