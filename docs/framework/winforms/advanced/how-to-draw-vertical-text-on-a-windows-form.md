---
title: "Como desenhar texto vertical em um formulário do Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- StringFormat.FormatFlags
- Graphics.DrawString
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- strings [Windows Forms], drawing vertical
- text [Windows Forms], drawing
- text [Windows Forms], vertical text
ms.assetid: 717a6131-00f6-4373-b574-9894e8317799
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76da7be50f9e12454e16e08ec4db494585fae613
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-vertical-text-on-a-windows-form"></a><span data-ttu-id="94833-102">Como desenhar texto vertical em um formulário do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="94833-102">How to: Draw Vertical Text on a Windows Form</span></span>
<span data-ttu-id="94833-103">O exemplo de código a seguir mostra como desenhar texto vertical em um formulário usando o <xref:System.Drawing.Graphics.DrawString%2A> método <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="94833-103">The following code example shows how to draw vertical text on a form by using the <xref:System.Drawing.Graphics.DrawString%2A> method of <xref:System.Drawing.Graphics>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94833-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94833-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94833-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="94833-105">Compiling the Code</span></span>  
 <span data-ttu-id="94833-106">Não é possível chamar este método <xref:System.Windows.Forms.Form.Load> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="94833-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="94833-107">O conteúdo desenhado não será redesenhado se o formulário é redimensionado ou obscurecido por outra forma.</span><span class="sxs-lookup"><span data-stu-id="94833-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="94833-108">Para tornar o seu conteúdo redesenhar automaticamente, você deve substituir o <xref:System.Windows.Forms.Control.OnPaint%2A> método.</span><span class="sxs-lookup"><span data-stu-id="94833-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="94833-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="94833-109">Robust Programming</span></span>  
 <span data-ttu-id="94833-110">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="94833-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="94833-111">A fonte Arial não está instalada.</span><span class="sxs-lookup"><span data-stu-id="94833-111">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94833-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94833-112">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawString%2A>  
 <xref:System.Drawing.StringFormat.FormatFlags%2A>  
 <xref:System.Drawing.StringFormatFlags>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="94833-113">Introdução à Programação de Elementos Gráficos</span><span class="sxs-lookup"><span data-stu-id="94833-113">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="94833-114">Usando fontes e texto</span><span class="sxs-lookup"><span data-stu-id="94833-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)