---
title: Assinatura de relatórios paginados no serviço do Power BI
description: Neste artigo, você aprenderá o que deve ter em mente em relação à assinatura de relatórios paginados no serviço do Power BI.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 07/15/2019
ms.openlocfilehash: 2d48892450bbf6ab09a4bc88cd2be9a58bbdc863
ms.sourcegitcommit: 9d13ef7a257b5006fca5f92acf5b611f5cd143a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/18/2019
ms.locfileid: "68307078"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Obtenha uma assinatura para você e para outras pessoas de relatórios paginados no serviço do Power BI 

Agora você pode configurar assinaturas de email para você e outras pessoas para relatórios paginados no serviço do Power BI. Em geral, o processo é o mesmo que [assinar relatórios e dashboards no serviço do Power BI](service-report-subscribe.md). Este artigo esclarece as diferenças e as considerações. 

Na configuração de assinaturas, escolha a frequência com que você deseja receber os emails: diariamente, semanalmente ou por hora. Se escolher diariamente ou mensalmente, será possível escolher o momento em que você gostaria de executar a assinatura. No total, você pode definir até 24 assinaturas diferentes por dia para cada relatório. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Considerações sobre assinaturas de relatório paginado 

- Diferentemente das assinaturas de dashboards ou relatórios do Power BI, sua assinatura contém um anexo da saída de relatório completa.  Os seguintes tipos de anexo são compatíveis: PDF, apresentação do PowerPoint (PPTX), pasta de trabalho do Excel (XLSX), documento do Word (DOCX), arquivo CSV e XML.

- Você pode incluir uma imagem de visualização do relatório no corpo do email.  Isso é opcional e pode ser ligeiramente diferente da primeira página do documento de relatório anexado, dependendo do formato de anexo selecionado. 

- O tamanho máximo de anexo do relatório é 25 MB. 

- Você pode assinar outros usuários para relatórios paginados que se conectam às fontes de dados compatíveis no momento, inclusive conjuntos de dados do Azure Analysis Services ou do Power BI. Tenha em mente que o anexo de relatório reflete os dados com base em suas permissões, assim como o SQL Server Reporting Services existe atualmente. 

- As assinaturas de email podem ser enviadas com os parâmetros padrão ou selecionados no momento para seu relatório.  Você pode definir valores de parâmetros diferentes para cada assinatura criada para o relatório. 

- Se o autor do relatório tiver definido parâmetros baseados em expressão (por exemplo, o padrão é sempre a data de hoje), a assinatura o usará como o valor padrão. Você pode alterar outros valores de parâmetro e optar por usar os valores atuais, porém, a menos que também altere explicitamente esse valor, a assinatura usará o parâmetro baseado em expressão.

- Não há opção **Após Atualização de Dados** para a frequência com relatórios paginados. Você sempre obtém os valores mais recentes da fonte de dados subjacente. 

## <a name="next-steps"></a>Próximas etapas

[Obtenha uma assinatura para você e outras pessoas de relatórios e dashboards no serviço do Power BI](service-report-subscribe.md)

[O que são os relatórios paginados no Power BI Premium?](paginated-reports-report-builder-power-bi.md)
