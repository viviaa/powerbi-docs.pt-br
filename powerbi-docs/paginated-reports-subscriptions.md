---
title: Assinar relatórios paginados no serviço do Power BI
description: Neste artigo, você aprenderá coisas para ter em mente sobre como assinar relatórios paginados no serviço do Power BI.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 05/24/2019
ms.openlocfilehash: ccec6658808d94728f2a4f14de67c36da0f51def
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222190"
---
# <a name="subscribe-yourself-and-others-to-paginated-reports-in-the-power-bi-service"></a>Inscrever-se por conta própria e outros relatórios paginados no serviço do Power BI 

Agora você pode configurar assinaturas de email para você e outras pessoas para relatórios paginados no serviço do Power BI. Em geral, o processo é o mesmo que [assinar relatórios e dashboards no serviço do Power BI](service-report-subscribe.md). Este artigo esclarece as diferenças e considerações. 

Na configuração de assinaturas, escolha a frequência com que você deseja receber os emails: diária, semanal ou por hora. Se você escolher diária ou semanal, você pode escolher a hora que a execução da assinatura. Em todos, você pode definir até 24 assinaturas diferentes por dia para cada relatório. 

## <a name="considerations-for-paginated-report-subscriptions"></a>Considerações para assinaturas de relatório paginado 

- Diferente das assinaturas de dashboards ou relatórios do Power BI, sua assinatura contém um anexo da saída do relatório inteiro.  Há suporte para os seguintes tipos de anexo: PDF, apresentação do PowerPoint (PPTX), pasta de trabalho do Excel (XLSX), documento do Word (DOCX), arquivo CSV e XML.

- Não há nenhuma imagem de visualização do relatório no corpo do email.  Estamos planejando ter a imagem da primeira página do relatório como um item opcional. 

- O tamanho máximo de relatório do anexo é de 25 MB. 

- Você pode assinar outros usuários para relatórios paginados que se conectam às fontes de dados com suporte no momento, inclusive conjuntos de dados do Azure Analysis Services ou o Power BI. Tenha em mente que o anexo de relatório reflete os dados com base em suas permissões, assim como o SQL Server Reporting Services existe atualmente. 

- Assinaturas da página de relatório são vinculadas ao nome do relatório.  

- Assinaturas de email são enviadas com valores de parâmetro padrão do relatório. 

- Não há nenhuma **após a atualização de dados** opção para a frequência com relatórios paginados. Você sempre pode obter os valores mais recentes da fonte de dados subjacente. 

## <a name="next-steps"></a>Próximas etapas

[Inscrever-se por conta própria e outros relatórios e painéis no serviço do Power BI](service-report-subscribe.md)

[O que são os relatórios paginados no Power BI Premium? (versão prévia)](paginated-reports-report-builder-power-bi.md)
