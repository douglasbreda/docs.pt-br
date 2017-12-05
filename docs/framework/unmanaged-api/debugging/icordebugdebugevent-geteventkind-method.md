---
title: "Método ICorDebugDebugEvent::GetEventKind"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: c37aaceb-c948-46bd-a943-08be4cbb76f4
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf3296eafb3e3ff933092240f8f353b2b69a89c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugeventgeteventkind-method"></a><span data-ttu-id="1602d-102">Método ICorDebugDebugEvent::GetEventKind</span><span class="sxs-lookup"><span data-stu-id="1602d-102">ICorDebugDebugEvent::GetEventKind Method</span></span>
<span data-ttu-id="1602d-103">Indica o tipo de evento que este objeto `ICorDebugDebugEvent` representa.</span><span class="sxs-lookup"><span data-stu-id="1602d-103">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1602d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1602d-104">Syntax</span></span>  
  
```  
HRESULT GetEventKind(  
    [out]CorDebugDebugEventKind *pDebugEventKind  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1602d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1602d-105">Parameters</span></span>  
 <span data-ttu-id="1602d-106">pDebugEventKind</span><span class="sxs-lookup"><span data-stu-id="1602d-106">pDebugEventKind</span></span>  
 <span data-ttu-id="1602d-107">Um ponteiro para um [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) membro de enumeração que indica o tipo de evento.</span><span class="sxs-lookup"><span data-stu-id="1602d-107">A pointer to a [CorDebugDebugEventKind](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) enumeration member that indicates the type of event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1602d-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="1602d-108">Remarks</span></span>  
 <span data-ttu-id="1602d-109">Com base no valor de `pDebugEventKind`, você pode chamar `QueryInterface` para obter uma interface de evento de depuração mais precisa com dados adicionais.</span><span class="sxs-lookup"><span data-stu-id="1602d-109">Based on the value of `pDebugEventKind`, you can call `QueryInterface` to get a more precise debug event interface that has additional data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1602d-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1602d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1602d-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1602d-111">Requirements</span></span>  
 <span data-ttu-id="1602d-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1602d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1602d-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1602d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1602d-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1602d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1602d-115">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1602d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1602d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1602d-116">See Also</span></span>  
 [<span data-ttu-id="1602d-117">Interface ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="1602d-117">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="1602d-118">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="1602d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)