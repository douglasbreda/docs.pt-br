---
title: Armazenamentos de instância
ms.date: 03/30/2017
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
ms.openlocfilehash: 7ea29c3604042d773590448e31ce4ea95125ca1f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519572"
---
# <a name="instance-stores"></a>Armazenamentos de instância
Um armazenamento de instância é um contêiner lógico instâncias. É o local onde os dados e os metadados de instância são armazenados. Um armazenamento de instância não implica o armazenamento físico dedicado. Um armazenamento de instância pode conter informações durável em uma base de dados SQL Server ou em uma informações de estado não durável na memória. Os vem de [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] com a instância Store de fluxo de trabalho SQL, que é uma implementação concreta de um armazenamento de instância que permite que os fluxos de trabalho persistam dados e metadados de instância em uma base de dados SQL Server 2005 ou SQL Server 2008. Além a tela de aplicativo Windows Server também fornece uma implementação concreta de um armazenamento de instância. Para obter mais informações, consulte [Store de instância do Windows Server App Fabric, consulta e provedores de controle](https://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409).  
  
 Persistência API é a interface entre um host e um armazenamento de instância que permite que o host enviar solicitações de comando (por exemplo, <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> e <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) para o armazenamento de instância. A implementação concreta deste API é chamado um provedor de persistência. O provedor de persistência recebe solicitações de um host e altera o armazenamento de instância.  
  
 Hosts e armazenamentos de instância são pluggable de modo que um host pode ser usado com muitos armazenamentos de instância, e um armazenamento de instância pode ser usado com muitos host. Um armazenamento de instância é otimizado para normalmente os padrões de uso de um host específico, embora o armazenamento e o host de instância possa evoluir em ciclos de vida independente. Por exemplo, o **WorkflowServiceHost** e o **SqlWorkflowInstanceStore** são projetados para funcionar bem juntos. Você pode criar seu próprio armazenamento de instância para persistir dados e metadados de instâncias de serviço de fluxo de trabalho e usar esse armazenamento de instância com o **WorkflowServiceHost**. Por exemplo, você pode criar um OracleWorkflowInstanceStore que permite fluxos de trabalho manter informações em uma base de dados Oracle em vez de salvar em uma base de dados SQL Server.  
  
 É comum para hosts sejam estendidos com funcionalidade adicional que altera os objetos persistentes. Por exemplo, um sistema de persistência de instância pode ter um host de fluxo de trabalho, uma extensão com suporte para a operação "Suspender" e um armazenamento de instância do SQL.  O host de fluxo de trabalho pode enviar um comando padrão como salvar ou carregá-lo para salvar ou carregar um fluxo de trabalho de um armazenamento de instância ou para salvar um fluxo de trabalho em um armazenamento de instância. A extensão de suspensão pode adicionar a semântica adicional para comandos para salvar e carregar instâncias de fluxo de trabalho de forma que uma instância suspendida de fluxo de trabalho não pode ser carregada. O provedor de persistência para o armazenamento de instância de SQL entenda os comandos para salvar e carregar instâncias de fluxo de trabalho, e implementa os comandos chamando procedimentos armazenados apropriadas que alteram as tabelas de objetos persistentes em uma base de dados SQL Server.  
  
 Um host atua como um proprietário de instância em um armazenamento de instância. Um host pode atuar como mais de um proprietário da instância com mais de uma instância armazena ao mesmo tempo. O host fornece as chaves de GUIDs por exemplo associadas com instâncias. Uma chave de instância é um alias exclusivos que identifiquem uma instância. O sistema de persistência cria, atualizações, e informações do proprietário de instância exclui como executar comandos por aplicativos host.  
  
 A lista a seguir contém as etapas importantes envolvidas na interação de host com o armazenamento de instância:  
  
1.  Obter um **InstanceStore** de um provedor de persistência.  

2.  Obter o identificador para uma instância chamando o <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> método em de **InstanceStore**.  
  
3.  Chamar comandos contra o identificador de instância chamando o <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> método em de **InstanceStore**.  
  
4.  Examine os <xref:System.Runtime.DurableInstancing.InstanceView> retornado por **Instancestore** para determinar os resultados dos comandos.
