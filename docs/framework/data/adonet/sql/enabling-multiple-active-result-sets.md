---
title: "Habilitando vários conjuntos de resultados ativos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1d39d1666f63d7d6f7a6154a124280486c3fccce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="enabling-multiple-active-result-sets"></a><span data-ttu-id="8670f-102">Habilitando vários conjuntos de resultados ativos</span><span class="sxs-lookup"><span data-stu-id="8670f-102">Enabling Multiple Active Result Sets</span></span>
<span data-ttu-id="8670f-103">O Multiple Active Result Sets (MARS) é um recurso que funciona com o SQL Server para permitir a execução de vários lotes em uma única conexão.</span><span class="sxs-lookup"><span data-stu-id="8670f-103">Multiple Active Result Sets (MARS) is a feature that works with SQL Server to allow the execution of multiple batches on a single connection.</span></span> <span data-ttu-id="8670f-104">Quando MARS está ativado para uso com o SQL Server, cada objeto de comando usado adiciona uma sessão à conexão.</span><span class="sxs-lookup"><span data-stu-id="8670f-104">When MARS is enabled for use with SQL Server, each command object used adds a session to the connection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8670f-105">Uma sessão única de MARS abre uma conexão lógica para MARS para uso e, em seguida, uma conexão lógica para cada comando ativo.</span><span class="sxs-lookup"><span data-stu-id="8670f-105">A single MARS session opens one logical connection for MARS to use and then one logical connection for each active command.</span></span>  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a><span data-ttu-id="8670f-106">Habilitando e desabilitando MARS na cadeia de conexão</span><span class="sxs-lookup"><span data-stu-id="8670f-106">Enabling and Disabling MARS in the Connection String</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8670f-107">As seguintes cadeias de caracteres de conexão usam o exemplo **AdventureWorks** incluído com o SQL Server do banco de dados.</span><span class="sxs-lookup"><span data-stu-id="8670f-107">The following connection strings use the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="8670f-108">As cadeias de conexão fornecidas supõem que o banco de dados esteja instalado em um servidor chamado MSSQL1.</span><span class="sxs-lookup"><span data-stu-id="8670f-108">The connection strings provided assume that the database is installed on a server named MSSQL1.</span></span> <span data-ttu-id="8670f-109">Modifique a cadeia de conexão conforme o necessário para seu ambiente.</span><span class="sxs-lookup"><span data-stu-id="8670f-109">Modify the connection string as necessary for your environment.</span></span>  
  
 <span data-ttu-id="8670f-110">O recurso MARS é desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="8670f-110">The MARS feature is disabled by default.</span></span> <span data-ttu-id="8670f-111">Ele pode ser ativado adicionando o par de palavras-chave de "MultipleActiveResultSets=True" à cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="8670f-111">It can be enabled by adding the "MultipleActiveResultSets=True" keyword pair to your connection string.</span></span> <span data-ttu-id="8670f-112">"Verdadeiro" é o único valor válido para habilitar o MARS.</span><span class="sxs-lookup"><span data-stu-id="8670f-112">"True" is the only valid value for enabling MARS.</span></span> <span data-ttu-id="8670f-113">O exemplo a seguir demonstra como conectar-se a uma instância do SQL Server e como especificar que o MARS deve ser habilitado.</span><span class="sxs-lookup"><span data-stu-id="8670f-113">The following example demonstrates how to connect to an instance of SQL Server and how to specify that MARS should be enabled.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 <span data-ttu-id="8670f-114">Você pode desabilitar MARS adicionando o par de palavras-chave de "MultipleActiveResultSets=False" à cadeia de conexão.</span><span class="sxs-lookup"><span data-stu-id="8670f-114">You can disable MARS by adding the "MultipleActiveResultSets=False" keyword pair to your connection string.</span></span> <span data-ttu-id="8670f-115">"Falso" é o único valor válido para desabilitar MARS.</span><span class="sxs-lookup"><span data-stu-id="8670f-115">"False" is the only valid value for disabling MARS.</span></span> <span data-ttu-id="8670f-116">A cadeia de conexão a seguir demonstra como desabilitar MARS.</span><span class="sxs-lookup"><span data-stu-id="8670f-116">The following connection string demonstrates how to disable MARS.</span></span>  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a><span data-ttu-id="8670f-117">Considerações especiais ao usar MARS</span><span class="sxs-lookup"><span data-stu-id="8670f-117">Special Considerations When Using MARS</span></span>  
 <span data-ttu-id="8670f-118">Geralmente, os aplicativos existentes não devem precisar de nenhuma alteração para usar uma conexão habilitada para MARS.</span><span class="sxs-lookup"><span data-stu-id="8670f-118">In general, existing applications should not need modification to use a MARS-enabled connection.</span></span> <span data-ttu-id="8670f-119">Entretanto, se você quiser usar os recursos do MARS em seus aplicativos, deverá compreender as seguintes considerações especiais.</span><span class="sxs-lookup"><span data-stu-id="8670f-119">However, if you wish to use MARS features in your applications, you should understand the following special considerations.</span></span>  
  
