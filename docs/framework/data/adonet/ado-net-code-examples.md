---
title: "Exemplos de código ADO.NET"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology: dotnet-ado
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c119657a-9ce6-4940-91e4-ac1d5f0d9584
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: fcdfee8486b089456d294d983c09dc6246bd8ac2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="adonet-code-examples"></a><span data-ttu-id="16cc6-102">Exemplos de código ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16cc6-102">ADO.NET code examples</span></span>
<span data-ttu-id="16cc6-103">As listagens de código neste tópico demonstram como recuperar dados de um banco de dados usando as seguintes tecnologias do ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="16cc6-103">The code listings in this topic demonstrate how to retrieve data from a database by using the following ADO.NET technologies:</span></span>

- <span data-ttu-id="16cc6-104">Provedores de dados do ADO.NET:</span><span class="sxs-lookup"><span data-stu-id="16cc6-104">ADO.NET data providers:</span></span>

  - <span data-ttu-id="16cc6-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span><span class="sxs-lookup"><span data-stu-id="16cc6-105">[SqlClient](#sqlclient) (`System.Data.SqlClient`)</span></span>

  - <span data-ttu-id="16cc6-106">[OleDb](#oledb) (`System.Data.OleDb`)</span><span class="sxs-lookup"><span data-stu-id="16cc6-106">[OleDb](#oledb) (`System.Data.OleDb`)</span></span>

  - <span data-ttu-id="16cc6-107">[ODBC](#odbc) (`System.Data.Odbc`)</span><span class="sxs-lookup"><span data-stu-id="16cc6-107">[Odbc](#odbc) (`System.Data.Odbc`)</span></span>

  - <span data-ttu-id="16cc6-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span><span class="sxs-lookup"><span data-stu-id="16cc6-108">[OracleClient](#oracleclient) (`System.Data.OracleClient`)</span></span>

- <span data-ttu-id="16cc6-109">ADO.NET Entity Framework:</span><span class="sxs-lookup"><span data-stu-id="16cc6-109">ADO.NET Entity Framework:</span></span>

  - [<span data-ttu-id="16cc6-110">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="16cc6-110">LINQ to Entities</span></span>](#linq-to-entities)

  - [<span data-ttu-id="16cc6-111">ObjectQuery tipado</span><span class="sxs-lookup"><span data-stu-id="16cc6-111">Typed ObjectQuery</span></span>](#typed-objectquery)

  - <span data-ttu-id="16cc6-112">[O EntityClient](#entityclient) (`System.Data.EntityClient`)</span><span class="sxs-lookup"><span data-stu-id="16cc6-112">[EntityClient](#entityclient) (`System.Data.EntityClient`)</span></span>

- [<span data-ttu-id="16cc6-113">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="16cc6-113">LINQ to SQL</span></span>](#linq-to-sql)

## <a name="adonet-data-provider-examples"></a><span data-ttu-id="16cc6-114">Exemplos de provedor de dados do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="16cc6-114">ADO.NET data provider examples</span></span>
<span data-ttu-id="16cc6-115">As listagens de código a seguir demonstram como recuperar dados de um banco de dados usando provedores de dados do ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="16cc6-115">The following code listings demonstrate how to retrieve data from a database using ADO.NET data providers.</span></span> <span data-ttu-id="16cc6-116">Os dados são retornados em um `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="16cc6-116">The data is returned in a `DataReader`.</span></span> <span data-ttu-id="16cc6-117">Para obter mais informações, consulte [recuperando dados usando um DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).</span><span class="sxs-lookup"><span data-stu-id="16cc6-117">For more information, see [Retrieving Data Using a DataReader](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md).</span></span>

### <a name="sqlclient"></a><span data-ttu-id="16cc6-118">SqlClient</span><span class="sxs-lookup"><span data-stu-id="16cc6-118">SqlClient</span></span>
<span data-ttu-id="16cc6-119">O código desse exemplo pressupõe que você pode se conectar ao banco de dados de exemplo `Northwind` no Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="16cc6-119">The code in this example assumes that you can connect to the `Northwind` sample database on Microsoft [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="16cc6-120">O código cria um <xref:System.Data.SqlClient.SqlCommand> para selecionar linhas da tabela Products, adicionando um <xref:System.Data.SqlClient.SqlParameter> para restringir os resultados às linhas com um UnitPrice maior que o valor do parâmetro especificado, neste caso, 5.</span><span class="sxs-lookup"><span data-stu-id="16cc6-120">The code creates a <xref:System.Data.SqlClient.SqlCommand> to select rows from the Products table, adding a <xref:System.Data.SqlClient.SqlParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="16cc6-121">O <xref:System.Data.SqlClient.SqlConnection> é aberto em um `using` bloco, que garante que os recursos estejam fechados e descartados quando o código será encerrado.</span><span class="sxs-lookup"><span data-stu-id="16cc6-121">The <xref:System.Data.SqlClient.SqlConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="16cc6-122">O código executa o comando usando um <xref:System.Data.SqlClient.SqlDataReader> e exibe os resultados na janela do console.</span><span class="sxs-lookup"><span data-stu-id="16cc6-122">The code executes the command by using a <xref:System.Data.SqlClient.SqlDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.SqlClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.SqlClient/VB/source.vb#1)]

### <a name="oledb"></a><span data-ttu-id="16cc6-123">OleDb</span><span class="sxs-lookup"><span data-stu-id="16cc6-123">OleDb</span></span>
<span data-ttu-id="16cc6-124">O código neste exemplo pressupõe que você pode se conectar ao banco de dados Northwind do Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="16cc6-124">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="16cc6-125">O código cria um <xref:System.Data.OleDb.OleDbCommand> para selecionar linhas da tabela Products, adicionando um <xref:System.Data.OleDb.OleDbParameter> para restringir os resultados às linhas com um UnitPrice maior que o valor do parâmetro especificado, neste caso, 5.</span><span class="sxs-lookup"><span data-stu-id="16cc6-125">The code creates a <xref:System.Data.OleDb.OleDbCommand> to select rows from the Products table, adding a <xref:System.Data.OleDb.OleDbParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="16cc6-126">O <xref:System.Data.OleDb.OleDbConnection> é aberto dentro de um bloco `using`, o que garante que os recursos sejam fechados e descartados quando o código for fechado.</span><span class="sxs-lookup"><span data-stu-id="16cc6-126">The <xref:System.Data.OleDb.OleDbConnection> is opened inside of a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="16cc6-127">O código executa o comando usando um <xref:System.Data.OleDb.OleDbDataReader> e exibe os resultados na janela do console.</span><span class="sxs-lookup"><span data-stu-id="16cc6-127">The code executes the command by using a <xref:System.Data.OleDb.OleDbDataReader>, and displays the results in the console window.</span></span>

 [!code-csharp[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.OleDb#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.OleDb/VB/source.vb#1)]

### <a name="odbc"></a><span data-ttu-id="16cc6-128">Odbc</span><span class="sxs-lookup"><span data-stu-id="16cc6-128">Odbc</span></span>
<span data-ttu-id="16cc6-129">O código neste exemplo pressupõe que você pode se conectar ao banco de dados Northwind do Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="16cc6-129">The code in this example assumes that you can connect to the Microsoft Access Northwind sample database.</span></span> <span data-ttu-id="16cc6-130">O código cria um <xref:System.Data.Odbc.OdbcCommand> para selecionar linhas da tabela Products, adicionando um <xref:System.Data.Odbc.OdbcParameter> para restringir os resultados às linhas com um UnitPrice maior que o valor do parâmetro especificado, neste caso, 5.</span><span class="sxs-lookup"><span data-stu-id="16cc6-130">The code creates a <xref:System.Data.Odbc.OdbcCommand> to select rows from the Products table, adding a <xref:System.Data.Odbc.OdbcParameter> to restrict the results to rows with a UnitPrice greater than the specified parameter value, in this case 5.</span></span> <span data-ttu-id="16cc6-131">O <xref:System.Data.Odbc.OdbcConnection> é aberto em um `using` bloco, que garante que os recursos estejam fechados e descartados quando o código será encerrado.</span><span class="sxs-lookup"><span data-stu-id="16cc6-131">The <xref:System.Data.Odbc.OdbcConnection> is opened inside a `using` block, which ensures that resources are closed and disposed when the code exits.</span></span> <span data-ttu-id="16cc6-132">O código executa o comando usando um <xref:System.Data.Odbc.OdbcDataReader> e exibe os resultados na janela do console.</span><span class="sxs-lookup"><span data-stu-id="16cc6-132">The code executes the command by using a <xref:System.Data.Odbc.OdbcDataReader>, and displays the results in the console window.</span></span>

[!code-csharp[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/CS/source.cs#1)] 
[!code-vb[DataWorks SampleApp.Odbc#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Odbc/VB/source.vb#1)] 

### <a name="oracleclient"></a><span data-ttu-id="16cc6-133">OracleClient</span><span class="sxs-lookup"><span data-stu-id="16cc6-133">OracleClient</span></span>
<span data-ttu-id="16cc6-134">O código neste exemplo pressupõe uma conexão a DEMO.CUSTOMER em um servidor Oracle.</span><span class="sxs-lookup"><span data-stu-id="16cc6-134">The code in this example assumes a connection to DEMO.CUSTOMER on an Oracle server.</span></span> <span data-ttu-id="16cc6-135">Você também deve adicionar uma referência ao System.Data.OracleClient.dll.</span><span class="sxs-lookup"><span data-stu-id="16cc6-135">You must also add a reference to the System.Data.OracleClient.dll.</span></span> <span data-ttu-id="16cc6-136">O código retorna os dados em um <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="16cc6-136">The code returns the data in an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>

 [!code-csharp[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/CS/source.cs#1)]
 [!code-vb[DataWorks SampleApp.Oracle#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SampleApp.Oracle/VB/source.vb#1)]

## <a name="entity-framework-examples"></a><span data-ttu-id="16cc6-137">Exemplos do Entity Framework</span><span class="sxs-lookup"><span data-stu-id="16cc6-137">Entity Framework examples</span></span>
<span data-ttu-id="16cc6-138">As seguintes listagens de código demonstram como recuperar dados de uma fonte de dados consultando entidades em um EDM (Modelo de Dados de Entidade).</span><span class="sxs-lookup"><span data-stu-id="16cc6-138">The following code listings demonstrate how to retrieve data from a data source by querying entities in an Entity Data Model (EDM).</span></span> <span data-ttu-id="16cc6-139">Esses exemplos usam o [Northwind modelo](http://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638).</span><span class="sxs-lookup"><span data-stu-id="16cc6-139">These examples use the [Northwind model](http://msdn.microsoft.com/74521f8c-e974-48cb-8858-c08deff52638).</span></span> <span data-ttu-id="16cc6-140">Para obter mais informações, consulte [visão geral do Entity Framework](../../../../docs/framework/data/adonet/ef/overview.md).</span><span class="sxs-lookup"><span data-stu-id="16cc6-140">For more information, see [Entity Framework Overview](../../../../docs/framework/data/adonet/ef/overview.md).</span></span>

### <a name="linq-to-entities"></a><span data-ttu-id="16cc6-141">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="16cc6-141">LINQ to Entities</span></span>
<span data-ttu-id="16cc6-142">O código neste exemplo usa uma consulta LINQ para retornar dados como objetos Categories, que são projetados como um tipo anônimo que contém somente as propriedades CategoryID e CategoryName.</span><span class="sxs-lookup"><span data-stu-id="16cc6-142">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="16cc6-143">Para obter mais informações, consulte [LINQ para visão geral de entidades](http://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6).</span><span class="sxs-lookup"><span data-stu-id="16cc6-143">For more information, see [LINQ to Entities Overview](http://msdn.microsoft.com/86d87a27-c17a-45ac-b28d-72c8500333c6).</span></span>

```csharp
using System;
using System.Linq;
using System.Data.Objects;
using NorthwindModel;

class LinqSample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            try
            {
                var query = from category in context.Categories
                            select new
                            {
                                categoryID = category.CategoryID,
                                categoryName = category.CategoryName
                            };

                foreach (var categoryInfo in query)
                {
                    Console.WriteLine("\t{0}\t{1}",
                        categoryInfo.categoryID, categoryInfo.categoryName);
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System
Imports System.Linq
Imports System.Data.Objects
Imports NorthwindModel

Class LinqSample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Try
                Dim query = From category In context.Categories _
                            Select New With _
                            { _
                                .categoryID = category.CategoryID, _
                                .categoryName = category.CategoryName _
                            }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                        categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using
    End Sub
End Class
```

### <a name="typed-objectquery"></a><span data-ttu-id="16cc6-144">ObjectQuery tipado</span><span class="sxs-lookup"><span data-stu-id="16cc6-144">Typed ObjectQuery</span></span>
<span data-ttu-id="16cc6-145">O código neste exemplo usa um <xref:System.Data.Objects.ObjectQuery%601> para retornar dados como objetos Categories.</span><span class="sxs-lookup"><span data-stu-id="16cc6-145">The code in this example uses an <xref:System.Data.Objects.ObjectQuery%601> to return data as Categories objects.</span></span> <span data-ttu-id="16cc6-146">Para obter mais informações, consulte [consultas de objeto](http://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).</span><span class="sxs-lookup"><span data-stu-id="16cc6-146">For more information, see [Object Queries](http://msdn.microsoft.com/0768033c-876f-471d-85d5-264884349276).</span></span>

```csharp
using System;
using System.Data.Objects;
using NorthwindModel;

class ObjectQuerySample
{
    public static void ExecuteQuery()
    {
        using (NorthwindEntities context = new NorthwindEntities())
        {
            ObjectQuery<Categories> categoryQuery = context.Categories;

            foreach (Categories category in 
                categoryQuery.Execute(MergeOption.AppendOnly))
            {
                Console.WriteLine("\t{0}\t{1}",
                    category.CategoryID, category.CategoryName);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System
Imports System.Data.Objects
Imports NorthwindModel

Class ObjectQuerySample
    Public Shared Sub ExecuteQuery()
        Using context As NorthwindEntities = New NorthwindEntities()
            Dim categoryQuery As ObjectQuery(Of Categories) = context.Categories

            For Each category As Categories In _
                categoryQuery.Execute(MergeOption.AppendOnly)
                Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                    category.CategoryID, category.CategoryName)
            Next
        End Using
    End Sub
End Class
```

### <a name="entityclient"></a><span data-ttu-id="16cc6-147">EntityClient</span><span class="sxs-lookup"><span data-stu-id="16cc6-147">EntityClient</span></span>
<span data-ttu-id="16cc6-148">O código neste exemplo usa um <xref:System.Data.EntityClient.EntityCommand> para executar uma consulta Entity SQL.</span><span class="sxs-lookup"><span data-stu-id="16cc6-148">The code in this example uses an <xref:System.Data.EntityClient.EntityCommand> to execute an Entity SQL query.</span></span> <span data-ttu-id="16cc6-149">Esta consulta retorna uma lista de registros que representam instâncias do tipo de entidade Categories.</span><span class="sxs-lookup"><span data-stu-id="16cc6-149">This query returns a list of records that represent instances of the Categories entity type.</span></span> <span data-ttu-id="16cc6-150">Um <xref:System.Data.EntityClient.EntityDataReader> é usado para acessar os registros de dados no conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="16cc6-150">An <xref:System.Data.EntityClient.EntityDataReader> is used to access data records in the result set.</span></span> <span data-ttu-id="16cc6-151">Para obter mais informações, consulte [provedor EntityClient para Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span><span class="sxs-lookup"><span data-stu-id="16cc6-151">For more information, see [EntityClient Provider for the Entity Framework](../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md).</span></span>

```csharp
using System;
using System.Data;
using System.Data.Common;
using System.Data.EntityClient;
using NorthwindModel;

class EntityClientSample
{
    public static void ExecuteQuery()
    {
        string queryString =
            @"SELECT c.CategoryID, c.CategoryName 
                FROM NorthwindEntities.Categories AS c";

        using (EntityConnection conn =
            new EntityConnection("name=NorthwindEntities"))
        {
            try
            {
                conn.Open();
                using (EntityCommand query = new EntityCommand(queryString, conn))
                {
                    using (DbDataReader rdr = 
                        query.ExecuteReader(CommandBehavior.SequentialAccess))
                    {
                        while (rdr.Read())
                        {
                            Console.WriteLine("\t{0}\t{1}", rdr[0], rdr[1]);
                        }
                    }
                }
            }
            catch (Exception ex)
            {
                Console.WriteLine(ex.Message);
            }
        }
    }
}
```

```vb
Option Explicit On
Option Strict On

Imports System
Imports System.Data
Imports System.Data.Common
Imports System.Data.EntityClient
Imports NorthwindModel

Class EntityClientSample
    Public Shared Sub ExecuteQuery()
        Dim queryString As String = _
            "SELECT c.CategoryID, c.CategoryName " & _
                "FROM NorthwindEntities.Categories AS c"

        Using conn As EntityConnection = _
            New EntityConnection("name=NorthwindEntities")

            Try
                conn.Open()
                Using query As EntityCommand = _
                New EntityCommand(queryString, conn)
                    Using rdr As DbDataReader = _
                        query.ExecuteReader(CommandBehavior.SequentialAccess)
                        While rdr.Read()
                            Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                                              rdr(0), rdr(1))
                        End While
                    End Using
                End Using
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
        End Using 
    End Sub
End Class
```

## <a name="linq-to-sql"></a><span data-ttu-id="16cc6-152">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="16cc6-152">LINQ to SQL</span></span>
<span data-ttu-id="16cc6-153">O código neste exemplo usa uma consulta LINQ para retornar dados como objetos Categories, que são projetados como um tipo anônimo que contém somente as propriedades CategoryID e CategoryName.</span><span class="sxs-lookup"><span data-stu-id="16cc6-153">The code in this example uses a LINQ query to return data as Categories objects, which are projected as an anonymous type that contains only the CategoryID and CategoryName properties.</span></span> <span data-ttu-id="16cc6-154">Este exemplo é baseado no contexto de dados do Northwind.</span><span class="sxs-lookup"><span data-stu-id="16cc6-154">This example is based on the Northwind data context.</span></span> <span data-ttu-id="16cc6-155">Para saber mais, confira a [Introdução](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="16cc6-155">For more information, see [Getting Started](../../../../docs/framework/data/adonet/sql/linq/getting-started.md).</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Northwind;

    class LinqSqlSample
    {
        public static void ExecuteQuery()
        {
            using (NorthwindDataContext db = new NorthwindDataContext())
            {
                try
                {
                    var query = from category in db.Categories
                                select new
                                {
                                    categoryID = category.CategoryID,
                                    categoryName = category.CategoryName
                                };

                    foreach (var categoryInfo in query)
                    {
                        Console.WriteLine("vbTab {0} vbTab {1}",
                            categoryInfo.categoryID, categoryInfo.categoryName);
                    }
                }
                catch (Exception ex)
                {
                    Console.WriteLine(ex.Message);
                }
            }
        }
    }
```

```vb
Option Explicit On
Option Strict On

Imports System
Imports System.Collections.Generic
Imports System.Linq
Imports System.Text
Imports Northwind

Class LinqSqlSample
    Public Shared Sub ExecuteQuery()
        Using db As NorthwindDataContext = New NorthwindDataContext()
            Try
                Dim query = From category In db.Categories _
                                Select New With _
                                { _
                                    .categoryID = category.CategoryID, _
                                    .categoryName = category.CategoryName _
                                }

                For Each categoryInfo In query
                    Console.WriteLine(vbTab & "{0}" & vbTab & "{1}", _
                            categoryInfo.categoryID, categoryInfo.categoryName)
                Next
            Catch ex As Exception
                Console.WriteLine(ex.Message)
            End Try
            End Using 
    End Sub
End Class
```

## <a name="see-also"></a><span data-ttu-id="16cc6-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16cc6-156">See also</span></span>
 <span data-ttu-id="16cc6-157">[ADO.NET Overview](../../../../docs/framework/data/adonet/ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="16cc6-157">[ADO.NET Overview](../../../../docs/framework/data/adonet/ado-net-overview.md)</span></span>  
 <span data-ttu-id="16cc6-158">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="16cc6-158">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>  
 [<span data-ttu-id="16cc6-159">Criando aplicativos de dados</span><span class="sxs-lookup"><span data-stu-id="16cc6-159">Creating Data Applications</span></span>](http://msdn.microsoft.com/library/ab334d5f-4f49-4346-bce0-3325d6130b3e)  
 [<span data-ttu-id="16cc6-160">Consultando um modelo de dados de entidade (Entity Framework tarefas)</span><span class="sxs-lookup"><span data-stu-id="16cc6-160">Querying an Entity Data Model (Entity Framework Tasks)</span></span>](http://msdn.microsoft.com/187f1caa-e4d3-4e31-bd99-5d5c2b329c77)  
 [<span data-ttu-id="16cc6-161">Como: executar uma consulta que retorna objetos de tipo anônimo</span><span class="sxs-lookup"><span data-stu-id="16cc6-161">How to: Execute a Query that Returns Anonymous Type Objects</span></span>](http://msdn.microsoft.com/3b264025-e911-4d73-90ce-992d2b9d189d)  
 <span data-ttu-id="16cc6-162">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="16cc6-162">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>  