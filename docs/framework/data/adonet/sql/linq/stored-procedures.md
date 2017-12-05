---
title: Procedimentos armazenados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1cf8d155dd04cd4f7b3f860186428c14ce4e462e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="stored-procedures"></a><span data-ttu-id="f7508-102">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="f7508-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="f7508-103">usa métodos em seu modelo de objeto para representar os procedimentos armazenados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="f7508-103"> uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="f7508-104">Você designa métodos como procedimentos armazenados aplicando o atributo <xref:System.Data.Linq.Mapping.FunctionAttribute> e, quando for necessário, o atributo <xref:System.Data.Linq.Mapping.ParameterAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f7508-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="f7508-105">Para obter mais informações, consulte [o LINQ no modelo de objeto do SQL](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span><span class="sxs-lookup"><span data-stu-id="f7508-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="f7508-106">Os desenvolvedores que usam [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] normalmente usaria o [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] para mapear os procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="f7508-106">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map stored procedures.</span></span> <span data-ttu-id="f7508-107">Os tópicos nesta seção de apresentação como formar e chamar esses métodos em seu aplicativo se você escreve o código que você mesmo.</span><span class="sxs-lookup"><span data-stu-id="f7508-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7508-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="f7508-108">In This Section</span></span>  
 [<span data-ttu-id="f7508-109">Como: retornar conjuntos de linhas</span><span class="sxs-lookup"><span data-stu-id="f7508-109">How to: Return Rowsets</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)  
 <span data-ttu-id="f7508-110">Descreve como retornar linhas de dados e mostra como usar um parâmetro de entrada.</span><span class="sxs-lookup"><span data-stu-id="f7508-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="f7508-111">Como: usar procedimentos armazenados que usam parâmetros</span><span class="sxs-lookup"><span data-stu-id="f7508-111">How to: Use Stored Procedures that Take Parameters</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="f7508-112">Descreve como usar os parâmetros de entrada e saída.</span><span class="sxs-lookup"><span data-stu-id="f7508-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="f7508-113">Como: usar procedimentos armazenados mapeados para várias formas de resultado</span><span class="sxs-lookup"><span data-stu-id="f7508-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="f7508-114">Descreve como fornecer para retornos de várias formas no mesmo procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="f7508-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="f7508-115">Como: usar procedimentos armazenados mapeados para formas sequenciais de resultado</span><span class="sxs-lookup"><span data-stu-id="f7508-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="f7508-116">Descreve como fornecer para várias formas onde a sequência de retorno é conhecida.</span><span class="sxs-lookup"><span data-stu-id="f7508-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="f7508-117">Personalizando operações usando procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="f7508-117">Customizing Operations By Using Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="f7508-118">Descreve como usar procedimentos armazenados para implementar operações de inserção, atualização e exclusão.</span><span class="sxs-lookup"><span data-stu-id="f7508-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="f7508-119">Personalizando operações usando procedimentos armazenados exclusivamente</span><span class="sxs-lookup"><span data-stu-id="f7508-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="f7508-120">Descreve como usar nada além de procedimentos armazenados para implementar operações de inserção, atualização e exclusão.</span><span class="sxs-lookup"><span data-stu-id="f7508-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f7508-121">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="f7508-121">Related Sections</span></span>  
 [<span data-ttu-id="f7508-122">Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="f7508-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="f7508-123">Fornece informações sobre como criar e usar seu modelo de objeto do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f7508-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="f7508-124">Passo a passo: Usando somente procedimentos armazenados de (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f7508-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="f7508-125">Inclui os procedimentos que ilustram como usar procedimentos armazenados no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f7508-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="f7508-126">Passo a passo: Usando somente procedimentos armazenados de (c#)</span><span class="sxs-lookup"><span data-stu-id="f7508-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="f7508-127">Inclui os procedimentos que ilustram como usar procedimentos armazenados no C#.</span><span class="sxs-lookup"><span data-stu-id="f7508-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>