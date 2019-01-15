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
ms.date: 10/10/2018
LocalizationGroup: Gateways
ms.openlocfilehash: cb4d53166c848bcdb111b667ff413d96da9e72d5
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54290511"
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

1. Selecione **Importar**, navegue para a samltest.crt e importe-o.

    ![Provedores de identidade](media/service-gateway-sso-saml/identity-providers.png)

1. No SAP HANA Studio, selecione a pasta **Segurança**.

    ![Pasta de segurança](media/service-gateway-sso-saml/security-folder.png)

1. Expanda **Usuários** e, em seguida, selecione o usuário para o qual você deseja mapear o usuário do Power BI.

1. Selecione **SAML** e, em seguida, **Configurar**.

    ![Configurar SAML](media/service-gateway-sso-saml/configure-saml.png)

1. Selecione o provedor de identidade que você criou na etapa 2. Para **Identidade Externa**, insira o nome UPN do usuário do Power BI e selecione **Adicionar**.

    ![Selecionar o provedor de identidade](media/service-gateway-sso-saml/select-identity-provider.png)

Em seguida, valide a instalação com uma *Asserção SAML* usando a [Ferramenta xmlsec1](http://sgros.blogspot.com/2013/01/signing-xml-document-using-xmlsec1.html).

1. Salve a asserção abaixo como assertion-template.xml. Substitua \<MyUserId\> pelo nome UPN do usuário do Power BI inserido na etapa 7.

    ```xml
    <?xml version="1.0" encoding="UTF-8" ?>
    <saml2:Assertion ID="Assertion12345789" IssueInstant="2015-07-16T04:47:49.858Z" Version="2.0" xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">
      <saml2:Issuer></saml2:Issuer> 
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
        <SignedInfo>
          <CanonicalizationMethod Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
          <SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/>
          <Reference URI="">
            <Transforms>
              <Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/>
              <Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
            </Transforms>
            <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
            <DigestValue />
          </Reference>
        </SignedInfo>
        <SignatureValue />
        <KeyInfo>
          <X509Data />
        </KeyInfo>
      </Signature>
      <saml2:Subject>
        <saml2:NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified"><MyUserId></saml2:NameID>
      </saml2:Subject>
      <saml2:Conditions NotBefore="2010-01-01T00:00:00Z" NotOnOrAfter="2050-01-01T00:00:00Z"/>
    </saml2:Assertion>
    ```

1. Execute o seguinte comando. saltest.key e samltest.crt são a chave e o certificado gerados na etapa 1.

    ```
    xmlsec1 --sign --privkey-pem samltest.key, samltest.crt --output signed.xml assertion-template.xml
    ```

1. No SAP HANA Studio, abra uma janela de console do SQL e execute o seguinte comando. Substitua \<SAMLAssertion\> pelo conteúdo do XML da etapa anterior.

    ```SQL
    CONNECT WITH SAML ASSERTION '<SAMLAssertion>'
    ```

Se a consulta for bem-sucedida, isso significará que sua configuração de SSO de SAML do SAP HANA foi bem-sucedida.

Agora que você tem o certificado e a identidade configurados com êxito, pode converter o certificado em um formato pfx e configurar o computador do gateway para usar o certificado.

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

## <a name="next-steps"></a>Próximas etapas

Para obter mais informações sobre o **Gateway de dados local** e o **DirectQuery**, confira os seguintes recursos:

* [Gateway de dados local](service-gateway-onprem.md)
* [DirectQuery no Power BI](desktop-directquery-about.md)
* [Fontes de dados com suporte do DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery e SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery e SAP HANA](desktop-directquery-sap-hana.md)