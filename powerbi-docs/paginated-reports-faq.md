---
title: 'Relatórios paginados no Power BI: Perguntas frequentes (versão prévia)'
description: Este artigo responde a perguntas frequentes sobre relatórios paginados. Esses relatórios oferecem uma saída altamente formatada e visualmente perfeita otimizada para impressão ou geração de PDF.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 11/05/2018
ms.author: maggies
ms.openlocfilehash: d86f52b45dfac4252dfd2e7de29de64c16a566ca
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54293999"
---
# <a name="paginated-reports-in-power-bi-faq-preview"></a>Relatórios paginados no Power BI: Perguntas frequentes (versão prévia)

Este artigo responde a perguntas frequentes sobre relatórios paginados. Esses relatórios oferecem uma saída altamente formatada e visualmente perfeita otimizada para impressão ou geração de PDF. Eles são chamados de "paginados" porque são formatados de modo a se adaptarem a várias páginas. Os relatórios paginados são baseados na tecnologia de relatório RDL no SQL Server Reporting Services. 

Este artigo responde a muitas perguntas comuns que as pessoas têm sobre relatórios paginados no Power BI Premium e sobre o Construtor de Relatórios, a ferramenta autônoma para criação de relatórios paginados. Você precisa de uma licença do Power BI Pro para publicar um relatório no serviço. É possível publicar e compartilhar relatórios paginados em Meu Workspace ou em espaços de trabalho do aplicativo, desde que o espaço de trabalho esteja em uma capacidade do Power BI Premium. 

## <a name="administration"></a>Administração

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Qual o tamanho da capacidade Premium que preciso para relatórios paginados?

A carga de trabalho de relatórios paginados está disponível em SKUs P1 – P3 para versão prévia pública.  Você também pode usá-la para cenários de teste/desenvolvimento com SKUs A4 – A6.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Qual é o limite máximo de memória que posso colocar para relatórios paginados na minha capacidade?

No momento, você só pode reservar 50% da memória para essa carga de trabalho. 

### <a name="how-does-user-access-work-for-paginated-reports"></a>Como funciona o acesso de usuário para relatórios paginados?

O acesso do usuário para relatórios paginados é o mesmo que o acesso do usuário para todos os outros conteúdos no serviço do Power BI 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Como fazer para ativar/desativar minha carga de trabalho de relatórios paginados?

O administrador de capacidade pode ativar ou desativar a carga de trabalho de relatórios paginados na página do portal de administração de capacidade.  

### <a name="how-can-i-monitor-usage-of-paginated-reports-in-my-tenant"></a>Como posso monitorar o uso de relatórios paginados no meu locatário?

Os logs de auditoria do Office 365 detalham o uso desse tipo de relatório nos seguintes eventos: 

- Exibir relatório do Power BI
- Excluir relatório do Power BI
- Criar relatório do Power BI
- Relatório do Power BI baixado

O campo ReportType tem o valor “PaginatedReport” para identificar os relatórios paginados, em oposição aos relatórios do Power BI.

Além disso, os logs de auditoria fornecem os seguintes eventos para relatórios paginados:

- Conjunto de dados do Power BI associado ao gateway
- Descobrir a fonte de dados do Power BI
- TakeOverDatasource

### <a name="can-i-monitor-this-workload-through-the-premium-capacity-monitoring-app"></a>Posso monitorar essa carga de trabalho por meio do aplicativo de Monitoramento da Capacidade Premium?

Sim, o monitoramento está disponível como uma nova guia com os mesmos detalhes relevantes para seus conjuntos de dados do Power BI.

### <a name="do-i-need-a-pro-license-to-create-and-publish-paginated-reports"></a>Preciso de uma licença Pro para criar e publicar relatórios paginados?

Sim. Não é possível enviar relatórios para o espaço de trabalho sem uma licença Pro. Você pode fazer o download e experimentar o Construtor de Relatórios sem a licença Pro, mas não publicar os relatórios paginados criados. 

### <a name="what-if-i-have-a-paginated-report-in-a-workspace-and-the-paginated-report-workload-is-turned-off"></a>E se eu tiver um relatório paginado em um espaço de trabalho e a carga de trabalho de relatório paginado estiver desativada?

Você recebe uma mensagem de erro e não pode exibir seu relatório até que a carga de trabalho seja ativada novamente. Você pode ainda excluir o relatório do espaço de trabalho.

### <a name="what-is-the-default-memory-for-each-of-the-premium-skus-supported-for-paginated-reports"></a>Qual é a memória padrão para cada um dos SKUs Premium compatíveis com relatórios paginados?

