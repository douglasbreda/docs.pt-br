---
title: Derivando a estrutura relacional do DataSet do esquema XML (XSD)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0aae23c295401d4b9565c35d4d47c5ab913029d5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="b7ce3-102">Derivando a estrutura relacional do DataSet do esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="b7ce3-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="b7ce3-103">Esta seção fornece uma visão geral de como o esquema relacional de um `DataSet` é compilado a partir de um documento de esquema XSD (linguagem de definição de esquema XML).</span><span class="sxs-lookup"><span data-stu-id="b7ce3-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="b7ce3-104">Em geral, para cada `complexType` elemento filho de um elemento de esquema, uma tabela é gerada no `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="b7ce3-105">A estrutura da tabela é determinada pela definição do tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="b7ce3-106">Tabelas são criadas no `DataSet` para elementos de nível superior no esquema.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="b7ce3-107">No entanto, uma tabela é criada somente para um nível superior `complexType` elemento quando o `complexType` elemento está aninhado em outro `complexType` aninhada de caso de elemento, no qual `complexType` elemento é mapeado para um `DataTable` dentro de `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="b7ce3-108">Para obter mais informações sobre o XSD, consulte a parte de esquema XML do World Wide Web Consortium (W3C) 0: Primer recomendação, o esquema de XML parte 1: estruturas de recomendação e o esquema XML parte 2: recomendação de tipos de dados, localizado em [http:// www.w3.org/](http://www.w3.org/TR/).</span><span class="sxs-lookup"><span data-stu-id="b7ce3-108">For more information about the XSD, see the World Wide Web Consortium (W3C) XML Schema Part 0: Primer Recommendation, the XML Schema Part 1: Structures Recommendation, and the XML Schema Part 2: Datatypes Recommendation, located at [http://www.w3.org/](http://www.w3.org/TR/).</span></span>  
  
 <span data-ttu-id="b7ce3-109">O exemplo a seguir demonstra um esquema XML onde `customers` é o elemento filho do `MyDataSet` elemento, que é um **DataSet** elemento.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="b7ce3-110">No exemplo anterior, o elemento `customers` é um elemento de tipo complexo.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="b7ce3-111">Portanto, o definição de tipo complexo é analisada, e o processo de mapeamento cria a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 <span data-ttu-id="b7ce3-112">O tipo de dados de cada coluna na tabela é derivado do tipo do Esquema XML do elemento ou atributo correspondente especificado.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7ce3-113">Se o elemento `customers` é um tipo de dados de esquema XML simples, como **inteiro**, nenhuma tabela é gerada.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="b7ce3-114">As tabelas são criadas apenas para os elementos de nível superior que são tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="b7ce3-115">No esquema XML a seguir, o **esquema** elemento tem dois filhos do elemento, `InStateCustomers` e `OutOfStateCustomers`.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="b7ce3-116">Os elementos filho `InStateCustomers` e `OutOfStateCustomers` são ambos elementos de tipo complexo (`customerType`).</span><span class="sxs-lookup"><span data-stu-id="b7ce3-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="b7ce3-117">Portanto, o processo de mapeamento gera duas tabelas a seguir idênticas no `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="b7ce3-118">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b7ce3-118">In This Section</span></span>  
 [<span data-ttu-id="b7ce3-119">Restrições de esquema (XSD) de XML de mapeamento para restrições de conjunto de dados</span><span class="sxs-lookup"><span data-stu-id="b7ce3-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="b7ce3-120">Descreve os elementos de esquema XML usados para criar restrições de chave estrangeiras e exclusivas em um `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="b7ce3-121">Gerar relações de conjunto de dados de esquema XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="b7ce3-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="b7ce3-122">Descreve os elementos de esquema XML usados para criar relações entre colunas da tabela em um `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="b7ce3-123">Relações e restrições de esquema XML</span><span class="sxs-lookup"><span data-stu-id="b7ce3-123">XML Schema Constraints and Relationships</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="b7ce3-124">Descreve como relações são criadas implicitamente ao usar elementos de esquema XML para criar restrições em um `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b7ce3-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="b7ce3-125">Related Sections</span></span>  
 <span data-ttu-id="b7ce3-126">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md) (Usando XML em um DataSet)</span><span class="sxs-lookup"><span data-stu-id="b7ce3-126">[Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)</span></span>  
 <span data-ttu-id="b7ce3-127">Descreve como carregar e manter a estrutura relacional e os dados em um `DataSet` como dados XML.</span><span class="sxs-lookup"><span data-stu-id="b7ce3-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ce3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7ce3-128">See Also</span></span>  
 <span data-ttu-id="b7ce3-129">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="b7ce3-129">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>