---
title: "Porady: bezpośrednie wykonywanie zapytań SQL"
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
ms.assetid: e491b9bf-741a-4296-9f51-76c25ddf6a82
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 000a7c50edacbae09675a9f9069f56aa6cd211f6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-directly-execute-sql-queries"></a>Porady: bezpośrednie wykonywanie zapytań SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tłumaczy zapytania zostanie zapisany w sparametryzowane zapytania SQL (w postaci tekstu) i wysyła je do serwera SQL w celu przetwarzania.  
  
 SQL nie można wykonać różnych metod, które mogą być dostępne lokalnie do aplikacji. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]podejmuje próbę przekonwertowania te metody lokalne na równoważne operacji i funkcje, które są dostępne w środowisku SQL. Większość metod i operatory w [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] wbudowanych typów ma bezpośredni tłumaczenia poleceń SQL. Niektóre można wyprodukować z funkcji, które są dostępne. Te, które nie mogą być tworzone Generowanie wyjątki czasu wykonywania. Aby uzyskać więcej informacji, zobacz [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 W przypadkach, gdy [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania jest niewystarczający dla specjalnych zadań, możesz użyć <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> metodę, aby wykonać zapytania SQL, a następnie wykonać konwersję wyników kwerendy bezpośrednio do obiektów.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przyjęto założenie, że dane dla `Customer` klasy jest rozkładu ponad dwie tabele (customer1 i customer2). Zapytanie zwraca sekwencji `Customer` obiektów.  
  
 [!code-csharp[DLinqQuerying#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#4)]
 [!code-vb[DLinqQuerying#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#4)]  
  
 Tak długo, jak nazwy kolumn w wynikach tabelarycznym odpowiada właściwości kolumny klasy jednostki, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy obiekty poza każde zapytanie SQL.  
  
## <a name="example"></a>Przykład  
 <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> Metody umożliwia także dla parametrów. Użyj kodu podobne do poniższych można wykonać zapytania parametrycznego.  
  
 [!code-csharp[DLinqQuerying#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#5)]
 [!code-vb[DLinqQuerying#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#5)]  
  
 Parametry są wyrażane w tekst zapytania przy użyciu tego samego notacji klamrowych używanych przez `Console.WriteLine()` i `String.Format()`. W rzeczywistości `String.Format()` faktycznie jest wywoływana w ciągu kwerendy podasz, zastępując nawiasy nawiasach klamrowych parametrów z wygenerowany takich jak nazwy parametrów @p0, @p1 ..., @p(n).  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje uzupełniające](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)  
 [Wykonywanie zapytania w bazie danych](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
