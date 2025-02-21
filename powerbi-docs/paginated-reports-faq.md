---
title: 'Relatórios paginados no Power BI: PERGUNTAS FREQUENTES'
description: Este artigo responde a perguntas frequentes sobre relatórios paginados. Esses relatórios oferecem uma saída altamente formatada e visualmente perfeita otimizada para impressão ou geração de PDF.
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: report-builder
ms.topic: overview
ms.date: 07/15/2019
ms.openlocfilehash: 10135e0fa725cd4093802cd1416cab302174e21d
ms.sourcegitcommit: 277fadf523e2555004f074ec36054bbddec407f8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68270793"
---
# <a name="paginated-reports-in-power-bi-faq"></a>Relatórios paginados no Power BI: PERGUNTAS FREQUENTES 

Este artigo responde a perguntas frequentes sobre relatórios paginados. Esses relatórios oferecem uma saída altamente formatada e visualmente perfeita otimizada para impressão ou geração de PDF. Eles são chamados de "paginados" porque são formatados de modo a se adaptarem a várias páginas. Os relatórios paginados são baseados na tecnologia de relatório RDL no SQL Server Reporting Services. 

Este artigo responde a muitas perguntas comuns que as pessoas têm sobre relatórios paginados no Power BI Premium e sobre o Construtor de Relatórios, a ferramenta autônoma para criação de relatórios paginados. Você precisa de uma licença do Power BI Pro para publicar um relatório no serviço. É possível publicar e compartilhar relatórios paginados em Meu Workspace ou em espaços de trabalho do aplicativo, desde que o espaço de trabalho esteja em uma capacidade do Power BI Premium. 

## <a name="administration"></a>Administração

### <a name="what-size-premium-capacity-do-i-need-for-paginated-reports"></a>Qual o tamanho da capacidade Premium que preciso para relatórios paginados?

A carga de trabalho de relatórios paginados está disponível em SKUs P1 – P3.  Você também pode usá-la com SKUs A4 – A6 para cenários de inserção de SaaS.

### <a name="what-is-the-maximum-memory-threshold-i-can-put-for-paginated-reports-in-my-capacity"></a>Qual é o limite máximo de memória que posso colocar para relatórios paginados na minha capacidade?

Você pode usar até 100% da memória para essa carga de trabalho até o final de junho de 2019. 

### <a name="how-does-user-access-work-for-paginated-reports"></a>Como funciona o acesso de usuário para relatórios paginados?

O acesso do usuário para relatórios paginados é o mesmo que o acesso do usuário para todos os outros conteúdos no serviço do Power BI 

### <a name="how-do-i-turn-onoff-my-paginated-reports-workload"></a>Como fazer para ativar/desativar minha carga de trabalho de relatórios paginados?

O administrador de capacidade pode ativar ou desativar a carga de trabalho de relatórios paginados na página do portal de administração de capacidade.  Por padrão, a carga de trabalho será ativada em quaisquer novas capacidades que você criar.  

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

Você pode carregar relatórios paginados para Meu Espaço de Trabalho sem uma licença do Pro, desde que ele tenha a capacidade Premium.  No caso de outros espaços de trabalho, você deve ter uma licença do Pro para criar e publicar conteúdo para eles. Recomendamos o download e uso do Construtor de Relatórios do Power BI até mesmo sem a licença do Pro, mas saiba que não será possível publicar os relatórios paginados criados sem ela. 

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

### <a name="the-documentation-says-power-bi-report-builder-is-the-preferred-authoring-tool-can-i-create-paginated-reports-in-sql-server-data-tools-for-power-bi"></a>A documentação indica que o Construtor de Relatórios do Power BI é a ferramenta de criação de preferência. Posso criar relatórios paginados no SQL Server Data Tools para o Power BI?

