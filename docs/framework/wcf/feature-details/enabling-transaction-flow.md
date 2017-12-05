---
title: "Ativando o fluxo de transações"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4b5d0b90ed28928e734089265cb8c58839b6d0cd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="enabling-transaction-flow"></a><span data-ttu-id="f9aaa-102">Ativando o fluxo de transações</span><span class="sxs-lookup"><span data-stu-id="f9aaa-102">Enabling Transaction Flow</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="f9aaa-103">Fornece opções altamente flexíveis para controlar o fluxo de transações.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-103"> provides highly flexible options for controlling transaction flow.</span></span> <span data-ttu-id="f9aaa-104">Configurações de fluxo de transações do serviço podem ser expressadas usando uma combinação de atributos e configuração.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-104">A service's transaction flow settings can be expressed using a combination of attributes and configuration.</span></span>  
  
## <a name="transaction-flow-settings"></a><span data-ttu-id="f9aaa-105">Configurações de fluxo de transações</span><span class="sxs-lookup"><span data-stu-id="f9aaa-105">Transaction Flow Settings</span></span>  
 <span data-ttu-id="f9aaa-106">Configurações de fluxo de transação são geradas para um ponto de extremidade de serviço como resultado da interseção dos três valores a seguir:</span><span class="sxs-lookup"><span data-stu-id="f9aaa-106">Transaction flow settings are generated for a service endpoint as a result of the intersection of the following three values:</span></span>  
  
-   <span data-ttu-id="f9aaa-107">O <xref:System.ServiceModel.TransactionFlowAttribute> atributo especificado para cada método de contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-107">The <xref:System.ServiceModel.TransactionFlowAttribute> attribute specified for each method in the service contract.</span></span>  
  
-   <span data-ttu-id="f9aaa-108">O `TransactionFlow` a propriedade binding na associação específica.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-108">The `TransactionFlow` binding property in the specific binding.</span></span>  
  
-   <span data-ttu-id="f9aaa-109">O `TransactionFlowProtocol` a propriedade binding na associação específica.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-109">The `TransactionFlowProtocol` binding property in the specific binding.</span></span> <span data-ttu-id="f9aaa-110">O `TransactionFlowProtocol` a propriedade binding permite que você escolha entre os dois protocolos de transação diferentes que você pode usar para transmitir uma transação.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-110">The `TransactionFlowProtocol` binding property enables you to choose among two different transaction protocols that you can use to flow a transaction.</span></span> <span data-ttu-id="f9aaa-111">As seções a seguir descrevem brevemente cada um deles.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-111">The following sections briefly describe each of them.</span></span>  
  
### <a name="ws-atomictransaction-protocol"></a><span data-ttu-id="f9aaa-112">Protocolo WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="f9aaa-112">WS-AtomicTransaction Protocol</span></span>  
 <span data-ttu-id="f9aaa-113">O protocolo WS-AtomicTransaction (WS-AT) é útil para cenários quando a interoperabilidade com pilhas de protocolo de terceiros é necessária.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-113">The WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span>  
  
### <a name="oletransactions-protocol"></a><span data-ttu-id="f9aaa-114">Protocolo OleTransactions</span><span class="sxs-lookup"><span data-stu-id="f9aaa-114">OleTransactions Protocol</span></span>  
 <span data-ttu-id="f9aaa-115">O protocolo OleTransactions é útil para cenários quando interoperabilidade com pilhas de protocolo de terceiros não é necessária, e o implantador de um serviço sabe com antecedência que o serviço de protocolo WS-AT está desabilitado localmente ou não de topologia de rede existente não favorecer o uso de WS-AT.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-115">The OleTransactions protocol is useful for scenarios when interoperability with third-party protocol stacks is not required, and the deployer of a service knows in advance that the WS-AT protocol service is disabled locally or the existing network topology does not favor the usage of WS-AT.</span></span>  
  
 <span data-ttu-id="f9aaa-116">A tabela a seguir mostra os diferentes tipos de fluxos de transação que podem ser gerados usando essas várias combinações.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-116">The following table shows the different types of transaction flows that can be generated using these various combinations.</span></span>  
  
