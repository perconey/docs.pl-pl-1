---
title: "Obiektów DataAdapter i DataReaders"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc952ca2-ec19-46ab-9189-15174b52cb74
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3e7a0af0b5fabdfacfcc825258242868b0fbb513
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="dataadapters-and-datareaders"></a><span data-ttu-id="90105-102">Obiektów DataAdapter i DataReaders</span><span class="sxs-lookup"><span data-stu-id="90105-102">DataAdapters and DataReaders</span></span>
<span data-ttu-id="90105-103">Można użyć ADO.NET **DataReader** do pobrania z bazy danych tylko do odczytu, tylko do przodu strumienia danych.</span><span class="sxs-lookup"><span data-stu-id="90105-103">You can use the ADO.NET **DataReader** to retrieve a read-only, forward-only stream of data from a database.</span></span> <span data-ttu-id="90105-104">Wyniki są zwracane jako zapytanie wykonuje i są przechowywane w buforze sieci na komputerze klienckim, dopóki ich zażądać przy użyciu **odczytu** metody **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="90105-104">Results are returned as the query executes, and are stored in the network buffer on the client until you request them using the **Read** method of the **DataReader**.</span></span> <span data-ttu-id="90105-105">Przy użyciu **DataReader** może zwiększyć wydajność aplikacji, zarówno przez pobranie danych, jak jest dostępny i (domyślnie) przechowywania tylko jeden wiersz jednocześnie w pamięci, zmniejszając narzut systemu.</span><span class="sxs-lookup"><span data-stu-id="90105-105">Using the **DataReader** can increase application performance both by retrieving data as soon as it is available, and (by default) storing only one row at a time in memory, reducing system overhead.</span></span>  
  
 <span data-ttu-id="90105-106">A <xref:System.Data.Common.DataAdapter> służy do pobierania danych ze źródła danych i wypełnić tabel w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="90105-106">A <xref:System.Data.Common.DataAdapter> is used to retrieve data from a data source and populate tables within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="90105-107">`DataAdapter` Rozwiązuje również zmiany wprowadzone w `DataSet` do źródła danych.</span><span class="sxs-lookup"><span data-stu-id="90105-107">The `DataAdapter` also resolves changes made to the `DataSet` back to the data source.</span></span> <span data-ttu-id="90105-108">`DataAdapter` Używa `Connection` obiekt dostawcy danych .NET Framework do nawiązania połączenia źródła danych który używa `Command` obiektów można pobrać danych z i rozwiązać zmian w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="90105-108">The `DataAdapter` uses the `Connection` object of the .NET Framework data provider to connect to a data source, and it uses `Command` objects to retrieve data from and resolve changes to the data source.</span></span>  
  
 <span data-ttu-id="90105-109">Każdy dostawca danych programu .NET Framework uwzględnionych w programie .NET Framework ma <xref:System.Data.Common.DbDataReader> i <xref:System.Data.Common.DbDataAdapter> obiektu: .NET Framework Data Provider for OLE DB zawiera <xref:System.Data.OleDb.OleDbDataReader> i <xref:System.Data.OleDb.OleDbDataAdapter> obiektu dostawcy danych programu .NET Framework dla serwera SQL Serwer zawiera <xref:System.Data.SqlClient.SqlDataReader> i <xref:System.Data.SqlClient.SqlDataAdapter> obiekt dostawcy danych programu .NET Framework dla ODBC obejmuje <xref:System.Data.Odbc.OdbcDataReader> i <xref:System.Data.Odbc.OdbcDataAdapter> obiektu i .NET Framework Data Provider for Oracle obejmuje <xref:System.Data.OracleClient.OracleDataReader> i <xref:System.Data.OracleClient.OracleDataAdapter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="90105-109">Each .NET Framework data provider included with the .NET Framework has a <xref:System.Data.Common.DbDataReader> and a <xref:System.Data.Common.DbDataAdapter> object: the .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbDataReader> and an <xref:System.Data.OleDb.OleDbDataAdapter> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlDataReader> and a <xref:System.Data.SqlClient.SqlDataAdapter> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcDataReader> and an <xref:System.Data.Odbc.OdbcDataAdapter> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleDataReader> and an <xref:System.Data.OracleClient.OracleDataAdapter> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90105-110">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="90105-110">In This Section</span></span>  
 [<span data-ttu-id="90105-111">Podczas pobierania danych przy użyciu elementu DataReader</span><span class="sxs-lookup"><span data-stu-id="90105-111">Retrieving Data Using a DataReader</span></span>](../../../../docs/framework/data/adonet/retrieving-data-using-a-datareader.md)  
 <span data-ttu-id="90105-112">W tym artykule opisano ADO.NET **DataReader** obiekt i jak z niego korzystać, aby zwrócić strumień wyniki ze źródła danych.</span><span class="sxs-lookup"><span data-stu-id="90105-112">Describes the ADO.NET **DataReader** object and how to use it to return a stream of results from a data source.</span></span>  
  
 [<span data-ttu-id="90105-113">Wypełnianie zestawu danych z element DataAdapter</span><span class="sxs-lookup"><span data-stu-id="90105-113">Populating a DataSet from a DataAdapter</span></span>](../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="90105-114">Opisuje sposób wypełnienia `DataSet` z tabel, kolumn i wierszy za pomocą `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="90105-114">Describes how to fill a `DataSet` with tables, columns, and rows by using a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="90105-115">Element DataAdapter parametrów</span><span class="sxs-lookup"><span data-stu-id="90105-115">DataAdapter Parameters</span></span>](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 <span data-ttu-id="90105-116">Informacje dotyczące używania parametry z właściwościami polecenia `DataAdapter` sposób mapowania zawartości kolumny w tym `DataSet` do parametru polecenia.</span><span class="sxs-lookup"><span data-stu-id="90105-116">Describes how to use parameters with the command properties of a `DataAdapter` including how to map the contents of a column in a `DataSet` to a command parameter.</span></span>  
  
 [<span data-ttu-id="90105-117">Dodawanie istniejących ograniczeń do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="90105-117">Adding Existing Constraints to a DataSet</span></span>](../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="90105-118">Zawiera opis sposobu dodawania istniejącego ograniczeń do `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="90105-118">Describes how to add existing constraints to a `DataSet`.</span></span>  
  
 [<span data-ttu-id="90105-119">Element DataAdapter DataTable i mapowania elementu DataColumn</span><span class="sxs-lookup"><span data-stu-id="90105-119">DataAdapter DataTable and DataColumn Mappings</span></span>](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)  
 <span data-ttu-id="90105-120">Zawiera opis sposobu konfigurowania `DataTableMappings` i `ColumnMappings` dla `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="90105-120">Describes how to set up `DataTableMappings` and `ColumnMappings` for a `DataAdapter`.</span></span>  
  
 [<span data-ttu-id="90105-121">Stronicowanie za pośrednictwem wyników z kwerendy</span><span class="sxs-lookup"><span data-stu-id="90105-121">Paging Through a Query Result</span></span>](../../../../docs/framework/data/adonet/paging-through-a-query-result.md)  
 <span data-ttu-id="90105-122">Przykład wyświetlania wyników zapytania jako strony danych.</span><span class="sxs-lookup"><span data-stu-id="90105-122">Provides an example of viewing the results of a query as pages of data.</span></span>  
  
 [<span data-ttu-id="90105-123">Aktualizowanie źródła danych za pomocą obiektów DataAdapter</span><span class="sxs-lookup"><span data-stu-id="90105-123">Updating Data Sources with DataAdapters</span></span>](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="90105-124">Informacje dotyczące używania `DataAdapter` rozpoznać zmian w `DataSet` w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="90105-124">Describes how to use a `DataAdapter` to resolve changes in a `DataSet` back to the database.</span></span>  
  
 [<span data-ttu-id="90105-125">Obsługa zdarzeń element DataAdapter</span><span class="sxs-lookup"><span data-stu-id="90105-125">Handling DataAdapter Events</span></span>](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)  
 <span data-ttu-id="90105-126">W tym artykule opisano `DataAdapter` zdarzenia i sposobu ich używania.</span><span class="sxs-lookup"><span data-stu-id="90105-126">Describes `DataAdapter` events and how to use them.</span></span>  
  
 [<span data-ttu-id="90105-127">Za pomocą obiektów DataAdapter operacji wsadowych.</span><span class="sxs-lookup"><span data-stu-id="90105-127">Performing Batch Operations Using DataAdapters</span></span>](../../../../docs/framework/data/adonet/performing-batch-operations-using-dataadapters.md)  
 <span data-ttu-id="90105-128">Opisuje zwiększanie wydajności aplikacji dzięki zmniejszeniu liczby rund do serwera SQL podczas stosowania aktualizacji z `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="90105-128">Describes enhancing application performance by reducing the number of round trips to SQL Server when applying updates from the `DataSet`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90105-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90105-129">See Also</span></span>  
 [<span data-ttu-id="90105-130">Połączenie ze źródłem danych</span><span class="sxs-lookup"><span data-stu-id="90105-130">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="90105-131">Poleceń i parametrów</span><span class="sxs-lookup"><span data-stu-id="90105-131">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="90105-132">Transakcje i współbieżność</span><span class="sxs-lookup"><span data-stu-id="90105-132">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="90105-133">Zbiory danych, DataTables i DataViews</span><span class="sxs-lookup"><span data-stu-id="90105-133">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="90105-134">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="90105-134">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)