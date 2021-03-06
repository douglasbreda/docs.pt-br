---
title: Como repetir uma animação
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 176fc9c31f85361a243cd9357d79608e0ff6a4cd
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855290"
---
# <a name="how-to-repeat-an-animation"></a>Como repetir uma animação
Este exemplo mostra como usar o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade de um <xref:System.Windows.Media.Animation.Timeline> para controlar o comportamento de repetição de uma animação.  
  
## <a name="example"></a>Exemplo  
 O <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade de um <xref:System.Windows.Media.Animation.Timeline> controla quantas vezes uma animação repete sua duração simples. Usando <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, você pode especificar que um <xref:System.Windows.Media.Animation.Timeline> se repete para um determinado número de vezes (uma contagem de iteração) ou por um período de tempo especificado. Em ambos os casos, a animação passa por quantas execuções do início ao fim forem necessárias para completar a contagem ou duração solicitada.  
  
 Por padrão, linhas de tempo têm uma contagem de repetição de 1,0, o que significa que elas são reproduzidas uma vez e não se repetem. No entanto, se você definir a <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade de um <xref:System.Windows.Media.Animation.Timeline> para <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, a linha do tempo se repete indefinidamente.  
  
 O exemplo a seguir mostra como usar o <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> propriedade para controlar o comportamento de repetição de uma animação. O exemplo anima a <xref:System.Windows.FrameworkElement.Width%2A> propriedade de cinco retângulos com cada retângulo usando um tipo diferente de comportamento de repetição.  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Para o exemplo completo, consulte [Exemplo de comportamento do tempo de animação](https://go.microsoft.com/fwlink/?LinkID=159970).  
  
## <a name="see-also"></a>Consulte também  
 [Acumular valores de animação durante ciclos de repetição](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [Especificar se uma linha do tempo é revertida automaticamente](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)  
 [Tópicos de instruções](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [Animação e tempo](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Visão geral da animação](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Amostra de comportamento de tempo da animação](https://go.microsoft.com/fwlink/?LinkID=159970)
