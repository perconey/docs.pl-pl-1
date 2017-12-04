---
title: "Rozwiązywanie załadowań zestawów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], resolving loads
- application domains, loading assemblies
- resolving assembly loads
- assemblies [.NET Framework], loading
- application domains, resolving assembly loads
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33dc3bfd3c70d5ea1105fb47c283aa8cf1c827c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="resolving-assembly-loads"></a><span data-ttu-id="bef0e-102">Rozwiązywanie załadowań zestawów</span><span class="sxs-lookup"><span data-stu-id="bef0e-102">Resolving Assembly Loads</span></span>
<span data-ttu-id="bef0e-103">Platforma .NET Framework zapewnia <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> zdarzenia dla aplikacji, które wymagają większej kontroli nad ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="bef0e-103">The .NET Framework provides the <xref:System.AppDomain.AssemblyResolve?displayProperty=nameWithType> event for applications that require greater control over assembly loading.</span></span> <span data-ttu-id="bef0e-104">Obsługa tego zdarzenia, aplikacja może załadować zestawu do kontekstu ładowania z poza zwykłych sondowania ścieżek, wybierz które z kilku wersji zestawu do załadowania, emisji dynamicznego zestawu i zwraca je i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="bef0e-104">By handling this event, your application can load an assembly into the load context from outside the normal probing paths, select which of several assembly versions to load, emit a dynamic assembly and return it, and so on.</span></span> <span data-ttu-id="bef0e-105">Ten temat zawiera wskazówki dotyczące obsługi <xref:System.AppDomain.AssemblyResolve> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="bef0e-105">This topic provides guidance for handling the <xref:System.AppDomain.AssemblyResolve> event.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bef0e-106">Rozwiązywanie załadowań zestawów w kontekstu reflection-only, użyj <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> zdarzeń zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="bef0e-106">For resolving assembly loads in the reflection-only context, use the <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=nameWithType> event instead.</span></span>  
  
## <a name="how-the-assemblyresolve-event-works"></a><span data-ttu-id="bef0e-107">Jak działa zdarzeń AssemblyResolve</span><span class="sxs-lookup"><span data-stu-id="bef0e-107">How the AssemblyResolve Event Works</span></span>  
 <span data-ttu-id="bef0e-108">Po dokonaniu rejestracji programu obsługi dla <xref:System.AppDomain.AssemblyResolve> zdarzeń, program obsługi jest wywoływane zawsze, gdy środowisko uruchomieniowe nie powiedzie się powiązać zestawu według nazwy.</span><span class="sxs-lookup"><span data-stu-id="bef0e-108">When you register a handler for the <xref:System.AppDomain.AssemblyResolve> event, the handler is invoked whenever the runtime fails to bind to an assembly by name.</span></span> <span data-ttu-id="bef0e-109">Na przykład następujące metody podczas wywoływania z kodu użytkownika może spowodować <xref:System.AppDomain.AssemblyResolve> się zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="bef0e-109">For example, calling the following methods from user code can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised:</span></span>  
  
-   <span data-ttu-id="bef0e-110"><xref:System.AppDomain.Load%2A?displayProperty=nameWithType> Przeciążenie metody lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążenie metody, której pierwszy argument jest ciąg reprezentujący nazwę wyświetlaną zestawu do załadowania (czyli długość ciągu zwróconego przez <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> właściwości).</span><span class="sxs-lookup"><span data-stu-id="bef0e-110">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is a string that represents the display name of the assembly to load (that is, the string returned by the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property).</span></span>  
  
-   <span data-ttu-id="bef0e-111"><xref:System.AppDomain.Load%2A?displayProperty=nameWithType> Przeciążenie metody lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążenie metody, której pierwszy argument jest <xref:System.Reflection.AssemblyName> obiekt, który identyfikuje zestaw do załadowania.</span><span class="sxs-lookup"><span data-stu-id="bef0e-111">An <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> method overload or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overload whose first argument is an <xref:System.Reflection.AssemblyName> object that identifies the assembly to load.</span></span>  
  
