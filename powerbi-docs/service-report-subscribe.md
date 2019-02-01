---
title: Obtenha uma assinatura para você e outras pessoas de relatórios e dashboards no serviço do Power BI
description: Saiba como obter uma assinatura para você e outras pessoas de um instantâneo de um relatório ou um dashboard do Power BI.
author: maggiesMSFT
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 01/29/2019
ms.author: maggies
LocalizationGroup: Common tasks
ms.openlocfilehash: a7c9c72dfbb75958be3119db61fa3aa03ac89171
ms.sourcegitcommit: a36f82224e68fdd3489944c9c3c03a93e4068cc5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55430937"
---
# <a name="subscribe-yourself-and-others-to-a-report-or-dashboard-in-the-power-bi-service"></a>Assine e obtenha assinaturas para terceiros de um relatório ou um dashboard no serviço do Power BI

Você pode assinar e obter assinaturas para seus colegas das páginas de relatórios e os dashboards mais importantes para vocês. O Power BI enviará um instantâneo por email para sua caixa de entrada. Informe ao Power BI a frequência com que deseja receber os emails: diária, semanal ou uma vez ao dia quando os dados forem atualizados.  Se escolher diária ou semanal, você poderá escolher as horas em que você gostaria que a assinatura executasse.  No total, você pode definir até 24 assinaturas diferentes por dia, para cada página de relatório e dashboard.

![instantâneo de email de dashboard](media/service-report-subscribe/power-bi-dashboard-email-new.jpg) 

Você só pode criar assinaturas no serviço do Power BI. Você receberá um email com um instantâneo da página de relatório ou dashboard, com um link para abrir o relatório ou o dashboard. Em dispositivos móveis com aplicativos do Power BI instalados, a seleção desse link iniciará o aplicativo do Power BI em vez de abrir o relatório ou o dashboard no site do Power BI.

## <a name="requirements"></a>Requisitos
- A **Criação** de assinaturas é um recurso do Power BI Pro.
- Você não precisa editar permissões para o conteúdo (dashboard ou relatório) para criar uma assinatura para si próprio, mas precisa ter permissões de edição para criar uma para outra pessoa. 
- Desde janeiro de 2019, você não precisa ter a atualização de conjunto de dados configurada para executar uma assinatura.  Ela será executada independentemente de quaisquer atualizações agendadas que você tiver configurado.  

## <a name="subscribe-to-a-dashboard-or-a-report-page"></a>Assine um dashboard ou uma página de relatório
Se você estiver assinando um dashboard ou um relatório, o processo será semelhante. O mesmo botão permite que você assine os dashboards e relatórios do serviço do Power BI.
 
![selecione o ícone Assinar](media/service-report-subscribe/power-bi-subscribe-orientation.png).

1. Abra o dashboard ou o relatório.
2. Na barra de menus superior, selecione **Assinar** ou selecione o ícone de envelope ![ícone Assinar](media/service-report-subscribe/power-bi-icon-envelope.png).
   
   ![Ícone Assinar](media/service-report-subscribe/power-bi-subscribe-icon.png)

3. Use o controle deslizante amarelo para ativar e desativar a assinatura.  Definir o controle deslizante como **Desativado** não exclui a assinatura. Para excluir a assinatura, selecione o ícone de cesto de lixo.

