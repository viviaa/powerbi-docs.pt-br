---
title: Conectar-se ao Zuora com o Power BI
description: Zuora para o Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/24/2018
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: 605cd2f135ff6d8626586abbd503bcb44687931d
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61156877"
---
# <a name="connect-to-zuora-with-power-bi"></a>Conectar-se ao Zuora com o Power BI
O Zuora para Power BI permite visualizar dados importantes de receita, de cobrança e de assinatura. Use o painel e os relatórios padrão para analisar tendências de uso, rastrear cobranças e pagamentos e monitorar receitas recorrentes ou personalizá-las para atender às suas necessidades exclusivas de painel e relatório.

Conecte-se ao [Zuora](https://app.powerbi.com/getdata/services/Zuora) para o Power BI.

## <a name="how-to-connect"></a>Como se conectar
1. Selecione **Obter Dados** na parte inferior do painel de navegação esquerdo.

   ![](media/service-connect-to-zuora/getdata.png)
2. Na caixa **Serviços** , selecione **Obter**.

   ![](media/service-connect-to-zuora/services.png)
3. Selecione **Zuora** \>  **Obter**.

   ![](media/service-connect-to-zuora/zuora.png)
4. Especifique a URL do Zuora. A URL normalmente é "<https://www.zuora.com>", confira detalhes sobre [como encontrar esses parâmetros](#FindingParams) abaixo.

   ![](media/service-connect-to-zuora/params.png)
5. Para o **Método de Autenticação**, selecione **Básico** e forneça seu nome de usuário e sua senha (diferencia maiúsculas de minúsculas) e selecione **Entrar**.

    ![](media/service-connect-to-zuora/creds.png)
6. Após a aprovação, o processo de importação será iniciado automaticamente. Quando concluído, um painel, um relatório e um modelo novos aparecerão no Painel de Navegação. Selecione o painel para exibir os dados importados por você.

     ![](media/service-connect-to-zuora/dashboard.png)

**E agora?**

* Tente [fazer uma pergunta na caixa de P e R](consumer/end-user-q-and-a.md) na parte superior do dashboard
* [Altere os blocos](service-dashboard-edit-tile.md) no dashboard.
* [Selecione um bloco](consumer/end-user-tiles.md) para abrir o relatório subjacente.
* Enquanto seu conjunto de dados será agendado para ser atualizado diariamente, você pode alterar o agendamento de atualização ou tentar atualizá-lo sob demanda usando **Atualizar Agora**

## <a name="whats-included"></a>O que está incluído
O pacote de conteúdo usa a API AQUA do Zuora para efetuar pull das seguintes tabelas:

| Tabelas |  |  |
| --- | --- | --- |
| Account |InvoiceItemAdjustment |Refund |
| AccountingCode |Payment |RevenueSchedule |
| AccountingPeriod |PaymentMethod |RevenueScheduleItem |
| BillTo |Product |Subscription |
| DateDim |ProductRatePlan |TaxationItem |
| Invoice |ProductRatePlanCharge |Uso |
| InvoiceAdjustment |RatePlan | |
| InvoiceItem |RatePlanCharge | |

Ela também inclui as medidas calculadas abaixo:

| Medida | Descrição | Pseudocálculo |
| --- | --- | --- |
| Conta: pagamentos |Valores totais de pagamento em um período de tempo, com base na data de efetivação do pagamento. |SUM (Payment.Amount) <br>EM QUE<br>Payment.EffectiveDate =< TimePeriod.EndDate<br>AND    Payment.EffectiveDate >= TimePeriod.StartDate |
| Conta: Reembolsos |Valores totais de reembolso em um período de tempo, com base na data de reembolso. O valor é relatado como um número negativo. |-1*SUM (Refund.Amount)<br>EM QUE<br>Refund.RefundDate =< TimePeriod.EndDate<br>E Refund.RefundDate >= TimePeriod.StartDate |
| Conta: pagamentos líquidos |Pagamentos de Conta mais Reembolsos de Conta em um período de tempo. |Account.Payments + Account.Refunds |
| Conta: contas ativas |A contagem de contas ativas em um período de tempo. As assinaturas devem ter sido iniciadas na data de início de um período de tempo ou antes dela. |COUNT (Account.AccountNumber)<br>EM QUE<br>    Subscription.Status != "Expired"<br>E Subscription.Status != "Draft"<br>E Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>E (Subscription.SubscriptionEndDate > TimePeriod.StartDate<br>OR<br>Subscription.SubscriptionEndDate = null) – assinatura perene |
| Conta: receita média recorrente |MRR bruta por conta ativa em um período de tempo. |Gross MRR/Account.ActiveAccounts |
| Conta: assinaturas canceladas |O número de contas que cancelaram uma assinatura em um período de tempo. |COUNT (Account.AccountNumber)<br>EM QUE<br>Subscription.Status = "Cancelled"<br>E Subscription.SubscriptionStartDate <= TimePeriod.StartDate<br>E Subscription.CancelledDate >= TimePeriod.StartDate |
| Conta: erros de pagamento |Valor total de erros de pagamento. |SUM (Payment.Amount)<br>EM QUE<br>Payment.Status = "Error" |
| Item de agendamento de receita: receita reconhecida |Receita total reconhecida em um período de contabilidade. |SUM (RevenueScheduleItem.Amount)<br>EM QUE<br>AccountingPeriod.StartDate = TimePeriod.StartDate |
| Assinatura: novas assinaturas |Contagem de novas assinaturas em um período de tempo. |COUNT (Subscription.ID)<br>EM QUE<br>Subscription.Version = "1"<br>E Subscription.CreatedDate <= TimePeriod.EndDate<br>E Subscription.CreatedDate >= TimePeriod.StartDate |
| Fatura: Itens da fatura |Valores totais de encargos de item da fatura em um período de tempo. |SUM (InvoiceItem.ChargeAmount)<br>EM QUE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate &lt;= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate &gt;= TimePeriod.StartDate |
| Fatura: Fatura: itens de tributação |Valores totais de item de tributação em um período de tempo. |SUM (TaxationItem.TaxAmount)<br>EM QUE<br>Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate &lt;= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate &gt;= TimePeriod.StartDate |
| Fatura: Fatura: ajustes de item da fatura |Valores totais de ajuste de item da fatura em um período de tempo. |SUM (InvoiceItemAdjustment.Amount) <br>EM QUE<br>    Invoice.Status = "Posted"<br>AND    InvoiceItemAdjustment.AdjustmentDate &lt;= TimePeriod.EndDate<br>E InvoiceItemAdjustment.AdjustmentDate &gt;= TimePeriod.StartDate |
| Fatura: Ajustes da fatura |Valores totais de ajuste de fatura em um período de tempo. |SUM (InvoiceAdjustment.Amount) <br>EM QUE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.AdjustmentDate &lt;= TimePeriod.EndDate<br>E InvoiceAdjustment.AdjustmentDate &gt;= TimePeriod.StartDate |
| Fatura: Cobranças líquidas |Soma dos itens da fatura, itens de tributação, ajustes de item da fatura e ajustes da fatura em um período de tempo. |Invoice.InvoiceItems + Invoice.TaxationItems + Invoice.InvoiceItemAdjustments + Invoice.InvoiceAdjustments |
| Fatura: saldo de vencimento da fatura |Soma do saldo de faturas lançadas. |SUM (Invoice.Balance) <br>EM QUE<br>    Invoice.Status = "Posted" |
| Fatura: cobranças brutas |Soma dos valores de cobrança de item da fatura para faturas lançadas em um período de tempo. |SUM (InvoiceItem.ChargeAmount) <br>EM QUE<br>    Invoice.Status = "Posted"<br>AND    Invoice.InvoiceDate &lt;= TimePeriod.EndDate<br>AND    Invoice.InvoiceDate &gt;= TimePeriod.StartDate |
| Fatura: total de ajustes |Soma de ajustes de fatura processados e ajustes de item de fatura associados às faturas lançadas. |SUM (InvoiceAdjustment.Amount) <br>EM QUE<br>    Invoice.Status = "Posted"<br>AND    InvoiceAdjustment.Status = "Processed"<br>+<br>SUM (InvoiceItemAdjustment.Amount) <br>EM QUE<br>    Invoice.Status = "Posted"<br>AND    invoiceItemAdjustment.Status = "Processed" |
| Encargo de plano de taxa: MRR bruta |Soma da receita mensal recorrente das assinaturas em um período de tempo. |SUM (RatePlanCharge.MRR) <br>EM QUE<br>    Subscription.Status != "Expired"<br>E Subscription.Status != "Draft"<br>E RatePlanCharge.EffectiveStartDate <= TimePeriod.StartDate<br>AND        RatePlanCharge.EffectiveEndDate > TimePeriod.StartDate<br>    OU RatePlanCharge.EffectiveEndDate = null --evergreen subscription |

## <a name="system-requirements"></a>Requisitos de sistema
É necessário ter acesso à API do Zuora.

<a name="FindingParams"></a>

## <a name="finding-parameters"></a>Localizando parâmetros
Forneça a URL com a qual você normalmente se conecta para acessar seus dados do Zuora. As opções válidas são:  

* https://www.zuora.com  
* O URL correspondente à sua instância de serviço  

## <a name="troubleshooting"></a>Solução de problemas
O pacote de conteúdo do Zuora mantém vários aspectos diferentes da sua conta do Zuora. Se você não usar determinados recursos, poderá ver blocos/relatórios correspondentes vazios. Entre em contato com o suporte do Power BI se você tiver problemas ao carregar.

## <a name="next-steps"></a>Próximas etapas
[Introdução ao Power BI](service-get-started.md)

[Obter dados no Power BI](service-get-data.md)
