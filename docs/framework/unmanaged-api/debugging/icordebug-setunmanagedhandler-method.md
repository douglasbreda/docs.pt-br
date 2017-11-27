---
title: "Método ICorDebug::SetUnmanagedHandler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.SetUnmanagedHandler
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::SetUnmanagerHandler
helpviewer_keywords:
- SetUnmanagedHandler method [.NET Framework debugging]
- ICorDebug::SetUnmanagedHandler method [.NET Framework debugging]
ms.assetid: 6b546be4-f86d-4536-8cfc-1d08e5066eb6
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 658cbaeb10496ccd88e0abb3d2174289a820c2e6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsetunmanagedhandler-method"></a><span data-ttu-id="c35c7-102">Método ICorDebug::SetUnmanagedHandler</span><span class="sxs-lookup"><span data-stu-id="c35c7-102">ICorDebug::SetUnmanagedHandler Method</span></span>
<span data-ttu-id="c35c7-103">Especifica o objeto do manipulador de eventos para eventos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c35c7-103">Specifies the event handler object for unmanaged events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c35c7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c35c7-104">Syntax</span></span>  
  
```  
HRESULT SetUnmanagedHandler (  
    [in] ICorDebugUnmanagedCallback  *pCallback  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c35c7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c35c7-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="c35c7-106">[in] Um ponteiro para um [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) objeto que representa o manipulador de eventos para eventos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="c35c7-106">[in] A pointer to an [ICorDebugUnmanagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md) object that represents the event handler for unmanaged events.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c35c7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c35c7-107">Remarks</span></span>  
 <span data-ttu-id="c35c7-108">O manipulador de eventos de objeto para não gerenciado eventos devem ser definidos após uma chamada para [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) e antes de qualquer chamada para [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) ou [: DebugActiveProcess ](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span><span class="sxs-lookup"><span data-stu-id="c35c7-108">The event handler object for unmanaged events must be set after a call to [ICorDebug::Initialize](../../../../docs/framework/unmanaged-api/debugging/icordebug-initialize-method.md) and before any calls to [ICorDebug::CreateProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md) or [ICorDebug::DebugActiveProcess](../../../../docs/framework/unmanaged-api/debugging/icordebug-debugactiveprocess-method.md).</span></span> <span data-ttu-id="c35c7-109">No entanto, para fins de legado não são necessário definir o objeto do manipulador de eventos para eventos não gerenciados até que o primeiro evento de depuração nativo seja gerado.</span><span class="sxs-lookup"><span data-stu-id="c35c7-109">However, for legacy purposes, you are not required to set the event handler object for unmanaged events until the first native debug event is raised.</span></span> <span data-ttu-id="c35c7-110">Especificamente, se `ICorDebug::CreateProcess` definiu o sinalizador CREATE_SUSPENDED, depuração nativo não podem ser distribuídos eventos até que o thread principal seja retomado.</span><span class="sxs-lookup"><span data-stu-id="c35c7-110">Specifically, if `ICorDebug::CreateProcess` has set the CREATE_SUSPENDED flag, native debug events cannot be dispatched until the main thread is resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c35c7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c35c7-111">Requirements</span></span>  
 <span data-ttu-id="c35c7-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c35c7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c35c7-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c35c7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c35c7-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c35c7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c35c7-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c35c7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c35c7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c35c7-116">See Also</span></span>  
 [<span data-ttu-id="c35c7-117">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="c35c7-117">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)