### <a name="statement-interleaving"></a><span data-ttu-id="8670f-120">Interpolação de instrução</span><span class="sxs-lookup"><span data-stu-id="8670f-120">Statement Interleaving</span></span>  
 <span data-ttu-id="8670f-121">As operações de MARS são executadas de maneira síncrona no servidor.</span><span class="sxs-lookup"><span data-stu-id="8670f-121">MARS operations execute synchronously on the server.</span></span> <span data-ttu-id="8670f-122">A interpolação das instruções SELECT e BULK INSERT é permitida.</span><span class="sxs-lookup"><span data-stu-id="8670f-122">Statement interleaving of SELECT and BULK INSERT statements is allowed.</span></span> <span data-ttu-id="8670f-123">No entanto, as instruções da linguagem DML e de DDL (linguagem de definição de dados) são executadas atomicamente.</span><span class="sxs-lookup"><span data-stu-id="8670f-123">However, data manipulation language (DML) and data definition language (DDL) statements execute atomically.</span></span> <span data-ttu-id="8670f-124">As instruções que tentarem ser executadas enquanto um lote atômico é executado serão bloqueadas.</span><span class="sxs-lookup"><span data-stu-id="8670f-124">Any statements attempting to execute while an atomic batch is executing are blocked.</span></span> <span data-ttu-id="8670f-125">A execução paralela no servidor não é um recurso do MARS.</span><span class="sxs-lookup"><span data-stu-id="8670f-125">Parallel execution at the server is not a MARS feature.</span></span>  
  
 <span data-ttu-id="8670f-126">Se dois lotes forem enviados em uma conexão de MARS, um deles contendo uma instrução SELECT e o outro contendo uma instrução de DML, o DML pode iniciar a execução dentro da execução da instrução SELECT.</span><span class="sxs-lookup"><span data-stu-id="8670f-126">If two batches are submitted under a MARS connection, one of them containing a SELECT statement, the other containing a DML statement, the DML can begin execution within execution of the SELECT statement.</span></span> <span data-ttu-id="8670f-127">No entanto, a instrução de DML deve ser executada para ser concluída antes de a instrução SELECT poder continuar.</span><span class="sxs-lookup"><span data-stu-id="8670f-127">However, the DML statement must run to completion before the SELECT statement can make progress.</span></span> <span data-ttu-id="8670f-128">Se as duas instruções estiverem em execução na mesma transação, as alterações feitas por uma instrução de DML após a declaração SELECT ter começado a execução não serão visíveis para a operação de leitura.</span><span class="sxs-lookup"><span data-stu-id="8670f-128">If both statements are running under the same transaction, any changes made by a DML statement after the SELECT statement has started execution are not visible to the read operation.</span></span>  
  
 <span data-ttu-id="8670f-129">Uma instrução WAITFOR dentro de uma instrução SELECT não produz a transação enquanto aguarda, ou seja, até que a primeira linha seja gerada.</span><span class="sxs-lookup"><span data-stu-id="8670f-129">A WAITFOR statement inside a SELECT statement does not yield the transaction while it is waiting, that is, until the first row is produced.</span></span> <span data-ttu-id="8670f-130">Isso significa que nenhum outro lote pode ser executado dentro da mesma conexão enquanto uma instrução WAITFOR estiver aguardando.</span><span class="sxs-lookup"><span data-stu-id="8670f-130">This implies that no other batches can execute within the same connection while a WAITFOR statement is waiting.</span></span>  
  
