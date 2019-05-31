---
title: Confiável para conectores de produtos de terceiros no Power BI
description: Como confiar um conector de produtos de terceiros assinado no Power BI
author: cpopell
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/3/2019
ms.author: gepopell
LocalizationGroup: Connect to data
ms.openlocfilehash: 30b7457c6149320c43f24b967a842382821b01b1
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65607782"
---
# <a name="trusting-third-party-connectors"></a>Conectores de produtos de terceiros confiantes

## <a name="why-do-you-need-trusted-third-party-connectors"></a>Por que você precisa de conectores de produtos de terceiros confiáveis?

No Power BI, geralmente Recomendamos manter sua segurança de extensão' dados' nível no nível superior, que impede o carregamento de código não certificado pela Microsoft. No entanto, pode haver muitos casos em que você deseja carregar conectores específicos – aquelas que você escreveu ou aqueles fornecidos por um consultor ou fornecedor fora do caminho de certificação da Microsoft.

O desenvolvedor de um determinado conector pode assiná-lo com um certificado e fornecer as informações necessárias com segurança carregá-lo sem reduzir as configurações de segurança.

Se você quiser saber mais sobre as configurações de segurança, você pode ler sobre elas [aqui](https://docs.microsoft.com/power-bi/desktop-connector-extensibility).

## <a name="using-the-registry-to-trust-third-party-connectors"></a>Usando o registro de confiar em conectores de produtos de terceiros

Confiar em conectores de produtos de terceiros no Power BI é feito por meio da listagem a impressão digital do certificado que você desejar confiar em um valor do Registro especificada. Se essa impressão digital corresponde a impressão digital do certificado no conector que você deseja carregar, você poderá carregá-lo no nível de segurança de "Recomendadas" do Power BI. 

O caminho do registro é HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\Power BI Desktop. Verifique se que o caminho existe, ou criá-lo. Escolhemos esse local devido a ele que está sendo controlado pela política de TI, bem como exigir acesso de administração do computador local para editar. 

![Conjunto de registro de área de trabalho do Power BI sem chaves de terceiros confiáveis](media/desktop-trusted-third-party-connectors/desktoptrustedthird1.png)

Adicione um novo valor no caminho especificado acima. O tipo deve ser "Valor de cadeia de caracteres múltipla" (REG_MULTI_SZ) e deve ser chamado "TrustedCertificateThumbprints" 

![Registro de área de trabalho do Power BI com uma entrada para conectores de produtos de terceiros confiáveis, mas nenhuma chave](media/desktop-trusted-third-party-connectors/desktoptrustedthird2.png)

Adicione as impressões digitais dos certificados que você deseja confiar. Você pode adicionar vários certificados usando "\0" como um delimitador ou no editor do registro, direito -> clique em modificar e colocar cada impressão digital em uma nova linha. Exemplo de impressão digital é obtido de um certificado autoassinado. 

 ![Registro de área de trabalho do Power BI com um conjunto de chaves de terceiros confiável](media/desktop-trusted-third-party-connectors/desktoptrustedthird3.png)

Se você seguiu as instruções corretamente e receberam a impressão digital apropriado pelo seu desenvolvedor, você agora deve ser capaz de forma segura os conectores de confiança assinados com o certificado associado.

## <a name="how-to-sign-connectors"></a>Como assinar os conectores

Se você tiver um conector, você ou um desenvolvedor precisa entrar, você pode ler sobre isso nos documentos do Power Query [aqui](https://docs.microsoft.com/power-query/handlingconnectorsigning).