-   <span data-ttu-id="bef0e-112"><xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> Przeciążenie metody.</span><span class="sxs-lookup"><span data-stu-id="bef0e-112">An <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType> method overload.</span></span>  
  
-   <span data-ttu-id="bef0e-113"><xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> Lub <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> przeciążenie metody, która tworzy wystąpienie obiektu w innej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bef0e-113">An <xref:System.AppDomain.CreateInstance%2A?displayProperty=nameWithType> or <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType> method overload that instantiates an object in another application domain.</span></span>  
  
### <a name="what-the-event-handler-does"></a><span data-ttu-id="bef0e-114">Co to jest program obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="bef0e-114">What the Event Handler Does</span></span>  
 <span data-ttu-id="bef0e-115">Program obsługi dla <xref:System.AppDomain.AssemblyResolve> zdarzenie otrzymuje nazwę wyświetlaną zestawu do załadowania do <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bef0e-115">The handler for the <xref:System.AppDomain.AssemblyResolve> event receives the display name of the assembly to be loaded, in the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="bef0e-116">Jeśli program obsługi nie może rozpoznać nazwę zestawu, zwraca wartość null (`Nothing` w języku Visual Basic `nullptr` w programie Visual C++).</span><span class="sxs-lookup"><span data-stu-id="bef0e-116">If the handler does not recognize the assembly name, it returns null (`Nothing` in Visual Basic, `nullptr` in Visual C++).</span></span>  
  
 <span data-ttu-id="bef0e-117">Program obsługi, jeśli rozpoznaje nazwy zestawu go załadować i zwraca zestaw, który spełnia żądania.</span><span class="sxs-lookup"><span data-stu-id="bef0e-117">If the handler recognizes the assembly name, it can load and return an assembly that satisfies the request.</span></span> <span data-ttu-id="bef0e-118">Poniżej opisano kilka przykładowych scenariuszy.</span><span class="sxs-lookup"><span data-stu-id="bef0e-118">The following list describes some sample scenarios.</span></span>  
  
-   <span data-ttu-id="bef0e-119">Jeśli program obsługi zna lokalizacji wersji zestawu, można załadować zestawu za pomocą <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> metody, możesz wrócić załadowany zestaw w przypadku powodzenia.</span><span class="sxs-lookup"><span data-stu-id="bef0e-119">If the handler knows the location of a version of the assembly, it can load the assembly by using the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=nameWithType> method, and can return the loaded assembly if successful.</span></span>  
  
-   <span data-ttu-id="bef0e-120">Jeśli program obsługi ma dostęp do bazy danych zestawów przechowywane jako tablice typu byte, tablica bajtów można załadować przy użyciu jednej z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążenia metody, które przyjmują tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="bef0e-120">If the handler has access to a database of assemblies stored as byte arrays, it can load a byte array by using one of the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that take a byte array.</span></span>  
  
