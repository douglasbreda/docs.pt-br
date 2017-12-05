---
title: "Formatação HTTP Web do WCF"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 43732c6c2effd38b8bfdb49c1a5fbf8275eb15e3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="3fcf0-102">Formatação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="3fcf0-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="3fcf0-103">O modelo de programação WCF Web HTTP permite que você determinar dinamicamente o melhor formato para uma operação de serviço retornar a resposta em.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="3fcf0-104">Há suporte para dois métodos para determinar um formato apropriado: automática e explícitas.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="3fcf0-105">Formatação automática</span><span class="sxs-lookup"><span data-stu-id="3fcf0-105">Automatic formatting</span></span>  
 <span data-ttu-id="3fcf0-106">Quando habilitada, formatação automática escolhe o melhor formato no qual retornar a resposta.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="3fcf0-107">Determina o melhor formato verificando o seguinte, em ordem:</span><span class="sxs-lookup"><span data-stu-id="3fcf0-107">It determines the best format by checking the following, in order:</span></span>  
  
1.  <span data-ttu-id="3fcf0-108">Os tipos de mídia no cabeçalho de aceitação da mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-108">The media types in the request message’s Accept header.</span></span>  
  
2.  <span data-ttu-id="3fcf0-109">O tipo de conteúdo da mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-109">The content-type of the request message.</span></span>  
  
3.  <span data-ttu-id="3fcf0-110">O formato padrão definindo na operação.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-110">The default format setting in the operation.</span></span>  
  
