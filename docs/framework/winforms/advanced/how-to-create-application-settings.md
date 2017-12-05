---
title: "Como criar configurações de aplicativo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 481239b472ced5ef6251b665dad16e83a170607d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-application-settings"></a><span data-ttu-id="85e0f-102">Como criar configurações de aplicativo</span><span class="sxs-lookup"><span data-stu-id="85e0f-102">How to: Create Application Settings</span></span>
<span data-ttu-id="85e0f-103">Usando código gerenciado, é possível criar novas configurações de aplicativo e associá-las a propriedades no seu formulário ou aos controles de formulário, para que essas configurações sejam carregadas e salvas automaticamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="85e0f-103">Using managed code, you can create new application settings and bind them to properties on your form or your form's controls, so that these settings are loaded and saved automatically at run time.</span></span>  
  
 <span data-ttu-id="85e0f-104">No procedimento a seguir, você criar manualmente uma classe wrapper que deriva de <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="85e0f-104">In the following procedure, you manually create a wrapper class that derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="85e0f-105">Uma propriedade publicamente acessível é adicionada a essa classe para cada configuração de aplicativo que você desejar expor.</span><span class="sxs-lookup"><span data-stu-id="85e0f-105">To this class you add a publicly accessible property for each application setting that you want to expose.</span></span>  
  
 <span data-ttu-id="85e0f-106">Também é possível executar esse procedimento usando o mínimo de código possível no designer do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="85e0f-106">You can also perform this procedure using minimal code in the Visual Studio designer.</span></span>  <span data-ttu-id="85e0f-107">Consulte também [Como criar configurações de aplicativo usando o Designer](http://msdn.microsoft.com/library/wabtadw6\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="85e0f-107">Also see [How to: Create Application Settings Using the Designer](http://msdn.microsoft.com/library/wabtadw6\(v=vs.110\)).</span></span>  
  
### <a name="to-create-new-application-settings-programmatically"></a><span data-ttu-id="85e0f-108">Criar novas configurações de aplicativo com programação</span><span class="sxs-lookup"><span data-stu-id="85e0f-108">To create new Application Settings programmatically</span></span>  
  
1.  <span data-ttu-id="85e0f-109">Adicione uma nova classe ao seu projeto e renomeie-o.</span><span class="sxs-lookup"><span data-stu-id="85e0f-109">Add a new class to your project, and rename it.</span></span> <span data-ttu-id="85e0f-110">Para este procedimento, chamaremos essa classe de `MyUserSettings`.</span><span class="sxs-lookup"><span data-stu-id="85e0f-110">For this procedure, we will call this class `MyUserSettings`.</span></span> <span data-ttu-id="85e0f-111">Alterar a definição de classe para que a classe derivada de <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="85e0f-111">Change the class definition so that the class derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span>  
  
2.  <span data-ttu-id="85e0f-112">Definir uma propriedade nesta classe wrapper para cada configuração de aplicativo precisar e aplique essa propriedade ou com o <xref:System.Configuration.ApplicationScopedSettingAttribute> ou <xref:System.Configuration.UserScopedSettingAttribute>, dependendo do escopo da configuração.</span><span class="sxs-lookup"><span data-stu-id="85e0f-112">Define a property on this wrapper class for each application setting you require, and apply that property with either the <xref:System.Configuration.ApplicationScopedSettingAttribute> or <xref:System.Configuration.UserScopedSettingAttribute>, depending on the scope of the setting.</span></span> <span data-ttu-id="85e0f-113">Para obter mais informações sobre o escopo das configurações, consulte [Visão geral de configurações de aplicativo](../../../../docs/framework/winforms/advanced/application-settings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="85e0f-113">For more information about settings scope, see [Application Settings Overview](../../../../docs/framework/winforms/advanced/application-settings-overview.md).</span></span> <span data-ttu-id="85e0f-114">Agora, seu código deverá se parecer com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="85e0f-114">By now, your code should look like this:</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  <span data-ttu-id="85e0f-115">Crie uma instância dessa classe wrapper no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85e0f-115">Create an instance of this wrapper class in your application.</span></span> <span data-ttu-id="85e0f-116">Ela geralmente será um membro privado do formulário principal.</span><span class="sxs-lookup"><span data-stu-id="85e0f-116">It will commonly be a private member of the main form.</span></span> <span data-ttu-id="85e0f-117">Agora que você definiu sua classe, você precisa associá-lo a uma propriedade; Nesse caso, o <xref:System.Windows.Forms.Form.BackColor%2A> propriedades do formulário.</span><span class="sxs-lookup"><span data-stu-id="85e0f-117">Now that you have defined your class, you need to bind it to a property; in this case, the <xref:System.Windows.Forms.Form.BackColor%2A> property of your form.</span></span> <span data-ttu-id="85e0f-118">Você pode fazer isso no manipulador de eventos `Load` do seu formulário.</span><span class="sxs-lookup"><span data-stu-id="85e0f-118">You can accomplish this in your form's `Load` event handler.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="85e0f-119">Se você fornecer uma maneira de alterar as configurações no tempo de execução, será necessário salvar as configurações atuais do usuário no disco quando o formulário for fechado, caso contrário, essas alterações serão perdidas.</span><span class="sxs-lookup"><span data-stu-id="85e0f-119">If you provide a way to change settings at run time, you will need to save the user's current settings to disk when your form closes, or else these changes will be lost.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     <span data-ttu-id="85e0f-120">Agora você criou com êxito uma nova configuração de aplicativo e a associou à propriedade especificada.</span><span class="sxs-lookup"><span data-stu-id="85e0f-120">You have now successfully created a new application setting and bound it to the specified property.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="85e0f-121">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="85e0f-121">.NET Framework Security</span></span>  
 <span data-ttu-id="85e0f-122">O provedor de configurações padrão, <xref:System.Configuration.LocalFileSettingsProvider>, persiste as informações nos arquivos de configuração como texto sem formatação.</span><span class="sxs-lookup"><span data-stu-id="85e0f-122">The default settings provider, <xref:System.Configuration.LocalFileSettingsProvider>, persists information to configuration files as plain text.</span></span> <span data-ttu-id="85e0f-123">Isso limita a segurança à segurança de acesso aos arquivos fornecida pelo sistema operacional para o usuário atual.</span><span class="sxs-lookup"><span data-stu-id="85e0f-123">This limits security to the file access security provided by the operating system for the current user.</span></span> <span data-ttu-id="85e0f-124">Por isso, é necessário ter cuidado com as informações armazenadas nos arquivos de configuração.</span><span class="sxs-lookup"><span data-stu-id="85e0f-124">Because of this, care must be taken with the information stored in configuration files.</span></span> <span data-ttu-id="85e0f-125">Por exemplo, um uso comum para configurações de aplicativo é armazenar cadeias de conexão que apontam para o armazenamento de dados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85e0f-125">For example, one common use for application settings is to store connection strings that point to the application's data store.</span></span> <span data-ttu-id="85e0f-126">No entanto, devido a questões de segurança, tais cadeias de caracteres não devem incluir senhas.</span><span class="sxs-lookup"><span data-stu-id="85e0f-126">However, because of security concerns, such strings should not include passwords.</span></span> <span data-ttu-id="85e0f-127">Para obter mais informações sobre cadeias de caracteres de conexão, consulte <xref:System.Configuration.SpecialSetting>.</span><span class="sxs-lookup"><span data-stu-id="85e0f-127">For more information about connection strings, see <xref:System.Configuration.SpecialSetting>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e0f-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="85e0f-128">See Also</span></span>  
 <xref:System.Configuration.SpecialSettingAttribute>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [<span data-ttu-id="85e0f-129">Visão Geral das Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="85e0f-129">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="85e0f-130">Como Validar Configurações do Aplicativo</span><span class="sxs-lookup"><span data-stu-id="85e0f-130">How to: Validate Application Settings</span></span>](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)