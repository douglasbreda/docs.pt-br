---
title: Especificando a execução do cliente- Comportamento do tempo
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- behaviors [WCF], system-provided client
ms.assetid: d16d3405-be70-4edb-8f62-b5f614ddeca5
ms.openlocfilehash: bc104c4f51ebc64154bd3d9b39ac2bca13b2fab1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805350"
---
# <a name="specifying-client-run-time-behavior"></a>Especificando a execução do cliente- Comportamento do tempo
Os clientes do Windows Communication Foundation (WCF), como serviços do Windows Communication Foundation (WCF), podem ser configurados para modificar o comportamento de tempo de execução de acordo com o aplicativo cliente. Três atributos estão disponíveis para especificar o comportamento de tempo de execução do cliente. Objetos de retorno de chamada duplex cliente podem usar o <xref:System.ServiceModel.CallbackBehaviorAttribute> e <xref:System.ServiceModel.Description.CallbackDebugBehavior> atributos para modificar seu comportamento de tempo de execução. O atributo, <xref:System.ServiceModel.Description.ClientViaBehavior>, pode ser usado para separar o destino lógico de destino da rede imediata. Além disso, podem usar tipos de retorno de chamada de cliente duplex alguns comportamentos no lado do serviço. Para obter mais informações, consulte [especificando comportamento de tempo de execução do serviço](../../../docs/framework/wcf/specifying-service-run-time-behavior.md).  
  
## <a name="using-the-callbackbehaviorattribute"></a>Usando o CallbackBehaviorAttribute  
 Você pode configurar ou estender o comportamento de execução de uma implementação do contrato de retorno de chamada em um aplicativo cliente usando o <xref:System.ServiceModel.CallbackBehaviorAttribute> classe. Esse atributo executa uma função semelhante para a classe de retorno de chamada como o <xref:System.ServiceModel.ServiceBehaviorAttribute> classe, com exceção de configurações de transações e o comportamento de instanciação.  
  
 O <xref:System.ServiceModel.CallbackBehaviorAttribute> classe deve ser aplicada à classe que implementa o contrato de retorno de chamada. Se aplicado a uma implementação do contrato nonduplex, um <xref:System.InvalidOperationException> exceção em tempo de execução. O seguinte exemplo de código mostra uma <xref:System.ServiceModel.CallbackBehaviorAttribute> classe em um objeto de retorno de chamada que usa o <xref:System.Threading.SynchronizationContext> objeto para determinar o thread para empacotar, o <xref:System.ServiceModel.CallbackBehaviorAttribute.ValidateMustUnderstand%2A> propriedade para impor a validação de mensagem e o <xref:System.ServiceModel.CallbackBehaviorAttribute.IncludeExceptionDetailInFaults%2A> propriedade a ser retornada exceções como <xref:System.ServiceModel.FaultException> objetos para o serviço para fins de depuração.  
  
 [!code-csharp[CallbackBehaviorAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/callbackbehaviorattribute/cs/client.cs#3)]
 [!code-vb[CallbackBehaviorAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/callbackbehaviorattribute/vb/client.vb#3)]  
  
## <a name="using-callbackdebugbehavior-to-enable-the-flow-of-managed-exception-information"></a>Usando CallbackDebugBehavior para habilitar o fluxo de informações de exceção gerenciada  
 Você pode habilitar o fluxo de informações de exceção gerenciada em um objeto de retorno de chamada do cliente para o serviço para fins de depuração, definindo o <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> propriedade `true` programaticamente ou de uma configuração de aplicativo do arquivo.  
  
 Retornando informações de exceção gerenciada aos serviços podem ser um risco de segurança porque os detalhes da exceção expõem informações sobre o cliente interno implementação não autorizados services pode usar. Além disso, embora o <xref:System.ServiceModel.Description.CallbackDebugBehavior> propriedades também podem ser definidas programaticamente, é fácil esquecer de desabilitar <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> durante a implantação.  
  
 Devido a problemas de segurança envolvida, é altamente recomendável que:  
  
-   Usar um arquivo de configuração do aplicativo para definir o valor da <xref:System.ServiceModel.Description.CallbackDebugBehavior.IncludeExceptionDetailInFaults%2A> propriedade `true`.  
  
-   É feito para que somente no controlado cenários de depuração.  
  
 O exemplo de código a seguir mostra um cliente de arquivo de configuração que instrui o WCF para retornar informações de exceção gerenciada de um cliente de objeto de retorno de chamada nas mensagens de SOAP.  
  
 [!code-xml[SCA.CallbackContract#4](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.callbackcontract/cs/client.exe.config#4)]  
 
## <a name="using-the-clientviabehavior-behavior"></a>Usando o comportamento de ClientViaBehavior  
 Você pode usar o <xref:System.ServiceModel.Description.ClientViaBehavior> comportamento para especificar o Uniform Resource Identifier para o qual o canal de transporte deve ser criado. Use esse comportamento quando o destino da rede imediata não é o processador pretendido da mensagem. Isso permite que vários saltos conversas quando o aplicativo de chamada não sabe, necessariamente, o destino final ou quando o destino `Via` cabeçalho não é um endereço.  
  
## <a name="see-also"></a>Consulte também  
 [Especificando o comportamento em tempo de execução do serviço](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
