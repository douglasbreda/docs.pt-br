---
title: Interface ICorProfilerCallback4
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4
helpviewer_keywords: ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 64a26f5dfb0ad9f06bb1b9eb31dcae36f4623c4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4-interface"></a><span data-ttu-id="e9ac9-102">Interface ICorProfilerCallback4</span><span class="sxs-lookup"><span data-stu-id="e9ac9-102">ICorProfilerCallback4 Interface</span></span>
<span data-ttu-id="e9ac9-103">Fornece métodos de retorno de chamada que o common language runtime (CLR) usa para comunicar informações para o criador de perfil.</span><span class="sxs-lookup"><span data-stu-id="e9ac9-103">Provides callback methods that the common language runtime (CLR) uses to communicate information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9ac9-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e9ac9-104">Methods</span></span>  
  
|<span data-ttu-id="e9ac9-105">Método</span><span class="sxs-lookup"><span data-stu-id="e9ac9-105">Method</span></span>|<span data-ttu-id="e9ac9-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9ac9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9ac9-107">Método GetReJITParameters</span><span class="sxs-lookup"><span data-stu-id="e9ac9-107">GetReJITParameters Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|<span data-ttu-id="e9ac9-108">Permite que o criador de perfil de código definir sinalizadores de geração de código alternativo para um novo corpo de método recompilada.</span><span class="sxs-lookup"><span data-stu-id="e9ac9-108">Allows the code profiler to set alternate code generation flags for a new recompiled method body.</span></span>|  
|[<span data-ttu-id="e9ac9-109">Método MovedReferences2</span><span class="sxs-lookup"><span data-stu-id="e9ac9-109">MovedReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|<span data-ttu-id="e9ac9-110">Relata o novo layout dos objetos no heap como resultado de uma coleta de lixo de compactação.</span><span class="sxs-lookup"><span data-stu-id="e9ac9-110">Reports the new layout of objects in the heap as a result of a compacting garbage collection.</span></span>|  
|[<span data-ttu-id="e9ac9-111">Método ReJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="e9ac9-111">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|<span data-ttu-id="e9ac9-112">Notifica o criador de perfil que o compilador just-in-time (JIT) concluiu a recompilação de uma função.</span><span class="sxs-lookup"><span data-stu-id="e9ac9-112">Notifies the profiler that the just-in-time (JIT) compiler has finished the recompilation of a function.</span></span>|  
|[<span data-ttu-id="e9ac9-113">Método ReJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="e9ac9-113">ReJITCompilationStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|<span data-ttu-id="e9ac9-114">Notifica o criador de perfil que o compilador just-in-time (JIT) foi iniciado recompilar uma função.</span><span class="sxs-lookup"><span data-stu-id="e9ac9-114">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>|  
|[<span data-ttu-id="e9ac9-115">Método ReJITError</span><span class="sxs-lookup"><span data-stu-id="e9ac9-115">ReJITError Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|<span data-ttu-id="e9ac9-116">Relata um erro ao processar uma solicitação de recompilação.</span><span class="sxs-lookup"><span data-stu-id="e9ac9-116">Reports an error encountered while processing a recompile request.</span></span>|  
|[<span data-ttu-id="e9ac9-117">Método SurvivingReferences2</span><span class="sxs-lookup"><span data-stu-id="e9ac9-117">SurvivingReferences2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|<span data-ttu-id="e9ac9-118">Relata o layout dos objetos no heap como resultado de uma coleta de lixo não compactar.</span><span class="sxs-lookup"><span data-stu-id="e9ac9-118">Reports the layout of objects in the heap as a result of a non-compacting garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9ac9-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9ac9-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9ac9-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9ac9-120">Requirements</span></span>  
 <span data-ttu-id="e9ac9-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9ac9-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9ac9-122">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9ac9-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9ac9-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9ac9-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9ac9-124">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9ac9-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ac9-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9ac9-125">See Also</span></span>  
 [<span data-ttu-id="e9ac9-126">Interface ICorProfilerCallback2</span><span class="sxs-lookup"><span data-stu-id="e9ac9-126">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="e9ac9-127">Interfaces de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="e9ac9-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="e9ac9-128">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="e9ac9-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)