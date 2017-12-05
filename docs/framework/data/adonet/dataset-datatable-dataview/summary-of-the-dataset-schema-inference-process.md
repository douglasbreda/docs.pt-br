---
title: "Resumo do processo de inferência de esquema de conjunto de dados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd0891c8-d068-4e30-a76f-7c375f078bf7
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 15469e917129db7668df17f22fb71b166993d4fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="summary-of-the-dataset-schema-inference-process"></a><span data-ttu-id="69fae-102">Resumo do processo de inferência de esquema de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="69fae-102">Summary of the DataSet Schema Inference Process</span></span>
<span data-ttu-id="69fae-103">O processo de inferência primeiro determina, do documento XML, quais elementos serão inferidos como tabelas.</span><span class="sxs-lookup"><span data-stu-id="69fae-103">The inference process first determines, from the XML document, which elements will be inferred as tables.</span></span> <span data-ttu-id="69fae-104">O XML restantes, o processo de inferência determina as colunas para as tabelas.</span><span class="sxs-lookup"><span data-stu-id="69fae-104">From the remaining XML, the inference process determines the columns for those tables.</span></span> <span data-ttu-id="69fae-105">Para tabelas aninhadas, o processo de inferência gera aninhada <xref:System.Data.DataRelation> e <xref:System.Data.ForeignKeyConstraint> objetos.</span><span class="sxs-lookup"><span data-stu-id="69fae-105">For nested tables, the inference process generates nested <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects.</span></span>  
  
 <span data-ttu-id="69fae-106">A seguir é um resumo das regras de inferência de tipos:</span><span class="sxs-lookup"><span data-stu-id="69fae-106">Following is a brief summary of inference rules:</span></span>  
  
-   <span data-ttu-id="69fae-107">Elementos que têm atributos são inferidos como tabelas.</span><span class="sxs-lookup"><span data-stu-id="69fae-107">Elements that have attributes are inferred as tables.</span></span>  
  
-   <span data-ttu-id="69fae-108">Elementos que têm elementos filho são inferidos como tabelas.</span><span class="sxs-lookup"><span data-stu-id="69fae-108">Elements that have child elements are inferred as tables.</span></span>  
  
-   <span data-ttu-id="69fae-109">Elementos que se repetem são inferidos como uma única tabela.</span><span class="sxs-lookup"><span data-stu-id="69fae-109">Elements that repeat are inferred as a single table.</span></span>  
  
-   <span data-ttu-id="69fae-110">Se o elemento do documento ou raiz, nenhum atributo e não há elementos filho que poderiam ser inferidos como colunas, ele é inferido como um <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="69fae-110">If the document, or root, element has no attributes, and no child elements that would be inferred as columns, it is inferred as a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="69fae-111">Caso contrário, o elemento do documento será inferido como uma tabela.</span><span class="sxs-lookup"><span data-stu-id="69fae-111">Otherwise, the document element is inferred as a table.</span></span>  
  
-   <span data-ttu-id="69fae-112">Atributos são inferidos como colunas.</span><span class="sxs-lookup"><span data-stu-id="69fae-112">Attributes are inferred as columns.</span></span>  
  
-   <span data-ttu-id="69fae-113">Elementos que não têm atributos ou elementos filho, e que não se repetem, são inferidos como colunas.</span><span class="sxs-lookup"><span data-stu-id="69fae-113">Elements that have no attributes or child elements, and that do not repeat, are inferred as columns.</span></span>  
  
-   <span data-ttu-id="69fae-114">Para elementos que são inferidos como tabelas aninhadas dentro de outros elementos que também são inferidos como tabelas, uma aninhada **DataRelation** é criada entre as duas tabelas.</span><span class="sxs-lookup"><span data-stu-id="69fae-114">For elements that are inferred as nested tables within other elements that are also inferred as tables, a nested **DataRelation** is created between the two tables.</span></span> <span data-ttu-id="69fae-115">Uma coluna de chave primária, novo chamada **TableName_Id** é adicionado a ambas as tabelas e usado pelo **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="69fae-115">A new, primary key column named **TableName_Id** is added to both tables and used by the **DataRelation**.</span></span> <span data-ttu-id="69fae-116">Um **ForeignKeyConstraint** é criada entre as duas tabelas usando o **TableName_Id** coluna.</span><span class="sxs-lookup"><span data-stu-id="69fae-116">A **ForeignKeyConstraint** is created between the two tables using the **TableName_Id** column.</span></span>  
  
-   <span data-ttu-id="69fae-117">Para elementos que são inferidos como tabelas e que contêm texto, mas que nenhum elemento filho, uma nova coluna chamada **TableName_Text** é criado para o texto de cada um dos elementos.</span><span class="sxs-lookup"><span data-stu-id="69fae-117">For elements that are inferred as tables and that contain text but have no child elements, a new column named **TableName_Text** is created for the text of each of the elements.</span></span> <span data-ttu-id="69fae-118">Se um elemento é inferido como uma tabela e tem o texto, mas também tem elementos filho, o texto será ignorado.</span><span class="sxs-lookup"><span data-stu-id="69fae-118">If an element is inferred as a table and has text, but also has child elements, the text is ignored.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69fae-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69fae-119">See Also</span></span>  
 [<span data-ttu-id="69fae-120">Inferindo estrutura relacional do conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="69fae-120">Inferring DataSet Relational Structure from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)  
 [<span data-ttu-id="69fae-121">Carregar um conjunto de dados do XML</span><span class="sxs-lookup"><span data-stu-id="69fae-121">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="69fae-122">Carregando informações de esquema de conjunto de dados de XML</span><span class="sxs-lookup"><span data-stu-id="69fae-122">Loading DataSet Schema Information from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 <span data-ttu-id="69fae-123">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="69fae-123">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 <span data-ttu-id="69fae-124">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md) (DataSets, DataTables e DataViews)</span><span class="sxs-lookup"><span data-stu-id="69fae-124">[DataSets, DataTables, and DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)</span></span>  
 <span data-ttu-id="69fae-125">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="69fae-125">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>