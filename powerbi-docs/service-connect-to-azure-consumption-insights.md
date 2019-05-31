---
title: Conectar-se ao Microsoft Azure Consumption Insights com o Power BI
description: Microsoft Azure Consumption Insights para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggies
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 05/20/2019
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 089f8c31a0b1eb11f6871268f2f848949be95d9b
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66222118"
---
# <a name="connect-to-microsoft-azure-consumption-insights-with-power-bi"></a>Conectar-se ao Microsoft Azure Consumption Insights com o Power BI
Explore e monitore seus dados de consumo do Microsoft Azure no Power BI com o pacote de conteúdo do Power BI. Os dados são atualizados automaticamente uma vez por dia.

Conecte-se ao [Pacote de conteúdo de consumo de informações do Microsoft Azure](https://app.powerbi.com/getdata/services/azureconsumption) para o Power BI.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.
   
    ![](media/service-connect-to-azure-consumption-insights/getdata.png)
2. Na caixa **Serviços** , selecione **Obter**.
   
   ![](media/service-connect-to-azure-consumption-insights/services.png)
3. Selecione **Microsoft Azure Consumption Insights** \> **obtê-lo agora**. 
   
   ![](media/service-connect-to-azure-consumption-insights/mazureconsumption.png)
4. Forneça o número de meses de dados que deseja importar e seu número de registro do Azure Enterprise. Veja detalhes sobre [como encontrar esses parâmetros](#FindingParams) abaixo.
   
    ![](media/service-connect-to-azure-consumption-insights/azureconsumptionparams.png)
5. Forneça sua Chave de acesso para se conectar. Você pode encontrar sua chave de registro no Portal de EA do Azure. 
   
    ![](media/service-connect-to-azure-consumption-insights/msazureconsumptioncreds.png)
6. O processo de importação é iniciado automaticamente. Ao concluir, um novo painel, relatório e modelo são exibidos no painel de navegação. Selecione o painel para exibir os dados importados por você.
   
   ![](media/service-connect-to-azure-consumption-insights/msazureconsumptiondashboard.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados é agendado para atualizar diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **atualizar agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdo do Microsoft Azure Consumption Insights inclui relatórios mensais de dados para o intervalo de meses que você forneceu ao se conectar. O intervalo é uma janela móvel, portanto, as datas incluídas são atualizadas à medida que atualiza o conjunto de dados.

## <a name="system-requirements"></a>Requisitos do sistema
O pacote de conteúdo requer acesso aos recursos do Enterprise no portal do Azure. 

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Localizando parâmetros
Relatórios do Power BI estão disponível para EA direto, parceiros e clientes indiretos que podem exibir informações de cobrança. Leia abaixo para obter detalhes sobre a localização de cada um dos valores espera que o fluxo de conexão.

**Número de meses**

* O número de meses (1 a 36) de dados a partir de hoje que você deseja importar.

**Número de registro**

* Seu número de registro do Azure Enterprise, você pode encontrar na [Azure Enterprise Portal](https://ea.azure.com/) tela inicial sob **detalhes do registro**.
  
    ![](media/service-connect-to-azure-consumption-insights/params2.png)

**Tecla de acesso**

* Você pode encontrar sua chave de acesso no portal do Azure Enterprise, sob **baixar uso** > **chave de acesso de API**.
  
    ![](media/service-connect-to-azure-consumption-insights/creds2.png)

**Ajuda adicional**

* Para obter ajuda adicional sobre como configurar o pacote do Azure Enterprise Power BI, entre no Azure Enterprise Portal e exibir o arquivo de Ajuda da API sob **ajudar**. Você também pode encontrar as instruções adicionais em **relatórios** -> **baixar uso** -> **chave de acesso de API**.

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)