|<span data-ttu-id="f9aaa-117">TransactionFlow</span><span class="sxs-lookup"><span data-stu-id="f9aaa-117">TransactionFlow</span></span><br /><br /> <span data-ttu-id="f9aaa-118">associação</span><span class="sxs-lookup"><span data-stu-id="f9aaa-118">binding</span></span>|<span data-ttu-id="f9aaa-119">Propriedade de associação TransactionFlow</span><span class="sxs-lookup"><span data-stu-id="f9aaa-119">TransactionFlow binding property</span></span>|<span data-ttu-id="f9aaa-120">Protocolo de associação de TransactionFlowProtocol</span><span class="sxs-lookup"><span data-stu-id="f9aaa-120">TransactionFlowProtocol binding protocol</span></span>|<span data-ttu-id="f9aaa-121">Tipo de fluxo de transações</span><span class="sxs-lookup"><span data-stu-id="f9aaa-121">Type of transaction flow</span></span>|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|<span data-ttu-id="f9aaa-122">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="f9aaa-122">Mandatory</span></span>|<span data-ttu-id="f9aaa-123">true</span><span class="sxs-lookup"><span data-stu-id="f9aaa-123">true</span></span>|<span data-ttu-id="f9aaa-124">WS-AT</span><span class="sxs-lookup"><span data-stu-id="f9aaa-124">WS-AT</span></span>|<span data-ttu-id="f9aaa-125">Transação deve ser colocada no formato WS-AT interoperável.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-125">Transaction must be flowed in the interoperable WS-AT format.</span></span>|  
|<span data-ttu-id="f9aaa-126">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="f9aaa-126">Mandatory</span></span>|<span data-ttu-id="f9aaa-127">true</span><span class="sxs-lookup"><span data-stu-id="f9aaa-127">true</span></span>|<span data-ttu-id="f9aaa-128">OleTransactions</span><span class="sxs-lookup"><span data-stu-id="f9aaa-128">OleTransactions</span></span>|<span data-ttu-id="f9aaa-129">Transação deve ser recebida no fluxo de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] OleTransactions formato.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-129">Transaction must be flowed in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] OleTransactions format.</span></span>|  
|<span data-ttu-id="f9aaa-130">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="f9aaa-130">Mandatory</span></span>|<span data-ttu-id="f9aaa-131">false</span><span class="sxs-lookup"><span data-stu-id="f9aaa-131">false</span></span>|<span data-ttu-id="f9aaa-132">Não aplicável</span><span class="sxs-lookup"><span data-stu-id="f9aaa-132">Not applicable</span></span>|<span data-ttu-id="f9aaa-133">Não aplicável porque esta é uma configuração inválida.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-133">Not applicable because this is an invalid configuration.</span></span>|  
|<span data-ttu-id="f9aaa-134">Permitido</span><span class="sxs-lookup"><span data-stu-id="f9aaa-134">Allowed</span></span>|<span data-ttu-id="f9aaa-135">true</span><span class="sxs-lookup"><span data-stu-id="f9aaa-135">true</span></span>|<span data-ttu-id="f9aaa-136">WS-AT</span><span class="sxs-lookup"><span data-stu-id="f9aaa-136">WS-AT</span></span>|<span data-ttu-id="f9aaa-137">Transação pode ser colocada no formato WS-AT interoperável.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-137">Transaction may be flowed in the interoperable WS-AT format.</span></span>|  
|<span data-ttu-id="f9aaa-138">Permitido</span><span class="sxs-lookup"><span data-stu-id="f9aaa-138">Allowed</span></span>|<span data-ttu-id="f9aaa-139">true</span><span class="sxs-lookup"><span data-stu-id="f9aaa-139">true</span></span>|<span data-ttu-id="f9aaa-140">OleTransactions</span><span class="sxs-lookup"><span data-stu-id="f9aaa-140">OleTransactions</span></span>|<span data-ttu-id="f9aaa-141">Transação pode ser recebida no fluxo de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] OleTransactions formato.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-141">Transaction may be flowed in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] OleTransactions format.</span></span>|  
|<span data-ttu-id="f9aaa-142">Permitido</span><span class="sxs-lookup"><span data-stu-id="f9aaa-142">Allowed</span></span>|<span data-ttu-id="f9aaa-143">false</span><span class="sxs-lookup"><span data-stu-id="f9aaa-143">false</span></span>|<span data-ttu-id="f9aaa-144">Qualquer valor</span><span class="sxs-lookup"><span data-stu-id="f9aaa-144">Any value</span></span>|<span data-ttu-id="f9aaa-145">Não resulta em uma transação.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-145">A transaction is not flowed.</span></span>|  
|<span data-ttu-id="f9aaa-146">Não permitido</span><span class="sxs-lookup"><span data-stu-id="f9aaa-146">NotAllowed</span></span>|<span data-ttu-id="f9aaa-147">Qualquer valor</span><span class="sxs-lookup"><span data-stu-id="f9aaa-147">Any value</span></span>|<span data-ttu-id="f9aaa-148">Qualquer valor</span><span class="sxs-lookup"><span data-stu-id="f9aaa-148">Any value</span></span>|<span data-ttu-id="f9aaa-149">Não resulta em uma transação.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-149">A transaction is not flowed.</span></span>|  
  
 <span data-ttu-id="f9aaa-150">A tabela a seguir resume as resultados de processamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-150">The following table summarizes the message processing result.</span></span>  
  
