---
title: Usando System. Transactions no ASP.NET
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1982c300-7ea6-4242-95ed-dc28ccfacac9
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 321489a2b32bafe4a73f56e0a5dba20f5661bdc2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="using-systemtransactions-in-aspnet"></a><span data-ttu-id="dca5f-102">Usando System. Transactions no ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dca5f-102">Using System.Transactions in ASP.NET</span></span>
<span data-ttu-id="dca5f-103">Este tópico descreve como você pode usar com êxito <xref:System.Transactions> dentro de um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dca5f-103">This topic describes how you can successfully use <xref:System.Transactions> inside an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application.</span></span>  
  
## <a name="enable-distributedtransactionpermission-in-aspnet"></a><span data-ttu-id="dca5f-104">Habilitar DistributedTransactionPermission no ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dca5f-104">Enable DistributedTransactionPermission in ASP.NET</span></span>  
 <span data-ttu-id="dca5f-105"><xref:System.Transactions>oferece suporte a chamadores parcialmente confiáveis e é marcado com o **AllowPartiallyTrustedCallers** atributo (APTCA).</span><span class="sxs-lookup"><span data-stu-id="dca5f-105"><xref:System.Transactions> supports partially trusted callers and is marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="dca5f-106">Níveis de confiança para <xref:System.Transactions> são definidos com base nos tipos de recursos (por exemplo, memória do sistema, recursos compartilhados de todo o processo, recursos de todo o sistema e outros recursos), que <xref:System.Transactions> expõe e o nível de confiança deve ser necessária para acessar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="dca5f-106">The trust levels for <xref:System.Transactions> are defined based on the types of resources, (for example, system memory, shared process-wide resources, system-wide resources, and other resources), that <xref:System.Transactions> exposes and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="dca5f-107">Em um ambiente de confiança parcial, um assembly de confiança total não pode usar somente as transações dentro do domínio de aplicativo (nesse caso, o único recurso que está sendo protegido é a memória do sistema), a menos que ele recebe o <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="dca5f-107">In a partial-trust environment, a non-full trust assembly can only use transactions within the Application Domain (in this case, the only resource being protected is system memory), unless it is granted the <xref:System.Transactions.DistributedTransactionPermission>.</span></span>  
  
 <span data-ttu-id="dca5f-108"><xref:System.Transactions.DistributedTransactionPermission>é solicitada sempre que o gerenciamento de transações será escalonado para ser gerenciado por Microsoft Distributed Transaction coordenador (MSDTC).</span><span class="sxs-lookup"><span data-stu-id="dca5f-108"><xref:System.Transactions.DistributedTransactionPermission> is demanded whenever transaction management is escalated to be managed by the Microsoft Distributed Transaction Coordinator (MSDTC).</span></span> <span data-ttu-id="dca5f-109">Esse tipo de cenário usa recursos de todo o processo e especialmente um recurso global, que é o espaço reservado no log do MSDTC.</span><span class="sxs-lookup"><span data-stu-id="dca5f-109">This kind of scenario utilizes process-wide resources and particularly a global resource, which is the reserved space in the MSDTC log.</span></span> <span data-ttu-id="dca5f-110">Um exemplo dessa utilização é uma Web front-end para um banco de dados ou um aplicativo que usa um banco de dados como parte dos serviços que ele fornece.</span><span class="sxs-lookup"><span data-stu-id="dca5f-110">An example of this usage is a Web front-end to a database or an application that uses a database as part of the services it provides.</span></span>  
  
 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]<span data-ttu-id="dca5f-111">tem seu próprio conjunto de níveis de confiança e associa um conjunto específico de permissões esses níveis de confiança por meio de arquivos de política.</span><span class="sxs-lookup"><span data-stu-id="dca5f-111"> has its own set of trust levels and associates a specific set of permissions with these trust levels through policy files.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="dca5f-112">[Níveis de confiança ASP.NET e arquivos de política](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1).</span><span class="sxs-lookup"><span data-stu-id="dca5f-112"> [ASP.NET Trust Levels and Policy Files](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1).</span></span> <span data-ttu-id="dca5f-113">Quando você instala o SDK do Windows, nenhum padrão inicialmente [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] arquivos de política associados a <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="dca5f-113">When you initially install the Windows SDK, none of the default [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] policy files are associated with the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="dca5f-114">Assim, quando sua transação em um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo será escalonado para ser gerenciado pelo MSDTC, o escalonamento falhará com um <xref:System.Security.SecurityException> após exigindo a <xref:System.Transactions.DistributedTransactionPermission>.</span><span class="sxs-lookup"><span data-stu-id="dca5f-114">As such, when your transaction in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application is escalated to be managed by the MSDTC, the escalation fails with a <xref:System.Security.SecurityException> upon demanding the <xref:System.Transactions.DistributedTransactionPermission>.</span></span> <span data-ttu-id="dca5f-115">Para habilitar o escalonamento de transação em um [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] ambiente de confiança parcial, você deve conceder a <xref:System.Transactions.DistributedTransactionPermission> nos níveis de confiança padrão mesmo que os do <xref:System.Data.SqlClient.SqlClientPermission>.</span><span class="sxs-lookup"><span data-stu-id="dca5f-115">To enable transaction escalation in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] partial trust environment, you should grant the <xref:System.Transactions.DistributedTransactionPermission> in the same default trust levels as those of <xref:System.Data.SqlClient.SqlClientPermission>.</span></span> <span data-ttu-id="dca5f-116">Você pode configurar seu próprio arquivo de nível e a política de confiança personalizado para dar suporte a isso, ou você pode modificar os arquivos de política padrão, que são **Web_hightrust** e **Web_mediumtrust**.</span><span class="sxs-lookup"><span data-stu-id="dca5f-116">You can either configure your own custom trust level and policy file to support this, or you can modify the default policy files, which are **Web_hightrust.config** and **Web_mediumtrust.config**.</span></span>  
  
 <span data-ttu-id="dca5f-117">Para modificar os arquivos de política, adicione um **SecurityClass** elemento para **DistributedTransactionPermission** para o **SecurityClasses** elemento sob o  **PolicyLevel** elemento e adicione um correspondente **IPermission** elemento sob o [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** para System. Transactions.</span><span class="sxs-lookup"><span data-stu-id="dca5f-117">To modify the policy files, add a **SecurityClass** element for **DistributedTransactionPermission** to the **SecurityClasses** element under the **PolicyLevel** element and add a corresponding **IPermission** element under the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] **NamedPermissionSet** for System.Transactions.</span></span> <span data-ttu-id="dca5f-118">O arquivo de configuração a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="dca5f-118">The following configuration file demonstrates this.</span></span>  
  
