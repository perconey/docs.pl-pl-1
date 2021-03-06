---
title: Przestrzenie nazw (jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 4df0cc483e922e93a8038da02248b5fdcb2e3471
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="namespaces-entity-sql"></a>Przestrzenie nazw (jednostka SQL)
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]wprowadza przestrzenie nazw, aby uniknąć konfliktów nazw identyfikatorów globalnych, takich jak nazwy typu, zestawów jednostek, funkcje i tak dalej. Obsługa przestrzeni nazw w [!INCLUDE[esql](../../../../../../includes/esql-md.md)] jest podobny do obsługi przestrzeni nazw w [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)].  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]zawiera dwa rodzaje klauzuli USING: kwalifikowana przestrzeni nazw (gdy krótszą alias zostało określone dla przestrzeni nazw), a niekwalifikowanych nazw, jak pokazano w poniższym przykładzie:  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>Zasady rozpoznawania nazw  
 Jeśli identyfikator nie jest rozpoznawany w lokalnym zakresów [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje zlokalizować nazwy w zakresach globalnych (przestrzenie nazw). [!INCLUDE[esql](../../../../../../includes/esql-md.md)]najpierw próbuje dopasować identyfikator (prefiks) z jednej z kwalifikowaną przestrzeni nazw. Jeśli istnieje dopasowanie, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje rozpoznać pozostałej części identyfikatora w określonej przestrzeni nazw. Jeśli nie znaleziono, zwracany jest wyjątek.  
  
 Następnie [!INCLUDE[esql](../../../../../../includes/esql-md.md)] próbuje wyszukiwanie wszystkich nazw niekwalifikowanych (określony w prologu) dla identyfikatora. Jeśli identyfikator może znajdować się w jednej przestrzeni nazw, zwracany jest tej lokalizacji. Jeśli więcej niż jeden obszar nazw ma dopasowania dla tego identyfikatora, zwracany jest wyjątek. Jeśli dla identyfikatora, można zidentyfikować bez przestrzeni nazw [!INCLUDE[esql](../../../../../../includes/esql-md.md)] przekazuje nazwę na następny zakres na zewnątrz ( <xref:System.Data.Common.DbCommand> lub <xref:System.Data.Common.DbConnection> obiektu), jak pokazano w poniższym przykładzie:  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>Różnice z programu .NET Framework  
 W [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)], można użyć częściowo kwalifikowanej przestrzeni nazw. [!INCLUDE[esql](../../../../../../includes/esql-md.md)]Pozwala to.  
  
## <a name="adonet-usage"></a>Użycie ADO.NET  
 Zapytania są wyrazić za pomocą ADO.NET <xref:System.Data.Common.DbCommand> obiektów. <xref:System.Data.Common.DbCommand>obiekty mogą być tworzone przez <xref:System.Data.Common.DbConnection> obiektów. Przestrzenie nazw można również określić jako część <xref:System.Data.Common.DbCommand> i <xref:System.Data.Common.DbConnection> obiektów. Jeśli [!INCLUDE[esql](../../../../../../includes/esql-md.md)] nie można rozpoznać identyfikatora w samej kwerendzie zewnętrznych przestrzenie nazw są sondowany (na podstawie podobnymi zasadami).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [Omówienie jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
