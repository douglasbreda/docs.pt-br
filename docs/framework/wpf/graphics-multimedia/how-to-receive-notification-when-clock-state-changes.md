---
title: "Como receber notificação quando o estado de um relógio mudar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f59fddb1add29d52ccba6fc8b8ce84938b53a1c2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a><span data-ttu-id="fff3d-102">Como receber notificação quando o estado de um relógio mudar</span><span class="sxs-lookup"><span data-stu-id="fff3d-102">How to: Receive Notification When a Clock&#39;s State Changes</span></span>
<span data-ttu-id="fff3d-103">Um relógio <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> evento ocorre quando seu <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> torna-se inválida, como quando o relógio inicia ou termina.</span><span class="sxs-lookup"><span data-stu-id="fff3d-103">A clock's <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> event occurs when its <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> becomes invalid, such as when the clock starts or stops.</span></span> <span data-ttu-id="fff3d-104">Você pode registrar este evento com diretamente usando um <xref:System.Windows.Media.Animation.Clock>, ou você pode registrar usando um <xref:System.Windows.Media.Animation.Timeline>.</span><span class="sxs-lookup"><span data-stu-id="fff3d-104">You can register for this event with directly using a <xref:System.Windows.Media.Animation.Clock>, or you can register using a <xref:System.Windows.Media.Animation.Timeline>.</span></span>  
  
 <span data-ttu-id="fff3d-105">No exemplo a seguir, uma <xref:System.Windows.Media.Animation.Storyboard> e dois <xref:System.Windows.Media.Animation.DoubleAnimation> objetos são usados para animar a largura de dois retângulos.</span><span class="sxs-lookup"><span data-stu-id="fff3d-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> and two <xref:System.Windows.Media.Animation.DoubleAnimation> objects are used to animate the width of two rectangles.</span></span> <span data-ttu-id="fff3d-106">O <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> eventos é usado para as alterações de estado do relógio.</span><span class="sxs-lookup"><span data-stu-id="fff3d-106">The <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event is used to listen for clock state changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fff3d-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fff3d-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 <span data-ttu-id="fff3d-108">A ilustração a seguir mostra os diferentes estados em que as animações entram à medida que a linha do tempo pai (*Storyboard*) avança.</span><span class="sxs-lookup"><span data-stu-id="fff3d-108">The following illustration shows the different states the animations enter as the parent timeline (*Storyboard*) progresses.</span></span>  
  
 <span data-ttu-id="fff3d-109">![Estados do relógio para uma Storyboard com duas animações](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span><span class="sxs-lookup"><span data-stu-id="fff3d-109">![Clock states for a Storyboard with two animations](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span></span>  
  
 <span data-ttu-id="fff3d-110">A tabela a seguir mostra os horários em que *Animation1*do <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> evento ser acionado:</span><span class="sxs-lookup"><span data-stu-id="fff3d-110">The following table shows the times at which *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
|<span data-ttu-id="fff3d-111">Tempo (segundos)</span><span class="sxs-lookup"><span data-stu-id="fff3d-111">Time (Seconds)</span></span>|<span data-ttu-id="fff3d-112">1</span><span class="sxs-lookup"><span data-stu-id="fff3d-112">1</span></span>|<span data-ttu-id="fff3d-113">10</span><span class="sxs-lookup"><span data-stu-id="fff3d-113">10</span></span>|<span data-ttu-id="fff3d-114">19</span><span class="sxs-lookup"><span data-stu-id="fff3d-114">19</span></span>|<span data-ttu-id="fff3d-115">21</span><span class="sxs-lookup"><span data-stu-id="fff3d-115">21</span></span>|<span data-ttu-id="fff3d-116">30</span><span class="sxs-lookup"><span data-stu-id="fff3d-116">30</span></span>|<span data-ttu-id="fff3d-117">39</span><span class="sxs-lookup"><span data-stu-id="fff3d-117">39</span></span>|  
|<span data-ttu-id="fff3d-118">Estado</span><span class="sxs-lookup"><span data-stu-id="fff3d-118">State</span></span>|<span data-ttu-id="fff3d-119">Ativo</span><span class="sxs-lookup"><span data-stu-id="fff3d-119">Active</span></span>|<span data-ttu-id="fff3d-120">Ativo</span><span class="sxs-lookup"><span data-stu-id="fff3d-120">Active</span></span>|<span data-ttu-id="fff3d-121">Parado</span><span class="sxs-lookup"><span data-stu-id="fff3d-121">Stopped</span></span>|<span data-ttu-id="fff3d-122">Ativo</span><span class="sxs-lookup"><span data-stu-id="fff3d-122">Active</span></span>|<span data-ttu-id="fff3d-123">Ativo</span><span class="sxs-lookup"><span data-stu-id="fff3d-123">Active</span></span>|<span data-ttu-id="fff3d-124">Parado</span><span class="sxs-lookup"><span data-stu-id="fff3d-124">Stopped</span></span>|  
  
 <span data-ttu-id="fff3d-125">A tabela a seguir mostra os horários em que *Animation2*do <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> evento ser acionado:</span><span class="sxs-lookup"><span data-stu-id="fff3d-125">The following table shows the times at which *Animation2*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="fff3d-126">Tempo (segundos)</span><span class="sxs-lookup"><span data-stu-id="fff3d-126">Time (Seconds)</span></span>|<span data-ttu-id="fff3d-127">1</span><span class="sxs-lookup"><span data-stu-id="fff3d-127">1</span></span>|<span data-ttu-id="fff3d-128">9</span><span class="sxs-lookup"><span data-stu-id="fff3d-128">9</span></span>|<span data-ttu-id="fff3d-129">11</span><span class="sxs-lookup"><span data-stu-id="fff3d-129">11</span></span>|<span data-ttu-id="fff3d-130">19</span><span class="sxs-lookup"><span data-stu-id="fff3d-130">19</span></span>|<span data-ttu-id="fff3d-131">21</span><span class="sxs-lookup"><span data-stu-id="fff3d-131">21</span></span>|<span data-ttu-id="fff3d-132">29</span><span class="sxs-lookup"><span data-stu-id="fff3d-132">29</span></span>|<span data-ttu-id="fff3d-133">31</span><span class="sxs-lookup"><span data-stu-id="fff3d-133">31</span></span>|<span data-ttu-id="fff3d-134">39</span><span class="sxs-lookup"><span data-stu-id="fff3d-134">39</span></span>|  
|<span data-ttu-id="fff3d-135">Estado</span><span class="sxs-lookup"><span data-stu-id="fff3d-135">State</span></span>|<span data-ttu-id="fff3d-136">Ativo</span><span class="sxs-lookup"><span data-stu-id="fff3d-136">Active</span></span>|<span data-ttu-id="fff3d-137">Preenchendo</span><span class="sxs-lookup"><span data-stu-id="fff3d-137">Filling</span></span>|<span data-ttu-id="fff3d-138">Ativo</span><span class="sxs-lookup"><span data-stu-id="fff3d-138">Active</span></span>|<span data-ttu-id="fff3d-139">Parado</span><span class="sxs-lookup"><span data-stu-id="fff3d-139">Stopped</span></span>|<span data-ttu-id="fff3d-140">Ativo</span><span class="sxs-lookup"><span data-stu-id="fff3d-140">Active</span></span>|<span data-ttu-id="fff3d-141">Preenchendo</span><span class="sxs-lookup"><span data-stu-id="fff3d-141">Filling</span></span>|<span data-ttu-id="fff3d-142">Ativo</span><span class="sxs-lookup"><span data-stu-id="fff3d-142">Active</span></span>|<span data-ttu-id="fff3d-143">Parado</span><span class="sxs-lookup"><span data-stu-id="fff3d-143">Stopped</span></span>|  
  
 <span data-ttu-id="fff3d-144">Observe que *Animation1*do <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> evento é acionado em 10 segundos, mesmo que seu estado permanece <xref:System.Windows.Media.Animation.ClockState.Active>.</span><span class="sxs-lookup"><span data-stu-id="fff3d-144">Notice that *Animation1*'s  <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires at 10 seconds, even though its state remains <xref:System.Windows.Media.Animation.ClockState.Active>.</span></span> <span data-ttu-id="fff3d-145">Isso ocorre porque seu estado é alterado em 10 segundos, mas ela alterada de <xref:System.Windows.Media.Animation.ClockState.Active> para <xref:System.Windows.Media.Animation.ClockState.Filling> e, em seguida, de volta para <xref:System.Windows.Media.Animation.ClockState.Active> na mesma escala.</span><span class="sxs-lookup"><span data-stu-id="fff3d-145">That's because its state changed at 10 seconds, but it changed from <xref:System.Windows.Media.Animation.ClockState.Active> to <xref:System.Windows.Media.Animation.ClockState.Filling> and then back to <xref:System.Windows.Media.Animation.ClockState.Active> in the same tick.</span></span>