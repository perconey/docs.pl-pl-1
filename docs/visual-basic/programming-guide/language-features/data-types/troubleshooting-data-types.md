---
title: "Rozwiązywanie problemów związanych z typami danych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Char data type [Visual Basic], converting
- Decimal data type [Visual Basic], conversions
- data types [Visual Basic], troubleshooting
- literals [Visual Basic], default types
- type characters [Visual Basic], literal
- Mod operator [Visual Basic], in floating-point operations
- troubleshooting Visual Basic, data types
- troubleshooting data types [Visual Basic]
- floating-point numbers [Visual Basic], precision
- Boolean data type [Visual Basic], converting
- literal types [Visual Basic]
- literal type characters [Visual Basic]
- floating-point numbers [Visual Basic], imprecision
- String data type [Visual Basic], converting
- floating-point numbers [Visual Basic], comparison
- floating-point numbers
ms.assetid: 90040d67-b630-4125-a6ae-37195b079042
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4d2fb1cd1be9c88ad0dd413eedb8a226fe59f41e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-data-types-visual-basic"></a><span data-ttu-id="e7401-102">Rozwiązywanie problemów związanych z typami danych (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e7401-102">Troubleshooting Data Types (Visual Basic)</span></span>
<span data-ttu-id="e7401-103">Ta strona zawiera listę typowych problemów, które mogą wystąpić podczas wykonywania operacji na typy danych wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="e7401-103">This page lists some common problems that can occur when you perform operations on intrinsic data types.</span></span>  
  
## <a name="floating-point-expressions-do-not-compare-as-equal"></a><span data-ttu-id="e7401-104">Zmiennoprzecinkowe wyrażenia porównuje jako równe</span><span class="sxs-lookup"><span data-stu-id="e7401-104">Floating-Point Expressions Do Not Compare as Equal</span></span>  
 <span data-ttu-id="e7401-105">Podczas pracy z liczb zmiennoprzecinkowych ([jednego typu danych](../../../../visual-basic/language-reference/data-types/single-data-type.md) i [— typ danych Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)), należy pamiętać, że są one przechowywane jako binarne ułamków.</span><span class="sxs-lookup"><span data-stu-id="e7401-105">When you work with floating-point numbers ([Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md) and [Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md)), remember that they are stored as binary fractions.</span></span> <span data-ttu-id="e7401-106">Oznacza to, że nie posiadają dokładną reprezentację żadnych ilość, która nie jest binarny ułamek (w postaci k / (2 ^ n) gdzie k i n są liczbami całkowitymi).</span><span class="sxs-lookup"><span data-stu-id="e7401-106">This means they cannot hold an exact representation of any quantity that is not a binary fraction (of the form k / (2 ^ n) where k and n are integers).</span></span> <span data-ttu-id="e7401-107">Na przykład 0,5 (= 1/2) i 0.3125 (= 5/16) może być przechowywany jako dokładne wartości, 0,2 (= 1/5) i 0,3 (= 3/10) może być tylko przybliżeniem.</span><span class="sxs-lookup"><span data-stu-id="e7401-107">For example, 0.5 (= 1/2) and 0.3125 (= 5/16) can be held as precise values, whereas 0.2 (= 1/5) and 0.3 (= 3/10) can be only approximations.</span></span>  
  
 <span data-ttu-id="e7401-108">W związku z tym błędu, możesz nie zależą od dokładne wyniki podczas działania na wartości zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="e7401-108">Because of this imprecision, you cannot rely on exact results when you operate on floating-point values.</span></span> <span data-ttu-id="e7401-109">W szczególności dwie wartości, które są równe teoretycznie może być nieco inne oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="e7401-109">In particular, two values that are theoretically equal might have slightly different representations.</span></span>  
  
