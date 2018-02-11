---
title: Analizator interfejs API .NET
description: "Dowiedz się, jak analizator interfejsu API platformy .NET mogą pomóc wykrywanie przestarzałe interfejsy API i problemy ze zgodnością platformy."
author: oliag
ms.author: mairaw
ms.date: 01/30/2018
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.openlocfilehash: 81ab7e32b2af6048d822243226f1054ebd1ca419
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="net-api-analyzer"></a><span data-ttu-id="9e9e3-103">Analizator interfejs API .NET</span><span class="sxs-lookup"><span data-stu-id="9e9e3-103">.NET API analyzer</span></span>

<span data-ttu-id="9e9e3-104">Analizator interfejs API .NET jest analizator Roslyn, który wykryje zgodność potencjalne zagrożenie dla interfejsów API języka C# na różnych platformach i wykrywa wywołania interfejsów API przestarzałe.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-104">The .NET API Analyzer is a Roslyn analyzer that discovers potential compatibility risks for C# APIs on different platforms and detects calls to deprecated APIs.</span></span> <span data-ttu-id="9e9e3-105">Może być przydatne dla wszystkich deweloperów języka C# na każdym etapie programowania.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-105">It can be useful for all C# developers at any stage of development.</span></span>

<span data-ttu-id="9e9e3-106">Analizator interfejsu API jest dostarczany jako pakietu NuGet [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span><span class="sxs-lookup"><span data-stu-id="9e9e3-106">API Analyzer comes as a NuGet package [Microsoft.DotNet.Analyzers.Compatibility](https://www.nuget.org/packages/Microsoft.DotNet.Analyzers.Compatibility/).</span></span> <span data-ttu-id="9e9e3-107">Po odwołanie w projekcie, automatycznie monitoruje kod i wskazuje problematyczne użycia interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-107">After you reference it in a project, it automatically monitors the code and indicates problematic API usage.</span></span> <span data-ttu-id="9e9e3-108">Sugestie na możliwe poprawek można również uzyskać, klikając żarówkę.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-108">You can also get suggestions on possible fixes by clicking on the light bulb.</span></span> <span data-ttu-id="9e9e3-109">Menu rozwijane zawiera opcję pomijania ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-109">The drop-down menu includes an option to suppress the warnings.</span></span>

> [!NOTE]
> <span data-ttu-id="9e9e3-110">Analizator interfejs API .NET jest nadal wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-110">The .NET API analyzer is still a pre-release version.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9e9e3-111">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9e9e3-111">Prerequisites</span></span>

* <span data-ttu-id="9e9e3-112">Visual Studio 2017 lub Visual Studio dla komputerów Mac (wszystkie wersje).</span><span class="sxs-lookup"><span data-stu-id="9e9e3-112">Visual Studio 2017 or Visual Studio for Mac (all versions).</span></span>

## <a name="discovering-deprecated-apis"></a><span data-ttu-id="9e9e3-113">Odnajdywanie przestarzałe interfejsy API</span><span class="sxs-lookup"><span data-stu-id="9e9e3-113">Discovering deprecated APIs</span></span>

### <a name="what-are-deprecated-apis"></a><span data-ttu-id="9e9e3-114">Co to są przestarzałe interfejsy API?</span><span class="sxs-lookup"><span data-stu-id="9e9e3-114">What are deprecated APIs?</span></span>

<span data-ttu-id="9e9e3-115">Rodzina .NET jest zestaw produktów dużych stale uaktualnionych do potrzeb potrzeb klientów.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-115">The .NET family is a set of large products that are constantly upgraded to better serve customer needs.</span></span> <span data-ttu-id="9e9e3-116">Jest fizyczne, aby zastąpić niektórych interfejsów API i zastąp je nowymi plikami.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-116">It's natural to deprecate some APIs and replace them with new ones.</span></span> <span data-ttu-id="9e9e3-117">Interfejs API zostanie uznane za przestarzałe, gdy istnieje lepszym.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-117">An API is considered deprecated when a better alternative exists.</span></span> <span data-ttu-id="9e9e3-118">Jednym ze sposobów poinformuj o tym, że interfejs API jest przestarzały i nie powinny być używane jest oznaczenie go przy użyciu <xref:System.ObsoleteAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-118">One way to inform that an API is deprecated and shouldn't be used is to mark it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="9e9e3-119">Wadą tego podejścia jest, że istnieje tylko jeden identyfikator diagnostycznych dla wszystkich interfejsów API przestarzałe (język C#, [CS0612](../../csharp/misc/cs0612.md)).</span><span class="sxs-lookup"><span data-stu-id="9e9e3-119">The disadvantage of this approach is that there is only one diagnostic ID for all obsolete APIs (for C#, [CS0612](../../csharp/misc/cs0612.md)).</span></span> <span data-ttu-id="9e9e3-120">Oznacza to, że:</span><span class="sxs-lookup"><span data-stu-id="9e9e3-120">This means that:</span></span>
- <span data-ttu-id="9e9e3-121">Nie jest możliwe są wyposażone w dedykowane dokumentów dla każdego przypadku.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-121">It's impossible to have dedicated documents for each case.</span></span>
- <span data-ttu-id="9e9e3-122">Nie można pominąć określonej kategorii ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-122">It's impossible to suppress certain category of warnings.</span></span> <span data-ttu-id="9e9e3-123">Można pominąć wszystkie lub żadne z nich.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-123">You can suppress either all or none of them.</span></span>
- <span data-ttu-id="9e9e3-124">Aby informować użytkowników o nowych amortyzacja, przywoływanego zestawu lub przeznaczonych dla pakietu ma zostać zaktualizowany.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-124">To inform users of a new deprecation, a referenced assembly or targeting package has to be updated.</span></span>

<span data-ttu-id="9e9e3-125">Analizator interfejsu API wykorzystuje interfejs API specyficzne kody błędów, które rozpoczynają się z DE (oznaczającą błąd amortyzacja), która zapewnia kontrolę nad wyświetlania ostrzeżeń indywidualnych.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-125">The API Analyzer uses API-specific error codes that begin with DE (which stands for Deprecation Error), which allows control over the display of individual warnings.</span></span> <span data-ttu-id="9e9e3-126">Przestarzałe interfejsy API zidentyfikowane przez analizatora są zdefiniowane w [dotnet/platform — compat](https://github.com/dotnet/platform-compat) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-126">The deprecated APIs identified by the analyzer are defined in the [dotnet/platform-compat](https://github.com/dotnet/platform-compat) repo.</span></span>

### <a name="using-the-api-analyzer"></a><span data-ttu-id="9e9e3-127">Za pomocą analizatora interfejsu API</span><span class="sxs-lookup"><span data-stu-id="9e9e3-127">Using the API Analyzer</span></span>

<span data-ttu-id="9e9e3-128">Gdy przestarzałe interfejsu API, takich jak <xref:System.Net.WebClient>, jest używana w kodzie interfejsu API analizatora wyróżnia ją z linii o dowolnym kształcie zielony.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-128">When a deprecated API, such as <xref:System.Net.WebClient>, is used in a code, API Analyzer highlights it with a green squiggly line.</span></span> <span data-ttu-id="9e9e3-129">Po umieszczeniu na wywołania interfejsu API, żarówka wyświetlane są informacje o amortyzacja interfejsu API, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9e9e3-129">When you hover over the API call, a light bulb is displayed with information about the API deprecation, as in the following example:</span></span>

!["Zrzut ekranu WebClient interfejsu API z zielonym dowolnym kształcie wiersza i żarówki po lewej stronie"](media/api-analyzer/green-squiggle.jpg)

<span data-ttu-id="9e9e3-131">**Listy błędów** okno zawiera ostrzeżenia o unikatowym identyfikatorze za przestarzały interfejsu API, jak pokazano w poniższym przykładzie (`DE004`):</span><span class="sxs-lookup"><span data-stu-id="9e9e3-131">The **Error List** window contains warnings with a unique ID per deprecated API, as shown in the following example (`DE004`):</span></span> 

!["Zrzut ekranu przedstawiający identyfikator i opis tego ostrzeżenia w oknie Lista błędów"](media/api-analyzer/warnings.jpg)

<span data-ttu-id="9e9e3-133">Klikając identyfikator, przejdź do strony sieci Web, szczegółowe informacje na temat przyczyny została uznana za przestarzałą interfejsu API i sugestie dotyczące alternatywnych interfejsów API, które mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-133">By clicking on the ID, you go to a webpage with detailed information about why the API was deprecated and suggestions regarding alternative APIs that can be used.</span></span>

<span data-ttu-id="9e9e3-134">Można pominąć wszelkie ostrzeżenia zaznaczony element członkowski prawym przyciskiem myszy i wybierając **Pomiń \<Identyfikator diagnostyczny >**.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-134">Any warnings can be suppressed by right-clicking on the highlighted member and selecting **Suppress \<diagnostic ID>**.</span></span> <span data-ttu-id="9e9e3-135">Istnieją dwa sposoby pomijanie ostrzeżeń:</span><span class="sxs-lookup"><span data-stu-id="9e9e3-135">There are two ways to suppress warnings:</span></span> 

* [<span data-ttu-id="9e9e3-136">lokalnie (w źródle)</span><span class="sxs-lookup"><span data-stu-id="9e9e3-136">locally (in source)</span></span>](#suppressing-warnings-locally)
* <span data-ttu-id="9e9e3-137">[globalny (w pliku pominięć)](#suppressing-warnings-globally) — jest to zalecane</span><span class="sxs-lookup"><span data-stu-id="9e9e3-137">[globally (in a suppression file)](#suppressing-warnings-globally) - recommended</span></span>

### <a name="suppressing-warnings-locally"></a><span data-ttu-id="9e9e3-138">Pomijanie ostrzeżeń lokalnie</span><span class="sxs-lookup"><span data-stu-id="9e9e3-138">Suppressing warnings locally</span></span>

<span data-ttu-id="9e9e3-139">Aby pominąć ostrzeżenia lokalnie, kliknij prawym przyciskiem myszy element członkowski ma być pomijanie ostrzeżeń dla, a następnie wybierz **szybkie akcje i Refaktoryzacje** > **Pomiń *Identyfikator diagnostyczny* \<Identyfikator diagnostyczny >** > **w źródle**.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-139">To suppress warnings locally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Source**.</span></span> <span data-ttu-id="9e9e3-140">[#Pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) ostrzeżenie dyrektywy preprocesora jest dodawana do kodu źródłowego w zakresie zdefiniowanym: !["Zrzut ekranu przedstawiający kodu w ramce z Wyłącz ostrzeżenia #pragma"](media/api-analyzer/suppress-in-source.jpg)</span><span class="sxs-lookup"><span data-stu-id="9e9e3-140">The [#pragma](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) warning preprocessor directive is added to your source code in the scope defined: !["Screenshot of code framed with #pragma warning disable"](media/api-analyzer/suppress-in-source.jpg)</span></span>

### <a name="suppressing-warnings-globally"></a><span data-ttu-id="9e9e3-141">Pomijanie ostrzeżeń globalny</span><span class="sxs-lookup"><span data-stu-id="9e9e3-141">Suppressing warnings globally</span></span>

<span data-ttu-id="9e9e3-142">Aby pominąć ostrzeżenia globalnie, kliknij prawym przyciskiem myszy element członkowski ma być pomijanie ostrzeżeń dla, a następnie wybierz **szybkie akcje i Refaktoryzacje** > **Pomiń *Identyfikator diagnostyczny* \<Identyfikator diagnostyczny >** > **w pliku pominięć**.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-142">To suppress warnings globally, right-click on the member you want to suppress warnings for and then select **Quick Actions and Refactorings** > **Suppress *diagnostic ID*\<diagnostic ID>** > **in Suppression File**.</span></span>

!["Zrzut ekranu WebClient interfejsu API z zielonym dowolnym kształcie wiersza i żarówki po lewej stronie"](media/api-analyzer/suppress-in-sup-file.jpg)

<span data-ttu-id="9e9e3-144">A *GlobalSuppressions.cs* plik zostanie dodany do projektu po pierwszym pomijania.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-144">A *GlobalSuppressions.cs* file is added to your project after the first suppression.</span></span> <span data-ttu-id="9e9e3-145">Nowe pominięcia globalne są dołączane do tego pliku.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-145">New global suppressions are appended to this file.</span></span>

!["Zrzut ekranu WebClient interfejsu API z zielonym dowolnym kształcie wiersza i żarówki po lewej stronie"](media/api-analyzer/suppression-file.jpg)

<span data-ttu-id="9e9e3-147">Pomijanie globalnego jest zalecanym sposobem zapewnienia spójności interfejsu API użycia wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-147">Global suppression is the recommended way to ensure consistency of API usage across projects.</span></span>

## <a name="discovering-cross-platform-issues"></a><span data-ttu-id="9e9e3-148">Wykrywanie problemów i platform</span><span class="sxs-lookup"><span data-stu-id="9e9e3-148">Discovering cross-platform issues</span></span>

<span data-ttu-id="9e9e3-149">Podobnie jak przestarzałe interfejsy API, wszystkich interfejsów API, które nie są międzyplatformowa identyfikuje analizatora.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-149">Similar to deprecated APIs, the analyzer identifies all APIs that are not cross-platform.</span></span> <span data-ttu-id="9e9e3-150">Na przykład <xref:System.Console.WindowWidth?displayProperty=nameWithType> działa w systemie Windows, ale nie w systemie Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-150">For example, <xref:System.Console.WindowWidth?displayProperty=nameWithType> works on Windows but not on Linux and macOS.</span></span> <span data-ttu-id="9e9e3-151">Identyfikator diagnostyczny jest wyświetlany w obszarze **listy błędów** okna.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-151">The diagnostic ID is shown in the **Error List** window.</span></span> <span data-ttu-id="9e9e3-152">Można pominąć tego ostrzeżenia, klikając prawym przyciskiem myszy i wybierając **szybkie akcje i Refaktoryzacje**.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-152">You can suppress that warning by right-clicking and selecting **Quick Actions and Refactorings**.</span></span> <span data-ttu-id="9e9e3-153">W odróżnieniu od amortyzacja przypadków, gdy są dostępne dwie opcje (nadal używaj przestarzały element członkowski i pomijanie ostrzeżeń lub nie używać na wszystkich), w tym miejscu Jeśli projektujesz kodu tylko dla niektórych platform, można pominąć wszystkie ostrzeżenia dla innych platform, nie musisz Zaplanuj uruchamianie kodzie.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-153">Unlike deprecation cases where you have two options (either keep using the deprecated member and suppress warnings or not use it at all), here if you're developing your code only for certain platforms, you can suppress all warnings for all other platforms you don't plan to run your code on.</span></span> <span data-ttu-id="9e9e3-154">W tym celu wystarczy edytowanie pliku projektu i dodawanie `PlatformCompatIgnore` właściwość, która zawiera listę wszystkich platform, które mają być ignorowane.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-154">To do so, you just need to edit your project file and add the `PlatformCompatIgnore` property that lists all platforms to be ignored.</span></span> <span data-ttu-id="9e9e3-155">Dopuszczalne wartości to: `Linux`, `MacOSX`, i `Windows`.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-155">The accepted values are: `Linux`, `MacOSX`, and `Windows`.</span></span>

```xml
<PropertyGroup>
    <PlatformCompatIgnore>Linux;MacOS</PlatformCompatIgnore>
</PropertyGroup>
```

<span data-ttu-id="9e9e3-156">Jeśli kod jest przeznaczony dla wielu platform i chcesz korzystać z interfejsu API nie jest obsługiwana w przypadku niektórych z nich, można zabezpieczyć części kodu przy użyciu `if` instrukcji:</span><span class="sxs-lookup"><span data-stu-id="9e9e3-156">If your code targets multiple platforms and you want to take advantage of an API not supported on some of them, you can guard that part of the code with an `if` statement:</span></span>

```csharp
if (RuntimeInformation.IsOSPlatform(OSPlatform.Windows))
{
     var w = Console.WindowWidth;
     // More code
}
```

<span data-ttu-id="9e9e3-157">Można również warunkowo kompilowania dla docelowego systemu operacyjnego/framework, ale należy obecnie w tym [ręcznie](../frameworks.md#how-to-specify-target-frameworks).</span><span class="sxs-lookup"><span data-stu-id="9e9e3-157">You can also conditionally compile per target framework/operating system, but you currently need to do that [manually](../frameworks.md#how-to-specify-target-frameworks).</span></span>

## <a name="supported-diagnostics"></a><span data-ttu-id="9e9e3-158">Obsługiwane diagnostyki</span><span class="sxs-lookup"><span data-stu-id="9e9e3-158">Supported diagnostics</span></span>

<span data-ttu-id="9e9e3-159">Analizatora obsługuje obecnie następujących przypadkach:</span><span class="sxs-lookup"><span data-stu-id="9e9e3-159">Currently, the analyzer handles the following cases:</span></span>

* <span data-ttu-id="9e9e3-160">Użycie API standardowe .NET, która zgłasza <xref:System.PlatformNotSupportedException> (PC001).</span><span class="sxs-lookup"><span data-stu-id="9e9e3-160">Usage of a .NET Standard API that throws <xref:System.PlatformNotSupportedException> (PC001).</span></span>
* <span data-ttu-id="9e9e3-161">Użycie standardowych interfejs API programu .NET, który nie jest dostępna w programie .NET Framework 4.6.1 (PC002).</span><span class="sxs-lookup"><span data-stu-id="9e9e3-161">Usage of a .NET Standard API that isn't available on the .NET Framework 4.6.1 (PC002).</span></span>
* <span data-ttu-id="9e9e3-162">Użycie natywnego interfejsu API, który nie istnieje w platformy uniwersalnej systemu Windows (PC003).</span><span class="sxs-lookup"><span data-stu-id="9e9e3-162">Usage of a native API that doesn’t exist in UWP (PC003).</span></span>
* <span data-ttu-id="9e9e3-163">Użycie interfejsu API, który jest oznaczony jako przestarzały (DEXXXX).</span><span class="sxs-lookup"><span data-stu-id="9e9e3-163">Usage of an API that is marked as deprecated (DEXXXX).</span></span>

## <a name="ci-machine"></a><span data-ttu-id="9e9e3-164">Elementu konfiguracji komputera</span><span class="sxs-lookup"><span data-stu-id="9e9e3-164">CI machine</span></span>

<span data-ttu-id="9e9e3-165">Te funkcje diagnostyki jest dostępna nie tylko w środowisku IDE, ale również w wierszu polecenia w ramach tworzenia projektu, która obejmuje serwer elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-165">All these diagnostics are available not only in the IDE, but also on the command line as part of building your project, which includes the CI server.</span></span>

## <a name="configuration"></a><span data-ttu-id="9e9e3-166">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="9e9e3-166">Configuration</span></span>

<span data-ttu-id="9e9e3-167">Użytkownik decyduje o tym, jak powinny być traktowane diagnostyki: jako ostrzeżenia, błędów, sugestie lub być wyłączone.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-167">The user decides how the diagnostics should be treated: as warnings, errors, suggestions, or to be turned off.</span></span> <span data-ttu-id="9e9e3-168">Na przykład jako architekta, można określić czy problemy ze zgodnością powinny być traktowane jako błędy, wywołania niektórych przestarzałych interfejsów API generowania ostrzeżeń, podczas gdy inne generować tylko sugestie.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-168">For example, as an architect, you can decide that compatibility issues should be treated as errors, calls to some deprecated APIs generate warnings, while others only generate suggestions.</span></span> <span data-ttu-id="9e9e3-169">Można skonfigurować to oddzielnie za pomocą Identyfikatora diagnostycznych i przez projekt.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-169">You can configure this separately by diagnostic ID and by project.</span></span> <span data-ttu-id="9e9e3-170">Dlatego w celu **Eksploratora rozwiązań**, przejdź do **zależności** węźle projektu.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-170">To do so in **Solution Explorer**, navigate to the **Dependencies** node under your project.</span></span> <span data-ttu-id="9e9e3-171">Rozwiń węzły **zależności** > **analizatorów** > **Microsoft.DotNet.Analyzers.Compatibility**.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-171">Expand the nodes **Dependencies** > **Analyzers** > **Microsoft.DotNet.Analyzers.Compatibility**.</span></span> <span data-ttu-id="9e9e3-172">Kliknij prawym przyciskiem myszy Identyfikator diagnostyczny wybierz **ustawić ważność ustawić reguły** i wybierz odpowiednią opcję.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-172">Right click on the diagnostic ID, select **Set Rule Set Severity** and pick the desired option.</span></span>

!["Zrzut ekranu przedstawiający Eksploratora rozwiązań przedstawiający diagnostyki i wyskakujące okno dialogowe z reguły ustawić ważność"](media/api-analyzer/disable-notifications.jpg)

## <a name="see-also"></a><span data-ttu-id="9e9e3-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e9e3-174">See also</span></span>

* <span data-ttu-id="9e9e3-175">[Wprowadzenie do interfejsu API analizator](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) wpis w blogu.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-175">[Introducing API Analyzer](https://blogs.msdn.microsoft.com/dotnet/2017/10/31/introducing-api-analyzer/) blog post.</span></span>
* <span data-ttu-id="9e9e3-176">[Analizator interfejsu API](https://youtu.be/eeBEahYXGd0) pokaz wideo w serwisie YouTube.</span><span class="sxs-lookup"><span data-stu-id="9e9e3-176">[API Analyzer](https://youtu.be/eeBEahYXGd0) demo video on YouTube.</span></span>