---
title: Migrando de .NET Remoting para o WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f39a26d52d7002e793935135e0c5d5e8f11c3d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="3c565-102">Migrando de .NET Remoting para o WCF</span><span class="sxs-lookup"><span data-stu-id="3c565-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="3c565-103">Este artigo descreve como migrar um aplicativo que usa comunicação remota do .NET para usar o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3c565-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="3c565-104">Ele compara os conceitos semelhantes entre esses produtos e, em seguida, descreve como realizar vários cenários comuns de comunicação remota no WCF.</span><span class="sxs-lookup"><span data-stu-id="3c565-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="3c565-105">Comunicação remota do .NET é um produto herdado que tem suporte somente para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="3c565-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="3c565-106">Não é seguro em ambientes mistos de confiança porque ele não pode manter os níveis de confiança separados entre cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="3c565-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="3c565-107">Por exemplo, você nunca deve expor um ponto de extremidade de comunicação remota do .NET para a Internet ou para clientes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="3c565-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="3c565-108">Recomendamos que a comunicação remota existente aplicativos ser migradas para as tecnologias mais recentes e mais seguras.</span><span class="sxs-lookup"><span data-stu-id="3c565-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="3c565-109">Se o design do aplicativo usa somente o HTTP e é RESTful, é recomendável API Web do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3c565-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="3c565-110">Para obter mais informações, consulte a API da Web do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3c565-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="3c565-111">Se o aplicativo é baseado em SOAP ou requer protocolos não Http, como TCP, é recomendável WCF.</span><span class="sxs-lookup"><span data-stu-id="3c565-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="3c565-112">Comparando a comunicação remota do .NET para WCF</span><span class="sxs-lookup"><span data-stu-id="3c565-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="3c565-113">Esta seção compara os blocos de construção básicos de .NET Remoting por seus equivalentes do WCF.</span><span class="sxs-lookup"><span data-stu-id="3c565-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="3c565-114">Posteriormente, usaremos esses blocos de construção para criar alguns cenários comuns de cliente-servidor no WCF. O gráfico a seguir resume as principais semelhanças e diferenças entre o .NET Remoting e WCF.</span><span class="sxs-lookup"><span data-stu-id="3c565-114">We will use these building blocks later to create some common client-server scenarios in WCF.The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="3c565-115">Comunicação remota .NET</span><span class="sxs-lookup"><span data-stu-id="3c565-115">.NET Remoting</span></span>|<span data-ttu-id="3c565-116">WCF</span><span class="sxs-lookup"><span data-stu-id="3c565-116">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="3c565-117">Tipo de servidor</span><span class="sxs-lookup"><span data-stu-id="3c565-117">Server type</span></span>|<span data-ttu-id="3c565-118">Subclasse MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="3c565-118">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="3c565-119">Marcar com o atributo [ServiceContract]</span><span class="sxs-lookup"><span data-stu-id="3c565-119">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="3c565-120">Operações de serviço</span><span class="sxs-lookup"><span data-stu-id="3c565-120">Service operations</span></span>|<span data-ttu-id="3c565-121">Métodos públicos no tipo de servidor</span><span class="sxs-lookup"><span data-stu-id="3c565-121">Public methods on server type</span></span>|<span data-ttu-id="3c565-122">Marcar com atributo [OperationContract]</span><span class="sxs-lookup"><span data-stu-id="3c565-122">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="3c565-123">Serialização</span><span class="sxs-lookup"><span data-stu-id="3c565-123">Serialization</span></span>|<span data-ttu-id="3c565-124">ISerializable ou [Serializable]</span><span class="sxs-lookup"><span data-stu-id="3c565-124">ISerializable or [Serializable]</span></span>|<span data-ttu-id="3c565-125">DataContractSerializer ou o XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="3c565-125">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="3c565-126">Objetos passados</span><span class="sxs-lookup"><span data-stu-id="3c565-126">Objects passed</span></span>|<span data-ttu-id="3c565-127">Por valor ou por referência</span><span class="sxs-lookup"><span data-stu-id="3c565-127">By-value or by-reference</span></span>|<span data-ttu-id="3c565-128">Por valor apenas</span><span class="sxs-lookup"><span data-stu-id="3c565-128">By-value only</span></span>|  
|<span data-ttu-id="3c565-129">Erros/exceções</span><span class="sxs-lookup"><span data-stu-id="3c565-129">Errors/exceptions</span></span>|<span data-ttu-id="3c565-130">Qualquer exceção serializável</span><span class="sxs-lookup"><span data-stu-id="3c565-130">Any serializable exception</span></span>|<span data-ttu-id="3c565-131">FaultContract\<TDetail ></span><span class="sxs-lookup"><span data-stu-id="3c565-131">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="3c565-132">Objetos de proxy de cliente</span><span class="sxs-lookup"><span data-stu-id="3c565-132">Client proxy objects</span></span>|<span data-ttu-id="3c565-133">Proxies transparentes com rigidez de tipos são criados automaticamente a partir MarshalByRefObjects existente</span><span class="sxs-lookup"><span data-stu-id="3c565-133">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="3c565-134">Proxies com rigidez de tipos gerados sob demanda usando ChannelFactory\<TChannel ></span><span class="sxs-lookup"><span data-stu-id="3c565-134">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="3c565-135">Plataforma necessária</span><span class="sxs-lookup"><span data-stu-id="3c565-135">Platform required</span></span>|<span data-ttu-id="3c565-136">Cliente e o servidor devem usar OS Microsoft e .NET</span><span class="sxs-lookup"><span data-stu-id="3c565-136">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="3c565-137">Plataforma cruzada</span><span class="sxs-lookup"><span data-stu-id="3c565-137">Cross-platform</span></span>|  
|<span data-ttu-id="3c565-138">Formato de mensagem</span><span class="sxs-lookup"><span data-stu-id="3c565-138">Message format</span></span>|<span data-ttu-id="3c565-139">Particular</span><span class="sxs-lookup"><span data-stu-id="3c565-139">Private</span></span>|<span data-ttu-id="3c565-140">Padrões do setor (SOAP, WS-*, etc.)</span><span class="sxs-lookup"><span data-stu-id="3c565-140">Industry standards (SOAP, WS-*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="3c565-141">Comparação de implementação do servidor</span><span class="sxs-lookup"><span data-stu-id="3c565-141">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="3c565-142">Criando um servidor de comunicação remota do .NET</span><span class="sxs-lookup"><span data-stu-id="3c565-142">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="3c565-143">Tipos de servidores de comunicação remota do .NET devem ser derivada de MarshalByRefObject e definir métodos que o cliente pode chamar, semelhante ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="3c565-143">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="3c565-144">Os métodos públicos deste tipo de servidor se tornar o contrato público disponível aos clientes.</span><span class="sxs-lookup"><span data-stu-id="3c565-144">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="3c565-145">Não há nenhuma separação entre a interface pública do servidor e sua implementação – um tipo lida com ambos.</span><span class="sxs-lookup"><span data-stu-id="3c565-145">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="3c565-146">Depois que o tipo de servidor tiver sido definido, ele pode ser disponibilizado para clientes, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c565-146">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),   
    "RemotingServer",   
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="3c565-147">Há muitas maneiras de disponibilizar o tipo de comunicação remota como um servidor, incluindo o uso de arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="3c565-147">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="3c565-148">Isso é apenas um exemplo.</span><span class="sxs-lookup"><span data-stu-id="3c565-148">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="3c565-149">Criando um servidor no WCF</span><span class="sxs-lookup"><span data-stu-id="3c565-149">Creating a Server in WCF</span></span>  
 <span data-ttu-id="3c565-150">A etapa equivalente no WCF envolve a criação de dois tipos – o público "contrato de serviço" e a implementação concreta.</span><span class="sxs-lookup"><span data-stu-id="3c565-150">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="3c565-151">A primeira é declarada como uma interface marcada com [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="3c565-151">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="3c565-152">Métodos disponíveis para os clientes são marcados com [OperationContract]:</span><span class="sxs-lookup"><span data-stu-id="3c565-152">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="3c565-153">Implementação do servidor é definida em uma classe concreta separada, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c565-153">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="3c565-154">Depois que esses tipos tiverem sido definidos, o servidor WCF pode ser disponibilizado aos clientes, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c565-154">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine(String.Format("The WCF server is ready at {0}.",  
                                    baseAddress));  
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="3c565-155">TCP é usado em ambos os exemplos para mantê-los mais semelhante possível.</span><span class="sxs-lookup"><span data-stu-id="3c565-155">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="3c565-156">Consulte a cenário orientações passo a passo neste tópico para obter exemplos usando HTTP.</span><span class="sxs-lookup"><span data-stu-id="3c565-156">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="3c565-157">Há muitas maneiras de configurar e hospedar serviços WCF.</span><span class="sxs-lookup"><span data-stu-id="3c565-157">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="3c565-158">Isso é apenas um exemplo, conhecido como "auto-hospedado".</span><span class="sxs-lookup"><span data-stu-id="3c565-158">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="3c565-159">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="3c565-159">For more information, see the following topics:</span></span>  
  
-   <span data-ttu-id="3c565-160">[How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md) (Como definir um contrato de serviço)</span><span class="sxs-lookup"><span data-stu-id="3c565-160">[How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md)</span></span>  
  
-   <span data-ttu-id="3c565-161">[Configuring Services Using Configuration Files](configuring-services-using-configuration-files.md) (Configurando serviços usando arquivos de configuração)</span><span class="sxs-lookup"><span data-stu-id="3c565-161">[Configuring Services Using Configuration Files](configuring-services-using-configuration-files.md)</span></span>  
  
-   <span data-ttu-id="3c565-162">[Hosting Services](hosting-services.md) (Hospedando serviços)</span><span class="sxs-lookup"><span data-stu-id="3c565-162">[Hosting Services](hosting-services.md)</span></span>  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="3c565-163">Comparação de implementação do cliente</span><span class="sxs-lookup"><span data-stu-id="3c565-163">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="3c565-164">Criando um cliente de comunicação remota do .NET</span><span class="sxs-lookup"><span data-stu-id="3c565-164">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="3c565-165">Depois que um objeto de servidor de .NET Remoting foi disponibilizado, eles podem ser consumidos por clientes, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c565-165">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("Customer {0} {1} received.",   
                                 customer.FirstName, customer.LastName));  
