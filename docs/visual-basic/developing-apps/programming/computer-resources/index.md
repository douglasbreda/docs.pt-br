---
title: Acessar recursos de computador (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- computer resources [Visual Basic]
- My.Computer object [Visual Basic], tasks
- computer resources [Visual Basic], accessing
ms.assetid: 75b81c88-f7c0-46e0-95c8-0c006d2120f9
ms.openlocfilehash: 7128a71f28d1755a14fcda5f09bee11202ab4154
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001893"
---
# <a name="accessing-computer-resources-visual-basic"></a><span data-ttu-id="e6e05-102">Acessar recursos de computador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6e05-102">Accessing computer resources (Visual Basic)</span></span>

<span data-ttu-id="e6e05-103">O objeto `My.Computer` é um dos três objetos centrais em `My`, fornecendo acesso a informações e a funcionalidades usadas com frequência.</span><span class="sxs-lookup"><span data-stu-id="e6e05-103">The `My.Computer` object is one of the three central objects in `My`, providing access to information and commonly used functionality.</span></span> <span data-ttu-id="e6e05-104">`My.Computer` fornece métodos, propriedades e eventos para acessar o computador no qual o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="e6e05-104">`My.Computer` provides methods, properties, and events for accessing the computer on which the application is running.</span></span> <span data-ttu-id="e6e05-105">Seus objetos incluem:</span><span class="sxs-lookup"><span data-stu-id="e6e05-105">Its objects include:</span></span>  
  
-   <xref:Microsoft.VisualBasic.Devices.Audio>
-   <span data-ttu-id="e6e05-106">Área de Transferência (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span><span class="sxs-lookup"><span data-stu-id="e6e05-106">Clipboard (<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>)</span></span>
-   <xref:Microsoft.VisualBasic.Devices.Clock>
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem>
-   <xref:Microsoft.VisualBasic.Devices.ServerComputer.Info%2A>
-   <xref:Microsoft.VisualBasic.Devices.Keyboard>
-   <xref:Microsoft.VisualBasic.Devices.Mouse>
-   <xref:Microsoft.VisualBasic.Devices.Network>
-   <xref:Microsoft.VisualBasic.Devices.Ports>
-   <span data-ttu-id="e6e05-107">Registro (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span><span class="sxs-lookup"><span data-stu-id="e6e05-107">Registry (<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>)</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="e6e05-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e6e05-108">In this section</span></span>

<span data-ttu-id="e6e05-109">[Reprodução de Sons](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md) </span><span class="sxs-lookup"><span data-stu-id="e6e05-109">[Playing Sounds](../../../../visual-basic/developing-apps/programming/computer-resources/playing-sounds.md) </span></span>  
<span data-ttu-id="e6e05-110">Lista tarefas associadas a `My.Computer.Audio`, como reproduzir um som em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="e6e05-110">Lists tasks associated with `My.Computer.Audio`, such as playing a sound in the background.</span></span>

<span data-ttu-id="e6e05-111">[Armazenar dados e ler da Área de Transferência](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md) </span><span class="sxs-lookup"><span data-stu-id="e6e05-111">[Storing Data to and Reading from the Clipboard](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md) </span></span>  
<span data-ttu-id="e6e05-112">Lista tarefas associadas a `My.Computer.Clipboard`, como leitura ou gravação de dados na Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="e6e05-112">Lists tasks associated with `My.Computer.Clipboard`, such as reading data from or writing data to the Clipboard.</span></span>

<span data-ttu-id="e6e05-113">[Obter informações sobre o computador](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md) </span><span class="sxs-lookup"><span data-stu-id="e6e05-113">[Getting Information about the Computer](../../../../visual-basic/developing-apps/programming/computer-resources/getting-information-about-the-computer.md) </span></span>  
<span data-ttu-id="e6e05-114">Lista tarefas associadas a `My.Computer.Info`, como determinar o nome completo ou endereços IP do computador.</span><span class="sxs-lookup"><span data-stu-id="e6e05-114">Lists tasks associated with `My.Computer.Info`, such as determining a computer's full name or IP addresses.</span></span>

<span data-ttu-id="e6e05-115">[Acessando o teclado](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md) </span><span class="sxs-lookup"><span data-stu-id="e6e05-115">[Accessing the Keyboard](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md) </span></span>  
<span data-ttu-id="e6e05-116">Lista tarefas associadas a `My.Computer.Keyboard`, como determinar se CAPS LOCK está ativado.</span><span class="sxs-lookup"><span data-stu-id="e6e05-116">Lists tasks associated with `My.Computer.Keyboard`, such as determining whether CAPS LOCK is on.</span></span>

<span data-ttu-id="e6e05-117">[Acessar o mouse](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md) </span><span class="sxs-lookup"><span data-stu-id="e6e05-117">[Accessing the Mouse](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-mouse.md) </span></span>  
<span data-ttu-id="e6e05-118">Lista tarefas associadas a `My.Computer.Mouse`, como determinar se um mouse está presente.</span><span class="sxs-lookup"><span data-stu-id="e6e05-118">Lists tasks associated with `My.Computer.Mouse`, such as determining whether a mouse is present.</span></span>

<span data-ttu-id="e6e05-119">[Realizar operações de rede](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md) </span><span class="sxs-lookup"><span data-stu-id="e6e05-119">[Performing Network Operations](../../../../visual-basic/developing-apps/programming/computer-resources/performing-network-operations.md) </span></span>  
<span data-ttu-id="e6e05-120">Lista tarefas associadas a `My.Computer.Network`, como carregar ou baixar arquivos.</span><span class="sxs-lookup"><span data-stu-id="e6e05-120">Lists tasks associated with `My.Computer.Network`, such as uploading or downloading files.</span></span>

<span data-ttu-id="e6e05-121">[Acessar as portas do computador](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md) </span><span class="sxs-lookup"><span data-stu-id="e6e05-121">[Accessing the Computer's Ports](../../../../visual-basic/developing-apps/programming/computer-resources/accessing-the-computer-s-ports.md) </span></span>  
<span data-ttu-id="e6e05-122">Lista tarefas associadas a `My.Computer.Ports`, como mostrar as portas seriais disponíveis ou enviar cadeias de caracteres a portas seriais.</span><span class="sxs-lookup"><span data-stu-id="e6e05-122">Lists tasks associated with `My.Computer.Ports`, such as showing available serial ports or sending strings to serial ports.</span></span>

<span data-ttu-id="e6e05-123">[Lendo e Gravando do Registro](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span><span class="sxs-lookup"><span data-stu-id="e6e05-123">[Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md) </span></span>  
<span data-ttu-id="e6e05-124">Lista tarefas associadas a `My.Computer.Registry`, como leitura ou gravação de dados em chaves do Registro.</span><span class="sxs-lookup"><span data-stu-id="e6e05-124">Lists tasks associated with `My.Computer.Registry`, such as reading data from or writing data to registry keys.</span></span>