### <a name="mars-session-cache"></a><span data-ttu-id="8670f-131">Cache de sessão de MARS</span><span class="sxs-lookup"><span data-stu-id="8670f-131">MARS Session Cache</span></span>  
 <span data-ttu-id="8670f-132">Quando uma conexão é aberta com o MARS habilitado, uma sessão lógica é criada, o que adiciona uma sobrecarga adicional.</span><span class="sxs-lookup"><span data-stu-id="8670f-132">When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead.</span></span> <span data-ttu-id="8670f-133">Para minimizar a sobrecarga e aumentar o desempenho, **SqlClient** armazena em cache a sessão MARS dentro de uma conexão.</span><span class="sxs-lookup"><span data-stu-id="8670f-133">To minimize overhead and enhance performance, **SqlClient** caches the MARS session within a connection.</span></span> <span data-ttu-id="8670f-134">O cache contém no máximo 10 sessões de MARS.</span><span class="sxs-lookup"><span data-stu-id="8670f-134">The cache contains at most 10 MARS sessions.</span></span> <span data-ttu-id="8670f-135">Este valor não é ajustável pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="8670f-135">This value is not user adjustable.</span></span> <span data-ttu-id="8670f-136">Se o limite de sessão for alcançado, uma nova sessão será criada. Um erro não será gerado.</span><span class="sxs-lookup"><span data-stu-id="8670f-136">If the session limit is reached, a new session is created—an error is not generated.</span></span> <span data-ttu-id="8670f-137">O cache e as sessões contidas nela são por conexão; não são compartilhados entre as conexões.</span><span class="sxs-lookup"><span data-stu-id="8670f-137">The cache and sessions contained in it are per-connection; they are not shared across connections.</span></span> <span data-ttu-id="8670f-138">Quando uma sessão é lançada, é retornada para o pool a menos que o limite superior do pool tenha sido alcançado.</span><span class="sxs-lookup"><span data-stu-id="8670f-138">When a session is released, it is returned to the pool unless the pool's upper limit has been reached.</span></span> <span data-ttu-id="8670f-139">Se o pool do cache estiver concluído, a sessão será fechada.</span><span class="sxs-lookup"><span data-stu-id="8670f-139">If the cache pool is full, the session is closed.</span></span> <span data-ttu-id="8670f-140">As sessões do MARS não expiram.</span><span class="sxs-lookup"><span data-stu-id="8670f-140">MARS sessions do not expire.</span></span> <span data-ttu-id="8670f-141">Elas somente são limpas quando o objeto de conexão é descartado.</span><span class="sxs-lookup"><span data-stu-id="8670f-141">They are only cleaned up when the connection object is disposed.</span></span> <span data-ttu-id="8670f-142">O cache de sessão de MARS não é pré-carregado.</span><span class="sxs-lookup"><span data-stu-id="8670f-142">The MARS session cache is not preloaded.</span></span> <span data-ttu-id="8670f-143">Ele é carregado quando o aplicativo exige mais sessões.</span><span class="sxs-lookup"><span data-stu-id="8670f-143">It is loaded as the application requires more sessions.</span></span>  
  
