---
title: "Jak grupować, sortować i filtrować dane w DataGrid kontrolce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], sort
- DataGrid [WPF], group
- DataGrid [WPF], filter
ms.assetid: 03345e85-89e3-4aec-9ed0-3b80759df770
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b3c8afacfafbe14794bf17a4e9a4df7c175a3668
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-sort-and-filter-data-in-the-datagrid-control"></a><span data-ttu-id="75351-102">Jak grupować, sortować i filtrować dane w DataGrid kontrolce</span><span class="sxs-lookup"><span data-stu-id="75351-102">How to: Group, Sort, and Filter Data in the DataGrid Control</span></span>
<span data-ttu-id="75351-103">Często jest to przydatne do wyświetlania danych w <xref:System.Windows.Controls.DataGrid> w różny sposób grupowania, sortowania i filtrowania danych.</span><span class="sxs-lookup"><span data-stu-id="75351-103">It is often useful to view data in a <xref:System.Windows.Controls.DataGrid> in different ways by grouping, sorting, and filtering the data.</span></span> <span data-ttu-id="75351-104">Do grupy, sortować i filtrować dane w <xref:System.Windows.Controls.DataGrid>, możesz powiązać <xref:System.Windows.Data.CollectionView> która obsługuje te funkcje.</span><span class="sxs-lookup"><span data-stu-id="75351-104">To group, sort, and filter the data in a <xref:System.Windows.Controls.DataGrid>, you bind it to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="75351-105">Potem można pracować z danymi w <xref:System.Windows.Data.CollectionView> bez wpływu na podstawowe źródło danych.</span><span class="sxs-lookup"><span data-stu-id="75351-105">You can then work with the data in the <xref:System.Windows.Data.CollectionView> without affecting the underlying source data.</span></span> <span data-ttu-id="75351-106">Zmiany w widoku kolekcji są uwzględniane w <xref:System.Windows.Controls.DataGrid> interfejsu użytkownika (UI).</span><span class="sxs-lookup"><span data-stu-id="75351-106">The changes in the collection view are reflected in the <xref:System.Windows.Controls.DataGrid> user interface (UI).</span></span>  
  
 <span data-ttu-id="75351-107"><xref:System.Windows.Data.CollectionView> Klasa udostępnia grupowanie i sortowanie funkcji dla źródła danych, który implementuje <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="75351-107">The <xref:System.Windows.Data.CollectionView> class provides grouping and sorting functionality for a data source that implements the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="75351-108"><xref:System.Windows.Data.CollectionViewSource> Klasa służy do ustawiania właściwości <xref:System.Windows.Data.CollectionView> z XAML.</span><span class="sxs-lookup"><span data-stu-id="75351-108">The <xref:System.Windows.Data.CollectionViewSource> class enables you to set the properties of a <xref:System.Windows.Data.CollectionView> from XAML.</span></span>  
  
 <span data-ttu-id="75351-109">W tym przykładzie zbiór `Task` obiektów jest powiązany z <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="75351-109">In this example, a collection of `Task` objects is bound to a <xref:System.Windows.Data.CollectionViewSource>.</span></span> <span data-ttu-id="75351-110"><xref:System.Windows.Data.CollectionViewSource> Jest używany jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="75351-110">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="75351-111">Grupowanie, sortowania i filtrowania są wykonywane na <xref:System.Windows.Data.CollectionViewSource> i są wyświetlane w <xref:System.Windows.Controls.DataGrid> interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="75351-111">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>  
  
 <span data-ttu-id="75351-112">![Grupowane dane w DataGrid](../../../../docs/framework/wpf/controls/media/wpf-datagridgroups.png "WPF_DataGridGroups")</span><span class="sxs-lookup"><span data-stu-id="75351-112">![Grouped data in a DataGrid](../../../../docs/framework/wpf/controls/media/wpf-datagridgroups.png "WPF_DataGridGroups")</span></span>  
<span data-ttu-id="75351-113">Dane zgrupowane w DataGrid</span><span class="sxs-lookup"><span data-stu-id="75351-113">Grouped Data in a DataGrid</span></span>  
  