```  
  
 <span data-ttu-id="3c565-166">A instância RemotingServer retornada de Activator.GetObject() é conhecida como "proxy transparente."</span><span class="sxs-lookup"><span data-stu-id="3c565-166">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="3c565-167">Ele implementa a API pública para o tipo de RemotingServer no cliente, mas todos os métodos de chamam o objeto de servidor em execução em um computador ou um processo diferente.</span><span class="sxs-lookup"><span data-stu-id="3c565-167">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="3c565-168">Criando um cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="3c565-168">Creating a Client in WCF</span></span>  
 <span data-ttu-id="3c565-169">A etapa equivalente no WCF envolve o uso de uma fábrica de canais para criar o proxy explicitamente.</span><span class="sxs-lookup"><span data-stu-id="3c565-169">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="3c565-170">Como a comunicação remota, o objeto de proxy pode ser usado para invocar operações no servidor, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c565-170">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("  Customer {0} {1} received.",  
                    customer.FirstName, customer.LastName));  
```  
  
 <span data-ttu-id="3c565-171">Este exemplo mostra a programação no nível do canal porque é mais semelhante ao exemplo a comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="3c565-171">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="3c565-172">Também disponível é o **adicionar referência de serviço** abordagem no Visual Studio que gera código para simplificar a programação do cliente.</span><span class="sxs-lookup"><span data-stu-id="3c565-172">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="3c565-173">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="3c565-173">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="3c565-174">Programação de nível de canal do cliente</span><span class="sxs-lookup"><span data-stu-id="3c565-174">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
