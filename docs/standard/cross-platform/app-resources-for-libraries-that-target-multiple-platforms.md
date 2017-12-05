---
title: "Recursos do aplicativo para bibliotecas direcionadas a várias plataformas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multiple platforms, resources for
- resources [.NET Framework]
- .NET Framework, resources when targeting multiple platforms
- resources, for multiple platforms
- targeting multiple platforms, resources for
ms.assetid: 72c76f0b-7255-4576-9261-3587f949669c
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 74cd3df645c2490bcf98533ca8846ddfb742f67f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="app-resources-for-libraries-that-target-multiple-platforms"></a><span data-ttu-id="a4d2e-102">Recursos do aplicativo para bibliotecas direcionadas a várias plataformas</span><span class="sxs-lookup"><span data-stu-id="a4d2e-102">App Resources for Libraries That Target Multiple Platforms</span></span>
<span data-ttu-id="a4d2e-103">Você pode usar o .NET Framework [biblioteca de classes portátil](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) tipo para garantir que os recursos em suas bibliotecas de classe podem ser acessados em várias plataformas de projeto.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-103">You can use the .NET Framework [Portable Class Library](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md) project type to ensure that resources in your class libraries can be accessed from multiple platforms.</span></span> <span data-ttu-id="a4d2e-104">Esse tipo de projeto está disponível em [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] e tem como alvo o subconjunto portátil da biblioteca de classes do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-104">This project type is available in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] and targets the portable subset of the .NET Framework class library.</span></span> <span data-ttu-id="a4d2e-105">Usar um [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] garante que a biblioteca possa ser acessada de aplicativos da área de trabalho, Silverlight, Windows Phone e [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4d2e-105">Using  a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] ensures that your library can be accessed from desktop apps, Silverlight apps, Windows Phone apps, and [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 <span data-ttu-id="a4d2e-106">O projeto [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] disponibiliza somente um subconjunto muito limitado dos tipos no namespace <xref:System.Resources> para o seu aplicativo, mas permite que você use a classe <xref:System.Resources.ResourceManager> para recuperar recursos.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-106">The [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project makes only a very limited subset of the types in the <xref:System.Resources> namespace available to your application, but it does allow you to use the <xref:System.Resources.ResourceManager> class to retrieve resources.</span></span> <span data-ttu-id="a4d2e-107">No entanto, se estiver criando um aplicativo com o Visual Studio, você deverá usar o wrapper fortemente tipado criado pelo Visual Studio em vez de usar a classe <xref:System.Resources.ResourceManager> diretamente.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-107">However, if you are creating an app by using Visual Studio, you should use the strongly typed wrapper created by Visual Studio instead of using the <xref:System.Resources.ResourceManager> class directly.</span></span>  
  
 <span data-ttu-id="a4d2e-108">Para criar um wrapper com rigidez de tipos no Visual Studio, defina o arquivo de recurso principal **modificador de acesso** no Designer de recursos Visual Studio para **público**.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-108">To create a strongly typed wrapper in Visual Studio, set the main resource file's **Access Modifier** in the Visual Studio Resource Designer to **Public**.</span></span> <span data-ttu-id="a4d2e-109">Isso cria um arquivo [resourceFileName].designer.cs ou [resourceFileName].designer.vb que contém o wrapper ResourceManager fortemente tipado.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-109">This creates a [resourceFileName].designer.cs or [resourceFileName].designer.vb file that contains the strongly typed ResourceManager wrapper.</span></span> <span data-ttu-id="a4d2e-110">Para obter mais informações sobre como usar um wrapper de recursos fortemente tipados, consulte a seção "Gerar um fortemente tipado classe de recurso" a [Resgen.exe (gerador de arquivo)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-110">For more information about using a strongly typed resource wrapper, see the "Generating a Strongly Typed Resource Class" section in the [Resgen.exe (Resource File Generator)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) topic.</span></span>  
  
## <a name="resource-manager-in-the-includenetportableincludesnet-portable-mdmd"></a><span data-ttu-id="a4d2e-111">Gerenciador de Recursos no [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4d2e-111">Resource Manager in the [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]</span></span>  
 <span data-ttu-id="a4d2e-112">Em um projeto do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], todos os acessos a recursos são tratados pela classe <xref:System.Resources.ResourceManager>.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-112">In a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, all access to resources is handled by the <xref:System.Resources.ResourceManager> class.</span></span> <span data-ttu-id="a4d2e-113">Como tipos no namespace <xref:System.Resources>, como <xref:System.Resources.ResourceReader> e <xref:System.Resources.ResourceSet>, não são acessíveis a partir de um projeto do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], eles não podem ser usados para acessar recursos.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-113">Because types in the <xref:System.Resources> namespace, such as <xref:System.Resources.ResourceReader> and <xref:System.Resources.ResourceSet>, are not accessible from a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project, they cannot be used to access resources.</span></span>  
  
 <span data-ttu-id="a4d2e-114">O projeto do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] inclui os quatro membros <xref:System.Resources.ResourceManager> listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-114">The [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project includes the four <xref:System.Resources.ResourceManager> members listed in the following table.</span></span> <span data-ttu-id="a4d2e-115">Esses construtores e métodos permitem que você crie uma instância de um objeto <xref:System.Resources.ResourceManager> e recupere recursos de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-115">These constructors and methods enable you to instantiate a <xref:System.Resources.ResourceManager> object and retrieve string resources.</span></span>  
  
|<span data-ttu-id="a4d2e-116">Membro do `ResourceManager`</span><span class="sxs-lookup"><span data-stu-id="a4d2e-116">`ResourceManager` member</span></span>|<span data-ttu-id="a4d2e-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a4d2e-117">Description</span></span>|  
|------------------------------|-----------------|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.String%2CSystem.Reflection.Assembly%29>|<span data-ttu-id="a4d2e-118">Cria uma instância de <xref:System.Resources.ResourceManager> para acessar o arquivo de recurso nomeado encontrado no assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-118">Creates a <xref:System.Resources.ResourceManager> instance to access the named resource file found in the specified assembly.</span></span>|  
|<xref:System.Resources.ResourceManager.%23ctor%28System.Type%29>|<span data-ttu-id="a4d2e-119">Cria uma instância de <xref:System.Resources.ResourceManager> que corresponde ao tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-119">Creates a <xref:System.Resources.ResourceManager> instance that corresponds to the specified type.</span></span>|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%29>|<span data-ttu-id="a4d2e-120">Recupera um recurso nomeado para a cultura atual.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-120">Retrieves a named resource for the current culture.</span></span>|  
|<xref:System.Resources.ResourceManager.GetString%28System.String%2CSystem.Globalization.CultureInfo%29>|<span data-ttu-id="a4d2e-121">Recupera um recurso nomeado que pertence à cultura especificada.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-121">Retrieves a named resource belonging to the specified culture.</span></span>|  
  
 <span data-ttu-id="a4d2e-122">A exclusão de outros membros de <xref:System.Resources.ResourceManager> do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] significa que objetos serializados, dados que não sejam cadeia de caracteres, e imagens não podem ser recuperados de um arquivo de recurso.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-122">The exclusion of other <xref:System.Resources.ResourceManager> members from the [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] means that serialized objects, non-string data, and images cannot be retrieved from a resource file.</span></span> <span data-ttu-id="a4d2e-123">Para usar recursos de um [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], você deve armazenar todos os dados de objeto na forma de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-123">To use resources from a [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], you should store all  object data in string form.</span></span> <span data-ttu-id="a4d2e-124">Por exemplo, você pode armazenar valores numéricos em um arquivo de recurso convertendo-os em cadeias de caracteres, e pode recuperá-los e convertê-los novamente em números ao usar o método `Parse` ou `TryParse` do tipo de dados numéricos.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-124">For example, you can store numeric values in a resource file by converting them to strings, and you can retrieve them and then convert them back to numbers by using the numeric data type's `Parse` or `TryParse` method.</span></span> <span data-ttu-id="a4d2e-125">Você pode converter imagens ou outros dados binários em uma representação de cadeia de caracteres ao chamar o método <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> e restaurá-los para uma matriz de bytes ao chamar o método <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-125">You can convert images or other binary data to a string representation by calling the <xref:System.Convert.ToBase64String%2A?displayProperty=nameWithType> method, and restore them to a byte array by calling the <xref:System.Convert.FromBase64String%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="the-includenetportableincludesnet-portable-mdmd-and-windows-store-apps"></a><span data-ttu-id="a4d2e-126">Os aplicativos do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] e da Windows Store</span><span class="sxs-lookup"><span data-stu-id="a4d2e-126">The [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] and Windows Store Apps</span></span>  
 <span data-ttu-id="a4d2e-127">Projetos do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] armazenam recursos em arquivos .resx que são compilados em arquivos .resources e inseridos no assembly principal ou em assemblies satélites em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-127">[!INCLUDE[net_portable](../../../includes/net-portable-md.md)] projects store resources in .resx files, which are then compiled into .resources files and embedded in the main assembly or in satellite assemblies at compile time.</span></span> <span data-ttu-id="a4d2e-128">Os aplicativos do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], por outro lado, exigem que os recursos sejam armazenados em arquivos .resw, que são compilados em um único arquivo de PRI (índice de recurso do pacote).</span><span class="sxs-lookup"><span data-stu-id="a4d2e-128">[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps, on the other hand, require resources to be stored in .resw files, which are then compiled into a single package resource index (PRI) file.</span></span> <span data-ttu-id="a4d2e-129">No entanto, independentemente dos formatos de arquivo incompatíveis, seu [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] funcionará em um aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4d2e-129">However, despite the incompatible file formats, your [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] will work in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span>  
  
 <span data-ttu-id="a4d2e-130">Para consumir sua biblioteca de classes do aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], adicione uma referência a ela em seu projeto de aplicativo da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-130">To consume your class library from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, add a reference to it in your Windows Store app project.</span></span> <span data-ttu-id="a4d2e-131">O Visual Studio extrairá de forma transparente os recursos de seu assembly em um arquivo .resw e os usará para gerar um arquivo de PRI do qual o [!INCLUDE[wrt](../../../includes/wrt-md.md)] poderá extrair recursos.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-131">Visual Studio will transparently extract the resources from your assembly into a .resw file and use it to generate a PRI file from which the [!INCLUDE[wrt](../../../includes/wrt-md.md)] can extract resources.</span></span> <span data-ttu-id="a4d2e-132">No tempo de execução, o [!INCLUDE[wrt](../../../includes/wrt-md.md)] executa o código em seu [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], mas recupera recursos de sua Biblioteca de Classes Portátil do arquivo de PRI.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-132">At run time, the [!INCLUDE[wrt](../../../includes/wrt-md.md)] executes the code in your [!INCLUDE[net_portable](../../../includes/net-portable-md.md)], but it retrieves your Portable Class Library's resources from the PRI file.</span></span>  
  
 <span data-ttu-id="a4d2e-133">Se seu projeto do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] incluir recursos localizados, use o modelo hub e spoke para implantá-los exatamente como faria para uma biblioteca em um aplicativo da área de trabalho.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-133">If your [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] project includes localized resources, you use the hub-and-spoke model to deploy them just as you would for a library in a desktop app.</span></span> <span data-ttu-id="a4d2e-134">Para consumir seu arquivo de recurso principal e quaisquer arquivos de recursos localizados em seu aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], adicione uma referência ao assembly principal.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-134">To consume your main resource file and any localized resource files in your [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, you add a reference to the main assembly.</span></span> <span data-ttu-id="a4d2e-135">No tempo de compilação, o Visual Studio extrai os recursos do arquivo de recursos principal e quaisquer arquivos de recursos localizados em arquivos .resw separados.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-135">At compile time, Visual Studio extracts the resources from your main resource file and any localized resource files into separate .resw files.</span></span> <span data-ttu-id="a4d2e-136">Em seguida, ele cria os arquivos .resw em um único arquivo de PRI que acessa o [!INCLUDE[wrt](../../../includes/wrt-md.md)] em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-136">It then compiles the .resw files into a single PRI file that the [!INCLUDE[wrt](../../../includes/wrt-md.md)] accesses at run time.</span></span>  
  
<a name="NonLoc"></a>   
## <a name="example-non-localized-includenetportableincludesnet-portable-mdmd"></a><span data-ttu-id="a4d2e-137">Exemplo: [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] não localizado</span><span class="sxs-lookup"><span data-stu-id="a4d2e-137">Example: Non-Localized [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]</span></span>  
 <span data-ttu-id="a4d2e-138">O exemplo simples e não localizado do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] a seguir usa recursos para armazenar os nomes das colunas e determinar o número de caracteres a serem reservados para dados tabulares.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-138">The following simple, non-localized [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] example uses resources to store the names of columns and to determine the number of characters to reserve for tabular data.</span></span> <span data-ttu-id="a4d2e-139">O exemplo usa um arquivo chamado LibResources.resx para armazenar os recursos de cadeia de caracteres listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-139">The example uses a file named LibResources.resx to store the string resources listed in the following table.</span></span>  
  
