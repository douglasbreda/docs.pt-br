---
title: "Como adicionar uma coluna não associada a um controle DataGridView dos Windows Forms associado a dados"
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
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2cd6a1494a98d912469f7e45c7751a0a9741ff17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="9a3b6-102">Como adicionar uma coluna não associada a um controle DataGridView dos Windows Forms associado a dados</span><span class="sxs-lookup"><span data-stu-id="9a3b6-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9a3b6-103">Os dados exibidos no <xref:System.Windows.Forms.DataGridView> controle normalmente será proveniente de uma fonte de dados de algum tipo, mas talvez você queira exibir uma coluna de dados que não vêm da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="9a3b6-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="9a3b6-104">Esse tipo de coluna é chamado de coluna não associada.</span><span class="sxs-lookup"><span data-stu-id="9a3b6-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="9a3b6-105">Colunas não associadas podem assumir várias formas.</span><span class="sxs-lookup"><span data-stu-id="9a3b6-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="9a3b6-106">Frequentemente, elas são usadas para fornecer acesso aos detalhes de uma linha de dados.</span><span class="sxs-lookup"><span data-stu-id="9a3b6-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="9a3b6-107">O exemplo de código a seguir demonstra como criar uma coluna não associada dos botões de **Detalhes** para exibir uma tabela filho relacionada a uma linha específica em uma tabela pai quando você implementa um cenário mestre/de detalhes.</span><span class="sxs-lookup"><span data-stu-id="9a3b6-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="9a3b6-108">Para responder a cliques de botão, implementar um <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> manipulador de eventos que exibe um formulário que contém a tabela filho.</span><span class="sxs-lookup"><span data-stu-id="9a3b6-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="9a3b6-109">Há suporte para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9a3b6-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="9a3b6-110">Consulte também [Como adicionar e remover colunas no controle DataGridView dos Windows Forms usando o designer](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="9a3b6-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/dyyesckz\(v=vs.110\))</span></span>  
  
## <a name="example"></a><span data-ttu-id="9a3b6-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9a3b6-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9a3b6-112">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9a3b6-112">Compiling the Code</span></span>  
 <span data-ttu-id="9a3b6-113">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="9a3b6-113">This example requires:</span></span>  
  
-   <span data-ttu-id="9a3b6-114">Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="9a3b6-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="9a3b6-115">Referências aos assemblies <xref:System?displayProperty=nameWithType> e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9a3b6-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a3b6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a3b6-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="9a3b6-117">Exibindo dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a3b6-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="9a3b6-118">Modos de exibição de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a3b6-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)