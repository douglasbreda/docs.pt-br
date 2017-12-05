---
title: Como acessar objetos associados a linhas DataGridView dos Windows Forms
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
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 910730f67024fbe0d292b4a329a36fb3ea8254b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="20b91-102">Como acessar objetos associados a linhas DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20b91-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="20b91-103">Às vezes, é útil exibir uma tabela de informações armazenadas em uma coleção de objetos de negócios.</span><span class="sxs-lookup"><span data-stu-id="20b91-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="20b91-104">Quando você associa um <xref:System.Windows.Forms.DataGridView> controle para essa coleção, cada propriedade pública é exibido em sua própria coluna, a menos que a propriedade foi marcado como não pesquisável com um <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="20b91-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="20b91-105">Por exemplo, uma coleção de objetos `Customer` teria colunas como **Nome** e **Endereço**.</span><span class="sxs-lookup"><span data-stu-id="20b91-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="20b91-106">Se esses objetos contiverem informações adicionais e o código que você deseja acessar, será possível alcançá-lo por meio de objetos de linha.</span><span class="sxs-lookup"><span data-stu-id="20b91-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="20b91-107">No exemplo de código a seguir, os usuários podem selecionar várias linhas e clicar em um botão para enviar uma fatura para cada um dos clientes correspondentes.</span><span class="sxs-lookup"><span data-stu-id="20b91-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="20b91-108">Para acessar objetos associados a linhas</span><span class="sxs-lookup"><span data-stu-id="20b91-108">To access row-bound objects</span></span>  
  
-   <span data-ttu-id="20b91-109">Use a propriedade <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="20b91-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="20b91-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="20b91-110">Example</span></span>  
 <span data-ttu-id="20b91-111">O exemplo de código completo inclui um simples `Customer` implementação e associa o <xref:System.Windows.Forms.DataGridView> para um <xref:System.Collections.ArrayList> que contém alguns `Customer` objetos.</span><span class="sxs-lookup"><span data-stu-id="20b91-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="20b91-112">O <xref:System.Windows.Forms.Control.Click> manipulador de eventos do <xref:System.Windows.Forms.Button?displayProperty=nameWithType> deve acessar o `Customer` objetos por meio de linhas, porque a coleção de cliente não está acessível fora de <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="20b91-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="20b91-113">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="20b91-113">Compiling the Code</span></span>  
 <span data-ttu-id="20b91-114">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="20b91-114">This example requires:</span></span>  
  
-   <span data-ttu-id="20b91-115">Referências aos assemblies Sistema e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="20b91-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="20b91-116">Para obter informações sobre como criar este exemplo da linha de comando para [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], consulte [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) (Compilação da linha de comando) ou [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) (Compilação da linha de comando com csc.exe).</span><span class="sxs-lookup"><span data-stu-id="20b91-116">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="20b91-117">Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.</span><span class="sxs-lookup"><span data-stu-id="20b91-117">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="20b91-118">Consulte também [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) (Como compilar e executar um exemplo completo de código dos Windows Forms usando o Visual Studio).</span><span class="sxs-lookup"><span data-stu-id="20b91-118">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20b91-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20b91-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="20b91-120">Exibindo dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20b91-120">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="20b91-121">Como associar objetos a controles DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20b91-121">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)