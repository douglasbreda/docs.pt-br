---
title: "&lt;variável&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 46cc8cbc-10ec-4625-8813-3f5cd6c6afde
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ad2a4d3768c26755a9437826c70585a43f967d09
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltvariablegt"></a><span data-ttu-id="d9422-102">&lt;variável&gt;</span><span class="sxs-lookup"><span data-stu-id="d9422-102">&lt;variable&gt;</span></span>
<span data-ttu-id="d9422-103">Representa uma coleção de variáveis associadas a essa consulta de atividade.</span><span class="sxs-lookup"><span data-stu-id="d9422-103">Represents a collection of variables associated with this activity query.</span></span>  
  
 <span data-ttu-id="d9422-104">Para obter mais informações sobre consultas de perfil de controle, consulte [perfis controle](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span><span class="sxs-lookup"><span data-stu-id="d9422-104">For more information on tracking profile queries, see [Tracking Profiles](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="d9422-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d9422-105">\<system.serviceModel></span></span>  
<span data-ttu-id="d9422-106">\<controle ></span><span class="sxs-lookup"><span data-stu-id="d9422-106">\<tracking></span></span>  
<span data-ttu-id="d9422-107">\<perfis ></span><span class="sxs-lookup"><span data-stu-id="d9422-107">\<profiles></span></span>  
<span data-ttu-id="d9422-108">\<trackingProfile ></span><span class="sxs-lookup"><span data-stu-id="d9422-108">\<trackingProfile></span></span>  
<span data-ttu-id="d9422-109">\<fluxo de trabalho ></span><span class="sxs-lookup"><span data-stu-id="d9422-109">\<workflow></span></span>  
<span data-ttu-id="d9422-110">\<activityStateQueries ></span><span class="sxs-lookup"><span data-stu-id="d9422-110">\<activityStateQueries></span></span>  
<span data-ttu-id="d9422-111">\<activityStateQuery ></span><span class="sxs-lookup"><span data-stu-id="d9422-111">\<activityStateQuery></span></span>  
<span data-ttu-id="d9422-112">\<variáveis ></span><span class="sxs-lookup"><span data-stu-id="d9422-112">\<variables></span></span>  
<span data-ttu-id="d9422-113">\<variável ></span><span class="sxs-lookup"><span data-stu-id="d9422-113">\<variable></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9422-114">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9422-114">Syntax</span></span>  
  
```xml  
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <variables>
          <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9422-115">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d9422-115">Attributes and Elements</span></span>  
 <span data-ttu-id="d9422-116">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d9422-116">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9422-117">Atributos</span><span class="sxs-lookup"><span data-stu-id="d9422-117">Attributes</span></span>  
  
|<span data-ttu-id="d9422-118">Atributo</span><span class="sxs-lookup"><span data-stu-id="d9422-118">Attribute</span></span>|<span data-ttu-id="d9422-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9422-119">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d9422-120">name</span><span class="sxs-lookup"><span data-stu-id="d9422-120">name</span></span>|<span data-ttu-id="d9422-121">Uma cadeia de caracteres que especifica o nome da variável.</span><span class="sxs-lookup"><span data-stu-id="d9422-121">A string that specifies the name of the variable.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d9422-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d9422-122">Child Elements</span></span>  
 <span data-ttu-id="d9422-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d9422-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d9422-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d9422-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d9422-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9422-125">Element</span></span>|<span data-ttu-id="d9422-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9422-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9422-127">\<variável ></span><span class="sxs-lookup"><span data-stu-id="d9422-127">\<variable></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/variable.md)|<span data-ttu-id="d9422-128">Uma variável associada a uma consulta de estado de atividade.</span><span class="sxs-lookup"><span data-stu-id="d9422-128">A variable associated with an activity state query.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9422-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9422-129">Remarks</span></span>  
 <span data-ttu-id="d9422-130">Um recurso exclusivo de um ActivityStateQuery é a capacidade de extrair dados para controlar a execução de um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d9422-130">One unique feature of an ActivityStateQuery is the ability to extract data when tracking the execution of a workflow.</span></span> <span data-ttu-id="d9422-131">Isso fornece contexto adicional ao acessar o rastreamento registra pós execução.</span><span class="sxs-lookup"><span data-stu-id="d9422-131">This provides additional context when accessing the tracking records post execution.</span></span> <span data-ttu-id="d9422-132">Você pode usar o [ \<argumentos >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) e [ \<estados >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elementos para extrair qualquer variável ou argumento de qualquer atividade em um fluxo de trabalho. O exemplo a seguir mostra uma consulta de estado de atividade que extrai os argumentos e variáveis quando a atividade `Closed` registro de rastreamento é emitido.</span><span class="sxs-lookup"><span data-stu-id="d9422-132">You can use the [\<arguments>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/arguments.md), [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) and [\<states>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/states.md) elements to extract any variable or argument from any activity in a workflow.The following example shows an activity state query that extracts variables and arguments when the activity’s `Closed` tracking record is emitted.</span></span> <span data-ttu-id="d9422-133">Variáveis e argumentos pode ser extraídos apenas com um ActivityStateRecord e, portanto, se inscreveu em um controle de perfil usando [ \<activityStateQuery >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span><span class="sxs-lookup"><span data-stu-id="d9422-133">Variables and arguments can be extracted only with an ActivityStateRecord and thus are subscribed to within a tracking profile using [\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d9422-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9422-134">See Also</span></span>  
 <span data-ttu-id="d9422-135"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d9422-135"><xref:System.ServiceModel.Activities.Tracking.Configuration.VariableElement?displayProperty=nameWithType></span></span>       
 <span data-ttu-id="d9422-136"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d9422-136"><xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType></span></span>       
 [<span data-ttu-id="d9422-137">Acompanhamento e rastreamento de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d9422-137">Workflow Tracking and Tracing</span></span>](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [<span data-ttu-id="d9422-138">Acompanhando perfis</span><span class="sxs-lookup"><span data-stu-id="d9422-138">Tracking Profiles</span></span>](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)