---
title: "Expedição por elemento Body"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f64a3c04-62b4-47b2-91d9-747a3af1659f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c3624290176d93519ae420a98a7e93534d910fa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="dispatch-by-body-element"></a><span data-ttu-id="01f1f-102">Expedição por elemento Body</span><span class="sxs-lookup"><span data-stu-id="01f1f-102">Dispatch by Body Element</span></span>
<span data-ttu-id="01f1f-103">Este exemplo demonstra como implementar um algoritmo alternativo para a atribuição de mensagens de entrada para as operações.</span><span class="sxs-lookup"><span data-stu-id="01f1f-103">This sample demonstrates how to implement an alternate algorithm for assigning incoming messages to operations.</span></span>  
  
 <span data-ttu-id="01f1f-104">Por padrão, o dispatcher do modelo de serviço seleciona o método de manipulação de apropriado para uma mensagem de entrada com base no WS-Addressing da mensagem "Ação" informação de cabeçalho ou a equivalente na solicitação HTTP SOAP.</span><span class="sxs-lookup"><span data-stu-id="01f1f-104">By default, the service model dispatcher selects the appropriate handling method for an incoming message based on the message's WS-Addressing "Action" header or the equivalent information in the HTTP SOAP request.</span></span>  
  
 <span data-ttu-id="01f1f-105">Alguns Web SOAP 1.1 serviços pilhas que não seguem o WS-I Basic Profile 1.1 diretrizes não enviar mensagens com base no URI de ação, mas em vez disso, com base no nome qualificado XML do primeiro elemento dentro do corpo SOAP.</span><span class="sxs-lookup"><span data-stu-id="01f1f-105">Some SOAP 1.1 Web services stacks that do not follow the WS-I Basic Profile 1.1 guidelines do not dispatch messages based on the Action URI, but rather based on the XML qualified name of the first element inside the SOAP body.</span></span> <span data-ttu-id="01f1f-106">Da mesma forma, o lado do cliente dessas pilhas pode enviar mensagens com um cabeçalho de HTTP SoapAction arbitrário ou vazio, que era permitido pela especificação do SOAP 1.1.</span><span class="sxs-lookup"><span data-stu-id="01f1f-106">Likewise, the client side of these stacks might send messages with an empty or arbitrary HTTP SoapAction header, which was permitted by the SOAP 1.1 specification.</span></span>  
  
 <span data-ttu-id="01f1f-107">Para alterar a maneira como as mensagens são enviadas para métodos, o exemplo implementa o <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface extensibilidade a `DispatchByBodyElementOperationSelector`.</span><span class="sxs-lookup"><span data-stu-id="01f1f-107">To change the way messages are dispatched to methods, the sample implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> extensibility interface on the `DispatchByBodyElementOperationSelector`.</span></span> <span data-ttu-id="01f1f-108">Essa classe seleciona operações de acordo com o primeiro elemento do corpo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="01f1f-108">This class selects operations based on the first element of the message body.</span></span>  
  
 <span data-ttu-id="01f1f-109">O construtor da classe espera um dicionário preenchido com pares de `XmlQualifiedName` e cadeias de caracteres, na qual os nomes qualificados indicam o nome do primeiro filho do corpo SOAP e as cadeias de caracteres indicam o nome da operação correspondente.</span><span class="sxs-lookup"><span data-stu-id="01f1f-109">The class constructor expects a dictionary populated with pairs of `XmlQualifiedName` and strings, whereby the qualified names indicate the name of the first child of the SOAP body and the strings indicate the matching operation name.</span></span> <span data-ttu-id="01f1f-110">O `defaultOperationName` é o nome da operação que recebe todas as mensagens que não podem ser comparadas com este dicionário:</span><span class="sxs-lookup"><span data-stu-id="01f1f-110">The `defaultOperationName` is the name of the operation that receives all messages that cannot be matched against this dictionary:</span></span>  
  
