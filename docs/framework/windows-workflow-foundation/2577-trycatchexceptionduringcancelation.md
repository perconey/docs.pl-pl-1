---
title: 2577 - TryCatchExceptionDuringCancelation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1e851a50c9677b2f10ea3478c3599706007d4d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a>2577 - TryCatchExceptionDuringCancelation
## <a name="properties"></a>Właściwości  
  
|||  
|-|-|  
|ID|2577|  
|Słowa kluczowe|WFActivities|  
|Poziom|Ostrzeżenie|  
|Kanał|Microsoft-Windows aplikacji debugowania serwera — aplikacje|  
  
## <a name="description"></a>Opis  
 Wskazuje, że działanie podrzędne działania TryCatch wywołało wyjątek podczas anulowania.  
  
## <a name="message"></a>Komunikat  
 Działanie podrzędne działania TryCatch "%1" wywołało wyjątek podczas anulowania.  
  
## <a name="details"></a>Szczegóły  
  
|Nazwa elementu danych|Typ elementu danych|Opis|  
|--------------------|--------------------|-----------------|  
|Nazwa wyświetlana|xs:String|Nazwa wyświetlana działania.|  
|Domeny aplikacji|xs:String|Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.|
