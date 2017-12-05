---
title: "Funções agregadas (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ff9462b1a5a6f6f9f4614098c38bb5fab14a5203
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="94cea-102">Funções agregadas (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="94cea-102">Aggregate Functions (Entity SQL)</span></span>
<span data-ttu-id="94cea-103">Uma agregação é uma construção de linguagem que condense uma coleção em um escalar como parte de uma operação de grupo.</span><span class="sxs-lookup"><span data-stu-id="94cea-103">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> <span data-ttu-id="94cea-104">as agregações de[!INCLUDE[esql](../../../../../../includes/esql-md.md)] vêm em duas formas:</span><span class="sxs-lookup"><span data-stu-id="94cea-104">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] aggregates come in two forms:</span></span>  
  
-   [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="94cea-105">funções de coleção que podem ser usadas em qualquer lugar em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="94cea-105"> collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="94cea-106">Isso inclui usar funções de agregação em projeções e predicados que atuam em coleções.</span><span class="sxs-lookup"><span data-stu-id="94cea-106">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="94cea-107">Funções de coleção são o modo preferido de especificar agregações em [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="94cea-107">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
-   <span data-ttu-id="94cea-108">O grupo agrega as expressões de consulta que têm um cláusula GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="94cea-108">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="94cea-109">Como em [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], agregados do grupo aceitam DISTINCT e ALL como modificadores a entrada aggregate.</span><span class="sxs-lookup"><span data-stu-id="94cea-109">As in [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)], group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="94cea-110">primeiro tenta interpretar uma expressão como uma função de coleção e, se a expressão for no contexto de uma expressão de seleção ele interpreta como uma agregação do grupo.</span><span class="sxs-lookup"><span data-stu-id="94cea-110"> first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="94cea-111">define um operador de agregação especial chamado [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="94cea-111"> defines a special aggregate operator called [GROUPPARTITION](../../../../../../docs/framework/data/adonet/ef/language-reference/grouppartition-entity-sql.md).</span></span> <span data-ttu-id="94cea-112">Este operador permite que você obtenha uma referência para o conjunto de entrada agrupado.</span><span class="sxs-lookup"><span data-stu-id="94cea-112">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="94cea-113">Isso permite uma consultas mais avançados de agrupamento, onde os resultados de cláusula GROUP BY podem ser usados em locais diferentes funções de agregação ou a coleção de grupo.</span><span class="sxs-lookup"><span data-stu-id="94cea-113">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="94cea-114">Funções de coleção</span><span class="sxs-lookup"><span data-stu-id="94cea-114">Collection Functions</span></span>  
 <span data-ttu-id="94cea-115">Funções de coleção operam em coleções e retornam um valor escalar.</span><span class="sxs-lookup"><span data-stu-id="94cea-115">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="94cea-116">Por exemplo, se `orders` é uma coleção de qualquer `orders`, você pode calcular a data de enviar a mais recente com a expressão a seguir:</span><span class="sxs-lookup"><span data-stu-id="94cea-116">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="94cea-117">Agregados do grupo</span><span class="sxs-lookup"><span data-stu-id="94cea-117">Group Aggregates</span></span>  
 <span data-ttu-id="94cea-118">Agregados de grupo são calculadas em um resultado de grupo como definidas por cláusula GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="94cea-118">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="94cea-119">O cláusula GROUP BY divide dados em grupos.</span><span class="sxs-lookup"><span data-stu-id="94cea-119">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="94cea-120">Para cada grupo em resultado, a função agregada é aplicada e uma agregação separada é calculada usando elementos em cada grupo como entradas para o cálculo agregado.</span><span class="sxs-lookup"><span data-stu-id="94cea-120">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="94cea-121">Quando um cláusula GROUP BY é usado em uma expressão SELECT, simplesmente agrupamento nomes de expressão, agregados, ou expressões constantes podem estar presente na projeção, em cláusula HAVING ou ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="94cea-121">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="94cea-122">O exemplo a seguir calcula a média quantidade ordenada para cada produto.</span><span class="sxs-lookup"><span data-stu-id="94cea-122">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="94cea-123">É possível ter uma agregação do grupo sem um GRUPO explícito pela cláusula SELECT na expressão.</span><span class="sxs-lookup"><span data-stu-id="94cea-123">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="94cea-124">Todos os elementos serão tratados como um único grupo, equivalente a exemplos de especificar um agrupamento com base em uma constante.</span><span class="sxs-lookup"><span data-stu-id="94cea-124">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="94cea-125">As expressões em GRUPO usadas pela cláusula são avaliadas usando o mesmo escopo de resolução que seria visível para a cláusula WHERE expressão.</span><span class="sxs-lookup"><span data-stu-id="94cea-125">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94cea-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94cea-126">See Also</span></span>  
 [<span data-ttu-id="94cea-127">Funções</span><span class="sxs-lookup"><span data-stu-id="94cea-127">Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/functions-entity-sql.md)