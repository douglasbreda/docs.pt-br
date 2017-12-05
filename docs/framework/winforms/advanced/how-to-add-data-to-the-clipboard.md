---
title: "Como adicionar dados à área de transferência"
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
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47858af6d4e3dc5f29632c5a74f2431a2cc200b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-data-to-the-clipboard"></a><span data-ttu-id="7e297-102">Como adicionar dados à área de transferência</span><span class="sxs-lookup"><span data-stu-id="7e297-102">How to: Add Data to the Clipboard</span></span>
<span data-ttu-id="7e297-103">O <xref:System.Windows.Forms.Clipboard> classe fornece métodos que você pode usar para interagir com o recurso de área de transferência do sistema operacional Windows.</span><span class="sxs-lookup"><span data-stu-id="7e297-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="7e297-104">Muitos aplicativos usam a Área de Transferência como um repositório temporário para dados.</span><span class="sxs-lookup"><span data-stu-id="7e297-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="7e297-105">Por exemplo, processadores globais usam a Área de Transferência durante operações de cortar e colar.</span><span class="sxs-lookup"><span data-stu-id="7e297-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="7e297-106">A Área de Transferência também é útil para transferir dados de um aplicativo para outro.</span><span class="sxs-lookup"><span data-stu-id="7e297-106">The Clipboard is also useful for transferring data from one application to another.</span></span>  
  
 <span data-ttu-id="7e297-107">Quando você adiciona dados à Área de Transferência, você pode indicar o formato de dados para que outros aplicativos possam reconhecer os dados se puderem usar esse formato.</span><span class="sxs-lookup"><span data-stu-id="7e297-107">When you add data to the Clipboard, you can indicate the data format so that other applications can recognize the data if they can use that format.</span></span> <span data-ttu-id="7e297-108">Você também pode adicionar dados à Área de Transferência em vários formatos diferentes para aumentar o número de outros aplicativos que potencialmente podem usar os dados.</span><span class="sxs-lookup"><span data-stu-id="7e297-108">You can also add data to the Clipboard in multiple different formats to increase the number of other applications that can potentially use the data.</span></span>  
  
 <span data-ttu-id="7e297-109">Um formato da Área de Transferência é uma cadeia de caracteres que identifica o formato para que um aplicativo que use esse formato possa recuperar os dados associados.</span><span class="sxs-lookup"><span data-stu-id="7e297-109">A Clipboard format is a string that identifies the format so that an application that uses that format can retrieve the associated data.</span></span> <span data-ttu-id="7e297-110">O <xref:System.Windows.Forms.DataFormats> classe fornece os nomes de formato predefinidos para seu uso.</span><span class="sxs-lookup"><span data-stu-id="7e297-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="7e297-111">Você também pode usar seus próprios nomes de formato ou usar o tipo de um objeto como o formato.</span><span class="sxs-lookup"><span data-stu-id="7e297-111">You can also use your own format names or use the type of an object as its format.</span></span>  
  
 <span data-ttu-id="7e297-112">Para adicionar dados à área de transferência em um ou vários formatos, use o <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> método.</span><span class="sxs-lookup"><span data-stu-id="7e297-112">To add data to the Clipboard in one or multiple formats, use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method.</span></span> <span data-ttu-id="7e297-113">Você pode passar qualquer objeto para esse método, mas, para adicionar dados em vários formatos, é preciso primeiro adicionar os dados a um objeto separado projetado para funcionar com vários formatos.</span><span class="sxs-lookup"><span data-stu-id="7e297-113">You can pass any object to this method, but to add data in multiple formats, you must first add the data to a separate object designed to work with multiple formats.</span></span> <span data-ttu-id="7e297-114">Normalmente, você adicionará os dados para um <xref:System.Windows.Forms.DataObject>, mas você pode usar qualquer tipo que implementa o <xref:System.Windows.Forms.IDataObject> interface.</span><span class="sxs-lookup"><span data-stu-id="7e297-114">Typically, you will add your data to a <xref:System.Windows.Forms.DataObject>, but you can use any type that implements the <xref:System.Windows.Forms.IDataObject> interface.</span></span>  
  
 <span data-ttu-id="7e297-115">No [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], você pode adicionar dados diretamente à Área de Transferência usando novos métodos projetados para facilitar as tarefas básicas da Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="7e297-115">In [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], you can add data directly to the Clipboard by using new methods designed to make basic Clipboard tasks easier.</span></span> <span data-ttu-id="7e297-116">Use esses métodos quando você trabalhar com os dados em um único formato comum, como texto.</span><span class="sxs-lookup"><span data-stu-id="7e297-116">Use these methods when you work with data in a single, common format such as text.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e297-117">Todos os aplicativos baseados em Windows compartilham a Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="7e297-117">All Windows-based applications share the Clipboard.</span></span> <span data-ttu-id="7e297-118">Portanto, os conteúdos estão sujeito a alterações quando você muda para outro aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7e297-118">Therefore, the contents are subject to change when you switch to another application.</span></span>  
