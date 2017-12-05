---
title: Como ancorar controles nos Windows Forms
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c6f7cc527c7409ffecab2ac67386d0f819cce3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="5146d-102">Como ancorar controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5146d-102">How to: Anchor Controls on Windows Forms</span></span>
<span data-ttu-id="5146d-103">Se você estiver criando um formulário que o usuário pode redimensionar em tempo de execução, os controles no formulário deverão redimensionados e reposicionados corretamente.</span><span class="sxs-lookup"><span data-stu-id="5146d-103">If you are designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="5146d-104">Para redimensionar controles dinamicamente com o formulário, você pode usar o <xref:System.Windows.Forms.Control.Anchor%2A> propriedade dos controles de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="5146d-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="5146d-105">O <xref:System.Windows.Forms.Control.Anchor%2A> propriedade define a posição de uma âncora para o controle.</span><span class="sxs-lookup"><span data-stu-id="5146d-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="5146d-106">Quando um controle é ancorado a um formulário e esse formulário é redimensionado, o controle mantém a distância entre o controle e as posições de âncora.</span><span class="sxs-lookup"><span data-stu-id="5146d-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="5146d-107">Por exemplo, se você tiver um <xref:System.Windows.Forms.TextBox> controle é ancorado à esquerda, direita e as bordas da parte inferior do formulário, como o formulário é redimensionado, o <xref:System.Windows.Forms.TextBox> controle será redimensionado horizontalmente para que ele mantém a mesma distância dos lados esquerdos e direito do formulário.</span><span class="sxs-lookup"><span data-stu-id="5146d-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="5146d-108">Além disso, o controle se posiciona verticalmente para que sua localização seja sempre a mesma distância da borda inferior do formulário.</span><span class="sxs-lookup"><span data-stu-id="5146d-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="5146d-109">Se um controle não estiver ancorado e o formulário for redimensionado, a posição do controle em relação às bordas do formulário será alterada.</span><span class="sxs-lookup"><span data-stu-id="5146d-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>  
  
 <span data-ttu-id="5146d-110">O <xref:System.Windows.Forms.Control.Anchor%2A> propriedade interage com o <xref:System.Windows.Forms.Control.AutoSize%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5146d-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="5146d-111">Para obter mais informações, consulte [Visão Geral da Propriedade AutoSize](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5146d-111">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5146d-112">As caixas de diálogo e os comandos de menu que você vê podem ser diferentes dos descritos na Ajuda, dependendo da sua edição ou das configurações ativas.</span><span class="sxs-lookup"><span data-stu-id="5146d-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5146d-113">Para alterar as configurações, escolha **Importar e Exportar Configurações** no menu **Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="5146d-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5146d-114">Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5146d-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-anchor-a-control-on-a-form"></a><span data-ttu-id="5146d-115">Ancorar um controle em um formulário</span><span class="sxs-lookup"><span data-stu-id="5146d-115">To anchor a control on a form</span></span>  
  
1.  <span data-ttu-id="5146d-116">Selecione o controle que deseja ancorar.</span><span class="sxs-lookup"><span data-stu-id="5146d-116">Select the control you want to anchor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5146d-117">É possível ancorar vários controles simultaneamente pressionando a tecla CTRL, clicando em cada controle para selecioná-lo e, em seguida, seguindo o resto desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="5146d-117">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>  
  
2.  <span data-ttu-id="5146d-118">No **propriedades** janela, clique na seta à direita do <xref:System.Windows.Forms.Control.Anchor%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5146d-118">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>  
  
     <span data-ttu-id="5146d-119">Um editor será exibido e mostra uma cruz.</span><span class="sxs-lookup"><span data-stu-id="5146d-119">An editor is displayed that shows a cross.</span></span>  
  
3.  <span data-ttu-id="5146d-120">Para definir uma âncora, clique na seção superior, esquerda, direita ou inferior da cruz.</span><span class="sxs-lookup"><span data-stu-id="5146d-120">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>  
  
     <span data-ttu-id="5146d-121">Os controles estão ancorados na parte superior e esquerda por padrão.</span><span class="sxs-lookup"><span data-stu-id="5146d-121">Controls are anchored to the top and left by default.</span></span>  
  
4.  <span data-ttu-id="5146d-122">Para limpar um lado do controle que foi ancorado, clique nessa parte da cruz.</span><span class="sxs-lookup"><span data-stu-id="5146d-122">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>  
  
5.  <span data-ttu-id="5146d-123">Para fechar o <xref:System.Windows.Forms.Control.Anchor%2A> editor de propriedades, clique no <xref:System.Windows.Forms.Control.Anchor%2A> novamente o nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="5146d-123">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>  
  
 <span data-ttu-id="5146d-124">Quando o formulário é exibido em tempo de execução, o controle é redimensionado para permanecer posicionado na mesma distância da borda do formulário.</span><span class="sxs-lookup"><span data-stu-id="5146d-124">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="5146d-125">A distância da borda ancorada sempre é a mesma distância definida quando o controle é posicionado no Designer de Formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="5146d-125">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5146d-126">Alguns controles, como o <xref:System.Windows.Forms.ComboBox> controlar, têm um limite para sua altura.</span><span class="sxs-lookup"><span data-stu-id="5146d-126">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="5146d-127">Ancorar o controle na parte inferior do formulário ou contêiner não pode forçar o controle a exceder o limite de altura.</span><span class="sxs-lookup"><span data-stu-id="5146d-127">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>  
  
 <span data-ttu-id="5146d-128">Controles herdados devem ser `Protected` para serem ancorados.</span><span class="sxs-lookup"><span data-stu-id="5146d-128">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="5146d-129">Para alterar o nível de acesso de um controle, defina sua propriedade `Modifiers` na janela **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5146d-129">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5146d-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5146d-130">See Also</span></span>  
 [<span data-ttu-id="5146d-131">Controles dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5146d-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="5146d-132">Organizando Controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5146d-132">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="5146d-133">Visão geral da propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="5146d-133">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="5146d-134">Como encaixar controles nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5146d-134">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [<span data-ttu-id="5146d-135">Passo a passo: organizando controles nos Windows Forms utilizando um FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5146d-135">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="5146d-136">Passo a passo: organizando controles nos Windows Forms usando um TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="5146d-136">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="5146d-137">Passo a passo: definindo o layout de controles dos Windows Forms com preenchimento, margens e a propriedade AutoSize</span><span class="sxs-lookup"><span data-stu-id="5146d-137">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)