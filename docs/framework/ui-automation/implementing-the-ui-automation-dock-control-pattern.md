---
title: "Implementando o padrão de controle de encaixe da automação de interface do usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 68c3dcdb1d8f15f312dea40ae59a3b1a4736c484
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a><span data-ttu-id="7c1f7-102">Implementando o padrão de controle de encaixe da automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7c1f7-102">Implementing the UI Automation Dock Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="7c1f7-103">Esta documentação destina-se a desenvolvedores do .NET Framework que querem usar as classes da [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] gerenciadas definidas no namespace <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7c1f7-104">Para obter as informações mais recentes sobre a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], consulte [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746) (API de Automação do Windows: Automação da Interface do Usuário).</span><span class="sxs-lookup"><span data-stu-id="7c1f7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="7c1f7-105">Este tópico apresenta diretrizes e convenções para implementar <xref:System.Windows.Automation.Provider.IDockProvider>, incluindo informações sobre propriedades.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IDockProvider>, including information about properties.</span></span> <span data-ttu-id="7c1f7-106">Links para referências adicionais são listadas no final do tópico.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="7c1f7-107">O <xref:System.Windows.Automation.DockPattern> padrão de controle é usado para expor as propriedades de encaixe de um controle em um contêiner de encaixe.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-107">The <xref:System.Windows.Automation.DockPattern> control pattern is used to expose the dock properties of a control within a docking container.</span></span> <span data-ttu-id="7c1f7-108">Um contêiner de encaixe é um controle que permite organizar os elementos filho horizontal e verticalmente, em relação a cada um dos outros.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-108">A docking container is a control that allows you to arrange child elements horizontally and vertically, relative to each other.</span></span> <span data-ttu-id="7c1f7-109">Para obter exemplos de controles que implementam este padrão de controle, consulte [mapeamento de padrão de controle para clientes de automação de interface do usuário](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="7c1f7-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
 <span data-ttu-id="7c1f7-110">![Contêiner de encaixe com dois filhos encaixados. ] (../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span><span class="sxs-lookup"><span data-stu-id="7c1f7-110">![Docking container with two docked children.](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")</span></span>  
<span data-ttu-id="7c1f7-111">Encaixe o exemplo do Visual Studio onde o "Modo de exibição de classe" janela é DockPosition.Right e janela "Lista de erros" é DockPosition.Bottom</span><span class="sxs-lookup"><span data-stu-id="7c1f7-111">Docking Example from Visual Studio Where "Class View" Window Is DockPosition.Right and "Error List" Window Is DockPosition.Bottom</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="7c1f7-112">Convenções e diretrizes de implementação</span><span class="sxs-lookup"><span data-stu-id="7c1f7-112">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="7c1f7-113">Ao implementar o padrão de controle de encaixe, observe as seguintes diretrizes e convenções:</span><span class="sxs-lookup"><span data-stu-id="7c1f7-113">When implementing the Dock control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="7c1f7-114"><xref:System.Windows.Automation.Provider.IDockProvider>não expõe as propriedades do contêiner de encaixe ou propriedades de controles que estão encaixados adjacente ao controle atual dentro do contêiner de encaixe.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-114"><xref:System.Windows.Automation.Provider.IDockProvider> does not expose any properties of the docking container or any properties of controls that are docked adjacent to the current control within the docking container.</span></span>  
  
-   <span data-ttu-id="7c1f7-115">Controles são encaixados em relação a outros com base em sua ordem-z atual; o mais alto sua ordem z colocação, quanto eles são colocados da borda do contêiner de encaixe especificada.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-115">Controls are docked relative to each other based on their current z-order; the higher their z-order placement, the farther they are placed from the specified edge of the docking container.</span></span>  
  
-   <span data-ttu-id="7c1f7-116">Se o contêiner de encaixe é redimensionado, os controles encaixados dentro do contêiner serão reposicionados liberação para a mesma margem ao qual eles foram originalmente encaixados.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-116">If the docking container is resized, any docked controls within the container will be repositioned flush to the same edge to which they were originally docked.</span></span> <span data-ttu-id="7c1f7-117">Os controles encaixados também serão redimensionado para preencher qualquer espaço dentro do contêiner de acordo com o comportamento de encaixe de seus <xref:System.Windows.Automation.DockPosition>.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-117">The docked controls will also resize to fill any space within the container according to the docking behavior of their <xref:System.Windows.Automation.DockPosition>.</span></span> <span data-ttu-id="7c1f7-118">Por exemplo, se <xref:System.Windows.Automation.DockPosition.Top> for especificado, à esquerda e à direita do controle se expandirá para preencher qualquer espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-118">For example, if <xref:System.Windows.Automation.DockPosition.Top> is specified, the left and right sides of the control will expand to fill any available space.</span></span> <span data-ttu-id="7c1f7-119">Se <xref:System.Windows.Automation.DockPosition.Fill> for especificado, todos os quatro lados do controle se expandirá para preencher qualquer espaço disponível.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-119">If <xref:System.Windows.Automation.DockPosition.Fill> is specified, all four sides of the control will expand to fill any available space.</span></span>  
  
-   <span data-ttu-id="7c1f7-120">Em um sistema de vários monitor, os controles devem encaixar à esquerda ou direita do monitor atual.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-120">On a multi-monitor system, controls should dock to the left or right side of the current monitor.</span></span> <span data-ttu-id="7c1f7-121">Se não for possível, eles devem encaixar o lado esquerdo do monitor mais à esquerda ou à direita do monitor mais à direita.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-121">If that is not possible, they should dock to the left side of the leftmost monitor or the right side of the rightmost monitor.</span></span>  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a><span data-ttu-id="7c1f7-122">Membros necessários para IDockProvider</span><span class="sxs-lookup"><span data-stu-id="7c1f7-122">Required Members for IDockProvider</span></span>  
 <span data-ttu-id="7c1f7-123">As propriedades e métodos a seguir são necessários para implementar a interface IDockProvider.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-123">The following properties and methods are required for implementing the IDockProvider interface.</span></span>  
  
|<span data-ttu-id="7c1f7-124">Membros necessários</span><span class="sxs-lookup"><span data-stu-id="7c1f7-124">Required members</span></span>|<span data-ttu-id="7c1f7-125">Tipo de membro</span><span class="sxs-lookup"><span data-stu-id="7c1f7-125">Member type</span></span>|<span data-ttu-id="7c1f7-126">Observações</span><span class="sxs-lookup"><span data-stu-id="7c1f7-126">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|<span data-ttu-id="7c1f7-127">Propriedade</span><span class="sxs-lookup"><span data-stu-id="7c1f7-127">Property</span></span>|<span data-ttu-id="7c1f7-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7c1f7-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|<span data-ttu-id="7c1f7-129">Método</span><span class="sxs-lookup"><span data-stu-id="7c1f7-129">Method</span></span>|<span data-ttu-id="7c1f7-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7c1f7-130">None</span></span>|  
  
 <span data-ttu-id="7c1f7-131">Esse padrão de controle não possui eventos associados.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-131">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="7c1f7-132">Exceções</span><span class="sxs-lookup"><span data-stu-id="7c1f7-132">Exceptions</span></span>  
 <span data-ttu-id="7c1f7-133">Provedores devem lançar as exceções a seguir.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-133">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="7c1f7-134">Tipo de exceção</span><span class="sxs-lookup"><span data-stu-id="7c1f7-134">Exception type</span></span>|<span data-ttu-id="7c1f7-135">Condição</span><span class="sxs-lookup"><span data-stu-id="7c1f7-135">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> <span data-ttu-id="7c1f7-136">-Quando um controle não é capaz de executar o estilo de encaixe solicitada.</span><span class="sxs-lookup"><span data-stu-id="7c1f7-136">-   When a control is not able to execute the requested dock style.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c1f7-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c1f7-137">See Also</span></span>  
 [<span data-ttu-id="7c1f7-138">Visão geral de padrões de controle de automação da interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7c1f7-138">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="7c1f7-139">Suporte a padrões de controle em um provedor de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7c1f7-139">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="7c1f7-140">Padrões de controle de automação de interface do usuário para clientes</span><span class="sxs-lookup"><span data-stu-id="7c1f7-140">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="7c1f7-141">Visão geral de árvore de automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7c1f7-141">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="7c1f7-142">Usar o cache em automação de interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7c1f7-142">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)