>   
>  <span data-ttu-id="7e297-119">O <xref:System.Windows.Forms.Clipboard> classe só pode ser usada em threads configurados para o modo single thread apartment (STA).</span><span class="sxs-lookup"><span data-stu-id="7e297-119">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="7e297-120">Para usar essa classe, certifique-se de que seu `Main` método está marcado com o <xref:System.STAThreadAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="7e297-120">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>  
>   
>  <span data-ttu-id="7e297-121">Um objeto deve ser serializável para que seja colocado na Área de Transferência.</span><span class="sxs-lookup"><span data-stu-id="7e297-121">An object must be serializable for it to be put on the Clipboard.</span></span> <span data-ttu-id="7e297-122">Para fazer um tipo serializável, marque-o com o <xref:System.SerializableAttribute> atributo.</span><span class="sxs-lookup"><span data-stu-id="7e297-122">To make a type serializable, mark it with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="7e297-123">Se você passar um objeto não serializável para um método de Área de Transferência, o método falhará sem lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="7e297-123">If you pass a non-serializable object to a Clipboard method, the method will fail without throwing an exception.</span></span> <span data-ttu-id="7e297-124">Para obter mais informações sobre serialização, consulte <xref:System.Runtime.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="7e297-124">For more information about serialization, see <xref:System.Runtime.Serialization>.</span></span>  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="7e297-125">Para adicionar dados à Área de Transferência em um único formato comum</span><span class="sxs-lookup"><span data-stu-id="7e297-125">To add data to the Clipboard in a single, common format</span></span>  
  
1.  <span data-ttu-id="7e297-126">Use o <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, ou <xref:System.Windows.Forms.Clipboard.SetText%2A> método.</span><span class="sxs-lookup"><span data-stu-id="7e297-126">Use the <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, or <xref:System.Windows.Forms.Clipboard.SetText%2A> method.</span></span> <span data-ttu-id="7e297-127">Esses métodos estão disponíveis somente em [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e297-127">These methods are available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a><span data-ttu-id="7e297-128">Para adicionar dados à Área de Transferência em um formato personalizado</span><span class="sxs-lookup"><span data-stu-id="7e297-128">To add data to the Clipboard in a custom format</span></span>  
  
1.  <span data-ttu-id="7e297-129">Use o <xref:System.Windows.Forms.Clipboard.SetData%2A> método com um nome de formato personalizado.</span><span class="sxs-lookup"><span data-stu-id="7e297-129">Use the <xref:System.Windows.Forms.Clipboard.SetData%2A> method with a custom format name.</span></span> <span data-ttu-id="7e297-130">Esse método está disponível apenas no [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e297-130">This method is available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     <span data-ttu-id="7e297-131">Você também pode usar nomes de formato predefinidos com o <xref:System.Windows.Forms.Clipboard.SetData%2A> método.</span><span class="sxs-lookup"><span data-stu-id="7e297-131">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="7e297-132">Para obter mais informações, consulte <xref:System.Windows.Forms.DataFormats>.</span><span class="sxs-lookup"><span data-stu-id="7e297-132">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a><span data-ttu-id="7e297-133">Para adicionar dados à Área de Transferência em vários formatos</span><span class="sxs-lookup"><span data-stu-id="7e297-133">To add data to the Clipboard in multiple formats</span></span>  
  
1.  <span data-ttu-id="7e297-134">Use o <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> método e passar um <xref:System.Windows.Forms.DataObject> que contém seus dados.</span><span class="sxs-lookup"><span data-stu-id="7e297-134">Use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method and pass in a <xref:System.Windows.Forms.DataObject> that contains your data.</span></span> <span data-ttu-id="7e297-135">Você deve usar esse método para adicionar dados à área de transferência em versões anteriores à [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7e297-135">You must use this method to add data to the Clipboard on versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="7e297-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e297-136">See Also</span></span>  
 [<span data-ttu-id="7e297-137">Operações do Tipo "Arrastar e Soltar" e Suporte à Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="7e297-137">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [<span data-ttu-id="7e297-138">Como Recuperar Dados da Área de Transferência</span><span class="sxs-lookup"><span data-stu-id="7e297-138">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)