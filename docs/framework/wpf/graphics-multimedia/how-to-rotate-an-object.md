---
title: Como girar um objeto
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
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b9b6212ed6c50faf73a6d3531f001a1b7e72d33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rotate-an-object"></a><span data-ttu-id="524ed-102">Como girar um objeto</span><span class="sxs-lookup"><span data-stu-id="524ed-102">How to: Rotate an Object</span></span>
<span data-ttu-id="524ed-103">Este exemplo mostra como girar um objeto.</span><span class="sxs-lookup"><span data-stu-id="524ed-103">This example shows how to rotate an object.</span></span> <span data-ttu-id="524ed-104">O exemplo cria primeiro um <xref:System.Windows.Media.RotateTransform> e, em seguida, especifica sua <xref:System.Windows.Media.RotateTransform.Angle%2A> em graus.</span><span class="sxs-lookup"><span data-stu-id="524ed-104">The example first creates a <xref:System.Windows.Media.RotateTransform> and then specifies its <xref:System.Windows.Media.RotateTransform.Angle%2A> in degrees.</span></span>  
  
 <span data-ttu-id="524ed-105">O exemplo a seguir gira um <xref:System.Windows.Shapes.Polyline> 45 graus sobre seu canto superior esquerdo do objeto.</span><span class="sxs-lookup"><span data-stu-id="524ed-105">The following example rotates a <xref:System.Windows.Shapes.Polyline> object 45 degrees about its upper-left corner.</span></span>  
  
## <a name="example"></a><span data-ttu-id="524ed-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="524ed-106">Example</span></span>  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <span data-ttu-id="524ed-107">O <xref:System.Windows.Media.RotateTransform.CenterX%2A> e <xref:System.Windows.Media.RotateTransform.CenterY%2A> propriedades do <xref:System.Windows.Media.RotateTransform> especificar o ponto sobre o qual o objeto for girado.</span><span class="sxs-lookup"><span data-stu-id="524ed-107">The <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties of the <xref:System.Windows.Media.RotateTransform> specify the point about which the object is rotated.</span></span> <span data-ttu-id="524ed-108">Esse ponto central é expresso no espaço coordenado do elemento que é transformado.</span><span class="sxs-lookup"><span data-stu-id="524ed-108">This center point is expressed in the coordinate space of the element that is transformed.</span></span> <span data-ttu-id="524ed-109">Por padrão, a rotação é aplicada a (0,0), que é o canto superior esquerdo do objeto a ser transformado.</span><span class="sxs-lookup"><span data-stu-id="524ed-109">By default, the rotation is applied to (0,0), which is the upper-left corner of the object to transform.</span></span>  
  
 <span data-ttu-id="524ed-110">O exemplo a seguir gira um <xref:System.Windows.Shapes.Polyline> 45 graus no sentido horário em torno do ponto (25,50) do objeto.</span><span class="sxs-lookup"><span data-stu-id="524ed-110">The next example rotates a <xref:System.Windows.Shapes.Polyline> object clockwise 45 degrees about the point (25,50).</span></span>  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 <span data-ttu-id="524ed-111">A ilustração a seguir mostra os resultados da aplicação de um <xref:System.Windows.Media.Transform> para os dois objetos.</span><span class="sxs-lookup"><span data-stu-id="524ed-111">The following illustration shows the results of applying a <xref:System.Windows.Media.Transform> to the two objects.</span></span>  
  
 <span data-ttu-id="524ed-112">![rotações de 45 graus com diferentes pontos centrais](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="524ed-112">![45 degree rotations with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
<span data-ttu-id="524ed-113">Dois objetos que giram 45 graus de diferentes centros de rotação</span><span class="sxs-lookup"><span data-stu-id="524ed-113">Two objects that rotate 45 degrees from different rotational centers</span></span>  
  
 <span data-ttu-id="524ed-114">O <xref:System.Windows.Shapes.Polyline> nos exemplos anteriores é um <xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="524ed-114">The <xref:System.Windows.Shapes.Polyline> in the previous examples is a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="524ed-115">Quando você aplica um <xref:System.Windows.Media.Transform> para o <xref:System.Windows.UIElement.RenderTransform%2A> propriedade de um <xref:System.Windows.UIElement>, você pode usar o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade para especificar uma origem para cada <xref:System.Windows.Media.Transform> aplicáveis ao elemento.</span><span class="sxs-lookup"><span data-stu-id="524ed-115">When you apply a <xref:System.Windows.Media.Transform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a <xref:System.Windows.UIElement>, you can use the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to specify an origin for every <xref:System.Windows.Media.Transform> that you apply to the element.</span></span> <span data-ttu-id="524ed-116">Porque o <xref:System.Windows.UIElement.RenderTransformOrigin%2A> propriedade usa coordenadas relativas, você pode aplicar uma transformação para o centro do elemento, mesmo se você não souber seu tamanho.</span><span class="sxs-lookup"><span data-stu-id="524ed-116">Because the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property uses relative coordinates, you can apply a transformation to the center of the element even if you do not know its size.</span></span> <span data-ttu-id="524ed-117">Para obter mais informações e para obter um exemplo, consulte [especificar a origem de uma transformação por valores relativos usando](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span><span class="sxs-lookup"><span data-stu-id="524ed-117">For more information and for an example, see [Specify the Origin of a Transform by Using Relative Values](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-the-origin-of-a-transform-by-using-relative-values.md).</span></span>  
  
 <span data-ttu-id="524ed-118">Para obter o exemplo completo, consulte [Amostras de Transformação 2D](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="524ed-118">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="524ed-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="524ed-119">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="524ed-120">Visão geral de transformações</span><span class="sxs-lookup"><span data-stu-id="524ed-120">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="524ed-121">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="524ed-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)