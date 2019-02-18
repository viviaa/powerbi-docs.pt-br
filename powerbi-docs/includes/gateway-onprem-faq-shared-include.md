## <a name="general"></a>Geral
**Pergunta:** Como o serviço Windows real é chamado?  
**Resposta:** O gateway é chamado de serviço de gateway de dados local em Serviços

**Pergunta:** Quais são os requisitos do gateway?  
**Resposta:** Dê uma olhada na seção Requisitos do [artigo principal sobre o gateway](../service-gateway-onprem.md).

**Pergunta:** Há suporte para quais fontes de dados no gateway?  
**Resposta:** Veja a tabela de fontes de dados no [artigo principal sobre o gateway](../service-gateway-onprem.md).

**Pergunta:** É necessário ter um gateway para fontes de dados de nuvem como o Banco de Dados SQL do Azure?  
**Resposta:** Não. O serviço poderá se conectar à fonte de dados sem um gateway.

**Pergunta:** Existem conexões de entrada com o gateway por meio da nuvem?  
**Resposta:** Não. O gateway usa conexões de saída ao Barramento de Serviço do Azure.

**Pergunta:** E se eu bloquear as conexões de saída? O que preciso abrir?  
**Resposta:** Veja a [lista de portas](../service-gateway-onprem.md#ports) e de hosts usados pelo gateway.

**Pergunta:** O gateway precisa ser instalado no mesmo computador da fonte de dados?  
**Resposta:** Não. O gateway será conectado à fonte de dados usando as informações de conexão fornecidas. Nesse sentido, considere o gateway como um aplicativo cliente. Ele apenas precisa conseguir se conectar ao nome do servidor que foi fornecido.

**Pergunta:** Qual é a latência de execução de consultas em uma fonte de dados por meio do gateway? Qual é a melhor arquitetura?  
**Resposta:** É recomendável ter o gateway o mais próximo possível da fonte de dados para evitar a latência da rede. Se você conseguir instalar o gateway na fonte de dados real, isso minimizará a latência introduzida. Considere também os datacenters. Por exemplo, caso seu serviço esteja fazendo uso do datacenter do Oeste dos EUA e você tiver o SQL Server hospedado em uma VM do Azure, é recomendável ter a VM do Azure também no Oeste dos EUA. Isso minimizará a latência e evitará encargos de saída na VM do Azure.

**Pergunta:** Há requisitos de largura de banda da rede?  
**Resposta:** É recomendado que a conexão de rede tenha uma boa taxa de transferência. Cada ambiente é diferente e isso também depende da quantidade de dados enviados. O uso do ExpressRoute pode ajudar a garantir um nível de taxa de transferência entre os datacenters locais e do Azure.

Você pode usar o aplicativo [Azure Speed Test](http://azurespeedtest.azurewebsites.net/) de terceiros para ajudar a medir sua taxa de transferência.

**Pergunta:** O serviço Windows do gateway pode ser executado com uma conta do Azure Active Directory?  
**Resposta:** Não. O serviço Windows precisa ter uma conta válida do Windows. Por padrão, ele será executado com o SID do Serviço, *NT SERVICE\PBIEgwService*.

**Pergunta:** Como os resultados são enviados novamente para a nuvem?  
**Resposta:** Isso é feito por meio do Barramento de Serviço do Azure. Para obter mais informações, veja [como isso funciona](../service-gateway-onprem.md#how-the-gateway-works).

**Pergunta:** Em que local minhas credenciais são armazenadas?  
**Resposta:** As credenciais inseridas para uma fonte de dados são armazenadas criptografadas no serviço de nuvem do gateway. As credenciais são descriptografadas no gateway local.

**Pergunta:** Posso colocar o gateway em uma rede de perímetro (também conhecida como DMZ, zona desmilitarizada e sub-rede filtrada)?  
**Resposta:** O gateway exige a conectividade com a fonte de dados. Se a fonte de dados não estiver acessível na rede de perímetro, o gateway poderá não conseguir se conectar a ela. Por exemplo, o SQL Server talvez não esteja na sua rede de perímetro. Além disso, não é possível se conectar ao SQL Server por meio da rede de perímetro. Se você tivesse colocado o gateway na rede de perímetro, ele não seria capaz de acessar o SQL Server.

**Pergunta:** É possível forçar o gateway a usar o tráfego HTTPS com o Barramento de Serviço do Azure em vez do TCP?  
**Resposta:** Sim. No entanto, isso reduzirá o desempenho significativamente. Talvez você queira modificar o arquivo *Microsoft.PowerBI.DataMovement.Pipeline.GatewayCore.dll.config*. Convém alterar o valor de `AutoDetect` para `Https`. Este arquivo está localizado, por padrão, em *C:\Arquivos de Programas\Gateway de dados local*.

**Pergunta:** É necessário colocar a lista de IP do Datacenter do Azure na lista de permissões? Onde posso obter a lista?  
**Resposta:** Se você estiver bloqueando o tráfego de IP de saída, poderá precisar colocar a lista de IP do Datacenter do Azure na lista de permissões. Atualmente, o gateway se comunicará com o Barramento de Serviço do Azure usando o endereço IP, além do nome de domínio totalmente qualificado. A lista de IP do Datacenter do Azure é atualizada semanalmente. Você pode baixar a [lista de IP do Data Center do Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653).

```xml
<setting name="ServiceBusSystemConnectivityModeString" serializeAs="String">
    <value>Https</value>
</setting>
```

## <a name="high-availabilitydisaster-recovery"></a>Alta Disponibilidade/Recuperação de Desastre
**Pergunta:** Há planos para habilitar cenários de alta disponibilidade com o gateway?  
**Resposta:** Sim, essa é uma área de investimento ativo da equipe do Power BI. Fique ligado no [blog do Power BI](https://powerbi.microsoft.com/blog/) para obter mais atualizações sobre esse recurso.

**Pergunta:** Quais opções estão disponíveis para recuperação de desastre?  
**Resposta:** Você pode usar a chave de recuperação para restaurar ou mover um gateway. Ao instalar o gateway, forneça a chave de recuperação.

**Pergunta:** Qual é o benefício da chave de recuperação?  
**Resposta:** Ela oferece uma maneira de migrar ou recuperar as configurações do gateway. Também é usada para a recuperação de desastre.

## <a name="troubleshooting"></a>Solução de problemas
**Pergunta:** Em que local os logs do gateway podem ser encontrados?  
**Resposta:** Confira a seção Ferramentas do [artigo sobre solução de problemas](../service-gateway-onprem-tshoot.md#tools-for-troubleshooting).

**Pergunta:** Como saber quais consultas estão sendo enviadas à fonte de dados local?  
**Resposta:** Você pode habilitar o rastreamento de consultas.  Isso incluirá as consultas que estão sendo enviadas. Lembre-se de alterá-lo para o valor original quando concluir a solução de problemas. Habilitar o rastreamento de consultas fará com que os logs sejam maiores.

Você também pode examinar as ferramentas que sua fonte de dados tem para o rastreamento de consultas. Por exemplo, para o SQL Server e o Analysis Services, é possível usar os Eventos Estendidos ou o SQL Profiler.

