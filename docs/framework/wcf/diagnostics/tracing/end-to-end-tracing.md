---
title: Rastreamento ponta a ponta
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f5ac7fc7-f97c-4313-b068-54e0c471b2aa
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c3f5c9f80bbf124440952e35049969c7cfa4f19c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="end-to-end-tracing"></a><span data-ttu-id="9c12a-102">Rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="9c12a-102">End-to-End Tracing</span></span>
<span data-ttu-id="9c12a-103">Ponta a ponta (e2e) rastreamento permite que os desenvolvedores acompanhar a execução de código a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infraestrutura para investigar por que um caminho de código falhou, ou para fornecer rastreamento detalhadas para análise de desempenho e planejamento de capacidade.</span><span class="sxs-lookup"><span data-stu-id="9c12a-103">End to End (e2e) Tracing allows developers to follow the execution of code in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] infrastructure to investigate why a code path has failed, or to provide detailed tracing for capacity planning and performance analysis.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="9c12a-104">fornece três mecanismos de correlação para ajudar a diagnosticar a causa do erro: atividades, transferência e propagação.</span><span class="sxs-lookup"><span data-stu-id="9c12a-104"> provides three correlation mechanisms to help diagnose the cause of an error: activities, transfers, and propagation.</span></span>  
  
 <span data-ttu-id="9c12a-105">Consulte [cenários de rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) para obter uma lista de cenários de rastreamento ponta a ponta e sua respectiva atividade e design de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9c12a-105">See [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md) for a list of end-to-end tracing scenarios, and their respective activity and tracing design.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9c12a-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="9c12a-106">In This Section</span></span>  
 <span data-ttu-id="9c12a-107">[Atividade](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md): descreve os rastreamentos de atividade no [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] modelo de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="9c12a-107">[Activity](../../../../../docs/framework/wcf/diagnostics/tracing/activity.md):  Describes activity traces in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model.</span></span>  
  
 <span data-ttu-id="9c12a-108">[Transferência de](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md): descreve a transferência de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] modelo de rastreamento e usar a transferência para correlacionar atividades dentro de pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9c12a-108">[Transfer](../../../../../docs/framework/wcf/diagnostics/tracing/transfer.md):  Describes transfer in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model, and using transfer to correlate activities within endpoints.</span></span>  
  
 <span data-ttu-id="9c12a-109">[Propagação](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md): descreve a propagação de atividade no [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] modelo de rastreamento e usando a propagação para correlacionar atividades entre pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9c12a-109">[Propagation](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md):  Describes activity propagation in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model, and using propagation to correlate activities across endpoints.</span></span>  
  
 [<span data-ttu-id="9c12a-110">Resumo de tipo de rastreamento</span><span class="sxs-lookup"><span data-stu-id="9c12a-110">Trace Type Summary</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/trace-type-summary.md)  
  
 <span data-ttu-id="9c12a-111">Fornece um resumo da atividade de todos os tipos de rastreamento</span><span class="sxs-lookup"><span data-stu-id="9c12a-111">Provides a summary of all activity trace types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c12a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9c12a-112">See Also</span></span>  
 [<span data-ttu-id="9c12a-113">Configurando o rastreamento</span><span class="sxs-lookup"><span data-stu-id="9c12a-113">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="9c12a-114">Usando o Visualizador de Rastreamento de Serviço para exibir rastreamentos correlacionados e solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="9c12a-114">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="9c12a-115">Cenários de rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="9c12a-115">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 <span data-ttu-id="9c12a-116">[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) (Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe))</span><span class="sxs-lookup"><span data-stu-id="9c12a-116">[Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)</span></span>