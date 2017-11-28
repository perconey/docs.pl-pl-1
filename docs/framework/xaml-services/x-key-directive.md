---
title: "x:Key — dyrektywa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
caps.latest.revision: "25"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 5e2ad03fcb52db1ffdd01849381a392187082991
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xkey-directive"></a><span data-ttu-id="85018-102">x:Key — dyrektywa</span><span class="sxs-lookup"><span data-stu-id="85018-102">x:Key Directive</span></span>
<span data-ttu-id="85018-103">Identyfikuje elementy, które są tworzone i przywoływany w słowniku zdefiniowany w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="85018-103">Uniquely identifies elements that are created and referenced in a XAML-defined dictionary.</span></span> <span data-ttu-id="85018-104">Dodawanie `x:Key` wartość do elementu obiektu XAML jest najczęściej do identyfikacji zasobu w słowniku zasobów, na przykład na platformie WPF <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="85018-104">Adding an `x:Key` value to a XAML object element is the most common way to identify a resource in a resource dictionary, for example in a WPF <xref:System.Windows.ResourceDictionary>.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="85018-105">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="85018-105">XAML Attribute Usage</span></span>  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a><span data-ttu-id="85018-106">Użycie atrybutu XAML (WPF specyficzne)</span><span class="sxs-lookup"><span data-stu-id="85018-106">XAML Attribute Usage (WPF-specific)</span></span>  
  
