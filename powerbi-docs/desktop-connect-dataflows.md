---
title: Conectar-se aos dados criados por fluxos de dados do Power BI no Power BI Desktop (Beta)
description: Conecte-se facilmente e use fluxos de dados no Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 11/06/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: f87db1f715118f346e3b8069897e92fd157f881c
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265922"
---
# <a name="connect-to-data-created-by-power-bi-dataflows-in-power-bi-desktop-beta"></a>Conectar-se aos dados criados por fluxos de dados do Power BI no Power BI Desktop (Beta)
No **Power BI Desktop**, é possível conectar-se a dados criados por **fluxos de dados do Power BI** como qualquer outra fonte de dados no Power BI Desktop.

![Conectar-se a fluxos de dados](media/desktop-connect-dataflows/connect-dataflows_01.png)

O conector de **fluxos de dados do Power BI (Beta)** permite a conexão a entidades criadas por fluxos de dados no serviço do Power BI. 

## <a name="considerations-and-limitations"></a>Considerações e limitações

Para usar esta versão beta do **conector de fluxos de dados do Power BI**, é necessário estar executando a versão mais recente do **Power BI Desktop**. Sempre é possível [baixar o Power BI Desktop](desktop-get-the-desktop.md) e instalá-lo em seu computador para garantir que você tem a versão mais recente.  

> [!NOTE]
> A versão anterior do conector de fluxos de dados do Power BI exigia que você fizesse o download de um arquivo .MEZ e o colocasse em uma pasta. As versões atuais do **Power BI Desktop** incluem o conector de fluxos de dados do Power BI, por isso esse arquivo não é mais necessário e pode causar conflitos com a versão incluída do conector. Caso tenha colocado o arquivo .MEZ manualmente na pasta, você *deve* exclui-lo da pasta **Documentos > Power BI Desktop > Conectores personalizados** para evitar conflitos. 

## <a name="desktop-performance"></a>Desempenho do desktop
O **Power BI Desktop** é executado localmente no computador em que se encontra instalado. Uma série de fatores determina o desempenho da ingestão de fluxos de dados. Entre eles estão o tamanho dos dados, a CPU e a memória RAM do seu computador, a largura de banda de rede, a distância do data center, além de outros fatores.

É possível melhorar o desempenho da ingestão de dados dos fluxos de dados. Por exemplo, se o tamanho dos dados ingeridos for muito grande para o **Power BI Desktop** gerenciar no seu computador, você pode usar as entidades vinculadas e computadas em fluxos de dados para agregar os dados (dentro de fluxos de dados) e ingerir apenas os dados agregados preparados previamente. Dessa forma, o processamento de dados grandes é executado online em fluxos de dados, em vez de ser executados localmente na instância em execução do **Power BI Desktop**. Essa abordagem permite ao Power BI Desktop ingerir menores quantidades de dados, além de manter a experiência com os fluxos de dados rápida e responsiva.


## <a name="next-steps"></a>Próximas etapas
Há inúmeras coisas interessantes que você pode fazer com os fluxos de dados do Power BI. Confira mais informações nos recursos a seguir:

* [Preparação de dados de autoatendimento com fluxos de dados](service-dataflows-overview.md)
* [Criação e uso de fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Uso de entidades computadas no Power BI Premium (versão prévia)](service-dataflows-computed-entities-premium.md)
* [Uso de fluxos de dados com fontes de dados locais (versão prévia)](service-dataflows-on-premises-gateways.md)
* [Recursos de desenvolvedor para fluxos de dados do Power BI (versão prévia)](service-dataflows-developer-resources.md)

Também há artigos sobre o **Power BI Desktop** que podem ser úteis:

* [Fontes de dados no Power BI Desktop](desktop-data-sources.md)
* [Formatar e combinar dados com o Power BI Desktop](desktop-shape-and-combine-data.md)
* [Inserir dados diretamente no Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

