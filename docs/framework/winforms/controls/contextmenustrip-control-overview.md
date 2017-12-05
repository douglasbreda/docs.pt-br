---
title: "Visão geral do controle ContextMenuStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ContextMenuStrip
helpviewer_keywords:
- context menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- shortcut menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- ContextMenuStrip control [Windows Forms], about ContextMenuStrip control
ms.assetid: 9787cdb3-88f1-4198-972f-eefd9524ce39
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c04e8095d84468ee7574b31f0a30fb6f2d2b03a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="contextmenustrip-control-overview"></a><span data-ttu-id="3f50c-102">Visão geral do controle ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="3f50c-102">ContextMenuStrip Control Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="3f50c-103">O <xref:System.Windows.Forms.ContextMenuStrip> controle substitui e adiciona a funcionalidade para o <xref:System.Windows.Forms.ContextMenu> controlar; no entanto, o <xref:System.Windows.Forms.ContextMenu> controle é mantido para compatibilidade com versões anteriores e para uso futuro, se você escolher.</span><span class="sxs-lookup"><span data-stu-id="3f50c-103">The <xref:System.Windows.Forms.ContextMenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> control; however, the <xref:System.Windows.Forms.ContextMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="3f50c-104">Menus de atalho, também chamados de menus de contexto, aparecem na posição do mouse quando o usuário clica no botão direito do mouse.</span><span class="sxs-lookup"><span data-stu-id="3f50c-104">Shortcut menus, also called context menus, appear at the mouse position when the user clicks the right mouse button.</span></span> <span data-ttu-id="3f50c-105">*Menus* de atalho fornecem opções para a área de cliente ou o controle no local do ponteiro do mouse.</span><span class="sxs-lookup"><span data-stu-id="3f50c-105">Shortcut *menus* provide options for the client area or the control at the mouse pointer location.</span></span>  
  
 <span data-ttu-id="3f50c-106">O <xref:System.Windows.Forms.ContextMenuStrip> controle foi projetado para funcionar perfeitamente com o novo <xref:System.Windows.Forms.ToolStrip> e controles relacionados, mas você pode associar um <xref:System.Windows.Forms.ContextMenuStrip> com outros controles tão facilmente.</span><span class="sxs-lookup"><span data-stu-id="3f50c-106">The <xref:System.Windows.Forms.ContextMenuStrip> control is designed to work seamlessly with the new <xref:System.Windows.Forms.ToolStrip> and related controls, but you can associate a <xref:System.Windows.Forms.ContextMenuStrip> with other controls just as easily.</span></span>  
  
 <span data-ttu-id="3f50c-107">A tabela a seguir mostra a importante <xref:System.Windows.Forms.ContextMenuStrip> complementar classes.</span><span class="sxs-lookup"><span data-stu-id="3f50c-107">The following table shows the important <xref:System.Windows.Forms.ContextMenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="3f50c-108">Classe</span><span class="sxs-lookup"><span data-stu-id="3f50c-108">Class</span></span>|<span data-ttu-id="3f50c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f50c-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="3f50c-110">Representa uma opção selecionável exibida em uma <xref:System.Windows.Forms.MenuStrip> ou <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="3f50c-110">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="3f50c-111">Representa um controle que permite que o usuário selecionar um único item em uma lista que é exibida quando o usuário clica em um <xref:System.Windows.Forms.ToolStripDropDownButton> ou um item de menu de nível superior.</span><span class="sxs-lookup"><span data-stu-id="3f50c-111">Represents a control that enables the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="3f50c-112">Fornece a funcionalidade básica para controles derivados de <xref:System.Windows.Forms.ToolStripItem> que exibem itens de lista suspensa quando clicado.</span><span class="sxs-lookup"><span data-stu-id="3f50c-112">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f50c-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f50c-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>