```  
class DispatchByBodyElementOperationSelector : IDispatchOperationSelector  
{  
    Dictionary<XmlQualifiedName, string> dispatchDictionary;  
    string defaultOperationName;  
  
    public DispatchByBodyElementOperationSelector(Dictionary<XmlQualifiedName,string> dispatchDictionary, string defaultOperationName)  
    {  
        this.dispatchDictionary = dispatchDictionary;  
        this.defaultOperationName = defaultOperationName;  
    }  
```  
  
 <span data-ttu-id="01f1f-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector>implementações são muito simples de compilação porque há apenas um método na interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span><span class="sxs-lookup"><span data-stu-id="01f1f-111"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> implementations are very straightforward to build as there is only one method on the interface: <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A>.</span></span> <span data-ttu-id="01f1f-112">O trabalho deste método é para inspecionar uma mensagem de entrada e retornar uma cadeia de caracteres que é igual ao nome de um método no contrato de serviço para o ponto de extremidade atual.</span><span class="sxs-lookup"><span data-stu-id="01f1f-112">The job of this method is to inspect an incoming message and to return a string that equals the name of a method on the service contract for the current endpoint.</span></span>  
  
 <span data-ttu-id="01f1f-113">Neste exemplo, o seletor de operação adquire um <xref:System.Xml.XmlDictionaryReader> para a mensagem de entrada do corpo usando <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span><span class="sxs-lookup"><span data-stu-id="01f1f-113">In this sample, the operation selector acquires an <xref:System.Xml.XmlDictionaryReader> for the incoming message's body using <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A>.</span></span> <span data-ttu-id="01f1f-114">Este método já posiciona o leitor no primeiro filho do corpo da mensagem, para que seja suficiente para obter o nome do elemento atual e o URI de namespace e combiná-los em um `XmlQualifiedName` que é usado para pesquisar a operação correspondente a dicionário mantido pelo seletor de operação.</span><span class="sxs-lookup"><span data-stu-id="01f1f-114">This method already positions the reader on the first child of the message's body so that it is sufficient to get the current element's name and namespace URI and combine them into an `XmlQualifiedName` that is then used for looking up the corresponding operation from the dictionary held by the operation selector.</span></span>  
  
```  
public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
{  
    XmlDictionaryReader bodyReader = message.GetReaderAtBodyContents();  
    XmlQualifiedName lookupQName = new  
       XmlQualifiedName(bodyReader.LocalName, bodyReader.NamespaceURI);  
    message = CreateMessageCopy(message,bodyReader);  
    if (dispatchDictionary.ContainsKey(lookupQName))  
    {  
         return dispatchDictionary[lookupQName];  
    }  
    else  
    {  
        return defaultOperationName;  
    }  
}  
```  
  
 <span data-ttu-id="01f1f-115">Acessando o corpo da mensagem com <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> ou qualquer um dos outros métodos que fornecem acesso ao conteúdo do corpo da mensagem faz com que a mensagem a ser marcado como "leitura", que significa que a mensagem é inválida para processamento.</span><span class="sxs-lookup"><span data-stu-id="01f1f-115">Accessing the message body with <xref:System.ServiceModel.Channels.Message.GetReaderAtBodyContents%2A> or any of the other methods that provide access to the message's body content causes the message to be marked as "read", which means that the message is invalid for any further processing.</span></span> <span data-ttu-id="01f1f-116">Portanto, o seletor de operação cria uma cópia da mensagem de entrada com o método mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="01f1f-116">Therefore, the operation selector creates a copy of the incoming message with the method shown in the following code.</span></span> <span data-ttu-id="01f1f-117">Porque a posição do leitor não foi alterada durante a inspeção, ele pode ser referenciado pela mensagem recém-criado para o qual as propriedades de mensagem e os cabeçalhos de mensagem também são copiados, que resulta em um clone exato da mensagem original:</span><span class="sxs-lookup"><span data-stu-id="01f1f-117">Because the reader's position has not been changed during the inspection, it can be referenced by the newly created message to which the message properties and the message headers are also copied, which results in an exact clone of the original message:</span></span>  
  
