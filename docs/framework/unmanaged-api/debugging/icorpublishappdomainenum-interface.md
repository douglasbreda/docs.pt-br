---
title: Interface ICorPublishAppDomainEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomainEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomainEnum
helpviewer_keywords: ICorPublishAppDomainEnum interface [.NET Framework debugging]
ms.assetid: bb798c56-042e-475d-a245-b6fac36d0c07
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8359eda5432a9b3818fd58f6adc18570e4c5f154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icorpublishappdomainenum-interface"></a><span data-ttu-id="50255-102">Interface ICorPublishAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="50255-102">ICorPublishAppDomainEnum Interface</span></span>
<span data-ttu-id="50255-103">Uma subclasse do [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface que fornece métodos para atravessar uma coleção de [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objetos que existem atualmente dentro de um processo.</span><span class="sxs-lookup"><span data-stu-id="50255-103">A subclass of the [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) interface that provides methods to traverse a collection of [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md) objects that currently exist within a process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="50255-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="50255-104">Methods</span></span>  
  
|<span data-ttu-id="50255-105">Método</span><span class="sxs-lookup"><span data-stu-id="50255-105">Method</span></span>|<span data-ttu-id="50255-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="50255-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="50255-107">Próximo método</span><span class="sxs-lookup"><span data-stu-id="50255-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-next-method.md)|<span data-ttu-id="50255-108">Obtém o número especificado de `ICorPublishAppDomain` instâncias da coleção, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="50255-108">Gets the specified number of `ICorPublishAppDomain` instances from the collection, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50255-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="50255-109">Remarks</span></span>  
 <span data-ttu-id="50255-110">O `ICorPublishAppDomainEnum` interface implementa os métodos da interface abstrata, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span><span class="sxs-lookup"><span data-stu-id="50255-110">The `ICorPublishAppDomainEnum` interface implements the methods of the abstract interface, [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50255-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="50255-111">Requirements</span></span>  
 <span data-ttu-id="50255-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50255-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50255-113">**Cabeçalho:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="50255-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="50255-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50255-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50255-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50255-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50255-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50255-116">See Also</span></span>  
 [<span data-ttu-id="50255-117">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="50255-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="50255-118">Coclass CorpubPublish</span><span class="sxs-lookup"><span data-stu-id="50255-118">CorpubPublish Coclass</span></span>](../../../../docs/framework/unmanaged-api/debugging/corpubpublish-coclass.md)