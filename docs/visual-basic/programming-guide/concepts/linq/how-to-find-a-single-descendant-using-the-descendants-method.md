---
title: 'Como: localizar um único descendente usando o método de descendentes (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 0c03468c-efc8-4140-98f3-fb67acd9e8e1
ms.openlocfilehash: 5c4e857d28ab4660638198c054cf93bf94a621a7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33642825"
---
# <a name="how-to-find-a-single-descendant-using-the-descendants-method-visual-basic"></a>Como: localizar um único descendente usando o método de descendentes (Visual Basic)
Você pode usar o método de eixo <xref:System.Xml.Linq.XContainer.Descendants%2A> para rapidamente escrever código para localizar um único elemento nomeado exclusivamente. Essa técnica é especialmente útil quando você quer localizar um descendente específico com um nome específico. Você pode escrever o código para navegar para o elemento desejado, mas geralmente é mais rápido e fácil escrever código usando o eixo <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o operador padrão de consulta <xref:System.Linq.Enumerable.First%2A>.  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1>GC1 Value</GrandChild1>  
        </Child1>  
        <Child2>  
            <GrandChild2>GC2 Value</GrandChild2>  
        </Child2>  
        <Child3>  
            <GrandChild3>GC3 Value</GrandChild3>  
        </Child3>  
        <Child4>  
            <GrandChild4>GC4 Value</GrandChild4>  
        </Child4>  
    </Root>  
Dim grandChild3 As String = _  
    (From el In root...<GrandChild3> _  
    Select el).First()  
Console.WriteLine(grandChild3)  
```  
  
 Esse código gera a seguinte saída:  
  
```  
GC3 Value  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a mesma consulta para XML que está em um namespace. Para obter mais informações, consulte [trabalhando com Namespaces de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```vb  
Imports <xmlns:aw='http://www.adventure-works.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child1>  
                    <aw:GrandChild1>GC1 Value</aw:GrandChild1>  
                </aw:Child1>  
                <aw:Child2>  
                    <aw:GrandChild2>GC2 Value</aw:GrandChild2>  
                </aw:Child2>  
                <aw:Child3>  
                    <aw:GrandChild3>GC3 Value</aw:GrandChild3>  
                </aw:Child3>  
                <aw:Child4>  
                    <aw:GrandChild4>GC4 Value</aw:GrandChild4>  
                </aw:Child4>  
            </aw:Root>  
        Dim grandChild3 As String = _  
            (From el In root...<aw:GrandChild3> _  
            Select el).First()  
        Console.WriteLine(grandChild3)  
    End Sub  
End Module  
```  
  
 Esse código gera a seguinte saída:  
  
```  
GC3 Value  
```  
  
## <a name="see-also"></a>Consulte também  
 [Consultas básicas (LINQ para XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