-   <span data-ttu-id="bef0e-121">Program obsługi, można wygenerować zestawu dynamicznego i przywrócić go.</span><span class="sxs-lookup"><span data-stu-id="bef0e-121">The handler can generate a dynamic assembly and return it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bef0e-122">Program obsługi musi załadować zestawu do obciążenia w kontekście, w kontekście ładowania lub bez kontekstu. Jeśli program obsługi ładuje zestawu do kontekstu reflection-only przy użyciu <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> podejmować obciążenia metody, która wywołała <xref:System.AppDomain.AssemblyResolve> zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="bef0e-122">The handler must load the assembly into the load-from context, into the load context, or without context.If the handler loads the assembly into the reflection-only context by using the <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> or the <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> method, the load attempt that raised the <xref:System.AppDomain.AssemblyResolve> event fails.</span></span>  
  
 <span data-ttu-id="bef0e-123">Jest odpowiedzialny za program obsługi zdarzeń, aby zwrócić odpowiedniego zestawu.</span><span class="sxs-lookup"><span data-stu-id="bef0e-123">It is the responsibility of the event handler to return a suitable assembly.</span></span> <span data-ttu-id="bef0e-124">Program obsługi może przeanalizować składni nazwę wyświetlaną żądany zestaw, przekazując <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> wartości właściwości do <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="bef0e-124">The handler can parse the display name of the requested assembly by passing the <xref:System.ResolveEventArgs.Name%2A?displayProperty=nameWithType> property value to the <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> constructor.</span></span> <span data-ttu-id="bef0e-125">Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć programu obsługi <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> właściwości w celu określenia, czy bieżące żądanie dotyczy zależność innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="bef0e-125">Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the handler can use the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property to determine whether the current request is a dependency of another assembly.</span></span> <span data-ttu-id="bef0e-126">Te informacje mogą pomóc w identyfikacji zestawu, który będzie odpowiadał zależności.</span><span class="sxs-lookup"><span data-stu-id="bef0e-126">This information can help identify an assembly that will satisfy the dependency.</span></span>  
  
 <span data-ttu-id="bef0e-127">Program obsługi zdarzeń może zwrócić innej wersji niż żądana wersja zestawu.</span><span class="sxs-lookup"><span data-stu-id="bef0e-127">The event handler can return a different version of the assembly than the version that was requested.</span></span>  
  
 <span data-ttu-id="bef0e-128">W większości przypadków zestawu, który jest zwracany przez program obsługi zostanie wyświetlony w kontekście ładowania, niezależnie od tego, program obsługi ładuje go do kontekstu.</span><span class="sxs-lookup"><span data-stu-id="bef0e-128">In most cases, the assembly that is returned by the handler appears in the load context, regardless of the context the handler loads it into.</span></span> <span data-ttu-id="bef0e-129">Na przykład, jeśli program obsługi używa <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> metody próbę załadowania zestawu w kontekście ładowania z zestawu jest wyświetlany w kontekście ładowania, gdy program obsługi zwraca go.</span><span class="sxs-lookup"><span data-stu-id="bef0e-129">For example, if the handler uses the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method to load an assembly into the load-from context, the assembly appears in the load context when the handler returns it.</span></span> <span data-ttu-id="bef0e-130">Jednak w przypadku następujących zestawu pojawia się bez kontekście podczas obsługi zwraca go:</span><span class="sxs-lookup"><span data-stu-id="bef0e-130">However, in the following case the assembly appears without context when the handler returns it:</span></span>  
  
-   <span data-ttu-id="bef0e-131">Program obsługi ładuje zestaw bez kontekstu.</span><span class="sxs-lookup"><span data-stu-id="bef0e-131">The handler loads an assembly without context.</span></span>  
  
-   <span data-ttu-id="bef0e-132"><xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> Właściwość nie jest zerowa.</span><span class="sxs-lookup"><span data-stu-id="bef0e-132">The <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property is not null.</span></span>  
  
-   <span data-ttu-id="bef0e-133">Żądanie zestawu (oznacza to, że zestaw, który jest zwracany przez <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> właściwości) została załadowana bez kontekstu.</span><span class="sxs-lookup"><span data-stu-id="bef0e-133">The requesting assembly (that is, the assembly that is returned by the <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=nameWithType> property) was loaded without context.</span></span>  
  
 <span data-ttu-id="bef0e-134">Aby uzyskać informacje o kontekstach, zobacz <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> przeciążenie metody.</span><span class="sxs-lookup"><span data-stu-id="bef0e-134">For information about contexts, see the <xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=nameWithType> method overload.</span></span>  
  
 <span data-ttu-id="bef0e-135">Wiele wersji tego samego zestawu mogą zostać załadowane do tej samej domenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bef0e-135">Multiple versions of the same assembly can be loaded into the same application domain.</span></span> <span data-ttu-id="bef0e-136">Takie rozwiązanie nie jest zalecane, ponieważ może to prowadzić do typu przydziału problemów.</span><span class="sxs-lookup"><span data-stu-id="bef0e-136">This practice is not recommended, because it can lead to type assignment problems.</span></span> <span data-ttu-id="bef0e-137">Zobacz [najlepsze rozwiązania dotyczące ładowania zestawu](../../../docs/framework/deployment/best-practices-for-assembly-loading.md).</span><span class="sxs-lookup"><span data-stu-id="bef0e-137">See [Best Practices for Assembly Loading](../../../docs/framework/deployment/best-practices-for-assembly-loading.md).</span></span>  
  
