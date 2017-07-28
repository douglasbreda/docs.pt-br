---
title: "Mpgo.exe (Ferramenta de Otimização Guiada por Perfil Gerenciado) | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Mpgo.exe
- training scenarios, generating profiles with
- Managed Profile Guided Optimization Tool
- Ngen.exe
- Ngen.exe, profilers and native images
ms.assetid: f6976502-a000-4fbe-aaf5-a7aab9ce4ec2
caps.latest.revision: 31
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 94dde0a1ae6d149a4161b90c19b329233c690ec5
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Ferramenta de Otimização Guiada por Perfil Gerenciado)
A Ferramenta de Otimização Guiada por Perfil Gerenciado (Mpgo.exe) é uma ferramenta de linha de comando que usa cenários de usuário final comuns para otimizar os assemblies de imagem nativa criados pelo [Gerador de Imagem Nativa (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). Essa ferramenta permite executar cenários de treinamento que geram dados de perfil. O [Gerador de Imagem Nativa (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) usa esses dados para otimizar seus assemblies de aplicativo de imagem nativa gerados. Um cenário de treinamento é uma execução de avaliação de um uso esperado do aplicativo. Mpgo.exe está disponível no Visual Studio Ultimate 2012 e em versões posteriores. Desde o [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], também é possível usar Mpgo.exe para otimizar aplicativos do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)].  
  
 A otimização guiada por perfil melhora o tempo de inicialização do aplicativo, a utilização da memória (tamanho do conjunto de trabalho) e a taxa de transferência coletando-se dados de cenários de treinamento e usando-os para otimizar o layout de imagens nativas.  
  
 Quando você encontrar problemas de desempenho em relação ao tempo de inicialização e ao tamanho do conjunto de trabalho para assemblies IL (Intermediate Language), será recomendável usar primeiro Ngen.exe para eliminar os custos de compilação JIT (just-in-time) e facilitar o compartilhamento de código. Se precisar de melhorias adicionais, você poderá usar Mpgo.exe para otimizar ainda mais o aplicativo. É possível usar os dados de desempenho com base nos assemblies de imagem nativa não otimizados como uma linha de base para avaliar os ganhos de desempenho. O uso de Mpgo.exe pode resultar em tempos de inicialização a frio mais rápidos e um tamanho do conjunto de trabalho menor. Mpgo.exe adiciona informações a assemblies IL usados por Ngen.exe para criar assemblies de imagem nativa otimizados. Para obter mais informações, consulte a entrada [Improving Launch Performance for your Desktop Applications](http://go.microsoft.com/fwlink/p/?LinkId=248943) (Melhorando o Desempenho de Inicialização dos Aplicativos de Área de Trabalho) no blog do .NET.  
  
 Essa ferramenta é instalada automaticamente com o Visual Studio. Para executar a ferramenta, use o Prompt de Comando do Desenvolvedor (ou o Prompt de Comando do Visual Studio no Windows 7) com credenciais de administrador e digite o seguinte no prompt de comando. Para obter mais informações, consulte [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Para aplicativos de área de trabalho:  
  
```  
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]  
```  
  
 Para aplicativos do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]:  
  
## <a name="syntax"></a>Sintaxe  
  
```  
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>  
```  
  
#### <a name="parameters"></a>Parâmetros  
 Todos os argumentos para Mpgo.exe não diferenciam maiúsculas de minúsculas. Os comandos são prefixados com um traço.  
  
> [!NOTE]
>  É possível usar `–Scenario` ou `–Import` como um comando exigido, mas não ambos. Nenhum dos parâmetros obrigatórios será usado se você especificar a opção `–Reset`.  
  
|Parâmetro obrigatório|Descrição|  
|------------------------|-----------------|  
|`-Scenario` \<*comando*><br /><br /> —ou—<br /><br /> `-Scenario` \<*packageName*><br /><br /> -ou-<br /><br /> `-Import` \<*diretório*>|Para aplicativos de área de trabalho, use `–Scenario` para especificar o comando para executar o aplicativo que você deseja otimizar, inclusive todos os argumentos de linha de comando. Use três conjuntos de aspas duplas em torno do *comando* caso ele especifique um caminho que inclua espaços, por exemplo: `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. Não use aspas duplas; elas não funcionarão corretamente se o *comando* incluir espaços.<br /><br /> -ou-<br /><br /> Para aplicativos do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], use `–Scenario` para especificar o pacote para o qual você deseja gerar informações de perfil. Se você especificar o nome para exibição do pacote ou o nome da família de pacotes, e não o nome do pacote completo, Mpgo.exe selecionará o pacote correspondente ao nome fornecido se houver apenas uma correspondência. Se vários pacotes corresponderem ao nome especificado, Mpgo.exe solicitará que você escolha um pacote.<br /><br /> —ou—<br /><br /> Use `-Import` para especificar que os dados de otimização dos assemblies otimizados anteriormente devem ser usados para otimizar os assemblies em `-AssemblyList`. *diretório* especifica o diretório que contém os arquivos otimizados anteriormente. Os assemblies especificados em `–AssemblyList` ou `–AssemblyListFile` são as novas versões dos assemblies que serão otimizados usando os dados dos arquivos importados. O uso dos dados de otimização da versão anterior dos assemblies permite otimizar versões mais recentes de assemblies sem executar novamente o cenário.  No entanto, se os assemblies importados e de destino incluírem um código bem diferente, os dados de otimização serão ineficazes. Os nomes de assembly especificados em `–AssemblyList` ou `–AssemblyListFile` devem estar presentes no diretório especificado por `–Import`*directory*. Use três conjuntos de aspas duplas em torno de *diretório* caso ele especifique um caminho que inclua espaços.<br /><br /> Você deve especificar `–Scenario` ou `–Import`, mas não ambos os parâmetros.|  
|`-OutDir` \<*diretório*>|O diretório no qual os assemblies otimizados devem ser colocados. Se um assembly já existir na pasta do diretório de saída, uma nova cópia será criada e um número de índice será acrescentado ao nome, por exemplo: *assemblyname*-1.exe. Use aspas duplas em torno de *directory* caso ele especifique um caminho que contenha espaços.|  
|`-AssemblyList` \<*assembly1 assembly2 ...*><br /><br /> —ou—<br /><br /> `-AssemblyListFile` \<*file*>|Uma lista de assemblies (incluindo arquivos .exe e .dll), separados por espaços, cujas informações de perfil você deseja coletar. É possível especificar `C:\Dir\*.dll` ou `*.dll` para selecionar todos os assemblies no diretório de trabalho designado ou atual. Consulte a seção Comentários para obter mais informações.<br /><br /> —ou—<br /><br /> Um arquivo de texto que contém a lista de assemblies cujas informações de perfil você deseja coletar, um assembly listado por linha. Se um nome de assembly começar com um hífen (-), use uma lista de arquivos de assembly ou renomeie o assembly.|  
|`-AppID` \<*appId*>|A ID do aplicativo no pacote especificado. Se você usar o curinga (\*), o Mpgo.exe tentará enumerar AppIDs no pacote e retornará a \<*package_family_name*>!App se falhar. Se você especificar uma cadeia de caracteres prefixada por um ponto de exclamação (!), Mpgo.exe concatenará o nome da família de pacotes com o argumento fornecido.|  
|`-Timeout` \<*segundos*>|O tempo para permitir que o aplicativo do [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] seja executado antes do aplicativo sair.|  
  
|Parâmetro opcional|Descrição|  
|------------------------|-----------------|  
|`-64bit`|Implementa os assemblies para sistemas 64 bits.  Você deve especificar esse parâmetro para assemblies 64 bits, mesmo que o assembly se declare como sendo 64 bits.|  
|`-ExeConfig` \<*filename*>|Especifica o arquivo de configuração usado pelo cenário para fornecer as informações de versão e carregador.|  
|`-f`|Força a inclusão dos dados de perfil em um assembly binário, mesmo que esteja assinado.  Se o assembly estiver assinado, ele deverá ser assinado novamente; do contrário, o assembly não será carregado e executado.|  
|`-Reset`|Redefine o ambiente para garantir que uma sessão de criação de perfil anulada não afete os assemblies e, em seguida, sai. O ambiente é redefinido por padrão antes e depois de uma sessão de criação de perfil.|  
|`-Timeout` \<*tempo em segundos*>|Especifica a duração da criação de perfil em segundos. Use um valor que seja um pouco maior do que os tempos de inicialização observados para aplicativos GUI. Ao final do período de tempo limite, os dados de perfil são registrados, ainda que o aplicativo continue sendo executado. Se você não definir essa opção, a criação de perfil continuará até o desligamento do aplicativo, quando os dados serão gravados.|  
|`-LeaveNativeImages`|Especifica que as imagens nativas instrumentadas não devem ser removidas após a execução do cenário. Essa opção é usada principalmente quando você está obtendo o aplicativo especificado para a execução do cenário. Isso evitará a recriação de imagens nativas para execuções subsequentes de Mpgo.exe. Quando você terminar de executar o aplicativo, talvez haja imagens nativas órfãs no cache caso você especifique essa opção. Nesse caso, execute Mpgo.exe com o mesmo cenário e a mesma lista de assemblies e use o parâmetro `–RemoveNativeImages` para remover essas imagens nativas.|  
|`-RemoveNativeImages`|Limpa uma execução em que `–LeaveNativeImages` foi especificado. Se você especificar `-RemoveNativeImages`, Mpgo.exe ignorará todos os argumentos, exceto `-64bit` e `–AssemblyList` e sairá depois da remoção de todas as imagens nativas instrumentadas.|  
  
## <a name="remarks"></a>Comentários  
 É possível usar `–AssemblyList` e `- AssemblyListFile` várias vezes na linha de comando.  
  
 Se você não especificar nomes de caminho completos ao especificar assemblies, Mpgo.exe examinará o diretório atual. Se você especificar um caminho incorreto, Mpgo.exe exibirá uma mensagem de erro, mas continuará gerando dados para outros assemblies. Se você especificar um assembly não carregado durante o cenário de treinamento, nenhum dado de treinamento será gerado para esse assembly.  
  
 Se um assembly na lista estiver no cache de assembly global, ele não será atualizado para conter informações de perfil.  Remova-o do cache de assembly global para coletar informações de perfil.  
  
 O uso de Ngen.exe e Mpgo.exe só é recomendado para grandes aplicativos gerenciados, porque o benefício de imagens nativas pré-compiladas só costuma ser visto quando elimina uma compilação JIT significativa no tempo de execução. A execução de Mpgo.exe em aplicativos ao estilo “Olá, Mundo” que não usam muito conjunto de trabalho não oferecerá nenhum benefício e Mpgo.exe pode até mesmo falhar na coleta de dados do perfil.  
  
> [!NOTE]
>  Ngen.exe e Mpgo.exe não são recomendados para aplicativos do ASP.NET e serviços do WCF (Windows Communication Foundation).  
  
## <a name="to-use-mpgoexe"></a>Para Usar Mpgo.exe  
  
1.  Use um computador que tenha o Visual Studio Ultimate 2012 e o aplicativo instalados.  
  
2.  Execute Mpgo.exe como um administrador com os parâmetros necessários.  Consulte a próxima seção para ver comandos de exemplo.  
  
     Os assemblies IL (linguagem intermediária) otimizados são criados na pasta especificada pelo parâmetro `–OutDir` (nos exemplos, essa é a pasta `C:\Optimized`).  
  
3.  Substitua os assemblies IL usados em Ngen.exe pelos novos assemblies IL que contêm as informações de perfil do diretório especificado por `–OutDir`.  
  
4.  A configuração do aplicativo (usando as imagens fornecidas por Mpgo.exe) instalará imagens nativas otimizadas.  
  
## <a name="suggested-workflow"></a>Fluxo de Trabalho Sugerido  
  
1.  Crie um conjunto de assemblies IL otimizados usando Mpgo.exe com o parâmetro `–Scenario`.  
  
2.  Verifique os assemblies IL otimizados no controle do código-fonte.  
  
3.  No processo de build, chame Mpgo.exe com o parâmetro `–Import` como uma etapa pós-build para gerar imagens IL otimizadas para passar para o Ngen.exe.  
  
 Esse processo garante que todos os assemblies tenham dados de otimização. Se você fizer check-in de assemblies otimizados atualizados (etapas 1 e 2) mais frequentemente, os números de desempenho serão mais consistentes durante todo o desenvolvimento do produto.  
  
## <a name="using-mpgoexe-from-visual-studio"></a>Usando Mpgo.exe com base no Visual Studio  
 É possível executar Mpgo.exe do Visual Studio (consulte o artigo [Como especificar eventos de build (C#)](http://msdn.microsoft.com/library/b4ce1ad9-5215-4b6f-b6a2-798b249aa335)) com as seguintes restrições:  
  
-   Não é possível usar caminhos entre aspas com marcas de barra à direita porque as macros do Visual Studio também usam marcas de barra à direita por padrão. (Por exemplo, `–OutDir "C:\Output Folder\"` é inválido.) Para solucionar essa restrição, é possível ignorar a barra à direita. (Por exemplo, use `-OutDir "$(OutDir)\"` em vez disso.)  
  
-   Por padrão, Mpgo.exe não está no caminho de compilação do Visual Studio. Você deve adicionar o caminho para o Visual Studio ou especificar o caminho completo na linha de comando de Mpgo. É possível usar o parâmetro `–Scenario` ou `–Import` no evento de pós-build no Visual Studio. No entanto, o processo típico é usar `–Scenario` uma vez de um prompt de comando do desenvolvedor do Visual Studio e, então, usar `–Import` para atualizar os assemblies otimizados após cada build, por exemplo: `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.  
  
<a name="samples"></a>   
## <a name="examples"></a>Exemplos  
 O seguinte comando de Mpgo.exe com base em um prompt de comando de desenvolvedor do Visual Studio otimiza um aplicativo de imposto:  
  
```  
mpgo –scenario "C:\MyApp\MyTax.exe /params par" –AssemblyList Mytax.dll MyTaxUtil2011.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 O seguinte comando de Mpgo.exe otimiza um aplicativo de som:  
  
```  
mpgo –scenario "C:\MyApp\wav2wma.exe –input song1.wav –output song1.wma" –AssemblyList transcode.dll –OutDir C:\Optimized –TimeOut 15  
```  
  
 O seguinte comando de Mpgo.exe usa dados de assemblies otimizados anteriormente para otimizar versões mais novas dos assemblies:  
  
```  
mpgo.exe -import "C:\Optimized" -assemblylist "C:\MyApp\MyTax.dll" "C:\MyApp\MyTaxUtil2011.dll" -outdir C:\ReOptimized  
```  
  
## <a name="see-also"></a>Consulte também  
 [Ngen.exe (Gerador de Imagens Nativas)](../../../docs/framework/tools/ngen-exe-native-image-generator.md)   
 [Prompts de Comando](../../../docs/framework/tools/developer-command-prompt-for-vs.md)   
 [Improving Launch Performance for your Desktop Applications (Melhorando o Desempenho de Inicialização dos Aplicativos de Área de Trabalho)](http://go.microsoft.com/fwlink/p/?LinkId=248943)   
 [Uma visão geral dos aprimoramentos de desempenho no .NET 4.5](http://go.microsoft.com/fwlink/p/?LinkId=249131)
