---
title: Aplicativos de n camadas e remoto com LINQ to SQL
ms.date: 03/30/2017
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
ms.openlocfilehash: 10eec92dcb9fdc5329f2cf19336ccc11f8bd181a
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032576"
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a>Aplicativos de n camadas e remoto com LINQ to SQL
Você pode criar aplicativos de n camadas ou multicamadas que usam [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Normalmente, o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] contexto de dados, classes de entidade e lógica de construção de consulta estão localizados na camada intermediária, como a camada de acesso de dados (DAL). A lógica comercial e todos os dados não persistentes podem ser completamente implementados em classes e métodos parciais nas entidades e de contexto de dados, ou pode ser implementado em classes separados.

 O cliente ou a camada de apresentação chamam métodos na interface remoto de camada intermediária, e o DAL na camada executará as consultas ou procedimentos armazenados que são mapeados para os métodos de <xref:System.Data.Linq.DataContext> . A camada intermediária retorna os dados para clientes geralmente como representações de XML de entidades ou objetos de proxy.

 Na camada intermediária, as entidades são criadas pelo contexto de dados, que acompanha seu estado, e gerencia a carga de exceção e o envio de alterações ao base de dados. Essas entidades são anexados” a “ `DataContext`. No entanto, depois que as entidades são enviadas a outra camada com a serialização, ficam destacadas, que significa que `DataContext` já não estiver controlando seu estado. As entidades que o cliente envia novamente para atualizações devem ser reatadas ao contexto de dados antes que [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pode enviar as alterações para o base de dados. O cliente é responsável por fornecer valores originais e/ou os carimbos de data/hora de volta a camada intermediária se esses são necessários para concorrência otimista verificações.

 Em aplicativos ASP.NET, <xref:System.Web.UI.WebControls.LinqDataSource> gerencia a maioria da complexidade. Para obter mais informações, consulte [NIB: Visão geral do controle de servidor Web LinqDataSource](https://msdn.microsoft.com/library/104cfc3f-7385-47d3-8a51-830dfa791136).

## <a name="additional-resources"></a>Recursos adicionais
 Para obter mais informações sobre como implementar aplicativos de n camadas que usam [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], consulte os seguintes tópicos:

-   [LINQ to SQL de N camadas com o ASP.NET](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)

-   [LINQ to SQL de N camadas com serviços Web](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md) 

-   [Implementando lógica de negócios de N camadas](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)

-   [Recuperação de dados e operações de CUD em aplicativos de N camadas (LINQ to SQL)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)

 Para obter mais informações sobre aplicativos de n camadas que usam DataSets ADO.NET, consulte [trabalhar com conjuntos de dados em aplicativos de n camadas](/visualstudio/data-tools/work-with-datasets-in-n-tier-applications).

## <a name="see-also"></a>Consulte também
 [Informações gerais](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
