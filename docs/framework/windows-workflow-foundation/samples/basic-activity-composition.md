---
title: "Composição básica de atividades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c283a1a7-1245-4ecd-8072-206c1b4ca379
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8eb909ce50c5faebf48339b07e8565fcd7afc718
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="basic-activity-composition"></a><span data-ttu-id="3a9aa-102">Composição básica de atividades</span><span class="sxs-lookup"><span data-stu-id="3a9aa-102">Basic Activity Composition</span></span>
<span data-ttu-id="3a9aa-103">Este exemplo demonstra como composto atividades personalizados e sistema forneceu atividades para criar uma atividades mais personalizados.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-103">This sample demonstrates how to compose custom activities and system-provided activities to build more custom activities.</span></span>  
  
 <span data-ttu-id="3a9aa-104">O fluxo de trabalho usando as agendas de atividade de pesquisa a pesquisa com uma lista de perguntas e em seguida, de saída que as respostas recebiam.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-104">The workflow using the Survey activity schedules the Survey with a list of questions, and then outputs the responses received.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="3a9aa-105">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="3a9aa-105">Sample Details</span></span>  
 <span data-ttu-id="3a9aa-106">Este exemplo usa três atividades personalizados.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-106">This sample uses three custom activities.</span></span> <span data-ttu-id="3a9aa-107">`ReadLine`é um simples <xref:System.Activities.NativeActivity> \<cadeia de caracteres > que cria um <xref:System.Activities.Bookmark> quando agendado e, em seguida, define o `Return` <xref:System.Activities.OutArgument%601> para o valor com o qual o <xref:System.Activities.Bookmark> é retomado.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-107">`ReadLine` is a simple <xref:System.Activities.NativeActivity>\<string> that creates a <xref:System.Activities.Bookmark> when scheduled, and then sets the `Return`<xref:System.Activities.OutArgument%601> to the value with which the <xref:System.Activities.Bookmark> is resumed.</span></span> <span data-ttu-id="3a9aa-108">`Prompt`é um <xref:System.Activities.Activity%601> \<cadeia de caracteres > que leva um <xref:System.Activities.InArgument%601>< cadeia de caracteres\> chamado `Text` e retorna os usuários a resposta no `Result` <xref:System.Activities.OutArgument%601> \<cadeia de caracteres >.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-108">`Prompt` is an <xref:System.Activities.Activity%601>\<string> that takes an <xref:System.Activities.InArgument%601><string\> named `Text` and returns the users response in the `Result`<xref:System.Activities.OutArgument%601>\<string>.</span></span> <span data-ttu-id="3a9aa-109">A atividade de `Prompt` usa as atividades de <xref:System.Activities.Statements.Sequence> e de <xref:System.Activities.Statements.WriteLine> fornecidos como parte do .NET Framework, e também inserir a atividade personalizado de `ReadLine` para obter a entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-109">The `Prompt` activity uses the <xref:System.Activities.Statements.Sequence> and <xref:System.Activities.Statements.WriteLine> activities that ship as part of the .NET Framework, and also incorporates the custom `ReadLine` activity for getting user input.</span></span> <span data-ttu-id="3a9aa-110">A atividade personalizado a última da atividade é `Survey` .</span><span class="sxs-lookup"><span data-stu-id="3a9aa-110">The last custom activity is the `Survey` activity.</span></span> <span data-ttu-id="3a9aa-111">É um <xref:System.Activities.Activity>< ICollection\<cadeia de caracteres >>.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-111">It is an <xref:System.Activities.Activity><ICollection\<string>>.</span></span>  <span data-ttu-id="3a9aa-112">Essa atividade tem um <xref:System.Activities.InArgument%601>< IEnumerable < cadeia de caracteres\>> denominado `Questions` e preenche o `Result` out argumento com as respostas.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-112">This activity takes an <xref:System.Activities.InArgument%601><IEnumerable<string\>> named `Questions` and populates the `Result` out argument with the responses.</span></span> <span data-ttu-id="3a9aa-113">A atividade de `Survey` usa <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> e <xref:System.Activities.Statements.AddToCollection%601> do .NET Framework e emprega a atividade de `Prompt` para fazer as perguntas de pesquisa e obter respostas.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-113">The `Survey` activity uses <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Sequence> and <xref:System.Activities.Statements.AddToCollection%601> from the .NET Framework and employs the `Prompt` activity for asking the survey questions and getting responses.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3a9aa-114">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="3a9aa-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="3a9aa-115">Abra o **BasicActivityComposition.sln** solução de exemplo [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a9aa-115">Open the **BasicActivityComposition.sln** sample solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="3a9aa-116">Criar e executar a solução.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-116">Build and run the solution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3a9aa-117">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3a9aa-118">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-118">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3a9aa-119">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a9aa-120">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="3a9aa-120">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\Composite\ActivityComposition`