| <span data-ttu-id="e7401-110">Aby porównać liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="e7401-110">To compare floating-point quantities</span></span> | 
|---| 
|<span data-ttu-id="e7401-111">1.  Obliczyć wartość bezwzględna różnica ich przy użyciu <xref:System.Math.Abs%2A> metody <xref:System.Math> klasy w <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e7401-111">1.  Calculate the absolute value of their difference by using the <xref:System.Math.Abs%2A> method of the <xref:System.Math> class in the <xref:System> namespace.</span></span><br /><span data-ttu-id="e7401-112">2.  Określ dopuszczalne maksymalnego różnica taki sposób, że należy wziąć pod uwagę dwa ilości, które mają być taka sama dla celów praktycznych, jeśli ich różnica jest nie większy.</span><span class="sxs-lookup"><span data-stu-id="e7401-112">2.  Determine an acceptable maximum difference, such that you can consider the two quantities to be equal for practical purposes if their difference is no larger.</span></span><br /><span data-ttu-id="e7401-113">3.  Porównanie wartości bezwzględne różnicy dopuszczalne różnicy.</span><span class="sxs-lookup"><span data-stu-id="e7401-113">3.  Compare the absolute value of the difference to the acceptable difference.</span></span>|  
  
 <span data-ttu-id="e7401-114">W poniższym przykładzie pokazano zarówno nieprawidłowych i poprawne porównanie dwóch `Double` wartości.</span><span class="sxs-lookup"><span data-stu-id="e7401-114">The following example demonstrates both incorrect and correct comparison of two `Double` values.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#10](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_1.vb)]  
  
 <span data-ttu-id="e7401-115">W poprzednim przykładzie użyto <xref:System.Double.ToString%2A> metody <xref:System.Double> struktury, dzięki czemu można określić większą dokładność niż `CStr` używa słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="e7401-115">The previous example uses the <xref:System.Double.ToString%2A> method of the <xref:System.Double> structure so that it can specify better  precision than the `CStr` keyword uses.</span></span> <span data-ttu-id="e7401-116">Wartość domyślna to 15 cyfr, ale w formacie "G17" rozszerza on 17 cyfr.</span><span class="sxs-lookup"><span data-stu-id="e7401-116">The default is 15 digits, but the "G17" format extends it to 17 digits.</span></span>  
  
## <a name="mod-operator-does-not-return-accurate-result"></a><span data-ttu-id="e7401-117">Mod — Operator nie zwraca wyniku dokładne</span><span class="sxs-lookup"><span data-stu-id="e7401-117">Mod Operator Does Not Return Accurate Result</span></span>  
 <span data-ttu-id="e7401-118">Z powodu błędu zmiennoprzecinkowe magazynu [Mod Operator](../../../../visual-basic/language-reference/operators/mod-operator.md) może zwrócić nieoczekiwany wynik, gdy co najmniej jeden z argumentów jest zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="e7401-118">Because of the imprecision of floating-point storage, the [Mod Operator](../../../../visual-basic/language-reference/operators/mod-operator.md) can return an unexpected result when at least one of the operands is floating-point.</span></span>  
  
 <span data-ttu-id="e7401-119">[Typu danych dziesiętnych](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) nie używa odwzorowanie liczby zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="e7401-119">The [Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md) does not use floating-point representation.</span></span> <span data-ttu-id="e7401-120">Liczby, które są niedokładnymi w `Single` i `Double` są dokładnie w `Decimal` (na przykład 0.2 i 0,3).</span><span class="sxs-lookup"><span data-stu-id="e7401-120">Many numbers that are inexact in `Single` and `Double` are exact in `Decimal` (for example 0.2 and 0.3).</span></span> <span data-ttu-id="e7401-121">Mimo że arytmetyczne działa wolniej w `Decimal` niż w liczb zmiennoprzecinkowych, może być warto obniżenie wydajności w celu osiągnięcia lepszej dokładności.</span><span class="sxs-lookup"><span data-stu-id="e7401-121">Although arithmetic is slower in `Decimal` than in floating-point, it might be worth the performance decrease to achieve better precision.</span></span>  
  