### <a name="what-the-event-handler-should-not-do"></a><span data-ttu-id="bef0e-138">Co nie należy przeprowadzać programu obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="bef0e-138">What the Event Handler Should Not Do</span></span>  
 <span data-ttu-id="bef0e-139">Podstawowe reguły obsługi <xref:System.AppDomain.AssemblyResolve> zdarzenie jest, że nie należy zwracać zestawu nie rozpoznają.</span><span class="sxs-lookup"><span data-stu-id="bef0e-139">The primary rule for handling the <xref:System.AppDomain.AssemblyResolve> event is that you should not try to return an assembly you do not recognize.</span></span> <span data-ttu-id="bef0e-140">Podczas pisania program obsługi, należy wiedzieć, zestawy, które mogą spowodować się zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="bef0e-140">When you write the handler, you should know which assemblies might cause the event to be raised.</span></span> <span data-ttu-id="bef0e-141">Dla innych zestawów programu obsługi powinien zwrócić wartości null.</span><span class="sxs-lookup"><span data-stu-id="bef0e-141">Your handler should return null for other assemblies.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bef0e-142">Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], <xref:System.AppDomain.AssemblyResolve> zdarzenia zestawów satelickich.</span><span class="sxs-lookup"><span data-stu-id="bef0e-142">Beginning with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the <xref:System.AppDomain.AssemblyResolve> event is raised for satellite assemblies.</span></span> <span data-ttu-id="bef0e-143">Ta zmiana wpływa napisane dla starszej wersji programu .NET Framework, program obsługi zdarzeń, jeśli program obsługi próbuje rozpoznać wszystkich żądań obciążenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="bef0e-143">This change affects an event handler that was written for an earlier version of the .NET Framework, if the handler tries to resolve all assembly load requests.</span></span> <span data-ttu-id="bef0e-144">Programy obsługi zdarzeń, które Ignoruj zestawy nie rozpoznają nie dotyczy tej zmiany: zwracają wartość null, a normalne mechanizmów powrotu zostaną wykonane.</span><span class="sxs-lookup"><span data-stu-id="bef0e-144">Event handlers that ignore assemblies they do not recognize are not affected by this change: They return null, and normal fallback mechanisms are followed.</span></span>  
  
 <span data-ttu-id="bef0e-145">Podczas ładowania zestawu, program obsługi zdarzeń nie może używać dowolnej z <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> przeciążenia metody, które mogą spowodować <xref:System.AppDomain.AssemblyResolve> zdarzeń będzie zgłoszono cyklicznie, ponieważ może to prowadzić do przepełnienia stosu.</span><span class="sxs-lookup"><span data-stu-id="bef0e-145">When loading an assembly, the event handler must not use any of the <xref:System.AppDomain.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method overloads that can cause the <xref:System.AppDomain.AssemblyResolve> event to be raised recursively, because this can lead to a stack overflow.</span></span> <span data-ttu-id="bef0e-146">(Zobacz listę podane wcześniej w tym temacie). Dzieje się tak nawet wtedy, gdy udostępniają obsługi dla żądania obciążenia wyjątków, ponieważ nie jest wyjątek do momentu zwrócono wszystkich procedur obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="bef0e-146">(See the list provided earlier in this topic.) This happens even if you provide exception handling for the load request, because no exception is thrown until all event handlers have returned.</span></span> <span data-ttu-id="bef0e-147">W ten sposób, następujący kod powoduje przepełnienie stosu Jeśli `MyAssembly` nie znaleziono:</span><span class="sxs-lookup"><span data-stu-id="bef0e-147">Thus, the following code results in a stack overflow if `MyAssembly` is not found:</span></span>  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)]
 [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)]
 [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bef0e-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bef0e-148">See Also</span></span>  
 [<span data-ttu-id="bef0e-149">Najlepsze praktyki dotyczące ładowania zestawu</span><span class="sxs-lookup"><span data-stu-id="bef0e-149">Best Practices for Assembly Loading</span></span>](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)  
 [<span data-ttu-id="bef0e-150">Używanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="bef0e-150">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)