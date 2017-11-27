---
title: "Funções de hospedagem CLR reprovadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- .NET Framework 1.1, hosting global static functions
- global static functions [.NET Framework hosting], version 2.0
- .NET Framework 2.0, hosting global static functions
- hosting global static functions [.NET Framework], version 2.0
ms.assetid: 91fbbb35-e543-4814-b806-371cebae8c5a
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9530fecb4f2ca6f59d165e49c282320966fd2fa8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="deprecated-clr-hosting-functions"></a><span data-ttu-id="92ec0-102">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="92ec0-102">Deprecated CLR Hosting Functions</span></span>
<span data-ttu-id="92ec0-103">Esta seção descreve as funções estáticas globais não gerenciadas usados por versões anteriores da API de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="92ec0-103">This section describes the unmanaged global static functions that earlier versions of the hosting API used.</span></span>  
  
 <span data-ttu-id="92ec0-104">Com exceção das funções de infraestrutura (`_Cor*` funções), que são usados apenas pelo .NET Framework, essas funções foram preteridas a [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92ec0-104">With the exception of the infrastructure functions (`_Cor*` functions), which are used only by the .NET Framework, these functions have been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="activation-functions"></a><span data-ttu-id="92ec0-105">Funções de ativação</span><span class="sxs-lookup"><span data-stu-id="92ec0-105">Activation functions</span></span>  
 [<span data-ttu-id="92ec0-106">Função ClrCreateManagedInstance</span><span class="sxs-lookup"><span data-stu-id="92ec0-106">ClrCreateManagedInstance Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/clrcreatemanagedinstance-function.md)  
 <span data-ttu-id="92ec0-107">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-107">Deprecated.</span></span> <span data-ttu-id="92ec0-108">Cria uma instância do tipo gerenciado especificado.</span><span class="sxs-lookup"><span data-stu-id="92ec0-108">Creates an instance of the specified managed type.</span></span>  
  
 [<span data-ttu-id="92ec0-109">Função CoInitializeCor</span><span class="sxs-lookup"><span data-stu-id="92ec0-109">CoInitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializecor-function.md)  
 <span data-ttu-id="92ec0-110">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="92ec0-110">Obsolete.</span></span> <span data-ttu-id="92ec0-111">Para inicializar o common language runtime (CLR), use [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) ou [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span><span class="sxs-lookup"><span data-stu-id="92ec0-111">To initialize the common language runtime (CLR), use either [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md).</span></span>  
  
 [<span data-ttu-id="92ec0-112">Função CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="92ec0-112">CoInitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coinitializeee-function.md)  
 <span data-ttu-id="92ec0-113">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-113">Deprecated.</span></span> <span data-ttu-id="92ec0-114">Garante que o mecanismo de execução de CLR é carregado em um processo.</span><span class="sxs-lookup"><span data-stu-id="92ec0-114">Ensures that the CLR execution engine is loaded into a process.</span></span> <span data-ttu-id="92ec0-115">Use o [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="92ec0-115">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
 [<span data-ttu-id="92ec0-116">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="92ec0-116">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 <span data-ttu-id="92ec0-117">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-117">Deprecated.</span></span> <span data-ttu-id="92ec0-118">Carrega o common language runtime (CLR) em um processo usando informações de versão armazenadas em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="92ec0-118">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span>  
  
 [<span data-ttu-id="92ec0-119">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="92ec0-119">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 <span data-ttu-id="92ec0-120">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-120">Deprecated.</span></span> <span data-ttu-id="92ec0-121">Habilita a hosts não gerenciados para carregar o CLR em um processo.</span><span class="sxs-lookup"><span data-stu-id="92ec0-121">Enables unmanaged hosts to load the CLR into a process.</span></span>  
  
 [<span data-ttu-id="92ec0-122">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="92ec0-122">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 <span data-ttu-id="92ec0-123">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-123">Deprecated.</span></span> <span data-ttu-id="92ec0-124">Carrega o CLR em um processo usando as informações de versão que é lido de um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="92ec0-124">Loads the CLR into a process by using version information that is read from an XML file.</span></span>  
  
 [<span data-ttu-id="92ec0-125">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="92ec0-125">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 <span data-ttu-id="92ec0-126">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-126">Deprecated.</span></span> <span data-ttu-id="92ec0-127">Permite que os hosts gerenciados carregar o CLR em um processo e permite que você defina os sinalizadores para especificar o comportamento do CLR.</span><span class="sxs-lookup"><span data-stu-id="92ec0-127">Enables unmanaged hosts to load the CLR into a process, and allows you to set flags to specify the behavior of the CLR.</span></span>  
  
 [<span data-ttu-id="92ec0-128">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="92ec0-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 <span data-ttu-id="92ec0-129">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-129">Deprecated.</span></span> <span data-ttu-id="92ec0-130">Permite que os hosts carregar uma versão especificada do CLR em um processo.</span><span class="sxs-lookup"><span data-stu-id="92ec0-130">Enables hosts to load a specified version of the CLR into a process.</span></span>  
  
 [<span data-ttu-id="92ec0-131">Função GetCORRequiredVersion</span><span class="sxs-lookup"><span data-stu-id="92ec0-131">GetCORRequiredVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorrequiredversion-function.md)  
 <span data-ttu-id="92ec0-132">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-132">Deprecated.</span></span> <span data-ttu-id="92ec0-133">Obtém o número de versão necessário do CLR.</span><span class="sxs-lookup"><span data-stu-id="92ec0-133">Gets the required CLR version number.</span></span>  
  
 [<span data-ttu-id="92ec0-134">Função GetCORSystemDirectory</span><span class="sxs-lookup"><span data-stu-id="92ec0-134">GetCORSystemDirectory Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)  
 <span data-ttu-id="92ec0-135">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-135">Deprecated.</span></span> <span data-ttu-id="92ec0-136">Retorna o diretório de instalação do CLR que é carregado no processo.</span><span class="sxs-lookup"><span data-stu-id="92ec0-136">Returns the installation directory of the CLR that is loaded into the process.</span></span>  
  
 [<span data-ttu-id="92ec0-137">Função GetRealProcAddress</span><span class="sxs-lookup"><span data-stu-id="92ec0-137">GetRealProcAddress Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)  
 <span data-ttu-id="92ec0-138">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-138">Deprecated.</span></span> <span data-ttu-id="92ec0-139">Obtém o endereço da função especificada é exportado da versão instalada mais recente do CLR.</span><span class="sxs-lookup"><span data-stu-id="92ec0-139">Gets the address of the specified function that is exported from the latest installed version of the CLR.</span></span>  
  
 [<span data-ttu-id="92ec0-140">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="92ec0-140">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 <span data-ttu-id="92ec0-141">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-141">Deprecated.</span></span> <span data-ttu-id="92ec0-142">Obtém a versão e informações de diretório sobre o CLR solicitado por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92ec0-142">Gets version and directory information about the CLR requested by an application.</span></span>  
  
## <a name="clr-version-functions"></a><span data-ttu-id="92ec0-143">Funções de versão CLR</span><span class="sxs-lookup"><span data-stu-id="92ec0-143">CLR version functions</span></span>  
 <span data-ttu-id="92ec0-144">As funções nesta seção retornam uma versão do CLR. eles não ativaram o CLR.</span><span class="sxs-lookup"><span data-stu-id="92ec0-144">The functions in this section return a CLR version; they do not activate the CLR.</span></span>  
  
 [<span data-ttu-id="92ec0-145">Função GetCORVersion</span><span class="sxs-lookup"><span data-stu-id="92ec0-145">GetCORVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getcorversion-function.md)  
 <span data-ttu-id="92ec0-146">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-146">Deprecated.</span></span> <span data-ttu-id="92ec0-147">Retorna o número de versão do CLR que está em execução no processo atual.</span><span class="sxs-lookup"><span data-stu-id="92ec0-147">Returns the version number of the CLR that is running in the current process.</span></span>  
  
 [<span data-ttu-id="92ec0-148">Função GetFileVersion</span><span class="sxs-lookup"><span data-stu-id="92ec0-148">GetFileVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)  
 <span data-ttu-id="92ec0-149">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-149">Deprecated.</span></span> <span data-ttu-id="92ec0-150">Obtém as informações de versão do CLR do arquivo especificado, usando o buffer especificado.</span><span class="sxs-lookup"><span data-stu-id="92ec0-150">Gets the CLR version information of the specified file, using the specified buffer.</span></span>  
  
 [<span data-ttu-id="92ec0-151">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="92ec0-151">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 <span data-ttu-id="92ec0-152">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-152">Deprecated.</span></span> <span data-ttu-id="92ec0-153">Obtém o número de versão do CLR solicitado pelo aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="92ec0-153">Gets the version number of the CLR requested by the specified application.</span></span> <span data-ttu-id="92ec0-154">Se essa versão não estiver instalado, obtém a versão mais recente está instalada antes da versão solicitada.</span><span class="sxs-lookup"><span data-stu-id="92ec0-154">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 [<span data-ttu-id="92ec0-155">Função GetRequestedRuntimeVersionForCLSID</span><span class="sxs-lookup"><span data-stu-id="92ec0-155">GetRequestedRuntimeVersionForCLSID Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversionforclsid-function.md)  
 <span data-ttu-id="92ec0-156">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-156">Deprecated.</span></span> <span data-ttu-id="92ec0-157">Obtém as informações de versão apropriadas do CLR para a classe com CLSID especificado.</span><span class="sxs-lookup"><span data-stu-id="92ec0-157">Gets the appropriate CLR version information for the class with the specified CLSID.</span></span>  
  
 [<span data-ttu-id="92ec0-158">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="92ec0-158">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 <span data-ttu-id="92ec0-159">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-159">Deprecated.</span></span> <span data-ttu-id="92ec0-160">Obtém o número de versão do CLR que está associado com o identificador de processo especificado.</span><span class="sxs-lookup"><span data-stu-id="92ec0-160">Gets the version number of the CLR that is associated with the specified process handle.</span></span>  
  
 [<span data-ttu-id="92ec0-161">Função LockClrVersion</span><span class="sxs-lookup"><span data-stu-id="92ec0-161">LockClrVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)  
 <span data-ttu-id="92ec0-162">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-162">Deprecated.</span></span> <span data-ttu-id="92ec0-163">Permite que o host determinar qual versão do CLR será usado dentro do processo antes de inicializar explicitamente o CLR.</span><span class="sxs-lookup"><span data-stu-id="92ec0-163">Allows the host to determine which version of the CLR will be used within the process before explicitly initializing the CLR.</span></span>  
  
## <a name="hosting-functions"></a><span data-ttu-id="92ec0-164">Funções de hospedagem</span><span class="sxs-lookup"><span data-stu-id="92ec0-164">Hosting functions</span></span>  
 [<span data-ttu-id="92ec0-165">Função CallFunctionShim</span><span class="sxs-lookup"><span data-stu-id="92ec0-165">CallFunctionShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/callfunctionshim-function.md)  
 <span data-ttu-id="92ec0-166">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-166">Deprecated.</span></span> <span data-ttu-id="92ec0-167">Faz uma chamada para a função que tem o nome especificado e os parâmetros na biblioteca especificada.</span><span class="sxs-lookup"><span data-stu-id="92ec0-167">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 [<span data-ttu-id="92ec0-168">Função CoEEShutDownCOM</span><span class="sxs-lookup"><span data-stu-id="92ec0-168">CoEEShutDownCOM Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/coeeshutdowncom-function.md)  
 <span data-ttu-id="92ec0-169">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-169">Deprecated.</span></span> <span data-ttu-id="92ec0-170">Descarrega um assembly COM o processo.</span><span class="sxs-lookup"><span data-stu-id="92ec0-170">Unloads a COM assembly from the process.</span></span>  
  
 [<span data-ttu-id="92ec0-171">Função CorExitProcess</span><span class="sxs-lookup"><span data-stu-id="92ec0-171">CorExitProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)  
 <span data-ttu-id="92ec0-172">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-172">Deprecated.</span></span> <span data-ttu-id="92ec0-173">Desliga o processo atual de não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="92ec0-173">Shuts down the current unmanaged process.</span></span>  
  
 [<span data-ttu-id="92ec0-174">Função CorLaunchApplication</span><span class="sxs-lookup"><span data-stu-id="92ec0-174">CorLaunchApplication Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corlaunchapplication-function.md)  
 <span data-ttu-id="92ec0-175">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-175">Deprecated.</span></span> <span data-ttu-id="92ec0-176">Inicia o aplicativo no caminho de rede especificado, usando os manifestos especificados e outros dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92ec0-176">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 [<span data-ttu-id="92ec0-177">Função CorMarkThreadInThreadPool</span><span class="sxs-lookup"><span data-stu-id="92ec0-177">CorMarkThreadInThreadPool Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cormarkthreadinthreadpool-function.md)  
 <span data-ttu-id="92ec0-178">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-178">Deprecated.</span></span> <span data-ttu-id="92ec0-179">Marca o thread do pool de threads atualmente em execução para a execução de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="92ec0-179">Marks the currently executing thread-pool thread for the execution of managed code.</span></span> <span data-ttu-id="92ec0-180">Iniciando com o .NET Framework versão 2.0, essa função não tem efeito.</span><span class="sxs-lookup"><span data-stu-id="92ec0-180">Starting with the .NET Framework version 2.0, this function has no effect.</span></span> <span data-ttu-id="92ec0-181">Ele não é necessário e pode ser removido do seu código.</span><span class="sxs-lookup"><span data-stu-id="92ec0-181">It is not required, and can be removed from your code.</span></span>  
  
 [<span data-ttu-id="92ec0-182">Função CoUninitializeCor</span><span class="sxs-lookup"><span data-stu-id="92ec0-182">CoUninitializeCor Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializecor-function.md)  
 <span data-ttu-id="92ec0-183">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="92ec0-183">Obsolete.</span></span> <span data-ttu-id="92ec0-184">O CLR não pode ser descarregado de um processo.</span><span class="sxs-lookup"><span data-stu-id="92ec0-184">The CLR cannot be unloaded from a process.</span></span>  
  
 [<span data-ttu-id="92ec0-185">Função CoUninitializeEE</span><span class="sxs-lookup"><span data-stu-id="92ec0-185">CoUninitializeEE Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md)  
 <span data-ttu-id="92ec0-186">Obsoleto.</span><span class="sxs-lookup"><span data-stu-id="92ec0-186">Obsolete.</span></span>  
  
 [<span data-ttu-id="92ec0-187">Função CreateDebuggingInterfaceFromVersion</span><span class="sxs-lookup"><span data-stu-id="92ec0-187">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)  
 <span data-ttu-id="92ec0-188">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-188">Deprecated.</span></span> <span data-ttu-id="92ec0-189">Cria um [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objeto com base nas informações de versão especificada.</span><span class="sxs-lookup"><span data-stu-id="92ec0-189">Creates an [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) object based on the specified version information.</span></span>  
  
 [<span data-ttu-id="92ec0-190">Função CreateICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="92ec0-190">CreateICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md)  
 <span data-ttu-id="92ec0-191">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-191">Deprecated.</span></span> <span data-ttu-id="92ec0-192">Cria um [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="92ec0-192">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="92ec0-193">Função DestroyICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="92ec0-193">DestroyICeeFileGen Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md)  
 <span data-ttu-id="92ec0-194">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-194">Deprecated.</span></span> <span data-ttu-id="92ec0-195">Destrói um [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="92ec0-195">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 [<span data-ttu-id="92ec0-196">Função FExecuteInAppDomainCallback</span><span class="sxs-lookup"><span data-stu-id="92ec0-196">FExecuteInAppDomainCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/fexecuteinappdomaincallback-function-pointer.md)  
 <span data-ttu-id="92ec0-197">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-197">Deprecated.</span></span> <span data-ttu-id="92ec0-198">Aponta para uma função que o CLR chama para executar código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="92ec0-198">Points to a function that the CLR calls to execute managed code.</span></span>  
  
 [<span data-ttu-id="92ec0-199">Função FLockClrVersionCallback</span><span class="sxs-lookup"><span data-stu-id="92ec0-199">FLockClrVersionCallback Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/flockclrversioncallback-function-pointer.md)  
 <span data-ttu-id="92ec0-200">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-200">Deprecated.</span></span> <span data-ttu-id="92ec0-201">Aponta para uma função que o CLR chama para notificar o host que a inicialização tiver seja iniciada ou concluída.</span><span class="sxs-lookup"><span data-stu-id="92ec0-201">Points to a function that the CLR calls to notify the host that initialization has either started or completed.</span></span>  
  
 [<span data-ttu-id="92ec0-202">Função GetCLRIdentityManager</span><span class="sxs-lookup"><span data-stu-id="92ec0-202">GetCLRIdentityManager Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getclridentitymanager-function.md)  
 <span data-ttu-id="92ec0-203">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-203">Deprecated.</span></span> <span data-ttu-id="92ec0-204">Obtém um ponteiro para uma interface que permite que o CLR gerenciar identidades.</span><span class="sxs-lookup"><span data-stu-id="92ec0-204">Gets a pointer to an interface that allows the CLR to manage identities.</span></span>  
  
 [<span data-ttu-id="92ec0-205">Função LoadLibraryShim</span><span class="sxs-lookup"><span data-stu-id="92ec0-205">LoadLibraryShim Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)  
 <span data-ttu-id="92ec0-206">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-206">Deprecated.</span></span> <span data-ttu-id="92ec0-207">Carrega uma versão especificada de uma DLL do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="92ec0-207">Loads a specified version of a .NET Framework DLL.</span></span>  
  
 [<span data-ttu-id="92ec0-208">Função LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="92ec0-208">LoadStringRC Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)  
 <span data-ttu-id="92ec0-209">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-209">Deprecated.</span></span> <span data-ttu-id="92ec0-210">Converte um valor HRESULT em uma mensagem de erro usando a cultura padrão do thread atual.</span><span class="sxs-lookup"><span data-stu-id="92ec0-210">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 [<span data-ttu-id="92ec0-211">Função LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="92ec0-211">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 <span data-ttu-id="92ec0-212">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-212">Deprecated.</span></span> <span data-ttu-id="92ec0-213">Converte um valor HRESULT a uma mensagem de erro apropriada para a cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="92ec0-213">Translates an HRESULT value to an appropriate error message for the specified culture.</span></span>  
  
 [<span data-ttu-id="92ec0-214">Função Lpoverlapped_completion_routine</span><span class="sxs-lookup"><span data-stu-id="92ec0-214">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpoverlapped-completion-routine-function-pointer.md)  
 <span data-ttu-id="92ec0-215">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-215">Deprecated.</span></span> <span data-ttu-id="92ec0-216">Aponta para uma função que notifica o host quando um sobreposto (ou seja, assíncrona) e/s para um dispositivo foi concluída.</span><span class="sxs-lookup"><span data-stu-id="92ec0-216">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 [<span data-ttu-id="92ec0-217">Função Lpthread_start_routine</span><span class="sxs-lookup"><span data-stu-id="92ec0-217">LPTHREAD_START_ROUTINE Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/lpthread-start-routine-function-pointer.md)  
 <span data-ttu-id="92ec0-218">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-218">Deprecated.</span></span> <span data-ttu-id="92ec0-219">Aponta para uma função que notifica o host que um thread começou a executar.</span><span class="sxs-lookup"><span data-stu-id="92ec0-219">Points to a function that notifies the host that a thread has started to execute.</span></span>  
  
 [<span data-ttu-id="92ec0-220">Função RunDll32ShimW</span><span class="sxs-lookup"><span data-stu-id="92ec0-220">RunDll32ShimW Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/rundll32shimw-function.md)  
 <span data-ttu-id="92ec0-221">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-221">Deprecated.</span></span> <span data-ttu-id="92ec0-222">Executa o comando especificado.</span><span class="sxs-lookup"><span data-stu-id="92ec0-222">Executes the specified command.</span></span>  
  
 [<span data-ttu-id="92ec0-223">Ponteiro de função WAITORTIMERCALLBACK</span><span class="sxs-lookup"><span data-stu-id="92ec0-223">WAITORTIMERCALLBACK Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/hosting/waitortimercallback-function-pointer.md)  
 <span data-ttu-id="92ec0-224">Preterido.</span><span class="sxs-lookup"><span data-stu-id="92ec0-224">Deprecated.</span></span> <span data-ttu-id="92ec0-225">Aponta para uma função que notifica o host que um identificador de espera foi sinalizado ou atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="92ec0-225">Points to a function that notifies the host that a wait handle has either been signaled or timed out.</span></span>  
  
## <a name="infrastructure-functions"></a><span data-ttu-id="92ec0-226">Funções de infraestrutura</span><span class="sxs-lookup"><span data-stu-id="92ec0-226">Infrastructure functions</span></span>  
 <span data-ttu-id="92ec0-227">As funções nesta seção são para uso apenas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="92ec0-227">The functions in this section are for use by the .NET Framework only.</span></span>  
  
 [<span data-ttu-id="92ec0-228">Função cordllmain</span><span class="sxs-lookup"><span data-stu-id="92ec0-228">_CorDllMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)  
 <span data-ttu-id="92ec0-229">Inicializa o CLR, localiza o ponto de entrada gerenciado no cabeçalho do CLR do assembly DLL e começa a ser executada.</span><span class="sxs-lookup"><span data-stu-id="92ec0-229">Initializes the CLR, locates the managed entry point in the DLL assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="92ec0-230">Função CorExeMain</span><span class="sxs-lookup"><span data-stu-id="92ec0-230">_CorExeMain Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)  
 <span data-ttu-id="92ec0-231">Inicializa o CLR, localiza o ponto de entrada gerenciado no cabeçalho do executável do assembly CLR e começa a ser executada.</span><span class="sxs-lookup"><span data-stu-id="92ec0-231">Initializes the CLR, locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
 [<span data-ttu-id="92ec0-232">Função CorExeMain2</span><span class="sxs-lookup"><span data-stu-id="92ec0-232">_CorExeMain2 Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corexemain2-function.md)  
 <span data-ttu-id="92ec0-233">Executa o ponto de entrada no código do mapeamento de memória especificado.</span><span class="sxs-lookup"><span data-stu-id="92ec0-233">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="92ec0-234">Essa função é chamada pelo carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="92ec0-234">This function is called by the operating system loader.</span></span>  
  
 [<span data-ttu-id="92ec0-235">Função CorImageUnloading</span><span class="sxs-lookup"><span data-stu-id="92ec0-235">_CorImageUnloading Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)  
 <span data-ttu-id="92ec0-236">Notifica o carregador quando as imagens do módulo gerenciado são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="92ec0-236">Notifies the loader when the managed module images are unloaded.</span></span>  
  
 [<span data-ttu-id="92ec0-237">Função CorValidateImage</span><span class="sxs-lookup"><span data-stu-id="92ec0-237">_CorValidateImage Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)  
 <span data-ttu-id="92ec0-238">Valida as imagens do módulo gerenciado e notifica o carregador do sistema operacional depois de terem sido carregados.</span><span class="sxs-lookup"><span data-stu-id="92ec0-238">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ec0-239">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92ec0-239">See Also</span></span>  
 [<span data-ttu-id="92ec0-240">.NET framework 4 hospedando funções estáticas globais</span><span class="sxs-lookup"><span data-stu-id="92ec0-240">.NET Framework 4 Hosting Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/net-framework-4-hosting-global-static-functions.md) 