|<span data-ttu-id="e7401-122">Aby znaleźć pozostałej liczby całkowitej ilości liczb zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="e7401-122">To find the integer remainder of floating-point quantities</span></span>|  
|---|  
|<span data-ttu-id="e7401-123">1.  Zadeklaruj zmienne jako `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e7401-123">1.  Declare variables as `Decimal`.</span></span><br /><span data-ttu-id="e7401-124">2.  Znak literalny typu `D` wymusić literały do `Decimal`, w przypadku, gdy ich wartości są za szerokie dla `Long` — typ danych.</span><span class="sxs-lookup"><span data-stu-id="e7401-124">2.  Use the literal type character `D` to force literals to `Decimal`, in case their values are too large for the `Long` data type.</span></span>|  
  
 <span data-ttu-id="e7401-125">W poniższym przykładzie pokazano ryzyko błędu argumentów operacji zmiennoprzecinkowej.</span><span class="sxs-lookup"><span data-stu-id="e7401-125">The following example demonstrates the potential imprecision of floating-point operands.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#11](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_2.vb)]  
  
 <span data-ttu-id="e7401-126">W poprzednim przykładzie użyto <xref:System.Double.ToString%2A> metody <xref:System.Double> struktury, dzięki czemu można określić większą dokładność niż `CStr` używa słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="e7401-126">The previous example uses the <xref:System.Double.ToString%2A> method of the <xref:System.Double> structure so that it can specify better precision than the `CStr` keyword uses.</span></span> <span data-ttu-id="e7401-127">Wartość domyślna to 15 cyfr, ale w formacie "G17" rozszerza on 17 cyfr.</span><span class="sxs-lookup"><span data-stu-id="e7401-127">The default is 15 digits, but the "G17" format extends it to 17 digits.</span></span>  
  
 <span data-ttu-id="e7401-128">Ponieważ `zeroPointTwo` jest `Double`, jego wartość 0,2 jest nieskończenie identycznych ułamek binarnego z wartością przechowywaną 0.20000000000000001.</span><span class="sxs-lookup"><span data-stu-id="e7401-128">Because `zeroPointTwo` is `Double`, its value for 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="e7401-129">Podzielenie 2.0 przez ilość ta daje 9.9999999999999995 pozostałych 0.19999999999999991.</span><span class="sxs-lookup"><span data-stu-id="e7401-129">Dividing 2.0 by this quantity yields 9.9999999999999995 with a remainder of 0.19999999999999991.</span></span>  
  
 <span data-ttu-id="e7401-130">W wyrażeniu dla `decimalRemainder`, znak literalny typu `D` wymusza oba argumenty do `Decimal`, i 0,2 ma reprezentację dokładne.</span><span class="sxs-lookup"><span data-stu-id="e7401-130">In the expression for `decimalRemainder`, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span> <span data-ttu-id="e7401-131">W związku z tym `Mod` operatora daje Oczekiwano końca 0,0.</span><span class="sxs-lookup"><span data-stu-id="e7401-131">Therefore the `Mod` operator yields the expected remainder of 0.0.</span></span>  
  
 <span data-ttu-id="e7401-132">Należy pamiętać, że nie jest wystarczające, aby zadeklarować `decimalRemainder` jako `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e7401-132">Note that it is not sufficient to declare `decimalRemainder` as `Decimal`.</span></span> <span data-ttu-id="e7401-133">Należy też wymusić literały do `Decimal`, lub wykorzystują `Double` domyślnie i `decimalRemainder` odbiera tę samą wartość niedokładne jako `doubleRemainder`.</span><span class="sxs-lookup"><span data-stu-id="e7401-133">You must also force the literals to `Decimal`, or they use `Double` by default and `decimalRemainder` receives the same inaccurate value as `doubleRemainder`.</span></span>  
  
