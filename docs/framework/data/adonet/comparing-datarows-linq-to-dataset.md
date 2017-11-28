---
title: "Porównanie wierszy danych (LINQ do DataSet)"
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
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9f17a73d2d6349d4fc35668d7251877034e5e29f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="0d4e0-102">Porównanie wierszy danych (LINQ do DataSet)</span><span class="sxs-lookup"><span data-stu-id="0d4e0-102">Comparing DataRows (LINQ to DataSet)</span></span>
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]<span data-ttu-id="0d4e0-103">definiuje różne operatory zestawów do porównania elementy źródłowe, aby zobaczyć, czy są równe.</span><span class="sxs-lookup"><span data-stu-id="0d4e0-103"> defines various set operators to compare source elements to see if they are equal.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]<span data-ttu-id="0d4e0-104">udostępnia następujące operatory zestawów:</span><span class="sxs-lookup"><span data-stu-id="0d4e0-104"> provides the following set operators:</span></span>  
  
-   <xref:System.Linq.Enumerable.Distinct%2A>  
  
-   <xref:System.Linq.Enumerable.Union%2A>  
  
-   <xref:System.Linq.Enumerable.Intersect%2A>  
  
-   <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="0d4e0-105">Te operatory porównania elementy źródłowe wywołując <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> i <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> metody dla każdej kolekcji elementów.</span><span class="sxs-lookup"><span data-stu-id="0d4e0-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="0d4e0-106">W przypadku liczby <xref:System.Data.DataRow>, tych operatorów wykonać porównanie odwołań, które zwykle nie jest idealne zachowanie operacje na zestawie za pośrednictwem danych tabelarycznych.</span><span class="sxs-lookup"><span data-stu-id="0d4e0-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="0d4e0-107">Dla operacji set zwykle chcesz określić, czy są równe wartości elementów i nie odwołania do elementu.</span><span class="sxs-lookup"><span data-stu-id="0d4e0-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="0d4e0-108">W związku z tym <xref:System.Data.DataRowComparer> klasy został dodany do [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0d4e0-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="0d4e0-109">Ta klasa umożliwia porównanie wartości wiersza.</span><span class="sxs-lookup"><span data-stu-id="0d4e0-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="0d4e0-110"><xref:System.Data.DataRowComparer> Klasa zawiera implementację porównania wartości <xref:System.Data.DataRow>, więc ta klasa może być używana dla operacje na zestawie takich jak <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="0d4e0-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="0d4e0-111">Ta klasa nie może występować bezpośrednio; Zamiast tego <xref:System.Data.DataRowComparer.Default%2A> właściwość musi być używana do zwrócenia wystąpienia klasy <xref:System.Data.DataRowComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="0d4e0-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="0d4e0-112"><xref:System.Data.DataRowComparer%601.Equals%2A> Następnie wywoływana jest metoda i dwa <xref:System.Data.DataRow> obiektów, które ma zostać porównane, są przekazywane w jako parametry wejściowe.</span><span class="sxs-lookup"><span data-stu-id="0d4e0-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="0d4e0-113"><xref:System.Data.DataRowComparer%601.Equals%2A> Metoda zwraca `true` w przypadku uporządkowanej zestaw kolumn wartości w obu <xref:System.Data.DataRow> obiekty są równe; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="0d4e0-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d4e0-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d4e0-114">Example</span></span>  
 <span data-ttu-id="0d4e0-115">W tym przykładzie użyto `Intersect` do zwrócenia kontaktów wyświetlane w obu tabel.</span><span class="sxs-lookup"><span data-stu-id="0d4e0-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="0d4e0-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d4e0-116">Example</span></span>  
 <span data-ttu-id="0d4e0-117">Porównuje dwa wiersze, pobiera ich skrótu w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0d4e0-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="0d4e0-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0d4e0-118">See Also</span></span>  
 <xref:System.Data.DataRowComparer>  
 [<span data-ttu-id="0d4e0-119">Podczas ładowania danych do zestawu danych</span><span class="sxs-lookup"><span data-stu-id="0d4e0-119">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)  
 [<span data-ttu-id="0d4e0-120">LINQ do DataSet przykłady</span><span class="sxs-lookup"><span data-stu-id="0d4e0-120">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)