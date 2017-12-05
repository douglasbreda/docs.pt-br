---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9e44d161e1229db9145f4ed7e337396bbd98c68
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="binding"></a><span data-ttu-id="22ec5-102">Associação</span><span class="sxs-lookup"><span data-stu-id="22ec5-102">Binding</span></span>
<span data-ttu-id="22ec5-103">WMI de associação</span><span class="sxs-lookup"><span data-stu-id="22ec5-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22ec5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22ec5-104">Syntax</span></span>  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="22ec5-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="22ec5-105">Methods</span></span>  
 <span data-ttu-id="22ec5-106">A classe de associação não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="22ec5-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="22ec5-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="22ec5-107">Properties</span></span>  
 <span data-ttu-id="22ec5-108">A classe de associação tem as seguintes propriedades.</span><span class="sxs-lookup"><span data-stu-id="22ec5-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="22ec5-109">Objetos BindingElements</span><span class="sxs-lookup"><span data-stu-id="22ec5-109">BindingElements</span></span>  
 <span data-ttu-id="22ec5-110">Tipo de dados: matriz BindingElement</span><span class="sxs-lookup"><span data-stu-id="22ec5-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="22ec5-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="22ec5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22ec5-112">A coleção de elementos implementados pela associação de associação.</span><span class="sxs-lookup"><span data-stu-id="22ec5-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="22ec5-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="22ec5-113">CloseTimeout</span></span>  
 <span data-ttu-id="22ec5-114">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="22ec5-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="22ec5-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="22ec5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22ec5-116">O intervalo de tempo fornecido para uma operação de fechamento concluir.</span><span class="sxs-lookup"><span data-stu-id="22ec5-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="22ec5-117">Nome</span><span class="sxs-lookup"><span data-stu-id="22ec5-117">Name</span></span>  
 <span data-ttu-id="22ec5-118">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="22ec5-118">Data type: string</span></span>  
  
 <span data-ttu-id="22ec5-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="22ec5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22ec5-120">O nome da associação.</span><span class="sxs-lookup"><span data-stu-id="22ec5-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="22ec5-121">Namespace</span><span class="sxs-lookup"><span data-stu-id="22ec5-121">Namespace</span></span>  
 <span data-ttu-id="22ec5-122">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="22ec5-122">Data type: string</span></span>  
  
 <span data-ttu-id="22ec5-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="22ec5-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22ec5-124">O namespace XML da associação.</span><span class="sxs-lookup"><span data-stu-id="22ec5-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="22ec5-125">openTimeout</span><span class="sxs-lookup"><span data-stu-id="22ec5-125">OpenTimeout</span></span>  
 <span data-ttu-id="22ec5-126">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="22ec5-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="22ec5-127">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="22ec5-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22ec5-128">O intervalo de tempo fornecido para uma operação de abertura concluir.</span><span class="sxs-lookup"><span data-stu-id="22ec5-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="22ec5-129">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="22ec5-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="22ec5-130">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="22ec5-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="22ec5-131">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="22ec5-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22ec5-132">O intervalo de tempo fornecido para uma operação de recebimento concluir.</span><span class="sxs-lookup"><span data-stu-id="22ec5-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="22ec5-133">Esquema</span><span class="sxs-lookup"><span data-stu-id="22ec5-133">Scheme</span></span>  
 <span data-ttu-id="22ec5-134">Tipo de dados: cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="22ec5-134">Data type: string</span></span>  
  
 <span data-ttu-id="22ec5-135">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="22ec5-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22ec5-136">O esquema de transporte URI usado pelas fábricas de canal e ouvinte construídas pela associação.</span><span class="sxs-lookup"><span data-stu-id="22ec5-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="22ec5-137">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="22ec5-137">SendTimeout</span></span>  
 <span data-ttu-id="22ec5-138">Tipo de dados: datetime</span><span class="sxs-lookup"><span data-stu-id="22ec5-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="22ec5-139">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="22ec5-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="22ec5-140">O intervalo de tempo fornecido para uma operação de envio concluir.</span><span class="sxs-lookup"><span data-stu-id="22ec5-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22ec5-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22ec5-141">Requirements</span></span>  
  
|<span data-ttu-id="22ec5-142">MOF</span><span class="sxs-lookup"><span data-stu-id="22ec5-142">MOF</span></span>|<span data-ttu-id="22ec5-143">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="22ec5-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="22ec5-144">Namespace</span><span class="sxs-lookup"><span data-stu-id="22ec5-144">Namespace</span></span>|<span data-ttu-id="22ec5-145">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="22ec5-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22ec5-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22ec5-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>