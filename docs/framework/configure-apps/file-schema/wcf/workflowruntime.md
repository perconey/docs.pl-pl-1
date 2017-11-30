---
title: '&lt;Obiekt workflowRuntime&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 304c70fa-78d1-4d0f-b89f-0ca23d734c6f
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ad33eee445e04d1e43fa8b15e92c08cd48c11b11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltworkflowruntimegt"></a>&lt;Obiekt workflowRuntime&gt;
Określa ustawienia dla wystąpienia <xref:System.Workflow.Runtime.WorkflowRuntime> hostingu opartego o przepływ pracy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usług.  
  
 \<System. ServiceModel >  
\<zachowania >  
\<serviceBehaviors >  
\<zachowanie >  
\<Obiekt workflowRuntime >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<workflowRuntime cachedInstanceExpiration="TimeSpan"  
                                  enablePerformanceCounters="Boolean"  
                                  name="String"  
                                  validateOnCreate="Boolean">  
                 <commonParameters>  
                    <add name="String" value="String" />  
                 </commonParameters>  
                 <services>  
                    <add type="String"/>  
                 </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|cachedInstanceExpiration|Opcjonalny <xref:System.TimeSpan> wartość, która określa maksymalny czas trwania wystąpienia przepływu pracy mogą pozostać w pamięci w stanie bezczynności przed jej wymuszeniem wyładowania lub zostało przerwane. Jeśli ma elementu workflowruntime `PersistenceService` który wykonuje unloadOnIdle, ten atrybut jest ignorowany.|  
|enablePerformanceCounters|Opcjonalna wartość logiczna określająca, czy liczniki wydajności są włączone. Liczniki wydajności zawierają informacje dotyczące różnych statystyki związane z przepływu pracy, ale ich spowodować spadek wydajności podczas uruchamiania aparatu wykonawczego workflow i uruchomionych wystąpień przepływu pracy. Wartość domyślna to `true`.|  
|nazwa|Ciąg zawierający nazwę środowiska uruchomieniowego przepływu. Nazwa jest używana w danych wyjściowych do odróżnienia to środowisko uruchomieniowe od innych środowisk uruchomieniowych, które mogą być uruchomione na komputerze, na przykład liczników wydajności.<br /><br /> Wartość domyślna to ciąg pusty.|  
|validateOnCreate|Opcjonalna wartość logiczna określająca, czy Walidacja definicji przepływu pracy nastąpi przy otwarciu WorkflowServiceHost.  Jeśli ten atrybut ma wartość `true`, sprawdzanie poprawności przepływu pracy jest wykonywane zawsze `WorkflowServiceHost.Open` jest wywoływana. W przypadku znalezienia błędów sprawdzania poprawności <xref:System.Workflow.ComponentModel.Compiler.WorkflowValidationFailedException> , jest zgłaszany błąd.<br /><br /> Jeśli ta właściwość jest równa `false`, weryfikacja definicji przepływu pracy nie zostanie wykonana.<br /><br /> Wartość domyślna dla tej właściwości to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|commonParameters|Kolekcja wspólnych parametrów używane przez usługi. Ta kolekcja zazwyczaj uwzględnia parametry połączenia bazy danych, które mogą być współużytkowane przez usługi trwałe.|  
|usługi|Kolekcja usług, które zostaną dodane do <xref:System.Workflow.Runtime.WorkflowRuntime> aparatu. Elementy są typu <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.  Usług określonych w kolekcji zostanie zainicjowany przez aparat środowiska uruchomieniowego przepływu pracy i dodawane do jej usług podczas odpowiednie <xref:System.Workflow.Runtime.WorkflowRuntime> Konstruktor jest wywoływany. W związku z tym usługi określona w kolekcji należy wykonać niektóre zasady dotyczące podpisy ich konstruktorów. Aby uzyskać więcej informacji, zobacz <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji na temat używania pliku konfiguracji do sterowania zachowaniem <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu aplikacji hosta Windows Workflow Foundation, zobacz [pliki konfiguracji przepływu pracy](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).  
  
## <a name="example"></a>Przykład  
  
```xml  
<serviceBehaviors>  
   <behavior name="ServiceBehavior">  
      <workflowRuntime name="WorkflowServiceHostRuntime"  
                       validateOnCreate="true"  
                       enablePerformanceCounters="true">  
         <commonParameters>  
            <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
            <add name="EnableRetries" value="True" />  
         </commonParameters>  
         <services>  
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>  
         </services>  
      </workflowRuntime>  
   </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [Pliki konfiguracji przepływu pracy](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)