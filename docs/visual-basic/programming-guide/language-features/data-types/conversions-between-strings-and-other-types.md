---
title: "Konwertowanie pomiędzy ciągami a innymi typami danych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 71ece18d4ce33b7b637410110e825b389affcd67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="fb42c-102">Konwertowanie pomiędzy ciągami a innymi typami danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb42c-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>
<span data-ttu-id="fb42c-103">Możesz przekształcić liczbową, `Boolean`, lub wartości daty/godziny `String`.</span><span class="sxs-lookup"><span data-stu-id="fb42c-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="fb42c-104">Można również przeprowadzić konwersję w kierunku odwrotnym — z wartości ciągu na liczbowe, `Boolean`, lub `Date` — pod warunkiem zawartość ciąg może zostać zinterpretowany jako prawidłowa wartość docelowego typu danych.</span><span class="sxs-lookup"><span data-stu-id="fb42c-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="fb42c-105">Jeśli nie, występuje błąd w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fb42c-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="fb42c-106">Konwersje wszystkich tych przydziałów w żadnym kierunku są zawężanie konwersji.</span><span class="sxs-lookup"><span data-stu-id="fb42c-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="fb42c-107">Należy używać słowa kluczowe konwersji typu (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, i `CType`).</span><span class="sxs-lookup"><span data-stu-id="fb42c-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="fb42c-108"><xref:Microsoft.VisualBasic.Strings.Format%2A> i <xref:Microsoft.VisualBasic.Conversion.Val%2A> funkcje zapewniają dodatkową kontrolę nad Konwertowanie pomiędzy ciągami a cyfry.</span><span class="sxs-lookup"><span data-stu-id="fb42c-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="fb42c-109">Jeśli zdefiniowano klasę lub strukturę można zdefiniować typu operatory konwersji między `String` i typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="fb42c-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="fb42c-110">Aby uzyskać więcej informacji, zobacz [porady: Definiowanie operatora konwersji](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="fb42c-110">For more information, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="fb42c-111">Konwersja liczb znajdujących się na ciągi</span><span class="sxs-lookup"><span data-stu-id="fb42c-111">Conversion of Numbers to Strings</span></span>  
 <span data-ttu-id="fb42c-112">Można użyć `Format` funkcja Konwertuj liczbę na ciąg formatowania, może zawierać nie tylko odpowiednie cyfr, ale również formatowanie symbole, takie jak znak waluty (takich jak `$`), tysięcy separatorów lub *grupowania cyfr symbole* (takich jak `,`) i separator dziesiętny (takie jak `.`).</span><span class="sxs-lookup"><span data-stu-id="fb42c-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="fb42c-113">`Format`automatycznie wykorzystuje odpowiednie symbole zgodnie z **Opcje regionalne** ustawienia określone w oknach **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="fb42c-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="fb42c-114">Należy pamiętać, że połączenie (`&`) — operator może konwertowanie liczby na ciąg niejawnie w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="fb42c-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="fb42c-115">Konwersja ciągów na liczby</span><span class="sxs-lookup"><span data-stu-id="fb42c-115">Conversion of Strings to Numbers</span></span>  
 <span data-ttu-id="fb42c-116">Można użyć `Val` funkcji, aby jawnie przekonwertować na liczbę cyfr w ciągu.</span><span class="sxs-lookup"><span data-stu-id="fb42c-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="fb42c-117">`Val`odczytuje ciąg, aż do napotkania znaków innych niż cyfry, miejsca, karta, wysuwu wiersza lub okres.</span><span class="sxs-lookup"><span data-stu-id="fb42c-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="fb42c-118">Sekwencje "&" i "& H" alter podstawą układzie i zakończenie skanowania.</span><span class="sxs-lookup"><span data-stu-id="fb42c-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="fb42c-119">Do jej zamknięcia czytania, `Val` konwertuje wszystkie znaki odpowiednią wartość liczbowa.</span><span class="sxs-lookup"><span data-stu-id="fb42c-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="fb42c-120">Na przykład następująca instrukcja zwraca wartość `141.825`.</span><span class="sxs-lookup"><span data-stu-id="fb42c-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="fb42c-121">Gdy [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] konwertuje ciąg na wartość numeryczną, używa **Opcje regionalne** ustawienia określone w oknach **Panelu sterowania** interpretować tysięcy separator, separator dziesiętny i symbol waluty.</span><span class="sxs-lookup"><span data-stu-id="fb42c-121">When [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="fb42c-122">Oznacza to, że konwersja może się powieść w jednej ustawienie, ale nie inna.</span><span class="sxs-lookup"><span data-stu-id="fb42c-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="fb42c-123">Na przykład `"$14.20"` jest akceptowalne z ustawieniami regionalnymi Angielski (Stany Zjednoczone), ale nie w dowolnych francuskim ustawień regionalnych.</span><span class="sxs-lookup"><span data-stu-id="fb42c-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb42c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fb42c-124">See Also</span></span>  
 [<span data-ttu-id="fb42c-125">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb42c-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="fb42c-126">Rozszerzanie i zwężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="fb42c-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="fb42c-127">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="fb42c-127">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="fb42c-128">Porady: konwertowanie obiektu do innego typu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb42c-128">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="fb42c-129">Konwersje tablic</span><span class="sxs-lookup"><span data-stu-id="fb42c-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="fb42c-130">Typy danych</span><span class="sxs-lookup"><span data-stu-id="fb42c-130">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="fb42c-131">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="fb42c-131">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="fb42c-132">Wprowadzenie do aplikacji międzynarodowych oparte na programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fb42c-132">Introduction to International Applications Based on the .NET Framework</span></span>](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)