```  
private Message CreateMessageCopy(Message message,   
                                     XmlDictionaryReader body)  
{  
    Message copy = Message.CreateMessage(message.Version,message.Headers.Action,body);  
    copy.Headers.CopyHeaderFrom(message,0);  
    copy.Properties.CopyProperties(message.Properties);  
    return copy;  
}  
```  
  
## <a name="adding-an-operation-selector-to-a-service"></a><span data-ttu-id="01f1f-118">Adicionando um seletor de operação para um serviço</span><span class="sxs-lookup"><span data-stu-id="01f1f-118">Adding an Operation Selector to a Service</span></span>  
 <span data-ttu-id="01f1f-119">Seletores de operação de expedição de serviço são extensões para o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dispatcher.</span><span class="sxs-lookup"><span data-stu-id="01f1f-119">Service dispatch operation selectors are extensions to the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dispatcher.</span></span> <span data-ttu-id="01f1f-120">Para selecionar os métodos no canal de retorno de chamada de contratos duplex, também há seletores de operação de cliente, que funcionam muito bem como os seletores de operação de expedição descritos aqui, mas que não é abordado neste exemplo explicitamente.</span><span class="sxs-lookup"><span data-stu-id="01f1f-120">For selecting methods on the callback channel of duplex contracts, there are also client operation selectors, which work very much like the dispatch operation selectors described here, but which are not explicitly covered in this sample.</span></span>  
  
 <span data-ttu-id="01f1f-121">Como a maioria das extensões do modelo de serviço, expedição seletores são adicionados para o distribuidor usando comportamentos de operação.</span><span class="sxs-lookup"><span data-stu-id="01f1f-121">Like most service model extensions, dispatch operation selectors are added to the dispatcher using behaviors.</span></span> <span data-ttu-id="01f1f-122">Um *comportamento* é um objeto de configuração, que adiciona uma ou mais extensões para o tempo de execução de despacho (ou no tempo de execução do cliente) ou se transforma suas configurações.</span><span class="sxs-lookup"><span data-stu-id="01f1f-122">A *behavior* is a configuration object, which either adds one or more extensions to the dispatch runtime (or to the client runtime) or otherwise changes its settings.</span></span>  
  
 <span data-ttu-id="01f1f-123">Como os seletores de operação têm escopo de contrato, o comportamento apropriado para implementar aqui é o <xref:System.ServiceModel.Description.IContractBehavior>.</span><span class="sxs-lookup"><span data-stu-id="01f1f-123">Because operation selectors have contract scope, the appropriate behavior to implement here is the <xref:System.ServiceModel.Description.IContractBehavior>.</span></span> <span data-ttu-id="01f1f-124">Porque a interface é implementada em um <xref:System.Attribute> classe derivada conforme mostrado no código a seguir, o comportamento pode ser adicionado declarativamente a qualquer contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="01f1f-124">Because the interface is implemented on a <xref:System.Attribute> derived class as shown in the following code, the behavior can be declaratively added to any service contract.</span></span> <span data-ttu-id="01f1f-125">Sempre que um <xref:System.ServiceModel.ServiceHost> é aberto e o tempo de execução de despacho é criado, todos os comportamentos encontrado como atributos em contratos, operações e implementações de serviço ou como um elemento na configuração de serviço são adicionados automaticamente e subsequentemente solicitado contribuir extensões ou modifique a configuração padrão.</span><span class="sxs-lookup"><span data-stu-id="01f1f-125">Whenever a <xref:System.ServiceModel.ServiceHost> is opened and the dispatch runtime is built, all behaviors found either as attributes on contracts, operations, and service implementations or as element in the service configuration are automatically added and subsequently asked to contribute extensions or modify the default configuration.</span></span>  
  
 <span data-ttu-id="01f1f-126">Para resumir, o trecho de código a seguir mostra apenas a implementação do método <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, que afeta as alterações de configuração para o dispatcher neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="01f1f-126">For brevity, the following code excerpt only shows the implementation of the method <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A>, which effects the configuration changes for the dispatcher in this sample.</span></span> <span data-ttu-id="01f1f-127">Os outros métodos não são mostrados porque elas retornam ao chamador sem fazer qualquer trabalho.</span><span class="sxs-lookup"><span data-stu-id="01f1f-127">The other methods are not shown because they return to the caller without doing any work.</span></span>  
  
