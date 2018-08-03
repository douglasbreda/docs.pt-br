---
title: Seleção de versão do .NET Core
description: Saiba como o .NET Core localiza e escolhe versões de tempo de execução para o seu programa.
author: billwagner
ms.author: wiwagn
ms.date: 06/27/2018
ms.openlocfilehash: d1b885ebbade4736d5f592d1dc1d4ba25a321a16
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874464"
---
# <a name="net-core-version-selection"></a><span data-ttu-id="cc6eb-103">Seleção de versão do .NET Core</span><span class="sxs-lookup"><span data-stu-id="cc6eb-103">.NET Core version selection</span></span>

[!INCLUDE [topic-appliesto-net-core-2plus](../../../includes/topic-appliesto-net-core-2plus.md)]

<span data-ttu-id="cc6eb-104">Este artigo explica as políticas usadas pelas ferramentas do .NET Core, pelo SDK e pelo tempo de execução para a seleção de versões.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-104">This article explains the policies used by the .NET Core tools, SDK, and runtime for selecting versions.</span></span> <span data-ttu-id="cc6eb-105">Essas políticas fornecem um equilíbrio entre a execução de aplicativos usando as versões especificadas e a possibilidade de fácil atualização dos computadores de desenvolvedores e usuários finais.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-105">These policies provide a balance between running applications using the specified versions and enabling ease of upgrading both developer and end user machines.</span></span> <span data-ttu-id="cc6eb-106">Essas políticas executam o seguinte:</span><span class="sxs-lookup"><span data-stu-id="cc6eb-106">These policies perform the following:</span></span>

- <span data-ttu-id="cc6eb-107">Implantação fácil e eficiente do .NET Core, incluindo atualizações de segurança e de confiabilidade.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-107">Easy and efficient deployment of .NET Core, including security and reliability updates.</span></span>
- <span data-ttu-id="cc6eb-108">Uso das ferramentas e dos comandos mais recentes independentes do tempo de execução de destino.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-108">Use the latest tools and commands independent of target runtime.</span></span>

<span data-ttu-id="cc6eb-109">A seleção de versão ocorre:</span><span class="sxs-lookup"><span data-stu-id="cc6eb-109">Version selection occurs:</span></span>

