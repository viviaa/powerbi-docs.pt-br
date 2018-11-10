---
title: Perguntas frequentes sobre os visuais personalizados do Power BI
description: Navegue por uma lista de perguntas frequentes e respostas sobre os visuais personalizados do Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 10/29/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 064d32944f52f6e391d4a7ec4df41ecbf09b7e3f
ms.sourcegitcommit: 02f918a4f27625b6f4e47473193ebc8219db40e2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51223066"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>Perguntas frequentes sobre os visuais personalizados do Power BI

## <a name="organizational-custom-visuals"></a>Visuais personalizados da organização

**De que maneira o administrador pode gerenciar os visuais personalizados da organização?**

Na guia “Elementos visuais personalizados da organização” do Portal de Administração, o administrador consegue visualizar e [gerenciar todos os elementos visuais personalizados da organização na empresa](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals): adicionar, desabilitar, habilitar e excluir.
Não há mais necessidade de compartilhar esses visuais por email ou pastas compartilhadas! Uma vez implantados no repositório da organização, os usuários podem descobri-los facilmente e importar os visuais personalizados da organização para os próprios relatórios diretamente do Serviço do Power BI ou do Power BI Desktop. Os visuais personalizados da organização podem ser encontrados no repositório interno (no serviço ou desktop) na guia “MINHA ORGANIZAÇÃO”. Quando o administrador carrega uma nova versão de um visual personalizado da organização, todos recebem a mesma versão atualizada. Os autores de relatórios não precisam excluir os visuais dos próprios relatórios para obter a nova versão, já que todos os relatórios que usam esses visuais são atualizados automaticamente! O mecanismo de atualização é semelhante ao dos visuais do marketplace.

**Se um administrador carregar um visual personalizado do marketplace público para o repositório da organização, ele será automaticamente atualizado quando um fornecedor atualizar o visual no marketplace público?**

Não, não há atualização automática do marketplace público.
É responsabilidade do administrador atualizar a versão dos visuais personalizados da organização, se desejar.

**Existe alguma forma de desabilitar o repositório organizacional?**

Não, os usuários sempre visualizam a guia “MINHA ORGANIZAÇÃO” no Serviço do Power BI ou no Power BI Desktop. O que o administrador pode fazer é desabilitar ou excluir todos os visuais personalizados da organização do Portal de Administração, deixando, assim, o repositório organizacional vazio.
  
**Se o administrador desativar os visuais personalizados do Portal de Administração (configurações de locatário), os usuários ainda terão acesso aos visuais personalizados da organização?**

Sim, se o administrador desativar os visuais personalizados no Portal de Administração, isso não afetará o repositório organizacional. Algumas organizações desabilitam os visuais personalizados e habilitam apenas os visuais selecionados que foram importados e carregados pelo administrador do Power BI para o repositório organizacional. A desabilitação dos visuais personalizados no Portal de Administração não é uma imposição no Power BI Desktop. Os usuários do desktop ainda poderão adicionar e usar os visuais personalizados do marketplace público nos próprios relatórios. No entanto, esses visuais personalizados públicos deixam de ser renderizados após serem publicados no serviço do Power BI e geram um erro apropriado. Ao usar o serviço do Power BI, não será possível importar visuais personalizados do marketplace público. Apenas os visuais do repositório organizacional poderão ser importados porque as configurações dos visuais personalizados no Portal de Administração serão aplicadas no serviço do Power BI.

**Por que o repositório organizacional e os visuais personalizados da organização constituem uma ótima solução empresarial?**

* Todos recebem a mesma versão do visual, que é controlada pelo administrador do Power BI. Depois que o administrador atualiza a versão do visual no Portal de Administração, todos os usuários na organização recebem a versão atualizada automaticamente.

* Não há mais necessidade de compartilhar arquivos dos visuais por email ou pastas compartilhadas! Um único lugar, visível para todos os membros conectados.

* Segurança e compatibilidade, as novas versões dos visuais personalizados da organização são atualizadas automaticamente em todos os relatórios, semelhante aos visuais do marketplace.

* Para visualizar e usar os visuais personalizados da organização, os usuários da organização que os utilizam precisam estar conectados, o que é um elemento de segurança para a organização.

* Os administradores podem controlar quais visuais personalizados disponibilizar na organização.

* Os administradores podem habilitar/desabilitar visuais para testes no Portal de Administração. Melhor aplicação da segurança já que os visuais serão permitidos apenas para os membros da organização.

## <a name="certified-custom-visuals"></a>Visuais personalizados certificados

**O que são os visuais personalizados certificados?**

Os visuais personalizados certificados são os visuais no [marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) que atendem a determinados testes e exigências de código [especificados](power-bi-custom-visuals-certified.md) da equipe do Power BI.  Os testes executados foram projetados para verificar se o visual não acessa serviços ou recursos externos. No entanto, a Microsoft não é autora dos visuais personalizados de terceiros; por isso, recomendamos aos clientes que entrem em contato diretamente com o autor para verificar a funcionalidade de tal visual.

## <a name="next-steps"></a>Próximas etapas

Para saber mais sobre a solução de problemas, acesse [Troubleshooting your Power BI custom visuals](power-bi-custom-visuals-troubleshoot.md) (Solucionar problemas dos visuais personalizados do Power BI).