-   [<span data-ttu-id="3c565-175">Como: adicionar, atualizar ou remover uma referência de serviço</span><span class="sxs-lookup"><span data-stu-id="3c565-175">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="3c565-176">Uso de serialização</span><span class="sxs-lookup"><span data-stu-id="3c565-176">Serialization Usage</span></span>  
 <span data-ttu-id="3c565-177">Usam serialização de .NET Remoting e WCF para enviar objetos entre cliente e servidor, mas elas diferem das seguintes maneiras importantes:</span><span class="sxs-lookup"><span data-stu-id="3c565-177">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1.  <span data-ttu-id="3c565-178">Eles usam convenções e serializadores diferentes para indicar quais serializar.</span><span class="sxs-lookup"><span data-stu-id="3c565-178">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2.  <span data-ttu-id="3c565-179">Comunicação remota do .NET oferece suporte à serialização "por referência" que permite o acesso de método ou propriedade em uma camada, para executar o código na camada que é entre limites de segurança.</span><span class="sxs-lookup"><span data-stu-id="3c565-179">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="3c565-180">Esse recurso expõe vulnerabilidades de segurança e é uma das principais razões por pontos de extremidade nunca devem ser expostos para clientes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="3c565-180">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3.  <span data-ttu-id="3c565-181">Serialização usado pela comunicação remota é uma recusa (excluir explicitamente quais não serializar) e serialização do WCF é uma opção (marcar explicitamente quais membros para serializar).</span><span class="sxs-lookup"><span data-stu-id="3c565-181">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="3c565-182">Serialização no .NET Remoting</span><span class="sxs-lookup"><span data-stu-id="3c565-182">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="3c565-183">Comunicação remota do .NET oferece suporte a dois modos para serializar e desserializar objetos entre o cliente e servidor:</span><span class="sxs-lookup"><span data-stu-id="3c565-183">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
-   <span data-ttu-id="3c565-184">*Por valor* – os valores do objeto são serializados em limites de camada, e uma nova instância do objeto é criada na camada de.</span><span class="sxs-lookup"><span data-stu-id="3c565-184">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="3c565-185">Todas as chamadas para métodos ou propriedades da nova instância executar apenas localmente e não afetam o objeto original ou camada.</span><span class="sxs-lookup"><span data-stu-id="3c565-185">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
-   <span data-ttu-id="3c565-186">*Por referência* – especial "referência de objeto" é serializado em limites de camada.</span><span class="sxs-lookup"><span data-stu-id="3c565-186">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="3c565-187">Quando uma camada interage com métodos ou propriedades do objeto, ele se comunica para o objeto original na camada original.</span><span class="sxs-lookup"><span data-stu-id="3c565-187">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="3c565-188">Objetos por referência podem fluir em ambas as direções – servidor para o cliente ou cliente ao servidor.</span><span class="sxs-lookup"><span data-stu-id="3c565-188">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="3c565-189">Tipos de por valor de comunicação remota são marcados com o atributo [Serializable] ou implementam ISerializable, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c565-189">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="3c565-190">Tipos por referência derivam da classe MarshalByRefObject, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c565-190">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="3c565-191">É extremamente importante entender as implicações de objetos por referência do comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="3c565-191">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="3c565-192">Se qualquer camada (cliente ou servidor) envia um objeto por referência à outra camada, todas as chamadas de método executar novamente na camada do objeto de propriedade.</span><span class="sxs-lookup"><span data-stu-id="3c565-192">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="3c565-193">Por exemplo, um cliente chamar métodos em um objeto por referência retornado pelo servidor executará o código no servidor.</span><span class="sxs-lookup"><span data-stu-id="3c565-193">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="3c565-194">Da mesma forma, um servidor de chamar métodos em um objeto por referência fornecido pelo cliente executará o código novamente no cliente.</span><span class="sxs-lookup"><span data-stu-id="3c565-194">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="3c565-195">Por esse motivo, o uso de .NET Remoting é recomendável somente em ambientes totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="3c565-195">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="3c565-196">Expor um ponto de extremidade público do .NET Remoting para clientes não confiáveis fará um servidor remoto vulnerável a ataques.</span><span class="sxs-lookup"><span data-stu-id="3c565-196">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="3c565-197">Serialização no WCF</span><span class="sxs-lookup"><span data-stu-id="3c565-197">Serialization in WCF</span></span>  
 <span data-ttu-id="3c565-198">O WCF suporta apenas serialização de por valor.</span><span class="sxs-lookup"><span data-stu-id="3c565-198">WCF supports only by-value serialization.</span></span> <span data-ttu-id="3c565-199">A maneira mais comum para definir um tipo para trocar entre cliente e servidor é como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c565-199">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="3c565-200">O atributo [DataContract] identifica desse tipo como um que pode ser serializado e desserializado entre cliente e servidor.</span><span class="sxs-lookup"><span data-stu-id="3c565-200">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="3c565-201">O atributo [DataMember] identifica as propriedades individuais ou campos para serializar.</span><span class="sxs-lookup"><span data-stu-id="3c565-201">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="3c565-202">Quando o WCF envia um objeto em camadas, ele serializa somente os valores e cria uma nova instância do objeto na camada de.</span><span class="sxs-lookup"><span data-stu-id="3c565-202">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="3c565-203">Qualquer interação com os valores do objeto ocorre apenas localmente – eles não se comunicam com a outra camada que são os forma como os objetos .NET Remoting por referência.</span><span class="sxs-lookup"><span data-stu-id="3c565-203">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="3c565-204">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="3c565-204">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="3c565-205">Serialização e desserialização</span><span class="sxs-lookup"><span data-stu-id="3c565-205">Serialization and Deserialization</span></span>](./feature-details/serialization-and-deserialization.md)  
  
-   [<span data-ttu-id="3c565-206">Serialização no Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="3c565-206">Serialization in Windows Communication Foundation</span></span>](http://msdn.microsoft.com/magazine/cc163569.aspx)  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="3c565-207">Recursos de manipulação de exceção</span><span class="sxs-lookup"><span data-stu-id="3c565-207">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="3c565-208">Exceções de comunicação remota do .NET</span><span class="sxs-lookup"><span data-stu-id="3c565-208">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="3c565-209">Exceções geradas por um servidor remoto são serializadas, enviadas ao cliente e geradas localmente no cliente, como qualquer outra exceção.</span><span class="sxs-lookup"><span data-stu-id="3c565-209">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="3c565-210">Exceções personalizadas podem ser criadas por sub classing o tipo de exceção e marcá-lo com [Serializable].</span><span class="sxs-lookup"><span data-stu-id="3c565-210">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="3c565-211">A maioria das exceções do framework já são marcados dessa forma, permitindo que a maioria dos gerada pelo servidor, serializada e gerada novamente no cliente.</span><span class="sxs-lookup"><span data-stu-id="3c565-211">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="3c565-212">Embora esse design é conveniente durante o desenvolvimento, informações do servidor podem ser divulgadas inadvertidamente ao cliente.</span><span class="sxs-lookup"><span data-stu-id="3c565-212">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="3c565-213">Esta é uma das muitas razões que comunicação remota deve ser usada somente em ambientes totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="3c565-213">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="3c565-214">Exceções e falhas no WCF</span><span class="sxs-lookup"><span data-stu-id="3c565-214">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="3c565-215">WCF não permite tipos de exceção arbitrário seja retornada do servidor para o cliente porque isso pode levar a divulgação acidental.</span><span class="sxs-lookup"><span data-stu-id="3c565-215">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="3c565-216">Se uma operação de serviço lança uma exceção inesperada, ele faz com que uma FaultException seja gerada no cliente para uso geral.</span><span class="sxs-lookup"><span data-stu-id="3c565-216">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="3c565-217">Essa exceção não contém qualquer informação porque ou onde o problema ocorreu, e para alguns aplicativos, isso é suficiente.</span><span class="sxs-lookup"><span data-stu-id="3c565-217">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="3c565-218">Aplicativos que precisam se comunicar as informações de erro para o cliente não isso definindo um contrato de falha.</span><span class="sxs-lookup"><span data-stu-id="3c565-218">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="3c565-219">Para fazer isso, primeiro crie um tipo de [DataContract] para realizar as informações de falha.</span><span class="sxs-lookup"><span data-stu-id="3c565-219">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 <span data-ttu-id="3c565-220">Especifique o contrato de falha para cada operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="3c565-220">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="3c565-221">O servidor informa a condições de erro, lançando uma FaultException.</span><span class="sxs-lookup"><span data-stu-id="3c565-221">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="3c565-222">E sempre que o cliente faz uma solicitação para o servidor, ele pode detectar falhas como exceções normais.</span><span class="sxs-lookup"><span data-stu-id="3c565-222">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine(String.Format("Fault received: {0}",  
    fault.Detail.ErrorMessage));  
}  
```  
  
 <span data-ttu-id="3c565-223">Para obter mais informações sobre contratos de falha, consulte <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="3c565-223">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="3c565-224">Considerações sobre segurança</span><span class="sxs-lookup"><span data-stu-id="3c565-224">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="3c565-225">Segurança de comunicação remota do .NET</span><span class="sxs-lookup"><span data-stu-id="3c565-225">Security in .NET Remoting</span></span>  
 <span data-ttu-id="3c565-226">Alguns canais de comunicação remota do .NET oferecem suporte a recursos de segurança, como autenticação e criptografia na camada do canal (TCP e IPC).</span><span class="sxs-lookup"><span data-stu-id="3c565-226">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="3c565-227">O canal HTTP se baseia em serviços de informações da Internet (IIS) para autenticação e criptografia.</span><span class="sxs-lookup"><span data-stu-id="3c565-227">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="3c565-228">Apesar desse suporte, considere um protocolo de comunicação não segura a comunicação remota do .NET e usá-lo somente em ambientes totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="3c565-228">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="3c565-229">Nunca exponha um ponto de extremidade de comunicação remota público à Internet ou clientes não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="3c565-229">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="3c565-230">Segurança no WCF</span><span class="sxs-lookup"><span data-stu-id="3c565-230">Security in WCF</span></span>  
 <span data-ttu-id="3c565-231">O WCF foi projetado com segurança em mente, em parte para resolver os tipos de vulnerabilidades encontradas na comunicação remota do .NET.</span><span class="sxs-lookup"><span data-stu-id="3c565-231">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="3c565-232">WCF oferece segurança no nível de transporte e de mensagem e oferece muitas opções de autenticação, autorização, criptografia e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="3c565-232">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="3c565-233">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="3c565-233">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="3c565-234">Segurança</span><span class="sxs-lookup"><span data-stu-id="3c565-234">Security</span></span>](./feature-details/security.md)  
  
-   [<span data-ttu-id="3c565-235">Diretrizes de segurança do WCF</span><span class="sxs-lookup"><span data-stu-id="3c565-235">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="3c565-236">Migrando para o WCF</span><span class="sxs-lookup"><span data-stu-id="3c565-236">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="3c565-237">Por que migrar de comunicação remota para o WCF?</span><span class="sxs-lookup"><span data-stu-id="3c565-237">Why Migrate from Remoting to WCF?</span></span>  
  
-   <span data-ttu-id="3c565-238">**Comunicação remota do .NET é um produto herdado.**</span><span class="sxs-lookup"><span data-stu-id="3c565-238">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="3c565-239">Conforme descrito em [.NET Remoting](http://msdn.microsoft.com/library/vstudio/72x4h507\(v=vs.100\).aspx), ele é considerado um produto herdado e não é recomendado para novo desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="3c565-239">As described in [.NET Remoting](http://msdn.microsoft.com/library/vstudio/72x4h507\(v=vs.100\).aspx), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="3c565-240">WCF ou API Web do ASP.NET são recomendados para aplicativos novos e existentes.</span><span class="sxs-lookup"><span data-stu-id="3c565-240">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
-   <span data-ttu-id="3c565-241">**WCF usa os padrões de plataforma cruzada.**</span><span class="sxs-lookup"><span data-stu-id="3c565-241">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="3c565-242">O WCF foi projetado com a interoperabilidade entre plataformas em mente e dá suporte a muitos padrões do setor (SOAP, WS-Security, WS-Trust, etc.).</span><span class="sxs-lookup"><span data-stu-id="3c565-242">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="3c565-243">Um serviço WCF pode interoperar com clientes que executam sistemas operacionais diferentes do Windows.</span><span class="sxs-lookup"><span data-stu-id="3c565-243">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="3c565-244">Comunicação remota foi projetada principalmente para ambientes em que aplicativos cliente e servidor executados usando o .NET framework em um sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="3c565-244">Remoting was designed primarily for environments where both the server and client applications run using the .NET framework on a Windows operating system.</span></span>  
  
-   <span data-ttu-id="3c565-245">**O WCF possui segurança interna.**</span><span class="sxs-lookup"><span data-stu-id="3c565-245">**WCF has built-in security.**</span></span> <span data-ttu-id="3c565-246">O WCF foi projetado com base na segurança e oferece muitas opções de autenticação, segurança em nível de transporte, segurança em nível de mensagem, etc. Comunicação remota foi projetada para tornar mais fácil para os aplicativos a interagir, mas não foi projetada para ser seguro em ambientes não confiável.</span><span class="sxs-lookup"><span data-stu-id="3c565-246">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="3c565-247">O WCF foi projetado para trabalhar em ambientes confiáveis e não confiáveis.</span><span class="sxs-lookup"><span data-stu-id="3c565-247">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="3c565-248">Recomendações de migração</span><span class="sxs-lookup"><span data-stu-id="3c565-248">Migration Recommendations</span></span>  
 <span data-ttu-id="3c565-249">A seguir está as etapas recomendadas para migrar de comunicação remota do .NET para WCF:</span><span class="sxs-lookup"><span data-stu-id="3c565-249">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
-   <span data-ttu-id="3c565-250">**Crie o contrato de serviço.**</span><span class="sxs-lookup"><span data-stu-id="3c565-250">**Create the service contract.**</span></span> <span data-ttu-id="3c565-251">Definir seus tipos de interface de serviço e marcá-los com o atributo [ServiceContract]. Marca todos os métodos que os clientes terão permissão para chamar com [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="3c565-251">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
-   <span data-ttu-id="3c565-252">**Crie o contrato de dados.**</span><span class="sxs-lookup"><span data-stu-id="3c565-252">**Create the data contract.**</span></span> <span data-ttu-id="3c565-253">Defina os tipos de dados que serão trocados entre cliente e servidor e marcá-los com o atributo [DataContract].</span><span class="sxs-lookup"><span data-stu-id="3c565-253">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="3c565-254">Marca todos os campos e propriedades que o cliente poderá usar com [DataMember].</span><span class="sxs-lookup"><span data-stu-id="3c565-254">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
-   <span data-ttu-id="3c565-255">**Crie o contrato de falha (opcional).**</span><span class="sxs-lookup"><span data-stu-id="3c565-255">**Create the fault contract (optional).**</span></span> <span data-ttu-id="3c565-256">Crie os tipos que serão trocados entre cliente e servidor quando são encontrados erros.</span><span class="sxs-lookup"><span data-stu-id="3c565-256">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="3c565-257">Marca estes tipos com [DataContract] e [DataMember] para torná-las serializável.</span><span class="sxs-lookup"><span data-stu-id="3c565-257">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="3c565-258">Para todas as operações de serviço marcado com [OperationContract], também marcá-los com [FaultContract] para indicar que eles podem retornar os erros.</span><span class="sxs-lookup"><span data-stu-id="3c565-258">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
-   <span data-ttu-id="3c565-259">**Configurar e hospedar o serviço.**</span><span class="sxs-lookup"><span data-stu-id="3c565-259">**Configure and host the service.**</span></span> <span data-ttu-id="3c565-260">Quando o contrato de serviço tiver sido criado, a próxima etapa é configurar uma associação para expor o serviço em um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3c565-260">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="3c565-261">Para obter mais informações, consulte [pontos de extremidade: endereços, associações e contratos](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="3c565-261">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="3c565-262">Depois que um aplicativo de comunicação remota tiver sido migrado para o WCF, é importante remover dependências na comunicação remota do .NET.</span><span class="sxs-lookup"><span data-stu-id="3c565-262">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="3c565-263">Isso garante que todas as vulnerabilidades Remoting são removidas do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3c565-263">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="3c565-264">Essas etapas incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3c565-264">These steps include the following:</span></span>  
  
-   <span data-ttu-id="3c565-265">**Interromper o uso de MarshalByRefObject.**</span><span class="sxs-lookup"><span data-stu-id="3c565-265">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="3c565-266">O tipo de MarshalByRefObject existe apenas para comunicação remota e não é usado pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="3c565-266">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="3c565-267">Quaisquer tipos de aplicativo que sub classe MarshalByRefObject devem ser removidos ou alterados.</span><span class="sxs-lookup"><span data-stu-id="3c565-267">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span> <span data-ttu-id="3c565-268">O tipo de MarshalByRefObject existe apenas para comunicação remota e não é usado pelo WCF.</span><span class="sxs-lookup"><span data-stu-id="3c565-268">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="3c565-269">Quaisquer tipos de aplicativo que sub classe MarshalByRefObject devem ser removidos ou alterados.</span><span class="sxs-lookup"><span data-stu-id="3c565-269">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
-   <span data-ttu-id="3c565-270">**Interromper o uso de [Serializable] e ISerializable.**</span><span class="sxs-lookup"><span data-stu-id="3c565-270">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="3c565-271">O atributo [Serializable] e a interface ISerializable foram originalmente projetados para serializar os tipos em ambientes confiáveis, e eles são usados pela comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="3c565-271">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="3c565-272">Serialização no WCF se baseia em tipos que estão sendo marcados com [DataContract] e [DataMember].</span><span class="sxs-lookup"><span data-stu-id="3c565-272">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="3c565-273">Tipos de dados usados por um aplicativo devem ser modificados para usar [DataContract] e não usar ISerializable ou [Serializable].</span><span class="sxs-lookup"><span data-stu-id="3c565-273">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span> <span data-ttu-id="3c565-274">O atributo [Serializable] e a interface ISerializable foram originalmente projetados para serializar os tipos em ambientes confiáveis, e eles são usados pela comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="3c565-274">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="3c565-275">Serialização no WCF se baseia em tipos que estão sendo marcados com [DataContract] e [DataMember].</span><span class="sxs-lookup"><span data-stu-id="3c565-275">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="3c565-276">Tipos de dados usados por um aplicativo devem ser modificados para usar [DataContract] e não usar ISerializable ou [Serializable].</span><span class="sxs-lookup"><span data-stu-id="3c565-276">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="3c565-277">Cenários de migração</span><span class="sxs-lookup"><span data-stu-id="3c565-277">Migration Scenarios</span></span>  
 <span data-ttu-id="3c565-278">Agora vamos ver como realizar os seguintes cenários comuns de comunicação remota no WCF:</span><span class="sxs-lookup"><span data-stu-id="3c565-278">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1.  <span data-ttu-id="3c565-279">Servidor retorna um objeto por valor para o cliente</span><span class="sxs-lookup"><span data-stu-id="3c565-279">Server returns an object by-value to the client</span></span>  
  
2.  <span data-ttu-id="3c565-280">Servidor retorna uma objeto por referência para o cliente</span><span class="sxs-lookup"><span data-stu-id="3c565-280">Server returns an object by-reference to the client</span></span>  
  
3.  <span data-ttu-id="3c565-281">Cliente envia um objeto por valor para o servidor</span><span class="sxs-lookup"><span data-stu-id="3c565-281">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c565-282">Enviar uma objeto por referência do cliente para o servidor não é permitido no WCF.</span><span class="sxs-lookup"><span data-stu-id="3c565-282">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="3c565-283">Ao ler os cenários, suponha que o nosso interfaces de linha de base para a comunicação remota do .NET se parecer com o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3c565-283">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="3c565-284">A implementação de comunicação remota do .NET não é importante aqui como queremos ilustram apenas como usar o WCF para implementar a funcionalidade equivalente.</span><span class="sxs-lookup"><span data-stu-id="3c565-284">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="3c565-285">Cenário 1: O serviço retorna um objeto por valor</span><span class="sxs-lookup"><span data-stu-id="3c565-285">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="3c565-286">Este cenário demonstra um servidor retornando um objeto para o cliente por valor.</span><span class="sxs-lookup"><span data-stu-id="3c565-286">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="3c565-287">WCF sempre retorna objetos do servidor por valor, portanto as etapas a seguir simplesmente descrevem como criar um serviço WCF normal.</span><span class="sxs-lookup"><span data-stu-id="3c565-287">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1.  <span data-ttu-id="3c565-288">Inicie com a definição de uma interface pública para o serviço WCF e marcá-la com o atributo [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="3c565-288">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="3c565-289">Usamos [OperationContract] para identificar os métodos do lado do servidor de que nosso cliente chamar.</span><span class="sxs-lookup"><span data-stu-id="3c565-289">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2.  <span data-ttu-id="3c565-290">A próxima etapa é criar o contrato de dados para este serviço.</span><span class="sxs-lookup"><span data-stu-id="3c565-290">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="3c565-291">Podemos fazer isso criando classes (não interfaces) marcados com o atributo [DataContract].</span><span class="sxs-lookup"><span data-stu-id="3c565-291">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="3c565-292">As propriedades individuais ou campos que desejamos visíveis para o cliente e servidor são marcados com [DataMember].</span><span class="sxs-lookup"><span data-stu-id="3c565-292">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="3c565-293">Se quisermos tipos derivados para ser permitido, podemos deve usar o atributo [KnownType] para identificá-los.</span><span class="sxs-lookup"><span data-stu-id="3c565-293">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="3c565-294">Os únicos tipos de WCF permitirá a ser serializado ou desserializado para esse serviço são aqueles na interface do serviço e essas "tipos conhecidos".</span><span class="sxs-lookup"><span data-stu-id="3c565-294">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="3c565-295">Tentativa de trocar de qualquer outro tipo ausentes nesta lista será rejeitada.</span><span class="sxs-lookup"><span data-stu-id="3c565-295">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer   
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3.  <span data-ttu-id="3c565-296">Em seguida, fornecemos a implementação da interface de serviço.</span><span class="sxs-lookup"><span data-stu-id="3c565-296">Next, we provide the implementation for the service interface.</span></span>  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4.  <span data-ttu-id="3c565-297">Para executar o serviço WCF, é necessário declarar um ponto de extremidade que expõe essa interface de serviço em uma URL específica usando uma associação específica do WCF.</span><span class="sxs-lookup"><span data-stu-id="3c565-297">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="3c565-298">Normalmente, isso é feito adicionando as seções a seguir ao arquivo de Web. config do projeto do servidor.</span><span class="sxs-lookup"><span data-stu-id="3c565-298">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5.  <span data-ttu-id="3c565-299">O serviço WCF, em seguida, pode ser iniciado com o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c565-299">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="3c565-300">Quando este ServiceHost é iniciado, ele usa o arquivo Web. config para estabelecer o contrato apropriado, a associação e o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3c565-300">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="3c565-301">Para obter mais informações sobre arquivos de configuração, consulte [Configurando serviços usando arquivos de configuração](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="3c565-301">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="3c565-302">Esse estilo de iniciar o servidor é conhecido como hospedagem interna.</span><span class="sxs-lookup"><span data-stu-id="3c565-302">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="3c565-303">Para saber mais sobre as outras opções de hospedar serviços WCF, consulte [serviços de hospedagem](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="3c565-303">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6.  <span data-ttu-id="3c565-304">App. config do projeto de cliente deve declarar correspondente informações de associação para o ponto de extremidade do serviço.</span><span class="sxs-lookup"><span data-stu-id="3c565-304">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="3c565-305">A maneira mais fácil de fazer isso no Visual Studio é usar **adicionar referência de serviço**, que atualizará automaticamente o arquivo App. config.</span><span class="sxs-lookup"><span data-stu-id="3c565-305">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="3c565-306">Como alternativa, essas mesmas alterações podem ser adicionadas manualmente.</span><span class="sxs-lookup"><span data-stu-id="3c565-306">Alternatively, these same changes can be added manually.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="3c565-307">Para obter mais informações sobre como usar **adicionar referência de serviço**, consulte [como: adicionar, atualizar ou remover uma referência de serviço](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span><span class="sxs-lookup"><span data-stu-id="3c565-307">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7.  <span data-ttu-id="3c565-308">Agora podemos chamar o serviço WCF do cliente.</span><span class="sxs-lookup"><span data-stu-id="3c565-308">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="3c565-309">Fazemos isso criando uma fábrica de canais para esse serviço, solicitando-lo para um canal e chamar diretamente o método que queremos naquele canal.</span><span class="sxs-lookup"><span data-stu-id="3c565-309">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="3c565-310">Podemos fazer isso porque o canal implementa a interface do serviço e manipula a lógica subjacente de solicitação/resposta para nós.</span><span class="sxs-lookup"><span data-stu-id="3c565-310">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="3c565-311">O valor de retorno de chamada de método que é a cópia desserializada de resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="3c565-311">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine(String.Format("  Customer {0} {1} received.",  
           customer.FirstName, customer.LastName));  
   ```  
  
 <span data-ttu-id="3c565-312">Objetos retornados pelo WCF do servidor para o cliente são sempre pelo valor.</span><span class="sxs-lookup"><span data-stu-id="3c565-312">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="3c565-313">Os objetos são cópias desserializadas dos dados enviados pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="3c565-313">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="3c565-314">O cliente pode chamar métodos nessas cópias locais sem qualquer risco de invocar o código do servidor por meio de retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="3c565-314">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="3c565-315">Cenário 2: O servidor retornará um objeto por referência</span><span class="sxs-lookup"><span data-stu-id="3c565-315">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="3c565-316">Este cenário demonstra o servidor que fornece um objeto para o cliente por referência.</span><span class="sxs-lookup"><span data-stu-id="3c565-316">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="3c565-317">Na comunicação remota do .NET, isso é tratado automaticamente para qualquer tipo derivado de MarshalByRefObject, que é serializado por referência.</span><span class="sxs-lookup"><span data-stu-id="3c565-317">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="3c565-318">Um exemplo desse cenário é permitir que vários clientes têm objetos independentes de sessão do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="3c565-318">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="3c565-319">Como mencionado anteriormente, objetos retornados por um serviço WCF não são sempre pelo valor, portanto não há nenhum equivalente direto de um objeto por referência, mas é possível obter algo semelhante ao uso de semântica por referência um <xref:System.ServiceModel.EndpointAddress10> objeto.</span><span class="sxs-lookup"><span data-stu-id="3c565-319">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="3c565-320">Esse é um objeto de serializável pelo valor que pode ser usado pelo cliente para obter um objeto de sessão por referência no servidor.</span><span class="sxs-lookup"><span data-stu-id="3c565-320">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="3c565-321">Isso permite que o cenário de ter vários clientes com objetos independentes de sessão do lado do servidor.</span><span class="sxs-lookup"><span data-stu-id="3c565-321">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1.  <span data-ttu-id="3c565-322">Primeiro, precisamos definir um contrato de serviço WCF que corresponde ao objeto de sessão em si.</span><span class="sxs-lookup"><span data-stu-id="3c565-322">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    >  <span data-ttu-id="3c565-323">Observe que o objeto de sessão é marcado com [ServiceContract], tornando uma interface de serviço WCF normal.</span><span class="sxs-lookup"><span data-stu-id="3c565-323">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="3c565-324">Definindo o SessionMode propriedade indica que é um serviço de sessão.</span><span class="sxs-lookup"><span data-stu-id="3c565-324">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="3c565-325">No WCF, uma sessão é uma maneira de correlacionar várias mensagens enviadas entre dois pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3c565-325">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="3c565-326">Isso significa que, depois que um cliente obtiver uma conexão para esse serviço, uma sessão será estabelecida entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="3c565-326">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="3c565-327">O cliente usará uma única instância exclusiva do objeto do lado do servidor para todas as interações dele nessa única sessão.</span><span class="sxs-lookup"><span data-stu-id="3c565-327">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2.  <span data-ttu-id="3c565-328">Em seguida, é preciso fornecer a implementação desta interface de serviço.</span><span class="sxs-lookup"><span data-stu-id="3c565-328">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="3c565-329">Que com [ServiceBehavior] e definindo o InstanceContextMode, informamos WCF que queremos usar uma instância exclusiva deste tipo para uma sessão de cada.</span><span class="sxs-lookup"><span data-stu-id="3c565-329">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3.  <span data-ttu-id="3c565-330">Agora precisamos de uma maneira de obter uma instância deste objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="3c565-330">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="3c565-331">Podemos fazer isso criando outra interface de serviço WCF que retorna um objeto EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="3c565-331">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="3c565-332">Esta é uma forma serializável de um ponto de extremidade que o cliente pode usar para criar o objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="3c565-332">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="3c565-333">E podemos implementar esse serviço WCF:</span><span class="sxs-lookup"><span data-stu-id="3c565-333">And we implement this WCF service:</span></span>  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =   
               new ChannelFactory<ISessionBoundObject>("sessionbound");  
 
           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     <span data-ttu-id="3c565-334">Essa implementação mantém uma fábrica de canais única para criar objetos de sessão.</span><span class="sxs-lookup"><span data-stu-id="3c565-334">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="3c565-335">Quando GetInstanceAddress() é chamado, ele cria um canal e cria um objeto EndpointAddress10 que efetivamente aponta para o endereço remoto associado a esse canal.</span><span class="sxs-lookup"><span data-stu-id="3c565-335">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="3c565-336">EndpointAddress10 é simplesmente um tipo de dados que pode ser retornado ao cliente pelo valor.</span><span class="sxs-lookup"><span data-stu-id="3c565-336">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4.  <span data-ttu-id="3c565-337">É preciso modificar o arquivo de configuração do servidor, fazendo os dois itens a seguir, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3c565-337">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1.  <span data-ttu-id="3c565-338">Declarar um \<cliente > seção que descreve o ponto de extremidade para o objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="3c565-338">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="3c565-339">Isso é necessário porque o servidor também atua como um cliente nessa situação.</span><span class="sxs-lookup"><span data-stu-id="3c565-339">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2.  <span data-ttu-id="3c565-340">Declare os pontos de extremidade para o objeto de fábrica e sessão.</span><span class="sxs-lookup"><span data-stu-id="3c565-340">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="3c565-341">Isso é necessário para permitir que o cliente para se comunicar com os pontos de extremidade de serviço para adquirir o EndpointAddress10 e criar o canal de sessão.</span><span class="sxs-lookup"><span data-stu-id="3c565-341">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="3c565-342">E, em seguida, podemos começar a esses serviços:</span><span class="sxs-lookup"><span data-stu-id="3c565-342">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5.  <span data-ttu-id="3c565-343">Podemos configurar o cliente declarando esses mesmos pontos de extremidade no arquivo de App. config do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="3c565-343">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6.  <span data-ttu-id="3c565-344">Para criar e usar esse objeto de sessão, o cliente deve fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3c565-344">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1.  <span data-ttu-id="3c565-345">Crie um canal para o serviço ISessionBoundFactory.</span><span class="sxs-lookup"><span data-stu-id="3c565-345">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2.  <span data-ttu-id="3c565-346">Use esse canal para invocar esse serviço para obter um EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="3c565-346">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3.  <span data-ttu-id="3c565-347">Use o EndpointAddress10 para criar um canal para obter um objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="3c565-347">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4.  <span data-ttu-id="3c565-348">Interagir com o objeto de sessão para demonstrar permanece a mesma instância em várias chamadas.</span><span class="sxs-lookup"><span data-stu-id="3c565-348">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =   
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 <span data-ttu-id="3c565-349">WCF sempre retorna objetos por valor, mas é possível dar suporte o equivalente de semântica por referência com o uso de EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="3c565-349">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="3c565-350">Isso permite que o cliente solicite uma instância de serviço WCF sessão, após o qual ele pode interagir com ele como qualquer outro serviço do WCF.</span><span class="sxs-lookup"><span data-stu-id="3c565-350">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="3c565-351">Cenário 3: O cliente envia Server uma instância por valor</span><span class="sxs-lookup"><span data-stu-id="3c565-351">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="3c565-352">Este cenário demonstra o cliente enviar uma instância de objeto não primitivos para o servidor por valor.</span><span class="sxs-lookup"><span data-stu-id="3c565-352">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="3c565-353">Como WCF apenas envia objetos pelo valor, este cenário demonstra o uso normal do WCF.</span><span class="sxs-lookup"><span data-stu-id="3c565-353">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1.  <span data-ttu-id="3c565-354">Use o mesmo serviço de WCF do cenário 1.</span><span class="sxs-lookup"><span data-stu-id="3c565-354">Use the same WCF Service from Scenario 1.</span></span>  
  