```  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="85018-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="85018-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`stringKeyValue`|<span data-ttu-id="85018-108">Ciąg tekstowy, można użyć jako klucza.</span><span class="sxs-lookup"><span data-stu-id="85018-108">A text string to use as a key.</span></span> <span data-ttu-id="85018-109">Ciąg tekstowy musi być zgodna z [xamlname — gramatyka](../../../docs/framework/xaml-services/xamlname-grammar.md).</span><span class="sxs-lookup"><span data-stu-id="85018-109">The text string must conform to the [XamlName Grammar](../../../docs/framework/xaml-services/xamlname-grammar.md).</span></span>|  
|`markupExtensionUsage`|<span data-ttu-id="85018-110">W ramach {} ograniczniki rozszerzenia znaczników użycie rozszerzenia znaczników, która zapewnia obiekt, aby użyć jako klucza.</span><span class="sxs-lookup"><span data-stu-id="85018-110">Within the markup extension delimiters {}, a markup extension usage that provides an object to use as a key.</span></span> <span data-ttu-id="85018-111">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="85018-111">See Remarks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85018-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85018-112">Remarks</span></span>  
 <span data-ttu-id="85018-113">`x:Key`obsługuje pojęcie słownika zasobów XAML.</span><span class="sxs-lookup"><span data-stu-id="85018-113">`x:Key` supports the XAML resource dictionary concept.</span></span> <span data-ttu-id="85018-114">XAML jako język nie definiuje implementacji słownika zasobów, który jest od lewej do określonych platform interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="85018-114">XAML as a language doesn't define a resource dictionary implementation, that is left to specific UI frameworks.</span></span> <span data-ttu-id="85018-115">Aby dowiedzieć się więcej na temat implementowania słowniki zasobów XAML w WPF, zobacz [zasobów XAML](../../../docs/framework/wpf/advanced/xaml-resources.md).</span><span class="sxs-lookup"><span data-stu-id="85018-115">To learn more about how XAML resource dictionaries are implemented in WPF, see [XAML Resources](../../../docs/framework/wpf/advanced/xaml-resources.md).</span></span>  
  
 <span data-ttu-id="85018-116">W języku XAML 2006 i WPF `x:Key` musi być dostarczona jako atrybut.</span><span class="sxs-lookup"><span data-stu-id="85018-116">In XAML 2006 and WPF, `x:Key` must be provided as an attribute.</span></span> <span data-ttu-id="85018-117">Można nadal używać kluczy typu, ale wymaga to użycia rozszerzenie znaczników w celu podania wartości typu w formie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="85018-117">You can still use nonstring keys, but this requires a markup extension usage in order to provide the nonstring value in attribute form.</span></span> <span data-ttu-id="85018-118">Jeśli używasz XAML 2009 `x:Key` może być określony jako element, do obsługi jawnie słowników, wyznaczaną przez obiekty mają typ innych niż ciągi bez konieczności pośredniego rozszerzeniem znacznika.</span><span class="sxs-lookup"><span data-stu-id="85018-118">If you are using XAML 2009, `x:Key` can be specified as an element, to explicitly support dictionaries keyed by object types other than strings without requiring a markup extension intermediate.</span></span> <span data-ttu-id="85018-119">Zobacz sekcję "XAML 2009" w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="85018-119">See the "XAML 2009" section in this topic.</span></span> <span data-ttu-id="85018-120">W pozostałej części sekcji uwag w szczególności dotyczy implementacji XAML 2006.</span><span class="sxs-lookup"><span data-stu-id="85018-120">The remainder of the Remarks section applies specifically to the XAML 2006 implementation.</span></span>  
  
 <span data-ttu-id="85018-121">Wartość atrybutu `x:Key` może być dowolny ciąg zdefiniowany w [xamlname — gramatyka](../../../docs/framework/xaml-services/xamlname-grammar.md) lub może być obiektem oceniane za pośrednictwem rozszerzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="85018-121">The attribute value of `x:Key` can be any string defined in the [XamlName Grammar](../../../docs/framework/xaml-services/xamlname-grammar.md) or can be an object evaluated through a markup extension.</span></span> <span data-ttu-id="85018-122">Na przykład z WPF, zobacz "Notatki dotyczące użytkowania WPF".</span><span class="sxs-lookup"><span data-stu-id="85018-122">See "WPF Usage Notes" for an example from WPF.</span></span>  
  
 <span data-ttu-id="85018-123">Elementy podrzędne elementu nadrzędnego, który jest <xref:System.Collections.IDictionary> zwykle musi zawierać implementację `x:Key` atrybut, który określa unikatową wartość klucza w ramach tego słownika.</span><span class="sxs-lookup"><span data-stu-id="85018-123">Child elements of a parent element that is an <xref:System.Collections.IDictionary> implementation must typically include an `x:Key` attribute that specifies a unique key value within that dictionary.</span></span> <span data-ttu-id="85018-124">Struktury mogą implementować Aliasy właściwości klucza do zastąpienia dla `x:Key` w określonych typach; powinien mieć atrybut typy, które definiują takich właściwości <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.</span><span class="sxs-lookup"><span data-stu-id="85018-124">Frameworks might implement aliased key properties to substitute for `x:Key` on particular types; types that define such properties should be attributed with <xref:System.Windows.Markup.DictionaryKeyPropertyAttribute>.</span></span>  
  
 <span data-ttu-id="85018-125">Określanie odpowiednikiem kodu `x:Key` jest klucz, który służy do odpowiadającego <xref:System.Collections.IDictionary>.</span><span class="sxs-lookup"><span data-stu-id="85018-125">The code equivalent of specifying `x:Key` is the key that is used for the underlying <xref:System.Collections.IDictionary>.</span></span> <span data-ttu-id="85018-126">Na przykład `x:Key` jakie jest stosowane w znaczniku zasobów na platformie WPF jest odpowiednikiem wartości `key` parametr <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> po dodaniu zasobu WPF <xref:System.Windows.ResourceDictionary> w kodzie.</span><span class="sxs-lookup"><span data-stu-id="85018-126">For example, an `x:Key` that is applied in markup for a resource in WPF is equivalent to the value of the `key` parameter of <xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> when you add the resource to a WPF <xref:System.Windows.ResourceDictionary> in code.</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="85018-127">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="85018-127">WPF Usage Notes</span></span>  
 <span data-ttu-id="85018-128">Obiekty podrzędne nadrzędny obiekt <xref:System.Collections.IDictionary> wdrażania, takie jak WPF <xref:System.Windows.ResourceDictionary>, zwykle musi zawierać `x:Key` atrybutu i wartości klucza muszą być unikatowe w obrębie tego słownika.</span><span class="sxs-lookup"><span data-stu-id="85018-128">Child objects of a parent object that is an <xref:System.Collections.IDictionary> implementation, such as the WPF <xref:System.Windows.ResourceDictionary>, must typically include an `x:Key` attribute, and the key value must be unique within that dictionary.</span></span> <span data-ttu-id="85018-129">Istnieją dwa godnymi uwagi wyjątkami:</span><span class="sxs-lookup"><span data-stu-id="85018-129">There are two notable exceptions:</span></span>  
  
-   <span data-ttu-id="85018-130">Niektóre typy WPF zadeklarować niejawne klucz dla słownika użycia.</span><span class="sxs-lookup"><span data-stu-id="85018-130">Some WPF types declare an implicit key for dictionary usage.</span></span> <span data-ttu-id="85018-131">Na przykład <xref:System.Windows.Style> z <xref:System.Windows.Style.TargetType%2A>, lub <xref:System.Windows.DataTemplate> z <xref:System.Windows.DataTemplate.DataType%2A>, mogą znajdować się w <xref:System.Windows.ResourceDictionary> i użyj niejawne klucza.</span><span class="sxs-lookup"><span data-stu-id="85018-131">For example, a <xref:System.Windows.Style> with a <xref:System.Windows.Style.TargetType%2A>, or a <xref:System.Windows.DataTemplate> with a <xref:System.Windows.DataTemplate.DataType%2A>, can be  in a <xref:System.Windows.ResourceDictionary> and use the implicit key.</span></span>  
  
-   <span data-ttu-id="85018-132">WPF obsługuje pojęcie słownika zasobów scalone.</span><span class="sxs-lookup"><span data-stu-id="85018-132">WPF supports a merged resource dictionary concept.</span></span> <span data-ttu-id="85018-133">Klucze mogą udostępniać scalonych słownikach i zachowanie klucza udostępnionego można uzyskać dostęp za pomocą <xref:System.Windows.FrameworkContentElement.FindResource%2A>.</span><span class="sxs-lookup"><span data-stu-id="85018-133">Keys can be shared between the merged dictionaries, and the shared key behavior can be accessed using <xref:System.Windows.FrameworkContentElement.FindResource%2A>.</span></span> <span data-ttu-id="85018-134">Aby uzyskać więcej informacji, zobacz [scalić słowniki zasobów](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).</span><span class="sxs-lookup"><span data-stu-id="85018-134">For more information, see [Merged Resource Dictionaries](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
 <span data-ttu-id="85018-135">W ogólnej WPF XAML wdrożenia i stosowania modelu unikatowości klucza nie jest sprawdzana przez kompilator znaczników XAML.</span><span class="sxs-lookup"><span data-stu-id="85018-135">In the overall WPF XAML implementation and application model, key uniqueness is not checked by the XAML markup compiler.</span></span> <span data-ttu-id="85018-136">Zamiast tego brakujące lub nieunikatowy `x:Key` wartości powodują błędy analizatora czasu ładowania XAML.</span><span class="sxs-lookup"><span data-stu-id="85018-136">Instead, missing or nonunique `x:Key` values cause load-time XAML parser errors.</span></span> <span data-ttu-id="85018-137">Jednak [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] obsługi słowników dla WPF często może zanotować takie błędy w fazie projektowania.</span><span class="sxs-lookup"><span data-stu-id="85018-137">However, [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] handling of dictionaries for WPF can often note such errors in the design phase.</span></span>  
  
 <span data-ttu-id="85018-138">Należy pamiętać, że w składni pokazano, <xref:System.Windows.ResourceDictionary> obiektu jest niejawnie w sposób procesora WPF XAML tworzy kolekcję, aby wypełnić <xref:System.Windows.FrameworkElement.Resources%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="85018-138">Note that in the syntax shown, the <xref:System.Windows.ResourceDictionary> object is implicit in how the WPF XAML processor produces a collection to populate a <xref:System.Windows.FrameworkElement.Resources%2A> collection.</span></span> <span data-ttu-id="85018-139">A <xref:System.Windows.ResourceDictionary> nie jest zwykle podana jawnie jako element w znaczniku, chociaż może być w niektórych przypadkach, jeśli dla jasności (byłoby elementu obiektu między <xref:System.Windows.FrameworkElement.Resources%2A> wypełniania elementu właściwości i elementów w tym Słownik).</span><span class="sxs-lookup"><span data-stu-id="85018-139">A <xref:System.Windows.ResourceDictionary> is not typically provided explicitly as an element in markup, although it can be in some cases if wanted for clarity (it would be a collection object element between the <xref:System.Windows.FrameworkElement.Resources%2A> property element and the items within that populate the dictionary).</span></span> <span data-ttu-id="85018-140">Aby uzyskać informacje o tym, dlaczego obiekt kolekcji jest prawie zawsze element niejawne w znaczniku, zobacz [szczegółów w składni języka XAML](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).</span><span class="sxs-lookup"><span data-stu-id="85018-140">For information about why a collection object is almost always an implicit element in markup, see [XAML Syntax In Detail](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md).</span></span>  
  
 <span data-ttu-id="85018-141">W implementacji WPF XAML obsługę klucze słownika zasobów jest definiowana za pomocą <xref:System.Windows.ResourceKey> klasy abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="85018-141">In the WPF XAML implementation, the handling for resource dictionary keys is defined by the <xref:System.Windows.ResourceKey> abstract class.</span></span> <span data-ttu-id="85018-142">Jednak procesora WPF XAML tworzy różne typy rozszerzeń podstawowej kluczy oparte na ich użycia.</span><span class="sxs-lookup"><span data-stu-id="85018-142">However the WPF XAML processor produces different underlying extension types for keys based on their usages.</span></span> <span data-ttu-id="85018-143">Na przykład klucz dla <xref:System.Windows.DataTemplate> lub dowolnej klasy pochodnej jest obsługiwane oddzielnie i tworzy oddzielny <xref:System.Windows.DataTemplateKey> obiektu.</span><span class="sxs-lookup"><span data-stu-id="85018-143">For example, the key for a <xref:System.Windows.DataTemplate> or any derived class is handled separately, and produces a distinct <xref:System.Windows.DataTemplateKey> object.</span></span>  
  
 <span data-ttu-id="85018-144">Klucze i nazwy używają różnych dyrektywy i elementy języka (`x:Key` i `x:Name`) do podstawowych definicji XAML.</span><span class="sxs-lookup"><span data-stu-id="85018-144">Keys and names use different directives and language elements (`x:Key` versus `x:Name`) in the basic XAML definition.</span></span> <span data-ttu-id="85018-145">Nazwy i klucze są również używane w różnych sytuacjach stosowania tych pojęć i definicji WPF.</span><span class="sxs-lookup"><span data-stu-id="85018-145">Keys and names are also used in different situations by the WPF definition and application of these concepts.</span></span> <span data-ttu-id="85018-146">Aby uzyskać więcej informacji, zobacz [WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).</span><span class="sxs-lookup"><span data-stu-id="85018-146">For details, see [WPF XAML Namescopes](../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md).</span></span>  
  
 <span data-ttu-id="85018-147">Jak wspomniano wcześniej, wartość klucza mogą być dostarczane za pomocą rozszerzenia znacznika i może być inna niż wartość ciągu.</span><span class="sxs-lookup"><span data-stu-id="85018-147">As stated previously, the value of a key can be supplied through a markup extension and can be other than a string value.</span></span> <span data-ttu-id="85018-148">Przykładowy scenariusz WPF jest wartością `x:Key` może być[ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md).</span><span class="sxs-lookup"><span data-stu-id="85018-148">An example WPF scenario is that the value of `x:Key` may be a[ComponentResourceKey](../../../docs/framework/wpf/advanced/componentresourcekey-markup-extension.md).</span></span> <span data-ttu-id="85018-149">Niektóre formanty ujawnia klucz styl tego typu zasobu styl niestandardowy, który wpływa bez całkowicie zastępowania styl części wygląd i zachowanie tego formantu.</span><span class="sxs-lookup"><span data-stu-id="85018-149">Certain controls expose a style key of that type for a custom style resource that influences part of the appearance and behavior of that control without totally replacing the style.</span></span> <span data-ttu-id="85018-150">Przykładem takiego klucza jest <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="85018-150">An example of such a key is <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>.</span></span>  
  
 <span data-ttu-id="85018-151">Funkcja połączony słownik WPF wprowadza dodatkowe zagadnienia dotyczące unikatowości klucza i zachowanie wyszukiwania klucza.</span><span class="sxs-lookup"><span data-stu-id="85018-151">The WPF merged dictionary feature introduces additional considerations for key uniqueness and key lookup behavior.</span></span> <span data-ttu-id="85018-152">Aby uzyskać więcej informacji, zobacz [scalić słowniki zasobów](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).</span><span class="sxs-lookup"><span data-stu-id="85018-152">For more information, see [Merged Resource Dictionaries](../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md).</span></span>  
  
## <a name="xaml-2009"></a><span data-ttu-id="85018-153">XAML 2009</span><span class="sxs-lookup"><span data-stu-id="85018-153">XAML 2009</span></span>  
 <span data-ttu-id="85018-154">XAML 2009 zwalnia ograniczenie który `x:Key` zawsze być udostępniane w formie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="85018-154">XAML 2009 relaxes the restriction that `x:Key` always be provided in attribute form.</span></span>  
  
 <span data-ttu-id="85018-155">Na platformie WPF można użyć XAML 2009 — funkcje, ale tylko dla języka XAML, który nie jest kompilowany do znaczników.</span><span class="sxs-lookup"><span data-stu-id="85018-155">In WPF, you can use XAML 2009 features, but only for XAML that is not markup-compiled.</span></span> <span data-ttu-id="85018-156">Skompilowany kod znaczników XAML w WPF i BAML formę XAML aktualnie nie obsługują słowa kluczowe języka XAML 2009 i funkcje.</span><span class="sxs-lookup"><span data-stu-id="85018-156">Markup-compiled XAML for WPF and the BAML form of XAML do not currently support the XAML 2009 keywords and features.</span></span>  
  
 <span data-ttu-id="85018-157">W obszarze XAML 2009, można określić `x:Key` elementów przy użyciu następującego użycia:</span><span class="sxs-lookup"><span data-stu-id="85018-157">Under XAML 2009, you can specify `x:Key` elements through the following usage:</span></span>  
  
### <a name="xaml-element-usage-xaml-2009-only"></a><span data-ttu-id="85018-158">Użycie elementu XAML (tylko w języku XAML 2009)</span><span class="sxs-lookup"><span data-stu-id="85018-158">XAML Element Usage (XAML 2009 only)</span></span>  
  
```  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a><span data-ttu-id="85018-159">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="85018-159">XAML Values</span></span>  
  
