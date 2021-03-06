---
title: '&lt;tracking&gt; w WCF'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 70cfaf24-a91c-4e56-ac47-d2ed87a963b3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7475c4a083d27e9c34e3662393981297c93580f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lttrackinggt-of-wcf"></a>&lt;tracking&gt; w WCF
Reprezentuje sekcję konfiguracji do definiowania ustawień śledzenia dla usługi przepływu pracy.  
  
 Aby uzyskać więcej informacji w śledzenia przepływu pracy i jego konfiguracja, zobacz [przepływu pracy śledzenia i śledzenia](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md) i [Konfigurowanie śledzenia przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).  
  
 \<system.serviceModel >  
\<Śledzenie >  
  
## <a name="syntax"></a>Składnia  
  
```xml
   <system.serviceModel>  <tracking>       <participants>       <add name="String"            profileName="String"           type="String" />      </participants>     <trackingProfile name="String">      <workflow activityDefinitionId="String">          <activityScheduledQueries>             <activityScheduledQuery activityName="String"                 childActivityName="String"/>          </activityScheduledQueries>             <activityStateQuery activityName="String" />                <arguments>                   <argument name="String"/>                </arguments>                <states>                   <state name="String"/>                </states>                <variables>                   <variable name="String"/>                </variables>          </activityStateQueries>          <bookmarkResumptionQueries>             <bookmarkResumptionQuery name="String" />          </bookmarkResumptionQueries>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>          <customTrackingQueries>             <customTrackingQuery activityName="String"                 name="String"/>          </customTrackingQueries>          <faultPropagationQueries>             <faultPropagationQuery activityName="String"                 faultHandlerActivityName="String"/>          </faultPropagationQueries>         <workflowInstanceQueries>            <workflowInstanceQuery>              <states>                 <state name="String"/>              </states>          </workflowInstanceQuery>        </workflowInstanceQueries>      </workflow>    </trackingProfile>           </profiles>  </tracking></system.serviceModel>  
```
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Uczestnicy >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/participants.md)|Kolekcję elementów konfiguracji Definiowanie uczestników subskrybować śledzenie rekordów. Uczestników śledzenia zawierają logikę przetwarzania ładunku z rekordów śledzenia (na przykład ich można zapisać do pliku).|  
|[\<trackingProfile >](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/trackingprofile.md)|Profil śledzenia do filtrowania rekordów śledzenia emitowane z wystąpienia przepływu pracy.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|System.ServiceModel|Element główny wszystkich elementów konfiguracji przepływu pracy.|  
  
## <a name="remarks"></a>Uwagi  
 Śledzenie umożliwia należy sprawdzić, czy wykonywania przepływu pracy. Infrastruktura śledzenia przepływu pracy instruments przepływu pracy, aby emitować rekordów odzwierciedlający kluczy zdarzeń podczas wykonywania. Na przykład podczas uruchamiania wystąpienia przepływu pracy, lub zakończeniu są emitowane rekordów śledzenia. Śledzenie również można wyodrębnić business odpowiednie dane skojarzone z zmienne przepływu pracy. Na przykład jeśli przepływ pracy reprezentuje kolejność przetwarzania systemu identyfikator zamówienia można wyodrębnić wraz z rekordem śledzenia. Ogólnie rzecz biorąc włączania WF śledzenia umożliwia wykonywanie operacji diagnostyki lub analiz biznesowych za wykonywanie przepływu pracy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection?displayProperty=nameWithType>       
 [Kontrola i śledzenie przepływu pracy](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
