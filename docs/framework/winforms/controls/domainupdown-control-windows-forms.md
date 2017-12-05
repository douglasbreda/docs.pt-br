---
title: Controle DomainUpDown (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 37cec82876edadfed5cda338ca12775ad19ae732
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="domainupdown-control-windows-forms"></a><span data-ttu-id="05488-102">Controle DomainUpDown (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="05488-102">DomainUpDown Control (Windows Forms)</span></span>
<span data-ttu-id="05488-103">Windows Forms <xref:System.Windows.Forms.DomainUpDown> controle parece com uma combinação de uma caixa de texto e um par de botões para mover para cima ou para baixo em uma lista.</span><span class="sxs-lookup"><span data-stu-id="05488-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control looks like a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="05488-104">O controle exibe e define uma sequências de texto em uma lista de escolhas.</span><span class="sxs-lookup"><span data-stu-id="05488-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="05488-105">O usuário pode selecionar a sequência clicando nos botões para cima e para baixo para mover a lista, apertando as teclas de direção PARA BAIXO e PARA CIMA ou digitando uma cadeia de caracteres que corresponda a um item na lista.</span><span class="sxs-lookup"><span data-stu-id="05488-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="05488-106">Um possível uso para este controle é selecionar itens de uma lista de nomes ordenada alfabeticamente.</span><span class="sxs-lookup"><span data-stu-id="05488-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span> <span data-ttu-id="05488-107">(Para classificar a lista, defina o <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> propriedade `true`.) A função deste controle é bem parecida com a da caixa de listagem ou caixa de combinação, mas ocupa muito pouco espaço.</span><span class="sxs-lookup"><span data-stu-id="05488-107">(To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.) The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
 <span data-ttu-id="05488-108">As propriedades de chave do controle são <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, e <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="05488-108">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="05488-109">O <xref:System.Windows.Forms.DomainUpDown.Items%2A> propriedade contém a lista de objetos cujos valores de texto são exibidos no controle.</span><span class="sxs-lookup"><span data-stu-id="05488-109">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="05488-110">Se <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> é definido como `false`, o controle preenche automaticamente o texto que o usuário digita e faz a correspondência com um valor na lista.</span><span class="sxs-lookup"><span data-stu-id="05488-110">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="05488-111">Se <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> é definido como `true`, após o último item de rolagem levará você para o primeiro item na lista e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="05488-111">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="05488-112">Os métodos de chave do controle são <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> e <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span><span class="sxs-lookup"><span data-stu-id="05488-112">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="05488-113">Este controle exibe somente sequências de texto.</span><span class="sxs-lookup"><span data-stu-id="05488-113">This control displays only text strings.</span></span> <span data-ttu-id="05488-114">Se você quiser um controle que exibe valores numéricos, use o <xref:System.Windows.Forms.NumericUpDown> controle.</span><span class="sxs-lookup"><span data-stu-id="05488-114">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="05488-115">Para obter mais informações, consulte [controle NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .</span><span class="sxs-lookup"><span data-stu-id="05488-115">For more information, see [NumericUpDown Control](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md) .</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05488-116">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="05488-116">In This Section</span></span>  
 [<span data-ttu-id="05488-117">Visão geral do controle DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="05488-117">DomainUpDown Control Overview</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 <span data-ttu-id="05488-118">Apresenta os conceitos gerais do <xref:System.Windows.Forms.DomainUpDown> controle, que permite aos usuários procurar e selecionar em uma lista de cadeias de caracteres de texto.</span><span class="sxs-lookup"><span data-stu-id="05488-118">Introduces the general concepts of the <xref:System.Windows.Forms.DomainUpDown> control, which allows users to browse through and select from a list of text strings.</span></span>  
  
 <span data-ttu-id="05488-119">[How to: Add Items to Windows Forms DomainUpDown Controls Programmatically](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md) (Como adicionar itens nos controles DomainUpDown dos Windows Forms de forma programática)</span><span class="sxs-lookup"><span data-stu-id="05488-119">[How to: Add Items to Windows Forms DomainUpDown Controls Programmatically](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)</span></span>  
 <span data-ttu-id="05488-120">Descreve como especificar as cadeias de caracteres de texto a <xref:System.Windows.Forms.DomainUpDown> controle deve exibir.</span><span class="sxs-lookup"><span data-stu-id="05488-120">Describes how to specify the text strings the <xref:System.Windows.Forms.DomainUpDown> control should display.</span></span>  
  
 [<span data-ttu-id="05488-121">Como remover itens de controles DomainUpDown dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05488-121">How to: Remove Items from Windows Forms DomainUpDown Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 <span data-ttu-id="05488-122">Descreve como excluir itens do <xref:System.Windows.Forms.DomainUpDown> controle no código.</span><span class="sxs-lookup"><span data-stu-id="05488-122">Describes how to delete items from the <xref:System.Windows.Forms.DomainUpDown> control in code.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="05488-123">Referência</span><span class="sxs-lookup"><span data-stu-id="05488-123">Reference</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 <span data-ttu-id="05488-124">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="05488-124">Describes this class and has links to all its members.</span></span>  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 <span data-ttu-id="05488-125">Descreve essa classe e tem links para todos os seus membros.</span><span class="sxs-lookup"><span data-stu-id="05488-125">Describes this class and has links to all its members..</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="05488-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="05488-126">Related Sections</span></span>  
 [<span data-ttu-id="05488-127">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05488-127">Controls You Can Use On Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 <span data-ttu-id="05488-128">Fornece uma lista completa dos controles dos Windows Forms, com links para informações sobre seu uso.</span><span class="sxs-lookup"><span data-stu-id="05488-128">Provides a complete list of Windows Forms controls, with links to information on their use.</span></span>