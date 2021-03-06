---
title: "Porady: kontrolowanie, ile powiązane dane są pobierane"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 3beb6f6b019535e273df7103e2e22f1be669797a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a>Porady: kontrolowanie, ile powiązane dane są pobierane
Użyj <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> metodę, aby określić, które dane powiązane z urządzenie docelowe głównej powinny zostać pobrane w tym samym czasie. Na przykład jeśli wiadomo, konieczne będą informacje dotyczące zamówienia klientów, można użyć <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> aby upewnić się, że informacje o kolejności są pobierane w tym samym czasie jako informacje o kliencie. Ta metoda powoduje podróży tylko jeden do bazy danych w obu zestawach danych.  
  
> [!NOTE]
>  Można pobrać danych związanych z głównym celem kwerendy, pobierając iloczyn wektorowy jako jeden duży projekcji, takie jak pobieranie zamówienia, jeśli zostanie rozpoczęta dla klientów. Jednak takie podejście charakteryzuje się często wady. Na przykład, wyniki są po prostu projekcje i nie jednostek, które można zmienić i utrwalone przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. I może być pobierania duże ilości danych, która nie ma potrzeby.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wszystkie `Orders` dla wszystkich `Customers` kto znajdują się w Londynie są pobierane, gdy zapytanie jest wykonywane. W rezultacie, kolejne dostęp do `Orders` właściwość `Customer` obiektu nie spowoduje wyzwolenia Nowa kwerenda bazy danych.  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
