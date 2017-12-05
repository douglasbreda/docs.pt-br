---
title: "Método EmitManifest"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- EmitManifest
- IALink.EmitManifest
api_location: alink.dll
api_type: COM
f1_keywords: EmitManifest
helpviewer_keywords: EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 03ef815f03a65cbf7e2dc936b21848e206132add
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="emitmanifest-method"></a><span data-ttu-id="50b37-102">Método EmitManifest</span><span class="sxs-lookup"><span data-stu-id="50b37-102">EmitManifest Method</span></span>
<span data-ttu-id="50b37-103">Emite o manifesto final.</span><span class="sxs-lookup"><span data-stu-id="50b37-103">Emits the final manifest.</span></span> <span data-ttu-id="50b37-104">Chame este método depois de importar todos os outros arquivos e definir todas as opções.</span><span class="sxs-lookup"><span data-stu-id="50b37-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="50b37-105">Não chame este método para os módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="50b37-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50b37-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50b37-106">Syntax</span></span>  
  
```  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="50b37-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="50b37-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="50b37-108">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="50b37-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="50b37-109">Recebe o tamanho da reserva no arquivo de assembly, recuperadas do [função StrongNameSignatureSize](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="50b37-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="50b37-110">Opcionalmente, recebe o token de manifesto do assembly.</span><span class="sxs-lookup"><span data-stu-id="50b37-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50b37-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="50b37-111">Return Value</span></span>  
 <span data-ttu-id="50b37-112">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="50b37-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50b37-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="50b37-113">Requirements</span></span>  
 <span data-ttu-id="50b37-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="50b37-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50b37-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50b37-115">See Also</span></span>  
 [<span data-ttu-id="50b37-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="50b37-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="50b37-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="50b37-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="50b37-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="50b37-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)