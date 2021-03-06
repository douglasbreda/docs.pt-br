---
title: '&lt;transporte&gt; de &lt;netHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 3b180006-1661-43bf-a699-96fd3da469af
ms.openlocfilehash: 03e245acd8cb31630d6154e01d934ce6d293f4e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507958"
---
# <a name="lttransportgt-of-ltnethttpbindinggt"></a>&lt;transporte&gt; de &lt;netHttpBinding&gt;
Define as propriedades que controlam os parâmetros de autenticação para o transporte HTTP.  
  
\<system.serviceModel>  
\<associações >  
\<netHttpBinding>  
\<associação >  
\<segurança >  
\<transporte >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<netHttpBinding>  
  <binding>  
    <security mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
      <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
                 proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string">  
        <extendedProtectionPolicy policyEnforcement="Never|WhenSupported|Always"  
                                  protectionScenario="TransportSelected|TrustedProxy">  
          <customServiceNames></customServiceNames>  
        </extendedProtectionPolicy>  
      </transport>  
    </security>  
  </binding>  
</netHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|clientCredentialType|-Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente usando a autenticação HTTP.  O padrão é `None`. Esse atributo é do tipo <xref:System.ServiceModel.HttpClientCredentialType>.|  
|proxyCredentialType|-Especifica o tipo de credencial a ser usada ao executar a autenticação de cliente de dentro de um domínio usando um proxy por meio de HTTP. Esse atributo é aplicável somente quando o `mode` atributo do pai `security` elemento é `Transport` ou `TransportCredentialsOnly`. Esse atributo é do tipo <xref:System.ServiceModel.HttpProxyCredentialType>.|  
|território|Uma cadeia de caracteres que especifica o realm que é usado pelo esquema de autenticação de HTTP para a autenticação básica ou digest. O padrão é uma cadeia de caracteres vazia.|  
|policyenforcement definido como|Esta enumeração Especifica quando o <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> deve ser imposta.<br /><br /> 1.  Nunca – a política de nunca é aplicada (proteção estendida é desabilitada).<br />2.  WhenSupported – a política é aplicada somente se o cliente oferece suporte à proteção estendida.<br />3.  Sempre – a política sempre é aplicada. Os clientes que não dão suporte a proteção estendida falharão ao autenticar.|  
|protectionScenario|Esta enumeração Especifica o cenário de proteção imposto pela política.|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType de atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|Mensagens não são protegidas durante a transferência.|  
|Basic|Especifica autenticação básica.|  
|Digest|Especifica a autenticação Digest.|  
|NTLM|Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.|  
|Windows|Especifica a autenticação integrada do Windows.|  
  
## <a name="proxycredentialtype-attribute"></a>proxyCredentialType atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|Nenhum|-Mensagens não são protegidas durante a transferência.|  
|Basic|Especifica autenticação básica, conforme definido pelo RFC 2617 – autenticação HTTP: autenticação básica e Digest.|  
|Digest|Especifica a autenticação digest, conforme definido pelo RFC 2617 – autenticação HTTP: autenticação básica e Digest.|  
|NTLM|Especifica a autenticação NTLM quando possível, e se a autenticação do Windows falhar.|  
|Windows|Especifica a autenticação integrada do Windows.|  
|Certificado|Executa a autenticação de cliente usando um certificado. Essa opção só funcionará se o `Mode` atributo do pai `security` elemento é definido como transporte e não funcionará se ele for definido como TransportCredentialOnly.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|Define os recursos de segurança para o [ \<netHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nethttpbinding.md).|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso da segurança de transporte SSL com a associação básica. Por padrão, a associação básica oferece suporte à comunicação HTTP.  
  
```xml
<system.serviceModel>  
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpBinding>  
      <!-- Configure basicHttpBinding with Transport security -- >  
      <!-- mode and clientCredentialType set to None.-->  
      <binding name="Binding1">  
        <security mode="Transport">  
          <transport clientCredentialType="None"  
                     proxyCredentialType="None">  
            <extendedProtectionPolicy policyEnforcement="WhenSupported"  
                                      protectionScenario="TransportSelected">  
              <customServiceNames></customServiceNames>  
            </extendedProtectionPolicy>
          </transport> 
        </security>  
      </binding>  
    </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [Protegendo serviços e clientes](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
