---
title: "Extensão de marcação x:Type"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: ed0372349a08687fd83b0fc989cc4cb88c29d96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="xtype-markup-extension"></a><span data-ttu-id="242c3-102">Extensão de marcação x:Type</span><span class="sxs-lookup"><span data-stu-id="242c3-102">x:Type Markup Extension</span></span>
<span data-ttu-id="242c3-103">Fornece o CLR <xref:System.Type> objeto que é o tipo base para um tipo XAML especificado.</span><span class="sxs-lookup"><span data-stu-id="242c3-103">Supplies the CLR <xref:System.Type> object that is the underlying type for a specified XAML type.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="242c3-104">Uso do Atributo XAML</span><span class="sxs-lookup"><span data-stu-id="242c3-104">XAML Attribute Usage</span></span>  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="242c3-105">Uso de elemento Object do XAML</span><span class="sxs-lookup"><span data-stu-id="242c3-105">XAML Object Element Usage</span></span>  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="242c3-106">Valores XAML</span><span class="sxs-lookup"><span data-stu-id="242c3-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`prefix`|<span data-ttu-id="242c3-107">Opcional.</span><span class="sxs-lookup"><span data-stu-id="242c3-107">Optional.</span></span> <span data-ttu-id="242c3-108">Um prefixo que mapeia um namespace XAML não padrão.</span><span class="sxs-lookup"><span data-stu-id="242c3-108">A prefix that maps a non-default XAML namespace.</span></span> <span data-ttu-id="242c3-109">Especificar um prefixo com frequência não é necessário.</span><span class="sxs-lookup"><span data-stu-id="242c3-109">Specifying a prefix is frequently not necessary.</span></span> <span data-ttu-id="242c3-110">Consulte Observações.</span><span class="sxs-lookup"><span data-stu-id="242c3-110">See Remarks.</span></span>|  
|`typeNameValue`|<span data-ttu-id="242c3-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="242c3-111">Required.</span></span> <span data-ttu-id="242c3-112">Um nome de tipo pode ser resolvido para o namespace XAML padrão atual; ou o prefixo mapeado se `prefix` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="242c3-112">A type name resolvable to the current default XAML namespace; or the specified mapped prefix if `prefix` is supplied.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="242c3-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="242c3-113">Remarks</span></span>  
 <span data-ttu-id="242c3-114">O `x:Type` extensão de marcação tem uma função semelhante para o `typeof()` operador em [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] ou `GetType` operador em [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="242c3-114">The `x:Type` markup extension has a similar function to the `typeof()` operator in [!INCLUDE[TLA#tla_cshrp](../../../includes/tlasharptla-cshrp-md.md)] or the `GetType` operator in [!INCLUDE[TLA#tla_visualb](../../../includes/tlasharptla-visualb-md.md)].</span></span>  
  
 <span data-ttu-id="242c3-115">O `x:Type` extensão de marcação fornece um comportamento de conversão de cadeia de caracteres para propriedades que usam o tipo <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="242c3-115">The `x:Type` markup extension supplies a from-string conversion behavior for properties that take the type <xref:System.Type>.</span></span> <span data-ttu-id="242c3-116">A entrada é um tipo XAML.</span><span class="sxs-lookup"><span data-stu-id="242c3-116">The input is a XAML type.</span></span> <span data-ttu-id="242c3-117">A relação entre o tipo de XAML de entrada e saída CLR <xref:System.Type> é que a saída <xref:System.Type> é o <xref:System.Xaml.XamlType.UnderlyingType%2A> da entrada <xref:System.Xaml.XamlType>, depois de pesquisar necessários <xref:System.Xaml.XamlType> com base no contexto do esquema XAML e o <xref:System.Windows.Markup.IXamlTypeResolver>fornece o contexto de serviço.</span><span class="sxs-lookup"><span data-stu-id="242c3-117">The relationship between the input XAML type and the output CLR <xref:System.Type> is that the output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input <xref:System.Xaml.XamlType>, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="242c3-118">Em serviços de XAML do .NET Framework, o tratamento para esta extensão de marcação é definida pelo <xref:System.Windows.Markup.TypeExtension> classe.</span><span class="sxs-lookup"><span data-stu-id="242c3-118">In .NET Framework XAML Services, the handling for this markup extension is defined by the <xref:System.Windows.Markup.TypeExtension> class.</span></span>  
  
 <span data-ttu-id="242c3-119">Implementações de estruturas específicas, algumas propriedades que exijam <xref:System.Type> como um valor pode aceitar o nome do tipo diretamente (o valor de cadeia de caracteres do tipo `Name`).</span><span class="sxs-lookup"><span data-stu-id="242c3-119">In specific framework implementations, some properties that take <xref:System.Type> as a value can accept the name of the type directly (the string value of the type `Name`).</span></span> <span data-ttu-id="242c3-120">No entanto, a implementação esse comportamento é um cenário complexo.</span><span class="sxs-lookup"><span data-stu-id="242c3-120">However, implementing this behavior is a complex scenario.</span></span> <span data-ttu-id="242c3-121">Para obter exemplos, consulte a seção "Observações de uso do WPF" que segue.</span><span class="sxs-lookup"><span data-stu-id="242c3-121">For examples, see the "WPF Usage Notes" section that follows.</span></span>  
  
 <span data-ttu-id="242c3-122">A sintaxe de atributo é a sintaxe mais comum usada com essa extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="242c3-122">Attribute syntax is the most common syntax used with this markup extension.</span></span> <span data-ttu-id="242c3-123">O token da cadeia de caracteres fornecido após a cadeia de caracteres identificadora `x:Type` é atribuído como o valor <xref:System.Windows.Markup.TypeExtension.TypeName%2A> da classe de extensão subjacente <xref:System.Windows.Markup.TypeExtension>.</span><span class="sxs-lookup"><span data-stu-id="242c3-123">The string token provided after the `x:Type` identifier string is assigned as the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> value of the underlying <xref:System.Windows.Markup.TypeExtension> extension class.</span></span> <span data-ttu-id="242c3-124">Sob o contexto do esquema padrão XAML para serviços de XAML do .NET Framework, que se baseia em tipos CLR, o valor desse atributo é o <xref:System.Reflection.MemberInfo.Name%2A> do tipo desejado, ou contém que <xref:System.Reflection.MemberInfo.Name%2A> precedido por um prefixo de namespace do XAML não padrão mapeamento.</span><span class="sxs-lookup"><span data-stu-id="242c3-124">Under the default XAML schema context for .NET Framework XAML Services, which is based on CLR types, the value of this attribute is either the <xref:System.Reflection.MemberInfo.Name%2A> of the desired type, or contains that <xref:System.Reflection.MemberInfo.Name%2A> preceded by a prefix for a non-default XAML namespace mapping.</span></span>  
  
 <span data-ttu-id="242c3-125">O `x:Type` extensão de marcação pode ser usada na sintaxe de elemento de objeto.</span><span class="sxs-lookup"><span data-stu-id="242c3-125">The `x:Type` markup extension can be used in object element syntax.</span></span> <span data-ttu-id="242c3-126">Nesse caso, especificando o valor de <xref:System.Windows.Markup.TypeExtension.TypeName%2A> propriedade é necessária para inicializar adequadamente a extensão.</span><span class="sxs-lookup"><span data-stu-id="242c3-126">In this case, specifying the value of the <xref:System.Windows.Markup.TypeExtension.TypeName%2A> property is required to properly initialize the extension.</span></span>  
  
 <span data-ttu-id="242c3-127">O `x:Type` extensão de marcação também pode ser usada como um atributo detalhado; no entanto esse uso não é comum: `<``object``property``="{x:Type TypeName=``typeNameValue``}" .../>`</span><span class="sxs-lookup"><span data-stu-id="242c3-127">The `x:Type` markup extension can also be used as a verbose attribute; however this use is not typical: `<``object` `property``="{x:Type TypeName=``typeNameValue``}" .../>`</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="242c3-128">Observações de uso do WPF</span><span class="sxs-lookup"><span data-stu-id="242c3-128">WPF Usage Notes</span></span>  
  
### <a name="default-xaml-namespace-and-type-mapping"></a><span data-ttu-id="242c3-129">Namespace XAML e mapeamento de tipo padrão</span><span class="sxs-lookup"><span data-stu-id="242c3-129">Default XAML Namespace and Type Mapping</span></span>  
 <span data-ttu-id="242c3-130">O namespace XAML padrão de programação WPF contém a maioria dos tipos de XAML que é necessário para cenários típicos de XAML; Portanto, você geralmente pode evitar prefixos ao fazer referência a valores de tipo XAML.</span><span class="sxs-lookup"><span data-stu-id="242c3-130">The default XAML namespace for WPF programming contains most of the XAML types you need for typical XAML scenarios; therefore, you can often avoid prefixes when referencing XAML type values.</span></span> <span data-ttu-id="242c3-131">Você precisará mapear um prefixo se você está fazendo referência a um tipo de um assembly personalizado ou para tipos que existem em um assembly do WPF, mas são de um namespace CLR que não foi mapeado para o namespace XAML padrão.</span><span class="sxs-lookup"><span data-stu-id="242c3-131">You might need to map a prefix if you are referencing a type from a custom assembly or for types that exist in a WPF assembly but are from a CLR namespace that was not mapped to the default XAML namespace.</span></span> <span data-ttu-id="242c3-132">Para obter mais informações sobre prefixos, namespaces XAML e namespaces CLR de mapeamento, consulte [Namespaces XAML e o mapeamento de Namespace para WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="242c3-132">For more information about prefixes, XAML namespaces, and mapping CLR namespaces, see [XAML Namespaces and Namespace Mapping for WPF XAML](../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md).</span></span>  
  
### <a name="type-properties-that-support-typename-as-string"></a><span data-ttu-id="242c3-133">Esse suporte Typename como cadeia de propriedades de tipo</span><span class="sxs-lookup"><span data-stu-id="242c3-133">Type Properties That Support Typename-as-String</span></span>  
 <span data-ttu-id="242c3-134">Técnicas que permitem especificar o valor de algumas propriedades do tipo oferece suporte a WPF <xref:System.Type> sem a necessidade de um `x:Type` uso de extensão de marcação.</span><span class="sxs-lookup"><span data-stu-id="242c3-134">WPF supports techniques that enable specifying the value of some properties of type <xref:System.Type> without requiring an `x:Type` markup extension usage.</span></span> <span data-ttu-id="242c3-135">Em vez disso, você pode especificar o valor como uma cadeia de caracteres que nomeia o tipo.</span><span class="sxs-lookup"><span data-stu-id="242c3-135">Instead, you can specify the value as a string that names the type.</span></span> <span data-ttu-id="242c3-136">Exemplos são <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> e <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="242c3-136">Examples of this are <xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> and <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="242c3-137">Suporte para esse comportamento não é fornecido por meio de conversores de tipo ou extensões de marcação.</span><span class="sxs-lookup"><span data-stu-id="242c3-137">Support for this behavior is not provided through either type converters or markup extensions.</span></span> <span data-ttu-id="242c3-138">Em vez disso, este é um comportamento de adiamento implementado por meio de <xref:System.Windows.FrameworkElementFactory>.</span><span class="sxs-lookup"><span data-stu-id="242c3-138">Instead, this is a deferral behavior implemented through <xref:System.Windows.FrameworkElementFactory>.</span></span>  
  
 <span data-ttu-id="242c3-139">O Silverlight oferece suporte a uma convenção semelhante.</span><span class="sxs-lookup"><span data-stu-id="242c3-139">Silverlight supports a similar convention.</span></span> <span data-ttu-id="242c3-140">Na verdade, o Silverlight não oferece suporte a `{x:Type}` em seu suporte de linguagem XAML e não aceita `{x:Type}` usos fora algumas circunstâncias que pretendem oferecer suporte à migração de XAML do Silverlight do WPF.</span><span class="sxs-lookup"><span data-stu-id="242c3-140">In fact, Silverlight does not currently support `{x:Type}` in its XAML language support, and does not accept `{x:Type}` usages outside of a few circumstances that are intended to support WPF-Silverlight XAML migration.</span></span> <span data-ttu-id="242c3-141">Portanto, o comportamento de typename como cadeia de caracteres é integrado para todos os avaliação de propriedade nativa do Silverlight em que um <xref:System.Type> é o valor.</span><span class="sxs-lookup"><span data-stu-id="242c3-141">Therefore, the typename-as-string behavior is built-in to all Silverlight native property evaluation where a <xref:System.Type> is the value.</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="242c3-142">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="242c3-142">XAML 2009</span></span>  
 <span data-ttu-id="242c3-143">XAML 2009 fornece suporte adicional para genérico, tipos e modifica o comportamento do recurso de `x:TypeArguments` e `x:Type` para oferecer esse suporte.</span><span class="sxs-lookup"><span data-stu-id="242c3-143">XAML 2009 provides additional support for generic types and modifies the feature behavior of `x:TypeArguments` and `x:Type` to provide this support.</span></span>  
  
-   <span data-ttu-id="242c3-144">`x:TypeArguments`e o elemento de objeto associado para uma instanciação genérica de objetos pode ser em elementos diferentes de raiz.</span><span class="sxs-lookup"><span data-stu-id="242c3-144">`x:TypeArguments` and the associated object element for a generic object instantiation can be on elements other than the root.</span></span> <span data-ttu-id="242c3-145">Para obter mais informações, consulte a seção "XAML 2009" [diretiva X:TypeArguments](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span><span class="sxs-lookup"><span data-stu-id="242c3-145">For more information, see the "XAML 2009" section of [x:TypeArguments Directive](../../../docs/framework/xaml-services/x-typearguments-directive.md).</span></span>  
  
-   <span data-ttu-id="242c3-146">XAML 2009 dá suporte a uma sintaxe para especificar a restrição de um tipo genérico na marcação.</span><span class="sxs-lookup"><span data-stu-id="242c3-146">XAML 2009 supports a syntax for specifying a generic type's constraint in markup.</span></span> <span data-ttu-id="242c3-147">Isso pode ser usado por `x:TypeArguments`, por `x:Type`, ou os dois recursos em combinação.</span><span class="sxs-lookup"><span data-stu-id="242c3-147">This can be used by `x:TypeArguments`, by `x:Type`, or by the two features in combination.</span></span>  
  
-   <span data-ttu-id="242c3-148">Implementação de WPF XAML durante o processamento de XAML 2009 para carga também adiciona esse recurso para o comportamento de conversão de tipo implícito para determinadas propriedades de estrutura que usam tipo <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="242c3-148">WPF XAML implementation when processing XAML 2009 for load also adds this capability to the implicit type conversion behavior for certain framework properties that use type <xref:System.Type>.</span></span>  
  
 <span data-ttu-id="242c3-149">No WPF, você pode usar recursos XAML 2009 mas somente para XAML livre (XAML não marcação-compilado).</span><span class="sxs-lookup"><span data-stu-id="242c3-149">In WPF, you can use XAML 2009 features but only for loose XAML (XAML that is not markup-compiled).</span></span> <span data-ttu-id="242c3-150">Compilação de marcação XAML WPF e do formulário BAML do XAML atualmente não dão os recursos e as palavras-chave de XAML 2009.</span><span class="sxs-lookup"><span data-stu-id="242c3-150">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="242c3-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="242c3-151">See Also</span></span>  
 <xref:System.Windows.Style>  
 [<span data-ttu-id="242c3-152">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="242c3-152">Styling and Templating</span></span>](../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="242c3-153">Visão geral de XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="242c3-153">XAML Overview (WPF)</span></span>](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="242c3-154">Extensões de marcação e XAML WPF</span><span class="sxs-lookup"><span data-stu-id="242c3-154">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)