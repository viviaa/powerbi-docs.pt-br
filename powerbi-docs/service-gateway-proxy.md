---
title: Definindo as configurações de proxy do gateway de dados locais
description: Informações sobre a definição das configurações de proxy do gateway de dados local.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 11/21/2017
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2122ce9bd6eb850a51a06188ca1c10faf78f4bb1
ms.sourcegitcommit: ac63b08a4085de35e1968fa90f2f49ea001b50c5
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57964653"
---
# <a name="configuring-proxy-settings-for-the-on-premises-data-gateway"></a>Definindo as configurações de proxy do gateway de dados locais
Seu ambiente de trabalho poderá exigir que você passe por um proxy para acessar a Internet. Isso pode impedir que o gateway de dados local se conecte ao serviço.

## <a name="does-your-network-use-a-proxy"></a>Sua rede usa um proxy?
A seguinte postagem no superuser.com discute como você pode tentar determinar se tem um proxy na rede.

[Como saber qual servidor proxy estou usando? (SuperUser.com)](https://superuser.com/questions/346372/how-do-i-know-what-proxy-server-im-using)

## <a name="configuration-file-location-and-default-configuration"></a>Local do arquivo de configuração e configuração padrão
As informações de proxy são configuradas em um arquivo de configuração do .NET. O local e os nomes de arquivo serão diferentes, dependendo do gateway usado.

### <a name="on-premises-data-gateway"></a>Gateway de dados local
Existem dois arquivos de configuração principais que se relacionam ao gateway de dados local.

**Configuração**

O primeiro refere-se às telas de configuração que, na verdade, configuram o gateway. Se estiver tendo problemas para configurar o gateway, este é o arquivo que você desejará examinar.

    C:\Program Files\On-premises data gateway\enterprisegatewayconfigurator.exe.config

**Serviço Windows**

O segundo refere-se ao serviço Windows real que interage com o serviço do Power BI e manipula as solicitações.

    C:\Program Files\On-premises data gateway\Microsoft.PowerBI.EnterpriseGateway.exe.config

## <a name="configuring-proxy-settings"></a>Definindo as configurações de proxy
A configuração de proxy padrão é a seguinte:

```
<system.net>
    <defaultProxy useDefaultCredentials="true" />
</system.net>
```


A configuração padrão funciona com a autenticação do Windows. Se o proxy usar outra forma de autenticação, você precisará alterar as configurações. Se você não tiver certeza, entre em contato com o administrador da rede. A autenticação de proxy básica não é recomendada e a tentativa de usá-la pode causar erros de autenticação de proxy fazendo com que o gateway não seja configurado corretamente. Use um mecanismo de autenticação de proxy mais forte para resolver.

Além de usar as credenciais padrão, você pode adicionar um elemento <proxy> para definir as configurações do servidor proxy em mais detalhes. Por exemplo, você pode especificar que o gateway de dados local deve sempre usar o proxy mesmo para recursos locais definindo o parâmetro bypassonlocal como false. Isso pode ajudar em situações de solução de problemas caso você queira controlar todas as solicitações https provenientes de um gateway de dados local nos arquivos de log do proxy. A configuração de exemplo a seguir especifica que todas as solicitações precisam passar por um proxy específico com o endereço IP 192.168.1.10.

```
<system.net>
    <defaultProxy useDefaultCredentials="true">
        <proxy  
            autoDetect="false"  
            proxyaddress="http://192.168.1.10:3128"  
            bypassonlocal="false"  
            usesystemdefault="true"
        />  
    </defaultProxy>
</system.net>
```

Além disso, para o gateway se conectar a fontes de dados na nuvem por meio de um proxy, atualize o arquivo a seguir: *C:\Arquivos de Programas\Gateway de dados locais\Microsoft.Mashup.Container.NetFX45.exe*. No arquivo, expanda a seção `<configurations>` para incluir o conteúdo abaixo e atualize o atributo `proxyaddress` com as informações de seu proxy. O exemplo a seguir rotearia todas as solicitações da nuvem por meio de um proxy específico com o endereço IP 192.168.1.10.

```
<configuration>
<system.net>
    <defaultProxy useDefaultCredentials="true" enabled="true">
    <proxy proxyaddress=""http://192.168.1.10:3128" bypassonlocal="true" />
    </defaultProxy>
</system.net>
</configuration>
```

Para saber mais sobre a configuração dos elementos de proxy para os arquivos de configuração do .NET, veja [Elemento defaultProxy (Configurações de Rede)](https://msdn.microsoft.com/library/kd3cf2ex.aspx).

## <a name="changing-the-gateway-service-account-to-a-domain-user"></a>Alterando a conta de serviço do gateway para um usuário de domínio
Ao definir as configurações de proxy para usar credenciais padrão, conforme explicado acima, você pode ter problemas de autenticação com o proxy. Isso ocorre porque a conta de serviço padrão é o SID de Serviço, não um usuário de domínio autenticado. É possível alterar a conta de serviço do gateway para permitir a autenticação adequada com o proxy.

> [!NOTE]
> É recomendável que você use uma conta de serviço gerenciado para evitar a redefinição de senhas. Saiba como criar uma [conta de serviço gerenciado](https://technet.microsoft.com/library/dd548356.aspx) dentro do Active Directory.
> 
> 

### <a name="change-the-on-premises-data-gateway-service-account"></a>Alterar a conta de serviço do gateway de dados local
1. Altere a conta de serviço Windows para o **serviço do gateway de dados local**.

    A conta padrão para esse serviço é *NT SERVICE\PBIEgwService*. Altere-a para uma conta de usuário do domínio dentro do seu domínio do Active Directory. Ou utilize uma conta de serviço gerenciado para evitar a necessidade de modificar a senha.

    Altere a conta na guia **Fazer Logon** dentro das propriedades do serviço Windows.
2. Reinicie o **serviço do gateway de dados local**.

    Em um prompt de comando do administrador, execute os comandos a seguir.

        net stop PBIEgwService

        net start PBIEgwService
3. Inicie o **configurador do gateway de dados local**. É possível selecionar o botão Iniciar do Windows e procurar *gateway de dados local*.
4. Entre no Power BI.
5. Restaure o gateway usando sua chave de recuperação.

    Isso permitirá que a nova conta de serviço consiga descriptografar as credenciais armazenadas para fontes de dados.

> [!NOTE]
> Quando você altera a conta de serviço usando diretamente o painel de controle de serviços, as ACLs não são atualizadas automaticamente. Você precisa garantir que a nova conta de serviço tenha acesso aos arquivos e à pasta de instalação. Você pode encontrar a pasta de instalação do Gateway no gateway de dados C:\Arquivos de Programas\Local. 
> 

## <a name="next-steps"></a>Próximas etapas
[Gateway de dados local (modo pessoal)](service-gateway-personal-mode.md)
[Informações sobre firewall](service-gateway-onprem-tshoot.md#firewall-or-proxy)  
Mais perguntas? [Experimente a Comunidade do Power BI](http://community.powerbi.com/)

