---
title: Configurando classes de criptografia
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration files [.NET Framework], cryptography
- cryptographic algorithms
- security [.NET Framework], encryption
- cryptography, classes
- .NET Framework application configuration, cryptography
- default cryptography
ms.assetid: eee3ccb8-2c0d-4f35-b38d-6892a46c14e5
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 79eb9f9ef95dae24dd38fa93b137c9303815143b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="configuring-cryptography-classes"></a><span data-ttu-id="8460b-102">Configurando classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="8460b-102">Configuring Cryptography Classes</span></span>
<span data-ttu-id="8460b-103">O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] permite que os administradores do computador configurar os algoritmos de criptografia padrão e implementações de algoritmo que usam o .NET Framework e aplicativos escritos corretamente.</span><span class="sxs-lookup"><span data-stu-id="8460b-103">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] allows computer administrators to configure the default cryptographic algorithms and algorithm implementations that the .NET Framework and appropriately written applications use.</span></span>  <span data-ttu-id="8460b-104">Por exemplo, uma empresa que tem sua própria implementação de um algoritmo de criptografia pode fazer essa implementação padrão em vez da implementação fornecida com o [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8460b-104">For example, an enterprise that has its own implementation of a cryptographic algorithm can make that implementation the default instead of the implementation shipped in the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span> <span data-ttu-id="8460b-105">Embora os aplicativos gerenciados que usam criptografia sempre podem optar por associar explicitamente uma implementação específica, é recomendável que criar objetos de criptografia usando o sistema de configuração de criptografia.</span><span class="sxs-lookup"><span data-stu-id="8460b-105">Although managed applications that use cryptography can always choose to explicitly bind to a particular implementation, it is recommended that they create cryptographic objects by using the crypto configuration system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8460b-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8460b-106">In This Section</span></span>  
 [<span data-ttu-id="8460b-107">Mapeando nomes de algoritmo para classes de criptografia</span><span class="sxs-lookup"><span data-stu-id="8460b-107">Mapping Algorithm Names to Cryptography Classes</span></span>](../../../docs/framework/configure-apps/map-algorithm-names-to-cryptography-classes.md)  
 <span data-ttu-id="8460b-108">Descreve como mapear um nome de algoritmo para uma classe de criptografia.</span><span class="sxs-lookup"><span data-stu-id="8460b-108">Describes how to map an algorithm name to a cryptography class.</span></span>  
  
 [<span data-ttu-id="8460b-109">Mapeando identificadores de objeto para algoritmos de criptografia</span><span class="sxs-lookup"><span data-stu-id="8460b-109">Mapping Object Identifiers to Cryptography Algorithms</span></span>](../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)  
 <span data-ttu-id="8460b-110">Descreve como mapear um identificador de objeto para um algoritmo de criptografia.</span><span class="sxs-lookup"><span data-stu-id="8460b-110">Describes how to map an object identifier to a cryptography algorithm.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8460b-111">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="8460b-111">Related Sections</span></span>  
 [<span data-ttu-id="8460b-112">Serviços criptográficos</span><span class="sxs-lookup"><span data-stu-id="8460b-112">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)  
 <span data-ttu-id="8460b-113">Fornece uma visão geral dos serviços de criptografia fornecidos pelo [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8460b-113">Provides an overview of cryptographic services provided by the [!INCLUDE[winsdkshort](../../../includes/winsdkshort-md.md)].</span></span>  
  
 [<span data-ttu-id="8460b-114">Esquema de configurações de criptografia</span><span class="sxs-lookup"><span data-stu-id="8460b-114">Cryptography Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 <span data-ttu-id="8460b-115">Descreve os elementos que mapeiam nomes amigáveis de algoritmo a classes que implementam algoritmos de criptografia.</span><span class="sxs-lookup"><span data-stu-id="8460b-115">Describes elements that map friendly algorithm names to classes that implement cryptography algorithms.</span></span>