- <span data-ttu-id="cc6eb-110">Quando você executa um comando do SDK, [o SDK usa a versão mais recente instalada](#the-sdk-uses-the-latest-installed-version).</span><span class="sxs-lookup"><span data-stu-id="cc6eb-110">When you run an SDK command, [the sdk uses the latest installed version](#the-sdk-uses-the-latest-installed-version).</span></span>
- <span data-ttu-id="cc6eb-111">Quando você compila um assembly [os monikers da estrutura de destino definem as APIs do tempo de build](#target-framework-monikers-define-build-time-apis).</span><span class="sxs-lookup"><span data-stu-id="cc6eb-111">When you build an assembly, [target framework monikers define build time APIs](#target-framework-monikers-define-build-time-apis).</span></span>
- <span data-ttu-id="cc6eb-112">Quando você executa um aplicativo .NET Core, [os aplicativos dependentes da estrutura de destino efetuam roll forward](#framework-dependent-apps-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="cc6eb-112">When you run a .NET Core application, [target framework dependent apps roll forward](#framework-dependent-apps-roll-forward).</span></span>
- <span data-ttu-id="cc6eb-113">Quando você publica um aplicativo autossuficiente, [as implantações autossuficientes incluem o tempo de execução selecionado](#self-contained-deployments-include-the-selected-runtime).</span><span class="sxs-lookup"><span data-stu-id="cc6eb-113">When you publish a self-contained application, [self-contained deployments include the selected runtime](#self-contained-deployments-include-the-selected-runtime).</span></span>

<span data-ttu-id="cc6eb-114">O restante deste documento examina esses quatro cenários.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-114">The rest of this document examines those four scenarios.</span></span>

## <a name="the-sdk-uses-the-latest-installed-version"></a><span data-ttu-id="cc6eb-115">O SDK usa a versão mais recente instalada</span><span class="sxs-lookup"><span data-stu-id="cc6eb-115">The SDK uses the latest installed version</span></span>

<span data-ttu-id="cc6eb-116">Os comandos do SDK incluem `dotnet new`, `dotnet build` ou `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-116">SDK commands include `dotnet new`, `dotnet build` or `dotnet run`.</span></span> <span data-ttu-id="cc6eb-117">A CLI `dotnet` precisa escolher uma versão do SDK para qualquer comando.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-117">The `dotnet` CLI must choose an SDK version for any command.</span></span> <span data-ttu-id="cc6eb-118">A CLI do .NET Core usa o SDK mais recente instalado no computador por padrão.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-118">The .NET Core CLI uses the latest SDK installed on the machine by default.</span></span> <span data-ttu-id="cc6eb-119">Você usará o SDK do .NET Core v2.1.301 quando ele estiver instalado, mesmo se o projeto que você estiver trabalhando seja direcionado ao tempo de execução do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-119">You'll use the .NET Core SDK v2.1.301 when it's installed, even if the project you are working with targets the .NET Core Runtime 2.0.</span></span> <span data-ttu-id="cc6eb-120">Observe que isso ocorre para as versões prévias e também para as versões lançadas.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-120">Note that this is true for preview versions as well as released versions.</span></span> <span data-ttu-id="cc6eb-121">Você pode aproveitar os recursos e as melhorias mais recentes do SDK mesmo ao direcionar a versões anteriores de tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-121">You can take advantage of the latest SDK features and improvements while targeting earlier .NET Core runtime versions.</span></span> <span data-ttu-id="cc6eb-122">Você pode direcionar a várias versões de tempo de execução do .NET Core em projetos diferentes, usando as mesmas ferramentas do SDK para todos os projetos.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-122">You can target multiple runtime versions of .NET Core on different projects, using the same SDK tools for all projects.</span></span>

<span data-ttu-id="cc6eb-123">Em raras ocasiões, talvez você precise usar uma versão anterior do SDK.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-123">On rare occasions, you may need to use an earlier version of the SDK.</span></span> <span data-ttu-id="cc6eb-124">Nesse caso, especifique essa versão em um [arquivo *global. JSON*](../tools/global-json.md).</span><span class="sxs-lookup"><span data-stu-id="cc6eb-124">You specify that version in a [*global.json* file](../tools/global-json.md).</span></span> <span data-ttu-id="cc6eb-125">A política "usar versão mais recente" significa usar o *global.json* somente para especificar uma versão do SDK do .NET Core anterior à versão mais recente instalada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-125">The "use latest" policy means you only use *global.json* to specify a .NET Core SDK version earlier than the latest installed version.</span></span>

<span data-ttu-id="cc6eb-126">O *global.json* pode ser colocado em qualquer lugar na hierarquia de arquivos.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-126">*global.json* can be placed anywhere in the file hierarchy.</span></span> <span data-ttu-id="cc6eb-127">A CLI procura no diretório do projeto em diante até encontrar o primeiro *global.json*.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-127">The CLI searches upward from the project directory for the first *global.json* it finds.</span></span> <span data-ttu-id="cc6eb-128">Você controla a quais projetos um determinado *global.json* se aplica a pelo seu lugar no sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-128">You control which projects a given *global.json* applies to by its place in the file system.</span></span> <span data-ttu-id="cc6eb-129">A CLI do .NET procura um arquivo *global.json* navegando iterativamente do caminho do diretório de trabalho atual em diante.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-129">The .NET CLI searches for a *global.json* file iteratively navigating the path upward from the current working directory.</span></span> <span data-ttu-id="cc6eb-130">O primeiro arquivo *global.json* encontrado especifica a versão usada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-130">The first *global.json* file found specifies the version used.</span></span> <span data-ttu-id="cc6eb-131">Se essa versão estiver instalada, ela será usada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-131">If that version is installed, that version is used.</span></span> <span data-ttu-id="cc6eb-132">Se o SDK especificado na *global.json* não for encontrado, a CLI do .NET efetuará roll forward para o SDK mais recente instalado.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-132">If the SDK specified in the *global.json* is not found, the .NET CLI rolls forward to the latest SDK installed.</span></span> <span data-ttu-id="cc6eb-133">Esse é o mesmo que o comportamento padrão, quando não é encontrado nenhum arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-133">This is the same as the default behavior, when no *global.json* file is found.</span></span>

<span data-ttu-id="cc6eb-134">O exemplo a seguir mostra a sintaxe *global.json*:</span><span class="sxs-lookup"><span data-stu-id="cc6eb-134">The following example shows the *global.json* syntax:</span></span>

``` json
{
  "sdk": {
    "version": "2.0.0"
  }
}
```

<span data-ttu-id="cc6eb-135">O processo para selecionar uma versão do SDK é:</span><span class="sxs-lookup"><span data-stu-id="cc6eb-135">The process for selecting an SDK version is:</span></span>

1. <span data-ttu-id="cc6eb-136">O `dotnet` procura um arquivo *global.json* navegando inversamente de forma iterativa no caminho do diretório de trabalho atual em diante.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-136">`dotnet` searches for a *global.json* file iteratively reverse-navigating the path upward from the current working directory.</span></span>
1. <span data-ttu-id="cc6eb-137">O `dotnet` usa o SDK especificado no primeiro *global.json* encontrado.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-137">`dotnet` uses the SDK specified in the first *global.json* found.</span></span>
1. <span data-ttu-id="cc6eb-138">O `dotnet` usará a versão mais recente do SDK instalada se nenhum *global.json* for encontrado.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-138">`dotnet` uses the latest installed SDK if no *global.json* is found.</span></span>

<span data-ttu-id="cc6eb-139">Saiba mais sobre como selecionar uma versão do SDK na seção [regras de correspondência](../tools/global-json.md) do tópico sobre o *global.json*.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-139">You can learn more about selecting an SDK version in the [matching rules](../tools/global-json.md) section of the topic on *global.json*.</span></span>

## <a name="target-framework-monikers-define-build-time-apis"></a><span data-ttu-id="cc6eb-140">Os Monikers da Estrutura de Destino definem as APIs de tempo de build</span><span class="sxs-lookup"><span data-stu-id="cc6eb-140">Target Framework Monikers define build time APIs</span></span>

<span data-ttu-id="cc6eb-141">Você compila seu projeto em relação às APIs definidas em um **TFM** (Moniker da Estrutura de Destino).</span><span class="sxs-lookup"><span data-stu-id="cc6eb-141">You build your project against APIs defined in a **Target Framework Moniker** (TFM).</span></span> <span data-ttu-id="cc6eb-142">Você especifica a [estrutura de destino](../../standard/frameworks.md) no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-142">You specify the [target framework](../../standard/frameworks.md) in the project file.</span></span> <span data-ttu-id="cc6eb-143">Defina o elemento `TargetFramework` no arquivo de projeto, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cc6eb-143">Set the `TargetFramework` element in your project file as shown in the following example:</span></span>

``` xml
<TargetFramework>netcoreapp2.0</TargetFramework>
```

<span data-ttu-id="cc6eb-144">Você pode compilar o projeto em relação a várias TFMs.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-144">You may build your project against multiple TFMs.</span></span> <span data-ttu-id="cc6eb-145">A definição de várias estruturas de destino é mais comum em bibliotecas, mas também pode ocorrer com aplicativos.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-145">Setting multiple target frameworks is more common for libraries but can be done with applications as well.</span></span> <span data-ttu-id="cc6eb-146">Especifique uma propriedade `TargetFrameworks` (plural de `TargetFramework`).</span><span class="sxs-lookup"><span data-stu-id="cc6eb-146">You specify a `TargetFrameworks` property (plural of `TargetFramework`).</span></span> <span data-ttu-id="cc6eb-147">As estruturas de destino são delimitadas por ponto e vírgula, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cc6eb-147">The target frameworks are semicolon-delimited as shown in the following example:</span></span>

``` xml
<TargetFrameworks>netcoreapp2.0;net47</TargetFrameworks>
```

<span data-ttu-id="cc6eb-148">Um determinado SDK dá suporte a um conjunto fixo de estruturas, limitado à estrutura de destino do tempo de execução com o qual é fornecido.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-148">A given SDK supports a fixed set of frameworks, capped to the target framework of the runtime it ships with.</span></span> <span data-ttu-id="cc6eb-149">Por exemplo, o SDK do .NET Core 2.0 inclui o tempo de execução do .NET Core 2.0, que é uma implementação da estrutura de destino `netcoreapp2.0`.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-149">For example, the .NET Core 2.0 SDK includes the .NET Core 2.0 runtime, which is an implementation of the `netcoreapp2.0` target framework.</span></span> <span data-ttu-id="cc6eb-150">O SDK do .NET Core 2.0 dá suporte ao `netcoreapp1.0`, `netcoreapp1.1` e `netcoreapp2.0` mas não ao `netcoreapp2.1` (ou superior).</span><span class="sxs-lookup"><span data-stu-id="cc6eb-150">The .NET Core 2.0 SDK supports `netcoreapp1.0`, `netcoreapp1.1`, and `netcoreapp2.0` but not `netcoreapp2.1` (or higher).</span></span> <span data-ttu-id="cc6eb-151">Instale o SDK do .NET Core 2.1 para compilar para o `netcoreapp2.1`.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-151">You install the .NET Core 2.1 SDK to build for `netcoreapp2.1`.</span></span>

<span data-ttu-id="cc6eb-152">As estruturas de destino do .NET Standard também são limitadas à estrutura de destino do tempo de execução com o qual o SDK é fornecido.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-152">.NET Standard target frameworks are also capped to the target framework of the runtime the SDK ships with.</span></span> <span data-ttu-id="cc6eb-153">O SDK do .NET Core 2.0 é limitado ao `netstandard2.0`.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-153">The .NET Core 2.0 SDK is capped to `netstandard2.0`.</span></span>

## <a name="framework-dependent-apps-roll-forward"></a><span data-ttu-id="cc6eb-154">Roll foward de aplicativos dependentes da estrutura</span><span class="sxs-lookup"><span data-stu-id="cc6eb-154">Framework-dependent apps roll forward</span></span>

<span data-ttu-id="cc6eb-155">Execute um aplicativo da origem com [`dotnet run`](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="cc6eb-155">You run an application from source with [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="cc6eb-156">O `dotnet run` compila e executa um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-156">`dotnet run` both builds and runs an application.</span></span> <span data-ttu-id="cc6eb-157">O executável `dotnet` é o **host** do aplicativo em ambientes de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-157">The `dotnet` executable is the **host** for the application in development environments.</span></span>

<span data-ttu-id="cc6eb-158">O host escolhe a versão de patch mais recente instalada no computador.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-158">The host chooses the latest patch version installed on the machine.</span></span> <span data-ttu-id="cc6eb-159">Por exemplo, se você especificar `netcoreapp2.0` em seu arquivo de projeto e `2.0.4` for o tempo de execução mais recente do .NET instalado, o tempo de execução `2.0.4` será usado.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-159">For example, if you specified `netcoreapp2.0` in your project file, and `2.0.4` is the latest .NET runtime installed, the `2.0.4` runtime is used.</span></span>

<span data-ttu-id="cc6eb-160">Se nenhuma versão `2.0.*` aceitável for encontrada, uma nova versão `2.*` será usada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-160">If no acceptable `2.0.*` version is found, a new `2.*` version is used.</span></span> <span data-ttu-id="cc6eb-161">Por exemplo, se você especificar `netcoreapp2.0` e só o `2.1.0` estiver instalado, o aplicativo será executado usando o tempo de execução `2.1.0`.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-161">For example, if you specified `netcoreapp2.0` and only `2.1.0` is installed, the application runs using the `2.1.0` runtime.</span></span> <span data-ttu-id="cc6eb-162">Esse comportamento é conhecido como "roll forward de versão secundária".</span><span class="sxs-lookup"><span data-stu-id="cc6eb-162">This behavior is referred to as "minor version roll-forward."</span></span> <span data-ttu-id="cc6eb-163">As versões inferiores também não serão consideradas.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-163">Lower versions also won't be considered.</span></span> <span data-ttu-id="cc6eb-164">Quando nenhum tempo de execução aceitável estiver instalado, o aplicativo não será executado.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-164">When no acceptable runtime is installed, the application won't run.</span></span>

<span data-ttu-id="cc6eb-165">Alguns exemplos de uso demonstram o comportamento:</span><span class="sxs-lookup"><span data-stu-id="cc6eb-165">A few usage examples demonstrate the behavior:</span></span>

- <span data-ttu-id="cc6eb-166">A 2.0.4 é necessária.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-166">2.0.4 is required.</span></span> <span data-ttu-id="cc6eb-167">A 2.0.5 é a versão de patch mais recente instalada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-167">2.0.5 is the highest patch version installed.</span></span> <span data-ttu-id="cc6eb-168">A 2.0.5 é usada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-168">2.0.5 is used.</span></span>
- <span data-ttu-id="cc6eb-169">A 2.0.4 é necessária.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-169">2.0.4 is required.</span></span> <span data-ttu-id="cc6eb-170">Não há nenhuma versão 2.0.\* instalada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-170">No 2.0.\* versions are installed.</span></span> <span data-ttu-id="cc6eb-171">O 1.1.1 é o tempo de execução mais recente instalado.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-171">1.1.1 is the highest runtime installed.</span></span> <span data-ttu-id="cc6eb-172">Uma mensagem de erro é exibida.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-172">An error message is displayed.</span></span>
- <span data-ttu-id="cc6eb-173">A 2.0.4 é necessária.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-173">2.0.4 is required.</span></span> <span data-ttu-id="cc6eb-174">2.0.0 é a versão mais recente instalada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-174">2.0.0 is the highest version installed.</span></span> <span data-ttu-id="cc6eb-175">Uma mensagem de erro é exibida.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-175">An error message is displayed.</span></span>
- <span data-ttu-id="cc6eb-176">A 2.0.4 é necessária.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-176">2.0.4 is required.</span></span> <span data-ttu-id="cc6eb-177">Não há nenhuma versão 2.0.\* instalada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-177">No 2.0.\* versions are installed.</span></span> <span data-ttu-id="cc6eb-178">2.2.2 é a versão de tempo de execução 2.x mais recente instalada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-178">2.2.2 is the highest 2.x runtime version installed.</span></span> <span data-ttu-id="cc6eb-179">A 2.2.2 é usada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-179">2.2.2 is used.</span></span>
- <span data-ttu-id="cc6eb-180">A 2.0.4 é necessária.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-180">2.0.4 is required.</span></span> <span data-ttu-id="cc6eb-181">Não há nenhuma versão 2.x instalada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-181">No 2.x versions are installed.</span></span> <span data-ttu-id="cc6eb-182">A 3.0.0 está instalada (não é uma versão disponível atualmente).</span><span class="sxs-lookup"><span data-stu-id="cc6eb-182">3.0.0 (not a currently available version) is installed.</span></span> <span data-ttu-id="cc6eb-183">Uma mensagem de erro é exibida.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-183">An error message is displayed.</span></span>

<span data-ttu-id="cc6eb-184">O roll forward de versão secundária tem um efeito colateral que pode afetar os usuários finais.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-184">Minor version roll-forward has one side-effect that may affect end users.</span></span> <span data-ttu-id="cc6eb-185">Considere o seguinte cenário:</span><span class="sxs-lookup"><span data-stu-id="cc6eb-185">Consider the following scenario:</span></span>

- <span data-ttu-id="cc6eb-186">A 2.0.4 é necessária.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-186">2.0.4 is required.</span></span> <span data-ttu-id="cc6eb-187">Não há nenhuma versão 2.0.\* instalada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-187">No 2.0.\* versions are installed.</span></span> <span data-ttu-id="cc6eb-188">A 2.2.2 está instalada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-188">2.2.2 is installed.</span></span> <span data-ttu-id="cc6eb-189">A 2.2.2 é usada.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-189">2.2.2 is used.</span></span>
- <span data-ttu-id="cc6eb-190">A 2.0.5 é instalada mais tarde.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-190">2.0.5 is later installed.</span></span> <span data-ttu-id="cc6eb-191">A 2.0.5 será usada para as próximas inicializações do aplicativo, não a 2.2.2.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-191">2.0.5 will be used for subsequent application launches, not 2.2.2.</span></span> <span data-ttu-id="cc6eb-192">O patch mais recente da versão secundária necessária é preferível em relação a uma versão secundária mais recente.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-192">The latest patch of the required minor version is preferred over a higher minor version.</span></span>
- <span data-ttu-id="cc6eb-193">É possível que a 2.0.5 e a 2.2.2 se comportem de forma diferente, principalmente para cenários como serializar dados binários.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-193">It's possible that 2.0.5 and 2.2.2 behave differently, particularly for scenarios like serializing binary data.</span></span>

## <a name="self-contained-deployments-include-the-selected-runtime"></a><span data-ttu-id="cc6eb-194">As implantações autossuficientes incluem o tempo de execução selecionado</span><span class="sxs-lookup"><span data-stu-id="cc6eb-194">Self-contained deployments include the selected runtime</span></span>

<span data-ttu-id="cc6eb-195">É possível publicar um aplicativo como uma [ **distribuição autossuficiente**](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="cc6eb-195">You can publish an application as a [**self-contained distribution**](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="cc6eb-196">Essa abordagem inclui o tempo de execução e as bibliotecas do .NET Core com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-196">This approach bundles the .NET Core runtime and libraries with your application.</span></span> <span data-ttu-id="cc6eb-197">As implantações autossuficientes não são dependentes dos ambientes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-197">Self-contained deployments don't have a dependency on runtime environments.</span></span> <span data-ttu-id="cc6eb-198">A seleção da versão do tempo de execução ocorre no momento da publicação, não no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-198">Runtime version selection occurs at publishing time, not run time.</span></span>

<span data-ttu-id="cc6eb-199">O processo de publicação seleciona a versão de patch mais recente da família de determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-199">The publishing process selects the latest patch version of the given runtime family.</span></span> <span data-ttu-id="cc6eb-200">Por exemplo, `dotnet publish` selecionará o .NET Core 2.0.4 se ele for a versão de patch mais recente da família do tempo de execução do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-200">For example, `dotnet publish` will select .NET Core 2.0.4 if it is the latest patch version in the .NET Core 2.0 runtime family.</span></span> <span data-ttu-id="cc6eb-201">A estrutura de destino (incluindo os patches de segurança mais recentes instalados) é empacotada com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-201">The target framework (including the latest installed security patches) is packaged with the application.</span></span>

<span data-ttu-id="cc6eb-202">É um erro quando a versão mínima especificada para um aplicativo não é atendida.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-202">It's an error if the minimum version specified for an application isn't satisfied.</span></span> <span data-ttu-id="cc6eb-203">O `dotnet publish` vincula-se à última versão de patch de tempo de execução (em uma determinada família de versão principal.secundária).</span><span class="sxs-lookup"><span data-stu-id="cc6eb-203">`dotnet publish` binds to the latest runtime patch version (within a given major.minor version family).</span></span> <span data-ttu-id="cc6eb-204">`dotnet publish` não dá suporte à semântica de roll forward de `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-204">`dotnet publish` doesn't support the roll-forward semantics of `dotnet run`.</span></span> <span data-ttu-id="cc6eb-205">Para obter mais informações sobre patches e implantações autossuficientes, consulte o artigo sobre [seleção de patch de tempo de execução](../deploying/runtime-patch-selection.md) na implantação de aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-205">For more information about patches and self-contained deployments, see the article on [runtime patch selection](../deploying/runtime-patch-selection.md) in deploying .NET Core applications.</span></span>

<span data-ttu-id="cc6eb-206">As implantações autossuficientes podem exigir uma versão de patch específica.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-206">Self-contained deployments may require a specific patch version.</span></span> <span data-ttu-id="cc6eb-207">Você pode substituir a versão de patch mínima do tempo de execução (para versões superiores ou inferiores) no arquivo de projeto, conforme é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="cc6eb-207">You can override the minimum runtime patch version (to higher or lower versions) in the project file, as shown in the following example:</span></span>

``` xml
<RuntimeFrameworkVersion>2.0.4</RuntimeFrameworkVersion>
```

<span data-ttu-id="cc6eb-208">O elemento `RuntimeFrameworkVersion` substitui a política de versão padrão.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-208">The `RuntimeFrameworkVersion` element  overrides the default version policy.</span></span> <span data-ttu-id="cc6eb-209">Para implantações autossuficientes, o `RuntimeFrameworkVersion` especifica a versão *exata* da estrutura do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-209">For self-contained deployments, the `RuntimeFrameworkVersion` specifies the *exact* runtime framework version.</span></span> <span data-ttu-id="cc6eb-210">Para aplicativos dependentes da estrutura, o `RuntimeFrameworkVersion` especifica a versão *mínima* da estrutura de tempo de execução necessária.</span><span class="sxs-lookup"><span data-stu-id="cc6eb-210">For framework dependent applications, the `RuntimeFrameworkVersion` specifies the *minimum* required runtime framework version.</span></span>