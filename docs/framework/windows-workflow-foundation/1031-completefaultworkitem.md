---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 260647b56d945600afea5609f06d36385fa66014
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="1031---completefaultworkitem"></a>1031 - CompleteFaultWorkItem
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|1031|  
|Słowa kluczowe|WFRuntime|  
|Poziom|Pełny|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że element roboczy FaultWorkItem została ukończona.  
  
## <a name="message"></a>Komunikat  
 Ukończono element roboczy FaultWorkItem dla działania %1, nazwa wyświetlana: %2, identyfikator wystąpienia: '%3'. Wyjątek pochodzi z działania %4, nazwa wyświetlana: %5, identyfikator wystąpienia: '%6'.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:String|Nazwa typu działania błędów.|  
|FaultActivityDisplayName|xs:String|Nazwa wyświetlana działania błędów.|  
|FaultActivityInstanceId|xs:String|Identyfikator wystąpienia działania błędów.|  
|ExceptionActivity|xs:String|Nazwa typu działania, która zgłosiła wyjątek.|  
|ExceptionActivityDisplayName|xs:String|Nazwa wyświetlana działania, która zgłosiła wyjątek.|  
|ExceptionActivityInstanceId|xs:String|Identyfikator wystąpienia działania, która zgłosiła wyjątek.|  
|Wyjątek|xs:String|Szczegóły wyjątku dla wyjątku|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|