|<span data-ttu-id="f9aaa-151">Mensagem de entrada</span><span class="sxs-lookup"><span data-stu-id="f9aaa-151">Incoming message</span></span>|<span data-ttu-id="f9aaa-152">Configuração de TransactionFlow</span><span class="sxs-lookup"><span data-stu-id="f9aaa-152">TransactionFlow setting</span></span>|<span data-ttu-id="f9aaa-153">Cabeçalho da transação</span><span class="sxs-lookup"><span data-stu-id="f9aaa-153">Transaction header</span></span>|<span data-ttu-id="f9aaa-154">Resultado do processamento de mensagem</span><span class="sxs-lookup"><span data-stu-id="f9aaa-154">Message processing result</span></span>|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|<span data-ttu-id="f9aaa-155">Transação coincide com o formato do protocolo esperado</span><span class="sxs-lookup"><span data-stu-id="f9aaa-155">Transaction matches expected protocol format</span></span>|<span data-ttu-id="f9aaa-156">Permitido ou obrigatório</span><span class="sxs-lookup"><span data-stu-id="f9aaa-156">Allowed or Mandatory</span></span>|<span data-ttu-id="f9aaa-157">`MustUnderstand` é igual a `true`.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-157">`MustUnderstand` equals `true`.</span></span>|<span data-ttu-id="f9aaa-158">Processo</span><span class="sxs-lookup"><span data-stu-id="f9aaa-158">Process</span></span>|  
|<span data-ttu-id="f9aaa-159">Transação não coincide com formato do protocolo esperado</span><span class="sxs-lookup"><span data-stu-id="f9aaa-159">Transaction does not match expected protocol format</span></span>|<span data-ttu-id="f9aaa-160">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="f9aaa-160">Mandatory</span></span>|<span data-ttu-id="f9aaa-161">`MustUnderstand` é igual a `false`.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-161">`MustUnderstand` equals `false`.</span></span>|<span data-ttu-id="f9aaa-162">Rejeitado porque uma transação é necessária</span><span class="sxs-lookup"><span data-stu-id="f9aaa-162">Rejected because a transaction is required</span></span>|  
|<span data-ttu-id="f9aaa-163">Transação não coincide com formato do protocolo esperado</span><span class="sxs-lookup"><span data-stu-id="f9aaa-163">Transaction does not match expected protocol format</span></span>|<span data-ttu-id="f9aaa-164">Permitido</span><span class="sxs-lookup"><span data-stu-id="f9aaa-164">Allowed</span></span>|<span data-ttu-id="f9aaa-165">`MustUnderstand` é igual a `false`.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-165">`MustUnderstand` equals `false`.</span></span>|<span data-ttu-id="f9aaa-166">Rejeitado porque o cabeçalho não é compreendido.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-166">Rejected because the header is not understood</span></span>|  
|<span data-ttu-id="f9aaa-167">Usando qualquer formato de protocolo de transação</span><span class="sxs-lookup"><span data-stu-id="f9aaa-167">Transaction using any protocol format</span></span>|<span data-ttu-id="f9aaa-168">Não permitido</span><span class="sxs-lookup"><span data-stu-id="f9aaa-168">NotAllowed</span></span>|<span data-ttu-id="f9aaa-169">`MustUnderstand` é igual a `false`.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-169">`MustUnderstand` equals `false`.</span></span>|<span data-ttu-id="f9aaa-170">Rejeitado porque o cabeçalho não é compreendido.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-170">Rejected because the header is not understood</span></span>|  
|<span data-ttu-id="f9aaa-171">Nenhuma transação</span><span class="sxs-lookup"><span data-stu-id="f9aaa-171">No transaction</span></span>|<span data-ttu-id="f9aaa-172">Obrigatório</span><span class="sxs-lookup"><span data-stu-id="f9aaa-172">Mandatory</span></span>|<span data-ttu-id="f9aaa-173">N/D</span><span class="sxs-lookup"><span data-stu-id="f9aaa-173">N/A</span></span>|<span data-ttu-id="f9aaa-174">Rejeitado porque uma transação é necessária</span><span class="sxs-lookup"><span data-stu-id="f9aaa-174">Rejected because a transaction is required</span></span>|  
|<span data-ttu-id="f9aaa-175">Nenhuma transação</span><span class="sxs-lookup"><span data-stu-id="f9aaa-175">No transaction</span></span>|<span data-ttu-id="f9aaa-176">Permitido</span><span class="sxs-lookup"><span data-stu-id="f9aaa-176">Allowed</span></span>|<span data-ttu-id="f9aaa-177">N/D</span><span class="sxs-lookup"><span data-stu-id="f9aaa-177">N/A</span></span>|<span data-ttu-id="f9aaa-178">Processo</span><span class="sxs-lookup"><span data-stu-id="f9aaa-178">Process</span></span>|  
|<span data-ttu-id="f9aaa-179">Nenhuma transação</span><span class="sxs-lookup"><span data-stu-id="f9aaa-179">No transaction</span></span>|<span data-ttu-id="f9aaa-180">Não permitido</span><span class="sxs-lookup"><span data-stu-id="f9aaa-180">NotAllowed</span></span>|<span data-ttu-id="f9aaa-181">N/D</span><span class="sxs-lookup"><span data-stu-id="f9aaa-181">N/A</span></span>|<span data-ttu-id="f9aaa-182">Processo</span><span class="sxs-lookup"><span data-stu-id="f9aaa-182">Process</span></span>|  
  
 <span data-ttu-id="f9aaa-183">Enquanto cada método em um contrato pode ter requisitos de fluxo de transação diferente, a configuração de protocolo de fluxo de transações tem seu escopo definida no nível de associação.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-183">While each method on a contract can have different transaction flow requirements, the transaction flow protocol setting is scoped at the level of the binding.</span></span> <span data-ttu-id="f9aaa-184">Isso significa que todos os métodos que compartilham o mesmo ponto de extremidade (e, portanto, a mesma associação) também compartilham a mesma política de permissão ou não exigir o fluxo de transação, bem como o mesmo protocolo de transação, se aplicável.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-184">This means that all methods that share the same endpoint (and therefore the same binding) also share the same policy allowing or requiring transaction flow, as well as the same transaction protocol if applicable.</span></span>  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a><span data-ttu-id="f9aaa-185">Ativando o fluxo de transação no nível de método</span><span class="sxs-lookup"><span data-stu-id="f9aaa-185">Enabling Transaction Flow at the Method Level</span></span>  
 <span data-ttu-id="f9aaa-186">Requisitos de fluxo de transação não são sempre o mesmo para todos os métodos em um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-186">Transaction flow requirements are not always the same for all methods in a service contract.</span></span> <span data-ttu-id="f9aaa-187">Portanto, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] também fornece um mecanismo baseado em atributos para permitir transações de cada método preferências de fluxo a ser expressa.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-187">Therefore, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] also provides an attribute-based mechanism to allow each method's transaction flow preferences to be expressed.</span></span> <span data-ttu-id="f9aaa-188">Isso é obtido com o <xref:System.ServiceModel.TransactionFlowAttribute> que especifica o nível no qual uma operação de serviço aceita um cabeçalho de transação.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-188">This is achieved by the <xref:System.ServiceModel.TransactionFlowAttribute> that specifies the level in which a service operation accepts a transaction header.</span></span> <span data-ttu-id="f9aaa-189">Se você deseja habilitar o fluxo de transações, você deve marcar seus métodos de contrato de serviço com esse atributo.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-189">You should mark your service contract methods with this attribute if you want to enable transaction flow.</span></span> <span data-ttu-id="f9aaa-190">Este atributo tem um dos valores da <xref:System.ServiceModel.TransactionFlowOption> enumeração, em que o valor padrão é <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-190">This attribute takes one of the values of the <xref:System.ServiceModel.TransactionFlowOption> enumeration, in which the default value is <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.</span></span> <span data-ttu-id="f9aaa-191">Se qualquer valor exceto <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> for especificado, o método é necessário para não ser unidirecional.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-191">If any value except <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> is specified, the method is required to not be one-way.</span></span> <span data-ttu-id="f9aaa-192">Um desenvolvedor pode usar esse atributo para especificar restrições ou requisitos de fluxo de transação de nível de método em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-192">A developer can use this attribute to specify method-level transaction flow requirements or constraints at design time.</span></span>  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a><span data-ttu-id="f9aaa-193">Ativando o fluxo de transação no nível do ponto de extremidade</span><span class="sxs-lookup"><span data-stu-id="f9aaa-193">Enabling Transaction Flow at the Endpoint Level</span></span>  
 <span data-ttu-id="f9aaa-194">Além da configuração de fluxo de transação de nível de método de <xref:System.ServiceModel.TransactionFlowAttribute> atributo fornece, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece uma configuração de todo o ponto de extremidade para o fluxo de transações para permitir que os administradores controlar o fluxo de transações em um nível superior.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-194">In addition to the method-level transaction flow setting  the <xref:System.ServiceModel.TransactionFlowAttribute> attribute provides, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides an endpoint-wide setting for transaction flow to allow administrators to control transaction flow at a higher level.</span></span>  
  
 <span data-ttu-id="f9aaa-195">Isso é obtido com o <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, que permite habilitar ou desabilitar o fluxo de transações de entrada em um ponto de extremidade do configurações de associação, bem como para especificar o formato do protocolo desejado de transação para transações de entrada.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-195">This is achieved by the <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, which enables you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired transaction protocol format for incoming transactions.</span></span>  
  
 <span data-ttu-id="f9aaa-196">Se a associação tiver desabilitado o fluxo de transações, mas uma das operações em um contrato de serviço exige uma transação de entrada, uma exceção de validação é lançada durante a inicialização do serviço.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-196">If the binding has disabled transaction flow, but one of the operations on a service contract requires an incoming transaction, then a validation exception is thrown at service startup.</span></span>  
  
 <span data-ttu-id="f9aaa-197">A maioria das associações aguardando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece contêm o `transactionFlow` e `transactionProtocol` atributos para que você possa configurar a associação específica para aceitar as transações de entrada.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-197">Most of the standing bindings [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides contain the `transactionFlow` and `transactionProtocol` attributes to enable you to configure the specific binding to accept incoming transactions.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="f9aaa-198">definir os elementos de configuração, consulte [ \<associação >](../../../../docs/framework/misc/binding.md).</span><span class="sxs-lookup"><span data-stu-id="f9aaa-198"> setting the configuration elements, see [\<binding>](../../../../docs/framework/misc/binding.md).</span></span>  
  
 <span data-ttu-id="f9aaa-199">Um administrador ou implantador pode usar o fluxo de transações de nível de ponto de extremidade para configurar restrições ou requisitos de transação de fluxo no momento da implantação usando o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-199">An administrator or deployer can use endpoint-level transaction flow to configure transaction flow requirements or constraints at deployment time using the configuration file.</span></span>  
  
