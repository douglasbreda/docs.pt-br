---
title: "Enumeração EClrEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrEvent
helpviewer_keywords: EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0585cea00865f4798c57ef5276076c2b0a5ff284
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="a0eed-102">Enumeração EClrEvent</span><span class="sxs-lookup"><span data-stu-id="a0eed-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="a0eed-103">Descreve os eventos de runtime (CLR) de linguagem comum para a qual o host pode registrar retornos de chamada.</span><span class="sxs-lookup"><span data-stu-id="a0eed-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0eed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0eed-104">Syntax</span></span>  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="a0eed-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a0eed-105">Members</span></span>  
  
|<span data-ttu-id="a0eed-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a0eed-106">Member</span></span>|<span data-ttu-id="a0eed-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0eed-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="a0eed-108">Especifica um erro fatal do CLR.</span><span class="sxs-lookup"><span data-stu-id="a0eed-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="a0eed-109">Especifica o descarregamento de uma determinada <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a0eed-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="a0eed-110">Especifica se uma mensagem gerenciados depuração MDA (Assistente) foi gerada.</span><span class="sxs-lookup"><span data-stu-id="a0eed-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="a0eed-111">Especifica que ocorreu um erro de estouro de pilha.</span><span class="sxs-lookup"><span data-stu-id="a0eed-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0eed-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0eed-112">Remarks</span></span>  
 <span data-ttu-id="a0eed-113">O host pode registrar retornos de chamada para qualquer um dos tipos de evento descritos por `EClrEvent` chamando métodos do [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="a0eed-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="a0eed-114">O host obtém um ponteiro para essa interface chamando o [Iclrcontrol](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="a0eed-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="a0eed-115">O `Event_CLRDisabled` e `Event_DomainUnload` eventos podem ser gerados mais de uma vez e de diversos threads para sinalizar um descarregamento ou a desabilitação do CLR.</span><span class="sxs-lookup"><span data-stu-id="a0eed-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="a0eed-116">O `Event_MDAFired` evento dispara a criação de um [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instância que contém os detalhes da mensagem de MDA.</span><span class="sxs-lookup"><span data-stu-id="a0eed-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="a0eed-117">Para obter mais informações sobre MDAs, consulte [diagnosticando erros com assistentes de depuração gerenciada](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="a0eed-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0eed-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0eed-118">Requirements</span></span>  
 <span data-ttu-id="a0eed-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0eed-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0eed-120">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a0eed-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a0eed-121">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a0eed-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0eed-122">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0eed-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0eed-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0eed-123">See Also</span></span>  
 [<span data-ttu-id="a0eed-124">Interface IActionOnCLREvent</span><span class="sxs-lookup"><span data-stu-id="a0eed-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="a0eed-125">Interface ICLRControl</span><span class="sxs-lookup"><span data-stu-id="a0eed-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="a0eed-126">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="a0eed-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)