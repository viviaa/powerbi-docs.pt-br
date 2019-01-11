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
ms.openlocfilehash: eaf76f2ba762a603bf37385ea00cd714499db4b5
ms.sourcegitcommit: 5206651c12f2b91a368f509470b46f3f4c5641e6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53983406"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidade do conector no Power BI

No Power BI, clientes e desenvolvedores podem estender de várias maneiras as fontes de dados às quais podem se conectar, por exemplo, usando conectores existentes e fontes de dados genéricas (por exemplo, ODBC, OData, Oledb, Web, CSV, XML, JSON). Além dessas fontes de dados, os desenvolvedores podem criar extensões de dados denominadas **Conectores Personalizados** e certificar um conector para que ele se torne um **Conector Certificado**.

Atualmente, a capacidade de usar **Conectores Personalizados** é habilitada por meio de um comutador de recurso. Antes de passar esse recurso de beta para disponibilidade geral, nós adicionamos um menu que permite controlar com segurança o nível de código personalizado que pode ser executado no sistema: todos os conectores personalizados ou apenas os conectores certificados e distribuídos pela Microsoft, na caixa de diálogo **Obter dados**.

## <a name="custom-connectors"></a>Conectores personalizados

Os **Conectores Personalizados** podem incluir uma ampla gama de possibilidades que variam de pequenas APIs essenciais para os negócios, até grandes serviços específicos do setor para os quais a Microsoft ainda não lançou um conector. A maioria desses conectores é distribuída pelos próprios fornecedores. Se você precisar de um conector de dados específico, contate o fornecedor.

Para usar um **Conector Personalizado**, coloque-o na pasta *\[Documentos]\\Power BI Desktop\\Conectores Personalizados* e ajuste as configurações de segurança, conforme descrito na seção a seguir.

Você não precisa ajustar as configurações de segurança para usar **Conectores Certificados**.

## <a name="data-extension-security"></a>Segurança da extensão de dados

Para alterar as configurações de segurança da extensão de dados, em **Power BI Desktop** selecione **Arquivo > Opções e Configurações > Opções > Segurança**.

![Controlar se você deseja ser capaz de carregar os conectores personalizados com opções de segurança da extensão de dados](media/desktop-connector-extensibility/data-extension-security-1.png)

Em **Extensões de Dados**, você pode selecionar dois níveis de segurança:

* (Recomendado) Permitir o carregamento somente de extensões certificadas
* (Não recomendado) Permitir o carregamento de qualquer extensão sem aviso

Se você planeja usar **Conectores Personalizados** ou conectores que você ou terceiros desenvolveram e distribuíram, selecione **“(Não recomendado) Permitir o carregamento de qualquer extensão sem aviso”**. Não recomendamos essa configuração de segurança, a menos que você confie plenamente em seus conectores personalizados, pois o código contido neles pode lidar com credenciais (incluindo enviá-las por HTTP) e ignorar os níveis de privacidade.

Na configuração de segurança **“(Recomendado)”**, se houver conectores personalizados em seu sistema, um erro será exibido descrevendo os conectores que não podem ser carregados devido à segurança.

![Uma caixa de diálogo descreverá os Conectores Personalizados que não podem ser carregados devido às configurações de segurança, nesse caso, o TripPin](media/desktop-connector-extensibility/data-extension-security-2.png)

Para resolver o erro e usar esses conectores, altere suas configurações de segurança para a configuração **“(Não recomendado)”** já descrita e reinicie o **Power BI Desktop**.

## <a name="certified-connectors"></a>Conectores certificados

Um subconjunto limitado de extensões de dados é considerado **Certificado**, e esses conectores certificados estão disponíveis pela caixa de diálogo **Obter Dados**, mas a parte responsável pela manutenção e pelo suporte ainda é o desenvolvedor de terceiros que criou o conector. Embora a Microsoft os distribua, ela não é responsável pelo desempenho ou pela funcionalidade contínua desses conectores.

Se você deseja que um conector personalizado seja certificado, solicite que seu fornecedor contate dataconnectors@microsoft.com.
