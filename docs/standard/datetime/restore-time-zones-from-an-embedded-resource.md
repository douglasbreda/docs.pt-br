---
title: 'Como: restaurar fusos horários de um recurso inserido'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], deserializing
- time zones [.NET Framework], restoring
ms.assetid: 6b7b4de9-da07-47e3-8f4c-823f81798ee7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99d38b336b5e655dd1c96682eec90c5fbe8469d6
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030702"
---
# <a name="how-to-restore-time-zones-from-an-embedded-resource"></a>Como: restaurar fusos horários de um recurso inserido

Este tópico descreve como restaurar fusos horários que tenha sido salvo em um arquivo de recurso. Para obter informações e instruções sobre como salvar fusos horários, consulte [como: salvar fusos horários em um recurso inserido](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md).

### <a name="to-deserialize-a-timezoneinfo-object-from-an-embedded-resource"></a>Para desserializar um objeto TimeZoneInfo de um recurso inserido

1. Se o fuso horário a ser recuperado não for um fuso horário personalizado, tente criar uma instância dele usando o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> método.

2. Criar uma instância de um <xref:System.Resources.ResourceManager> objeto, passando o nome totalmente qualificado do arquivo de recurso inserido e uma referência ao assembly que contém o arquivo de recurso.

   Se você não puder determinar o nome totalmente qualificado do arquivo de recurso inserido, use o [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) para examinar o manifesto do assembly. Um `.mresource` entrada identifica o recurso. No exemplo, o nome do recurso totalmente qualificado é `SerializeTimeZoneData.SerializedTimeZones`.

   Se o arquivo de recurso é incorporado no mesmo assembly que contém o código de instanciação de fuso horário, você pode recuperar uma referência a ele, chamando o `static` (`Shared` no Visual Basic) <xref:System.Reflection.Assembly.GetExecutingAssembly%2A> método.

3. Se a chamada para o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> método falhar, ou se for um fuso horário personalizado a ser instanciado, recuperar uma cadeia de caracteres que contenha o fuso horário serializado chamando o <xref:System.Resources.ResourceManager.GetString%2A?displayProperty=nameWithType> método.

4. Desserialize os dados de fuso horário chamando o <xref:System.TimeZoneInfo.FromSerializedString%2A> método.

## <a name="example"></a>Exemplo

O exemplo a seguir desserializa um <xref:System.TimeZoneInfo> objeto armazenado em um arquivo de recurso XML .NET incorporado.

[!code-csharp[TimeZone2.Serialization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#3)]
[!code-vb[TimeZone2.Serialization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#3)]

Esse código ilustra a manipulação de exceção para garantir que um <xref:System.TimeZoneInfo> objeto exigido pelo aplicativo está presente. Ele primeiro tenta criar uma instância de um <xref:System.TimeZoneInfo> objeto por recuperá-los a partir do registro usando o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> método. Se o fuso horário não pode ser instanciado, o código recupera do arquivo de recurso inserido.

Porque dados para fusos horários personalizados (fusos horários instanciados usando o <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> método) não são armazenadas no registro, o código chama o <xref:System.TimeZoneInfo.FindSystemTimeZoneById%2A> para instanciar o fuso horário para Palmer, Antártica. Em vez disso, ele imediatamente verifica o arquivo de recurso inserido para recuperar uma cadeia de caracteres que contém os dados da zona de tempo antes de chamar o <xref:System.TimeZoneInfo.FromSerializedString%2A> método.

## <a name="compiling-the-code"></a>Compilando o código

Este exemplo requer:

* Que uma referência à dll e dll seja adicionada ao projeto.

* Se os seguintes namespaces sejam importados:

  [!code-csharp[TimeZone2.Serialization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/TimeZone2.Serialization/cs/SerializeTimeZoneData.cs#2)]
  [!code-vb[TimeZone2.Serialization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/TimeZone2.Serialization/vb/SerializeTimeZoneData.vb#2)]

## <a name="see-also"></a>Consulte também

* [Datas, horas e fusos horários](../../../docs/standard/datetime/index.md)
* [Visão geral de fusos horários](../../../docs/standard/datetime/time-zone-overview.md)
* [Como salvar fusos horários em um recurso inserido](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md)
