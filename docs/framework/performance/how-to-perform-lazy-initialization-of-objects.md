---
title: "Porady: wykonywanie incjalizacji obiektów z opóźnieniem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: lazy initialization in .NET, how to perform
ms.assetid: 8cd68620-dcc3-4f20-8835-c728a6820e71
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b616aa284b6f7fff01b3b1fbfb15f2ceb54c9663
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-perform-lazy-initialization-of-objects"></a><span data-ttu-id="d6145-102">Porady: wykonywanie incjalizacji obiektów z opóźnieniem</span><span class="sxs-lookup"><span data-stu-id="d6145-102">How to: Perform Lazy Initialization of Objects</span></span>
<span data-ttu-id="d6145-103"><xref:System.Lazy%601?displayProperty=nameWithType> Klasa upraszcza pracy wykonania inicjowania z opóźnieniem i tworzenie wystąpień obiektów.</span><span class="sxs-lookup"><span data-stu-id="d6145-103">The <xref:System.Lazy%601?displayProperty=nameWithType> class simplifies the work of performing lazy initialization and instantiation of objects.</span></span> <span data-ttu-id="d6145-104">Inicjowanie obiektów w sposób opóźnieniem, można uniknąć konieczności tworzenia ich w ogóle, jeśli nigdy nie są one potrzebne lub można odroczyć inicjalizacji, aż najpierw uzyskiwania do nich.</span><span class="sxs-lookup"><span data-stu-id="d6145-104">By initializing objects in a lazy manner, you can avoid having to create them at all if they are never needed, or you can postpone their initialization until they are first accessed.</span></span> <span data-ttu-id="d6145-105">Aby uzyskać więcej informacji, zobacz [Incjalizacji](../../../docs/framework/performance/lazy-initialization.md).</span><span class="sxs-lookup"><span data-stu-id="d6145-105">For more information, see [Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6145-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6145-106">Example</span></span>  
 <span data-ttu-id="d6145-107">Poniższy przykład pokazuje, jak zainicjować wartości z <xref:System.Lazy%601>.</span><span class="sxs-lookup"><span data-stu-id="d6145-107">The following example shows how to initialize a value with <xref:System.Lazy%601>.</span></span> <span data-ttu-id="d6145-108">Załóżmy, że opóźnieniem zmiennej może nie być potrzebne, w zależności od innego kodu, która ustawia `someCondition` zmiennej wartość PRAWDA lub FAŁSZ.</span><span class="sxs-lookup"><span data-stu-id="d6145-108">Assume that the lazy variable might not be needed, depending on some other code that sets the `someCondition` variable to true or false.</span></span>  
  
```vb  
Dim someCondition As Boolean = False  
  
Sub Main()  
    'Initializing a value with a big computation, computed in parallel  
    Dim _data As Lazy(Of Integer) = New Lazy(Of Integer)(Function()  
                                                             Dim result =  
                                                                 ParallelEnumerable.Range(0, 1000).  
                                                                 Aggregate(Function(x, y)  
                                                                               Return x + y  
                                                                           End Function)  
                                                             Return result  
                                                         End Function)  
  
    '  do work that may or may not set someCondition to True  
    ' ...  
    '  Initialize the data only if needed  
    If someCondition = True Then  
  
        If (_data.Value > 100) Then  
  
            Console.WriteLine("Good data")  
        End If  
    End If  
End Sub  
```  
  
```csharp  
  static bool someCondition = false;    
  //Initializing a value with a big computation, computed in parallel  
  Lazy<int> _data = new Lazy<int>(delegate  
  {  
      return ParallelEnumerable.Range(0, 1000).  
          Select(i => Compute(i)).Aggregate((x,y) => x + y);  
  }, LazyExecutionMode.EnsureSingleThreadSafeExecution);  
  
  // Do some work that may or may not set someCondition to true.  
  //  ...  
  // Initialize the data only if necessary  
  if (someCondition)  
{  
    if (_data.Value > 100)  
      {  
          Console.WriteLine("Good data");  
      }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="d6145-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="d6145-109">Example</span></span>  
 <span data-ttu-id="d6145-110">Poniższy przykład przedstawia użycie <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> klasy można zainicjować typu, który jest widoczny tylko dla bieżącego wystąpienia obiektu w bieżącym wątku.</span><span class="sxs-lookup"><span data-stu-id="d6145-110">The following example shows how to use the <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> class to initialize a type that is visible only to the current object instance on the current thread.</span></span>  
  
 [!code-csharp[CDS#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cds/cs/cds2.cs#13)]
 [!code-vb[CDS#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds/vb/lazyhowto.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="d6145-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6145-111">See Also</span></span>  
 <xref:System.Threading.LazyInitializer?displayProperty=nameWithType>  
 [<span data-ttu-id="d6145-112">Inicjalizacja z opóźnieniem</span><span class="sxs-lookup"><span data-stu-id="d6145-112">Lazy Initialization</span></span>](../../../docs/framework/performance/lazy-initialization.md)