```  
[AttributeUsage(AttributeTargets.Class|AttributeTargets.Interface)]  
class DispatchByBodyElementBehaviorAttribute : Attribute, IContractBehavior  
{  
    // public void AddBindingParameters(...)   
    // public void ApplyClientBehavior(...)  
    // public void Validate(...)  
```  
  
 <span data-ttu-id="01f1f-128">Primeiro, o <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementação define o dicionário de pesquisa para o seletor de operação pela iteração no <xref:System.ServiceModel.Description.OperationDescription> elementos na extremidade do serviço <xref:System.ServiceModel.Description.ContractDescription>.</span><span class="sxs-lookup"><span data-stu-id="01f1f-128">First, the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%2A> implementation sets up the lookup dictionary for the operation selector by iterating over the <xref:System.ServiceModel.Description.OperationDescription> elements in the service endpoint's <xref:System.ServiceModel.Description.ContractDescription>.</span></span> <span data-ttu-id="01f1f-129">Em seguida, a descrição de cada operação é inspecionada a presença do `DispatchBodyElementAttribute` comportamento, uma implementação de <xref:System.ServiceModel.Description.IOperationBehavior> que também está definido neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="01f1f-129">Then, each operation description is inspected for the presence of the `DispatchBodyElementAttribute` behavior, an implementation of <xref:System.ServiceModel.Description.IOperationBehavior> that is also defined in this sample.</span></span> <span data-ttu-id="01f1f-130">Embora essa classe também é um comportamento, é passivo e não contribuem ativamente alterações de configuração para o tempo de execução de expedição.</span><span class="sxs-lookup"><span data-stu-id="01f1f-130">While this class is also a behavior, it is passive and does not actively contribute any configuration changes to the dispatch runtime.</span></span> <span data-ttu-id="01f1f-131">Todos os seus métodos de retornam ao chamador sem realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="01f1f-131">All of its methods return to the caller without taking any actions.</span></span> <span data-ttu-id="01f1f-132">O comportamento de operação só existe para que os metadados necessários para o novo expedição mecanismo, ou seja, o nome qualificado do elemento body em cuja ocorrência de uma operação for selecionada, podem ser associados com as operações do respectivas.</span><span class="sxs-lookup"><span data-stu-id="01f1f-132">The operation behavior only exists so that the metadata required for the new dispatch mechanism, namely the qualified name of the body element on whose occurrence an operation is selected, can be associated with the respective operations.</span></span>  
  
 <span data-ttu-id="01f1f-133">Se tal comportamento de um for encontrado, um par de valor criado a partir o nome qualificado XML (`QName` propriedade) e o nome da operação (`Name` propriedade) é adicionada ao dicionário.</span><span class="sxs-lookup"><span data-stu-id="01f1f-133">If such a behavior is found, a value pair created from the XML qualified name (`QName` property) and the operation name (`Name` property) is added to the dictionary.</span></span>  
  
 <span data-ttu-id="01f1f-134">Depois que o dicionário for preenchido, um novo `DispatchByBodyElementOperationSelector` é construído com essas informações e definido como o seletor de operação de tempo de execução de despacho:</span><span class="sxs-lookup"><span data-stu-id="01f1f-134">Once the dictionary is populated, a new `DispatchByBodyElementOperationSelector` is constructed with this information and set as the operation selector of the dispatch runtime:</span></span>  
  
```  
public void ApplyDispatchBehavior(ContractDescription contractDescription, ServiceEndpoint endpoint, System.ServiceModel.Dispatcher.DispatchRuntime dispatchRuntime)  
{  
    Dictionary<XmlQualifiedName,string> dispatchDictionary =   
                     new Dictionary<XmlQualifiedName,string>();  
    foreach( OperationDescription operationDescription in   
                              contractDescription.Operations )  
    {  
        DispatchBodyElementAttribute dispatchBodyElement =   
   operationDescription.Behaviors.Find<DispatchBodyElementAttribute>();  
        if ( dispatchBodyElement != null )  
        {  
             dispatchDictionary.Add(dispatchBodyElement.QName,   
                              operationDescription.Name);  
        }  
    }  
    dispatchRuntime.OperationSelector =   
            new DispatchByBodyElementOperationSelector(  
               dispatchDictionary,   
               dispatchRuntime.UnhandledDispatchOperation.Name);  
    }  
}  
```  
  
