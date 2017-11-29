---
title: Zbiory danych, DataTables i DataViews
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 642a81b926262fb8ea95234d90e4c1a0c49ea96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="datasets-datatables-and-dataviews"></a>Zbiory danych, DataTables i DataViews
ADO.NET <xref:System.Data.DataSet> jest rezydentny reprezentację danych, która zapewnia spójny model programowania relacyjne niezależnie od tego źródła danych zawiera. A <xref:System.Data.DataSet> reprezentuje kompletny zestaw danych w tym tabel, które zawierają, kolejność i Zachowaj dane, jak również relacje między tabelami.  
  
 Istnieje kilka sposobów pracy z <xref:System.Data.DataSet>, które można stosować niezależnie lub razem. Można:  
  
-   Programowe tworzenie <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, i <xref:System.Data.Constraint> w <xref:System.Data.DataSet> i wypełnić tabel z danymi.  
  
-   Wypełnij <xref:System.Data.DataSet> z tabelami danych z istniejącego relacyjne źródła danych przy użyciu `DataAdapter`.  
  
-   Ładowanie i utrwalić <xref:System.Data.DataSet> zawartości za pomocą języka XML. Aby uzyskać więcej informacji, zobacz [za pomocą XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).  
  
 Silnie typizowaną <xref:System.Data.DataSet> również może być transportowane przy użyciu usługi XML sieci Web. Projekt <xref:System.Data.DataSet> to idealny dla transportu danych przy użyciu usług XML sieci Web. Omówienie usług XML sieci Web, zobacz [Omówienie usług XML sieci Web](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d). Na przykład eksploatującego <xref:System.Data.DataSet> usługi XML sieci Web, zobacz temat [korzystających z zestawu danych z usługi XML sieci Web](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Tworzenie zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 W tym artykule opisano składnia tworzenia wystąpienia <xref:System.Data.DataSet>.  
  
 [Dodawanie elementu DataTable z zestawem danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 Opisuje sposób tworzenia i dodawanie tabel i kolumn do <xref:System.Data.DataSet>.  
  
 [Dodawanie DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 Opisuje sposób tworzenia relacji między tabelami w <xref:System.Data.DataSet>.  
  
 [Nawigowanie po DataRelations](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 Informacje dotyczące używania relacji między tabelami w <xref:System.Data.DataSet> do zwrócenia wierszy podrzędnej lub nadrzędnej w relacji nadrzędny podrzędny.  
  
 [Scalanie zawartości zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 Opisuje sposób scalania zawartość jednej <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, lub <xref:System.Data.DataRow> tablicy do innej <xref:System.Data.DataSet>.  
  
 [Kopiowanie zawartości zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 Opisuje sposób tworzenia kopii <xref:System.Data.DataSet> zawierających schematu, a także określonych danych.  
  
 [Obsługa zdarzeń zestawu danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 Opisuje zdarzenia z <xref:System.Data.DataSet> i sposobu ich używania.  
  
 [Typizowane zbiory danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 W tym artykule omówiono jakiego typu <xref:System.Data.DataSet> jest i jak utworzyć i użyć go.  
  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 Opisuje sposób tworzenia <xref:System.Data.DataTable>, zdefiniować schemat i manipulowanie danymi.  
  
 [DataTableReaders](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 Opisuje sposób tworzenia i używania <xref:System.Data.DataTableReader>.  
  
 [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 Opisuje sposób tworzenia i pracy z `DataViews` i pracować z <xref:System.Data.DataView> zdarzenia.  
  
 [Za pomocą języka XML w zestawie danych](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 Opisuje sposób <xref:System.Data.DataSet> współdziała z językiem XML jako źródło danych, w tym ładowanie i przechowywanie zawartości <xref:System.Data.DataSet> danych XML.  
  
 [Korzystanie z zestawu danych z usługi sieci Web XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 Opisuje sposób tworzenia usługi XML sieci Web, która używa <xref:System.Data.DataSet> danych transportu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [What's New in ADO.NET](../../../../../docs/framework/data/adonet/whats-new.md)  
 Zawiera funkcje, które są nowością w programie ADO.NET.  
  
 [ADO.NET — omówienie](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 Wprowadzenie do projektowania i składniki ADO.NET.  
  
 [Wypełnianie zestawu danych z element DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 Opisuje sposób załadować **DataSet** z danymi ze źródła danych.  
  
 [Aktualizowanie źródła danych za pomocą obiektów DataAdapter](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 Opisuje sposób rozwiązania zmiany danych w **DataSet** do źródła danych.  
  
 [Dodawanie istniejących ograniczeń do zestawu danych](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 Opisuje sposób wypełnienia **DataSet** o informacje o kluczu podstawowym ze źródła danych.  
  
## <a name="see-also"></a>Zobacz też  
 [ADO.NET](../../../../../docs/framework/data/adonet/index.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)