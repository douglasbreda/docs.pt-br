---
title: "Método IAssemblyCache::CreateAssemblyCacheItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache.CreateAssemblyCacheItem
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 84291d3dea34aba43889baeb1f6e3d501f71b782
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="03918-102">Método IAssemblyCache::CreateAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="03918-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="03918-103">Obtém uma referência a um novo [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="03918-103">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03918-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03918-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03918-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="03918-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="03918-106">[in] Sinalizadores definidos no Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="03918-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="03918-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="03918-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="03918-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="03918-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="03918-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="03918-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="03918-110">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="03918-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="03918-111">`pvReserved`deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="03918-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="03918-112">[out] Retornado `IAssemblyCacheItem` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="03918-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="03918-113">[in, opcional] Uncanonicalized, separados por vírgulas `name=value` pares.</span><span class="sxs-lookup"><span data-stu-id="03918-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03918-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="03918-114">Requirements</span></span>  
 <span data-ttu-id="03918-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03918-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03918-116">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="03918-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="03918-117">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03918-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03918-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="03918-118">See Also</span></span>  
 [<span data-ttu-id="03918-119">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="03918-119">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="03918-120">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="03918-120">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)