2.  <span data-ttu-id="3c565-355">Use o cliente para criar um novo objeto de por valor (cliente), criar um canal para se comunicar com o serviço de ICustomerService e enviar o objeto para ele.</span><span class="sxs-lookup"><span data-stu-id="3c565-355">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {   
   FirstName = "Bob",   
   LastName = "Jones",   
   CustomerId = 43,   
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine(String.Format("  Server returned {0}.", success));  
   ```  
  
     <span data-ttu-id="3c565-356">O objeto de cliente será serializado e enviado ao servidor, onde ele é desserializado em uma nova cópia do objeto.</span><span class="sxs-lookup"><span data-stu-id="3c565-356">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3c565-357">Esse código também ilustra o envio de um tipo derivado (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="3c565-357">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="3c565-358">A interface de serviço espera um objeto de cliente, mas o atributo [KnownType] na classe Customer indicado que premiumcustomer também foi permitido.</span><span class="sxs-lookup"><span data-stu-id="3c565-358">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="3c565-359">WCF falharão qualquer tentativa de serializar ou desserializar qualquer outro tipo por meio dessa interface de serviço.</span><span class="sxs-lookup"><span data-stu-id="3c565-359">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="3c565-360">Trocas de WCF normal de dados são por valor.</span><span class="sxs-lookup"><span data-stu-id="3c565-360">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="3c565-361">Isso garante que invocar métodos em um desses objetos de dados executa apenas localmente – não chamará o código na camada de.</span><span class="sxs-lookup"><span data-stu-id="3c565-361">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="3c565-362">Embora seja possível fazer algo como objetos por referência retornados *de* o servidor, não é possível para um cliente passar um objeto por referência *para* o servidor.</span><span class="sxs-lookup"><span data-stu-id="3c565-362">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="3c565-363">Um cenário que requer uma conversa de ida e volta entre o cliente e o servidor pode ser obtido no WCF usando um serviço duplex.</span><span class="sxs-lookup"><span data-stu-id="3c565-363">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="3c565-364">Para obter mais informações, consulte [serviços Duplex](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="3c565-364">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="3c565-365">Resumo</span><span class="sxs-lookup"><span data-stu-id="3c565-365">Summary</span></span>  
 <span data-ttu-id="3c565-366">Comunicação remota do .NET é uma estrutura de comunicação deve ser usado somente em ambientes totalmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="3c565-366">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="3c565-367">É um produto herdado e tem suporte somente para compatibilidade com versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="3c565-367">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="3c565-368">Ele não deve ser usado para criar novos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="3c565-368">It should not be used to build new applications.</span></span> <span data-ttu-id="3c565-369">Por outro lado, o WCF foi projetado com base na segurança e é recomendado para aplicativos novos e existentes.</span><span class="sxs-lookup"><span data-stu-id="3c565-369">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="3c565-370">A Microsoft recomenda se os aplicativos remotos ser migrada para usar o WCF ou API Web do ASP.NET em vez disso.</span><span class="sxs-lookup"><span data-stu-id="3c565-370">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>