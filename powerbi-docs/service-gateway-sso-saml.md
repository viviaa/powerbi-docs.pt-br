---
title: Usar o SAML para logon único (SSO) para fontes de dados locais
description: Configure seu gateway com SAML (Security Assertion Markup Language) para habilitar SSO (logon único) do Power BI para fontes de dados locais.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 03/05/2019
LocalizationGroup: Gateways
ms.openlocfilehash: c1ca797efa2e40bf74384a1e9f2362acd26c6f8f
ms.sourcegitcommit: 883a58f63e4978770db8bb1cc4630e7ff9caea9a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/07/2019
ms.locfileid: "57555657"
---
# <a name="use-security-assertion-markup-language-saml-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>Use SAML (Security Assertion Markup Language) para SSO (logon único) do Power BI para fontes de dados locais

Use [SAML (Security Assertion Markup Language)](https://www.onelogin.com/pages/saml) para habilitar a conectividade ininterrupta de logon único. Habilitar SSO torna mais fácil para relatórios e dashboards do Power BI atualizar os dados de fontes locais.

## <a name="supported-data-sources"></a>Fontes de dados para as quais há suporte

Atualmente, há suporte para SAP HANA com SAML. Para obter mais informações sobre como configurar e definir logon único para SAP HANA usando SAML, confira o tópico [SSO do SAML para a Plataforma BI para HANA](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA) na documentação do SAP HANA.

Damos suporte a fontes de dados adicionais com [Kerberos](service-gateway-sso-kerberos.md).

## <a name="configuring-the-gateway-and-data-source"></a>Como configurar a fonte de dados e o gateway

Para usar SAML, você primeiro gera um certificado para o provedor de identidade SAML e mapeia um usuário do Power BI para a identidade.

1. Gere um certificado. Verifique se você usar o FQDN do servidor do SAP HANA ao preencher o *nome comum*. O certificado expira em 365 dias.

    ```
    openssl req -newkey rsa:2048 -nodes -keyout samltest.key -x509 -days 365 -out samltest.crt
    ```

1. No SAP HANA Studio, clique com o botão direito do mouse no servidor SAP HANA e, em seguida, navegue até **Segurança** > **Abrir Console de Segurança** > **Provedor de Identidade SAML**  >  **Biblioteca Criptográfica do OpenSSL**.

    É possível, inclusive, usar a Biblioteca de Códigos Criptográficos do SAP (conhecida também como CommonCryptoLib ou sapcrypto) em vez do OpenSSL para realizar as etapas de configuração. Para saber mais, verifique a documentação oficial do SAP.

1. Selecione **Importar**, navegue para a samltest.crt e importe-o.

    ![Provedores de identidade](media/service-gateway-sso-saml/identity-providers.png)

1. No SAP HANA Studio, selecione a pasta **Segurança**.

    ![Pasta de segurança](media/service-gateway-sso-saml/security-folder.png)

1. Expanda **Usuários** e, em seguida, selecione o usuário para o qual você deseja mapear o usuário do Power BI.

1. Selecione **SAML** e, em seguida, **Configurar**.

    ![Configurar SAML](media/service-gateway-sso-saml/configure-saml.png)

1. Selecione o provedor de identidade que você criou na etapa 2. Para **Identidade Externa**, insira o nome UPN do usuário do Power BI e selecione **Adicionar**.

    ![Selecionar o provedor de identidade](media/service-gateway-sso-saml/select-identity-provider.png)

Agora que você tem o certificado e a identidade configurados, converta o certificado em um formato pfx e configure o computador do gateway para usar o certificado.

1. Converta o certificado para o formato pfx executando o comando a seguir.

    ```
    openssl pkcs12 -inkey samltest.key -in samltest.crt -export -out samltest.pfx
    ```

1. Copie o arquivo pfx para o computador do gateway:

    1. Clique duas vezes em samltest.pfx e, em seguida, selecione **Computador Local** > **Avançar**.

    1. Insira a senha e, em seguida, selecione **Próximo**.

    1. Selecione **Colocar todos os certificados no repositório a seguir**, então **Procurar** > **Pessoal** > **OK**.

    1. Selecione **Próximo** e, em seguida, **Concluir**.

    ![Importar certificado](media/service-gateway-sso-saml/import-certificate.png)

1. Conceda à conta de serviço de gateway acesso à chave privada do certificado:

    1. No computador do gateway, execute o MMC (Console de Gerenciamento Microsoft).

        ![Executar MMC](media/service-gateway-sso-saml/run-mmc.png)

    1. Em **Arquivo**, selecione **Adicionar/Remover Snap-in**.

        ![Adicionar snap-in](media/service-gateway-sso-saml/add-snap-in.png)

    1. Selecione **Certificados** > **Adicionar** e, em seguida, selecione **Conta de computador** > **Avançar**.

    1. Selecione **Computador Local** > **Concluir** > **OK**.

    1. Expandir **Certificados** > **Pessoal** > **Certificados** e localize o certificado.

    1. Clique com o botão direito do mouse no certificado e navegue até **Todas as Tarefas** > **Gerenciar Chaves Privadas**.

        ![Gerenciar chaves privadas](media/service-gateway-sso-saml/manage-private-keys.png)

    1. Adicione a conta de serviço de gateway à lista. Por padrão, a conta é **NT SERVICE\PBIEgwService.** Você pode descobrir qual conta está executando o serviço de gateway executando **services.msc** e localizando **Serviço de gateway de dados local**.

        ![Serviço do gateway](media/service-gateway-sso-saml/gateway-service.png)

Por fim, siga estas etapas para adicionar a impressão digital do certificado para a configuração do gateway.

1. Execute o seguinte comando do PowerShell para listar os certificados em seu computador.

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```
1. Copie a impressão digital do certificado criado.

1. Navegue até o diretório de gateway, que assume como padrão C:\Arquivos de Programas\On-premises data gateway.

1. Abra PowerBI.DataMovement.Pipeline.GatewayCore.dll.config e localize a seção \*SapHanaSAMLCertThumbprint\*. Cole a impressão digital copiada.

1. Reinicie o serviço de gateway.

## <a name="running-a-power-bi-report"></a>Executando um relatório do Power BI

Agora você pode usar a página **Gerenciar Gateway** no Power BI para configurar a fonte de dados e, em **Configurações Avançadas**, habilitar o SSO. Em seguida, você pode publicar relatórios e conjuntos de dados associados àquela fonte de dados.

![Configurações avançadas](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="troubleshooting"></a>Solução de problemas

Depois de configurar o SSO, talvez você veja o seguinte erro no portal do Power BI: "As credenciais fornecidas não podem ser usadas para a fonte SAP HANA". Esse erro indica que a credencial do SAML foi rejeitada pelo SAP HANA.

Os rastreamentos de autenticação fornecem informações detalhadas para solução de problemas com credenciais no SAP HANA. Siga estas etapas para configurar o rastreamento no servidor SAP HANA.

1. No servidor SAP HANA, ative o rastreamento de autenticação executando a consulta a seguir.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') set ('trace', 'authentication') = 'debug' with reconfigure 
    ```

1. Reproduza o problema que você está enfrentando.

1. No HANA Studio, abra o console de administração e vá para a guia **Arquivos de diagnóstico**.

1. Abra o rastreamento mais recente do servidor de indexação e procure por SAMLAuthenticator.cpp.

    Você encontrará uma mensagem de erro detalhada indicando a causa raiz, como no exemplo a seguir.

    ```
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815797 d Authentication   SAMLAuthenticator.cpp(00091) : Element '{urn:oasis:names:tc:SAML:2.0:assertion}Assertion', attribute 'ID': '123123123123123' is not a valid value of the atomic type 'xs:ID'.
    [3957]{-1}[-1/-1] 2018-09-11 21:40:23.815914 i Authentication   SAMLAuthenticator.cpp(00403) : No valid SAML Assertion or SAML Protocol detected
    ```

1. Depois de solucionar os problemas, desative o rastreamento de autenticação executando a consulta a seguir.

    ```
    ALTER SYSTEM ALTER CONFIGURATION ('indexserver.ini', 'SYSTEM') UNSET ('trace', 'authentication');
    ```

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre o **Gateway de dados local** e o **DirectQuery**, confira os seguintes recursos:

* [Gateway de dados local](service-gateway-onprem.md)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)