|||  
|-|-|  
|`keyObject`|<span data-ttu-id="85018-160">Element Object dla obiekt, który jest używany jako klucz dla danego `object` w słowniku specjalne.</span><span class="sxs-lookup"><span data-stu-id="85018-160">Object element for the object that is used as the key for a given `object` in a specialized dictionary.</span></span>|  
  
-   <span data-ttu-id="85018-161">Kontener/nadrzędne dla tego rodzaju użycie nie jest wyświetlane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="85018-161">The container/parent for this kind of use is not shown here.</span></span> <span data-ttu-id="85018-162">`object`powinien być elementem podrzędnym elementu obiektu, który reprezentuje implementację specjalne słownika.</span><span class="sxs-lookup"><span data-stu-id="85018-162">`object` is expected to be a child of an object element that represents a specialized dictionary implementation.</span></span> <span data-ttu-id="85018-163">`keyObject`Oczekiwana wartość pola wystąpienia obiektu (lub wartość typu value) odpowiednią jako klucz dla tej implementacji określonego słownika specjalne.</span><span class="sxs-lookup"><span data-stu-id="85018-163">`keyObject` is expected to be an object instance (or a value of a value type) that is appropriate as the key for that particular specialized dictionary implementation.</span></span>  
  
-   <span data-ttu-id="85018-164">WPF nie implementuje słowników, które wymagają użycia.</span><span class="sxs-lookup"><span data-stu-id="85018-164">WPF does not implement dictionaries that require this usage.</span></span> <span data-ttu-id="85018-165">Klucze obiektu jest bardziej ogólne funkcji języka XAML, prawdopodobnie przydatne w przypadku niektórych scenariuszy słownika którym pożądane jest Tworzenie słownika w kodzie XAML.</span><span class="sxs-lookup"><span data-stu-id="85018-165">Object keys is more a general feature of the XAML language, possibly useful for certain custom dictionary scenarios where creating the dictionary in XAML is desirable.</span></span> <span data-ttu-id="85018-166">Dla funkcji WPF, takich jak niejawne style, które używają kluczy innych niż ciąg dla zasobów innych technik za ustanawianie lub określenie kluczy istnieje, więc przy użyciu klucza obiektu nie jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="85018-166">For WPF features such as implicit styles that use non-string keys for resources, other techniques for establishing or specifying the keys exist, so using an object key is not necessary.</span></span>  
  