### <a name="thread-safety"></a><span data-ttu-id="8670f-144">Segurança de threads</span><span class="sxs-lookup"><span data-stu-id="8670f-144">Thread Safety</span></span>  
 <span data-ttu-id="8670f-145">As operações de MARS não são thread-safe.</span><span class="sxs-lookup"><span data-stu-id="8670f-145">MARS operations are not thread-safe.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="8670f-146">Pool de conexões</span><span class="sxs-lookup"><span data-stu-id="8670f-146">Connection Pooling</span></span>  
 <span data-ttu-id="8670f-147">As conexões habilitadas para MARS são agrupadas como qualquer outra conexão.</span><span class="sxs-lookup"><span data-stu-id="8670f-147">MARS-enabled connections are pooled like any other connection.</span></span> <span data-ttu-id="8670f-148">Se um aplicativo abrir duas conexões, uma com MARS habilitado e outra com MARS desabilitado, as duas conexões estarão em pools separados.</span><span class="sxs-lookup"><span data-stu-id="8670f-148">If an application opens two connections, one with MARS enabled and one with MARS disabled, the two connections are in separate pools.</span></span> <span data-ttu-id="8670f-149">Para obter mais informações, consulte [Pooling de Conexão do SQL Server (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span><span class="sxs-lookup"><span data-stu-id="8670f-149">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
### <a name="sql-server-batch-execution-environment"></a><span data-ttu-id="8670f-150">Ambiente de execução em lotes do SQL Server</span><span class="sxs-lookup"><span data-stu-id="8670f-150">SQL Server Batch Execution Environment</span></span>  
 <span data-ttu-id="8670f-151">Quando uma conexão é aberta, um ambiente padrão é definido.</span><span class="sxs-lookup"><span data-stu-id="8670f-151">When a connection is opened, a default environment is defined.</span></span> <span data-ttu-id="8670f-152">Esse ambiente é, em seguida, copiado em uma sessão lógica do MARS.</span><span class="sxs-lookup"><span data-stu-id="8670f-152">This environment is then copied into a logical MARS session.</span></span>  
  
 <span data-ttu-id="8670f-153">O ambiente de execução em lotes inclui os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="8670f-153">The batch execution environment includes the following components:</span></span>  
  
-   <span data-ttu-id="8670f-154">Opções de conjunto (por exemplo, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span><span class="sxs-lookup"><span data-stu-id="8670f-154">Set options (for example, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span></span>  
  
-   <span data-ttu-id="8670f-155">Contexto de segurança (usuário/função do aplicativo)</span><span class="sxs-lookup"><span data-stu-id="8670f-155">Security context (user/application role)</span></span>  
  
-   <span data-ttu-id="8670f-156">Contexto de banco de dados (o banco de dados atual)</span><span class="sxs-lookup"><span data-stu-id="8670f-156">Database context (current database)</span></span>  
  
-   <span data-ttu-id="8670f-157">Variáveis de estado de execução (por exemplo, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span><span class="sxs-lookup"><span data-stu-id="8670f-157">Execution state variables (for example, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span></span>  
  
-   <span data-ttu-id="8670f-158">Tabelas temporárias de nível superior</span><span class="sxs-lookup"><span data-stu-id="8670f-158">Top-level temporary tables</span></span>  
  
 <span data-ttu-id="8670f-159">Com o MARS, um ambiente padrão de execução está associado a uma conexão.</span><span class="sxs-lookup"><span data-stu-id="8670f-159">With MARS, a default execution environment is associated to a connection.</span></span> <span data-ttu-id="8670f-160">Cada novo lote que inicia sendo executado em uma determinada conexão recebe uma cópia do ambiente padrão.</span><span class="sxs-lookup"><span data-stu-id="8670f-160">Every new batch that starts executing under a given connection receives a copy of the default environment.</span></span> <span data-ttu-id="8670f-161">Sempre que o código é executado em um determinado lote, todas as alterações feitas ao ambiente são do escopo do lote específico.</span><span class="sxs-lookup"><span data-stu-id="8670f-161">Whenever code is executed under a given batch, all changes made to the environment are scoped to the specific batch.</span></span> <span data-ttu-id="8670f-162">Quando a execução estiver concluída, as configurações de execução serão copiadas no ambiente padrão.</span><span class="sxs-lookup"><span data-stu-id="8670f-162">Once execution finishes, the execution settings are copied into the default environment.</span></span> <span data-ttu-id="8670f-163">No caso de um único lote que emite vários comandos para serem executados em sequência na mesma transação, a semântica é a mesma que as expostas por conexões que envolvem clientes ou servidores anteriores.</span><span class="sxs-lookup"><span data-stu-id="8670f-163">In the case of a single batch issuing several commands to be executed sequentially under the same transaction, semantics are the same as those exposed by connections involving earlier clients or servers.</span></span>  
  
### <a name="parallel-execution"></a><span data-ttu-id="8670f-164">Execução paralela</span><span class="sxs-lookup"><span data-stu-id="8670f-164">Parallel Execution</span></span>  
 <span data-ttu-id="8670f-165">O MARS não é criado para remover todos os requisitos para várias conexões em um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8670f-165">MARS is not designed to remove all requirements for multiple connections in an application.</span></span> <span data-ttu-id="8670f-166">Se um aplicativo precisar de execução paralela verdadeira de comandos em um servidor, várias conexões deverão ser usadas.</span><span class="sxs-lookup"><span data-stu-id="8670f-166">If an application needs true parallel execution of commands against a server, multiple connections should be used.</span></span>  
  
 <span data-ttu-id="8670f-167">Por exemplo, considere o seguinte cenário.</span><span class="sxs-lookup"><span data-stu-id="8670f-167">For example, consider the following scenario.</span></span> <span data-ttu-id="8670f-168">Dois objetos de comando são criados, um para processar um conjunto de resultados e outro para atualizar dados; eles compartilham uma conexão comum através do MARS.</span><span class="sxs-lookup"><span data-stu-id="8670f-168">Two command objects are created, one for processing a result set and another for updating data; they share a common connection via MARS.</span></span> <span data-ttu-id="8670f-169">Nesse cenário, o `Transaction`.`Commit`</span><span class="sxs-lookup"><span data-stu-id="8670f-169">In this scenario, the `Transaction`.`Commit`</span></span> <span data-ttu-id="8670f-170">Falha na atualização até que todos os resultados foram lidos no primeiro objeto de comando, gerando a seguinte exceção:</span><span class="sxs-lookup"><span data-stu-id="8670f-170">fails on the update until all the results have been read on the first command object, yielding the following exception:</span></span>  
  
 <span data-ttu-id="8670f-171">Mensagem: Contexto de transação em uso por outra sessão.</span><span class="sxs-lookup"><span data-stu-id="8670f-171">Message: Transaction context in use by another session.</span></span>  
  
 <span data-ttu-id="8670f-172">Origem: provedor de dados .Net SqlClient</span><span class="sxs-lookup"><span data-stu-id="8670f-172">Source: .Net SqlClient Data Provider</span></span>  
  
 <span data-ttu-id="8670f-173">Esperado: (null)</span><span class="sxs-lookup"><span data-stu-id="8670f-173">Expected: (null)</span></span>  
  
 <span data-ttu-id="8670f-174">Recebido: System.Data.SqlClient.SqlException</span><span class="sxs-lookup"><span data-stu-id="8670f-174">Received: System.Data.SqlClient.SqlException</span></span>  
  
 <span data-ttu-id="8670f-175">Há três opções para tratar esse cenário:</span><span class="sxs-lookup"><span data-stu-id="8670f-175">There are three options for handling this scenario:</span></span>  
  
1.  <span data-ttu-id="8670f-176">Inicie a transação após o leitor ter sido criado, de modo que não faça parte da transação.</span><span class="sxs-lookup"><span data-stu-id="8670f-176">Start the transaction after the reader is created, so that it is not part of the transaction.</span></span> <span data-ttu-id="8670f-177">Cada atualização em seguida se torna sua própria transação.</span><span class="sxs-lookup"><span data-stu-id="8670f-177">Every update then becomes its own transaction.</span></span>  
  
2.  <span data-ttu-id="8670f-178">Confirme todo o trabalho depois que o leitor for fechado.</span><span class="sxs-lookup"><span data-stu-id="8670f-178">Commit all work after the reader is closed.</span></span> <span data-ttu-id="8670f-179">Isso tem o potencial para um lote significativo de atualizações.</span><span class="sxs-lookup"><span data-stu-id="8670f-179">This has the potential for a substantial batch of updates.</span></span>  
  
3.  <span data-ttu-id="8670f-180">Não use MARS; em vez disso, use uma conexão separada para cada objeto de comando, da mesma forma que você faria antes do MARS.</span><span class="sxs-lookup"><span data-stu-id="8670f-180">Don't use MARS; instead use a separate connection for each command object as you would have before MARS.</span></span>  
  
### <a name="detecting-mars-support"></a><span data-ttu-id="8670f-181">Detectando o suporte de MARS</span><span class="sxs-lookup"><span data-stu-id="8670f-181">Detecting MARS Support</span></span>  
 <span data-ttu-id="8670f-182">Um aplicativo pode verificar o suporte de MARS lendo o valor `SqlConnection.ServerVersion`.</span><span class="sxs-lookup"><span data-stu-id="8670f-182">An application can check for MARS support by reading the `SqlConnection.ServerVersion` value.</span></span> <span data-ttu-id="8670f-183">O número principal deve ser 9 para o SQL Server 2005 e 10 para o SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="8670f-183">The major number should be 9 for SQL Server 2005 and 10 for SQL Server 2008.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8670f-184">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8670f-184">See Also</span></span>  
 [<span data-ttu-id="8670f-185">Vários conjuntos de resultados ativos (MARS)</span><span class="sxs-lookup"><span data-stu-id="8670f-185">Multiple Active Result Sets (MARS)</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 <span data-ttu-id="8670f-186">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="8670f-186">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>