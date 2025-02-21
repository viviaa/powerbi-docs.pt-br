---
title: Power BI para clientes do Governo dos Estados Unidos – visão geral
description: Para clientes do Governo Clientes do Governo, saibam mais sobre os recursos e as limitações para o serviço do Governo dos EUA do Power BI
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/06/2019
ms.author: davidi
LocalizationGroup: Get started
ms.openlocfilehash: 554a5de238af650ab4009669d55a2fadedd4a29f
ms.sourcegitcommit: aef57ff94a5d452d6b54a90598bd6a0dd1299a46
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66809130"
---
# <a name="power-bi-for-us-government-customers"></a>Power BI para clientes do Governo dos EUA
O **serviço do Power BI** tem uma versão disponível para clientes do Governo dos Estados Unidos como parte das assinaturas da **Comunidade do Governo dos EUA do Office 365**. A versão do **serviço do Power BI** discutida neste artigo é desenvolvida especificamente para clientes do Governo dos EUA e é separada e diferente da versão comercial do **serviço do Power BI**.

![](media/service-govus-overview/service_usgov_overview-1.png)

As seções a seguir descrevem os *recursos* disponíveis para a versão do Governo dos EUA do **serviço do Power BI**, esclarece algumas das *limitações*, lista as **Perguntas Frequentes** e as respostas (incluindo como fazer a inscrição) e fornece links para obter mais informações.

## <a name="features-of-power-bi-us-government"></a>Recursos do Power BI para o Governo dos EUA
É importante observar que o **Power BI do Governo dos EUA** só está disponível como uma **licença Pro** e não está disponível como uma licença Gratuita. Alguns recursos do serviço do Power BI estão disponíveis na versão do **Power BI do Governo dos EUA** do serviço.

Os seguintes recursos estão disponíveis para clientes do **Power BI do Governo dos EUA**, pois se aplicam à funcionalidade da licença **Pro**:

* Criar e exibir dashboards e relatórios
* [Limites de capacidade de dados](service-admin-manage-your-data-storage-in-power-bi.md)
* [Atualização de dados agendada](refresh-data.md)
* Dashboards de equipe atualizáveis
* Grupos do Active Directory para compartilhar e gerenciar o controle de acesso
* [Importar dados](service-get-data.md) e relatórios de arquivos do Excel, CSV e Power BI Desktop
* Gateway de Gerenciamento de Dados
* Todos os dados são criptografados no SQL Azure e no Armazenamento de Blobs para o Power BI
* Conectar serviços a [pacotes de conteúdo](service-connect-to-services.md)

## <a name="connectivity-between-government-and-global-azure-cloud-services"></a>Conectividade entre os Serviços de Nuvem globais e Governamentais do Azure 

O Azure é distribuído entre várias nuvens. Por padrão, é permitido que os locatários abram as regras de firewall para uma instância específica a uma nuvem, mas a rede entre nuvens é diferente e requer a abertura de regras de firewall específicas para a comunicação entre os serviços. Se você for um cliente do Power BI e tiver instâncias existentes do SQL na nuvem pública que precisará acessar, será preciso abrir regras de firewall específicas no SQL para o espaço de IP de Nuvem do Azure Governamental para os datacenters a seguir:

* Gov. EUA – Iowa
* Gov. EUA – Virgínia
* Gov. EUA – Texas
* Gov. EUA – Arizona

Na nuvem pública, os espaços IP estão disponíveis, mas na nuvem governamental, é preciso abrir um tíquete de suporte do Azure para solicitar os intervalos de IP para os datacenters listados acima. 


## <a name="limitations-of-power-bi-us-government"></a>Limitações do Power BI para o Governo dos EUA
Alguns dos recursos disponíveis na versão comercial do **serviço do Power BI** *não* estão disponíveis no **serviço do Power BI** para clientes do Governo dos EUA. Equipe do Power BI está trabalhando ativamente para tornar esses recursos disponíveis para clientes do Governo dos EUA e atualizará este artigo quando esses recursos estiverem disponíveis.

