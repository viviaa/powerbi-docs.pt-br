---
title: Conectar-se ao Project Online com o Power BI
description: Project Online para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: dd6698cab5b9fed407e6e8f45ceb160209a38fae
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/04/2019
ms.locfileid: "54007558"
---
# <a name="connect-to-project-online-with-power-bi"></a>Conectar-se ao Project Online com o Power BI
Microsoft Project Online é uma solução online flexível para PPM (gerenciamento de portfólio de projetos) e para o trabalho cotidiano. O Project Online permite que as organizações comecem, priorizem investimentos de portfólio de projetos e entreguem o valor comercial pretendido. O pacote de conteúdo do Project Online para o Power BI permite desbloquear insight do Project Online para ajudar a gerenciar recursos, projetos e portfólios.

Conecte-se ao [pacote de conteúdo do Project Online](https://app.powerbi.com/getdata/services/project-online) para o Power BI.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![](media/service-connect-to-project-online/getdata.png)
2. Na caixa **Serviços** , selecione **Obter**.
   
   ![](media/service-connect-to-project-online/services.png)
3. Selecione **Microsoft Project Online** \> **Obter**.
   
   ![](media/service-connect-to-project-online/mproject.png)
4. Na caixa de texto **URL do Project Web App** , digite a URL para o PWA (Project Web Add) à qual você deseja se conectar e pressione **Avançar**. Observe que isso pode ser diferente do exemplo, caso você tenha um domínio personalizado. Na caixa de texto **Idioma do site do PWA**, digite o número que corresponde ao seu idioma de site do PWA. Digite “1” para inglês, “2” para francês, “3” para alemão, “4” para português (Brasil), “5” para português (Portugal) e “6” para espanhol. 
   
    ![](media/service-connect-to-project-online/params.png)
5. Para o Método de Autenticação, selecione **oAuth2** \> **Entrar**. Quando solicitado, insira suas credenciais do Project Online e siga o processo de autenticação.
   
    ![](media/service-connect-to-project-online/creds.png)
    
Observe que você precisa ter as permissões Visualizador de portfólio, Gerente de portfólio ou Administrador do Project Web App ao qual você está se conectando.

6. Você verá uma notificação indicando que os dados estão sendo carregados. Dependendo do tamanho de sua conta, isso pode levar algum tempo. Após o Power BI importar os dados, você verá um novo dashboard, 13 relatórios e um conjunto de dados no painel de navegação esquerdo. Esse é o painel padrão criado pelo Power BI para exibir seus dados. Você pode alterar esse painel para exibir seus dados de qualquer modo que desejar.

   ![](media/service-connect-to-project-online/dashboard2.png)

7. Depois que o dashboard e os relatórios estiverem prontos, vá em frente e comece a explorar seus dados do Project Online! O pacote de conteúdo vem com 13 relatórios avançados e detalhados para a visão geral do portfólio (seis páginas de relatório), a visão geral de recursos (cinco páginas de relatório) e o status de projeto (duas páginas de relatório). 

   ![](media/service-connect-to-project-online/report1.png)
   
   ![](media/service-connect-to-project-online/report3.png)
   
   ![](media/service-connect-to-project-online/report2.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

**Expandir o pacote de conteúdo**

Baixe o [arquivo GitHub PBIT](https://github.com/OfficeDev/Project-Power-BI-Content-Packs) para personalizar ainda mais e atualizar o pacote de conteúdo

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

