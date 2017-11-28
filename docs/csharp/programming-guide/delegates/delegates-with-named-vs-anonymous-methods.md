---
title: "Obiekty delegowane z nazwanego vs. Metody anonimowe (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 59317ad3cd9a5d360d0375bf46ff0c9f752a5944
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a><span data-ttu-id="4670f-102">Obiekty delegowane z nazwanego vs. Metody anonimowe (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="4670f-102">Delegates with Named vs. Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="4670f-103">A [delegować](../../../csharp/language-reference/keywords/delegate.md) może być skojarzony z metodę o nazwie.</span><span class="sxs-lookup"><span data-stu-id="4670f-103">A [delegate](../../../csharp/language-reference/keywords/delegate.md) can be associated with a named method.</span></span> <span data-ttu-id="4670f-104">Gdy przy użyciu nazwanego metody tworzenia wystąpienia delegata, metody jest przekazywany jako parametru, na przykład:</span><span class="sxs-lookup"><span data-stu-id="4670f-104">When you instantiate a delegate by using a named method, the method is passed as a parameter, for example:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#1](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_1.cs)]  
  
 <span data-ttu-id="4670f-105">Jest to, za pomocą metodę o nazwie.</span><span class="sxs-lookup"><span data-stu-id="4670f-105">This is called using a named method.</span></span> <span data-ttu-id="4670f-106">Obiekty delegowane skonstruowany przy metodę o nazwie umożliwiająca Hermetyzowanie albo [statycznych](../../../csharp/language-reference/keywords/static.md) metody lub metodą wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4670f-106">Delegates constructed with a named method can encapsulate either a [static](../../../csharp/language-reference/keywords/static.md) method or an instance method.</span></span> <span data-ttu-id="4670f-107">Nazwane metody są jedynym sposobem tworzenia wystąpienia delegata we wcześniejszych wersjach języka C#.</span><span class="sxs-lookup"><span data-stu-id="4670f-107">Named methods are the only way to instantiate a delegate in earlier versions of C#.</span></span> <span data-ttu-id="4670f-108">Jednak w sytuacji, gdy tworzenie nowej metody jest niechciane nakładów pracy, C# umożliwia tworzenia wystąpienia delegata i natychmiast Określ blok kodu, który przetworzy delegata, gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="4670f-108">However, in a situation where creating a new method is unwanted overhead, C# enables you to instantiate a delegate and immediately specify a code block that the delegate will process when it is called.</span></span> <span data-ttu-id="4670f-109">Blok może zawierać wyrażenia lambda lub metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="4670f-109">The block can contain either a lambda expression or an anonymous method.</span></span> <span data-ttu-id="4670f-110">Aby uzyskać więcej informacji, zobacz [funkcje anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4670f-110">For more information, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4670f-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4670f-111">Remarks</span></span>  
 <span data-ttu-id="4670f-112">Metodę przekazać jako parametru delegowanego musi mieć taką samą sygnaturę jak deklaracji obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="4670f-112">The method that you pass as a delegate parameter must have the same signature as the delegate declaration.</span></span>  
  
 <span data-ttu-id="4670f-113">Wystąpienie obiektu delegowanego Hermetyzowanie statycznych lub metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4670f-113">A delegate instance may encapsulate either static or instance method.</span></span>  
  
 <span data-ttu-id="4670f-114">Mimo że można używać delegata [limit](../../../csharp/language-reference/keywords/out.md) parametru, nie zaleca się on z delegaty multiemisji zdarzeń ponieważ nie wiadomo, delegata, która zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="4670f-114">Although the delegate can use an [out](../../../csharp/language-reference/keywords/out.md) parameter, we do not recommend its use with multicast event delegates because you cannot know which delegate will be called.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="4670f-115">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="4670f-115">Example 1</span></span>  
 <span data-ttu-id="4670f-116">Oto prosty przykład deklarowania i przy użyciu delegata.</span><span class="sxs-lookup"><span data-stu-id="4670f-116">The following is a simple example of declaring and using a delegate.</span></span> <span data-ttu-id="4670f-117">Zwróć uwagę, że oba delegata, `Del`i skojarzone metody `MultiplyNumbers`, mają taką samą sygnaturę</span><span class="sxs-lookup"><span data-stu-id="4670f-117">Notice that both the delegate, `Del`, and the associated method, `MultiplyNumbers`, have the same signature</span></span>  
  
 [!code-csharp[csProgGuideDelegates#2](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_2.cs)]  
  
## <a name="example-2"></a><span data-ttu-id="4670f-118">Przykład 2</span><span class="sxs-lookup"><span data-stu-id="4670f-118">Example 2</span></span>  
 <span data-ttu-id="4670f-119">W poniższym przykładzie jednego delegata jest mapowany na obu statyczna i metod i zwraca określone informacje z każdego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="4670f-119">In the following example, one delegate is mapped to both static and instance methods and returns specific information from each.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#3](../../../csharp/programming-guide/delegates/codesnippet/CSharp/delegates-with-named-vs-anonymous-methods_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4670f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4670f-120">See Also</span></span>  
 [<span data-ttu-id="4670f-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4670f-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4670f-122">Obiekty delegowane</span><span class="sxs-lookup"><span data-stu-id="4670f-122">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="4670f-123">Metody anonimowe</span><span class="sxs-lookup"><span data-stu-id="4670f-123">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)  
 [<span data-ttu-id="4670f-124">Porady: łączenie obiektów delegowanych (obiekty delegowane multiemisji)</span><span class="sxs-lookup"><span data-stu-id="4670f-124">How to: Combine Delegates (Multicast Delegates)</span></span>](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)  
 [<span data-ttu-id="4670f-125">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4670f-125">Events</span></span>](../../../csharp/programming-guide/events/index.md)