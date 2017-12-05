---
title: "Enumeração COR_PRF_GC_GENERATION"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_GC_GENERATION
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_GC_GENERATION
helpviewer_keywords: COR_GC_GENERATION_FLAGS enumeration [.NET Framework profiling]
ms.assetid: d6ece160-26ad-4d39-abd7-05acd6f78c48
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a296dd333579f9d0e734b7c00a8adb648605295d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corprfgcgeneration-enumeration"></a><span data-ttu-id="dba12-102">Enumeração COR_PRF_GC_GENERATION</span><span class="sxs-lookup"><span data-stu-id="dba12-102">COR_PRF_GC_GENERATION Enumeration</span></span>
<span data-ttu-id="dba12-103">Identifica uma geração de coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="dba12-103">Identifies a garbage-collection generation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dba12-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dba12-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_GEN_0 = 0,  
    COR_PRF_GC_GEN_1 = 1,  
    COR_PRF_GC_GEN_2 = 2,  
    COR_PRF_GC_LARGE_OBJECT_HEAP = 3  
} COR_PRF_GC_GENERATION;  
```  
  
## <a name="members"></a><span data-ttu-id="dba12-105">Membros</span><span class="sxs-lookup"><span data-stu-id="dba12-105">Members</span></span>  
  
|<span data-ttu-id="dba12-106">Membro</span><span class="sxs-lookup"><span data-stu-id="dba12-106">Member</span></span>|<span data-ttu-id="dba12-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dba12-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_GEN_0`|<span data-ttu-id="dba12-108">O objeto é armazenado como geração 0.</span><span class="sxs-lookup"><span data-stu-id="dba12-108">The object is stored as generation 0.</span></span>|  
|`COR_PRF_GC_GEN_1`|<span data-ttu-id="dba12-109">O objeto é armazenado como geração 1.</span><span class="sxs-lookup"><span data-stu-id="dba12-109">The object is stored as generation 1.</span></span>|  
|`COR_PRF_GC_GEN_2`|<span data-ttu-id="dba12-110">O objeto é armazenado como geração 2.</span><span class="sxs-lookup"><span data-stu-id="dba12-110">The object is stored as generation 2.</span></span>|  
|`COR_PRF_GC_LARGE_OBJECT_HEAP`|<span data-ttu-id="dba12-111">O objeto é armazenado no heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="dba12-111">The object is stored in the large-object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dba12-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="dba12-112">Remarks</span></span>  
 <span data-ttu-id="dba12-113">O coletor de lixo melhora o desempenho de gerenciamento de memória por objetos separam em gerações com base na idade.</span><span class="sxs-lookup"><span data-stu-id="dba12-113">The garbage collector improves memory management performance by dividing objects into generations based on age.</span></span> <span data-ttu-id="dba12-114">O coletor de lixo atualmente usa três gerações, numeradas de 0, 1 e 2, além de um segmento de pilha especial que é usado para objetos grandes.</span><span class="sxs-lookup"><span data-stu-id="dba12-114">The garbage collector currently uses three generations, numbered 0, 1, and 2, plus a special heap segment that is used for large objects.</span></span> <span data-ttu-id="dba12-115">Objetos cujo tamanho é maior que um valor específico são armazenados no heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="dba12-115">Objects whose size is larger than a particular value are stored in the large-object heap.</span></span> <span data-ttu-id="dba12-116">Outros objetos alocados começam pertencentes a geração 0.</span><span class="sxs-lookup"><span data-stu-id="dba12-116">Other allocated objects start out belonging to generation 0.</span></span> <span data-ttu-id="dba12-117">Todos os objetos que existem após a coleta de lixo na geração 0 são promovidos para a geração 1.</span><span class="sxs-lookup"><span data-stu-id="dba12-117">All objects that exist after garbage collection occurs in generation 0 are promoted to generation 1.</span></span> <span data-ttu-id="dba12-118">Movem objetos existentes após a coleta de lixo na geração 1 na geração 2.</span><span class="sxs-lookup"><span data-stu-id="dba12-118">Objects that exist after garbage collection occurs in generation 1 move into generation 2.</span></span>  
  
 <span data-ttu-id="dba12-119">O uso de gerações significa que o coletor de lixo precisa trabalhar com apenas um subconjunto dos objetos alocados a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="dba12-119">The use of generations means that the garbage collector has to work with only a subset of the allocated objects at any one time.</span></span>  
  
 <span data-ttu-id="dba12-120">O `COR_PRF_GC_GENERATION` enumeração é usada pelo [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="dba12-120">The `COR_PRF_GC_GENERATION` enumeration is used by the [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dba12-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dba12-121">Requirements</span></span>  
 <span data-ttu-id="dba12-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dba12-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dba12-123">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dba12-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dba12-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dba12-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dba12-125">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dba12-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba12-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dba12-126">See Also</span></span>  
 [<span data-ttu-id="dba12-127">Enumerações de criação de perfil</span><span class="sxs-lookup"><span data-stu-id="dba12-127">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)