4.  <span data-ttu-id="3fcf0-111">O formato padrão definindo no WebHttpBehavior.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="3fcf0-112">Se a mensagem de solicitação contiver um cabeçalho Accept de [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] pesquisas de infraestrutura para um tipo que oferece suporte a ele.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-112">If the request message contains an Accept header the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="3fcf0-113">Se o `Accept` cabeçalho Especifica prioridades para seus tipos de mídia, elas são consideradas.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="3fcf0-114">Se nenhum formato adequado foi encontrado no `Accept` cabeçalho, o tipo de conteúdo da mensagem de solicitação é usado.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="3fcf0-115">Se nenhum tipo de conteúdo adequado for especificado, a configuração para a operação do formato padrão é usado.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="3fcf0-116">O formato padrão é definido com o `ResponseFormat` parâmetro o <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute> atributos.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="3fcf0-117">Se nenhum formato padrão é especificado na operação, o valor de <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> propriedade é usada.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="3fcf0-118">Formatação automática depende do <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="3fcf0-119">Quando essa propriedade é definida como `true`, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura determina o melhor formato a ser usado.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-119">When this property is set to `true`, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure determines the best format to use.</span></span> <span data-ttu-id="3fcf0-120">Seleção automática de formato com versões anteriores é desabilitada por padrão para compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="3fcf0-121">Seleção automática de formato pode ser habilitada programaticamente ou por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="3fcf0-122">O exemplo a seguir mostra como habilitar a seleção automática de formato no código.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
```csharp
// This code assumes the service name is MyService and the service contract is IMyContract     
Uri baseAddress = new Uri("http://localhost:8000");  
  
WebServiceHost host = new WebServiceHost(typeof(MyService), baseAddress)  
try  
{  
   ServiceEndpoint sep = host.AddServiceEndpoint(typeof(IMyContract), new WebHttpBinding(), "");  
   // Check it see if the WebHttpBehavior already exists  
   WebHttpBehavior whb = sep.Behaviors.Find<WebHttpBehavior>();  
  
   if (whb != null)  
   {  
      whb.AutomaticFormatSelectionEnabled = true;  
   }  
   else  
   {  
      WebHttpBehavior webBehavior = new WebHttpBehavior();  
      webBehavior.AutomaticFormatSelectionEnabled = true;  
      sep.Behaviors.Add(webBehavior);  
   }  
         // Open host to start listening for messages  
   host.Open();        
  
  // ...  
}  
  catch(CommunicationException ex)  
  {  
     Console.WriteLine("An exception occurred: " + ex.Message());  
  }  
```  
  
 <span data-ttu-id="3fcf0-123">Formatação automática também pode ser habilitado por meio da configuração.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="3fcf0-124">Você pode definir o <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> propriedade diretamente no <xref:System.ServiceModel.Description.WebHttpBehavior> ou usando o <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="3fcf0-125">O exemplo a seguir mostra como habilitar a seleção automática de formato no <xref:System.ServiceModel.Description.WebHttpBehavior>.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <endpointBehaviors>  
      <behavior>  
        <webHttp automaticFormatSelectionEnabled="true" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
      <standardEndpoint name="" helpEnabled="true" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="3fcf0-126">O exemplo a seguir mostra como habilitar o uso de seleção automática de formato <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
        <standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true"  />  
      </webHttpEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```  
  
## <a name="explicit-formatting"></a><span data-ttu-id="3fcf0-127">Formatação de explícita</span><span class="sxs-lookup"><span data-stu-id="3fcf0-127">Explicit formatting</span></span>  
 <span data-ttu-id="3fcf0-128">Como o nome implica, na formatação explícita, o desenvolvedor determina o melhor formato a ser usado dentro do código de operação.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="3fcf0-129">Se o melhor formato XML ou JSON define o desenvolvedor <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> como <xref:System.ServiceModel.Web.WebMessageFormat.Xml> ou <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="3fcf0-130">Se o <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> propriedade não está definida explicitamente e, em seguida, o formato padrão da operação é usado.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="3fcf0-131">O exemplo a seguir verifica se o parâmetro de cadeia de caracteres de consulta de formato para um formato a ser usado.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="3fcf0-132">Se tiver sido especificado, define a operação Formatar usando <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
```csharp
public class Service : IService  
{  
    [WebGet]  
     public string EchoWithGet(string s)  
    {  
         // if a format query string parameter has been specified, set the response format to that. If no such  
         // query string parameter exists the Accept header will be used  
        string formatQueryStringValue = WebOperationContext.Current.IncomingRequest.UriTemplateMatch.QueryParameters["format"];  
        if (!string.IsNullOrEmpty(formatQueryStringValue))  
        {  
             if (formatQueryStringValue.Equals("xml", System.StringComparison.OrdinalIgnoreCase))  
             {  
                  WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Xml;  
             }  
             else if (formatQueryStringValue.Equals("json", System.StringComparison.OrdinalIgnoreCase))  
            {  
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Json;  
            }  
            else  
            {  
                 throw new WebFaultException<string>(string.Format("Unsupported format '{0}'", formatQueryStringValue), HttpStatusCode.BadRequest);  
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 <span data-ttu-id="3fcf0-133">Se você precisar oferecer suporte a formatos diferentes de XML ou JSON, defina a operação para ter um tipo de retorno <xref:System.ServiceModel.Channels.Message>.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="3fcf0-134">Dentro do código de operação, determinar o formato apropriado para usar e, em seguida, criar um <xref:System.ServiceModel.Channels.Message> objeto usando um dos seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="3fcf0-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
-   `WebOperationContext.CreateAtom10Response`  
  
-   `WebOperationContext.CreateJsonResponse`  
  
-   `WebOperationContext.CreateStreamResponse`  
  
-   `WebOperationContext.CreateTextResponse`  
  
-   `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="3fcf0-135">Cada um desses métodos usa conteúda e cria uma mensagem com o formato apropriado.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="3fcf0-136">O `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` método pode ser usado para obter uma lista de formatos preferencial pelo cliente em ordem decrescente de preferência.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="3fcf0-137">O exemplo a seguir mostra como usar `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` para determinar o formato a ser usado e, em seguida, usa o método de resposta para criar a mensagem de resposta create apropriada.</span><span class="sxs-lookup"><span data-stu-id="3fcf0-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
```csharp
public class Service : IService  
{  
    public Message EchoListWithGet(string list)  
    {  
        List<string> returnList = new List<string>(list.Split(new char[] { ',' }, StringSplitOptions.RemoveEmptyEntries));  
        IList<ContentType> acceptHeaderElements = WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements();  
        for (int x = 0; x < acceptHeaderElements.Count; x++)  
        {  
            string normalizedMediaType = acceptHeaderElements[x].MediaType.ToLowerInvariant();  
            switch (normalizedMediaType)  
            {  
                case "image/jpeg": return CreateJpegResponse(returnList);  
                case "application/xhtml+xml": return CreateXhtmlResponse(returnList);  
                case "application/atom+xml": return CreateAtom10Response(returnList);  
                case "application/xml": return CreateXmlResponse(returnList);  
                case "application/json": return CreateJsonResponse(returnList);  
          }  
    }  
  
    // Default response format is XML  
    return CreateXmlResponse(returnList);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3fcf0-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fcf0-138">See also</span></span>  
 <xref:System.UriTemplate>  
 <xref:System.UriTemplateMatch>  
 [<span data-ttu-id="3fcf0-139">Modelo de programação WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="3fcf0-139">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="3fcf0-140">UriTemplate e UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="3fcf0-140">UriTemplate and UriTemplateTable</span></span>](../../../../docs/framework/wcf/feature-details/uritemplate-and-uritemplatetable.md)  
 [<span data-ttu-id="3fcf0-141">Visão geral do modelo de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="3fcf0-141">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [<span data-ttu-id="3fcf0-142">Modelo de objeto de programação HTTP Web do WCF</span><span class="sxs-lookup"><span data-stu-id="3fcf0-142">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)