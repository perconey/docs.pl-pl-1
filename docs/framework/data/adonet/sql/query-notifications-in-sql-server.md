---
title: "Powiadomienia zapytań w programie SQL Server"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f0ba1a1-3180-4af8-87f7-c795dc8f8f55
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 376f2cfefcaf53affe5a20a5812a02839dd5d4a9
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="query-notifications-in-sql-server"></a>Powiadomienia zapytań w programie SQL Server
Wbudowane w system infrastruktury programu Service Broker, powiadomień o zapytaniach umożliwiają aplikacjom otrzymać powiadomienie, gdy dane zostały zmienione. Ta funkcja jest szczególnie przydatne w przypadku aplikacji, które zapewniają pamięci podręcznej informacje z bazy danych, takich jak aplikacji sieci Web i musi być zgłoszone, gdy źródło danych zostanie zmieniona.  
  
 Istnieją trzy sposoby, które można wdrożyć za pomocą ADO.NET powiadomień o zapytaniach:  
  
1.  Niskiego poziomu implementacji jest zapewniana przez `SqlNotificationRequest` klasy, która udostępnia funkcje po stronie serwera, dzięki któremu można wykonać polecenia z żądaniem powiadomień.  
  
2.  Wdrożenia wysokiego poziomu są dostarczane przez `SqlDependency` klasy, która jest klasa, która zapewnia Abstrakcja wysokiego poziomu funkcjonalności powiadomień od źródłowej aplikacji i programu SQL Server, dzięki któremu można użyć do wykrycia zmian w zależności serwer. W większości przypadków jest to najprostsza i najbardziej efektywny sposób wykorzystać możliwości powiadomienia programu SQL Server przez aplikacje klienckie zarządzane za pomocą dostawcy .NET Framework Data Provider for SQL Server.  
  
3.  Ponadto aplikacje sieci Web w utworzonym przy użyciu składnika ASP.NET 2.0 lub później za pomocą `SqlCacheDependency` klasy pomocy.  
  
 Liczba powiadomień o zapytaniach są używane dla aplikacji, które trzeba odświeżyć Wyświetla lub buforuje w odpowiedzi na zmiany w danych źródłowych. Microsoft SQL Server umożliwia aplikacji .NET Framework wysyłania polecenia programu SQL Server i powiadomień żądania, jeśli wykonywanie tego samego polecenia wywołałoby inny niż początkowo pobranych zestawów wyników. Powiadomień generowanych na serwerze są wysyłane za pośrednictwem kolejek na przetworzenie później.  
  
 Można skonfigurować powiadomienia dla wybierz i WYKONAJ instrukcje. Korzystając z instrukcji EXECUTE, SQL Server rejestruje powiadomień dla polecenia wykonywane zamiast instrukcji EXECUTE sam. Polecenie musi spełniać wymagania i ograniczenia dotyczące instrukcji SELECT. Jeśli polecenie, które rejestruje powiadomienie zawiera więcej niż jedną instrukcję, aparatu bazy danych tworzy powiadomień dla każdej instrukcji w partii.  
  
 Jeśli tworzysz aplikację, konieczne niezawodnej sekundę podrzędne powiadomienia po zmianie danych, należy przejrzeć sekcje **planowania strategii wydajne powiadomienia kwerendy** i **alternatywy dla zapytania Powiadomienia** w [planowanie powiadomienia](http://go.microsoft.com/fwlink/?LinkId=211984) tematu w dokumentacji SQL Server — książki Online. Aby uzyskać więcej informacji na temat powiadomień o zapytaniach i brokera usług serwera SQL zobacz następujące linki do tematów w dokumentacji SQL Server — książki Online.  
  
 **SQL Server — książki Online**  
  
-   [Za pomocą powiadomień o zapytaniach](http://msdn.microsoft.com/library/ms175110.aspx)  
  
-   [Tworzenie zapytania o powiadomienie](http://msdn.microsoft.com/library/ms181122.aspx)  
  
-   [Usługa Service Broker](http://msdn.microsoft.com/library/bb522889.aspx)  
  
-   [Centrum usługi Broker Developer informacyjne](http://msdn.microsoft.com/library/ms166100.aspx)  
  
-   [Programowanie (Service Broker)](http://msdn.microsoft.com/library/bb522908.aspx)  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Włączanie powiadomień o zapytaniach](../../../../../docs/framework/data/adonet/sql/enabling-query-notifications.md)  
 W tym artykule omówiono sposób używania powiadomień kwerendy, w tym wymagania dotyczące włączania i używania ich.  
  
 [Element SqlDependency w aplikacji ASP.NET](../../../../../docs/framework/data/adonet/sql/sqldependency-in-an-aspnet-app.md)  
 Pokazuje, jak korzystać z zapytania powiadomień w aplikacji ASP.NET.  
  
 [Wykrywanie zmian za pomocą elementu SqlDependency](../../../../../docs/framework/data/adonet/sql/detecting-changes-with-sqldependency.md)  
 Demonstracja Wykryj, kiedy wyniki zapytania będą inne niż pierwotnie odebrane.  
  
 [Wykonywanie polecenia SqlCommand za pomocą SqlNotificationRequest](../../../../../docs/framework/data/adonet/sql/sqlcommand-execution-with-a-sqlnotificationrequest.md)  
 Pokazuje Konfigurowanie <xref:System.Data.SqlClient.SqlCommand> obiekt do pracy z powiadomienia kwerendy.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Data.Sql.SqlNotificationRequest>  
 W tym artykule opisano <xref:System.Data.Sql.SqlNotificationRequest> klasy i wszystkich jego elementów członkowskich.  
  
 <xref:System.Data.SqlClient.SqlDependency>  
 W tym artykule opisano <xref:System.Data.SqlClient.SqlDependency> klasy i wszystkich jego elementów członkowskich.  
  
 <xref:System.Web.Caching.SqlCacheDependency>  
 W tym artykule opisano <xref:System.Web.Caching.SqlCacheDependency> klasy i wszystkich jego elementów członkowskich.  
  
## <a name="see-also"></a>Zobacz też  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
