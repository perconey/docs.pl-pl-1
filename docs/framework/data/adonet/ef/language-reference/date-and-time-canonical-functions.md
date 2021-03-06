---
title: Canonical funkcji daty i godziny
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9628b74f-1585-436a-b385-8b02ed0cdd63
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 143962ec91ebd8b24141b94af522585dd572d7f0
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="date-and-time-canonical-functions"></a>Canonical funkcji daty i godziny
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]obejmuje kanonicznej funkcji daty i godziny.  
  
## <a name="remarks"></a>Uwagi  
 W poniższej tabeli przedstawiono daty i godziny [!INCLUDE[esql](../../../../../../includes/esql-md.md)] kanonicznej funkcji. `datetime`jest <xref:System.DateTime> wartość.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|`AddNanoseconds(` `expression`, `number``)`|Dodaje określony `number` z nanosekundach do `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddMicroseconds(` `expression`, `number``)`|Dodaje określony `number` mikrosekund do `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddMilliseconds(` `expression`, `number``)`|Dodaje określony `number` milisekundach czas `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddSeconds(` `expression`, `number``)`|Dodaje określony `number` czas w sekundach `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddMinutes(` `expression`, `number``)`|Dodaje określony `number` minutach `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddHours(` `expression`, `number``)`|Dodaje określony `number` godziny `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime`, `DateTimeOffset`, lub `Time`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddDays(` `expression`, `number``)`|Dodaje określony `number` dni do `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` lub `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddMonths(` `expression`, `number``)`|Dodaje określony `number` miesięcy do `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` lub `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`AddYears(` `expression`, `number``)`|Dodaje określony `number` lat do `expression`.<br /><br /> **Argumenty**<br /><br /> `expression`: `DateTime` lub `DateTimeOffset`.<br /><br /> `number`: `Int32`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`CreateDateTime(` `year`, `month`, `day`, `hour`, `minute`, `second``)`|Zwraca nowy `DateTime` wartość jako bieżącą datę i godzinę serwera w strefie czasowej serwera.<br /><br /> **Argumenty**<br /><br /> `year`, `month`, `day`, `hour`, `minute`: `Int16` i `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTime`.|  
