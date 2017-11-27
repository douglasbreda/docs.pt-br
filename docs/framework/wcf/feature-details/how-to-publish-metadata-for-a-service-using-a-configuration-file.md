---
title: "Como publicar metadados para um serviço usando um arquivo de configuração"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f061443f-92df-4824-b36a-609c4cd14a17
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e94fe7135d51c4e1578ca69768b6d0ba2aa6ae6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-publish-metadata-for-a-service-using-a-configuration-file"></a><span data-ttu-id="c0c0b-102">Como publicar metadados para um serviço usando um arquivo de configuração</span><span class="sxs-lookup"><span data-stu-id="c0c0b-102">How to: Publish Metadata for a Service Using a Configuration File</span></span>
<span data-ttu-id="c0c0b-103">Este é um dos dois tópicos de instruções que demonstram os metadados de publicação para um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-103">This is one of two how-to topics that demonstrate publishing metadata for a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service.</span></span> <span data-ttu-id="c0c0b-104">Há duas maneiras de especificar como um serviço deve publicar metadados, usando um arquivo de configuração e código.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-104">There are two ways to specify how a service should publish metadata, using a configuration file and using code.</span></span> <span data-ttu-id="c0c0b-105">Este tópico mostra como publicar metadados para um serviço usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-105">This topic shows how to publish metadata for a service using a configuration file.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c0c0b-106">Este tópico mostra como publicar metadados de maneira insegura.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-106">This topic shows how to publish metadata in an unsecure manner.</span></span> <span data-ttu-id="c0c0b-107">Qualquer cliente pode recuperar os metadados do serviço.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-107">Any client can retrieve the metadata from the service.</span></span> <span data-ttu-id="c0c0b-108">Se você precisar de seu serviço para publicar metadados de uma maneira segura, consulte [ponto de extremidade de metadados de segurança personalizada](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="c0c0b-108">If you require your service to publish metadata in a secure manner, see [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md).</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="c0c0b-109">a publicação de metadados no código, consulte [como: publicar metadados para um serviço usando código](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span><span class="sxs-lookup"><span data-stu-id="c0c0b-109"> publishing metadata in code, see [How to: Publish Metadata for a Service Using Code](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md).</span></span> <span data-ttu-id="c0c0b-110">Metadados de publicação permite que os clientes recuperar os metadados usando uma solicitação GET do WS-transferência ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-110">Publishing metadata allows clients to retrieve the metadata using a WS-Transfer GET request or an HTTP/GET request using the `?wsdl` query string.</span></span> <span data-ttu-id="c0c0b-111">Para certificar-se de que o código está funcionando, criar básico [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-111">To be sure that the code is working, create a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="c0c0b-112">Para simplificar, um serviço auto-hospedado básico é fornecido no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-112">For simplicity, a basic self-hosted service is provided in the following code.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
 <span data-ttu-id="c0c0b-113">Esse serviço é um serviço de hospedagem interna, que é configurado usando um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-113">This service is a self-hosted service, which is configured using a configuration file.</span></span> <span data-ttu-id="c0c0b-114">O arquivo de configuração a seguir serve como um ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-114">The following configuration file serves as a starting point.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Metadata.Example.SimpleService">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
      </service>  
    </services>  
    <behaviors>  
  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-publish-metadata-for-a-wcf-service-using-an-application-configuration-file"></a><span data-ttu-id="c0c0b-115">Para publicar metadados para um serviço WCF usando um arquivo de configuração do aplicativo</span><span class="sxs-lookup"><span data-stu-id="c0c0b-115">To publish metadata for a WCF service using an application configuration file</span></span>  
  
1.  <span data-ttu-id="c0c0b-116">Dentro do arquivo App. config, após o fechamento `</services>` elemento, crie um `<behaviors>` elemento.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-116">Within the App.config file, after the closing `</services>` element, create a `<behaviors>` element.</span></span>  
  
  
  
2.  <span data-ttu-id="c0c0b-117">Dentro de `<behaviors>` elemento, adicionar um `<serviceBehaviors>` elemento.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-117">Within the `<behaviors>` element, add a `<serviceBehaviors>` element.</span></span>  
  
  
  
3.  <span data-ttu-id="c0c0b-118">Adicionar um `<behavior>` elemento para o `<serviceBehaviors>` elemento e especifique um valor para o `name` atributo do `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-118">Add a `<behavior>` element to the `<serviceBehaviors>` element and specify a value for the `name` attribute of the `<behavior>` element.</span></span>  
  
  
  
4.  <span data-ttu-id="c0c0b-119">Adicionar um `<serviceMetadata>` elemento para o `<behavior>` elemento.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-119">Add a `<serviceMetadata>` element to the `<behavior>` element.</span></span> <span data-ttu-id="c0c0b-120">Definir o `httpGetEnabled` atributo `true` e `policyVersion` atributo Policy15.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-120">Set the `httpGetEnabled` attribute to `true` and the `policyVersion` attribute to Policy15.</span></span> <span data-ttu-id="c0c0b-121">`httpGetEnabled`permite que o serviço responder a solicitações de metadados feitas por uma solicitação HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-121">`httpGetEnabled` allows the service to respond to metadata requests made by an HTTP GET request.</span></span> <span data-ttu-id="c0c0b-122">`policyVersion`informa o serviço de acordo com a especificação WS-Policy 1.5 durante a geração de metadados.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-122">`policyVersion` tells the service to conform to WS-Policy 1.5 when generating metadata.</span></span>  
  
  
  
5.  <span data-ttu-id="c0c0b-123">Adicionar um `behaviorConfiguration` de atributo para o `<service>` elemento e especifique o `name` atributo do `<behavior>` elemento adicionado na etapa 1, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-123">Add a `behaviorConfiguration` attribute to the `<service>` element and specify the `name` attribute of the `<behavior>` element added in step 1, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
        ...  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy15" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
6.  <span data-ttu-id="c0c0b-124">Adicione um ou mais `<endpoint>` elementos com o contrato definido como `IMetadataExchange`, conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-124">Add one or more `<endpoint>` elements with the contract set to `IMetadataExchange`, as shown in the following code example.</span></span>  
  
    ```xml  
    <services>  
      <service  
          name="Metadata.Example.SimpleService"  
          behaviorConfiguration="SimpleServiceBehavior">  
  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Metadata.Example.ISimpleService" />  
  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    ```  
  
7.  <span data-ttu-id="c0c0b-125">Para os pontos de extremidade de metadados adicionados na etapa anterior, defina o `binding` de atributo para um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="c0c0b-125">For the metadata endpoints added in the previous step, set the `binding` attribute to one of the following:</span></span>  
  
    -   <span data-ttu-id="c0c0b-126">`mexHttpBinding`para publicação de HTTP.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-126">`mexHttpBinding` for HTTP publication.</span></span>  
  
    -   <span data-ttu-id="c0c0b-127">`mexHttpsBinding`para publicação de HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-127">`mexHttpsBinding` for HTTPS publication.</span></span>  
  
    -   <span data-ttu-id="c0c0b-128">`mexNamedPipeBinding`para publicação de pipe nomeado.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-128">`mexNamedPipeBinding` for named pipe publication.</span></span>  
  
    -   <span data-ttu-id="c0c0b-129">`mexTcpBinding`para publicação de TCP.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-129">`mexTcpBinding` for TCP publication.</span></span>  
  
8.  <span data-ttu-id="c0c0b-130">Para os pontos de extremidade de metadados adicionados em uma etapa anterior, defina o endereço para:</span><span class="sxs-lookup"><span data-stu-id="c0c0b-130">For the metadata endpoints added in a previous step, set the address equal to:</span></span>  
  
    -   <span data-ttu-id="c0c0b-131">Uma cadeia de caracteres vazia para usar o endereço base do aplicativo host como o ponto de publicação se o endereço base é o mesmo que a associação de metadados.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-131">An empty string to use the host application's base address as the publication point if the base address is the same as the metadata binding.</span></span>  
  
    -   <span data-ttu-id="c0c0b-132">Um endereço relativo, se o aplicativo de host tem um endereço base.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-132">A relative address if the host application has a base address.</span></span>  
  
    -   <span data-ttu-id="c0c0b-133">Um endereço absoluto.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-133">An absolute address.</span></span>  
  
9. <span data-ttu-id="c0c0b-134">Compilar e executar o aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-134">Build and run the console application.</span></span>  
  
10. <span data-ttu-id="c0c0b-135">Use o Internet Explorer para navegar até o endereço base do serviço (http://localhost:8001/MetadataSample neste exemplo) e verifique se a publicação de metadados está ligada.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-135">Use Internet Explorer to browse to the base address of the service (http://localhost:8001/MetadataSample in this sample) and verify that the metadata publishing is turned on.</span></span> <span data-ttu-id="c0c0b-136">Se não, uma mensagem na parte superior da página resultante é exibida: "a publicação de metadados para este serviço está atualmente desabilitada."</span><span class="sxs-lookup"><span data-stu-id="c0c0b-136">If not, a message at the top of the resulting page displays: "Metadata publishing for this service is currently disabled."</span></span>  
  
### <a name="to-use-default-endpoints"></a><span data-ttu-id="c0c0b-137">Para usar pontos de extremidade padrão</span><span class="sxs-lookup"><span data-stu-id="c0c0b-137">To use default endpoints</span></span>  
  
1.  <span data-ttu-id="c0c0b-138">Para configurar os metadados em um serviço que usa pontos de extremidade padrão, especifique o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> na configuração do arquivo do exemplo anterior, mas não especificar nenhum ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-138">To configure metadata on a service that uses default endpoints, specify the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> in the configuration file as in the previous example, but do not specify any endpoints.</span></span> <span data-ttu-id="c0c0b-139">O arquivo de configuração, em seguida, ficaria assim.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-139">The configuration file would then look like this.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="SimpleServiceBehavior">  
              <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="c0c0b-140">Porque o serviço possui um <xref:System.ServiceModel.Description.ServiceMetadataBehavior> com o `httpGetEnabled` definida como `true`, o serviço tem metadados de publicação habilitado e porque nenhum ponto de extremidade foram adicionados explicitamente, o tempo de execução adiciona pontos de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-140">Because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> with the `httpGetEnabled` set to `true`, the service has publishing metadata enabled, and because no endpoints were explicitly added, the runtime adds the default endpoints.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="c0c0b-141">pontos de extremidade padrão, associações e comportamentos, consulte [configuração simplificada](../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c0c0b-141"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0c0b-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c0c0b-142">Example</span></span>  
 <span data-ttu-id="c0c0b-143">O exemplo de código a seguir mostra a implementação de um basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço e o arquivo de configuração que publica os metadados para o serviço.</span><span class="sxs-lookup"><span data-stu-id="c0c0b-143">The following code example shows the implementation of a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service and the configuration file that publishes metadata for the service.</span></span>  
  
```csharp  
using System;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Description;  
  
namespace Metadata.Samples  
{  
    [ServiceContract]  
    public interface ISimpleService  
    {  
        [OperationContract]  
        string SimpleMethod(string msg);  
    }  
  
    class SimpleService : ISimpleService  
    {  
        public string SimpleMethod(string msg)  
        {  
            Console.WriteLine("The caller passed in " + msg);  
            return "Hello " + msg;  
        }  
    }  
  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            ServiceHost host = new ServiceHost(typeof(SimpleService),  
                new Uri("http://localhost:8001/MetadataSample"));   
            try  
            {  
                // Open the service host to accept incoming calls  
                host.Open();  
  
                // The service can now be accessed.  
                Console.WriteLine("The service is ready.");  
                Console.WriteLine("Press <ENTER> to terminate service.");  
                Console.WriteLine();  
                Console.ReadLine();  
  
                // Close the ServiceHostBase to shutdown the service.  
                host.Close();  
            }  
            catch (CommunicationException commProblem)  
            {  
                Console.WriteLine("There was a communication problem. " + commProblem.Message);  
                Console.Read();  
            }  
        }  
    }  
}  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="SimpleServiceBehavior">  
          <serviceMetadata httpGetEnabled="True" policyVersion="Policy12" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c0c0b-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0c0b-144">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 <span data-ttu-id="c0c0b-145">[How to: Host a WCF Service in a Managed Application](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md) (Como hospedar um serviço do WCF em um aplicativo gerenciado)</span><span class="sxs-lookup"><span data-stu-id="c0c0b-145">[How to: Host a WCF Service in a Managed Application](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)</span></span>  
 [<span data-ttu-id="c0c0b-146">Hospedagem interna</span><span class="sxs-lookup"><span data-stu-id="c0c0b-146">Self-Host</span></span>](../../../../docs/framework/wcf/samples/self-host.md)  
 [<span data-ttu-id="c0c0b-147">Visão geral da arquitetura de metadados</span><span class="sxs-lookup"><span data-stu-id="c0c0b-147">Metadata Architecture Overview</span></span>](../../../../docs/framework/wcf/feature-details/metadata-architecture-overview.md)  
 [<span data-ttu-id="c0c0b-148">Uso de metadados</span><span class="sxs-lookup"><span data-stu-id="c0c0b-148">Using Metadata</span></span>](../../../../docs/framework/wcf/feature-details/using-metadata.md)  
 [<span data-ttu-id="c0c0b-149">Como: publicar metadados utilizando código para um serviço</span><span class="sxs-lookup"><span data-stu-id="c0c0b-149">How to: Publish Metadata for a Service Using Code</span></span>](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)