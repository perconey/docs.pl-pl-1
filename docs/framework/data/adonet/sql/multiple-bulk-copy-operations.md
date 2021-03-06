---
title: Wiele operacji kopiowania zbiorczego
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
ms.assetid: 5ad12f94-7459-4a93-a421-4160d1a90715
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 8a753357719f451ce7acc2d7f42c0493ca2357ab
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="multiple-bulk-copy-operations"></a>Wiele operacji kopiowania zbiorczego
Można wykonywać wiele operacji kopiowania zbiorczego, za pomocą jednego wystąpienia <xref:System.Data.SqlClient.SqlBulkCopy> klasy. Jeśli parametry operacji zmiany między kopiami (na przykład nazwa tabeli docelowej), należy zaktualizować je przed kolejnych wywołań dowolnej z **WriteToServer** metod, jak pokazano w poniższym przykładzie. Chyba że jawnie zmieniona wszystkich wartości właściwości pozostają takie same, jakie były na poprzedniej operacji kopiowania zbiorczego dla danego wystąpienia.  
  
> [!NOTE]
>  Wykonywanie wielu operacji kopiowania zbiorczego przy użyciu tego samego wystąpienia <xref:System.Data.SqlClient.SqlBulkCopy> jest zazwyczaj bardziej efektywne niż przy użyciu osobnego wystąpienia dla każdej operacji.  
  
 Jeśli wykonano kilka operacji kopiowania zbiorczego korzystającej z tego samego <xref:System.Data.SqlClient.SqlBulkCopy> obiektu, nie ma żadnych ograniczeń czy informacji źródłowa lub docelowa jest taki sam lub inny w każdej operacji. Należy jednak upewnić się, czy informacje o skojarzeniu kolumny są ustawione właściwie zawsze, gdy zapisać na serwerze.  
  
> [!IMPORTANT]
>  W tym przykładzie nie będzie działać, jeśli nie utworzono tabel roboczych zgodnie z opisem w [Instalatora przykład kopiowania zbiorczego](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md). Ten kod jest dostarczany do zaprezentowania składnia przy użyciu **SqlBulkCopy** tylko. Jeśli tabele źródłowy i docelowy znajdują się w tym samym wystąpieniu programu SQL Server, jest łatwiejsze i szybsze do używania języka Transact-SQL `INSERT … SELECT` instrukcji, aby skopiować dane.  
  
 [!code-csharp[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/CS/source.cs#1)]
 [!code-vb[DataWorks SqlBulkCopy.ColumnMappingOrdersDetails#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlBulkCopy.ColumnMappingOrdersDetails/VB/source.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operacje kopiowania masowego w programie SQL Server](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
