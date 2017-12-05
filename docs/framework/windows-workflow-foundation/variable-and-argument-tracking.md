---
title: "Rastreamento de variável e argumento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f3d9d30-d899-49aa-b7ce-a8d0d32c4ff0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50bcb67fa4f51318ef7afa69e37d03bb80400539
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="variable-and-argument-tracking"></a><span data-ttu-id="3af23-102">Rastreamento de variável e argumento</span><span class="sxs-lookup"><span data-stu-id="3af23-102">Variable and Argument Tracking</span></span>
<span data-ttu-id="3af23-103">Para controlar a execução de um fluxo de trabalho, geralmente é útil extrair dados.</span><span class="sxs-lookup"><span data-stu-id="3af23-103">When tracking the execution of a workflow, it is often useful to extract data.</span></span> <span data-ttu-id="3af23-104">Isso fornece um contexto extra para acessar uma execução de postagem de registro de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3af23-104">This provides additional context when accessing a tracking record post execution.</span></span> <span data-ttu-id="3af23-105">Em [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], você pode extrair qualquer variável ou argumento visível no escopo de qualquer atividade em um fluxo de trabalho usando o rastreamento.</span><span class="sxs-lookup"><span data-stu-id="3af23-105">In [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)], you can extract any visible variable or argument within the scope of any activity in a workflow using tracking.</span></span> <span data-ttu-id="3af23-106">Controlando os perfis facilitam extrair dados.</span><span class="sxs-lookup"><span data-stu-id="3af23-106">Tracking profiles make it easy to extract data.</span></span>  
  
## <a name="variables-and-arguments"></a><span data-ttu-id="3af23-107">Variáveis e argumentos</span><span class="sxs-lookup"><span data-stu-id="3af23-107">Variables and Arguments</span></span>  
 <span data-ttu-id="3af23-108">Variáveis e os argumentos são extraídos quando uma atividade se emite um ActivityStateRecord.</span><span class="sxs-lookup"><span data-stu-id="3af23-108">Variables and arguments are extracted when an activity emits an ActivityStateRecord.</span></span>  <span data-ttu-id="3af23-109">Uma variável está disponível para a extração somente se está no escopo da atividade.</span><span class="sxs-lookup"><span data-stu-id="3af23-109">A variable is available for extraction only if it is within the scope of the activity.</span></span> <span data-ttu-id="3af23-110">Uma variável para ser extraído dentro de uma atividade é especificado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="3af23-110">A variable to be extracted within an activity is specified in the following manner:</span></span>  
  
-   <span data-ttu-id="3af23-111">Se uma variável é especificado pelo nome de variável, então o rastreamento para a variável dentro da atividade sendo controlada e em atividades pai.</span><span class="sxs-lookup"><span data-stu-id="3af23-111">If a variable is specified by the variable name, then tracking looks for the variable within the current activity being tracked and in parent activities.</span></span> <span data-ttu-id="3af23-112">A variável é procurada no escopo da atividade atual e o escopo pai.</span><span class="sxs-lookup"><span data-stu-id="3af23-112">The variable is searched in current activity scope and in parent scope.</span></span>  
  
