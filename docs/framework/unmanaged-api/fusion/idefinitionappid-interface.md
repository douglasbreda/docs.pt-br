---
title: Interface IDefinitionAppId
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionAppId
helpviewer_keywords: IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 382c82ff773d0ab1c046fc131fa87a4f74d19ea6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="idefinitionappid-interface"></a><span data-ttu-id="a559e-102">Interface IDefinitionAppId</span><span class="sxs-lookup"><span data-stu-id="a559e-102">IDefinitionAppId Interface</span></span>
<span data-ttu-id="a559e-103">Representa um identificador exclusivo para o código que define o aplicativo no escopo atual.</span><span class="sxs-lookup"><span data-stu-id="a559e-103">Represents a unique identifier for the code that defines the application in the current scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a559e-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="a559e-104">Methods</span></span>  
  
|<span data-ttu-id="a559e-105">Método</span><span class="sxs-lookup"><span data-stu-id="a559e-105">Method</span></span>|<span data-ttu-id="a559e-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="a559e-106">Description</span></span>|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|<span data-ttu-id="a559e-107">Obtém uma cadeia de caracteres formatada que representa o código neste `IDefinitionAppId` objeto.</span><span class="sxs-lookup"><span data-stu-id="a559e-107">Gets a formatted string that represents the code in this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_Codebase`|<span data-ttu-id="a559e-108">Define o código deste `IDefinitionAppId` objeto especificado formatado valor de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a559e-108">Sets the code of this `IDefinitionAppId` object to the specified formatted string value.</span></span>|  
|`IDefinitionAppId::EnumAppPath`|<span data-ttu-id="a559e-109">Obtém um ponteiro de interface para um [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) objeto que contém os assemblies no caminho do aplicativo atual.</span><span class="sxs-lookup"><span data-stu-id="a559e-109">Gets an interface pointer to an [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) object that contains the assemblies in the current application path.</span></span>|  
|`IDefinitionAppId::SetAppPath`|<span data-ttu-id="a559e-110">Define o caminho do aplicativo para o assembly no escopo atual com o valor referenciado por especificado [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="a559e-110">Sets the application path for the assembly in the current scope to the value referenced by the specified [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) object.</span></span>|  
|`IDefinitionAppId::get_SubscriptionId`|<span data-ttu-id="a559e-111">Obtém um ponteiro para uma representação de cadeia de caracteres do identificador de token para uma assinatura `IDefinitionAppId` objeto.</span><span class="sxs-lookup"><span data-stu-id="a559e-111">Gets a pointer to a string representation of the token identifier for a subscription to this `IDefinitionAppId` object.</span></span>|  
|`IDefinitionAppId::put_SubscriptionId`|<span data-ttu-id="a559e-112">Define o identificador para uma assinatura de token para este `IDefinitionAppId` objeto para o valor de cadeia de caracteres especificada.</span><span class="sxs-lookup"><span data-stu-id="a559e-112">Sets the token identifier for a subscription to this `IDefinitionAppId` object to the specified string value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a559e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a559e-113">Requirements</span></span>  
 <span data-ttu-id="a559e-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a559e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a559e-115">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="a559e-115">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a559e-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a559e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a559e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a559e-117">See Also</span></span>  
 [<span data-ttu-id="a559e-118">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="a559e-118">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)