* **Inserir no SharePoint Online** - não é possível inserir o conteúdo no SharePoint Online usando a web part do Power BI. No entanto, a inserção segura funciona usando a [web part *Inserir*](https://docs.microsoft.com/power-bi/service-embed-secure). Você precisa adicionar *app.powerbigov.us* à lista de exceções, o que pode ser realizado seguindo as instruções no artigo [Permitir ou restringir a capacidade de inserir conteúdo nas páginas do SharePoint](https://support.office.com/article/allow-or-restrict-the-ability-to-embed-content-on-sharepoint-pages-e7baf83f-09d0-4bd1-9058-4aa483ee137b).
* O **Power BI do Governo dos EUA** só está disponível como uma licença **Pro**. Todas as referências a licenças do Power BI (Gratuito) em um portal de administrador (ou como usuários) estão em execução em uma nuvem de serviço do Power BI comercial.
* **Auditoria** – agora a auditoria está disponível por meio do portal de Segurança e Conformidade do Office 365, a partir de junho de 2018.
* **Conteúdo do Power BI no Cortana** – os resultados do Power BI não aparecerão nos resultados da pesquisa do Cortana, o que inclui resultados para o conteúdo do Power BI (dashboards, relatórios, aplicativos), bem como os resultados que mostram as páginas do relatório de otimização do Cortana para palavras-chave específicas.
* **Compartilhamento de usuário externo** – o compartilhamento é permitido dentro de um locatário do Power BI e, a partir de junho de 2018, também será possível compartilhar com usuários fora do seu locatário do Power BI. Veja [Distribuição do conteúdo do Power BI para usuários convidados externos com o Azure AD B2B](service-admin-azure-ad-b2b.md).
* **Métricas de uso para relatórios e dashboards** – as métricas de uso não estão disponíveis para relatórios e dashboards. Os clientes podem usar dados de log de auditoria para obter informações de uso do conteúdo em sua organização.
* **Fluxos de dados** – os fluxos de dados não estão disponíveis.

Se você tem licenças Gratuitas do **Power BI** atribuídas à sua conta, essas contas estão em execução em uma versão comercial do serviço do **Power BI** e não fazem parte da oferta do **Power BI do Governo dos EUA**. Para essas contas Gratuitas, você poderá se deparar com os seguintes problemas:

* Gateway, Móvel e Desktop não podem ser autenticados
* Você não pode acessar as fontes de dados comerciais do Azure
* Arquivos PBIX devem ser carregados manualmente do comercial
* Os aplicativos móveis do Power BI não estão disponíveis

Para resolver os problemas, contate seu representante de conta.

## <a name="frequently-asked-questions-faq-for-the-us-government-version-of-the-power-bi-service"></a>Perguntas Frequentes para a versão do Governo dos EUA do serviço do Power BI
As seguintes perguntas (e respostas) são fornecidas para ajudá-lo a obter rapidamente as informações necessárias sobre o serviço.

**Pergunta:** Como migrar meus dados do **Power BI** comercial para o **serviço do Power BI** para o Governo dos EUA?

**Resposta:** O administrador deve criar uma nova instância do **Power BI** em uma assinatura específica e separada do Governo dos EUA. Você poderá replicar seus dados comerciais no **serviço do Power BI** para o Governo dos EUA, remover sua licença comercial e associar seu domínio existente ao novo serviço específico para o Governo dos EUA.

**Pergunta:** Por que não consigo me conectar a um pacote de conteúdo específico?

**Resposta:** Garanta que a sua assinatura esteja habilitada para poder se conectar a esse pacote de conteúdo.

**Pergunta:** Estou interessado em obter o **Power BI** para minha organização do Governo dos EUA. Como fazer para começar?

**Resposta:** A inscrição (geralmente chamada de *integração*) pode ser diferente, dependendo da licença e da assinatura existentes. Consulte o artigo [Inscrever-se no Power BI para o Governo dos EUA](service-govus-signup.md) para obter mais informações.

**Pergunta:** A URL para conectar-se ao **Power BI** para o Governo dos EUA é diferente da URL do **Power BI** comercial?

**Resposta:** Sim, as URLs são diferentes. A tabela a seguir mostra cada URL:

| URL da versão comercial | URL de versão do Governo dos EUA |
| --- | --- |
| https://app.powerbi.com/ |[https://app.powerbigov.us](https://app.powerbigov.us) |

**Pergunta:** Minha conta é provisionada em mais de uma nuvem nacional. Ao usar o **Power BI Desktop**, como fazer para selecionar a nuvem a qual posso me conectar?

**Resposta:** A partir da versão de julho de 2018 do **Power BI Desktop**, é possível escolher qual nuvem deseja usar ao entrar no **Power BI Desktop**.


## <a name="next-steps"></a>Próximas etapas
Você pode fazer muito com o Power BI. Para obter mais informações e aprendizado, incluindo um artigo que mostra como se inscrever para o serviço, confira os seguintes recursos:

* [Inscrever-se para o Power BI para o Governo dos EUA](service-govus-signup.md)
* <a href="https://channel9.msdn.com/Blogs/Azure/Cognitive-Services-HDInsight-and-Power-BI-on-Azure-Government">Demonstração do governo dos EUA do Power BI</a>
* [Aprendizagem Orientada para o Power BI](guided-learning/gettingstarted.yml?tutorial-step=1)
* [Introdução ao serviço do Power BI](service-get-started.md)
* [O que é o Power BI Desktop?](desktop-what-is-desktop.md)