|`CreateDateTimeOffset(` `year`, `month`, `day`, `hour`, `minute`, `second`, `tzoffset``)`|Zwraca nowy `DateTimeOffset` wartość jako bieżącą datę i godzinę serwera względem uniwersalny czas koordynowany (UTC).<br /><br /> **Argumenty**<br /><br /> `year`, `month`, `day`, `hour`, `minute`, `tzoffset`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTimeOffset`.|  
|`CreateTime(` `hour`, `minute`, `second``)`|Zwraca nowy `Time` wartość, jak bieżący czas.<br /><br /> **Argumenty**<br /><br /> `hour`i `minute`: `Int32`.<br /><br /> `second`: `Double`.<br /><br /> **Wartość zwracana**<br /><br /> A `Time`.|  
|`CurrentDateTime()`|Zwraca `DateTime` wartość jako bieżącą datę i godzinę serwera w strefie czasowej serwera.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTime`.|  
|`CurrentDateTimeOffset()`|Zwraca bieżącą datę, czas i przesunięcie jako `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTimeOffset`.|  
|`CurrentUtcDateTime()`|Zwraca <xref:System.DateTime> wartość jako aktualnej daty i godziny w strefie czasowej UTS serwera.<br /><br /> **Wartość zwracana**<br /><br /> A `DateTime`.|  
|`Day(` `expression` `)`|Zwraca część dnia z `expression` jako `Int32` od 1 do 31.<br /><br /> **Argumenty**<br /><br /> A `DateTime` i `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 12.`<br /><br /> `Day(cast('03/12/1998' as DateTime))`|  
|`DayOfYear(` `expression` `)`|Zwraca część dnia z `expression` jako `Int32` od 1 do 366, dla których 366 są zwracane do ostatni dzień w roku przestępnym.<br /><br /> **Argumenty**<br /><br /> A `DateTime` lub `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffNanoseconds(` `startExpression`, `endExpression``)`|Zwraca w nanosekundach różnicę między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, lub `Time`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffMilliseconds(` `startExpression`, `endExpression``)`|Zwraca różnicę, w milisekundach między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, lub `Time`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffMicroseconds(` `startExpression`, `endExpression``)`|Zwraca w mikrosekundach, różnicę między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, lub `Time`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffSeconds(` `startExpression`, `endExpression``)`|Zwraca różnicę, w sekundach między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, lub `Time`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffMinutes(` `startExpression`, `endExpression``)`|Zwraca różnicę (w minutach) między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, lub `Time`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffHours(` `startExpression`, `endExpression``)`|Zwraca wartość to różnica w godzinach, między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime`, `DateTimeOffset`, lub `Time`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffDays(` `startExpression`, `endExpression``)`|Zwraca różnicę w dniach między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` lub `DateTimeOffset`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffMonths(` `startExpression`, `endExpression``)`|Zwraca różnicę, w miesiącach między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` lub `DateTimeOffset`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`DiffYears(` `startExpression`, `endExpression``)`|Zwraca w lat różnicę między `startExpression` i `endExpression`.<br /><br /> **Argumenty**<br /><br /> `startExpression`, `endExpression`: `DateTime` lub `DateTimeOffset`. **Uwaga:** `startExpression` i `endExpression` muszą być tego samego typu. <br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`GetTotalOffsetMinutes(` `datetimeoffset` `)`|Zwraca liczbę minut, która `datetimeoffset` przesunięcia względem GMT. Zwykle jest to między +780 i-780 (+ lub - 13 godzin). **Uwaga:** ta funkcja jest obsługiwana tylko w programie SQL Server 2008. <br /><br /> **Argumenty**<br /><br /> A `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`Hour (` `expression` `)`|Zwraca część godzin z `expression` jako `Int32` od 0 do 23.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` i `DateTimeOffset`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 22.`<br /><br /> `Hour(cast('22:35:5' as DateTime))`|  
|`Millisecond(` `expression` `)`|Zwraca część milisekund `expression` jako `Int32` zakresu od 0 do 999.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` i `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.|  
|`Minute(` `expression` `)`|Zwraca część minut z `expression` jako `Int32` od 0 do 59.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` lub `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 35`<br /><br /> `Minute(cast('22:35:5' as DateTime))`|  
|`Month` `(` `expression` `)`|Zwraca część miesiąca `expression` jako `Int32` od 1 do 12.<br /><br /> **Argumenty**<br /><br /> A `DateTime` lub `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 3.`<br /><br /> `Month(cast('03/12/1998' as DateTime))`|  
|`Second(` `expression` `)`|Zwraca sekund część `expression` jako `Int32` od 0 do 59.<br /><br /> **Argumenty**<br /><br /> A `DateTime, Time` i `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 5`<br /><br /> `Second(cast('22:35:5' as DateTime))`|  
|`TruncateTime(` `expression` `)`|Zwraca `expression`, wartościami czasu obcięte.<br /><br /> **Argumenty**<br /><br /> A `DateTime` lub `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> Typ `expression`.|  
|`Year(` `expression` `)`|Zwraca część `expression` jako `Int32``YYYY`.<br /><br /> **Argumenty**<br /><br /> A `DateTime` i `DateTimeOffset`.<br /><br /> **Wartość zwracana**<br /><br /> `Int32`.<br /><br /> **Przykład**<br /><br /> `-- The following example returns 1998.`<br /><br /> `Year(cast('03/12/1998' as DateTime))`|  
  
 Te funkcje będą zwracać `null` Jeśli podane `null` wejściowego.  
  
 Równoważne funkcje są dostępne w Microsoft SQL klienta zarządzanego dostawcy. Aby uzyskać więcej informacji, zobacz [SqlClient Entity Framework funkcji](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje Canonical](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