Sim, mas o serviço do Power BI só permite fazer upload de um único item por vez, portanto, ainda não há suporte para muitos dos autores de cenários usados ​​com o SQL Server Data Tools (SSDT). Confira a [lista completa de recursos sem suporte](#what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi) disponíveis posteriormente nesta seção de perguntas frequentes.  

### <a name="what-versions-of-report-builder-do-you-support"></a>Quais versões do Construtor de Relatórios têm suporte?

Recentemente, lançamos o Construtor de Relatórios do Power BI como a principal ferramenta de criação para relatórios paginados no serviço do Power BI. Instale o [Construtor de Relatórios do Power BI no Centro de Download da Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513).

### <a name="how-do-i-move-existing-reports-i-have-saved-in-sql-server-reporting-services-to-power-bi"></a>Como fazer para mover os relatórios existentes que salvei no SQL Server Reporting Services para o Power BI?

É preciso fazer o download do relatório do servidor e o upload para o Power BI por meio do portal.  Não há uma ferramenta de migração disponível no momento, mas estamos pensando em criar uma, depois que terminarmos a versão prévia pública e obtivermos o nível certo de paridade de recursos entre os produtos.

### <a name="can-i-open-reports-and-publish-directly-to-the-service"></a>Posso abrir relatórios e publicar diretamente no serviço?

Sim. Vamos adicionar suporte para abrir relatórios e publicá-los diretamente para o serviço no Construtor de Relatórios do Power BI.

### <a name="what-paginated-report-features-in-ssrs-arent-yet-supported-in-power-bi"></a>Quais recursos de relatório paginados no SSRS ainda não são compatíveis com o Power BI?

Atualmente, os relatórios paginados não oferecem suporte aos seguintes itens:

- Fontes de dados compartilhados
- Conjuntos de dados compartilhados
- Sub-relatórios
- Detalhamento e ações de clique para outros relatórios
- Relatórios vinculados
- Camadas do mapa do Bing
- Fontes personalizadas

Você recebe uma mensagem de erro se tentar carregar um arquivo que tenha um recurso não suportado no serviço do Power BI, que não seja alternar/classificar.

### <a name="what-data-sources-do-you-support-currently-for-paginated-reports"></a>Quais fontes de dados têm suporte atualmente para relatórios paginados?

Damos suporte para as seguintes fontes de dados - 

- Conjuntos de dados do Power BI (por meio de SSO (logon único))
- Azure Analysis Services (por meio de logon único (SSO) e oAuth)
- SQL Data Warehouse do Azure
- Banco de Dados SQL do Azure (nome de usuário/senha, SSO e oAuth)
- SQL Server*
- Modelos de tabela (DAX) e multidimensionais (MDX) do SQL Server Analysis Services (SSAS)* 
- Oracle* 
- Teradata* 

* exige o Gateway local.

Ao acessar o SSAS por meio do gateway, o usuário cujas credenciais estão armazenadas precisa de permissões elevadas no SSAS para trabalhar no gateway.

### <a name="what-authentication-methods-do-you-support"></a>Quais métodos de autenticação têm suporte?

Damos suporte ao SSO para o Azure Analysis Services, o Banco de Dados SQL do Azure e fontes de dados do Power BI.  Também damos suporte a OAuth para o Banco de Dados SQL do Azure e o Azure Analysis Services.  Para as outras fontes de dados, você precisa armazenar um nome de usuário e uma senha com a fonte de dados no portal ou gateway.  

### <a name="can-i-use-a-power-bi-dataset-as-a-data-source-for-my-paginated-report"></a>Posso usar um conjunto de dados do Power BI como fonte de dados para meu relatório paginado?

Sim, damos suporte a conjuntos de dados do Power BI como fontes de dados para seus relatórios paginados.

### <a name="can-i-use-stored-procedures-through-the-gateway"></a>Posso usar procedimentos armazenados pelo gateway?

Você pode usar um procedimento armazenado por meio do Gateway, mas talvez você tenha problemas em determinados cenários se o procedimento armazenado tiver parâmetros.

### <a name="what-export-formats-are-available-for-my-report-in-the-power-bi-service"></a>Quais formatos de exportação estão disponíveis para o meu relatório no serviço do Power BI?

Você pode exportar para Microsoft Excel, Microsoft Word, Microsoft PowerPoint, PDF, .CSV, XML e MHTML.

### <a name="can-i-print-paginated-reports"></a>Posso imprimir relatórios paginados?

Sim, a impressão está disponível para relatórios paginados, incluindo uma experiência de visualização de impressão nova e aprimorada. 

### <a name="are-e-mail-subscriptions-available-yet-for-paginated-reports"></a>As assinaturas de email ainda estão disponíveis para relatórios paginados?

Sim, as assinaturas de email são totalmente compatíveis com relatórios paginados e incluem suporte para seis diferentes formatos de arquivo e valores de parâmetro.

### <a name="can-i-run-custom-code-in-my-report"></a>Posso executar um código personalizado no meu relatório?

Sim, oferecemos suporte à capacidade de executar código em seus relatórios, como no SSRS.

### <a name="can-i-use-power-bi-embedded-to-embed-my-paginated-reports-into-an-app-im-hosting"></a>Posso usar o Power BI Embedded para inserir meus relatórios paginados em um aplicativo que estou hospedando?

A inserção de SaaS terá suporte no decorrer de junho.  Planejamos dar suporte também à inserção de PaaS com as APIs do Power BI, mas ainda não definimos um prazo para disponibilizar esse cenário.

### <a name="can-i-drill-through-from-a-power-bi-report-to-a-paginated-report"></a>Posso fazer uma consulta detalhada de um relatório do Power BI para um relatório paginado?

Ainda não, mas com certeza planejamos oferecer suporte a este cenário.

### <a name="can-i-share-my-paginated-report-content-through-a-power-bi-app"></a>Posso compartilhar meu conteúdo de relatório paginado por meio de um aplicativo do Power BI?

Sim, os relatórios paginados podem ser implantados com os aplicativos de espaço de trabalho v1 e v2. 

### <a name="will-other-report-specific-features-in-power-bi-like-pinning-to-report-tiles-to-dashboards-work-with-paginated-reports"></a>Outros recursos específicos de relatório no Power BI, como a fixação de relatórios de blocos a painéis, funcionam com relatórios paginados?

A intenção é que os relatórios suportem os mesmos cenários principais no serviço, tanto quanto possível.  Idealmente, embora a ferramenta para criá-los seja diferente, na perspectiva do consumidor, é apenas outro relatório na lista deles no portal. Eles não se importam com a forma como foram criados, conseguem fazer o que precisam.  Um bom exemplo dessa paridade de recursos é o suporte ao comentário planejado. Embora o recurso em si possa funcionar de forma um pouco diferente para cada tipo de relatório, você poderá usar comentários para ambos.

### <a name="is-a-migration-tool-planned-so-ssrs-customers-can-move-their-existing-reports-and-assets-to-power-bi"></a>É uma ferramenta de migração planejada para que os clientes do SSRS possam mover seus relatórios e ativos existentes para o Power BI?

Estamos avaliando opções para permitir que o conteúdo seja movido para o Power BI de maneira automatizada, mas isso não estará disponível até depois da GA.

### <a name="is-there-a-report-viewer-control-for-paginated-reports-in-the-power-bi-service"></a>Existe um controle de visualizador de relatórios para relatórios paginados no serviço do Power BI?

Não, um controle de visualizador de relatório não está disponível atualmente.

### <a name="can-you-search-for-paginated-reports-from-the-new-home-experience-in-the-power-bi-service"></a>Você pode pesquisar relatórios paginados a partir da nova experiência inicial no serviço do Power BI?

Sim, agora é possível pesquisar seus relatórios paginados na Página Inicial.  Também é possível vê-los em outras partes da nova experiência com a Página Inicial.

## <a name="next-steps"></a>Próximas etapas

- [Instale o Construtor de Relatórios do Power BI no Centro de Download da Microsoft](https://go.microsoft.com/fwlink/?linkid=2086513)
- [Tutorial: Criar um relatório paginado](paginated-reports-quickstart-aw.md)