## <a name="using-a-collectionviewsource-as-an-itemssource"></a><span data-ttu-id="75351-114">Przy użyciu CollectionViewSource jako ItemsSource.</span><span class="sxs-lookup"><span data-stu-id="75351-114">Using a CollectionViewSource as an ItemsSource</span></span>  
 <span data-ttu-id="75351-115">Do grupy, sortowanie i filtrowanie danych <xref:System.Windows.Controls.DataGrid> bind formant, <xref:System.Windows.Controls.DataGrid> do <xref:System.Windows.Data.CollectionView> która obsługuje te funkcje.</span><span class="sxs-lookup"><span data-stu-id="75351-115">To group, sort, and filter data in a <xref:System.Windows.Controls.DataGrid> control, you bind the <xref:System.Windows.Controls.DataGrid> to a <xref:System.Windows.Data.CollectionView> that supports these functions.</span></span> <span data-ttu-id="75351-116">W tym przykładzie <xref:System.Windows.Controls.DataGrid> jest powiązany z <xref:System.Windows.Data.CollectionViewSource> zapewnia następujące funkcje dla <xref:System.Collections.Generic.List%601> z `Task` obiektów.</span><span class="sxs-lookup"><span data-stu-id="75351-116">In this example, the <xref:System.Windows.Controls.DataGrid> is bound to a <xref:System.Windows.Data.CollectionViewSource> that provides these functions for a <xref:System.Collections.Generic.List%601> of `Task` objects.</span></span>  
  
#### <a name="to-bind-a-datagrid-to-a-collectionviewsource"></a><span data-ttu-id="75351-117">Aby powiązać CollectionViewSource DataGrid</span><span class="sxs-lookup"><span data-stu-id="75351-117">To bind a DataGrid to a CollectionViewSource</span></span>  
  
