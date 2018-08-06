---
title: Extensibilidade do conector no Power BI
description: Funcionalidades de extensibilidade do conector, recursos, configurações de segurança e conectores certificados
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/25/2018
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: c63357df043ff6a646562d398a07d8042dd5a0ee
ms.sourcegitcommit: 7fb0b68203877ff01f29724f0d1761d023075445
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2018
ms.locfileid: "39256529"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidade do conector no Power BI

No Power BI, clientes e desenvolvedores podem estender de várias maneiras as fontes de dados às quais podem se conectar, por exemplo, usando conectores existentes e fontes de dados genéricas (por exemplo, ODBC, OData, Oledb, Web, CSV, XML, JSON). Além dessas fontes de dados, os desenvolvedores podem criar extensões de dados denominadas **Conectores Personalizados** e certificar um conector para que ele se torne um **Conector Certificado**.

Nas versões anteriores do Power BI, a capacidade de usar **Conectores Personalizados** era habilitada usando um comutador de recurso. Agora, há um menu que permite que você controle com segurança o nível de código personalizado que deseja permitir que seja executado no sistema: todos os conectores personalizados ou somente os conectores certificados e distribuídos pela Microsoft, na caixa de diálogo **Obter Dados**.

## <a name="custom-connectors"></a>Conectores personalizados

Os **Conectores Personalizados** podem incluir uma ampla gama de possibilidades que variam de pequenas APIs essenciais para os negócios, até grandes serviços específicos do setor que a Microsoft ainda não implementou. A maioria desses conectores será distribuída pelos próprios fornecedores. Se você precisar de um conector de dados específico, contate um fornecedor.

Para usar um **Conector Personalizado**, coloque-o na pasta *\[Documentos]\\Power BI Desktop\\Conectores Personalizados* e ajuste as configurações de segurança, conforme descrito na seção a seguir.

Você não precisa ajustar as configurações de segurança para usar **Conectores Certificados**.

## <a name="data-extension-security"></a>Segurança da extensão de dados

Para alterar as configurações de segurança da extensão de dados, em **Power BI Desktop** selecione **Arquivo > Opções e Configurações > Opções > Segurança**.

![Controlar se você deseja ser capaz de carregar os conectores personalizados com opções de segurança da extensão de dados](media/desktop-connector-extensibility/data-extension-security-1.png)

Em **Extensões de Dados**, você pode selecionar dois níveis de segurança:

* (Recomendado) Permitir o carregamento somente de extensões certificadas
* (Não recomendado) Permitir o carregamento de qualquer extensão sem aviso

Se você planeja usar **Conectores Personalizados** ou conectores que você ou terceiros desenvolveram e distribuíram selecione **(Não recomendado) Permitir o carregamento de qualquer extensão sem aviso**. Não recomendamos essa configuração de segurança, a menos que você planeje executar **Conectores Personalizados**.

Na configuração de segurança **(Recomendado)**, se houver conectores personalizados em seu sistema, um erro será exibido descrevendo os conectores que não podem ser carregados devido à segurança.

![Uma caixa de diálogo descreverá os Conectores Personalizados que não podem ser carregados devido às configurações de segurança, nesse caso, o TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Para resolver o erro e usar esses conectores, altere suas configurações de segurança para a configuração **(Não recomendado)** descrita anteriormente e reinicie o **Power BI Desktop**.

## <a name="certified-connectors"></a>Conectores certificados

Um subconjunto limitado de extensões de dados são consideradas **Certificadas**, e esses conectores certificados estão disponíveis pela caixa de diálogo **Obter Dados**, mas a parte responsável por manutenção e suporte ainda é o desenvolvedor de terceiros que criou o conector. Embora a Microsoft os distribua, ela não é responsável pelo desempenho ou pela funcionalidade contínua desses conectores.

Se você deseja que um conector personalizado seja certificado, peça ao seu fornecedor que contate a Microsoft.
