---
title: 'Tutorial: Conectar-se a um repositório do GitHub com o Power BI'
description: Neste tutorial, você se conecta a dados reais no serviço do GitHub com o Power BI, e Power BI cria dashboards e relatórios automaticamente.
author: maggiesMSFT
manager: kfile
ms.reviewer: SarinaJoan
ms.service: powerbi
ms.subservice: powerbi-service
ms.custom: connect-to-services
ms.topic: tutorial
ms.date: 04/19/2019
ms.author: maggies
LocalizationGroup: Connect to services
ms.openlocfilehash: 3aeb1fc16ae200399125a2366a8993d45aad34c4
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "64578621"
---
# <a name="tutorial-connect-to-a-github-repo-with-power-bi"></a>Tutorial: Conectar-se a um repositório do GitHub com o Power BI
Neste tutorial, você se conecta a dados reais no serviço do GitHub com o Power BI, e Power BI cria dashboards e relatórios automaticamente. Conectar-se para o repositório público do conteúdo do Power BI (também conhecido como um *repositório*) e ver respostas a perguntas como: Quantas pessoas contribuem com o conteúdo público do Power BI? Quem contribui mais? Qual dia da semana tem mais contribuições? E outras perguntas. 

![O relatório do GitHub no Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-punch-card.png)

Neste tutorial, você concluirá as etapas a seguir:

> [!div class="checklist"]
> * Inscrever-se para uma conta do GitHub, caso ainda não tenha uma 
> * Entrar em sua conta do Power BI ou inscrever-se, caso ainda não tenha uma
> * Abrir o serviço do Power BI
> * Encontrar o aplicativo GitHub
> * Inserir as informações do repositório GitHub público do Power BI
> * Exibir o dashboard e o relatório com os dados do GitHub
> * Limpar os recursos, excluindo o aplicativo

Se você não estiver inscrito no Power BI, [inscreva-se para uma avaliação gratuita](https://app.powerbi.com/signupredirect?pbi_source=web) antes de começar.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial, você precisará de uma conta do GitHub, caso ainda não tenha uma. 

- Inscreva-se um [conta do GitHub](https://docs.microsoft.com/contribute/get-started-setup-github).


## <a name="how-to-connect"></a>Como se conectar
1. Entre no serviço do Power BI (https://app.powerbi.com). 
2. No painel de navegação esquerdo, selecione **Aplicativos** e, em seguida, **Obter aplicativos**.
   
   ![Obter aplicativos do Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial.png) 

3. Selecione **aplicativos**, digite **GitHub** na caixa de pesquisa > **obter agora**.
   
   ![Get GitHub do Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-app-source.png) 

4. Na **instalar este aplicativo do Power BI?** selecionar **instalar**.
5. Na **seu novo aplicativo está pronto**, selecione **ir para o aplicativo**.
6. Na **começar com seu novo aplicativo**, selecione **Conecte dados**.

    ![Introdução ao novo aplicativo](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect-data.png)

7. Digite o nome do repositório e também o seu proprietário. A URL desse repositório é https://github.com/MicrosoftDocs/powerbi-docs, portanto o **Proprietário do Repositório** é **MicrosoftDocs** e o **Repositório** é **powerbi-docs**. 
   
    ![Nome do repositório do GitHub do Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-connect.png)

5. Insira as credenciais do GitHub que você criou. O Power BI poderá ignorar esta etapa se você já tiver entrado no GitHub em seu navegador. 

6. Para **método de autenticação**, mantenha **oAuth2** selecionado \> **entrar**.

7. Siga as telas de autenticação do GitHub. Conceda permissão para o Power BI aos dados do GitHub.
   
   Agora o Power BI pode se conectar ao GitHub e aos dados.  Os dados são atualizados uma vez por dia.

8. Depois que o Power BI importar os dados, você pode ver o conteúdo de seu novo espaço de trabalho do GitHub. 
9. Selecione a seta ao lado do nome do espaço de trabalho na barra de navegação à esquerda. Você ver que o espaço de trabalho contém um painel e um relatório. 

    ![Aplicativo no painel de navegação à esquerda](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav-expanded.png)

10. Selecione as reticências (...) ao lado do nome do dashboard > **renomeie** > digite **dashboard do GitHub**.
 
    ![Bloco do GitHub do Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-left-nav.png) 

8. Selecione o ícone de navegação global para minimizar o painel de navegação esquerdo, aumentando o espaço disponível.

    ![Ícone de navegação global](media/service-tutorial-connect-to-github/power-bi-global-navigation-icon.png)

10. Selecione seu dashboard do GitHub.
    
    O painel do GitHub contém dados reais, para que os valores que você vê podem ser diferentes.

    ![Dashboard do GitHub no Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-new-dashboard.png)

    

## <a name="ask-a-question"></a>Fazer uma pergunta

1. Coloque o cursor **faça uma pergunta sobre seus dados**. Power BI oferece **perguntas para introdução ao**. 

1. Selecione **quantos usuários estão lá**.
 
    ![Quantos usuários estão lá](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-users.png)

13. Entre os dois **quantos** e **usuários existem**, digite **solicitações por pull**. 

     Power BI cria um gráfico de barras mostrando o número de solicitações de pull por pessoa.

    ![Há quantas solicitações pull por usuário](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-qna-how-many-prs.png)


13. Selecionar para fixá-lo ao seu painel, em seguida, o pin **Exit p e r**.

## <a name="view-the-github-report"></a>Exibir o relatório do GitHub 

1. No painel do GitHub, selecione o gráfico de colunas **solicitações de Pull por mês** para abrir o relatório relacionado.

    ![Solicitações de pull pelo gráfico de coluna do mês](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-column-chart.png)

2. Selecione um nome de usuário na **solicitações de pull Total por usuário** gráfico. Neste exemplo, podemos ver que a maioria de suas horas foi em fevereiro.

    ![Realce do relatório do GitHub do Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-cross-filter-total-prs.png)

3. Selecione a guia **Cartão de Pontos** para exibir a próxima página do relatório. 
 
    ![Cartão de Pontos do relatório do GitHub do Power BI](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-tues-3pm.png)

    Aparentemente, terça-feira às 15h é o momento mais comum e o dia da semana para *confirma*, quando as pessoas fazer check-in de seu trabalho.

## <a name="clean-up-resources"></a>Limpar recursos

Agora que você já concluiu o tutorial, é possível excluir o aplicativo GitHub. 

1. Na barra de navegação esquerda, selecione **Aplicativos**.
2. Focalize o bloco do GitHub e selecione a lixeira **Excluir**.

    ![Excluir o aplicativo GitHub](media/service-tutorial-connect-to-github/power-bi-github-app-tutorial-delete.png)

## <a name="next-steps"></a>Próximas etapas

Neste tutorial, você se conectou a um repositório público do GitHub e obteve dados que o Power BI formatou em um dashboard e em um relatório. Você respondeu algumas perguntas sobre os dados explorando o dashboard e o relatório. Agora você pode aprender mais sobre como se conectar a outros serviços, como o Salesforce, o Microsoft Dynamics e o Google Analytics. 
 
> [!div class="nextstepaction"]
> [Conectar aos serviços online que você usa](service-connect-to-services.md)


