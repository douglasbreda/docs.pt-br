---
title: 1034 - CompleteRuntimeWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45620011-8b04-4f87-ab5a-65b24145e17d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63ab145b8a0688a7f7bbf7dbcbe8dfe612eab294
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="1034---completeruntimeworkitem"></a><span data-ttu-id="c4306-102">1034 - CompleteRuntimeWorkItem</span><span class="sxs-lookup"><span data-stu-id="c4306-102">1034 - CompleteRuntimeWorkItem</span></span>
## <a name="properties"></a><span data-ttu-id="c4306-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c4306-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c4306-104">ID</span><span class="sxs-lookup"><span data-stu-id="c4306-104">ID</span></span>|<span data-ttu-id="c4306-105">1034</span><span class="sxs-lookup"><span data-stu-id="c4306-105">1034</span></span>|  
|<span data-ttu-id="c4306-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c4306-106">Keywords</span></span>|<span data-ttu-id="c4306-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="c4306-107">WFRuntime</span></span>|  
|<span data-ttu-id="c4306-108">Nível</span><span class="sxs-lookup"><span data-stu-id="c4306-108">Level</span></span>|<span data-ttu-id="c4306-109">Detalhado</span><span class="sxs-lookup"><span data-stu-id="c4306-109">Verbose</span></span>|  
|<span data-ttu-id="c4306-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c4306-110">Channel</span></span>|<span data-ttu-id="c4306-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração</span><span class="sxs-lookup"><span data-stu-id="c4306-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c4306-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4306-112">Description</span></span>  
 <span data-ttu-id="c4306-113">Indica que um RuntimeWorkItem terminado.</span><span class="sxs-lookup"><span data-stu-id="c4306-113">Indicates a RuntimeWorkItem has completed.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c4306-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c4306-114">Message</span></span>  
 <span data-ttu-id="c4306-115">Um item de trabalho de tempo de execução concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3".</span><span class="sxs-lookup"><span data-stu-id="c4306-115">A runtime work item has completed for Activity '%1', DisplayName: '%2', InstanceId: '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c4306-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c4306-116">Details</span></span>  
  
|<span data-ttu-id="c4306-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="c4306-117">Data Item Name</span></span>|<span data-ttu-id="c4306-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="c4306-118">Data Item Type</span></span>|<span data-ttu-id="c4306-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c4306-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c4306-120">Atividade</span><span class="sxs-lookup"><span data-stu-id="c4306-120">Activity</span></span>|<span data-ttu-id="c4306-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="c4306-121">xs:string</span></span>|<span data-ttu-id="c4306-122">O nome do tipo de atividade.</span><span class="sxs-lookup"><span data-stu-id="c4306-122">The type name of the activity.</span></span>|  
|<span data-ttu-id="c4306-123">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c4306-123">DisplayName</span></span>|<span data-ttu-id="c4306-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="c4306-124">xs:string</span></span>|<span data-ttu-id="c4306-125">O nome para exibição de atividade.</span><span class="sxs-lookup"><span data-stu-id="c4306-125">The display name of the activity.</span></span>|  
|<span data-ttu-id="c4306-126">InstanceId</span><span class="sxs-lookup"><span data-stu-id="c4306-126">InstanceId</span></span>|<span data-ttu-id="c4306-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="c4306-127">xs:string</span></span>|<span data-ttu-id="c4306-128">A identificação de instância de atividade.</span><span class="sxs-lookup"><span data-stu-id="c4306-128">The instance id of the activity.</span></span>|  
|<span data-ttu-id="c4306-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c4306-129">AppDomain</span></span>|<span data-ttu-id="c4306-130">xs:string</span><span class="sxs-lookup"><span data-stu-id="c4306-130">xs:string</span></span>|<span data-ttu-id="c4306-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c4306-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|