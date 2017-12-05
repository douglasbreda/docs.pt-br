---
title: "Instruções passo a passo: criando o primeiro aplicativo sensível ao toque"
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
- creating a touch-sensitive application [WPF]
- touchscreen applications [WPF], creating
- touch-sensitive applications [WPF], creating
- creating a touchscreen application [WPF]
ms.assetid: d69e602e-9a25-4e24-950b-e89eaa2a906b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ee85a5d8764fc27205cf09e1af43069b25096ef1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-your-first-touch-application"></a><span data-ttu-id="3cf9e-102">Instruções passo a passo: criando o primeiro aplicativo sensível ao toque</span><span class="sxs-lookup"><span data-stu-id="3cf9e-102">Walkthrough: Creating Your First Touch Application</span></span>
<span data-ttu-id="3cf9e-103">O [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] possibilita que os aplicativos respondam ao toque.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-103">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] enables applications to respond to touch.</span></span> <span data-ttu-id="3cf9e-104">Por exemplo, você pode interagir com um aplicativo usando um ou mais dedos em um dispositivo sensível ao toque, como uma tela sensível ao toque. Este passo a passo cria um aplicativo que possibilita ao usuário mover, redimensionar ou girar um único objeto usando toque.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-104">For example, you can interact with an application by using one or more fingers on a touch-sensitive device, such as a touchscreen This walkthrough creates an application that enables the user to move, resize, or rotate a single object by using touch.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3cf9e-105">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="3cf9e-105">Prerequisites</span></span>  
 <span data-ttu-id="3cf9e-106">Você precisa dos seguintes componentes para concluir esta instrução passo a passo:</span><span class="sxs-lookup"><span data-stu-id="3cf9e-106">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_ext](../../../../includes/vs-dev10-ext-md.md)]<span data-ttu-id="3cf9e-107">.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-107">.</span></span>  
  
-   <span data-ttu-id="3cf9e-108">Windows 7.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-108">Windows 7.</span></span>  
  
-   <span data-ttu-id="3cf9e-109">Um dispositivo que aceita entrada de toque, como uma tela sensível ao toque, que dá suporte a Windows Touch.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-109">A device that accepts touch input, such as a touchscreen, that supports Windows Touch.</span></span>  
  
 <span data-ttu-id="3cf9e-110">Além disso, você deve ter um entendimento básico de como criar um aplicativo em [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], especialmente como assinar um evento e manipulá-lo.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-110">Additionally, you should have a basic understanding of how to create an application in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], especially how to subscribe to and handle an event.</span></span> <span data-ttu-id="3cf9e-111">Para obter mais informações, consulte [passo a passo: meu primeiro aplicativo de área de trabalho do WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="3cf9e-111">For more information, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="creating-the-application"></a><span data-ttu-id="3cf9e-112">Criando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3cf9e-112">Creating the Application</span></span>  
  
#### <a name="to-create-the-application"></a><span data-ttu-id="3cf9e-113">Para criar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3cf9e-113">To create the application</span></span>  
  
