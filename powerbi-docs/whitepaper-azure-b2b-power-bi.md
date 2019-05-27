---
title: Distribuir o conteúdo do Power BI para usuários convidados externo com o Azure Active Directory B2B
description: White paper que descreve como usar o Azure Active Directory B2B para distribuir o Power BI para usuários convidados externo
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 03/07/2019
ms.author: davidi
LocalizationGroup: Conceptual
ms.openlocfilehash: 79b8ae80413cc54b065d12bf36ccb1651a670812
ms.sourcegitcommit: ec5b6a9f87bc098a85c0f4607ca7f6e2287df1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66051590"
---
# <a name="distribute-power-bi-content-to-external-guest-users-using-azure-active-directory-b2b"></a>Distribuir o conteúdo do Power BI para usuários convidados externo com o Azure Active Directory B2B

**Resumo:** Este é um white paper técnico explicando como distribuir conteúdo para usuários fora da organização usando a integração do Azure Active Directory Business-to-business (B2B do AD do Azure).

**Gravadores de:** Lukasz Pawlowski, Kasper de Jonge

**Revisores técnicos:** ADAM Wilson, Sheng Liu, Qian Liang, Sergei Gundorov, Jacob Grimm, Adam Saxton, Shenhav Maya, Nimrod Shalit, Elisabeth Olson

> [!NOTE]
> Você pode salvar ou imprimir este whitepaper selecionando **Imprimir** no seu navegador e, em seguida, selecionando **Salvar como PDF**.

## <a name="introduction"></a>Introdução

Power BI oferece às organizações um modo de exibição de 360 graus de seus negócios e capacita todos para tomar decisões inteligentes usando dados dessas organizações. Muitas dessas organizações têm relações confiáveis e de alta seguras com parceiros externos, clientes e prestadores de serviço. Essas organizações precisam para fornecer acesso seguro aos painéis do Power BI e relatórios para usuários nesses parceiros externos.

