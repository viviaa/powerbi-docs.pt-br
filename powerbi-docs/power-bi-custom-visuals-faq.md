---
title: Perguntas frequentes sobre os visuais personalizados do Power BI
description: Navegue por uma lista de perguntas frequentes e respostas sobre os visuais personalizados do Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: conceptual
ms.custom: ''
ms.date: 12/17/2018
ms.openlocfilehash: 9b4ff995b1cfaede1608e976bf2715feece0ade6
ms.sourcegitcommit: a2f274cfb392fe3b1b466a39ec7eaf58a7c5ce00
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "56408128"
---
# <a name="frequently-asked-questions-about-power-bi-custom-visuals"></a>Perguntas frequentes sobre os visuais personalizados do Power BI

## <a name="organizational-custom-visuals"></a>Visuais personalizados da organização

### <a name="how-can-the-admin-manage-the-organizational-custom-visuals"></a>De que maneira o administrador pode gerenciar os visuais personalizados da organização?

Na guia “Elementos visuais personalizados da organização” do Portal de Administração, o administrador consegue visualizar e [gerenciar todos os elementos visuais personalizados da organização na empresa](https://docs.microsoft.com/power-bi/service-admin-portal#organization-visuals): adicionar, desabilitar, habilitar e excluir.
Não há mais necessidade de compartilhar esses visuais por emails ou por pastas compartilhadas! Uma vez implantados no repositório da organização, os usuários podem localizá-los facilmente e importar os visuais personalizados da organização para os próprios relatórios diretamente do Serviço do Power BI ou do Power BI Desktop. Os visuais personalizados da organização podem ser encontrados no repositório interno (no serviço ou desktop) na guia *MINHA ORGANIZAÇÃO*. Quando o administrador carrega uma nova versão de um visual personalizado da organização, todos recebem a mesma versão atualizada. Os autores de relatórios não precisam excluir os visuais nos próprios relatórios para obter a nova versão, já que todos os relatórios que usam esses visuais são atualizados automaticamente! O mecanismo de atualização é semelhante ao dos visuais do marketplace.

### <a name="if-an-admin-uploads-a-custom-visual-from-the-public-marketplace-to-the-organization-store-is-it-automatically-updated-once-a-vendor-updates-the-visual-in-the-public-marketplace"></a>Se um administrador carregar um visual personalizado do marketplace público para o repositório da organização, ele será automaticamente atualizado quando um fornecedor atualizar o visual no marketplace público?

Não, não há uma atualização automática do marketplace público.
É responsabilidade do administrador atualizar a versão dos visuais personalizados da organização.

### <a name="is-there-a-way-to-disable-the-organizational-store"></a>Existe alguma forma de desabilitar o repositório da organização?

Não, os usuários sempre visualizam a guia “MINHA ORGANIZAÇÃO” no Serviço do Power BI ou no Power BI Desktop. O que o administrador pode fazer é desabilitar ou excluir todos os visuais personalizados da organização do Portal de Administração, deixando, assim, o repositório organizacional vazio.
  
### <a name="if-the-administrator-disables-custom-visuals-from-the-admin-portal-tenant-settings-do-users-still-have-access-to-the-organizational-custom-visuals"></a>Se o administrador desabilitar os visuais personalizados do Portal de Administração (configurações de locatário), os usuários ainda terão acesso aos visuais personalizados da organização?

Sim, se o administrador desativar os visuais personalizados no Portal de Administração, isso não afetará o repositório organizacional. Algumas organizações desabilitam os visuais personalizados e habilitam apenas os visuais selecionados que foram importados e carregados pelo administrador do Power BI para o repositório organizacional. A desabilitação dos visuais personalizados no Portal de Administração não é uma imposição no Power BI Desktop. Os usuários do desktop ainda poderão adicionar e usar os visuais personalizados do marketplace público nos próprios relatórios. No entanto, esses visuais personalizados públicos deixam de ser renderizados após serem publicados no serviço do Power BI e geram um erro apropriado. Ao usar o serviço do Power BI, não é possível importar visuais personalizados do marketplace público. Apenas os visuais do repositório organizacional poderão ser importados porque as configurações dos visuais personalizados no Portal de Administração serão aplicadas no serviço do Power BI.

### <a name="why-does-the-organizational-store-and-organizational-custom-visuals-make-a-great-enterprise-solution"></a>Por que o repositório organizacional e os visuais personalizados da organização constituem uma ótima solução empresarial?

* Todos recebem a mesma versão do visual, que é controlada pelo administrador do Power BI. Depois que o administrador atualiza a versão do visual no Portal de Administração, todos os usuários na organização recebem a versão atualizada automaticamente.

* Não há mais necessidade de compartilhar arquivos dos visuais por email ou pastas compartilhadas! Um único lugar, visível para todos os membros conectados.

* Segurança e compatibilidade, as novas versões dos visuais personalizados da organização são atualizadas automaticamente em todos os relatórios, semelhante aos visuais do marketplace.

* Para visualizar e usar os visuais personalizados da organização, os usuários da organização que os utilizam precisam estar conectados, o que é um elemento de segurança para a organização.

* Os administradores podem controlar quais visuais personalizados disponibilizar na organização.

* Os administradores podem habilitar/desabilitar visuais para testes no Portal de Administração. Melhor aplicação da segurança já que os visuais serão permitidos apenas para os membros da organização.

## <a name="certified-custom-visuals"></a>Visuais personalizados certificados

### <a name="what-are-certified-custom-visuals"></a>O que são visuais personalizados certificados?

Os visuais personalizados certificados são os visuais no [marketplace](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) que atendem a determinados testes e exigências de código [especificados](power-bi-custom-visuals-certified.md) da equipe do Power BI.  Os testes executados foram criados para verificar se o visual não acessa serviços ou recursos externos. No entanto, a Microsoft não é o autor de visuais personalizados de terceiros. Recomendamos aos clientes contatar o autor diretamente para verificar a funcionalidade do visual em questão.

## <a name="visuals-with-additional-purchases"></a>Visuais com compras adicionais

### <a name="what-is-a-visual-with-additional-purchases"></a>O que é um visual com compras adicionais?

Um visual com compras adicionais é semelhante a suplementos de IAP (compra no aplicativo) no marketplace; esses suplementos têm uma etiqueta de preço **Pode ser necessária uma compra adicional**.

Os visuais personalizados de IAP são visuais personalizados gratuitos e que podem ser baixados – os usuários não pagam nada para baixar esses visuais personalizados do marketplace. Os visuais de IAP oferecem compras opcionais no aplicativo para recursos avançados.  

### <a name="whats-the-benefit-to-developers"></a>Qual é o benefício para desenvolvedores?

Os visuais personalizados de IAP no AppSource serão detectáveis para muitos visitantes diários, trazendo tráfego valioso e maior reconhecimento para seus visuais personalizados de IAP e para você enquanto desenvolvedor.

Se até recentemente você gerenciava esses visuais por meio do seu site, agora é possível enviá-los ao AppSource. Que aumentará o nível de capacidade de descoberta e visibilidade dos visuais de IAP dentro da comunidade do Power BI.

Os visuais no AppSource aproveitam um canal de comentários direto dos seus clientes que estão usando o visual personalizado de IAP por meio de um sistema de análises e classificações na loja.  

Após a aprovação do visual de IAP pela equipe de validação do AppSource, você também poderá enviar esses visuais para certificação. É um processo opcional.  

Depois que o visual é certificado, os visuais personalizados de IAP podem ser exportados para o PowerPoint e exibidos nos emails recebidos quando um usuário assina páginas de relatório. Portanto, ao enviar visuais de IAP ao marketplace, os visuais personalizados de IAP também podem ser certificados e compatíveis com um conjunto de recursos extra.  

### <a name="do-iap-visuals-need-to-be-certified"></a>Os visuais de IAP precisam ser certificados?

O processo de certificação é opcional. Cabe ao desenvolvedor decidir certificar seus visuais personalizados de IAP ou não fazer o mesmo com visuais gratuitos.

### <a name="what-is-changing-in-the-submission-process"></a>O que está mudando no processo de envio?

O processo de envio de visuais personalizados de IAP para o marketplace é o mesmo processo para visuais gratuitos. Isso acontece por meio do dashboard do vendedor.  A única mudança no processo de envio é que os desenvolvedores precisarão declarar nas notas do desenvolvedor no dashboard do vendedor: "Visual com compra no aplicativo". Também será necessário fornecer uma chave/token de licença se for preciso validar os recursos pagos/avançados.  

Não haverá nenhuma opção nova no dashboard do vendedor: *gratuito com compras no aplicativo*, será necessário enviar seus visuais de IAP como *gratuitos*.

Além disso, permita que os usuários saibam o que esperar fornecendo, em sua loja, uma longa descrição de quais recursos são gratuitos e quais recursos precisam de outras compras para operar.  

### <a name="what-should-i-do-beforesubmittingmy-iap-custom-visual"></a>O que devo fazer antes de enviar meu visual personalizado de IAP?

Se estiver trabalhando em um visual personalizado de IAP ou já tiver um, verifique se ele está em conformidade com as diretrizes.  

Se tiver um logotipo no visual personalizado, verifique se ele está em conformidade com as diretrizes de logotipo (cor, localização, tamanho e disparo de ação).

Também é possível localizar, nas diretrizes, notas de práticas recomendadas.  
> [!Note]
> Todos os visuais gratuitos devem manter os mesmos recursos gratuitos oferecidos anteriormente. Você pode adicionar recursos pagos avançados opcionais aos recursos gratuitos antigos. Recomendamos o envio dos visuais de IAP com os recursos avançados como novos visuais e a não atualização dos gratuitos antigos.


### <a name="can-i-get-my-iap-custom-visual-certified"></a>Posso ter meu visual personalizado de IAP certificado?

Sim, o mesmo que ocorre com visuais gratuitos.  Após a aprovação do seu visual personalizado de IAP pela equipe do AppSource, será possível enviar o visual para o processo de certificação.

Para certificar seu visual, ele deve estar em conformidade com os requisitos de certificação, por exemplo, o visual não pode acessar os serviços externos para validação de licenças.

A certificação de recall é um processo opcional; cabe a você decidir se deseja que seu visual de IAP seja certificado.

## <a name="additional-questions"></a>Outras perguntas

### <a name="how-to-get-support"></a>Como obtenho suporte?

Fique à vontade para contatar a equipe de suporte de visuais personalizados: *pbicvsupport@microsoft.com* caso tenha perguntas, comentários ou problemas.  

## <a name="next-steps"></a>Próximas etapas

Para saber mais, acesse [Troubleshooting your Power BI custom visuals](power-bi-custom-visuals-troubleshoot.md) (Solucionar problemas dos visuais personalizados do Power BI).