```xml  
<SecurityClasses>  
   <SecurityClass Name="DistributedTransactionPermission" Description="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
...  
</SecurityClasses>  
  
<PermissionSet  
  class="NamedPermissionSet"  
  version="1"  
  Name="ASP.Net">  
     <IPermission  
        class="System.Transactions.DistributedTransactionPermission, System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
        version="1"  
        Unrestricted="true"  
     />  
...  
</PermissionSet>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="dca5f-119">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] política de segurança, consulte [securityPolicy Element (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba).</span><span class="sxs-lookup"><span data-stu-id="dca5f-119"> [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] security policy, see [securityPolicy Element (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba).</span></span>  
  
## <a name="dynamic-compilation"></a><span data-ttu-id="dca5f-120">Compilação dinâmica</span><span class="sxs-lookup"><span data-stu-id="dca5f-120">Dynamic Compilation</span></span>  
 <span data-ttu-id="dca5f-121">Se você deseja importar e usar <xref:System.Transactions> em uma [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo é compilado dinamicamente no access, você deve colocar uma referência para o <xref:System.Transactions> assembly no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="dca5f-121">If you want to import and use <xref:System.Transactions> in an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application that is dynamically compiled on access, you should place a reference to the <xref:System.Transactions> assembly in the configuration file.</span></span> <span data-ttu-id="dca5f-122">Especificamente, a referência deve ser adicionada sob o **compilação**/**assemblies** seção da raiz padrão **Web. config** arquivo de configuração, ou um arquivo de configuração do aplicativo Web específico.</span><span class="sxs-lookup"><span data-stu-id="dca5f-122">Specifically, the reference should be added under the **compilation**/**assemblies** section of the default root **Web.config** configuration file, or a specific Web application's configuration file.</span></span> <span data-ttu-id="dca5f-123">O exemplo a seguir demonstra isso.</span><span class="sxs-lookup"><span data-stu-id="dca5f-123">The following example demonstrates this.</span></span>  
  
```xml  
<configuration>  
   <system.web>  
      <compilation>  
         <assemblies>  
      <add assembly="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
         </assemblies>  
      </compilation>  
   </system.web>  
</configuration>  
```  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="dca5f-124">[adicionar elemento para assemblies de compilação (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/602197e8-108d-4249-b752-ba2a318f75e4).</span><span class="sxs-lookup"><span data-stu-id="dca5f-124"> [add Element for assemblies for compilation (ASP.NET Settings Schema)](http://msdn.microsoft.com/en-us/602197e8-108d-4249-b752-ba2a318f75e4).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca5f-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dca5f-125">See Also</span></span>  
 [<span data-ttu-id="dca5f-126">Níveis de confiança ASP.NET e arquivos de política</span><span class="sxs-lookup"><span data-stu-id="dca5f-126">ASP.NET Trust Levels and Policy Files</span></span>](http://msdn.microsoft.com/library/f897c794-10d3-414c-86b7-59b66564bbf1)  
 [<span data-ttu-id="dca5f-127">securityPolicy Element (ASP.NET Settings Schema)</span><span class="sxs-lookup"><span data-stu-id="dca5f-127">securityPolicy Element (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/en-us/469d8d22-d263-46bb-8400-40d8d027faba)  
 [<span data-ttu-id="dca5f-128">Escalonamento de bloqueios de gerenciamento de transação</span><span class="sxs-lookup"><span data-stu-id="dca5f-128">Transaction Management Escalation</span></span>](../../../../docs/framework/data/transactions/transaction-management-escalation.md)