## <a name="implementing-the-service"></a><span data-ttu-id="01f1f-135">Implementando o serviço</span><span class="sxs-lookup"><span data-stu-id="01f1f-135">Implementing the Service</span></span>  
 <span data-ttu-id="01f1f-136">O comportamento implementado neste exemplo diretamente afeta como mensagens de transmissão são interpretadas e distribuídas, que é uma função do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="01f1f-136">The behavior implemented in this sample directly affects how messages from the wire are interpreted and dispatched, which is a function of the service contract.</span></span> <span data-ttu-id="01f1f-137">Consequentemente, o comportamento deve ser declarado no nível de contrato de serviço em qualquer implementação de serviço que desejar usá-lo.</span><span class="sxs-lookup"><span data-stu-id="01f1f-137">Consequently, the behavior should be declared on the service contract level in any service implementation that chooses to use it.</span></span>  
  
 <span data-ttu-id="01f1f-138">O serviço de projeto de exemplo se aplica a `DispatchByBodyElementBehaviorAttribute` contrato comportamento para o `IDispatchedByBody` contrato e rótulos as duas operações de serviço `OperationForBodyA()` e `OperationForBodyB()` com um `DispatchBodyElementAttribute` comportamento da operação.</span><span class="sxs-lookup"><span data-stu-id="01f1f-138">The sample project service applies the `DispatchByBodyElementBehaviorAttribute` contract behavior to the `IDispatchedByBody` service contract and labels each of the two operations `OperationForBodyA()` and `OperationForBodyB()` with a `DispatchBodyElementAttribute` operation behavior.</span></span> <span data-ttu-id="01f1f-139">Quando um host de serviço para um serviço que implementa este contrato é aberto, esses metadados é captados pelo construtor de dispatcher conforme descrito anteriormente.</span><span class="sxs-lookup"><span data-stu-id="01f1f-139">When a service host for a service that implements this contract is opened, this metadata is picked up by the dispatcher builder as previously described.</span></span>  
  
 <span data-ttu-id="01f1f-140">Como o seletor de operação despacha exclusivamente com base no elemento de corpo de mensagem e ignora a "ação", é necessário informar o tempo de execução para não verificar o cabeçalho "Ação" nas respostas retornadas atribuindo o caractere curinga "*" para o `ReplyAction` propriedade <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="01f1f-140">Because the operation selector dispatches solely based on the message body element and ignores the "Action", it is required to tell the runtime not to check the "Action" header on the returned replies by assigning the wildcard "*" to the `ReplyAction` property of <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="01f1f-141">Além disso, é necessário ter uma operação de padrão que tem a propriedade "Ação" definida como o caractere curinga "\*".</span><span class="sxs-lookup"><span data-stu-id="01f1f-141">Furthermore, it is required to have a default operation that has the "Action" property set to the wildcard "\*".</span></span> <span data-ttu-id="01f1f-142">A operação padrão recebe todas as mensagens que não podem ser distribuídas e não tem um `DispatchBodyElementAttribute`:</span><span class="sxs-lookup"><span data-stu-id="01f1f-142">The default operation receives all messages which cannot be dispatched and does not have a `DispatchBodyElementAttribute`:</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),  
                            DispatchByBodyElementBehavior]  
