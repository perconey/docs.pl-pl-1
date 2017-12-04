---
title: "Porady: filtrowanie wyników zapytania za pomocą LINQ (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 09f2eb65858853fd759ae033f749151b348c124d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a><span data-ttu-id="df695-102">Porady: filtrowanie wyników zapytania za pomocą LINQ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df695-102">How to: Filter Query Results by Using LINQ (Visual Basic)</span></span>
<span data-ttu-id="df695-103">Zapytanie języku zintegrowanym (LINQ) ułatwia dostęp do bazy danych informacji i wykonywanie zapytań.</span><span class="sxs-lookup"><span data-stu-id="df695-103">Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.</span></span>  
  
 <span data-ttu-id="df695-104">Poniższy przykład pokazuje, jak utworzyć nową aplikację, która wykonuje kwerendy względem bazy danych programu SQL Server i filtruje wyniki według określonej wartości przy użyciu `Where` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="df695-104">The following example shows how to create a new application that performs queries against a SQL Server database and filters the results by a particular value by using the `Where` clause.</span></span> <span data-ttu-id="df695-105">Aby uzyskać więcej informacji, zobacz [klauzuli Where](../../../../visual-basic/language-reference/queries/where-clause.md).</span><span class="sxs-lookup"><span data-stu-id="df695-105">For more information, see [Where Clause](../../../../visual-basic/language-reference/queries/where-clause.md).</span></span>  
  
 <span data-ttu-id="df695-106">W przykładach w tym temacie użyto przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="df695-106">The examples in this topic use the Northwind sample database.</span></span> <span data-ttu-id="df695-107">Jeśli nie masz przykładowej bazy danych Northwind na komputerze deweloperskim, możesz pobrać go z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) witryny sieci Web.</span><span class="sxs-lookup"><span data-stu-id="df695-107">If you do not have the Northwind sample database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088) Web site.</span></span> <span data-ttu-id="df695-108">Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](https://msdn.microsoft.com/library/bb399411).</span><span class="sxs-lookup"><span data-stu-id="df695-108">For instructions, see [Downloading Sample Databases](https://msdn.microsoft.com/library/bb399411).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a><span data-ttu-id="df695-109">Aby utworzyć połączenie z bazą danych</span><span class="sxs-lookup"><span data-stu-id="df695-109">To create a connection to a database</span></span>  
  
1.  <span data-ttu-id="df695-110">W programie Visual Studio Otwórz **Eksploratora serwera**/**Eksploratora bazy danych** klikając **Eksploratora serwera**/**bazy danych Eksplorator** na **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="df695-110">In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.</span></span>  
  
2.  <span data-ttu-id="df695-111">Kliknij prawym przyciskiem myszy **połączenia danych** w **Eksploratora serwera**/**Eksploratora bazy danych** , a następnie kliknij przycisk **Dodawanie połączenia**.</span><span class="sxs-lookup"><span data-stu-id="df695-111">Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.</span></span>  
  
3.  <span data-ttu-id="df695-112">Określ prawidłowe połączenie z przykładową bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="df695-112">Specify a valid connection to the Northwind sample database.</span></span>  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a><span data-ttu-id="df695-113">Aby dodać projekt, który zawiera LINQ do SQL pliku</span><span class="sxs-lookup"><span data-stu-id="df695-113">To add a project that contains a LINQ to SQL file</span></span>  
  
1.  <span data-ttu-id="df695-114">W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**.</span><span class="sxs-lookup"><span data-stu-id="df695-114">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span> <span data-ttu-id="df695-115">Wybierz pozycję Visual Basic **aplikacji Windows Forms** jako typ projektu.</span><span class="sxs-lookup"><span data-stu-id="df695-115">Select Visual Basic **Windows Forms Application** as the project type.</span></span>  
  
2.  <span data-ttu-id="df695-116">Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="df695-116">On the **Project** menu, click **Add New Item**.</span></span> <span data-ttu-id="df695-117">Wybierz **klasy LINQ do SQL** szablon elementu.</span><span class="sxs-lookup"><span data-stu-id="df695-117">Select the **LINQ to SQL Classes** item template.</span></span>  
  
3.  <span data-ttu-id="df695-118">Nadaj nazwę plikowi `northwind.dbml`.</span><span class="sxs-lookup"><span data-stu-id="df695-118">Name the file `northwind.dbml`.</span></span> <span data-ttu-id="df695-119">Kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="df695-119">Click **Add**.</span></span> <span data-ttu-id="df695-120">Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) otwiera plik northwind.dbml.</span><span class="sxs-lookup"><span data-stu-id="df695-120">The Object Relational Designer (O/R Designer) opens for the northwind.dbml file.</span></span>  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a><span data-ttu-id="df695-121">Aby dodać tabele, aby zapytania do Projektanta obiektów relacyjnych</span><span class="sxs-lookup"><span data-stu-id="df695-121">To add tables to query to the O/R Designer</span></span>  
  
1.  <span data-ttu-id="df695-122">W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="df695-122">In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database.</span></span> <span data-ttu-id="df695-123">Rozwiń węzeł **tabel** folderu.</span><span class="sxs-lookup"><span data-stu-id="df695-123">Expand the **Tables** folder.</span></span>  
  
     <span data-ttu-id="df695-124">Po zamknięciu Projektanta obiektów relacyjnych, możesz uruchomić go, klikając dwukrotnie plik northwind.dbml dodanego wcześniej.</span><span class="sxs-lookup"><span data-stu-id="df695-124">If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.</span></span>  
  
2.  <span data-ttu-id="df695-125">Tabeli Klienci kliknij i przeciągnij go do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="df695-125">Click the Customers table and drag it to the left pane of the designer.</span></span> <span data-ttu-id="df695-126">Tabela zamówienia kliknij i przeciągnij go do lewego okienka projektanta.</span><span class="sxs-lookup"><span data-stu-id="df695-126">Click the Orders table and drag it to the left pane of the designer.</span></span>  
  
     <span data-ttu-id="df695-127">Projektant tworzy nowy `Customer` i `Order` obiektów dla projektu.</span><span class="sxs-lookup"><span data-stu-id="df695-127">The designer creates new `Customer` and `Order` objects for your project.</span></span> <span data-ttu-id="df695-128">Zwróć uwagę, że projektant automatycznie wykrywa relacje między tabelami i tworzy właściwości w poszukiwaniu powiązanych obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="df695-128">Notice that the designer automatically detects relationships between the tables and creates child properties for related objects.</span></span> <span data-ttu-id="df695-129">Na przykład IntelliSense będzie wynikać, że `Customer` obiekt ma `Orders` właściwości dla wszystkich zleceń związane z tego klienta.</span><span class="sxs-lookup"><span data-stu-id="df695-129">For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.</span></span>  
  
3.  <span data-ttu-id="df695-130">Zapisz zmiany i zamknij projektanta.</span><span class="sxs-lookup"><span data-stu-id="df695-130">Save your changes and close the designer.</span></span>  
  
4.  <span data-ttu-id="df695-131">Zapisz projekt.</span><span class="sxs-lookup"><span data-stu-id="df695-131">Save your project.</span></span>  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a><span data-ttu-id="df695-132">Aby dodać kod, aby w bazie danych i wyświetlić wyniki</span><span class="sxs-lookup"><span data-stu-id="df695-132">To add code to query the database and display the results</span></span>  
  
1.  <span data-ttu-id="df695-133">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza systemu Windows dla projektu, Form1.</span><span class="sxs-lookup"><span data-stu-id="df695-133">From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.</span></span>  
  
2.  <span data-ttu-id="df695-134">Kliknij dwukrotnie Form1 kod, aby dodać `Load` zdarzenia formularza.</span><span class="sxs-lookup"><span data-stu-id="df695-134">Double-click Form1 to add code to the `Load` event of the form.</span></span>  
  
3.  <span data-ttu-id="df695-135">Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodane <xref:System.Data.Linq.DataContext> obiektu dla projektu.</span><span class="sxs-lookup"><span data-stu-id="df695-135">When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project.</span></span> <span data-ttu-id="df695-136">Ten obiekt zawiera kod, który musi mieć dostęp do tych tabel, oprócz poszczególnych obiektów i kolekcji dla każdej tabeli.</span><span class="sxs-lookup"><span data-stu-id="df695-136">This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table.</span></span> <span data-ttu-id="df695-137"><xref:System.Data.Linq.DataContext> Obiektu dla nosi nazwę projektu na podstawie nazwy pliku .dbml.</span><span class="sxs-lookup"><span data-stu-id="df695-137">The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file.</span></span> <span data-ttu-id="df695-138">Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="df695-138">For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.</span></span>  
  
     <span data-ttu-id="df695-139">Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> w kodzie i zapytania tabele określone przez Projektanta obiektów relacyjnych.</span><span class="sxs-lookup"><span data-stu-id="df695-139">You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.</span></span>  
  
     <span data-ttu-id="df695-140">Dodaj następujący kod do `Load` zdarzenie, aby wykonywać zapytania dotyczące tabel, które są dostępne jako właściwości kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="df695-140">Add the following code to the `Load` event to query the tables that are exposed as properties of your data context.</span></span> <span data-ttu-id="df695-141">Kwerenda filtruje wyniki i zwraca tylko klienci, którzy znajdują się w `London`.</span><span class="sxs-lookup"><span data-stu-id="df695-141">The query filters the results and returns only customers that are located in `London`.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#11](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_1.vb)]  
  
4.  <span data-ttu-id="df695-142">Naciśnij klawisz F5, aby uruchomić projekt i wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="df695-142">Press F5 to run your project and view the results.</span></span>  
  
5.  <span data-ttu-id="df695-143">Poniżej przedstawiono niektóre filtry, których można spróbować.</span><span class="sxs-lookup"><span data-stu-id="df695-143">Following are some other filters that you can try.</span></span>  
  
     [!code-vb[VbLINQToSQLHowTos#12](../../../../visual-basic/programming-guide/language-features/linq/codesnippet/VisualBasic/how-to-filter-query-results-by-using-linq_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="df695-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df695-144">See Also</span></span>  
 [<span data-ttu-id="df695-145">LINQ</span><span class="sxs-lookup"><span data-stu-id="df695-145">LINQ</span></span>](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="df695-146">Zapytania</span><span class="sxs-lookup"><span data-stu-id="df695-146">Queries</span></span>](../../../../visual-basic/language-reference/queries/queries.md)  
 [<span data-ttu-id="df695-147">LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="df695-147">LINQ to SQL</span></span>](https://msdn.microsoft.com/library/bb386976)  
 [<span data-ttu-id="df695-148">Metody DataContext (Projektanta obiektów relacyjnych)</span><span class="sxs-lookup"><span data-stu-id="df695-148">DataContext Methods (O/R Designer)</span></span>](/visualstudio/data-tools/datacontext-methods-o-r-designer)