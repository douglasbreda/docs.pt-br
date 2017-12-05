---
title: "Implantando serviços"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac361bfb-017d-4da9-a2d7-fc0fb72d65bb
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5e8a853ebfa84ab5517e34bd67ae38672fdacddf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="deploying-services"></a><span data-ttu-id="50052-102">Implantando serviços</span><span class="sxs-lookup"><span data-stu-id="50052-102">Deploying Services</span></span>
<span data-ttu-id="50052-103">Este tópico descreve como você pode implantar um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplicativo em um ambiente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="50052-103">This topic describes how you can deploy a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] application to a run-time environment.</span></span>  
  
## <a name="choosing-the-hosting-environment-for-your-application"></a><span data-ttu-id="50052-104">Escolher o ambiente de hospedagem para o seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="50052-104">Choosing the Hosting Environment for Your Application</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="50052-105">os serviços são projetados para funcionar em qualquer processo do Windows que dá suporte a código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="50052-105"> services are designed to run in any Windows process that supports managed code.</span></span> <span data-ttu-id="50052-106">Para se tornar ativa, um serviço deve ser hospedado em um ambiente de tempo de execução que cria e controla o contexto e o tempo de vida.</span><span class="sxs-lookup"><span data-stu-id="50052-106">To become active, a service must be hosted within a run-time environment that creates it and controls its context and lifetime.</span></span> <span data-ttu-id="50052-107">As opções variam de execução dentro do aplicativo de console mais simples para ambientes de servidor como um serviço do Windows, serviços de informações da Internet (IIS), ou dentro de um processo de trabalho de hospedagem gerenciado pelo serviço de ativação do Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="50052-107">Hosting options range from running inside the simplest console application to server environments like a Windows service, Internet Information Services (IIS), or within a worker process managed by the Windows Activation Service (WAS).</span></span> <span data-ttu-id="50052-108">Para examinar as diferentes opções de hospedagem para o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo, consulte [serviços de hospedagem](../../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="50052-108">To review the different hosting options for your [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, see [Hosting Services](../../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50052-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50052-109">See Also</span></span>  
 [<span data-ttu-id="50052-110">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="50052-110">Hosting</span></span>](../../../../docs/framework/wcf/feature-details/hosting.md)  
 <span data-ttu-id="50052-111">[Hosting Services](../../../../docs/framework/wcf/hosting-services.md) (Hospedando serviços)</span><span class="sxs-lookup"><span data-stu-id="50052-111">[Hosting Services](../../../../docs/framework/wcf/hosting-services.md)</span></span>