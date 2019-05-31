---
title: Filtrar um relatório e compartilhá-lo com colegas de trabalho - Power BI
description: Saiba como filtrar um relatório do Power BI e compartilhá-lo com colegas de trabalho em sua organização.
author: maggiesMSFT
manager: kfile
ms.reviewer: lukaszp
featuredvideoid: 0tUwn8DHo3s
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 04/24/2019
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: 5f3808884e63521ec1dd775d876f1cf707bbe56b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64770685"
---
# <a name="filter-a-power-bi-report-and-share-it-with-coworkers"></a>Filtrar um relatório do Power BI e compartilhá-lo com colegas de trabalho
O *compartilhamento* é uma boa maneira de conceder acesso a algumas pessoas aos dashboards e relatórios. Se você deseja compartilhar uma versão filtrada de um relatório? Talvez um relatório que mostre apenas os dados para uma cidade específica, vendedor ou ano. Tente filtrar um relatório e compartilhá-la ou criar uma URL personalizada. O relatório será filtrado quando os destinatários o abrirem pela primeira vez. Eles poderão remover o filtro modificando a URL. 

O Power BI também oferece [várias outras maneiras para colaborar e distribuir seus relatórios](service-how-to-collaborate-distribute-dashboards-reports.md). Com o compartilhamento, você e os destinatários precisarão de uma [licença do Power BI Pro](service-features-license-type.md) ou então o conteúdo precisará estar em uma [capacidade Premium](service-premium-what-is.md). 

## <a name="two-ways-to-filter-a-report"></a>Duas maneiras para filtrar um relatório

### <a name="set-a-filter"></a>Defina um filtro

Abra o relatório no [Modo de Exibição de Edição](consumer/end-user-reading-view.md), aplique o filtro e salve o relatório.
   
Neste exemplo, estamos filtrando a [amostra de Análise de Varejo](sample-tutorial-connect-to-the-samples.md) para mostrar apenas valores em que o **Território** é igual a **NC**.
   
![Painel de filtro do relatório](media/service-share-reports/power-bi-filter-report2.png)

### <a name="create-a-filter-in-the-url"></a>Criar um filtro na URL

Adicione o seguinte ao final da URL da página de relatório:
   
?filter=*tablename*/*fieldname* eq *value*
   
O campo deve ser do tipo número, data e hora ou cadeia de caracteres. Os valores de *tablename* ou *fieldname* não podem conter espaços.
   
Em nosso exemplo, o nome da tabela é **Loja**, o nome do campo é **Território** e o valor que desejamos usar para filtrar é **NC**:
   
?filter=Store/Territory eq 'NC'
   
![URL do relatório filtrado](media/service-share-reports/power-bi-filter-url3.png)
   
O navegador adiciona caracteres especiais para representar barras, espaços e apóstrofes, portanto, você acabará com:
   
app.powerbi.com/groups/me/reports/010ae9ad-a9ab-4904-a7a1-xxxxxxxxxxxx/ReportSection2?filter=Store%252FTerritory%20eq%20%27NC%27

Consulte o artigo [filtrar um relatório usando parâmetros de cadeia de caracteres de consulta na URL](service-url-filters.md) para muito mais detalhes.

## <a name="share-the-filtered-report"></a>Compartilhar o relatório filtrado

1. Quando você [compartilharem o relatório](service-share-dashboards.md), desmarque as **enviar notificação de email para destinatários** caixa de seleção.

    ![Caixa de diálogo Compartilhar relatório](media/service-share-reports/power-bi-share-report-dialog.png)

4. Envie o link com o filtro que você criou anteriormente.

## <a name="next-steps"></a>Próximas etapas
* Tem comentários? Vá para o [site da comunidade do Power BI](https://community.powerbi.com/) para fazer sugestões.
* [Como devo colaborar e compartilhar relatórios e dashboards?](service-how-to-collaborate-distribute-dashboards-reports.md)
* [Compartilhar um dashboard](service-share-dashboards.md)
* Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/).