1.  <span data-ttu-id="3cf9e-114">Crie um novo projeto de aplicativo do WPF no Visual Basic ou no Visual C# chamado `BasicManipulation`.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-114">Create a new WPF Application project in Visual Basic or Visual C# named `BasicManipulation`.</span></span> <span data-ttu-id="3cf9e-115">Para obter mais informações, consulte [Como criar um novo projeto de aplicativo do WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="3cf9e-115">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
2.  <span data-ttu-id="3cf9e-116">Substitua o conteúdo de MainWindow.xaml pelo XAML a seguir.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-116">Replace the contents of MainWindow.xaml with the following XAML.</span></span>  
  
     <span data-ttu-id="3cf9e-117">Essa marcação cria um aplicativo simples que contém um vermelho <xref:System.Windows.Shapes.Rectangle> em um <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-117">This markup creates a simple application that contains a red <xref:System.Windows.Shapes.Rectangle> on a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="3cf9e-118">O <xref:System.Windows.UIElement.IsManipulationEnabled%2A> propriedade o <xref:System.Windows.Shapes.Rectangle> for definido como true para que ele receba eventos de manipulação.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-118">The <xref:System.Windows.UIElement.IsManipulationEnabled%2A> property of the <xref:System.Windows.Shapes.Rectangle> is set to true so that it will receive manipulation events.</span></span> <span data-ttu-id="3cf9e-119">O aplicativo assina o <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, e <xref:System.Windows.UIElement.ManipulationInertiaStarting> eventos.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-119">The application subscribes to the <xref:System.Windows.UIElement.ManipulationStarting>, <xref:System.Windows.UIElement.ManipulationDelta>, and <xref:System.Windows.UIElement.ManipulationInertiaStarting> events.</span></span> <span data-ttu-id="3cf9e-120">Esses eventos contêm a lógica para mover o <xref:System.Windows.Shapes.Rectangle> quando o usuário manipula.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-120">These events contain the logic to move the <xref:System.Windows.Shapes.Rectangle> when the user manipulates it.</span></span>  
  
     [!code-xaml[BasicManipulation#UI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml#ui)]  
  
3.  <span data-ttu-id="3cf9e-121">Se você estiver usando o Visual Basic, na primeira linha de MainWindow.xaml, substitua `x:Class="BasicManipulation.MainWindow"` por `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-121">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="BasicManipulation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
4.  <span data-ttu-id="3cf9e-122">No `MainWindow` de classe, adicione o seguinte <xref:System.Windows.UIElement.ManipulationStarting> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-122">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationStarting> event handler.</span></span>  
  
     <span data-ttu-id="3cf9e-123">O <xref:System.Windows.UIElement.ManipulationStarting> evento ocorre quando [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detecta que toque começa a entrada manipular um objeto.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-123">The <xref:System.Windows.UIElement.ManipulationStarting> event occurs when [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] detects that touch input begins to manipulate an object.</span></span> <span data-ttu-id="3cf9e-124">O código especifica que a posição da manipulação de deve ser relativo a <xref:System.Windows.Window> definindo o <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-124">The code specifies that the position of the manipulation should be relative to the <xref:System.Windows.Window> by setting the <xref:System.Windows.Input.ManipulationStartingEventArgs.ManipulationContainer%2A> property.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationstarting)]
     [!code-vb[BasicManipulation#ManipulationStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationstarting)]  
  
5.  <span data-ttu-id="3cf9e-125">No `MainWindow` de classe, adicione o seguinte <xref:System.Windows.Input.ManipulationDelta> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-125">In the `MainWindow` class, add the following <xref:System.Windows.Input.ManipulationDelta> event handler.</span></span>  
  
     <span data-ttu-id="3cf9e-126">O <xref:System.Windows.Input.ManipulationDelta> evento ocorre quando o toque altera a posição de entrada e pode ocorrer várias vezes durante uma manipulação.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-126">The <xref:System.Windows.Input.ManipulationDelta> event occurs when the touch input changes position and can occur multiple times during a manipulation.</span></span> <span data-ttu-id="3cf9e-127">O evento também pode ocorrer depois que um dedo for retirado da tela.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-127">The event can also occur after a finger is raised.</span></span> <span data-ttu-id="3cf9e-128">Por exemplo, se o usuário arrasta um dedo em uma tela, o <xref:System.Windows.Input.ManipulationDelta> evento ocorre várias vezes como move o dedo.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-128">For example, if the user drags a finger across a screen, the <xref:System.Windows.Input.ManipulationDelta> event occurs multiple times as the finger moves.</span></span> <span data-ttu-id="3cf9e-129">Quando o usuário retira um dedo na tela, o <xref:System.Windows.Input.ManipulationDelta> evento continua a ocorrer simular inércia.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-129">When the user raises a finger from the screen, the <xref:System.Windows.Input.ManipulationDelta> event keeps occurring to simulate inertia.</span></span>  
  
     <span data-ttu-id="3cf9e-130">O código se aplica a <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> para o <xref:System.Windows.UIElement.RenderTransform%2A> do <xref:System.Windows.Shapes.Rectangle> para movê-lo como o usuário move o toque de entrada.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-130">The code applies the <xref:System.Windows.Input.ManipulationDeltaEventArgs.DeltaManipulation%2A> to the <xref:System.Windows.UIElement.RenderTransform%2A> of the <xref:System.Windows.Shapes.Rectangle> to move it as the user moves the touch input.</span></span> <span data-ttu-id="3cf9e-131">Ele também verifica se o <xref:System.Windows.Shapes.Rectangle> está fora dos limites do <xref:System.Windows.Window> quando ocorre o evento durante inércia.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-131">It also checks whether the <xref:System.Windows.Shapes.Rectangle> is outside the bounds of the <xref:System.Windows.Window> when the event occurs during inertia.</span></span> <span data-ttu-id="3cf9e-132">Se assim, o aplicativo chama o <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> método para encerrar a manipulação.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-132">If so, the application calls the <xref:System.Windows.Input.ManipulationDeltaEventArgs.Complete%2A?displayProperty=nameWithType> method to end the manipulation.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationDelta](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationdelta)]
     [!code-vb[BasicManipulation#ManipulationDelta](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationdelta)]  
  
6.  <span data-ttu-id="3cf9e-133">No `MainWindow` de classe, adicione o seguinte <xref:System.Windows.UIElement.ManipulationInertiaStarting> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-133">In the `MainWindow` class, add the following <xref:System.Windows.UIElement.ManipulationInertiaStarting> event handler.</span></span>  
  
     <span data-ttu-id="3cf9e-134">O <xref:System.Windows.UIElement.ManipulationInertiaStarting> evento ocorre quando o usuário gera todos os dedos na tela.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-134">The <xref:System.Windows.UIElement.ManipulationInertiaStarting> event occurs when the user raises all fingers from the screen.</span></span> <span data-ttu-id="3cf9e-135">O código define a velocidade inicial e a desaceleração para a movimentação, a expansão e a rotação do retângulo.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-135">The code sets the initial velocity and deceleration for the movement, expansion, and rotation of the rectangle.</span></span>  
  
     [!code-csharp[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/csharp/VS_Snippets_Wpf/basicmanipulation/csharp/mainwindow.xaml.cs#manipulationinertiastarting)]
     [!code-vb[BasicManipulation#ManipulationInertiaStarting](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/basicmanipulation/visualbasic/mainwindow.xaml.vb#manipulationinertiastarting)]  
  
7.  <span data-ttu-id="3cf9e-136">Compile e execute o projeto.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-136">Build and run the project.</span></span>  
  
     <span data-ttu-id="3cf9e-137">Você deve ver um quadrado vermelho aparecer na janela.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-137">You should see a red square appear in the window.</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="3cf9e-138">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3cf9e-138">Testing the Application</span></span>  
 <span data-ttu-id="3cf9e-139">Para testar o aplicativo, tente as seguintes manipulações.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-139">To test the application, try the following manipulations.</span></span> <span data-ttu-id="3cf9e-140">Observe que você pode fazer mais de uma das seguintes opções ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-140">Note that you can do more than one of the following at the same time.</span></span>  
  
-   <span data-ttu-id="3cf9e-141">Para mover o <xref:System.Windows.Shapes.Rectangle>, coloque um dedo no <xref:System.Windows.Shapes.Rectangle> e mova o dedo na tela.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-141">To move the <xref:System.Windows.Shapes.Rectangle>, put a finger on the <xref:System.Windows.Shapes.Rectangle> and move the finger across the screen.</span></span>  
  
-   <span data-ttu-id="3cf9e-142">Para redimensionar o <xref:System.Windows.Shapes.Rectangle>, coloque dois dedos no <xref:System.Windows.Shapes.Rectangle> e mover os dedos próximo juntos ou mais distantes um do outro.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-142">To resize the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and move the fingers closer together or farther apart from each other.</span></span>  
  
-   <span data-ttu-id="3cf9e-143">Para girar o <xref:System.Windows.Shapes.Rectangle>, coloque dois dedos no <xref:System.Windows.Shapes.Rectangle> e girar os dedos em torno do outro.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-143">To rotate the <xref:System.Windows.Shapes.Rectangle>, put two fingers on the <xref:System.Windows.Shapes.Rectangle> and rotate the fingers around each other.</span></span>  
  
 <span data-ttu-id="3cf9e-144">Para causar inércia, retire seus dedos da tela enquanto realiza as manipulações anteriores.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-144">To cause inertia, quickly raise your fingers from the screen as you perform the previous manipulations.</span></span> <span data-ttu-id="3cf9e-145">O <xref:System.Windows.Shapes.Rectangle> continuará a mover, redimensionar ou girar por alguns segundos antes de parar.</span><span class="sxs-lookup"><span data-stu-id="3cf9e-145">The <xref:System.Windows.Shapes.Rectangle> will continue to move, resize, or rotate for a few seconds before it stops.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cf9e-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cf9e-146">See Also</span></span>  
 <xref:System.Windows.UIElement.ManipulationStarting?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationDelta?displayProperty=nameWithType>  
 <xref:System.Windows.UIElement.ManipulationInertiaStarting?displayProperty=nameWithType>