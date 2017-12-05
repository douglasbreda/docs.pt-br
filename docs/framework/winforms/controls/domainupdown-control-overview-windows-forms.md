---
title: "Visão geral do controle DomainUpDown (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DomainUpDown
helpviewer_keywords:
- spin button control [Windows Forms], about spin button
- DomainUpDown control [Windows Forms], about DomainUpDown control
ms.assetid: 3f40f9c1-20ad-4331-b9b5-b0127eb36eb3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a0692677b8ef596bb31b1869480603573a9ec98d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="domainupdown-control-overview-windows-forms"></a><span data-ttu-id="acc78-102">Visão geral do controle DomainUpDown (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="acc78-102">DomainUpDown Control Overview (Windows Forms)</span></span>
<span data-ttu-id="acc78-103">Windows Forms <xref:System.Windows.Forms.DomainUpDown> controle é essencialmente uma combinação de uma caixa de texto e um par de botões para cima ou para baixo em uma lista.</span><span class="sxs-lookup"><span data-stu-id="acc78-103">The Windows Forms <xref:System.Windows.Forms.DomainUpDown> control is essentially a combination of a text box and a pair of buttons for moving up or down through a list.</span></span> <span data-ttu-id="acc78-104">O controle exibe e define uma sequências de texto em uma lista de escolhas.</span><span class="sxs-lookup"><span data-stu-id="acc78-104">The control displays and sets a text string from a list of choices.</span></span> <span data-ttu-id="acc78-105">O usuário pode selecionar a sequência clicando nos botões para cima e para baixo para mover a lista, apertando as teclas de direção PARA BAIXO e PARA CIMA ou digitando uma cadeia de caracteres que corresponda a um item na lista.</span><span class="sxs-lookup"><span data-stu-id="acc78-105">The user can select the string by clicking up and down buttons to move through a list, by pressing the UP and DOWN ARROW keys, or by typing a string that matches an item in the list.</span></span> <span data-ttu-id="acc78-106">Um possível uso para este controle é selecionar itens de uma lista de nomes ordenada alfabeticamente.</span><span class="sxs-lookup"><span data-stu-id="acc78-106">One possible use for this control is for selecting items from an alphabetically sorted list of names.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="acc78-107">Para classificar a lista, defina o <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> propriedade `true`.</span><span class="sxs-lookup"><span data-stu-id="acc78-107">To sort the list, set the <xref:System.Windows.Forms.DomainUpDown.Sorted%2A> property to `true`.</span></span>  
  
 <span data-ttu-id="acc78-108">A função deste controle é bem parecida com a da caixa de listagem ou caixa de combinação, mas ocupa muito pouco espaço.</span><span class="sxs-lookup"><span data-stu-id="acc78-108">The function of this control is very similar to the list box or combo box, but it takes up very little space.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="acc78-109">Propriedades da chave</span><span class="sxs-lookup"><span data-stu-id="acc78-109">Key Properties</span></span>  
 <span data-ttu-id="acc78-110">As propriedades de chave do controle são <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, e <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span><span class="sxs-lookup"><span data-stu-id="acc78-110">The key properties of the control are <xref:System.Windows.Forms.DomainUpDown.Items%2A>, <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>, and <xref:System.Windows.Forms.DomainUpDown.Wrap%2A>.</span></span> <span data-ttu-id="acc78-111">O <xref:System.Windows.Forms.DomainUpDown.Items%2A> propriedade contém a lista de objetos cujos valores de texto são exibidos no controle.</span><span class="sxs-lookup"><span data-stu-id="acc78-111">The <xref:System.Windows.Forms.DomainUpDown.Items%2A> property contains the list of objects whose text values are displayed in the control.</span></span> <span data-ttu-id="acc78-112">Se <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> é definido como `false`, o controle preenche automaticamente o texto que o usuário digita e faz a correspondência com um valor na lista.</span><span class="sxs-lookup"><span data-stu-id="acc78-112">If <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A> is set to `false`, the control automatically completes text that the user types and matches it to a value in the list.</span></span> <span data-ttu-id="acc78-113">Se <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> é definido como `true`, após o último item de rolagem levará você para o primeiro item na lista e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="acc78-113">If <xref:System.Windows.Forms.DomainUpDown.Wrap%2A> is set to `true`, scrolling past the last item will take you to the first item in the list and vice versa.</span></span> <span data-ttu-id="acc78-114">Os métodos de chave do controle são <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> e <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span><span class="sxs-lookup"><span data-stu-id="acc78-114">The key methods of the control are <xref:System.Windows.Forms.DomainUpDown.UpButton%2A> and <xref:System.Windows.Forms.DomainUpDown.DownButton%2A>.</span></span>  
  
 <span data-ttu-id="acc78-115">Este controle exibe somente sequências de texto.</span><span class="sxs-lookup"><span data-stu-id="acc78-115">This control displays only text strings.</span></span> <span data-ttu-id="acc78-116">Se você quiser um controle que exibe valores numéricos, use o <xref:System.Windows.Forms.NumericUpDown> controle.</span><span class="sxs-lookup"><span data-stu-id="acc78-116">If you want a control that displays numeric values, use the <xref:System.Windows.Forms.NumericUpDown> control.</span></span> <span data-ttu-id="acc78-117">Para mais informação, consulte [Visão geral do controle NumericUpDown](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="acc78-117">For more information, see [NumericUpDown Control Overview](../../../../docs/framework/winforms/controls/numericupdown-control-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc78-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="acc78-118">See Also</span></span>  
 <xref:System.Windows.Forms.DomainUpDown>  
 [<span data-ttu-id="acc78-119">Controle DomainUpDown</span><span class="sxs-lookup"><span data-stu-id="acc78-119">DomainUpDown Control</span></span>](../../../../docs/framework/winforms/controls/domainupdown-control-windows-forms.md)