## <a name="boolean-type-does-not-convert-to-numeric-type-accurately"></a><span data-ttu-id="e7401-134">Typ Boolean nie konwertować na typ liczbowy dokładnie</span><span class="sxs-lookup"><span data-stu-id="e7401-134">Boolean Type Does Not Convert to Numeric Type Accurately</span></span>  
 <span data-ttu-id="e7401-135">[Boolean — typ danych](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) wartości nie są przechowywane jako liczby i przechowywane wartości nie są przeznaczone do równoważne cyfry.</span><span class="sxs-lookup"><span data-stu-id="e7401-135">[Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="e7401-136">Zgodność z wcześniejszymi wersjami [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zawiera słowa kluczowe konwersji ([CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`i tak dalej) umożliwia konwersję pomiędzy `Boolean` typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="e7401-136">For compatibility with earlier versions, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] provides conversion keywords ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md), `CBool`, `CInt`, and so on) to convert between `Boolean` and numeric types.</span></span> <span data-ttu-id="e7401-137">Jednak inne języki czasem wykonywania tych konwersji inaczej, tak jak [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] metody.</span><span class="sxs-lookup"><span data-stu-id="e7401-137">However, other languages sometimes perform these conversions differently, as do the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] methods.</span></span>  
  
 <span data-ttu-id="e7401-138">Nigdy nie powinien pisania kodu, który polega na równoważne wartości numerycznych `True` i `False`.</span><span class="sxs-lookup"><span data-stu-id="e7401-138">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="e7401-139">Jeśli to możliwe, należy ograniczyć użycie `Boolean` zmienne do wartości logiczne, dla których są przeznaczone.</span><span class="sxs-lookup"><span data-stu-id="e7401-139">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span> <span data-ttu-id="e7401-140">Jeśli musisz mieszać `Boolean` i wartości liczbowe, upewnij się, że rozumiesz wybranej metody konwersji.</span><span class="sxs-lookup"><span data-stu-id="e7401-140">If you must mix `Boolean` and numeric values, make sure that you understand the conversion method that you select.</span></span>  
  
### <a name="conversion-in-visual-basic"></a><span data-ttu-id="e7401-141">Konwersja w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7401-141">Conversion in Visual Basic</span></span>  
 <span data-ttu-id="e7401-142">Jeśli używasz `CType` lub `CBool` słowa kluczowe konwersji do konwersji liczbowych typów danych do `Boolean`, staje się 0 `False` i stać się wszystkie inne wartości `True`.</span><span class="sxs-lookup"><span data-stu-id="e7401-142">When you use the `CType` or `CBool` conversion keywords to convert numeric data types to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="e7401-143">Podczas konwertowania `Boolean` wartości na typy liczbowe za pomocą słowa kluczowe konwersji, `False` staje się 0 i `True` staje się wartość -1.</span><span class="sxs-lookup"><span data-stu-id="e7401-143">When you convert `Boolean` values to numeric types by using the conversion keywords, `False` becomes 0 and `True` becomes -1.</span></span>  
  
### <a name="conversion-in-the-framework"></a><span data-ttu-id="e7401-144">Konwersja w ramach</span><span class="sxs-lookup"><span data-stu-id="e7401-144">Conversion in the Framework</span></span>  
 <span data-ttu-id="e7401-145"><xref:System.Convert.ToInt32%2A> Metody <xref:System.Convert> klasy w <xref:System> konwertuje przestrzeń nazw `True` do + 1.</span><span class="sxs-lookup"><span data-stu-id="e7401-145">The <xref:System.Convert.ToInt32%2A> method of the <xref:System.Convert> class in the <xref:System> namespace converts `True` to +1.</span></span>  
  
 <span data-ttu-id="e7401-146">Jeśli trzeba przekonwertować `Boolean` wartości na dane typu liczbowego, należy zachować ostrożność o wyborze metody konwersji używasz.</span><span class="sxs-lookup"><span data-stu-id="e7401-146">If you must convert a `Boolean` value to a numeric data type, be careful about which conversion method you use.</span></span>  
  
## <a name="character-literal-generates-compiler-error"></a><span data-ttu-id="e7401-147">Literał znaku generuje błąd kompilatora</span><span class="sxs-lookup"><span data-stu-id="e7401-147">Character Literal Generates Compiler Error</span></span>  
 <span data-ttu-id="e7401-148">W przypadku braku znaków typu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zakłada domyślne typy danych dla literałów.</span><span class="sxs-lookup"><span data-stu-id="e7401-148">In the absence of any type characters, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] assumes default data types for literals.</span></span> <span data-ttu-id="e7401-149">Domyślny typ literał znakowy — ujęta w znaki cudzysłowu (`" "`) — jest `String`.</span><span class="sxs-lookup"><span data-stu-id="e7401-149">The default type for a character literal — enclosed in quotation marks (`" "`) — is `String`.</span></span>  
  
 <span data-ttu-id="e7401-150">`String` — Typ danych nie są rozszerzane [Char — typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="e7401-150">The `String` data type does not widen to the [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md).</span></span> <span data-ttu-id="e7401-151">Oznacza to, że jeśli chcesz przypisać literał do `Char` zmiennej, należy dokonać konwersji zawężającej lub wymusić literał do `Char` typu.</span><span class="sxs-lookup"><span data-stu-id="e7401-151">This means that if you want to assign a literal to a `Char` variable, you must either make a narrowing conversion or force the literal to the `Char` type.</span></span>  

|<span data-ttu-id="e7401-152">Aby utworzyć literał można przypisać do zmiennej lub stała wartość typu Char</span><span class="sxs-lookup"><span data-stu-id="e7401-152">To create a Char literal to assign to a variable or constant</span></span>|
|---|  
|<span data-ttu-id="e7401-153">1.  Deklarowanie zmiennej lub stała jako `Char`.</span><span class="sxs-lookup"><span data-stu-id="e7401-153">1.  Declare the variable or constant as `Char`.</span></span><br /><span data-ttu-id="e7401-154">2.  Należy wpisać wartość znaku w cudzysłowie (`" "`).</span><span class="sxs-lookup"><span data-stu-id="e7401-154">2.  Enclose the character value in quotation marks (`" "`).</span></span><br /><span data-ttu-id="e7401-155">3.  Wykonaj podwójnego cudzysłowu zamykającego znak literalny typu `C` wymusić literał do `Char`.</span><span class="sxs-lookup"><span data-stu-id="e7401-155">3.  Follow the closing double quotation mark with the literal type character `C` to force the literal to `Char`.</span></span> <span data-ttu-id="e7401-156">Jest to konieczne, jeśli sprawdzanie typu przełącznik ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `On`, i jest pożądane w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="e7401-156">This is necessary if the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On`, and it is desirable in any case.</span></span>|  
  
 <span data-ttu-id="e7401-157">W poniższym przykładzie pokazano przypisania nie powiodło się jak pomyślnie literału do `Char` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e7401-157">The following example demonstrates both unsuccessful and successful assignments of a literal to a `Char` variable.</span></span>  
  
 [!code-vb[VbVbalrDataTypes#12](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/troubleshooting-data-types_3.vb)]  
  
 <span data-ttu-id="e7401-158">Istnieje ryzyko za pomocą konwersji zawężającej, ponieważ może zakończyć się niepowodzeniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e7401-158">There is always a risk in using narrowing conversions, because they can fail at run time.</span></span> <span data-ttu-id="e7401-159">Na przykład konwersji `String` do `Char` może zakończyć się niepowodzeniem, jeśli `String` wartość zawiera więcej niż jeden znak.</span><span class="sxs-lookup"><span data-stu-id="e7401-159">For example, a conversion from `String` to `Char` can fail if the `String` value contains more than one character.</span></span> <span data-ttu-id="e7401-160">W związku z tym lepiej jest programowania do użycia `C` znaku typu.</span><span class="sxs-lookup"><span data-stu-id="e7401-160">Therefore, it is better programming to use the `C` type character.</span></span>  
  
## <a name="string-conversion-fails-at-run-time"></a><span data-ttu-id="e7401-161">Konwersja ciągu nie powiedzie się w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="e7401-161">String Conversion Fails at Run Time</span></span>  
 <span data-ttu-id="e7401-162">[String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md) uczestniczy w bardzo mało poszerzanie konwersji.</span><span class="sxs-lookup"><span data-stu-id="e7401-162">The [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) participates in very few widening conversions.</span></span> <span data-ttu-id="e7401-163">`String`rozszerzenie tylko do samego siebie i `Object`i tylko `Char` i `Char()` ( `Char` tablicy) rozszerzane `String`.</span><span class="sxs-lookup"><span data-stu-id="e7401-163">`String` widens only to itself and `Object`, and only `Char` and `Char()` (a `Char` array) widen to `String`.</span></span> <span data-ttu-id="e7401-164">Jest to spowodowane `String` zmiennych i stałych może zawierać wartości, które nie mogą zawierać inne typy danych.</span><span class="sxs-lookup"><span data-stu-id="e7401-164">This is because `String` variables and constants can contain values that other data types cannot contain.</span></span>  
  
 <span data-ttu-id="e7401-165">Podczas sprawdzania typu przełącznika ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `On`, kompilator nie zezwala na wszystkich niejawnej konwersji zawężającej.</span><span class="sxs-lookup"><span data-stu-id="e7401-165">When the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `On`, the compiler disallows all implicit narrowing conversions.</span></span> <span data-ttu-id="e7401-166">Obejmuje to te obejmujące `String`.</span><span class="sxs-lookup"><span data-stu-id="e7401-166">This includes those involving `String`.</span></span> <span data-ttu-id="e7401-167">Kod można nadal używać słowa kluczowe konwersji takich jak `CStr` i [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md), które bezpośrednio [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] próby konwersji.</span><span class="sxs-lookup"><span data-stu-id="e7401-167">Your code can still use conversion keywords such as `CStr` and [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md), which direct the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] to attempt the conversion.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e7401-168">Błąd zawężanie konwersji jest pomijane w przypadku konwersji z typu elementów w `For Each…Next` kolekcję, aby zmienna sterująca pętli for.</span><span class="sxs-lookup"><span data-stu-id="e7401-168">The narrowing-conversion error is suppressed for conversions from the elements in a `For Each…Next` collection to the loop control variable.</span></span> <span data-ttu-id="e7401-169">Aby uzyskać dodatkowe informacje i przykłady, zobacz sekcję "Zawężanie konwersji" w [For Each... Następna instrukcja](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e7401-169">For more information and examples, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
### <a name="narrowing-conversion-protection"></a><span data-ttu-id="e7401-170">Zawężanie konwersji ochrony</span><span class="sxs-lookup"><span data-stu-id="e7401-170">Narrowing Conversion Protection</span></span>  
 <span data-ttu-id="e7401-171">Zawężanie konwersji wadą jest to, że ich może zakończyć się niepowodzeniem w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e7401-171">The disadvantage of narrowing conversions is that they can fail at run time.</span></span> <span data-ttu-id="e7401-172">Na przykład jeśli `String` zmiennej zawiera coś innego niż "Prawda" lub "Fałsz", nie można przekonwertować na `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e7401-172">For example, if a `String` variable contains anything other than "True" or "False," it cannot be converted to `Boolean`.</span></span> <span data-ttu-id="e7401-173">Jeśli zawiera znaki interpunkcyjne, konwersji do dowolnego typu liczbowego kończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="e7401-173">If it contains punctuation characters, conversion to any numeric type fails.</span></span> <span data-ttu-id="e7401-174">Jeśli nie wiesz, że Twoje `String` zmienna zawsze przechowuje wartości, które może zaakceptować docelowego, nie należy spróbować konwersji.</span><span class="sxs-lookup"><span data-stu-id="e7401-174">Unless you know that your `String` variable always holds values that the destination type can accept, you should not try a conversion.</span></span>  
  
 <span data-ttu-id="e7401-175">Jeśli muszą być konwertowane z `String` na inny typ danych ma ujmij próba konwersji w możliwie najbezpieczniejszy procedura [spróbuj... CATCH... Instrukcji finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e7401-175">If you must convert from `String` to another data type, the safest procedure is to enclose the attempted conversion in the [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span> <span data-ttu-id="e7401-176">Dzięki temu można rozwiązać błąd czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e7401-176">This lets you deal with a run-time failure.</span></span>  
  
### <a name="character-arrays"></a><span data-ttu-id="e7401-177">Tablice znaków</span><span class="sxs-lookup"><span data-stu-id="e7401-177">Character Arrays</span></span>  
 <span data-ttu-id="e7401-178">Pojedynczy `Char` i tablica `Char` elementy zarówno rozszerzane `String`.</span><span class="sxs-lookup"><span data-stu-id="e7401-178">A single `Char` and an array of `Char` elements both widen to `String`.</span></span> <span data-ttu-id="e7401-179">Jednak `String` nie rozszerzane `Char()`.</span><span class="sxs-lookup"><span data-stu-id="e7401-179">However, `String` does not widen to `Char()`.</span></span> <span data-ttu-id="e7401-180">Aby przekonwertować `String` do wartości `Char` tablicy, można użyć <xref:System.String.ToCharArray%2A> metody <xref:System.String?displayProperty=nameWithType> klasy.</span><span class="sxs-lookup"><span data-stu-id="e7401-180">To convert a `String` value to a `Char` array, you can use the <xref:System.String.ToCharArray%2A> method of the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
### <a name="meaningless-values"></a><span data-ttu-id="e7401-181">Znaczenia wartości</span><span class="sxs-lookup"><span data-stu-id="e7401-181">Meaningless Values</span></span>  
 <span data-ttu-id="e7401-182">Ogólnie rzecz biorąc `String` wartości nie są przydatne w przypadku innych typów danych, a konwersja jest wysoce sztuczne i niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="e7401-182">In general, `String` values are not meaningful in other data types, and conversion is highly artificial and dangerous.</span></span> <span data-ttu-id="e7401-183">Jeśli to możliwe, należy ograniczyć użycie `String` zmienne sekwencji znaków, dla których są przeznaczone.</span><span class="sxs-lookup"><span data-stu-id="e7401-183">Whenever possible, you should restrict usage of `String` variables to the character sequences for which they are designed.</span></span> <span data-ttu-id="e7401-184">Nigdy nie powinien pisania kodu, który polega na równoważne wartości w innych typach.</span><span class="sxs-lookup"><span data-stu-id="e7401-184">You should never write code that relies on equivalent values in other types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7401-185">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7401-185">See Also</span></span>  
 [<span data-ttu-id="e7401-186">Typy danych</span><span class="sxs-lookup"><span data-stu-id="e7401-186">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="e7401-187">Znaki typu</span><span class="sxs-lookup"><span data-stu-id="e7401-187">Type Characters</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [<span data-ttu-id="e7401-188">Typy wartości i typy referencyjne</span><span class="sxs-lookup"><span data-stu-id="e7401-188">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="e7401-189">Konwersje typów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e7401-189">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="e7401-190">Typy danych</span><span class="sxs-lookup"><span data-stu-id="e7401-190">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="e7401-191">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="e7401-191">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="e7401-192">Skuteczne stosowanie typów danych</span><span class="sxs-lookup"><span data-stu-id="e7401-192">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)