-   <span data-ttu-id="85018-167">*keyObject* mogą być również użytkowania rozszerzenie znaczników w formularzu elementu obiektu, a nie wystąpienia obiektu bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="85018-167">*keyObject* could also be a markup extension usage in object element form, rather than a direct object instance.</span></span>  
  
## <a name="silverlight-usage-notes"></a><span data-ttu-id="85018-168">Uwagi dotyczące użycia programu Silverlight</span><span class="sxs-lookup"><span data-stu-id="85018-168">Silverlight Usage Notes</span></span>  
 <span data-ttu-id="85018-169">`x:Key`dla programu Silverlight jest udokumentowany oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="85018-169">`x:Key` for Silverlight is documented separately.</span></span> <span data-ttu-id="85018-170">Aby uzyskać więcej informacji, zobacz [Namespace XAML (x:) Funkcje języka (platformy Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).</span><span class="sxs-lookup"><span data-stu-id="85018-170">For more information, see [XAML Namespace (x:) Language Features (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85018-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85018-171">See Also</span></span>  
 [<span data-ttu-id="85018-172">Zasoby dla języka XAML</span><span class="sxs-lookup"><span data-stu-id="85018-172">XAML Resources</span></span>](../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="85018-173">Zasoby i kod</span><span class="sxs-lookup"><span data-stu-id="85018-173">Resources and Code</span></span>](../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [<span data-ttu-id="85018-174">Rozszerzenie StaticResource znaczników</span><span class="sxs-lookup"><span data-stu-id="85018-174">StaticResource Markup Extension</span></span>](../../../docs/framework/wpf/advanced/staticresource-markup-extension.md)