---
title: '&lt;dispatcherSynchronization&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc030f9c-4e38-4b14-94dc-9a0e41ec8e2d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 24ae6dbf0fb67b5755aca848ea7fce6abda14b0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltdispatchersynchronizationgt"></a>&lt;dispatcherSynchronization&gt;

Określa zachowanie punktu końcowego, który włącza usługę Aby wysłać odpowiedzi asynchronicznie.

\<system.serviceModel > \<zachowania > \<endpointBehaviors > \<zachowanie >

## <a name="syntax"></a>Składnia

```xml
<dispatcherSynchronizationBehavior asynchronousSendEnabled="Boolean" 
                                   maxPendingReceives="Integer" />
```

## <a name="type"></a>Typ

`Type`

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

| Atrybut               | Opis       |
| ----------------------- | ----------------- |
| asynchronousSendEnabled | Wartość logiczna określająca czy zachowanie przesyłu asynchronicznego jest włączone. |
| `maxPendingReceives`    | Liczba całkowita, która określa, że liczba równoczesnych pobrań, które mogą być wystawiane w kanale.<br /><br /> Ta wartość musi być skonfigurowany tylko wtedy, gdy zostały poprawnie skonfigurowane zachowanie ograniczenia przepustowości usługi. |

### <a name="child-elements"></a>Elementy podrzędne

Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

| Element | Opis |  
| ------- | ----------- |  
| [\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie punktu końcowego. |

## <a name="see-also"></a>Zobacz także

 <xref:System.ServiceModel.Configuration.DispatcherSynchronizationElement><xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior>