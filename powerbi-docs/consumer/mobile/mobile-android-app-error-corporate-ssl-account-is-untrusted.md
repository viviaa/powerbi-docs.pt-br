---
title: Como corrigir "Certificado SSL corporativo não é confiável"
description: Ao entrar no aplicativo Android para o Power BI, você poderá ver a mensagem “Não foi possível autenticar porque seu certificado SSL corporativo não é confiável
.": ''
author: mshenhav
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: mshenhav
ms.openlocfilehash: de103412e21e0d26d20058e2d4e1fb9a8a5449bf
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61341331"
---
# <a name="fixing-corporate-ssl-certificate-is-untrusted---power-bi"></a>Como corrigir "Certificado SSL corporativo não é confiável" – Power BI
Ao entrar no aplicativo móvel Android para o Microsoft Power BI, você verá a mensagem “Não foi possível autenticar porque o certificado SSL corporativo não é confiável para este dispositivo. Contate o administrador de TI da sua empresa”. 

O que você precisa fazer geralmente depende do sistema operacional em seu dispositivo Android, mas há alguns outros problemas que podem causar esse erro.

## <a name="on-android-7-or-later"></a>No Android 7 ou posterior
Procure uma atualização para um aplicativo chamado **Chrome** e instale a atualização.

## <a name="on-android-6-and-earlier"></a>No Android 6 e anteriores
Seu dispositivo pode precisar de uma versão atualizada do System Webview. Ela pode estar instalada em seu dispositivo e você poderá apenas precisar clicar em **Atualizar**.

Se o System Webview não estiver instalado no seu dispositivo:

1. No dispositivo Android, feche o Power BI.
2. Abra a Google Play Store e pesquise **System Webview** da Google Inc.
3. Instale-o.
4. Reinicie o aplicativo Power BI e conecte-se.

## <a name="time-zone-settings"></a>Configurações de fuso horário
As configurações de fuso horário no seu dispositivo podem estar erradas. 

Acesse **Configurações** > **Sistema** > **Data e hora** para verificá-las.

## <a name="custom-authentication-server"></a>Servidor de autenticação personalizado
Se você estiver usando um servidor de autenticação personalizado, o certificado SSL no servidor de autenticação corporativa poderá não ser válido. Trabalhe com a TI da sua organização para testar a configuração do servidor de autenticação corporativa, seguindo as orientações [deste artigo](https://support.microsoft.com/en-us/help/3203929/using-adal-to-authenticate-from-android-devices-fails-if-additional-ce).

## <a name="next-steps"></a>Próximas etapas
* [Baixe o aplicativo Android](http://go.microsoft.com/fwlink/?LinkID=544867) na loja de aplicativos Android.
* Dúvidas? [Experimente perguntar à Comunidade do Power BI](http://community.powerbi.com/) 