public interface IDispatchedByBody  
{  
    [OperationContract(ReplyAction="*"),   
     DispatchBodyElement("bodyA","http://tempuri.org")]  
    Message OperationForBodyA(Message msg);  
    [OperationContract(ReplyAction = "*"),   
     DispatchBodyElement("bodyB", "http://tempuri.org")]  
    Message OperationForBodyB(Message msg);  
    [OperationContract(Action="*", ReplyAction="*")]  
    Message DefaultOperation(Message msg);  
}  
```  
  
 <span data-ttu-id="01f1f-143">A implementação do serviço de exemplo é simples.</span><span class="sxs-lookup"><span data-stu-id="01f1f-143">The sample service implementation is straightforward.</span></span> <span data-ttu-id="01f1f-144">Cada método envolve a mensagem recebida em uma mensagem de resposta e exibe-lo de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="01f1f-144">Every method wraps the received message into a reply message and echoes it back to the client.</span></span>  
  
## <a name="running-and-building-the-sample"></a><span data-ttu-id="01f1f-145">Executando e compilar o exemplo</span><span class="sxs-lookup"><span data-stu-id="01f1f-145">Running and Building the Sample</span></span>  
 <span data-ttu-id="01f1f-146">Quando você executar o exemplo, o conteúdo do corpo das respostas de operação são exibidos na janela do console do cliente semelhante à seguinte saída (formatada).</span><span class="sxs-lookup"><span data-stu-id="01f1f-146">When you run the sample, the body content of the operation responses are displayed in the client console window similar to the following (formatted) output.</span></span>  
  
 <span data-ttu-id="01f1f-147">O cliente envia três mensagens para o serviço cujo conteúdo de elemento é chamado de corpo `bodyA`, `bodyB`, e `bodyX`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="01f1f-147">The client sends three messages to the service whose body content element is named `bodyA`, `bodyB`, and `bodyX`, respectively.</span></span> <span data-ttu-id="01f1f-148">Como podem ser adiadas a descrição anterior e o contrato de serviço mostrado, a mensagem de entrada com o `bodyA` elemento é enviado para o `OperationForBodyA()` método.</span><span class="sxs-lookup"><span data-stu-id="01f1f-148">As can be deferred from the previous description and the service contract shown, the incoming message with the `bodyA` element is dispatched to the `OperationForBodyA()` method.</span></span> <span data-ttu-id="01f1f-149">Porque não há nenhum destino de expedição explícita para a mensagem com o `bodyX` elemento body, a mensagem é enviada para o `DefaultOperation()`.</span><span class="sxs-lookup"><span data-stu-id="01f1f-149">Because there is no explicit dispatch target for the message with the `bodyX` body element, the message is dispatched to the `DefaultOperation()`.</span></span> <span data-ttu-id="01f1f-150">Cada uma das operações de serviço encapsula o corpo da mensagem recebida em um elemento específico para o método e retorna, que é feito para correlacionar a entrada e saída mensagens claramente para este exemplo:</span><span class="sxs-lookup"><span data-stu-id="01f1f-150">Each of the service operations wraps the received message body into an element specific to the method and returns it, which is done to correlate input and output messages clearly for this sample:</span></span>  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyA xmlns="http://tempuri.org">  
   <q:bodyA xmlns:q="http://tempuri.org">test</q:bodyA>  
</replyBodyA>  
<?xml version="1.0" encoding="IBM437"?>  
<replyBodyB xmlns="http://tempuri.org">  
  <q:bodyB xmlns:q="http://tempuri.org">test</q:bodyB>  
</replyBodyB>  
<?xml version="1.0" encoding="IBM437"?>  
<replyDefault xmlns="http://tempuri.org">  
   <q:bodyX xmlns:q="http://tempuri.org">test</q:bodyX>  
</replyDefault>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="01f1f-151">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="01f1f-151">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="01f1f-152">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="01f1f-152">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="01f1f-153">Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="01f1f-153">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="01f1f-154">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="01f1f-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="01f1f-155">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="01f1f-155">The samples may already be installed on your machine.</span></span> <span data-ttu-id="01f1f-156">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="01f1f-156">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="01f1f-157">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="01f1f-157">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="01f1f-158">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="01f1f-158">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\AdvancedDispatchByBody`  
  
## <a name="see-also"></a><span data-ttu-id="01f1f-159">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01f1f-159">See Also</span></span>