|<span data-ttu-id="a4d2e-140">Nome do recurso</span><span class="sxs-lookup"><span data-stu-id="a4d2e-140">Resource name</span></span>|<span data-ttu-id="a4d2e-141">Valor do recurso</span><span class="sxs-lookup"><span data-stu-id="a4d2e-141">Resource value</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="a4d2e-142">Born</span><span class="sxs-lookup"><span data-stu-id="a4d2e-142">Born</span></span>|<span data-ttu-id="a4d2e-143">Birthdate</span><span class="sxs-lookup"><span data-stu-id="a4d2e-143">Birthdate</span></span>|  
|<span data-ttu-id="a4d2e-144">BornLength</span><span class="sxs-lookup"><span data-stu-id="a4d2e-144">BornLength</span></span>|<span data-ttu-id="a4d2e-145">12</span><span class="sxs-lookup"><span data-stu-id="a4d2e-145">12</span></span>|  
|<span data-ttu-id="a4d2e-146">Hired</span><span class="sxs-lookup"><span data-stu-id="a4d2e-146">Hired</span></span>|<span data-ttu-id="a4d2e-147">Hire Date</span><span class="sxs-lookup"><span data-stu-id="a4d2e-147">Hire Date</span></span>|  
|<span data-ttu-id="a4d2e-148">HiredLength</span><span class="sxs-lookup"><span data-stu-id="a4d2e-148">HiredLength</span></span>|<span data-ttu-id="a4d2e-149">12</span><span class="sxs-lookup"><span data-stu-id="a4d2e-149">12</span></span>|  
|<span data-ttu-id="a4d2e-150">ID</span><span class="sxs-lookup"><span data-stu-id="a4d2e-150">ID</span></span>|<span data-ttu-id="a4d2e-151">ID</span><span class="sxs-lookup"><span data-stu-id="a4d2e-151">ID</span></span>|  
|<span data-ttu-id="a4d2e-152">ID.Length</span><span class="sxs-lookup"><span data-stu-id="a4d2e-152">ID.Length</span></span>|<span data-ttu-id="a4d2e-153">12</span><span class="sxs-lookup"><span data-stu-id="a4d2e-153">12</span></span>|  
|<span data-ttu-id="a4d2e-154">Nome</span><span class="sxs-lookup"><span data-stu-id="a4d2e-154">Name</span></span>|<span data-ttu-id="a4d2e-155">Nome</span><span class="sxs-lookup"><span data-stu-id="a4d2e-155">Name</span></span>|  
|<span data-ttu-id="a4d2e-156">NameLength</span><span class="sxs-lookup"><span data-stu-id="a4d2e-156">NameLength</span></span>|<span data-ttu-id="a4d2e-157">25</span><span class="sxs-lookup"><span data-stu-id="a4d2e-157">25</span></span>|  
|<span data-ttu-id="a4d2e-158">Título</span><span class="sxs-lookup"><span data-stu-id="a4d2e-158">Title</span></span>|<span data-ttu-id="a4d2e-159">Employee Database</span><span class="sxs-lookup"><span data-stu-id="a4d2e-159">Employee Database</span></span>|  
  
 <span data-ttu-id="a4d2e-160">O código a seguir define uma `UILibrary` classe que usa o wrapper do Gerenciador de recursos denominado `resources` gerado pelo Visual Studio quando o **modificador de acesso** para o arquivo é alterado para **público** .</span><span class="sxs-lookup"><span data-stu-id="a4d2e-160">The following code defines a `UILibrary` class that uses the Resource Manager wrapper named `resources` generated by Visual Studio when the **Access Modifier** for the file is changed to **Public**.</span></span> <span data-ttu-id="a4d2e-161">A classe UILibrary analisa os dados de cadeia de caracteres conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-161">The UILibrary class parses the string data as necessary.</span></span> <span data-ttu-id="a4d2e-162">.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-162">.</span></span> <span data-ttu-id="a4d2e-163">Observe que a classe está no namespace `MyCompany.Employees`.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-163">Note that the class is in the `MyCompany.Employees` namespace.</span></span>  
  
 [!code-csharp[Conceptual.Resources.Portable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/uilibrary.cs#1)]
 [!code-vb[Conceptual.Resources.Portable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/uilibrary.vb#1)]  
  
 <span data-ttu-id="a4d2e-164">O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo no modo de console.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-164">The following code illustrates how the `UILibrary` class and its resources can be accessed from a console-mode app.</span></span> <span data-ttu-id="a4d2e-165">Ele requer que uma referência a UILIbrary.dll seja adicionada ao projeto de aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-165">It requires a reference to UILIbrary.dll to be added to the console app project.</span></span>  
  
 [!code-csharp[Conceptual.Resources.Portable#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program.cs#2)]
 [!code-vb[Conceptual.Resources.Portable#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module1.vb#2)]  
  
 <span data-ttu-id="a4d2e-166">O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4d2e-166">The following code illustrates how the `UILibrary` class and its resources can be accessed from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span> <span data-ttu-id="a4d2e-167">Ele requer que uma referência a UILIbrary.dll seja adicionada ao projeto de aplicativo da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-167">It requires a reference to UILIbrary.dll to be added to the Windows Store app project.</span></span>  
  
 [!code-csharp[Conceptual.Resources.PortableMetro#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetro/cs/blankpage.xaml.cs#1)]  
  
## <a name="example-localized-includenetportableincludesnet-portable-mdmd"></a><span data-ttu-id="a4d2e-168">Exemplo: [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] localizado</span><span class="sxs-lookup"><span data-stu-id="a4d2e-168">Example: Localized [!INCLUDE[net_portable](../../../includes/net-portable-md.md)]</span></span>  
 <span data-ttu-id="a4d2e-169">O exemplo do [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] localizado a seguir inclui recursos para francês (França) e inglês (Estados Unidos).</span><span class="sxs-lookup"><span data-stu-id="a4d2e-169">The following localized [!INCLUDE[net_portable](../../../includes/net-portable-md.md)] example includes resources for the French (France) and English (United States) cultures.</span></span> <span data-ttu-id="a4d2e-170">A cultura do inglês (Estados Unidos) é a cultura padrão do aplicativo seus recursos são mostrados na tabela de [seção anterior](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc).</span><span class="sxs-lookup"><span data-stu-id="a4d2e-170">The English (United States) culture is the app's default culture; its resources are shown in the table in the [previous section](../../../docs/standard/cross-platform/app-resources-for-libraries-that-target-multiple-platforms.md#NonLoc).</span></span> <span data-ttu-id="a4d2e-171">O arquivo de recursos para francês (França) é chamado LibResources.fr-FR.resx e consiste nos recursos de cadeia de caracteres listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-171">The resources file for the French (France) culture is named LibResources.fr-FR.resx and consists of the string resources listed in the following table.</span></span> <span data-ttu-id="a4d2e-172">O código-fonte para a classe `UILibrary` é o mesmo mostrado na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-172">The source code for the `UILibrary` class is the same as that shown in the previous section.</span></span>  
  
|<span data-ttu-id="a4d2e-173">Nome do recurso</span><span class="sxs-lookup"><span data-stu-id="a4d2e-173">Resource name</span></span>|<span data-ttu-id="a4d2e-174">Valor do recurso</span><span class="sxs-lookup"><span data-stu-id="a4d2e-174">Resource value</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="a4d2e-175">Born</span><span class="sxs-lookup"><span data-stu-id="a4d2e-175">Born</span></span>|<span data-ttu-id="a4d2e-176">Date de naissance</span><span class="sxs-lookup"><span data-stu-id="a4d2e-176">Date de naissance</span></span>|  
|<span data-ttu-id="a4d2e-177">BornLength</span><span class="sxs-lookup"><span data-stu-id="a4d2e-177">BornLength</span></span>|<span data-ttu-id="a4d2e-178">20</span><span class="sxs-lookup"><span data-stu-id="a4d2e-178">20</span></span>|  
|<span data-ttu-id="a4d2e-179">Hired</span><span class="sxs-lookup"><span data-stu-id="a4d2e-179">Hired</span></span>|<span data-ttu-id="a4d2e-180">Date embauché</span><span class="sxs-lookup"><span data-stu-id="a4d2e-180">Date embauché</span></span>|  
|<span data-ttu-id="a4d2e-181">HiredLength</span><span class="sxs-lookup"><span data-stu-id="a4d2e-181">HiredLength</span></span>|<span data-ttu-id="a4d2e-182">16</span><span class="sxs-lookup"><span data-stu-id="a4d2e-182">16</span></span>|  
|<span data-ttu-id="a4d2e-183">ID</span><span class="sxs-lookup"><span data-stu-id="a4d2e-183">ID</span></span>|<span data-ttu-id="a4d2e-184">ID</span><span class="sxs-lookup"><span data-stu-id="a4d2e-184">ID</span></span>|  
|<span data-ttu-id="a4d2e-185">Nome</span><span class="sxs-lookup"><span data-stu-id="a4d2e-185">Name</span></span>|<span data-ttu-id="a4d2e-186">Nom</span><span class="sxs-lookup"><span data-stu-id="a4d2e-186">Nom</span></span>|  
|<span data-ttu-id="a4d2e-187">Título</span><span class="sxs-lookup"><span data-stu-id="a4d2e-187">Title</span></span>|<span data-ttu-id="a4d2e-188">Base de données des employés</span><span class="sxs-lookup"><span data-stu-id="a4d2e-188">Base de données des employés</span></span>|  
  
 <span data-ttu-id="a4d2e-189">O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo no modo de console.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-189">The following code illustrates how the `UILibrary` class and its resources can be accessed from a console-mode app.</span></span> <span data-ttu-id="a4d2e-190">Ele requer que uma referência a UILIbrary.dll seja adicionada ao projeto de aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-190">It requires a reference to UILIbrary.dll to be added to the console app project.</span></span>  
  
 [!code-csharp[Conceptual.Resources.Portable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portable/cs/program2.cs#3)]
 [!code-vb[Conceptual.Resources.Portable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portable/vb/module2.vb#3)]  
  
 <span data-ttu-id="a4d2e-191">O código a seguir ilustra como a classe `UILibrary` e seus recursos podem ser acessados de um aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a4d2e-191">The following code illustrates how the `UILibrary` class and its resources can be accessed from a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app.</span></span> <span data-ttu-id="a4d2e-192">Ele requer que uma referência a UILIbrary.dll seja adicionada ao projeto de aplicativo da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-192">It requires a reference to UILIbrary.dll to be added to the Windows Store app project.</span></span> <span data-ttu-id="a4d2e-193">Usa a propriedade estática `ApplicationLanguages.PrimaryLanguageOverride` para definir o idioma preferencial do aplicativo como francês.</span><span class="sxs-lookup"><span data-stu-id="a4d2e-193">It uses the static `ApplicationLanguages.PrimaryLanguageOverride` property to set the app's preferred language to French.</span></span>  
  
 [!code-csharp[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.portablemetroloc/cs/blankpage.xaml.cs#1)]
 [!code-vb[Conceptual.Resources.PortableMetroLoc#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.portablemetroloc/vb/blankpage.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a4d2e-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4d2e-194">See Also</span></span>  
 <xref:System.Resources.ResourceManager>  
 [<span data-ttu-id="a4d2e-195">Recursos em aplicativos de área de trabalho</span><span class="sxs-lookup"><span data-stu-id="a4d2e-195">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)  
 [<span data-ttu-id="a4d2e-196">Empacotando e implantando recursos</span><span class="sxs-lookup"><span data-stu-id="a4d2e-196">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)