Power BI integra [Azure Active Directory Business-to-business (B2B do AD do Azure)](https://docs.microsoft.com/azure/active-directory/b2b/what-is-b2b) para permitir distribuição segura do Power BI conteúdo aos usuários convidados fora da organização – enquanto ainda mantém o controle e que controlam o acesso aos dados internos.

Este white paper aborda os todos os detalhes que é necessário compreender a integração do Power BI com o Azure Active Directory B2B. Abordaremos o seu caso de uso mais comum, a instalação, licenciamento e segurança em nível de linha.

> [!NOTE]
> Em todo este white paper, chamamos o Azure Active Directory como o Azure AD e o Azure Active Directory empresas como o Azure AD B2B.

## <a name="scenarios"></a>Cenários

A Contoso é um fabricante automotivo e funciona com muitos fornecedores diferentes que fornecem-lo com os componentes, materiais e serviços necessários para executar suas operações de manufatura. A Contoso deseja simplificar seu logística de cadeia de suprimentos e os planos para usar o Power BI para monitorar as principais métricas de desempenho de sua cadeia de fornecimento. A Contoso deseja compartilhar com a análise de parceiros de cadeia de fornecedores externos de forma segura e gerenciável.

A Contoso pode habilitar as seguintes experiências para usuários externos usando o Power BI e o Azure AD B2B.

### <a name="ad-hoc-per-item-sharing"></a>Ad hoc por compartilhamento de itens

A Contoso funciona com um fornecedor que compila radiadores para carros da Contoso. Geralmente, eles precisam otimizar a confiabilidade dos radiadores usando dados de todos os carros da Contoso. Um analista de Contoso usa o Power BI para compartilhar um relatório de confiabilidade radiador com um engenheiro do fornecedor. O engenheiro recebe um email com um link para exibir o relatório.

Conforme descrito acima, esse compartilhamento ad hoc é executada por usuários de negócios no conforme necessário. O link enviado pelo Power BI para o usuário externo é um link de convite B2B do AD do Azure. Quando o usuário externo é aberto no link, será solicitado que ele ingressar a organização do Azure AD da Contoso como um usuário convidado. Depois que o convite é aceita, o link abre o painel ou relatório específico. O administrador do Azure Active Directory delega a permissão para convidar usuários externos à organização e escolhe o que esses usuários podem fazer quando eles aceitarem o convite, conforme descrito na seção de governança deste documento. O analista de Contoso pode convidar o usuário convidado só porque o administrador do Azure AD permitido essa ação e o Power BI administrador de usuários permitido para convidar convidados para exibir o conteúdo em configurações de locatário do Power BI.

![Convidar convidados para o Power BI usando o AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_01.png)

1. O processo começa com um usuário interno da Contoso compartilhar um dashboard ou relatório com um usuário externo. Se o usuário externo não já é um convidado no Azure da Contoso AD, eles são convidados. Um email é enviado para seu endereço de email que inclui um convite para o Azure do Contoso AD
2. O destinatário aceita o convite para a Contoso do Azure AD e é adicionado como um usuário convidado no Azure da Contoso AD.
3. O destinatário, em seguida, será redirecionado para o painel do Power BI, relatório ou aplicativo, que são somente leitura para o usuário.

O processo é considerado ad-hoc, pois os usuários corporativos da Contoso executam a ação de convite, conforme necessário para seus objetivos de negócios. Cada item compartilhado é um único link que o usuário externo pode acessar para exibir o conteúdo.

Depois que o usuário externo foi convidado para acessar recursos da Contoso, uma conta de sombra pode ser criada para eles no Azure AD da Contoso e não precisam ser convidado novamente.  Na primeira vez que tentarem acessar um recurso de Contoso como um dashboard do Power BI, eles passarem por um processo de consentimento que resgata o convite.  Se não concluírem o consentimento, eles não conseguir acessar nenhum conteúdo da Contoso.  Se eles tiverem problemas para resgatar o convite por meio do link original fornecido, o administrador do Azure AD pode reenviadas um link de convite específico para que eles resgatar.

### <a name="planned-per-item-sharing"></a>Planejado por compartilhamento de itens

A Contoso funciona com uma prestadora de serviço para executar a análise de confiabilidade do radiadores. A prestadora de serviço tem uma equipe de 10 pessoas que precisam de acesso a dados no ambiente do Power BI da Contoso. O administrador da Contoso do Azure AD está envolvido para convidar todos os usuários e para lidar com quaisquer adições/alterações como funcionário na alteração de prestadora de serviço. O administrador do AD do Azure cria um grupo de segurança para todos os funcionários em subcontratado. Usando o grupo de segurança, os funcionários da Contoso podem facilmente gerenciar o acesso a relatórios e garantir que todos os funcionários prestadora de serviço necessários tenham acesso para todos os relatórios necessários, painéis e aplicativos do Power BI. O administrador do AD do Azure também pode evitar que está sendo envolvidos no processo de convite completamente escolhendo delegar direitos de convite para um funcionário confiável na Contoso, ou em subcontratado para garantir que os funcionários em tempo hábil gerenciamento.

Algumas organizações exigem mais controle sobre quando os usuários externos são adicionados, convidando muitos usuários em uma organização externa, ou muitas organizações externas. Nesses casos, o compartilhamento planejado pode ser usado para gerenciar a escala de compartilhamento, para impor as políticas organizacionais e até mesmo delegar direitos somente a pessoas confiáveis para convidar e gerenciar usuários externos. B2B do AD do Azure dá suporte a convites planejados sejam enviadas diretamente [do portal do Azure por um administrador de TI](https://docs.microsoft.com/azure/active-directory/b2b/add-users-administrator), ou por meio das [PowerShell usando a API do Gerenciador de convite](https://docs.microsoft.com/azure/active-directory/b2b/customize-invitation-api) onde um conjunto de usuários pode ser convidado em um ação. Usar o planejado convida abordagem, a organização pode controlar quem pode convidar usuários e implementar processos de aprovação. Azure AD com recursos avançados, como grupos dinâmicos podem tornar fácil manter a associação de grupo de segurança automaticamente.


![Controle quais convidados podem ver o conteúdo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_02.png)



1. As estrelas de processo com um administrador de TI convidar o usuário convidado manualmente ou por meio da API fornecido pelo Azure Active Directory
2. O usuário aceitar o convite para a organização.
3. Depois que o usuário aceitou o convite, um usuário no Power BI pode compartilhar um relatório ou painel com o usuário externo, ou eles estão em um grupo de segurança. Assim como o compartilhamento regular do Power BI, o usuário externo receberá um email com o link para o item.
4. Quando os acessos de usuário externo no link, a autenticação em seu diretório é passado para a Contoso do Azure AD e usado para obter acesso ao conteúdo do Power BI.

### <a name="ad-hoc-or-planned-sharing-of-power-bi-apps"></a>Ad hoc ou planejado para o compartilhamento de aplicativos do Power BI

A Contoso tem um conjunto de relatórios e painéis que eles precisam compartilhar com um ou mais fornecedores. Para garantir que todos os usuários externos necessários tenham acesso a esse conteúdo, ele é empacotado como um aplicativo do Power BI. Os usuários externos são adicionados diretamente para a lista de acesso do aplicativo ou por meio de grupos de segurança. Alguém na Contoso, em seguida, envia a URL do aplicativo para todos os usuários externos, por exemplo, em um email. Quando os usuários externos abrirem o link, eles veem todo o conteúdo em um único fácil a experiência de navegação.

Usar um aplicativo do Power BI torna fácil para a Contoso criar um Portal de BI para seus fornecedores. Uma lista de acesso único controla o acesso a todo o conteúdo necessário reduzir o desperdício de tempo de verificação e definindo permissões de nível de item. B2B do AD do Azure mantém o acesso de segurança usando a identidade de nativa do fornecedor para que os usuários não precisam de credenciais de logon adicionais. Se o uso planejado convida com grupos de segurança, gerenciamento de acesso para o aplicativo conforme pessoal gira dentro ou fora do projeto é simplificado. Manualmente ou por meio de grupos de associação em segurança [grupos dinâmicos](https://docs.microsoft.com/azure/active-directory/b2b/use-dynamic-groups), de modo que todos os usuários externos de um fornecedor são automaticamente adicionados ao grupo de segurança apropriado.


![Controle de conteúdo com o AAD](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_03.png)

1. O processo é iniciado pelo usuário que está sendo convidado a organização do Azure AD da Contoso por meio do portal do Azure ou PowerShell
2. O usuário pode ser adicionado a um grupo de usuários no AD do Azure. Um grupo de usuários estático ou dinâmico pode ser usado, mas os grupos dinâmicos ajudar a reduzir o trabalho manual.
3. Os usuários externos recebem acesso para o aplicativo do Power BI por meio do grupo de usuários. O aplicativo de URL deve ser enviada diretamente para o usuário externo ou colocada em um site, eles têm acesso ao. Power BI se esforça para enviar um email com o link do aplicativo para usuários externos, mas ao usar grupos de usuários cujos membros podem alterar, o Power BI não é capaz de enviar para todos os usuários externos gerenciados por meio de grupos de usuários.
4. Quando o usuário externo acesse a URL do aplicativo do Power BI, eles são autenticados pelo Azure da Contoso AD, o aplicativo é instalado para o usuário e o usuário pode ver todos os relatórios contidos e painéis no aplicativo.

Aplicativos também terão um recurso exclusivo que permite que os autores de aplicativo instalar o aplicativo automaticamente para o usuário, para que ele esteja disponível quando o usuário fizer logon. Esse recurso só instala automaticamente para usuários externos que já fazem parte da organização da Contoso no momento em que o aplicativo é publicado ou atualizado. Portanto, ele é melhor usado com a abordagem de convites planejados e depende do aplicativo que está sendo publicada ou atualizada depois que os usuários são adicionados ao Azure da Contoso AD. Os usuários externos sempre poderá instalar o aplicativo usando o link do aplicativo.

### <a name="commenting-and-subscribing-to-content-across-organizations"></a>Os comentários e assinando conteúdo entre organizações

Como a Contoso continua a trabalhar com seus prestadores de serviço ou fornecedores, os engenheiros externos precisam trabalhar em sintonia com analistas da Contoso. O Power BI fornece vários recursos de colaboração que ajudam os usuários a se comunicar sobre o conteúdo que podem consumir. Painel de comentário (e os comentários de relatórios em breve) permite que os usuários discutir pontos de dados que eles vejam e se comuniquem com os autores de relatório para fazer perguntas.

Atualmente, os usuários convidados externo podem participar em comentários deixar comentários e lendo as respostas. No entanto, ao contrário de usuários internos, os usuários convidados não podem ser @mentioned e não recebe notificações de que receberam um comentário. Usuários convidados não podem usar o recurso de assinaturas no Power BI no momento da gravação. Em uma versão futura, essas restrições serão eliminadas e o usuário convidado receberá um email quando um comentário @mentions -los, ou quando uma assinatura é entregue ao seu email que contém um link para o conteúdo no Power BI.

### <a name="access-content-in-the-power-bi-mobile-apps"></a>Acessar o conteúdo nos aplicativos móveis do Power BI

Em uma versão futura, quando os usuários da Contoso compartilham relatórios ou painéis com suas contrapartes do convidado externos, o Power BI enviará um email notificando o convidado. Quando o usuário convidado é aberto o link para o relatório ou dashboard em seu dispositivo móvel, o conteúdo será aberto nos aplicativos móveis do Power BI nativos em seu dispositivo, se eles estão instalados. O usuário convidado, em seguida, poderá navegar entre o conteúdo compartilhado com eles no locatário externo e de volta para seu próprio conteúdo de seu locatário inicial.

> [!NOTE]
> O usuário convidado não é possível abrir o aplicativo móvel do Power BI e imediatamente navegue até o locatário externo, eles devem começar com um link para um item no locatário externo. Soluções alternativas comuns são descritas as [distribuindo links para conteúdo no Power BI da organização pai](#distributing-links-to-content-in-the-parent-organizations-power-bi) seção mais adiante neste documento.

### <a name="cross-organization-editing-and-management-of-power-bi-content"></a>Entre organizações de edição e o gerenciamento de conteúdo do Power BI

A Contoso e seus fornecedores e prestadores de serviço funcionam cada vez mais próximas uma da outra. Geralmente um analista de subcontratado precisa visualizações de métricas ou dados adicionais a serem adicionados a um relatório que Contoso compartilhou com eles. Os dados devem residir no locatário do Power BI da Contoso, mas os usuários externos devem ser capazes de editá-lo, crie um novo conteúdo e até mesmo distribuí-lo para pessoas apropriadas.

O Power BI fornece uma opção que permite **usuários convidados externo podem editar e gerenciar conteúdo** na organização. Por padrão, os usuários externos têm uma experiência orientada para o consumo de somente leitura. No entanto, essa nova configuração permite que o administrador do Power BI escolher quais usuários externos podem editar e gerenciar conteúdo em sua própria organização. Depois que o permitido, o usuário externo pode editar relatórios, painéis, publicar ou atualizar aplicativos, trabalhar em espaços de trabalho e conecte-se aos dados que eles têm permissão para usar.

Esse cenário é descrito detalhadamente na seção habilitando os usuários externos para editar e gerenciar o conteúdo do Power BI neste documento.

## <a name="organizational-relationships-using-power-bi-and-azure-ad-b2b"></a>Relações organizacionais usando o Power BI e o Azure AD B2B

Quando todos os usuários do Power BI são internos para a organização, não é necessário usar o Azure AD B2B. No entanto, quando dois ou mais organizações querem colaborar em dados e insights, suporte do Power BI para o Azure AD B2B torna mais fácil e econômica para fazê-lo.

Abaixo estão normalmente encontradas estruturas organizacionais que são adequadas para colaboração do Azure AD B2B estilo entre organizações no Power BI. B2B do AD do Azure funciona bem na maioria dos casos, mas em algumas situações comuns abordagens alternativas abordadas no final deste documento se vale a pena considerar.

### <a name="case-1-direct-collaboration-between-organizations"></a>Caso 1: Colaboração direta entre as organizações

Relação da Contoso com seu fornecedor de radiador é um exemplo de colaboração direta entre as organizações. Uma vez que há relativamente poucos usuários da Contoso e o compartilhamento externo com base em seus fornecedores que precisam de acesso a informações de confiabilidade radiador, usando o Azure AD B2B é ideal. É fácil de usar e simples de administrar. Isso também é um padrão comum em serviços de consultoria em que um consultor pode ser necessário compilar o conteúdo para uma organização.

![Compartilhar entre organizações](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_04.png)


Normalmente, esse compartilhamento ocorre inicialmente com o Ad hoc por compartilhamento de itens. No entanto, conforme o crescem de equipes ou relações aprofundar, o planejado por compartilhamento de itens abordagem torna-se o método preferencial para reduzir a sobrecarga de gerenciamento. Além disso, o Ad hoc ou planejado de compartilhamento de aplicativos do Power BI, comentários e assinatura de conteúdo entre organizações, acesso ao conteúdo de aplicativos móveis pode vir em play também e entre organizações de edição e o gerenciamento de conteúdo do Power BI. É importante, se os usuários de ambas as organizações têm licenças do Power BI Pro em suas respectivas organizações, eles podem usar essas licenças Pro uns dos outros ambientes do Power BI. Isso fornece licenciamento vantajoso desde que a organização que convida talvez não precise pagar por uma licença do Power BI Pro para os usuários externos. Isso é discutido mais detalhadamente na seção de licenciamento neste documento.

### <a name="case-2-parent-and-its-subsidiaries-or-affiliates"></a>Caso 2: Pai e suas subsidiárias ou afiliadas

Algumas estruturas de organização são mais complexas, incluindo totalmente ou parcialmente subsidiárias, afiliadas ou relações de provedor de serviço gerenciado. Essas organizações têm uma organização pai, como uma empresa controladora, mas as organizações subjacentes operam autonomamente ponto e vírgula, às vezes com diferentes requisitos regionais. Isso resulta em cada organização que tem seu próprio ambiente do Azure AD e locatários separados do Power BI.

![Trabalhando com subsidiárias](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_05.png)


Nessa estrutura, a organização pai normalmente precisa distribuir insights padronizados para suas subsidiárias. Normalmente, esse compartilhamento ocorre usando o Ad hoc ou planejado compartilhamento da abordagem de aplicativos do Power BI, conforme ilustrado na imagem a seguir, pois permite a distribuição de conteúdo autoritativo padronizado a um público amplo. Na prática, uma combinação de todos os cenários mencionados anteriormente neste documento é usada.

![Cenários de combinação](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_06.png)


Isso segue o processo a seguir:

1. Os usuários de cada subsidiária são convidados a Azure do Contoso AD
2. Em seguida, o aplicativo Power BI é publicado para fornecer acesso a esses usuários para os dados necessários
3. Por fim, os usuários abrirem o aplicativo por meio de um link que tenham recebido para ver os relatórios

Vários importantes desafios enfrentados pelas organizações nessa estrutura:

- Como distribuir os links para conteúdo Power BI da organização pai
- Como permitir que os usuários da subsidiária acessar a fonte de dados hospedado pela organização pai

#### <a name="distributing-links-to-content-in-the-parent-organizations-power-bi"></a>Distribuição de links para conteúdo Power BI da organização pai

Três abordagens normalmente são usadas para distribuir os links para o conteúdo. O primeiro a maioria dos basic está para enviar o link para o aplicativo para os usuários necessários ou colocá-lo em um site do SharePoint Online do qual ele pode ser aberto. Os usuários, em seguida, podem indicador no link em seus navegadores para acesso mais rápido aos dados que precisam.

A segunda abordagem se baseia na edição de entre organizações e no gerenciamento de capacidade de conteúdo do Power BI. Organização pai permite que os usuários de subsidiárias acessar seu Power BI e controla o que eles podem acessar por meio da permissão. Isso dá acesso ao Power BI início em que o usuário a subsidiária vê uma lista abrangente de conteúdo compartilhado com eles no locatário da organização pai. Em seguida, a URL para o ambiente do Power BI organizações pai recebe para os usuários sem as subsidiárias.

A abordagem final usa um aplicativo do Power BI criado dentro do locatário do Power BI para cada subsidiária. O aplicativo Power BI inclui um painel com [blocos configurados com a opção de link externo](https://docs.microsoft.com/power-bi/service-dashboard-edit-tile#hyperlink). Quando o usuário pressiona o bloco, eles são aplicados para o relatório apropriado, o dashboard ou o aplicativo no Power BI da organização pai. Essa abordagem tem a vantagem adicional de que o aplicativo pode ser instalado automaticamente para todos os usuários das subsidiárias e está disponível para eles sempre que ele entrar em seu próprio ambiente do Power BI. Uma vantagem dessa abordagem é que ele funciona bem com aplicativos móveis do Power BI que podem abrir o link do modo nativo. Você também pode combinar isso com a segunda abordagem para habilitar mais fácil alternar entre os ambientes do Power BI.

#### <a name="allowing-subsidiary-users-to-access-data-sources-hosted-by-the-parent-organization"></a>Permitir que os usuários da subsidiária acessar fontes de dados hospedados pela organização pai

Muitas vezes os analistas uma subsidiária precisam criar suas próprias análises usando os dados fornecidos pela organização pai. Nesse caso, fontes de dados de nuvem são usados para resolver o desafio.

A primeira abordagem aproveita [do Azure Analysis Services](https://docs.microsoft.com/azure/analysis-services/analysis-services-overview) para criar um data warehouse corporativo nível empresarial que atenda às necessidades dos analistas entre pai e suas subsidiárias, como mostra a imagem a seguir. A Contoso pode hospedar os dados e usar recursos como a segurança em nível de linha para garantir que os usuários em cada subsidiária pode acessar somente seus dados. Analistas de cada organização podem acessar o data warehouse por meio do Power BI Desktop e publique a análise resultante para os respectivos locatários do Power BI.

![Como ocorre o compartilhamento com locatários do Power BI](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_07.png)


A segunda abordagem aproveita [banco de dados SQL](https://azure.microsoft.com/services/sql-database/) para criar um data warehouse relacional para fornecer acesso a dados. Isso funciona de forma semelhante à abordagem do Azure Analysis Services, embora alguns recursos, como segurança em nível de linha pode ser mais difícil de implantar e manter em subsidiárias.

Abordagens mais sofisticadas também são possíveis, no entanto, as opções acima é de longe o mais comuns.

### <a name="case-3-shared-environment-across-partners"></a>Caso 3: Ambiente compartilhado entre parceiros

A Contoso pode inserir uma parceria com um concorrente criem um carro em conjunto em uma linha de assembly compartilhada, mas para distribuir o veículo em marcas diferentes ou em regiões diferentes. Isso exige uma colaboração extensiva e co-ownership de dados, inteligência e análise entre organizações. Essa estrutura também é comum no setor de serviços de consultoria em que uma equipe de consultores pode realizar a análise baseada em projeto para um cliente.

![Ambiente compartilhado entre parceiros](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_08.png)



Na prática, essas estruturas complexas, como mostrado na imagem a seguir, em exigem a manter a equipe de TI. Para ser eficiente essa estrutura se baseia na edição de entre organizações e no gerenciamento de capacidade de conteúdo do Power BI, pois ele permite que as organizações reutilizar licenças do Power BI Pro adquiridas para os respectivos locatários do Power BI.

![Licenças e o conteúdo compartilhado organizacional](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_09.png)



Para estabelecer um locatário do Power BI compartilhado, um Azure Active Directory precisa ser criado e pelo menos uma conta de usuário do Power BI Pro precisa ser adquiridas para um usuário em que o active directory. Este usuário convida usuários necessários para a organização compartilhado. Importante é que, nesse cenário, os usuários da Contoso são tratados como usuários externos quando eles operam dentro Power BI da organização compartilhado.

O processo é da seguinte maneira:

1. A organização compartilhado é estabelecida como um novo Azure Active Directory e pelo menos uma conta de usuário é criada na nova organização. Esse usuário deve ter uma licença do Power BI Pro atribuída a eles.
2. Este usuário, em seguida, estabelece um locatário do Power BI e convida os usuários necessários da Contoso e a organização do parceiro. O usuário também estabelece quaisquer ativos de dados compartilhados, como o Azure Analysis Services. A Contoso e os usuários do parceiro podem acessar Power BI da organização compartilhada como usuários convidados. Se a permissão para editar e gerenciar conteúdo no Power BI dos usuários externos podem usar o Power BI inicial, use espaços de trabalho, carregar ou editar conteúdo e compartilhar relatórios. Normalmente, todos os ativos compartilhados são armazenados e acessados a partir da organização compartilhada.
3. Dependendo de como as partes concordam colaborar, é possível para cada organização desenvolver seus próprios dados proprietários e análise usando os ativos do depósito de dados compartilhada. Eles podem distribuir aqueles aos respectivos usuários internos usando seus locatários do Power BI internos.

### <a name="case-4-distribution-to-hundreds-or-thousands-of-external-partners"></a>Caso 4: Distribuição para centenas ou milhares de parceiros externos

Enquanto a Contoso criou um relatório de confiabilidade do radiador para um fornecedor, agora a Contoso deseja criar um conjunto de relatórios padronizados para centenas de fornecedores. Isso permite que a Contoso garantir que todos os fornecedores tenham a análise que precisam para fazer melhorias ou para corrigir defeitos de fabricação.

![Distribuição à definição dos muitos parceiros](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_10.png)


Quando uma organização precisa distribuir insights e dados padronizados para muitos usuários/organizações externas, eles podem usar o compartilhamento Ad hoc ou planejado de cenário de aplicativos do Power BI para criar um Portal de BI rapidamente e sem os custos de desenvolvimento abrangente. O processo para criar tal um portal usando um aplicativo do Power BI é abordado no estudo de caso: Criando um Portal de BI usando o Power BI + AD B2B do Azure – passo a passo de instruções mais adiante neste documento.

Uma variante comum desse caso é quando uma organização é tentar compartilhar insights com consumidores, especialmente quando desejam para utilizar B2C do Azure com o Power BI. Power BI não dá suporte nativo a B2C do Azure. Se você estiver avaliando as opções para esse caso, considere o uso de alternativas opção 2 nas abordagens alternativas comuns a seção mais adiante neste documento.

## <a name="case-study-building-a-bi-portal-using-power-bi--azure-ad-b2b--step-by-step-instructions"></a>Estudo de caso: Criação de um Portal de BI usando o Power BI + B2B do Azure AD – instruções passo a passo

Integração do Power BI com o Azure AD B2B dá uma maneira perfeita de complicações para fornecer aos usuários de convidado acesso seguro ao seu portal de BI de Contoso. A Contoso pode fazê-lo com as três etapas:

![Criação de um portal](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_11.png)


1. Criar um portal de BI no Power BI

    A primeira tarefa para a Contoso é criar o seu portal de BI no Power BI. Portal de BI da Contoso consiste em uma coleção de painéis com finalidade específica e relatórios que serão disponibilizados para muitos usuários internos e convidados. A maneira recomendada para fazer isso no Power BI é criar um aplicativo do Power BI. Saiba mais sobre [aplicativos no Power BI](https://powerbi.microsoft.com/blog/distribute-to-large-audiences-with-power-bi-apps/).

- Equipe de BI da Contoso cria um espaço de trabalho do aplicativo no Power BI

    ![Workspace de aplicativo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_12.png)
    

- Outros autores são adicionados ao espaço de trabalho

    ![Adicione autores](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_13.png)


- O conteúdo é criado dentro do espaço de trabalho

    ![Criar o conteúdo dentro do espaço de trabalho](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_14.png)


    Agora que o conteúdo é criado em um espaço de trabalho do aplicativo, a Contoso está pronto para convidar usuários nas organizações dos parceiros para consumir este conteúdo.

2. Convidar usuários convidados

    Há duas maneiras para a Contoso convidar usuários convidados ao seu portal de BI no Power BI:

    * Convites planejados
    * Convites ad hoc

    **Convites planejados**

    Nessa abordagem, a Contoso convites para os usuários convidados ao seu AD do Azure antecipadamente e, em seguida, distribui o conteúdo do Power BI para eles. A Contoso pode convidar usuários convidados de portal do Azure ou usando o PowerShell. Aqui estão as etapas para convidar usuários convidados do portal do Azure:

    - Administrador do Azure AD da Contoso navega para **portal do Azure > Azure Active Directory > usuários e grupos > todos os usuários > novo usuário convidado**

    ![Usuário convidado](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_15.png)


    - Adicionar uma mensagem de convite para os usuários convidados e clique em Convidar

    ![Adicione o convite](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_16.png)


    > [!NOTE]
    > Para convidar usuários convidados do portal do Azure, você precisa para um administrador para o Azure Active Directory do seu locatário.

    Se a Contoso deseja convidar muitos usuários, eles podem fazer isso usando o PowerShell. Administrador do Azure AD da Contoso armazena os endereços de email de todos os usuários convidados em um arquivo CSV. Aqui estão [código de colaboração B2B do Azure Active Directory e exemplos do PowerShell](https://docs.microsoft.com/azure/active-directory/b2b/code-samples) e instruções.

    Após o convite, os usuários convidados recebem um email com o link de convite.

    ![Link de convite](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_17.png)


    Depois que os usuários convidados clicarem no link, eles podem acessar o conteúdo no locatário Contoso do Azure AD.

    > [!NOTE]
    > É possível alterar o layout do email de convite usando o recurso de identidade visual do AD do Azure, conforme descrito [aqui](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-invitation-email).


    **Convites ad hoc**

    E se Contoso não sabe todos os usuários convidados que ele deseja convidar antecipadamente? Ou, e se deseja que o analista na Contoso que criou o portal de BI distribuir conteúdo para usuários convidados por conta própria? Há também suporte para esse cenário no Power BI com convites ad-hoc.

    O analista pode adicionar apenas os usuários externos à lista de acesso do aplicativo quando eles são publicá-lo. Os usuários convidados obtém um convite e depois de aceitá-la, eles são automaticamente redirecionados para o conteúdo do Power BI.

    ![Adicionar usuário externo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_18.png)


    > [!NOTE]
    > Convites são necessários apenas na primeira vez em que um usuário externo é convidado para sua organização.


3. Distribuir conteúdo

    Agora que a equipe de BI da Contoso tem criadas no portal de BI e usuários convidados, eles podem distribuir seu portal para seus usuários finais, dando a usuários convidados acesso ao aplicativo e publicá-la. Power BI é preenchida automaticamente nomes de usuários convidados que foram adicionados anteriormente ao locatário Contoso. Convites ad hoc para outros usuários convidados também podem ser adicionados neste momento.

    > [!NOTE]
    > Se usar grupos de segurança para gerenciar o acesso ao aplicativo para usuários externos, use a abordagem de convites planejados e compartilhar o link do aplicativo diretamente com cada usuário externo que precisa acessá-lo. Caso contrário, o usuário externo pode não ser capaz de instalar ou exibir o conteúdo de dentro do aplicativo. _

    Usuários convidados recebem um email com um link para o aplicativo.

    ![Link de convite por email](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_19.png)


    Em clicar nesse link, os usuários convidados deverá autenticar com a identidade de sua própria organização.

    ![Na página de entrada](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_20.png)


    Depois que eles são autenticados com êxito, ele será redirecionado ao aplicativo de BI da Contoso.

    ![Consulte o conteúdo compartilhado](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_21.png)

    Usuários convidados, posteriormente, podem obter ao aplicativo da Contoso clicando no link no email ou o link de uso de indicadores. A Contoso pode também tornar mais fácil para usuários convidados adicionando este link para qualquer portal extranet existente que já usam os usuários convidados.

4. Próximas etapas

    Usando um aplicativo do Power BI e o Azure AD B2B, Contoso foi capaz de criar rapidamente um Portal de BI para seus fornecedores de uma maneira sem código. Isso bastante simplificado distribuindo analytics padronizado para todos os fornecedores que precisasse dele.

    Embora o exemplo mostrou como um único relatório comuns pode ser distribuído entre fornecedores, o Power BI pode avançar muito mais. Para garantir que cada parceiro vê apenas dados relevantes a mesmos, segurança em nível de linha podem ser adicionada facilmente ao modelo de relatório e dados. A segurança de dados para a seção de parceiros externos neste documento descreve esse processo em detalhes.

    Painéis e relatórios individuais geralmente precisam ser inserido em um portal existente. Isso também pode ser feito reutilizando muitas das técnicas mostradas no exemplo. No entanto, essas situações pode ser mais fácil de incorporar relatórios ou dashboards diretamente de um espaço de trabalho. O processo para convidar e atribuindo permissão de segurança para a exigir que os usuários permanecem os mesmos.

## <a name="under-the-hood-how-is-lucy-from-supplier1-able-to-access-power-bi-content-from-contosos-tenant"></a>Nos bastidores: Como é Lucy de Supplier1 capaz de acessar o conteúdo do Power BI do locatário da Contoso?

Agora que temos visto como a Contoso é capaz de distribuir o conteúdo do Power BI para usuários convidados de organizações parceiras, vejamos como isso funciona nos bastidores.

Quando a Contoso convidados [ lucy@supplier1.com ](mailto:lucy@supplier1.com) ao seu diretório, o Azure AD criará um link entre [ Lucy@supplier1.com ](mailto:Lucy@supplier1.com) e o locatário Contoso do Azure AD. Esse link permite que o Azure AD sabe que Lucy@supplier1.com podem acessar o conteúdo no locatário Contoso.

Quando Lucy tenta acessar o aplicativo do Power BI da Contoso, o Azure AD verifica se Lucy pode acessar o locatário Contoso e fornece um token que indica que Lucy é autenticada para acessar conteúdo no locatário Contoso do Power BI. Power BI usa esse token para autorizar e certifique-se de que Lucy tem acesso ao aplicativo do Power BI da Contoso.

![Verificação e autorização](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_22.png)

Integração do Power BI com o Azure AD B2B funciona com todos os endereços de email comercial. Se o usuário não tem uma identidade do AD do Azure, eles podem ser solicitados para criar um. A imagem a seguir mostra o fluxo detalhado:

![Gráfico de fluxo de integração](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_23.png)


É importante reconhecer que a conta do AD do Azure será usada ou criada na parte externa do AD do Azure, este será tornar possível que Lucy pode usar seu próprio nome de usuário e senha e suas credenciais automaticamente irá parar de funcionar em outros locatários sempre que ela sair da empresa quando sua organização também usa o Azure AD.

## <a name="licensing"></a>Licenças

A Contoso pode escolher uma das três abordagens para usuários convidados de licença de seus fornecedores e organizações parceiras tenham acesso ao conteúdo do Power BI.

> [!NOTE]
> _Camada gratuita do B2B AD do Azure é o suficiente para usar o Power BI com o Azure AD B2B. Alguns recursos avançados do Azure AD B2B, como grupos dinâmicos exigem uma licença adicional. Consulte a documentação do Azure AD B2B para obter informações adicionais:_ [_https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance_](https://docs.microsoft.com/azure/active-directory/b2b/licensing-guidance)

### <a name="approach-1-contoso-uses-power-bi-premium"></a>Abordagem 1: A Contoso usa o Power BI Premium

Com essa abordagem, a Contoso adquire a capacidade do Power BI Premium e atribui seu conteúdo de BI portal a essa capacidade. Isso permite que os usuários convidados de organizações parceiras acessar o aplicativo do Power BI da Contoso sem qualquer licença do Power BI.

Os usuários externos também estão sujeitos ao consumo de experiências somente oferecidas aos usuários "Gratuita" no Power BI durante o consumo de conteúdo dentro do Power BI Premium.

A Contoso também pode tirar proveito dos outros recursos do premium do Power BI para seus aplicativos, como taxas de atualização maior, capacidade dedicada e tamanhos grandes de modelos.

![Recursos adicionais](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_24.png)


### <a name="approach-2-contoso-assigns-power-bi-pro-licenses-to-guest-users"></a>Abordagem 2: A Contoso atribui licenças do Power BI Pro aos usuários convidados

Com essa abordagem, Contoso atribui licenças pro a usuários convidados do parceiro em organizações – isso pode ser feito no Centro de administração do Microsoft 365 da Contoso. Isso permite que os usuários convidados de organizações parceiras acessar o aplicativo do Power BI da Contoso sem precisar adquirir uma licença si mesmos. Isso pode ser adequado para compartilhar com usuários externos cuja organização ainda não adotada Power BI.

> [!NOTE]
> _Licença do pro da Contoso se aplica a usuários convidados somente quando eles acessam o conteúdo no locatário Contoso. Licenças Pro habilitam o acesso ao conteúdo que não está em uma capacidade do Power BI Premium. No entanto, os usuários externos com uma licença Pro são restritas por padrão para uma experiência única de consumo. Isso pode ser alterar usando a abordagem descrita a_ _permitir que usuários externos editar e gerenciar o conteúdo do Power BI_ _seção mais adiante neste documento._

![Informações de licença](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_25.png)


### <a name="approach-3-guest-users-bring-their-own-power-bi-pro-license"></a>Abordagem 3: Usuários convidados tragam suas próprias licenças do Power BI Pro

Com essa abordagem, o fornecedor 1 atribui uma licença do Power BI Pro para Lucy. Em seguida, ela pode acessar o aplicativo do Power BI da Contoso com esta licença. Uma vez que Lucy pode usar sua licença do Pro da própria organização ao acessar um ambiente externo do Power BI, essa abordagem, às vezes, é conhecida como _Traga sua própria licença_ (BYOL). Se ambas as organizações estão usando o Power BI, isso oferece licenciamento vantajoso para a solução de análise geral e minimiza a sobrecarga de atribuição de licenças a usuários externos.

> [!NOTE]
> _A licença do pro por fornecedor 1 concedida ao Lucy se aplica a qualquer locatário do Power BI onde Lucy é um usuário convidado. Licenças Pro habilitam o acesso ao conteúdo que não está em uma capacidade do Power BI Premium. No entanto, os usuários externos com uma licença Pro são restritas por padrão para uma experiência única de consumo. Isso pode ser alterar usando a abordagem descrita a_ _permitir que usuários externos editar e gerenciar o conteúdo do Power BI_ _seção mais adiante neste documento._

![Requisitos de licença do PRO](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_26.png)

## <a name="data-security-for-external-partners"></a>Segurança de dados para parceiros externos

Normalmente ao trabalhar com vários fornecedores externos, a Contoso precisa garantir que cada fornecedor veja dados apenas sobre seus próprios produtos. Segurança baseada em usuário e segurança em nível de linha dinâmica tornam fácil de fazer com o Power BI.

### <a name="user-based-security"></a>Segurança baseada em usuário

Um dos recursos mais avançados do Power BI é a segurança em nível de linha. Esse recurso permite que a Contoso criar um único relatório e conjunto de dados, mas ainda aplicar as regras de segurança diferentes para cada usuário. Para obter uma explicação detalhada, consulte [segurança de nível de linha (RLS)](https://powerbi.microsoft.com/documentation/powerbi-admin-rls/).

Integração do Power BI com o Azure AD B2B permite que a Contoso atribuir regras de segurança de nível de linha para usuários convidados, assim que eles forem convidados para o locatário Contoso. Como já vimos antes, a Contoso pode adicionar usuários convidados por meio de um planejados ou convites ad hoc. Se a Contoso deseja impor segurança em nível de linha, é altamente recomendável usar convites planejados para adicionar os usuários convidados antes do tempo e atribuí-los às funções de segurança antes de compartilhar o conteúdo. Se, em vez disso, a Contoso usa convites ad hoc, pode haver um curto período de tempo em que os usuários convidados não poderão ver os dados.

> [!NOTE]
> Esse atraso ao acessar os dados protegidos pelo RLS ao usar ad-hoc convida pode levar a dar suporte a solicitações para sua equipe de TI porque os usuários verão em branco ou desfeito procurando relatórios/painéis quando abrir um compartilhamento de link no email que recebem. Portanto, é altamente recomendável usar convites planejados neste scenario.* *

Vamos explicar isso com um exemplo.

Como mencionado anteriormente, a Contoso tem fornecedores em todo o mundo, e eles desejam certificar-se de que os usuários de suas organizações supplier obtenham percepções de dados de apenas seu território.  Mas os usuários da Contoso podem acessar todos os dados. Em vez de criar vários relatórios diferentes, a Contoso cria um único relatório e filtra os dados com base em usuário visualizando-lo.

![Conteúdo compartilhado](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_27.png)

Para garantir que a Contoso pode filtrar dados com base em quem está se conectando, duas funções são criadas no Power BI desktop. Uma para filtrar todos os dados do SalesTerritory "Europa" e outra para "América do Norte".

![Gerenciar funções](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_28.png)

Sempre que as funções são definidas no relatório, um usuário deve ser atribuído a uma função específica para que eles possam obter acesso a dados. A atribuição de funções acontece dentro do serviço do Power BI ( **conjuntos de dados > segurança** )

![Configuração de segurança](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_29.png)

Isso abre uma página onde a equipe de BI da Contoso pode ver as duas funções criados por eles.  Agora a equipe de BI da Contoso pode atribuir usuários às funções.

![Segurança em nível de linha](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_30.png)

No exemplo a Contoso está adicionando um usuário em uma organização parceira com endereço de email "[adam@themeasuredproduct.com](mailto:adam@themeasuredproduct.com)" à função Europa:

![Configurações de segurança de nível de linha](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_31.png)

Quando isso é resolvido pelo AD do Azure, a Contoso pode ver o nome aparecem na janela pronto para ser adicionado:

![Mostrar funções](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_32.png)

Agora quando esse usuário abre o aplicativo que foi compartilhado com ele, ele vê apenas um relatório com os dados da Europa:

![Exibir conteúdo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_33.png)

### <a name="dynamic-row-level-security"></a>Segurança em nível de linha dinâmica

Outro tópico interessante é ver como o trabalho de nível RLS (segurança) com o Azure AD B2B de linha dinâmico.

Em resumo, a segurança em nível de linha dinâmica funciona por meio da filtragem de dados no modelo com base no nome de usuário da pessoa que se conectar ao Power BI. Em vez de adicionar várias funções para grupos de usuários, você pode definir os usuários no modelo. Não descreveremos o padrão em detalhes aqui. Kasper de Jong oferece uma gravação detalhada até em todos os os tipos de segurança em nível de linha [roteiro de segurança dinâmica de área de trabalho do Power BI](https://www.kasperonbi.com/power-bi-desktop-dynamic-security-cheat-sheet/)e, na [neste white paper](https://msdn.microsoft.com/library/jj127437.aspx) .

Vamos examinar um pequeno exemplo – a Contoso tem um relatório simples nas vendas por grupos:

![Conteúdo de exemplo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_34.png)

Agora este relatório precisa ser compartilhado com dois usuários convidados e um usuário interno – o usuário interno pode ver tudo, mas os usuários convidados só podem ver os grupos tiverem acesso à. Isso significa que podemos deve filtrar os dados somente para os usuários convidados. Para filtrar os dados adequadamente, a Contoso usa o padrão de RLS dinâmica conforme descrito na postagem do blog e white paper. Isso significa que, a Contoso adiciona os nomes de usuário para os dados em si:

![Exibir os usuários RLS nos próprios dados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_35.png)

Em seguida, a Contoso cria o modelo de dados à direita que filtra os dados adequadamente com as relações da direita:

![Os dados apropriados são mostrados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_36.png)

Para filtrar os dados automaticamente com base em quem está conectado, a Contoso precisa criar uma função que passa o usuário que está se conectando. Nesse caso, a Contoso cria duas funções – a primeira é a "securityrole" que filtra a tabela de usuários com o nome de usuário atual do usuário conectado ao Power BI (isso funciona mesmo para os usuários convidados de B2B do Azure AD).

![Gerenciar funções](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_37.png)

A Contoso também cria outro "AllRole" para seus usuários internos que podem ver tudo – essa função não tem nenhum predicado de segurança.

Depois de carregar o arquivo da área de trabalho do Power BI para o serviço, a Contoso pode atribuir os usuários convidados para os usuários internos para "AllRole" e "SecurityRole"

Agora, quando os usuários convidados abrem o relatório, ele vê apenas vendas de grupo:

![Somente a partir de um grupo](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_38.png)

Na matriz para a direita, você pode ver o resultado da função username () e userPrincipalName () retornam que os usuários convidados de endereço de email.

Agora o usuário interno obtém para ver todos os dados:

![Todos os dados mostrados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_39.png)

Como você pode ver, a RLS dinâmica funciona com usuários internos ou convidados.

> [!NOTE]
> Este cenário também funciona ao usar um modelo no Azure Analysis Services. Normalmente, o Azure Analysis Services é conectado ao mesmo Azure AD como o Power BI – nesse caso, o Azure Analysis Services também saiba os usuários convidados por meio do Azure AD B2B.

## <a name="connecting-to-on-premises-data-sources"></a>Conectar-se a fontes de dados local

O Power BI oferece a capacidade de aproveitar em fontes de dados local, como a Contoso [SQL Server Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/) ou [SQL Server](https://powerbi.microsoft.com/documentation/powerbi-gateway-kerberos-for-sso-pbi-to-on-premises-data/) diretamente graças à [gateway de dados no local](https://powerbi.microsoft.com/documentation/powerbi-gateway-onprem/). Também é possível fazer logon para essas fontes de dados com as mesmas credenciais usadas com o Power BI.

> [!NOTE]
> Ao instalar um gateway para se conectar ao seu locatário do Power BI, você deve usar um usuário criado dentro do seu locatário. Os usuários externos não é possível instalar um gateway e conectá-lo ao seu locatário. _

Para usuários externos, isso pode ser mais complicado, já que os usuários externos não são geralmente conhecidos para os locais AD. O Power BI oferece uma solução alternativa para isso, permitindo que os administradores da Contoso mapear os nomes de usuário externo para nomes de usuário interno, conforme descrito em [gerenciar sua fonte de dados – Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Por exemplo, [ lucy@supplier1.com ](mailto:lucy@supplier1.com) pode ser mapeado para [lucy\_supplier1\_com #EXT@contoso.com](mailto:lucy_supplier1_com).

![Mapeando nomes de usuário](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_40.png)

Esse método é bem se a Contoso tiver apenas um punhado de usuários ou se a Contoso pode mapear todos os usuários externos para uma única conta interna. Para cenários mais complexos, onde cada usuário precisa de suas próprias credenciais, há uma abordagem mais avançada que usa [atributos personalizados do AD](https://technet.microsoft.com/library/cc961737.aspx) para fazer o mapeamento, conforme descrito em [gerenciar sua fonte de dados – Analysis Services](https://powerbi.microsoft.com/documentation/powerbi-gateway-enterprise-manage-ssas/). Isso permitiria que o administrador da Contoso definir um mapeamento para todos os usuários no AD do Azure (também usuários de B2B externos).  Esses atributos podem ser definidos por meio do modelo de objeto AD usando scripts ou códigos para que a Contoso pode automatizar totalmente o mapeamento no convite ou em uma cadência agendada.

## <a name="enabling-external-users-to-edit-and-manage-content-within-power-bi"></a>Permitir que usuários externos editar e gerenciar o conteúdo do Power BI

A Contoso pode permitir que usuários externos contribuir com conteúdo dentro da organização, conforme descrito anteriormente a entre organizações de edição e o gerenciamento da seção de conteúdo do Power BI.

> [!NOTE]
> Para editar e gerenciar o conteúdo do Power BI de sua organização, o usuário deve ter uma licença do Power BI Pro no espaço de trabalho que não seja o meu espaço de trabalho. Os usuários podem obter licenças Pro conforme abordado nos the_ _Licensing__section deste documento._

O Portal de administração do Power BI fornece o **permitir que os usuários convidados externo editar e gerenciar o conteúdo da organização** configuração nas configurações de locatário. Por padrão, a configuração é definida como desabilitada, o que significa que os usuários externos obtenham uma experiência de somente leitura restrita por padrão. A configuração se aplica a usuários com UserType definido como convidado no Azure AD. A tabela a seguir descreve os comportamentos que os usuários experimentam dependendo do seu UserType e como as configurações são definidas.

| **Tipo de usuário no Azure AD** | **Permitir que os usuários convidados externo editar e gerenciar a configuração de conteúdo** | **Comportamento** |
| --- | --- | --- |
| Convidado | Desabilitado para o usuário (padrão) | Por item consumo somente modo de exibição. Permite acesso somente leitura a relatórios, painéis e aplicativos quando visualizado por meio de uma URL enviada para o usuário convidado. Aplicativos móveis Power BI fornecem uma exibição somente leitura para o usuário convidado. |
| Convidado | Habilitado para o usuário | O usuário externo obtém acesso à experiência completa do Power BI, embora alguns recursos não estão disponíveis para eles. O usuário externo deve fazer logon Power BI usando a URL do serviço do Power BI com as informações de locatário incluídas. Obtém o usuário que baseado em permissões, meu espaço de trabalho e a experiência inicial pode procurar, exibir e criar conteúdo. </br></br> Aplicativos móveis Power BI fornecem uma exibição somente leitura para o usuário convidado. |

> [!NOTE]
> Usuários externos no Azure AD também podem ser definidos como UserType de membro. Isso não é suportado atualmente no Power BI.

No portal do administrador do Power BI, a configuração é mostrada na imagem a seguir.

![Configurações do administrador](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_41.png)

Os usuários convidados recebem a experiência padrão somente leitura e que pode editar e gerenciar o conteúdo. O padrão é desativado, o que significa que todos os usuários convidados têm a experiência de somente leitura. O administrador do Power BI podem habilitar a configuração para todos os usuários convidados da organização ou para grupos de segurança específicos definidos no Azure AD. Na imagem a seguir, o administrador do Power BI Contoso criou um grupo de segurança no AD do Azure para gerenciar quais usuários externos podem editar e gerenciar o conteúdo no locatário Contoso.

Para ajudar a esses usuários para fazer logon no Power BI, forneça a URL do locatário. Para localizar a URL do locatário, siga estas etapas.

1. No serviço do Power BI, no menu superior, selecione a Ajuda ( **?** ), em seguida, **sobre o Power BI**.
2. Procure o valor próximo a **URL do locatário**. Esta é a URL de locatário que você pode compartilhar com os usuários convidados.

    ![URL do Locatário](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_42.png)

Ao usar a permitir que usuários do convidado externo para editar e gerenciar o conteúdo da organização, os usuários convidados especificado obtém acesso ao Power BI de sua organização e vir algum conteúdo ao qual eles têm permissão. Eles podem acessar a página inicial, procure e contribuir com conteúdo para os espaços de trabalho, instalar aplicativos em que eles estão na lista de acesso e tem um meu espaço de trabalho. Eles podem ser administradores de workspaces que usam a nova experiência de workspace e até mesmo criar tais workspaces.

> [!NOTE]
> Ao usar essa opção, certifique-se de examinar a seção de governança deste documento, pois as configurações do AD do Azure padrão impedir que usuários convidados para usar determinados recursos, como seletores de pessoas que podem levar a uma redução experience.* *

Para os usuários convidados habilitados por meio de usuários convidados externo de permitir editar e gerenciar conteúdo em que a configuração de locatário da organização, algumas experiências não estão disponíveis a eles. Para atualizar ou publicar relatórios, os usuários convidados precisam usar a web de serviço do Power BI da interface do usuário, incluindo obter dados para carregar arquivos do Power BI Desktop. As seguintes experiências não são compatíveis:

- Publicação direta do Power BI Desktop para o serviço do Power BI
- Usuários convidados não podem usar o Power BI Desktop para se conectar a conjuntos de dados de serviço no serviço do Power BI
- Workspaces clássicos associados a Grupos do Office 365: Um usuário convidado não é capaz de criar ou ser administradores desses workspaces. Eles podem ser membros.
- O envio de convites ad-hoc para listas de acesso do workspace não é uma ação compatível
- O Power BI Publisher para Excel não é compatível com usuários convidados
- Usuários convidados não podem instalar um Power BI Gateway e conectá-lo à sua organização
- Usuários convidados não podem instalar aplicativos e publicá-los para toda a organização
- Usuários convidados não podem usar, criar, atualizar ou instalar pacotes de conteúdo organizacional
- Usuários convidados não podem usar o Analisar no Excel
- Usuários convidados não podem ser @mentioned em comentários (essa funcionalidade será adicionada em uma versão futura)
- Usuários convidados não podem usar assinaturas (essa funcionalidade será adicionada em uma versão futura)
- Usuários convidados que usam essa funcionalidade devem ter uma conta corporativa ou de estudante. A experiência de usuários convidados usando contas pessoais mais limitações devido às restrições de logon.



## <a name="governance"></a>Governança

### <a name="additional-azure-ad-settings-that-affect-experiences-in-power-bi-related-to-azure-ad-b2b"></a>Azure AD configurações adicionais que afetam as experiências no Power BI relacionados ao Azure AD B2B

Ao usar o compartilhamento do Azure AD B2B, o administrador do Active Directory do Azure controla os aspectos da experiência do usuário externo. Elas são controladas na página de configurações de colaboração externa nas configurações do Active Directory do Azure para seu locatário.

Detalhes sobre as configurações estão disponíveis aqui:

[https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations](https://docs.microsoft.com/azure/active-directory/b2b/delegate-invitations)

> [!NOTE]
> Por padrão, as permissões de usuários convidados são limitadas opção é definida como Sim, para que os usuários convidados no Power BI limitaram experiências especialmente envolvem compartilhamento em que as interfaces do usuário do seletor de pessoas não funcionam para os usuários. É importante trabalhar com seu administrador do Azure AD para defini-lo como não, conforme mostrado abaixo para garantir uma boa experience.* *

![Configurações de colaboração externa](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_43.png)


### <a name="control-guest-invites"></a>Convites do convidado de controle

Os administradores do Power BI podem controlar o compartilhamento externo para o Power BI, visitando o portal de administração do Power BI. Mas os administradores de inquilinos também podem controlar o compartilhamento externo com várias políticas de AD do Azure.  Essas políticas permitem locatário aos administradores

- Desativar convites pelos usuários finais
- Somente administradores e usuários na função emissor do convite convidado podem convidar
- Administradores, a função emissor do convite convidado e membros podem convidar
- Todos os usuários, incluindo convidados, podem convidar

Você pode ler mais sobre essas políticas em [delegar convites para colaboração B2B do Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-delegate-invitations).

Todas as ações do Power BI por usuários externos são também [auditado em nosso portal de auditoria](https://powerbi.microsoft.com/documentation/powerbi-admin-auditing/).

### <a name="conditional-access-policies-for-guest-users"></a>Políticas de acesso condicional para usuários convidados

A Contoso pode impor políticas de acesso condicional para usuários convidados que acessar o conteúdo do locatário Contoso. Você pode encontrar instruções detalhadas em [acesso condicional para usuários de colaboração B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

## <a name="common-alternative-approaches"></a>Abordagens alternativas comuns

Enquanto o Azure AD B2B facilita a compartilhar dados e relatórios entre organizações, há várias outras abordagens que são comumente usadas e podem ser superior em determinados casos.

### <a name="alternative-option-1-create-duplicate-identities-for-partner-users"></a>Opção alternativa 1: Criar usuários de identidades duplicadas para parceiros

Com essa opção, a Contoso tinha que criar manualmente o identidades duplicadas para cada usuário do parceiro no locatário Contoso, conforme mostrado na imagem a seguir. Em seguida, no Power BI, Contoso pode compartilhar às identidades atribuídas a aplicativos, painéis ou relatórios apropriados.

![Nomes e os mapeamentos de configuração apropriados](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_44.png)

Motivos para escolher essa alternativa:

- Como a identidade do usuário é controlada pela sua organização, todas relacionadas de serviço, como email, SharePoint, etc. também estão dentro do controle da sua organização. Seus administradores de TI podem redefinir senhas, desabilitar o acesso a contas ou auditar atividades nesses serviços.
- Os usuários que usam contas pessoais para os negócios geralmente são impedidos de acessar determinados serviços talvez seja necessário uma conta organizacional.
- Alguns serviços só funcionam por usuários da sua organização. Por exemplo, usando o Intune para gerenciar o conteúdo nos dispositivos pessoais/móvel de usuários externos usando B2B do Azure não possível.

Motivos para não escolher essa alternativa:

- Os usuários de organizações parceiras devem se lembrar de dois conjuntos de credenciais — um para acessar o conteúdo da sua própria organização e outro para acessar o conteúdo da Contoso. Isso é algo incômodo para esses usuários convidados e muitos usuários convidados são confundidos por essa experiência.
- A Contoso deve comprar e atribuir licenças por usuário para esses usuários. Se um usuário precisa receber email ou usar os aplicativos do office, eles precisam de licenças apropriadas, incluindo Power BI Pro para editar e compartilhar conteúdo no Power BI.
- A Contoso poderá impor políticas de governança para usuários externos em comparação com usuários internos e autorização mais estritos. Para fazer isso, a Contoso precisa para criar uma nomenclatura internamente para usuários externos e todos os usuários da Contoso precisam ser instruídas sobre essa nomenclatura.
- Quando o usuário deixa a sua organização, eles continuarão a ter acesso aos recursos da Contoso até que o administrador da Contoso exclui manualmente sua conta
- Administradores da Contoso precisam gerenciar a identidade do convidado, incluindo criação, redefinições de senha, etc.

### <a name="alternative-option-2-create-a-custom-power-bi-embedded-application-using-custom-authentication"></a>Opção alternativa 2: Criar um aplicativo do Power BI Embedded personalizado usando a autenticação personalizada

Outra opção para a Contoso é criar seu próprio aplicativo personalizado do Power BI embedded com autenticação personalizada (['Aplicativo possui dados'](https://docs.microsoft.com/power-bi/developer/embed-sample-for-customers)). Embora muitas organizações não têm tempo ou recursos para criar um aplicativo personalizado para o Power BI de distribuir conteúdo para seus parceiros externos, para algumas organizações essa é a melhor abordagem e merece uma consideração séria.

Muitas vezes, as organizações têm portais de parceiro existente que centralizem o acesso a todos os recursos organizacionais para parceiros, fornecem isolamento de recursos organizacionais internos e fornecem uma experiência simplificada para parceiros dar suporte a muitos parceiros e seus usuários individuais.

![Muitos portais de parceiro](media/whitepaper-azure-b2b-power-bi/whitepaper-azure-b2b-power-bi_45.png)

No exemplo acima, os usuários de cada logon do fornecedor para o Portal de parceiros da Contoso que usa o AAD como um provedor de identidade. Ele poderia usar AAD B2B, o Azure B2C, identidades nativas ou federar com qualquer número de outros provedores de identidade. O usuário seria fazer logon e acessar uma compilação de portal de parceiro usando o aplicativo Web do Azure ou uma infraestrutura semelhante.

Dentro do aplicativo web, os relatórios do Power BI são inseridos de uma implantação do Power BI Embedded. O aplicativo web seria simplificar o acesso a relatórios e todos os serviços relacionados em uma experiência coesa com o objetivo tornar mais fácil para os fornecedores interagir com a Contoso. Este ambiente do portal seriam isolado do Contoso AAD interno e ambiente interno do Power BI da Contoso para garantir que os fornecedores não foi possível acessar esses recursos. Normalmente, os dados serão armazenados em um data warehouse separado do parceiro para garantir o isolamento de dados também. Esse isolamento tem benefícios, já que limita o número de usuários externos com acesso direto aos dados da sua organização, limitando a quais dados potencialmente poderia estar disponíveis para o usuário externo e limitando o compartilhamento acidental com usuários externos.

Usando o Power BI Embedded, o portal pode aproveitar o licenciamento vantajoso, usando o token de aplicativo ou o usuário mestre mais capacidade premium adquirido no modelo do Azure, o que simplifica questões sobre como atribuir licenças aos usuários finais e pode escalar verticalmente/inativo com base na esperado uso. O portal pode oferecer uma qualidade mais alta geral e uma experiência consistente, pois os parceiros acessar um portal único projetado com todas as necessidades de um parceiro em mente. Por fim, uma vez que o Power BI Embedded com base em soluções geralmente são projetadas para ser multilocatário, ela torna mais fácil garantir o isolamento entre organizações parceiras.

Motivos para escolher essa alternativa:

- Cresce mais fácil de gerenciar como o número de organizações parceiras. Uma vez que os parceiros são adicionados a um diretório separado isolado do diretório do AAD interno da Contoso, ele simplifica tarefas de governança e ajuda a impedir o compartilhamento acidental de dados internos para usuários externos.
- Típico portais de parceiro são altamente da marca experiências com experiências consistentes entre parceiros e simplificados para atender às necessidades dos parceiros típicos. A Contoso, portanto, pode oferecer uma melhor experiência geral aos parceiros, integrando todos os serviços necessários em um único portal.
- Custos de licenciamento para cenários avançados, como o conteúdo de edição dentro do Power BI Embedded é coberto por do Azure adquirido o Power BI Premium e não exigir a atribuição de licenças do Power BI Pro aos usuários.
- Fornece melhor isolamento entre parceiros se projetado como uma solução de multilocatário.
- O Portal de parceiros geralmente inclui outras ferramentas para parceiros, além de aplicativos, painéis e relatórios do Power BI.

Motivos para não escolher essa alternativa:

- Esforço significativo é necessário para compilar, operar e manter tal um portal tornando-o um investimento significativo no tempo e recursos.
- Tempo para a solução é muito mais do que usar o compartilhamento de B2B desde o planejamento cuidadoso e execução em vários fluxos de trabalho é necessária.
- Em que há um número menor de parceiros o esforço necessário para essa alternativa provavelmente é muito alto para justificar.
- Colaboração com o compartilhamento de ad hoc é o cenário principal enfrentado pela sua organização.
- Os relatórios e dashboards são diferentes para cada parceiro. Essa alternativa apresenta o gerenciamento de sobrecarga além de apenas compartilhar diretamente com parceiros.



## <a name="faq"></a>PERGUNTAS FREQUENTES

**A Contoso pode enviar um convite resgatado automaticamente, para que o usuário simplesmente esteja "pronto para ir"? Ou o usuário sempre que clicar em para a URL de resgate?**

O usuário final deve sempre clique por meio da experiência de consentimento antes que possam acessar o conteúdo.

Se você irá convidando muitos usuários convidados, é recomendável que você delegue isso de seus administradores de núcleo do Azure AD por [adicionando um usuário à função emissor do convite para convidado na organização do recurso](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-add-guest-to-role). Esse usuário pode convidar outros usuários na organização do parceiro, usando a IU de entrada, scripts do PowerShell ou APIs. Isso reduz a sobrecarga administrativa em seus administradores do Azure AD para convidar ou reenviadas convites aos usuários da organização parceira.

**A Contoso pode forçar a autenticação multifator para usuários convidados se seus parceiros não tem a autenticação multifator?**

Sim. Para obter mais informações, consulte [acesso condicional para usuários de colaboração B2B](https://docs.microsoft.com/azure/active-directory/active-directory-b2b-mfa-instructions).

**Como a colaboração B2B funciona quando o parceiro convidado estiver utilizando federação para adicionar sua própria autenticação local?**

Se o parceiro tiver um locatário do Azure AD federado à infraestrutura de autenticação local, no local logon único (SSO) será feito automaticamente. Se o parceiro não tiver um locatário do AD do Azure, uma conta do AD do Azure pode ser criada para novos usuários.

**Eu convidar usuários com contas de email do consumidor?**

Há suporte para convidar usuários com contas de email do consumidor no Power BI. Isso inclui domínios como hotmail.com, outlook.com e gmail.com. No entanto, esses usuários podem enfrentar as limitações além dos quais os usuários com funcionam ou encontram contas de estudante.
