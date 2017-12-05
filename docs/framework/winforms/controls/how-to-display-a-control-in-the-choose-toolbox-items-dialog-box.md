---
title: "Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f7bbb13e8a2b877d0f503e091b5bb8b1e7e89d00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="9bd81-102">Como exibir um controle na caixa de diálogo Escolher Itens da Caixa de Ferramentas</span><span class="sxs-lookup"><span data-stu-id="9bd81-102">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>
<span data-ttu-id="9bd81-103">Ao desenvolver e distribuir controles, é possível fazer com que esses controles apareçam na caixa de diálogo **Escolher itens da caixa de ferramentas** que é exibida quando você clica com o botão direito do mouse na **Caixa de ferramentas** e seleciona **Escolher itens**.</span><span class="sxs-lookup"><span data-stu-id="9bd81-103">As you develop and distribute controls, you may want those controls to appear in the **Choose Toolbox Items** dialog box, which is displayed when you right-click the **Toolbox** and select **Choose Items**.</span></span> <span data-ttu-id="9bd81-104">Você pode permitir que seu controle apareça na caixa de diálogo usando o procedimento de registro AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="9bd81-104">You can enable your control to appear in this dialog box by using the AssemblyFoldersEx registration procedure.</span></span>  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a><span data-ttu-id="9bd81-105">Para exibir o controle na caixa de diálogo Escolher itens da caixa de ferramentas</span><span class="sxs-lookup"><span data-stu-id="9bd81-105">To display your control in the Choose Toolbox Items dialog box</span></span>  
  
-   <span data-ttu-id="9bd81-106">Instale o assembly do controle no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="9bd81-106">Install your control assembly to the global assembly cache.</span></span> <span data-ttu-id="9bd81-107">Para obter mais informações, consulte [Como instalar um assembly no cache de assembly global](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span><span class="sxs-lookup"><span data-stu-id="9bd81-107">For more information, see [How to: Install an Assembly into the Global Assembly Cache](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)</span></span>  
  
     <span data-ttu-id="9bd81-108">-ou-</span><span class="sxs-lookup"><span data-stu-id="9bd81-108">-or-</span></span>  
  
-   <span data-ttu-id="9bd81-109">Registre o controle e assemblies de tempo de design associados usando o procedimento de registro AssemblyFoldersEx.</span><span class="sxs-lookup"><span data-stu-id="9bd81-109">Register your control and its associated design-time assemblies by using the AssemblyFoldersEx registration procedure.</span></span> <span data-ttu-id="9bd81-110">AssemblyFoldersEx é um local de Registro em que os fornecedores de terceiros armazenam caminhos para cada versão da estrutura à qual dão suporte.</span><span class="sxs-lookup"><span data-stu-id="9bd81-110">AssemblyFoldersEx is a registry location where third-party vendors store paths for each version of the framework that they support.</span></span> <span data-ttu-id="9bd81-111">A resolução de tempo de design pode procurar neste local do Registro para localizar assemblies de referência.</span><span class="sxs-lookup"><span data-stu-id="9bd81-111">Design-time resolution can look in this registry location to find reference assemblies.</span></span> <span data-ttu-id="9bd81-112">O script de Registro pode especificar os controles que deseja que apareçam na caixa de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="9bd81-112">The registry script can specify the controls you want to appear in the Toolbox.</span></span> <span data-ttu-id="9bd81-113">Para obter mais informações, consulte [Implantando um controle personalizado e assemblies de tempo de Design (Visual Studio 2013)](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span><span class="sxs-lookup"><span data-stu-id="9bd81-113">For more information, see [Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bd81-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bd81-114">See Also</span></span>  
 [<span data-ttu-id="9bd81-115">Caixa de diálogo Escolher Itens da Caixa de Ferramentas (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="9bd81-115">Choose Toolbox Items Dialog Box (Visual Studio)</span></span>](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [<span data-ttu-id="9bd81-116">Implantando um controle personalizado e Assemblies de tempo de Design (Visual Studio 2013)</span><span class="sxs-lookup"><span data-stu-id="9bd81-116">Deploying a Custom Control and Design-time Assemblies (Visual Studio 2013)</span></span>](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [<span data-ttu-id="9bd81-117">Desenvolvendo controles dos Windows Forms em tempo de design</span><span class="sxs-lookup"><span data-stu-id="9bd81-117">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [<span data-ttu-id="9bd81-118">Como instalar um assembly no cache de assembly global</span><span class="sxs-lookup"><span data-stu-id="9bd81-118">How to: Install an Assembly into the Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [<span data-ttu-id="9bd81-119">Passo a passo: preenchendo automaticamente a caixa de ferramentas com componentes personalizados</span><span class="sxs-lookup"><span data-stu-id="9bd81-119">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)