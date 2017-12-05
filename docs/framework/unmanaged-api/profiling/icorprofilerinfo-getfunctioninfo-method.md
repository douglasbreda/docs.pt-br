---
title: "Método ICorProfilerInfo::GetFunctionInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetFunctionInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 859887d25e33b4780920ed688684c22031eac16c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="f9ac7-102">Método ICorProfilerInfo::GetFunctionInfo</span><span class="sxs-lookup"><span data-stu-id="f9ac7-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="f9ac7-103">Obtém a classe pai e os metadados de token para a função especificada.</span><span class="sxs-lookup"><span data-stu-id="f9ac7-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9ac7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9ac7-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f9ac7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9ac7-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f9ac7-106">[in] A ID da função para a qual obter a classe pai e os metadados de token.</span><span class="sxs-lookup"><span data-stu-id="f9ac7-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="f9ac7-107">[out] Um ponteiro para a classe pai da função.</span><span class="sxs-lookup"><span data-stu-id="f9ac7-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="f9ac7-108">[out] Um ponteiro para o módulo no qual a classe do pai da função é definido.</span><span class="sxs-lookup"><span data-stu-id="f9ac7-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="f9ac7-109">[out] Um ponteiro para o token de metadados para a função.</span><span class="sxs-lookup"><span data-stu-id="f9ac7-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9ac7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9ac7-110">Remarks</span></span>  
 <span data-ttu-id="f9ac7-111">O criador de perfil código pode chamar [Getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) para obter uma interface de metadados para um determinado módulo.</span><span class="sxs-lookup"><span data-stu-id="f9ac7-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="f9ac7-112">O token de metadados que é retornado para o local referenciado pelo `pToken` , em seguida, pode ser usado para acessar os metadados para a função.</span><span class="sxs-lookup"><span data-stu-id="f9ac7-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="f9ac7-113">O `ClassID` de uma função em uma classe genérica pode não ser obtido sem mais informações contextuais sobre o uso da função.</span><span class="sxs-lookup"><span data-stu-id="f9ac7-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="f9ac7-114">Nesse caso, `pClassId` será 0.</span><span class="sxs-lookup"><span data-stu-id="f9ac7-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="f9ac7-115">Criador de perfil código deve usar [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) com um valor COR_PRF_FRAME_INFO para fornecer mais contexto.</span><span class="sxs-lookup"><span data-stu-id="f9ac7-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9ac7-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9ac7-116">Requirements</span></span>  
 <span data-ttu-id="f9ac7-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9ac7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9ac7-118">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f9ac7-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f9ac7-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9ac7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9ac7-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9ac7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9ac7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9ac7-121">See Also</span></span>  
 [<span data-ttu-id="f9ac7-122">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f9ac7-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)