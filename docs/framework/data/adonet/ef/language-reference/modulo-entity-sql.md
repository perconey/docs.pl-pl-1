---
title: (Modulo) (Jednostka SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 243ddc4f-3c4e-41e1-a3ef-4ed39e36248b
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: cff0e4eaadf601b7a90f3caa0ecd9cf2f48feab0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="modulo-entity-sql"></a>(Modulo) (Jednostka SQL)
Zwraca resztę z jednego wyrażenia podzielona przez inny.  
  
## <a name="syntax"></a>Składnia  
  
```  
dividend % divisor  
```  
  
## <a name="arguments"></a>Argumenty  
 `dividend`  
 Wyrażenie liczbowe do dzielenia. `dividend`jest dowolne prawidłowe wyrażenie jednego z typów numerycznych.  
  
 `divisor`  
 Wyrażenie liczbowe do dzielenia dzielna przez. `divisor`jest dowolne prawidłowe wyrażenie jednego z typów numerycznych.  
  
## <a name="result-types"></a>Typy wyników  
 Typem Edm.Int32  
  
## <a name="example"></a>Przykład  
 Następujące zapytanie SQL jednostki użyto operatora arytmetycznego %, która zwraca pozostałej części jedno wyrażenie podzielona przez inny. Kwerenda jest oparta na modelu sprzedaży AdventureWorks. Aby skompilować i uruchomić to zapytanie, wykonaj następujące kroki:  
  
1.  Postępuj zgodnie z procedurą w [porady: wykonywanie zapytań tego zwraca wyniki StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).  
  
2.  Przekaż następujące zapytanie jako argument do `ExecuteStructuralTypeQuery` metody:  
  
 [!code-csharp[DP EntityServices Concepts 2#MODULO](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#modulo)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do jednostki SQL](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)