## <a name="security"></a><span data-ttu-id="f9aaa-200">Segurança</span><span class="sxs-lookup"><span data-stu-id="f9aaa-200">Security</span></span>  
 <span data-ttu-id="f9aaa-201">Para garantir a integridade e segurança do sistema, você deve proteger as trocas de mensagens ao fluir transações entre aplicativos.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-201">To ensure system security and integrity, you must secure message exchanges when flowing transactions between applications.</span></span> <span data-ttu-id="f9aaa-202">Você não deve fluxo ou divulgar detalhes da transação para qualquer aplicativo que não está qualificada para participar na mesma transação.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-202">You should not flow or disclose transaction details to any application that is not entitled to participate in the same transaction.</span></span>  
  
 <span data-ttu-id="f9aaa-203">Ao gerar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes desconhecidos ou não confiáveis serviços Web com o uso de troca de metadados, chamadas para operações nesses serviços da Web devem suprimir a transação atual se possível.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-203">When generating [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients to unknown or untrusted Web services through the use of metadata exchange, calls to operations on these Web services should suppress the current transaction if possible.</span></span> <span data-ttu-id="f9aaa-204">O exemplo a seguir demonstra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-204">The following example demonstrates how to do this.</span></span>  
  
```  
//client code which has an ambient transaction  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Suppress))  
{  
    // No transaction will flow to this operation  
    untrustedProxy.Operation1(...);  
    scope.Complete();  
}  
//remainder of client code  
```  
  
 <span data-ttu-id="f9aaa-205">Além disso, os serviços devem ser configurados para aceitar as transações de entrada somente de clientes que eles têm autenticado e autorizado.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-205">In addition, services should be configured to accept incoming transactions only from clients that they have authenticated and authorized.</span></span> <span data-ttu-id="f9aaa-206">Transações de entrada devem ser aceita somente se eles forem provenientes de clientes altamente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-206">Incoming transactions should only be accepted if they come from highly trusted clients.</span></span>  
  