4. Seu email já está na caixa **Assinar**. Você pode adicionar outros endereços de email para a assinatura também, mas apenas no mesmo domínio. Se o relatório ou o dashboard estiver hospedado na [capacidade Premium](service-premium.md), você poderá assinar outros endereços de email individuais e aliases de grupo. Se o relatório ou o dashboard não estiver hospedado na capacidade Premium, você poderá assinar outros indivíduos, mas eles também precisarão ter licenças do Power BI Pro. Para obter detalhes, veja [Considerações e solução de problemas](#considerations-and-troubleshooting) abaixo. 

5. Preencha os detalhes **Assunto** e **Mensagem** do email. 

5. Selecione uma **Frequência** para sua assinatura: **Diária**, **Semanal** ou **Após a atualização de dados (Diária)**.  Para receber o email de assinatura somente em determinados dias, selecione **Semanal** e escolha em quais dias você gostaria de recebê-lo.  Por exemplo, se você quiser receber o email de assinatura somente em dias úteis, selecione **Semanal** e desmarque as caixas **Sáb** e **Dom**.  

6. Se escolher **Diária** ou **Semanal**, você também poderá escolher uma **Hora Agendada** para a assinatura.  Você faz com que ela seja executada na hora exata ou após 15, 30 ou 45 minutos.  Selecione manhã (A.M.) ou tarde/noite (P.M.). Você também pode especificar o fuso horário.

7. Por padrão, a data de início para a sua assinatura é a data em que você a cria. Você tem a opção de selecionar uma data de término. Se você não definir uma data de término, a data de término será definida automaticamente para um ano após a data de início. É possível alterar para qualquer data no futuro (até o ano 9999) a qualquer momento antes do término da assinatura. Quando uma assinatura atinge uma data de término, ela é interrompida até que você a habilite novamente. Você receberá notificações antes da data de término agendada, perguntando se deseja estendê-la.    

    Na captura de tela abaixo, observe que quando você assina um relatório, na verdade, você está assinando uma *página* de relatório.  Para assinar mais de uma página em um relatório, selecione **Adicionar outra assinatura** e selecione uma página diferente. 
      
   ![Painel Assinar](media/service-report-subscribe/power-bi-subscribe-pane.png)  

7. Selecione **Salvar e fechar**. Os inscritos receberão um email e o instantâneo da página de relatório ou dashboard para a frequência e a hora que você selecionou. No total, você pode criar até 24 assinaturas por relatório ou dashboard e pode fornecer frequências, horas e destinatários exclusivos para cada assinatura.  Todas as assinaturas definidas para **Após a atualização de dados** do seu dashboard ou relatório somente enviarão um email após a primeira atualização agendada.   
      
   > [!TIP]
   > Deseja ver o email agora mesmo? Dispare um email ao atualizar um dos conjuntos de dados associados ao dashboard ou o conjunto de dados associado ao relatório. Se não tiver permissões de edição para o conjunto de dados, peça que alguém que as tenha atualize-o para você. Para ver os conjuntos de dados relacionados, selecione o ícone **Exibir relacionados** ![ícone de Exibir relacionados](media/service-report-subscribe/power-bi-view-related.png) para abrir o **Conteúdo relacionado** e, em seguida, selecione o ícone de atualização ![ícone de atualização](media/service-report-subscribe/power-bi-refresh.png). 
   > 
   > 
   
   ![Conjuntos de dados relacionados](media/service-report-subscribe/power-bi-view-related-screen.png)

## <a name="email-languages"></a>Idiomas do Email

O instantâneo e o email usam o idioma definido nas configurações do Power BI (confira [Idiomas e países/regiões com suporte para o Power BI](supported-languages-countries-regions.md)). Se nenhum idioma for definido, o Power BI usará o idioma de acordo com a configuração de localidade no navegador atual. Para obter ou definir sua preferência de idioma, selecione o ícone de engrenagem ![ícone de engrenagem](media/service-report-subscribe/power-bi-settings-icon.png) > **Configurações > Geral > Idioma**. 

![Lista suspensa Idioma](media/service-report-subscribe/power-bi-language.png)

## <a name="manage-your-subscriptions"></a>Gerenciar suas assinaturas
Somente a pessoa que criou a assinatura possa gerenciá-la.  Há dois caminhos que levam à tela para gerenciar suas assinaturas.  O primeiro é selecionando **Gerenciar todas as assinaturas** na caixa de diálogo **Assinar emails** (confira as capturas de tela abaixo da etapa 4 acima). O segundo é selecionar o ícone de engrenagem ![ícone de engrenagem](media/service-report-subscribe/power-bi-settings-icon.png) do Power BI na barra de menus superior e escolher **Configurações**.

![selecionar Configurações](media/service-report-subscribe/power-bi-subscribe-settings.png)

As assinaturas específicas exibidas dependerão de qual workspace está ativo no momento.  Para ver todas as suas assinaturas de todos os workspaces ao mesmo tempo, verifique se **Meu Workspace** está ativo. Para obter ajuda para entender os workspaces, consulte [Workspaces no Power BI](service-create-workspaces.md).

![veja todas as assinaturas no Meu workspace](media/service-report-subscribe/power-bi-subscriptions.png)

Uma assinatura será encerrada se a licença Pro expirar, se o proprietário excluir o dashboard ou o relatório ou se a conta de usuário usada para criar a assinatura for excluída.

## <a name="considerations-and-troubleshooting"></a>Considerações e solução de problemas
* Para assinaturas de email do dashboard, se quaisquer blocos tiverem a RLS (Segurança em Nível de Linha) aplicada, esses blocos não serão exibidos.  Para assinaturas de email do relatório, se o conjunto de dados usar a RLS, não será possível criar uma assinatura.
* As assinaturas da página de relatório são vinculadas ao nome da página de relatório. Se você assinar uma página de relatório e renomeá-la, precisará recriar sua assinatura.
* Sua organização pode definir certas configurações no Azure Active Directory que limitam a capacidade de usar assinaturas de email no Power BI.  Essas limitações incluem, sem limitação, ter autenticação multifator ou restrições de intervalo de IP ao acessar recursos.
* Atualmente, as assinaturas de email para relatórios/dashboards que usam conjuntos de dados de conexão dinâmica não têm suporte para inscrever outros usuários, exceto a si próprio.
* Assinaturas de email não dão suporte à maioria dos [visuais personalizados](power-bi-custom-visuals.md).  A única exceção é para os elementos visuais personalizados que foram [certificados](power-bi-custom-visuals-certified.md).  
* No momento, as assinaturas de email não dão suporte a visuais personalizados da plataforma R.  
* Se algum bloco do dashboard tiver a RLS (Segurança em Nível de Linha) aplicada, esse bloco não será exibido.
* Você não pode inscrever outros usuários em um relatório que tem RLS (Segurança em Nível de Linha) aplicada.
* Assinaturas de email são enviadas com estados de segmentação e filtro padrão do relatório. As alterações feitas nos padrões após a assinatura não serão exibidas no email.    
* Especificamente para assinaturas de dashboards, ainda não há suporte para alguns tipos de blocos.  Eles incluem: blocos de streaming, blocos de vídeo, blocos de conteúdo da Web personalizado.     
* Se você compartilhar um dashboard com um colega fora de seu locatário, não será possível criar uma assinatura para esse colega também. Portanto, se você for aaron@xyz.com, poderá compartilhar com anyone@ABC.com, mas ainda não poderá incluir anyone@ABC.com, e ele não poderá assinar o conteúdo compartilhado.      
* As assinaturas poderão falhar em dashboards ou relatórios com imagens extremamente grandes devido aos limites de tamanho de email.    
* O Power BI pausa a atualização automaticamente em conjuntos de dados associados a dashboards e relatórios que não foram visitados há mais de dois meses.  No entanto, se você adicionar uma assinatura a um dashboard ou um relatório, ele não ficará em pausa mesmo que não seja visitado.    
* Se você não estiver recebendo emails de assinatura, verifique se o nome UPN pode receber emails. [A equipe do Power BI está trabalhando para atenuar esse requisito](https://community.powerbi.com/t5/Issues/No-Mail-from-Cloud-Service/idc-p/205918#M10163), portanto, fique ligado. 
* Se o painel ou o relatório estiver na capacidade Premium, você poderá usar o alias de email de grupo para assinaturas, em vez de inserir um endereço de email de colega de cada vez na assinatura. Os aliases são baseados no Active Directory atual. 

## <a name="next-steps"></a>Próximas etapas
* Mais perguntas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/)    
* [Ler a postagem no blog](https://powerbi.microsoft.com/blog/introducing-dashboard-email-subscriptions-a-360-degree-view-of-your-business-in-your-inbox-every-day/)