1.  <span data-ttu-id="75351-118">Utwórz kolekcję danych, która implementuje <xref:System.Collections.IEnumerable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="75351-118">Create a data collection that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
     <span data-ttu-id="75351-119">Jeśli używasz <xref:System.Collections.Generic.List%601> do utworzenia kolekcji, należy utworzyć nową klasę, która dziedziczy <xref:System.Collections.Generic.List%601> zamiast instancji <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="75351-119">If you use <xref:System.Collections.Generic.List%601> to create your collection, you should create a new class that inherits from <xref:System.Collections.Generic.List%601> instead of instantiating an instance of <xref:System.Collections.Generic.List%601>.</span></span> <span data-ttu-id="75351-120">Dzięki temu można utworzyć powiązania danych do kolekcji w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="75351-120">This enables you to data bind to the collection in XAML.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75351-121">Obiekty w kolekcji musi implementować <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu zmienione i <xref:System.ComponentModel.IEditableObject> interfejsu, aby <xref:System.Windows.Controls.DataGrid> do poprawnej odpowiedzi do zmian właściwości i modyfikacji.</span><span class="sxs-lookup"><span data-stu-id="75351-121">The objects in the collection must implement the <xref:System.ComponentModel.INotifyPropertyChanged> changed interface and the <xref:System.ComponentModel.IEditableObject> interface in order for the <xref:System.Windows.Controls.DataGrid> to respond correctly to property changes and edits.</span></span> <span data-ttu-id="75351-122">Aby uzyskać więcej informacji, zobacz [powiadomienia o zmianie właściwości wdrożenie](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span><span class="sxs-lookup"><span data-stu-id="75351-122">For more information, see [Implement Property Change Notification](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md).</span></span>  
  
     [!code-csharp[DataGrid_GroupSortFilter#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#101)]
     [!code-vb[DataGrid_GroupSortFilter#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#101)]  
  
2.  <span data-ttu-id="75351-123">W języku XAML, należy utworzyć wystąpienia klasy kolekcji i ustawić [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md).</span><span class="sxs-lookup"><span data-stu-id="75351-123">In XAML, create an instance of the collection class and set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md).</span></span>  
  
3.  <span data-ttu-id="75351-124">W języku XAML, Utwórz wystąpienie <xref:System.Windows.Data.CollectionViewSource> klasy, ustaw [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md)i ustaw wystąpienia klasy kolekcji jako <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span><span class="sxs-lookup"><span data-stu-id="75351-124">In XAML, create an instance of the <xref:System.Windows.Data.CollectionViewSource> class, set the [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md), and set the instance of your collection class as the <xref:System.Windows.Data.CollectionViewSource.Source%2A>.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#201](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml#201)]  
  
4.  <span data-ttu-id="75351-125">Utwórz wystąpienie <xref:System.Windows.Controls.DataGrid> klasy, a następnie ustaw <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwości <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="75351-125">Create an instance of the <xref:System.Windows.Controls.DataGrid> class, and set the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#002](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#002)]  
  
5.  <span data-ttu-id="75351-126">Aby uzyskać dostęp do <xref:System.Windows.Data.CollectionViewSource> w kodzie, użyj <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> metodę, aby pobrać odwołanie do <xref:System.Windows.Data.CollectionViewSource>.</span><span class="sxs-lookup"><span data-stu-id="75351-126">To access the <xref:System.Windows.Data.CollectionViewSource> from your code, use the <xref:System.Windows.Data.CollectionViewSource.GetDefaultView%2A> method to get a reference to the <xref:System.Windows.Data.CollectionViewSource>.</span></span>  
  
     [!code-csharp[DataGrid_GroupSortFilter#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#102)]
     [!code-vb[DataGrid_GroupSortFilter#102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#102)]  
  
## <a name="grouping-items-in-a-datagrid"></a><span data-ttu-id="75351-127">Grupowanie elementów w DataGrid</span><span class="sxs-lookup"><span data-stu-id="75351-127">Grouping items in a DataGrid</span></span>  
 <span data-ttu-id="75351-128">Aby określić sposób grupowania elementów w <xref:System.Windows.Controls.DataGrid>, możesz użyć <xref:System.Windows.Data.PropertyGroupDescription> typu grupować elementy w widoku źródła.</span><span class="sxs-lookup"><span data-stu-id="75351-128">To specify how items are grouped in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.Windows.Data.PropertyGroupDescription> type to group the items in the source view.</span></span>  
  
#### <a name="to-group-items-in-a-datagrid-using-xaml"></a><span data-ttu-id="75351-129">Grupowanie elementów w DataGrid przy użyciu kodu XAML</span><span class="sxs-lookup"><span data-stu-id="75351-129">To group items in a DataGrid using XAML</span></span>  
  
1.  <span data-ttu-id="75351-130">Utwórz <xref:System.Windows.Data.PropertyGroupDescription> , który określa właściwość do grupy przez.</span><span class="sxs-lookup"><span data-stu-id="75351-130">Create a <xref:System.Windows.Data.PropertyGroupDescription> that specifies the property to group by.</span></span> <span data-ttu-id="75351-131">Można określić właściwości, w języku XAML, lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="75351-131">You can specify the property in XAML or in code.</span></span>  
  
    1.  <span data-ttu-id="75351-132">W języku XAML, ustaw <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> na nazwę właściwości do grupowania.</span><span class="sxs-lookup"><span data-stu-id="75351-132">In XAML, set the <xref:System.Windows.Data.PropertyGroupDescription.PropertyName%2A> to the name of the property to group by.</span></span>  
  
    2.  <span data-ttu-id="75351-133">W kodzie należy przekazać nazwę właściwości do grupy przez konstruktora.</span><span class="sxs-lookup"><span data-stu-id="75351-133">In code, pass the name of the property to group by to the constructor.</span></span>  
  
2.  <span data-ttu-id="75351-134">Dodaj <xref:System.Windows.Data.PropertyGroupDescription> do <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="75351-134">Add the <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A?displayProperty=nameWithType> collection.</span></span>  
  
3.  <span data-ttu-id="75351-135">Dodaj kolejne wystąpienia <xref:System.Windows.Data.PropertyGroupDescription> do <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekcji można dodać więcej poziomy grupowania.</span><span class="sxs-lookup"><span data-stu-id="75351-135">Add additional instances of <xref:System.Windows.Data.PropertyGroupDescription> to the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection to add more levels of grouping.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#012](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#012)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#112](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#112)]
     [!code-vb[DataGrid_GroupSortFilter#112](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#112)]  
  
4.  <span data-ttu-id="75351-136">Aby usunąć grupę, Usuń <xref:System.Windows.Data.PropertyGroupDescription> z <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="75351-136">To remove a group, remove the <xref:System.Windows.Data.PropertyGroupDescription> from the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>  
  
5.  <span data-ttu-id="75351-137">Aby usunąć wszystkie grupy, należy wywołać <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> metody <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="75351-137">To remove all groups, call the <xref:System.Collections.ObjectModel.Collection%601.Clear%2A> method of the <xref:System.Windows.Data.CollectionViewSource.GroupDescriptions%2A> collection.</span></span>  
  
     [!code-csharp[DataGrid_GroupSortFilter#114](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#114)]
     [!code-vb[DataGrid_GroupSortFilter#114](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#114)]  
  
 <span data-ttu-id="75351-138">Gdy elementy są zgrupowane w <xref:System.Windows.Controls.DataGrid>, można zdefiniować <xref:System.Windows.Controls.GroupStyle> , który określa wygląd każdej grupy.</span><span class="sxs-lookup"><span data-stu-id="75351-138">When items are grouped in the <xref:System.Windows.Controls.DataGrid>, you can define a <xref:System.Windows.Controls.GroupStyle> that specifies the appearance of each group.</span></span> <span data-ttu-id="75351-139">Należy zastosować <xref:System.Windows.Controls.GroupStyle> przez dodanie go do <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> kolekcji elementu DataGrid.</span><span class="sxs-lookup"><span data-stu-id="75351-139">You apply the <xref:System.Windows.Controls.GroupStyle> by adding it to the <xref:System.Windows.Controls.ItemsControl.GroupStyle%2A> collection of the DataGrid.</span></span> <span data-ttu-id="75351-140">Jeśli masz wiele poziomów grupowania różnych stylów można zastosować do każdego poziomu grupy.</span><span class="sxs-lookup"><span data-stu-id="75351-140">If you have multiple levels of grouping, you can apply different styles to each group level.</span></span> <span data-ttu-id="75351-141">Style są stosowane w kolejności, w którym jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="75351-141">Styles are applied in the order in which they are defined.</span></span> <span data-ttu-id="75351-142">Na przykład w przypadku definiowania dwa style, pierwszy będą stosowane do grup najwyższego poziomu wiersza.</span><span class="sxs-lookup"><span data-stu-id="75351-142">For example, if you define two styles, the first will be applied to top level row groups.</span></span> <span data-ttu-id="75351-143">Drugi styl będą stosowane do wszystkich grup wierszy na drugim poziomie i niższych.</span><span class="sxs-lookup"><span data-stu-id="75351-143">The second style will be applied to all row groups at the second level and lower.</span></span> <span data-ttu-id="75351-144"><xref:System.Windows.FrameworkElement.DataContext%2A> z <xref:System.Windows.Controls.GroupStyle> jest <xref:System.Windows.Data.CollectionViewGroup> reprezentujący grupy.</span><span class="sxs-lookup"><span data-stu-id="75351-144">The <xref:System.Windows.FrameworkElement.DataContext%2A> of the <xref:System.Windows.Controls.GroupStyle> is the <xref:System.Windows.Data.CollectionViewGroup> that the group represents.</span></span>  
  
#### <a name="to-change-the-appearance-of-row-group-headers"></a><span data-ttu-id="75351-145">Aby zmienić wygląd nagłówki grupy wierszy</span><span class="sxs-lookup"><span data-stu-id="75351-145">To change the appearance of row group headers</span></span>  
  
1.  <span data-ttu-id="75351-146">Utwórz <xref:System.Windows.Controls.GroupStyle> która definiuje wygląd grupy wierszy.</span><span class="sxs-lookup"><span data-stu-id="75351-146">Create a <xref:System.Windows.Controls.GroupStyle> that defines the appearance of the row group.</span></span>  
  
2.  <span data-ttu-id="75351-147">Umieść <xref:System.Windows.Controls.GroupStyle> wewnątrz `<DataGrid.GroupStyle>` tagów.</span><span class="sxs-lookup"><span data-stu-id="75351-147">Put the <xref:System.Windows.Controls.GroupStyle> inside the `<DataGrid.GroupStyle>` tags.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#003](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#003)]  
  
## <a name="sorting-items-in-a-datagrid"></a><span data-ttu-id="75351-148">Sortowanie elementów w DataGrid</span><span class="sxs-lookup"><span data-stu-id="75351-148">Sorting items in a DataGrid</span></span>  
 <span data-ttu-id="75351-149">Aby określić sposób sortowania elementów w <xref:System.Windows.Controls.DataGrid>, możesz użyć <xref:System.ComponentModel.SortDescription> typu, aby posortować elementy w widoku źródła.</span><span class="sxs-lookup"><span data-stu-id="75351-149">To specify how items are sorted in a <xref:System.Windows.Controls.DataGrid>, you use the <xref:System.ComponentModel.SortDescription> type to sort the items in the source view.</span></span>  
  
#### <a name="to-sort-items-in-a-datagrid"></a><span data-ttu-id="75351-150">Aby posortować elementy DataGrid</span><span class="sxs-lookup"><span data-stu-id="75351-150">To sort items in a DataGrid</span></span>  
  
1.  <span data-ttu-id="75351-151">Utwórz <xref:System.ComponentModel.SortDescription> , który określa właściwość, aby posortować według.</span><span class="sxs-lookup"><span data-stu-id="75351-151">Create a <xref:System.ComponentModel.SortDescription> that specifies the property to sort by.</span></span> <span data-ttu-id="75351-152">Można określić właściwości, w języku XAML, lub w kodzie.</span><span class="sxs-lookup"><span data-stu-id="75351-152">You can specify the property in XAML or in code.</span></span>  
  
    1.  <span data-ttu-id="75351-153">W języku XAML, ustaw <xref:System.ComponentModel.SortDescription.PropertyName%2A> do nazwy właściwości, aby posortować według.</span><span class="sxs-lookup"><span data-stu-id="75351-153">In XAML, set the <xref:System.ComponentModel.SortDescription.PropertyName%2A> to the name of the property to sort by.</span></span>  
  
    2.  <span data-ttu-id="75351-154">W kodzie, przekaż nazwę właściwości, aby posortować według i <xref:System.ComponentModel.ListSortDirection> do konstruktora.</span><span class="sxs-lookup"><span data-stu-id="75351-154">In code, pass the name of the property to sort by and the <xref:System.ComponentModel.ListSortDirection> to the constructor.</span></span>  
  
2.  <span data-ttu-id="75351-155">Dodaj <xref:System.ComponentModel.SortDescription> do <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="75351-155">Add the <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A?displayProperty=nameWithType> collection.</span></span>  
  
3.  <span data-ttu-id="75351-156">Dodaj kolejne wystąpienia <xref:System.ComponentModel.SortDescription> do <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> kolekcji, aby posortować według dodatkowych właściwości.</span><span class="sxs-lookup"><span data-stu-id="75351-156">Add additional instances of <xref:System.ComponentModel.SortDescription> to the <xref:System.Windows.Data.CollectionViewSource.SortDescriptions%2A> collection to sort by additional properties.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#011](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#011)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#211](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/WindowSnips1.xaml.cs#211)]
     [!code-vb[DataGrid_GroupSortFilter#211](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#211)]  
  
## <a name="filtering-items-in-a-datagrid"></a><span data-ttu-id="75351-157">Filtrowanie elementów w DataGrid</span><span class="sxs-lookup"><span data-stu-id="75351-157">Filtering items in a DataGrid</span></span>  
 <span data-ttu-id="75351-158">Aby filtrować elementy w <xref:System.Windows.Controls.DataGrid> przy użyciu <xref:System.Windows.Data.CollectionViewSource>, podaj filtrowania logikę programu obsługi <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="75351-158">To filter items in a <xref:System.Windows.Controls.DataGrid> using a <xref:System.Windows.Data.CollectionViewSource>, you provide the filtering logic in the handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>  
  
#### <a name="to-filter-items-in-a-datagrid"></a><span data-ttu-id="75351-159">Aby filtrować elementy w DataGrid</span><span class="sxs-lookup"><span data-stu-id="75351-159">To filter items in a DataGrid</span></span>  
  
1.  <span data-ttu-id="75351-160">Dodaj obsługę <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="75351-160">Add a handler for the <xref:System.Windows.Data.CollectionViewSource.Filter?displayProperty=nameWithType> event.</span></span>  
  
2.  <span data-ttu-id="75351-161">W <xref:System.Windows.Data.CollectionViewSource.Filter> program obsługi zdarzeń, zdefiniuj logiki filtrowania.</span><span class="sxs-lookup"><span data-stu-id="75351-161">In the <xref:System.Windows.Data.CollectionViewSource.Filter> event handler, define the filtering logic.</span></span>  
  
     <span data-ttu-id="75351-162">Za każdym razem, gdy widok jest odświeżany, będzie stosowany filtr.</span><span class="sxs-lookup"><span data-stu-id="75351-162">The filter will be applied every time the view is refreshed.</span></span>  
  
     [!code-xaml[DataGrid_GroupSortFilter#013](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#013)]  
  
     [!code-csharp[DataGrid_GroupSortFilter#113](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#113)]
     [!code-vb[DataGrid_GroupSortFilter#113](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#113)]  
  
 <span data-ttu-id="75351-163">Alternatywnie można filtrować elementy <xref:System.Windows.Controls.DataGrid> tworząc metodę, która zawiera wartości logiczne i ustawienia filtrowania <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> właściwości, aby zastosować filtr.</span><span class="sxs-lookup"><span data-stu-id="75351-163">Alternatively, you can filter items in a <xref:System.Windows.Controls.DataGrid> by creating a method that provides the filtering logic and setting the <xref:System.Windows.Data.CollectionView.Filter%2A?displayProperty=nameWithType> property to apply the filter.</span></span> <span data-ttu-id="75351-164">Aby wyświetlić przykład tej metody, zobacz [filtrowanie danych w widoku](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).</span><span class="sxs-lookup"><span data-stu-id="75351-164">To see an example of this method, see [Filter Data in a View](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="75351-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="75351-165">Example</span></span>  
 <span data-ttu-id="75351-166">W poniższym przykładzie pokazano grupowania, sortowania i filtrowania `Task` danych w <xref:System.Windows.Data.CollectionViewSource> i wyświetlanie zgrupowane, posortowane i przefiltrowane `Task` danych w <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="75351-166">The following example demonstrates grouping, sorting, and filtering `Task` data in a <xref:System.Windows.Data.CollectionViewSource> and displaying the grouped, sorted, and filtered `Task` data in a <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="75351-167"><xref:System.Windows.Data.CollectionViewSource> Jest używany jako <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> dla <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="75351-167">The <xref:System.Windows.Data.CollectionViewSource> is used as the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> for the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="75351-168">Grupowanie, sortowania i filtrowania są wykonywane na <xref:System.Windows.Data.CollectionViewSource> i są wyświetlane w <xref:System.Windows.Controls.DataGrid> interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="75351-168">Grouping, sorting, and filtering are performed on the <xref:System.Windows.Data.CollectionViewSource> and are displayed in the <xref:System.Windows.Controls.DataGrid> UI.</span></span>  
  
 <span data-ttu-id="75351-169">Aby przetestować w tym przykładzie, należy dostosować nazwę DGGroupSortFilterExample do dopasowania nazwę projektu.</span><span class="sxs-lookup"><span data-stu-id="75351-169">To test this example, you will need to adjust the DGGroupSortFilterExample name to match your project name.</span></span> <span data-ttu-id="75351-170">Jeśli używasz programu Visual Basic, musisz zmienić nazwę klasy dla <xref:System.Windows.Window> do następującego.</span><span class="sxs-lookup"><span data-stu-id="75351-170">If you are using Visual Basic, you will need to change the class name for <xref:System.Windows.Window> to the following.</span></span>  
  
 `<Window x:Class="MainWindow"`  
  
 [!code-xaml[DataGrid_GroupSortFilter#000](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml#000)]  
  
 [!code-csharp[DataGrid_GroupSortFilter#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataGrid_GroupSortFilter/CS/MainWindow.xaml.cs#100)]
 [!code-vb[DataGrid_GroupSortFilter#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataGrid_GroupSortFilter/VB/MainWindow.xaml.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="75351-171">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="75351-171">Compiling the Code</span></span>  
  
-  
  
## <a name="robust-programming"></a><span data-ttu-id="75351-172">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="75351-172">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="75351-173">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="75351-173">.NET Framework Security</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75351-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="75351-174">See Also</span></span>  
 [<span data-ttu-id="75351-175">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="75351-175">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="75351-176">Tworzenie i powiązać obiektu ObservableCollection</span><span class="sxs-lookup"><span data-stu-id="75351-176">Create and Bind to an ObservableCollection</span></span>](../../../../docs/framework/wpf/data/how-to-create-and-bind-to-an-observablecollection.md)  
 [<span data-ttu-id="75351-177">Filtrowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="75351-177">Filter Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)  
 [<span data-ttu-id="75351-178">Sortowanie danych w widoku</span><span class="sxs-lookup"><span data-stu-id="75351-178">Sort Data in a View</span></span>](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)  
 [<span data-ttu-id="75351-179">Sortowanie i grupowanie danych przy użyciu widoku w języku XAML</span><span class="sxs-lookup"><span data-stu-id="75351-179">Sort and Group Data Using a View in XAML</span></span>](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)