-   <span data-ttu-id="3af23-113">Se as variáveis a ser extraído são especificadas usando nome = "*", em seguida, todas as variáveis dentro da atividade atual que está sendo rastreada são extraídas.</span><span class="sxs-lookup"><span data-stu-id="3af23-113">If variables to be extracted are specified by using name="*", then all variables within the current activity being tracked are extracted.</span></span> <span data-ttu-id="3af23-114">Variáveis que estão no escopo mas são definidos em atividades pai não são extraídos nesse caso.</span><span class="sxs-lookup"><span data-stu-id="3af23-114">In this case variables that are in scope but defined in parent activities are not extracted.</span></span>  
  
 <span data-ttu-id="3af23-115">Para extrair argumentos, os argumentos extraídos dependem de estado da atividade.</span><span class="sxs-lookup"><span data-stu-id="3af23-115">When extracting arguments, the arguments extracted depend on the state of the activity.</span></span> <span data-ttu-id="3af23-116">Quando o estado de uma atividade é executado, então somente `InArguments` está disponível para a extração.</span><span class="sxs-lookup"><span data-stu-id="3af23-116">When the state of an activity is Executing, then only the `InArguments` are available for extraction.</span></span> <span data-ttu-id="3af23-117">Para qualquer outro estado da atividade (zipado, criticado, cancelado), todos os argumentos, InArguments e OutArguments, estão disponíveis para a extração.</span><span class="sxs-lookup"><span data-stu-id="3af23-117">For any other activity state (Closed, Faulted, Canceled), all arguments, both InArguments and OutArguments, are available for extraction.</span></span>  
  
 <span data-ttu-id="3af23-118">O exemplo a seguir mostra uma consulta de estado da atividade que extrai variáveis e argumentos quando `Closed` de atividade que controla o registro é emitida.</span><span class="sxs-lookup"><span data-stu-id="3af23-118">The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="3af23-119">Variáveis e os argumentos podem ser extraídos somente com <xref:System.Activities.Tracking.ActivityStateRecord> e são assinados bem em um perfil de rastreamento usando <xref:System.Activities.Tracking.ActivityStateQuery>.</span><span class="sxs-lookup"><span data-stu-id="3af23-119">Variables and arguments can be extracted only with an <xref:System.Activities.Tracking.ActivityStateRecord> and thus are subscribed to within a tracking profile using <xref:System.Activities.Tracking.ActivityStateQuery>.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <variables>  
    <variable name="FromAddress"/>  
  </variables>  
  <arguments>  
    <argument name="Result"/>  
  </arguments>  
</activityStateQuery>  
```  
  
## <a name="protecting-information-stored-within-variables-and-arguments"></a><span data-ttu-id="3af23-120">Informações de proteção armazenada em variáveis e os argumentos</span><span class="sxs-lookup"><span data-stu-id="3af23-120">Protecting Information Stored Within Variables and Arguments</span></span>  
 <span data-ttu-id="3af23-121">Uma variável ou um argumento controlado por padrão são feitas visível no tempo de execução de WF.</span><span class="sxs-lookup"><span data-stu-id="3af23-121">A tracked variable or argument is by default made visible by the WF runtime.</span></span> <span data-ttu-id="3af23-122">Um desenvolvedor de fluxo de trabalho de protegê-lo pode ser acessado colocando as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="3af23-122">A workflow developer can protect it from being accessed by taking the following steps:</span></span>  
  
1.  <span data-ttu-id="3af23-123">Criptografar o valor de uma variável.</span><span class="sxs-lookup"><span data-stu-id="3af23-123">Encrypt the value of a variable.</span></span>  
  
2.  <span data-ttu-id="3af23-124">Controle a criação de um perfil de rastreamento para evitar a extração de uma variável ou um argumento.</span><span class="sxs-lookup"><span data-stu-id="3af23-124">Control the authoring of a tracking profile to prevent the extraction of a variable or argument.</span></span>  
  
3.  <span data-ttu-id="3af23-125">Para participantes personalizados de rastreamento certifique-se de que o código de WF não divulgue informações sigilosas que é armazenada em variáveis ou nos argumentos.</span><span class="sxs-lookup"><span data-stu-id="3af23-125">For custom tracking participants ensure that the WF code does not disclose sensitive information that is stored in variables or arguments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3af23-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3af23-126">See Also</span></span>  
 [<span data-ttu-id="3af23-127">Monitoramento do Windows Server App Fabric</span><span class="sxs-lookup"><span data-stu-id="3af23-127">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="3af23-128">Monitoramento de aplicativos com App Fabric</span><span class="sxs-lookup"><span data-stu-id="3af23-128">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)