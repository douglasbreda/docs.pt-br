---
title: Como desabilitar criptografia de assinaturas digitais
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd174313-ad81-4dca-898a-016ccaff8187
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ce72cb4d71bcc08980104158940a15ea6ecd0c6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-disable-encryption-of-digital-signatures"></a><span data-ttu-id="06a67-102">Como desabilitar criptografia de assinaturas digitais</span><span class="sxs-lookup"><span data-stu-id="06a67-102">How to: Disable Encryption of Digital Signatures</span></span>
<span data-ttu-id="06a67-103">Por padrão, uma mensagem é assinada e a assinatura digital é criptografada.</span><span class="sxs-lookup"><span data-stu-id="06a67-103">By default, a message is signed and the signature is digitally encrypted.</span></span> <span data-ttu-id="06a67-104">Isso é controlado pela criação de uma associação personalizada com uma instância do <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> e configuração de `MessageProtectionOrder` propriedade ou classe a um <xref:System.ServiceModel.Security.MessageProtectionOrder> valor de enumeração.</span><span class="sxs-lookup"><span data-stu-id="06a67-104">This is controlled by creating a custom binding with an instance of the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> or the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and setting the `MessageProtectionOrder` property of either class to a <xref:System.ServiceModel.Security.MessageProtectionOrder> enumeration value.</span></span> <span data-ttu-id="06a67-105">O padrão é <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span><span class="sxs-lookup"><span data-stu-id="06a67-105">The default is <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span></span> <span data-ttu-id="06a67-106">Esse processo consome até 30% mais tempo do que simplesmente assinatura e criptografia com base no tamanho da mensagem geral (quanto menor a mensagem, maior o impacto de desempenho).</span><span class="sxs-lookup"><span data-stu-id="06a67-106">This process consumes up to 30 percent more time than simply signing and encrypting based on the overall message size (the smaller the message, the greater the performance impact).</span></span> <span data-ttu-id="06a67-107">A desabilitação da criptografia da assinatura, no entanto, pode permitir que um invasor adivinhar o conteúdo da mensagem.</span><span class="sxs-lookup"><span data-stu-id="06a67-107">Disabling encryption of the signature, however, might allow an attacker to guess the content of the message.</span></span> <span data-ttu-id="06a67-108">Isso é possível porque o elemento de assinatura contém o código de hash do texto sem formatação de todas as partes da mensagem assinada.</span><span class="sxs-lookup"><span data-stu-id="06a67-108">This is possible because the signature element contains the hash code of the plain text of every signed part in the message.</span></span> <span data-ttu-id="06a67-109">Por exemplo, embora o corpo da mensagem é criptografado por padrão, a assinatura não criptografada contém o código hash do corpo da mensagem antes da criptografia.</span><span class="sxs-lookup"><span data-stu-id="06a67-109">For example, although the message body is encrypted by default, the unencrypted signature contains the hash code of the message body before the encryption.</span></span> <span data-ttu-id="06a67-110">Se o conjunto de valores possíveis para a parte assinada e criptografada é pequeno, um invasor consiga deduzir o conteúdo examinando o valor de hash.</span><span class="sxs-lookup"><span data-stu-id="06a67-110">If the set of possible values for the signed and encrypted part is small, an attacker might be able to deduce the contents by looking at the hash value.</span></span> <span data-ttu-id="06a67-111">Criptografando a assinatura atenua esse vetor de ataque.</span><span class="sxs-lookup"><span data-stu-id="06a67-111">Encrypting the signature mitigates this attack vector.</span></span>  
  
 <span data-ttu-id="06a67-112">Portanto, desabilite a criptografia da assinatura somente quando o valor do conteúdo for baixo ou o conjunto de valores possíveis de conteúdo é grande e não determinísticas, e o ganho de desempenho mais importante do que como reduzir o ataque descrito acima.</span><span class="sxs-lookup"><span data-stu-id="06a67-112">Therefore, disable encryption of the signature only when the value of the content is low or the set of possible content values is large and nondeterministic, and the performance gain is more important than mitigating the attack described above.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="06a67-113">Se não houver nada na mensagem que é criptografada, o elemento de assinatura não é criptografado, mesmo quando o <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> está definida como <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span><span class="sxs-lookup"><span data-stu-id="06a67-113">If there is nothing in the message that is encrypted, the signature element is not encrypted, even when the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> property is set to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span></span> <span data-ttu-id="06a67-114">Esse comportamento ocorre mesmo com associações fornecidas pelo sistema; todas as associações fornecidas pelo sistema que a ordem de proteção de mensagem definida como `SignBeforeEncryptAndEncryptSignature`.</span><span class="sxs-lookup"><span data-stu-id="06a67-114">This behavior occurs even with system-provided bindings; all system-provided bindings have the message protection order set to `SignBeforeEncryptAndEncryptSignature`.</span></span> <span data-ttu-id="06a67-115">No entanto, o WSDL Web Services Description Language () [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] gera a será ainda contêm o `<sp:EncryptSignature>` asserção.</span><span class="sxs-lookup"><span data-stu-id="06a67-115">However, the Web Services Description Language (WSDL) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates will still contain the `<sp:EncryptSignature>` assertion.</span></span>  
  
### <a name="to-disable-digital-signing"></a><span data-ttu-id="06a67-116">Para desabilitar a assinatura digital</span><span class="sxs-lookup"><span data-stu-id="06a67-116">To disable digital signing</span></span>  
  
1.  <span data-ttu-id="06a67-117">Criará um <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="06a67-117">Create a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="06a67-118">[Como: criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="06a67-118"> [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
2.  <span data-ttu-id="06a67-119">Adicione um <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> ou <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> à coleção de associação.</span><span class="sxs-lookup"><span data-stu-id="06a67-119">Add either an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> or a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> to the binding collection.</span></span>  
  
3.  <span data-ttu-id="06a67-120">Definir o <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> propriedade <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, ou defina o <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> propriedade para <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.</span><span class="sxs-lookup"><span data-stu-id="06a67-120">Set the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, or set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06a67-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06a67-121">See Also</span></span>  
 [<span data-ttu-id="06a67-122">Recursos de segurança com associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="06a67-122">Security Capabilities with Custom Bindings</span></span>](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)