Memória padrão em cada SKU Premium para relatórios paginados:

- **P1/A4**: Padrão de 20%; mínimo de 10%
- **P2/A5**: Padrão de 20%; mínimo de 5%
- **P3/A6**: Padrão de 20%; mínimo de 2,5%

## <a name="general"></a>Geral

### <a name="when-should-i-use-a-paginated-report-vs-a-power-bi-report"></a>Quando devo usar um relatório paginado ao invés de um relatório do Power BI?

Os relatórios paginados são melhores para cenários que exigem uma saída altamente formatada e visualmente perfeita otimizada para impressão ou geração de PDF.  Um demonstrativo de resultados é um bom exemplo do tipo de relatório que você provavelmente deseja criar como um relatório paginado.  

Os relatórios do Power BI são otimizados para exploração e interatividade.  Um relatório de vendas em que diferentes vendedores desejam dividir os dados no mesmo relatório para sua região/setor/cliente específico e ver como a alteração dos números seria melhor atendida por um relatório do Power BI.

### <a name="the-documentation-says-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>A documentação indica que o Construtor de Relatórios é a ferramenta de criação de preferência. Posso criar relatórios paginados no SQL Server Data Tools para o Power BI?

Sim, mas o serviço do Power BI só permite fazer upload de um único item por vez, portanto, ainda não há suporte para muitos dos autores de cenários usados ​​com o SQL Server Data Tools (SSDT). Confira a [lista completa de recursos sem suporte](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) disponíveis posteriormente nesta seção de perguntas frequentes.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Quais versões do Construtor de Relatórios têm suporte?

