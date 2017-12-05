---
title: Estrutura StackTrace_SimpleContext
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StackTrace_SimpleContext
api_location: diasymreader.dll
api_type: COM
f1_keywords: SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 87ce3d50d6da6a7c23b13fa10123033efbb6c52c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="stacktracesimplecontext-structure"></a><span data-ttu-id="00628-102">Estrutura StackTrace_SimpleContext</span><span class="sxs-lookup"><span data-stu-id="00628-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="00628-103">Fornece um contexto simples que pode ser usado em lugar de uma estrutura `CONTEXT` completa.</span><span class="sxs-lookup"><span data-stu-id="00628-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00628-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00628-104">Syntax</span></span>  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="00628-105">Membros</span><span class="sxs-lookup"><span data-stu-id="00628-105">Members</span></span>  
  
|<span data-ttu-id="00628-106">Membro</span><span class="sxs-lookup"><span data-stu-id="00628-106">Member</span></span>|<span data-ttu-id="00628-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="00628-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="00628-108">O ponteiro de pilha ou o ponteiro de pilha enter (ESP) em x86 plataformas.</span><span class="sxs-lookup"><span data-stu-id="00628-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="00628-109">O deslocamento de quadro ou registre EBP x86 plataformas.</span><span class="sxs-lookup"><span data-stu-id="00628-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="00628-110">O ponteiro de instrução ou o ponteiro de instrução enter (EIP) em x86 plataformas.</span><span class="sxs-lookup"><span data-stu-id="00628-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="00628-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="00628-111">Remarks</span></span>  
 <span data-ttu-id="00628-112">Como as funções de rastreamento de pilha normalmente precisam retornar apenas o endereço, o deslocamento de quadro e endereço de pilha, opcionalmente, você pode usar o `SimpleContext` estrutura em vez de um grande `CONTEXT` estrutura.</span><span class="sxs-lookup"><span data-stu-id="00628-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00628-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="00628-113">Requirements</span></span>  
 <span data-ttu-id="00628-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00628-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00628-115">**Cabeçalho:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="00628-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="00628-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00628-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00628-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="00628-117">See Also</span></span>  
 [<span data-ttu-id="00628-118">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="00628-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="00628-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="00628-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)