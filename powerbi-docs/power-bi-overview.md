---
title: O que é Power BI?
description: Visão geral do Power BI e como as diferentes partes se encaixam - Power BI Desktop, o serviço do Power BI, Power BI mobile, servidor de relatório e Power BI embedded.
author: maggiesMSFT
manager: kfile
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: overview
ms.date: 05/29/2019
ms.author: maggies
LocalizationGroup: Get started
ms.openlocfilehash: 7236caba1c7a8eb07e93c6f2af7068141b8ac3a7
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66413049"
---
# <a name="what-is-power-bi"></a>O que é Power BI?
O **Power BI** é uma coleção de serviços de software, aplicativos e conectores que trabalham juntos para transformar suas fontes de dados não relacionadas em informações coerentes, visualmente envolventes e interativas. Os dados podem estar em uma planilha do Excel ou em uma coleção de data warehouses híbridos locais ou baseados na nuvem. Power BI permite que você facilmente se conectar às fontes de dados, visualizar e descobrir o que é importante e compartilhe isso com qualquer pessoa ou com quem que você quiser.

![diagrama mostrando fontes de entrada para o Power BI](media/power-bi-overview/power-bi-input-new.png)

Power BI pode ser simples e rápida, com capacidade de criar análises rápidas de uma planilha do Excel ou um banco de dados local. Mas o Power BI também é robusto e empresarial, pronto para ampla modelagem e análise em tempo real, bem como desenvolvimento personalizado. Ele pode ser sua ferramenta de visualização e o pessoal de relatório e também servem como o mecanismo de decisão e análise para projetos de grupo, divisões ou empresas inteiras.

## <a name="the-parts-of-power-bi"></a>As partes do Power BI
Power BI consiste em: 
- Um aplicativo de desktop do Windows chamado **Power BI Desktop**
- Um SaaS online (*Software como serviço*) chamado de serviço a **serviço do Power BI** 
- Power BI **aplicativos móveis** para dispositivos Android, iOS e Windows

![Power BI Desktop, serviço, Mobile](media/power-bi-overview/power-bi-blocks.png)

Esses três elementos&mdash;Power BI Desktop, o serviço e os aplicativos móveis&mdash;são projetados para permitir que as pessoas criar, compartilhar e consumir análises de negócios da maneira que serve-los, ou para sua função, com mais eficiência.

O quarto elemento, o **Servidor de Relatórios do Power BI**, permite publicar relatórios do Power BI em um servidor de relatórios local, depois de criá-los no Power BI Desktop. Leia mais sobre o [Servidor de Relatório do Power BI](#on-premises-reporting-with-power-bi-report-server).

## <a name="how-power-bi-matches-your-role"></a>Como o Power BI corresponde à sua função
A forma de uso do Power BI pode depender de sua função em um projeto ou uma equipe. Outras pessoas, em outras funções, podem usar o Power BI diferente.

Por exemplo, você pode usar principalmente o **serviço do Power BI**, mas seu colega que trabalha com cálculos de grandes dados numéricos e com a criação de relatórios de negócios pode usar extensivamente o **Power BI Desktop** para criar relatórios e publicá-los no serviço do Power BI, onde é possível exibi-los. Outro colega de trabalho, nas vendas, talvez use principalmente suas **aplicativo de telefone do Power BI** para monitorar o progresso em suas cotas de vendas e analisar os detalhes do novo cliente potencial de vendas.

Caso seja um desenvolvedor, você pode usar APIs do Power BI para efetuar push dos dados para conjuntos de dados ou para inserir relatórios e dashboards em seus próprios aplicativos personalizados. Ter uma ideia de um novo visual? Crie-o você mesmo e compartilhe-o com outras pessoas.  

Você também pode usar cada elemento do Power BI em momentos diferentes, dependendo da sua função para um determinado projeto ou o que você está tentando alcançar.

A maneira de usar o Power BI depende do respectivo recurso ou serviço que seja mais adequado como ferramenta para o caso. Por exemplo, você pode usar o Power BI Desktop para criar relatórios para sua própria equipe sobre as estatísticas de envolvimento do cliente e você pode exibir o inventário e fabricação progresso em um painel em tempo real no serviço do Power BI. Todos os elementos do Power BI estão disponíveis para você. Por isso, ele é um programa tão versátil e interessante.

Explore os documentos pertinentes à sua função:
- Power BI para [***designers***](desktop-what-is-desktop.md)
- Power BI para [***consumidores***](consumer/end-user-consumer.md)
- Power BI para [***desenvolvedores***](developer/what-can-you-do.md)
- Power BI para [***administradores***](service-admin-administering-power-bi-in-your-organization.md)

## <a name="the-flow-of-work-in-power-bi"></a>O fluxo de trabalho no Power BI
Um fluxo de trabalho no Power BI comum começa conectando-se a fontes de dados e criação de um relatório no Power BI Desktop. Em seguida, publicar o relatório do Power BI Desktop no serviço do Power BI e compartilhá-lo para que os usuários finais no serviço do Power BI e dispositivos móveis podem exibir e interagir com o relatório.
Esse fluxo de trabalho é comum e mostra como os três principais elementos do Power BI se complementam.

Veja uma [comparação detalhada entre o Power BI Desktop e o serviço do Power BI](service-service-vs-desktop.md).

Mas e se você não estiver pronto para ir para a nuvem e quiser manter seus relatórios atrás de um firewall corporativo?  Continue lendo.

## <a name="on-premises-reporting-with-power-bi-report-server"></a>Relatórios com o servidor de relatório do Power BI locais
Criar, implantar e gerenciar relatórios do Power BI móveis e paginados localmente com a variedade de ferramentas prontas para usar e serviços fornecidos pelo servidor de relatório do Power BI.

![diagrama para local](media/power-bi-overview/power-bi-report-server2.png)

O Servidor de Relatórios do Power BI é uma solução que você implanta atrás do firewall e, em seguida, fornece relatórios para os usuários corretos de diferentes maneiras, seja exibindo-os em um navegador da Web, em um dispositivo móvel ou como um email. E, como o Servidor de Relatórios do Power BI é compatível com o Power BI na nuvem, você pode ir para a nuvem quando estiver pronto. 

Leia mais sobre o [Servidor de Relatório do Power BI](report-server/get-started.md).

## <a name="next-steps"></a>Próximas etapas
- [Início Rápido: Aprenda do seu jeito em torno do serviço do Power BI](service-the-new-power-bi-experience.md)   
- [Tutorial: Introdução ao serviço do Power BI](service-get-started.md)
- [Início Rápido: conectar-se a dados no Power BI Desktop](desktop-quickstart-connect-to-data.md)
