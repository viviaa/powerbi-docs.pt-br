---
title: Vincular entidades entre fluxos de dados no Power BI
description: Saiba como vincular as entidades em fluxos de dados no Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 11/06/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: b69b84c7c61227ef7a827722c86f54100bd2f3b7
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51266502"
---
# <a name="link-entities-between-dataflows-in-power-bi-preview"></a>Vincular entidades entre fluxos de dados no Power BI (versão prévia)

Com fluxos de dados no Power BI, você pode ter uma única fonte de armazenamento de dados organizacionais em que os analistas de negócios podem preparar e gerenciar seus dados uma vez e, em seguida, reutilizá-los entre aplicativos de análise diferentes na organização. 

Quando você vincula entidades entre fluxos de dados, pode reutilizar entidades que já foram incluídas, limpas e transformadas por outros fluxos de dados pertencentes a terceiros sem a necessidade de manter esses dados. As entidades vinculadas simplesmente apontam para as entidades em outros fluxos de dados e *não* copiam ou duplicam os dados.

![Entidades vinculadas no Power BI](media/service-dataflows-linked-entities/linked-entities_00.png)

As entidades vinculadas são **somente leitura**. Se você quiser criar transformações para uma entidade vinculada, deverá criar uma nova entidade computada com uma referência à entidade vinculada.

## <a name="linked-entity-availability"></a>Disponibilidade da entidade vinculada

As entidades vinculadas exigem uma assinatura [Power BI Premium](service-premium.md) para atualizar. As entidades vinculadas estão disponíveis em qualquer fluxo de dados em um espaço de trabalho que está hospedado na capacidade do Power BI Premium. Não há nenhuma limitação no fluxo de dados de origem.

As entidades vinculadas só funcionam corretamente em novos workspaces do Power BI. Saiba mais sobre os [novos workspaces do Power BI](service-create-the-new-workspaces.md). Todos os fluxos de dados vinculados devem estar localizados em novos espaços de trabalho para funcionar corretamente.

## <a name="how-to-link-entities-between-dataflows"></a>Como vincular entidades entre fluxos de dados

Há algumas maneiras de vincular entidades entre fluxos de dados no Power BI. Você pode selecionar **Adicionar entidades vinculadas** da ferramenta de criação Fluxos de dados, conforme mostrado na imagem a seguir. 

![Entidades vinculadas no Power BI](media/service-dataflows-linked-entities/linked-entities_00.png)

Você também pode selecionar **Adicionar entidades vinculadas** do item de menu **Adicionar entidades** no serviço do Power BI.

![Entidades vinculadas no Power BI](media/service-dataflows-linked-entities/linked-entities_01.png)

Para vincular entidades, você deverá entrar com suas credenciais do Power BI.

Uma janela **Navegador** é aberta e permite que você escolha um conjunto de entidades ao qual pode se conectar. As entidades exibidas são entidades para as quais você tem permissões, em todos os espaços de trabalho em seu locatário do Power BI. 

Depois que suas entidades vinculadas são selecionadas, elas aparecem na lista de entidades para seu fluxo de dados na ferramenta de criação, com um ícone especial que as identifica como entidades vinculadas.

Você também pode exibir o fluxo de dados de origem nas configurações de fluxo de dados de sua entidade vinculada.

## <a name="refresh-logic-of-linked-entities"></a>Atualizar a lógica de entidades vinculadas
A lógica de atualização padrão das entidades vinculadas muda com base em se o fluxo de dados de origem reside no mesmo espaço de trabalho como o fluxo de dados de destino. As seções a seguir descrevem o comportamento de cada.

### <a name="links-between-workspaces"></a>Links entre espaços de trabalho

A atualização dos links de entidades em espaços de trabalho diferentes comporta-se como uma fonte de dados externa. Quando o fluxo de dados é atualizado, ele leva os dados mais recentes para a entidade de fluxo de dados de origem. Se o fluxo de dados de origem for atualizado, ele não afetará automaticamente os dados no fluxo de dados de destino.

### <a name="links-in-the-same-workspace"></a>Links no mesmo espaço de trabalho

Quando ocorre a atualização dos dados para um fluxo de dados de origem, esse evento dispara automaticamente um processo de atualização para entidades dependentes em todos os fluxos de dados de destino no mesmo espaço de trabalho, incluindo as entidades calculadas com base neles. Todas as outras entidades no fluxo de dados de destino são atualizadas de acordo com a agenda do fluxo de dados. As entidades que dependem de mais de uma fonte atualizam seus dados sempre que qualquer uma das suas fontes é atualizada com êxito.

É útil observar que o processo inteiro de atualização é confirmado ao mesmo tempo. Por isso, se a atualização de fluxo de dados de destino não for atualizada, o fluxo de dados de origem falhará também sua atualização.

## <a name="permissions-when-viewing-reports-from-dataflows"></a>Permissões ao exibir relatórios de fluxos de dados

Ao criar um relatório do Power BI que inclui dados com base em um fluxo de dados, os usuários podem ver as entidades vinculadas somente quando o usuário tem acesso ao fluxo de dados de origem.

## <a name="limitations-and-considerations"></a>Limitações e considerações

Há algumas limitações para ter em mente ao trabalhar com entidades vinculadas:

* Há um máximo de cinco saltos de referência
* Dependências cíclicas de entidades vinculadas não são permitidas
* O fluxo de dados deve residir em um [novo workspace do Power BI do Power BI](service-create-the-new-workspaces.md)


## <a name="next-steps"></a>Próximas etapas

Os artigos a seguir podem ser úteis para criar ou trabalhar com fluxos de dados. 

* [Preparação de dados de autoatendimento no Power BI (versão prévia)](service-dataflows-overview.md)
* [Criação e uso de fluxos de dados no Power BI](service-dataflows-create-use.md)
* [Uso de entidades computadas no Power BI Premium (versão prévia)](service-dataflows-computed-entities-premium.md)
* [Uso de fluxos de dados com fontes de dados locais (versão prévia)](service-dataflows-on-premises-gateways.md)
* [Recursos de desenvolvedor para fluxos de dados do Power BI (versão prévia)](service-dataflows-developer-resources.md)

Confira mais informações sobre o Power Query e a atualização agendada nestes artigos:
* [Visão geral da Consulta no Power BI Desktop](desktop-query-overview.md)
* [Configuração de atualização agendada](refresh-scheduled-refresh.md)

Leia este artigo de visão geral para saber mais sobre o Common Data Service:
* [Common Data Service - visão geral ](https://docs.microsoft.com/powerapps/common-data-model/overview)

