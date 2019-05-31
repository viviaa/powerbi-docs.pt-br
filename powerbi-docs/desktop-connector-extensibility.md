---
title: Extensibilidade do conector no Power BI
description: Funcionalidades de extensibilidade do conector, recursos, configurações de segurança e conectores certificados
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 05/22/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 16b96d91a9dd37fa8a502bbcca772438c703cb63
ms.sourcegitcommit: d88cc6a87d4ba82ad2c4d496a3634f927e4ac529
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66412984"
---
# <a name="connector-extensibility-in-power-bi"></a>Extensibilidade do conector no Power BI

No Power BI, clientes e desenvolvedores podem estender as fontes de dados que se conectam de várias maneiras. Eles usam conectores existentes e fontes de dados genéricos (por exemplo, ODBC, OData, Oledb, Web, CSV, XML, JSON). Ou, os desenvolvedores criar extensões de dados, conhecidas como **conectores personalizados**e torná-los **Certified conectores**.

No momento, você habilitar **conectores personalizados** usando um menu que permite que você com segurança controlar o nível de código personalizado que você deseja permitir que seja executado em seu sistema. Você pode escolher todos os conectores personalizados ou apenas os conectores certified e distribuídas pela Microsoft na **obter dados** caixa de diálogo.

## <a name="custom-connectors"></a>Conectores personalizados

**Conectores personalizados** pode incluir uma ampla gama de possibilidades, que variam de pequenas APIs críticas para os negócios, até grandes serviços específicos do setor que a Microsoft ainda não liberou um conector para. Muitos conectores são distribuídos pelo fornecedor. Se você tiver uma necessidade de um conector de dados específico, entre em contato com um fornecedor.

Para usar um **conector personalizado**, coloque-o na  *\[documentos]\\Power BI Desktop\\conectores personalizados* pasta e ajustar as configurações de segurança, conforme descrito em a seção a seguir.

Você não precisa ajustar as configurações de segurança para usar **Conectores Certificados**.

## <a name="data-extension-security"></a>Segurança da extensão de dados

Para alterar as configurações de segurança da extensão de dados, na **Power BI Desktop** selecionar **arquivo > Opções e configurações > Opções > segurança**.

![Se você deseja carregar conectores personalizados com opções de segurança da extensão de dados de controle](media/desktop-connector-extensibility/data-extension-security-1.png)

Em **Extensões de Dados**, você pode selecionar dois níveis de segurança:

* (Recomendado) Permitir o carregamento somente de extensões certificadas
* (Não recomendado) Permitir o carregamento de qualquer extensão sem aviso

Se você planeja usar **conectores personalizados** ou conectores que você ou terceiros desenvolveram, você deve selecionar **"(Not Recommended) permitir qualquer extensão carregar sem aviso"** . Não recomendamos essa configuração de segurança, a menos que você confie plenamente seus conectores personalizados. Porque o código lá pode lidar com as credenciais, incluindo enviá-los por HTTP e ignorar os níveis de privacidade.

No **"(recomendado)"** segurança configuração, se não houver conectores personalizados em seu sistema, aparecerá um erro que descreve os conectores que não é possível carregar devido à segurança.

![Uma caixa de diálogo descreve os conectores personalizados que não é possível carregar devido a configurações de segurança, no TripPin neste caso](media/desktop-connector-extensibility/data-extension-security-2.png)

Para resolver o erro e usar esses conectores, alterar as configurações de segurança para o **"(Not Recommended) permitir qualquer extensão carregar sem aviso"** configuração conforme descrito anteriormente. Em seguida, reinicie **Power BI Desktop**.

## <a name="certified-connectors"></a>Conectores certificados

Um subconjunto limitado de extensões de dados é considerado **Certified**. Acessar os conectores de certificado na **obter dados** caixa de diálogo. Porém, o desenvolvedor de terceiros que criou o conector é responsável por sua manutenção e suporte. Embora a Microsoft distribui os conectores, não é responsável por seu desempenho ou a função contínua.

Se você deseja que um conector personalizado seja certificado, solicite que seu fornecedor contate dataconnectors@microsoft.com.
