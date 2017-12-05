---
title: "Método SetAssemblyFile"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.SetAssemblyFile
api_location: alink.dll
api_type: COM
f1_keywords: SetAssemblyFile
helpviewer_keywords: SetAssemblyFile method
ms.assetid: 3a912787-f139-43ca-a841-8bbda3107ecf
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d83062db41b5fa1485555de40be0a39a65e0459a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="setassemblyfile-method"></a><span data-ttu-id="29205-102">Método SetAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="29205-102">SetAssemblyFile Method</span></span>
<span data-ttu-id="29205-103">Atribui o nome do assembly a ser criado.</span><span class="sxs-lookup"><span data-stu-id="29205-103">Assigns the name of the assembly to be built.</span></span> <span data-ttu-id="29205-104">Não para uso durante a produção de módulos não associados.</span><span class="sxs-lookup"><span data-stu-id="29205-104">Not for use when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29205-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29205-105">Syntax</span></span>  
  
```  
HRESULT SetAssemblyFile(  
    LPCWSTR pszFilename,  
    IMetaDataEmit* pEmitter,  
    AssemblyFlags afFlags,  
    mdAssembly* pAssemblyID  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29205-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29205-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="29205-107">Nome totalmente qualificado do arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="29205-107">Fully qualified name of the manifest file.</span></span>  
  
 `pEmitter`  
 <span data-ttu-id="29205-108">Ponteiro para [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="29205-108">Pointer to [IMetaDataEmit Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface.</span></span>  
  
 `afFlags`  
 <span data-ttu-id="29205-109">Sinalizadores conforme definido em [enumeração AssemblyFlags](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="29205-109">Flags as defined in [AssemblyFlags Enumeration](../../../../docs/framework/unmanaged-api/metadata/assemblyflags-enumeration.md).</span></span>  
  
 `pAssemblyID`  
 <span data-ttu-id="29205-110">Ponteiro para a ID do assembly resultante.</span><span class="sxs-lookup"><span data-stu-id="29205-110">Pointer to ID of resulting assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29205-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="29205-111">Return Value</span></span>  
 <span data-ttu-id="29205-112">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="29205-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29205-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29205-113">Requirements</span></span>  
 <span data-ttu-id="29205-114">Requer alink.h.</span><span class="sxs-lookup"><span data-stu-id="29205-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29205-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29205-115">See Also</span></span>  
 [<span data-ttu-id="29205-116">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="29205-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="29205-117">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="29205-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="29205-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="29205-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)