Use a versão mais recente do Construtor de Relatórios do SQL Server 2016 para criar e publicar seus relatórios no serviço do Power BI. Instale o [Construtor de Relatórios no Centro de Download da Microsoft](https://www.microsoft.com/download/details.aspx?id=53613).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Como fazer para mover os relatórios existentes que salvei no SQL Server Reporting Services para o Power BI?

É preciso fazer o download do relatório do servidor e o upload para o Power BI por meio do portal.  Não há uma ferramenta de migração disponível no momento, mas estamos pensando em criar uma, depois que terminarmos a versão prévia pública e obtivermos o nível certo de paridade de recursos entre os produtos.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Posso abrir relatórios e publicar diretamente no serviço?

Neste ponto, não. Vamos adicionar suporte para abrir relatórios e publicá-los diretamente para o serviço no Construtor de Relatórios no futuro, assim como acontece com o Power BI Desktop.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Quais recursos de relatório paginados no SSRS ainda não são compatíveis com o Power BI?

Atualmente, os relatórios paginados não oferecem suporte aos seguintes itens:

- Fontes de dados compartilhados
- Conjuntos de dados compartilhados
- Sub-relatórios
- Ações de clique e detalhamento
- Relatórios vinculados
- Indicadores
- Camadas do mapa do Bing
- Fontes personalizadas

Você recebe uma mensagem de erro se tentar carregar um arquivo que tenha um recurso não suportado no serviço do Power BI, que não seja alternar/classificar.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Quais fontes de dados têm suporte atualmente para relatórios paginados?

Damos suporte ao Banco de Dados SQL do Azure, ao SQL Server e aos modelos de tabela (DAX) e multidimensionais (MDX) do SSAS (SQL Server Analysis Services) usando o gateway local.

Ao acessar o SSAS por meio do gateway, o usuário cujas credenciais estão armazenadas precisa de permissões elevadas no SSAS para trabalhar no gateway.

### <a name="what-authentication-methods-do-you-support"></a>Quais métodos de autenticação têm suporte?

Atualmente, você precisa armazenar um nome de usuário e senha com a fonte de dados no portal ou gateway.  Métodos de autenticação adicionais para oferecer suporte a itens como a segurança de nível de linha serão apresentados posteriormente na versão prévia.

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Posso usar um conjunto de dados do Power BI como fonte de dados para meu relatório paginado?

Ainda não, mas esse suporte está previsto para breve.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Posso usar procedimentos armazenados pelo gateway?

Você pode usar um procedimento armazenado por meio do Gateway, mas talvez você tenha problemas em determinados cenários se o procedimento armazenado tiver parâmetros.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Quais formatos de exportação estão disponíveis para o meu relatório no serviço do Power BI?

Você pode exportar para Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, .CSV, XML e MHTML.

### <a name="can-i-print-paginated-reports"></a>Posso imprimir relatórios paginados?

Sim, a impressão está disponível para relatórios paginados, incluindo uma experiência de visualização de impressão nova e aprimorada. 

### <a name="are-e-mail-subscriptions-available-yet-for-paginated-reports"></a>As assinaturas de email ainda estão disponíveis para relatórios paginados?

Não, as assinaturas de email chegarão em breve, contudo.

### <a name="what-features-from-ssrs-will-you-be-supporting-in-the-power-bi-service"></a>Quais recursos do SSRS terão suporte no serviço do Power BI?

Nosso plano é fornecer paridade de recursos para a maioria dos cenários, mas algumas coisas sobre o SSRS e o Power BI talvez não façam sentido para tentar alterar de acordo com os padrões de SSRS existentes.  Por exemplo, os modelos de permissão diferentes no Power BI não podem ser mapeados para o SSRS.  Gostaríamos de receber comentários de clientes e parceiros para tomar esses tipos de decisões.

### <a name="can-i-run-custom-code-in-my-report"></a>Posso executar um código personalizado no meu relatório?

Sim, oferecemos suporte à capacidade de executar código em seus relatórios, como no SSRS.

### <a name="does-this-mean-ssrs-is-going-away"></a>Isso significa que o SSRS está acabando?

De modo algum.  Essa nova oferta oferece aos clientes uma opção baseada em nuvem para seus relatórios paginados.  

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Posso usar o Power BI Embedded para inserir meus relatórios paginados em um aplicativo que estou hospedando?

Planejamos dar suporte a esse cenário com as APIs do Power BI existentes, mas ainda não temos um prazo de quando esse cenário estará disponível.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Posso fazer uma consulta detalhada de um relatório do Power BI para um relatório paginado?

Ainda não, mas com certeza planejamos oferecer suporte a este cenário.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Posso compartilhar meu conteúdo de relatório paginado por meio de um aplicativo do Power BI?

No momento, você pode compartilhar relatórios paginados individuais com outros usuários por meio da ação de compartilhamento no portal ou por meio da barra de ferramentas. Ainda não oferecemos suporte ao compartilhamento em um aplicativo, mas esperamos fazer isso em breve. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>Outros recursos específicos de relatório no Power BI, como a fixação de relatórios de blocos a painéis, funcionam com relatórios paginados?

A intenção é que os relatórios suportem os mesmos cenários principais no serviço, tanto quanto possível.  Idealmente, embora a ferramenta para criá-los seja diferente, na perspectiva do consumidor, é apenas outro relatório na lista deles no portal. Eles não se importam com a forma como foram criados, conseguem fazer o que precisam.  Um bom exemplo dessa paridade de recursos é o suporte ao comentário planejado. Embora o recurso em si possa funcionar de forma um pouco diferente para cada tipo de relatório, você poderá usar comentários para ambos.

### <a name="are-you-planning-to-create-a-new-authoring-tool-for-paginated-reports-in-the-power-bi-service--we-cant-do-everything-we-need-to-with-report-builder-today"></a>Há planos para a criação de uma nova ferramenta de criação para relatórios paginados no serviço do Power BI?  Não conseguimos fazer tudo o que precisamos no Construtor de Relatórios hoje.

Ainda estamos observando diferentes opções aqui para a melhor história de ferramentas para relatórios paginados no Power BI. 

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>É uma ferramenta de migração planejada para que os clientes do SSRS possam mover seus relatórios e ativos existentes para o Power BI?

Estamos avaliando opções para permitir que o conteúdo seja movido para o Power BI de maneira automatizada, mas isso não estará disponível até depois da GA.

### <a name="will-i-ever-be-able-to-create-both-paginated-reports-and-power-bi-reports-in-a-single-authoring-tool"></a>No futuro poderei criar relatórios paginados e relatórios do Power BI em uma única ferramenta de criação?

Potencialmente.  No momento, estamos procurando maneiras de permitir esse cenário ou se simplesmente distribuirmos as ferramentas de criação como um único pacote de BI em vez de contar com downloads/marcas individuais.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Existe um controle de visualizador de relatórios para relatórios paginados no serviço do Power BI?

Não, um controle de visualizador de relatório não está disponível atualmente.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Você pode pesquisar relatórios paginados a partir da nova experiência inicial no serviço do Power BI?

Não, não é possível pesquisar seus relatórios paginados a partir da Página Inicial no momento.  No entanto, é possível vê-los em outras partes da nova experiência Página Inicial.

## <a name="next-steps"></a>Próximas etapas

- [Instalar o Construtor de Relatórios no Centro de Download da Microsoft](https://www.microsoft.com/download/details.aspx?id=53613)
- [Tutorial: Criar um relatório paginado](paginated-reports-quickstart-aw.md)