## <a name="policy-assertions"></a><span data-ttu-id="f9aaa-207">Declarações de política</span><span class="sxs-lookup"><span data-stu-id="f9aaa-207">Policy Assertions</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="f9aaa-208">usa declarações de política para controlar o fluxo de transações.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-208"> uses policy assertions to control transaction flow.</span></span> <span data-ttu-id="f9aaa-209">Declarações de política podem ser encontradas no documento de política do serviço, que é gerado por contratos de agregação, configuração e atributos.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-209">Policy assertions can be found in a service’s policy document, which is generated by aggregating contracts, configuration, and attributes.</span></span> <span data-ttu-id="f9aaa-210">O cliente pode obter o documento de política do serviço usando um HTTP GET ou uma resposta de solicitação do WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-210">The client can obtain the service’s policy document using an HTTP GET or a WS-MetadataExchange request-reply.</span></span> <span data-ttu-id="f9aaa-211">Os clientes podem processar o documento de política para determinar quais operações em um contrato de serviço podem dar suporte a ou exigir o fluxo de transações.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-211">Clients can then process the policy document to determine which operations on a service contract may support or require transaction flow.</span></span>  
  
 <span data-ttu-id="f9aaa-212">Declarações de política de fluxo de transações afetam o fluxo de transações, especificando os cabeçalhos SOAP que um cliente deve enviar para um serviço para representar uma transação.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-212">Transaction flow policy assertions affect transaction flow by specifying the SOAP headers that a client should send to a service to represent a transaction.</span></span> <span data-ttu-id="f9aaa-213">Todos os cabeçalhos de transação devem ser marcados com `MustUnderstand` igual a `true`.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-213">All transaction headers must be marked with `MustUnderstand` equal to `true`.</span></span> <span data-ttu-id="f9aaa-214">Qualquer mensagem com um cabeçalho marcada caso contrário é rejeitada com uma falha de SOAP.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-214">Any message with a header marked otherwise is rejected with a SOAP fault.</span></span>  
  
 <span data-ttu-id="f9aaa-215">Somente uma declaração de política relacionadas à transação pode estar presente em uma única operação.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-215">Only one transaction-related policy assertion can be present on a single operation.</span></span> <span data-ttu-id="f9aaa-216">Documentos de política com mais de uma declaração de transação em uma operação são considerados inválidos e serão rejeitados pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f9aaa-216">Policy documents with more than one transaction assertion on an operation are considered invalid and are rejected by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="f9aaa-217">Além disso, um protocolo de transação única pode estar presente em cada tipo de porta.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-217">In addition, only a single transaction protocol can be present inside each port type.</span></span> <span data-ttu-id="f9aaa-218">Documentos de política com operações fazendo referência a mais de um protocolo de transação dentro de um único tipo de porta são considerados inválidos e serão rejeitados pelo [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f9aaa-218">Policy documents with operations referencing more than one transaction protocol inside a single port type are considered invalid, and are rejected by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="f9aaa-219">Documentos de política com declarações de transação presente nas mensagens de saída ou mensagens de entrada unidirecionais também são consideradas inválidas.</span><span class="sxs-lookup"><span data-stu-id="f9aaa-219">Policy documents with transaction assertions present on output messages or one-way input messages are also considered invalid.</span></span>