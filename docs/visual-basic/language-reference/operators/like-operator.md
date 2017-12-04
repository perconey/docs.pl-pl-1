---
title: "Like — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad5729515362bfd52b0c3b401f218a49f569726e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="like-operator-visual-basic"></a><span data-ttu-id="58a0d-102">Like — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58a0d-102">Like Operator (Visual Basic)</span></span>
<span data-ttu-id="58a0d-103">Porównuje ciąg do wzorca.</span><span class="sxs-lookup"><span data-stu-id="58a0d-103">Compares a string against a pattern.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58a0d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58a0d-104">Syntax</span></span>  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="58a0d-105">Części</span><span class="sxs-lookup"><span data-stu-id="58a0d-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="58a0d-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="58a0d-106">Required.</span></span> <span data-ttu-id="58a0d-107">Wszelkie `Boolean` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="58a0d-107">Any `Boolean` variable.</span></span> <span data-ttu-id="58a0d-108">Wynik jest `Boolean` wartość wskazującą, czy `string` spełnia `pattern`.</span><span class="sxs-lookup"><span data-stu-id="58a0d-108">The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.</span></span>  
  
 `string`  
 <span data-ttu-id="58a0d-109">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="58a0d-109">Required.</span></span> <span data-ttu-id="58a0d-110">Wszelkie `String` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="58a0d-110">Any `String` expression.</span></span>  
  
 `pattern`  
 <span data-ttu-id="58a0d-111">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="58a0d-111">Required.</span></span> <span data-ttu-id="58a0d-112">Wszelkie `String` wyrażeń zgodnych z konwencjami dopasowywanie do wzorca opisanego w "Uwagi".</span><span class="sxs-lookup"><span data-stu-id="58a0d-112">Any `String` expression conforming to the pattern-matching conventions described in "Remarks."</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58a0d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58a0d-113">Remarks</span></span>  
 <span data-ttu-id="58a0d-114">Jeśli wartość w `string` spełnia wzorzec zawarte w `pattern`, `result` jest `True`.</span><span class="sxs-lookup"><span data-stu-id="58a0d-114">If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`.</span></span> <span data-ttu-id="58a0d-115">Jeśli ciąg nie spełnia wzorzec, `result` jest `False`.</span><span class="sxs-lookup"><span data-stu-id="58a0d-115">If the string does not satisfy the pattern, `result` is `False`.</span></span> <span data-ttu-id="58a0d-116">Jeśli oba `string` i `pattern` są puste ciągi, wynikiem jest `True`.</span><span class="sxs-lookup"><span data-stu-id="58a0d-116">If both `string` and `pattern` are empty strings, the result is `True`.</span></span>  
  
## <a name="comparison-method"></a><span data-ttu-id="58a0d-117">Porównanie — metoda</span><span class="sxs-lookup"><span data-stu-id="58a0d-117">Comparison Method</span></span>  
 <span data-ttu-id="58a0d-118">Zachowanie `Like` zależy od operatora [instrukcji porównanie opcji](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span><span class="sxs-lookup"><span data-stu-id="58a0d-118">The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md).</span></span> <span data-ttu-id="58a0d-119">Domyślną metodę porównywania ciągów dla każdego pliku źródłowego jest `Option Compare Binary`.</span><span class="sxs-lookup"><span data-stu-id="58a0d-119">The default string comparison method for each source file is `Option Compare Binary`.</span></span>  
  
## <a name="pattern-options"></a><span data-ttu-id="58a0d-120">Opcje wzorca</span><span class="sxs-lookup"><span data-stu-id="58a0d-120">Pattern Options</span></span>  
 <span data-ttu-id="58a0d-121">Dopasowanie wzorca wbudowanych zapewnia elastyczne narzędzia do porównywania ciągów znaków.</span><span class="sxs-lookup"><span data-stu-id="58a0d-121">Built-in pattern matching provides a versatile tool for string comparisons.</span></span> <span data-ttu-id="58a0d-122">Dopasowywanie do wzorca funkcje umożliwiają dopasowanie każdego znaku w `string` przed określony znak symbolu wieloznacznego, listę znaku albo zakresu znaków.</span><span class="sxs-lookup"><span data-stu-id="58a0d-122">The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="58a0d-123">W poniższej tabeli przedstawiono znaków dozwolonych w `pattern` i są zgodne.</span><span class="sxs-lookup"><span data-stu-id="58a0d-123">The following table shows the characters allowed in `pattern` and what they match.</span></span>  
  
|<span data-ttu-id="58a0d-124">Znaków`pattern`</span><span class="sxs-lookup"><span data-stu-id="58a0d-124">Characters in `pattern`</span></span>|<span data-ttu-id="58a0d-125">Dopasowania w`string`</span><span class="sxs-lookup"><span data-stu-id="58a0d-125">Matches in `string`</span></span>|  
|-----------------------------|-------------------------|  
|`?`|<span data-ttu-id="58a0d-126">Dowolny pojedynczy znak</span><span class="sxs-lookup"><span data-stu-id="58a0d-126">Any single character</span></span>|  
|`*`|<span data-ttu-id="58a0d-127">Zero lub więcej znaków</span><span class="sxs-lookup"><span data-stu-id="58a0d-127">Zero or more characters</span></span>|  
|`#`|<span data-ttu-id="58a0d-128">Dowolna cyfra (0 – 9)</span><span class="sxs-lookup"><span data-stu-id="58a0d-128">Any single digit (0–9)</span></span>|  
|`[charlist]`|<span data-ttu-id="58a0d-129">Dowolny pojedynczy znak`charlist`</span><span class="sxs-lookup"><span data-stu-id="58a0d-129">Any single character in `charlist`</span></span>|  
|`[!charlist]`|<span data-ttu-id="58a0d-130">Dowolny pojedynczy znak nie`charlist`</span><span class="sxs-lookup"><span data-stu-id="58a0d-130">Any single character not in `charlist`</span></span>|  
  
## <a name="character-lists"></a><span data-ttu-id="58a0d-131">Znak list</span><span class="sxs-lookup"><span data-stu-id="58a0d-131">Character Lists</span></span>  
 <span data-ttu-id="58a0d-132">Grupy co najmniej jeden znak (`charlist`) w nawiasach (`[ ]`) może służyć do dopasowuje dowolny pojedynczy znak w `string` i może zawierać kod prawie każdego znaku, w tym cyfr.</span><span class="sxs-lookup"><span data-stu-id="58a0d-132">A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.</span></span>  
  
 <span data-ttu-id="58a0d-133">Wykrzyknika (`!`) na początku `charlist` oznacza, że zgodność ma miejsce, jeśli dowolny znak z wyjątkiem znaków `charlist` znajduje się w `string`.</span><span class="sxs-lookup"><span data-stu-id="58a0d-133">An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`.</span></span> <span data-ttu-id="58a0d-134">W przypadku poza nawiasy wykrzyknika wykrzyknikami.</span><span class="sxs-lookup"><span data-stu-id="58a0d-134">When used outside brackets, the exclamation point matches itself.</span></span>  
  
## <a name="special-characters"></a><span data-ttu-id="58a0d-135">Znaki specjalne</span><span class="sxs-lookup"><span data-stu-id="58a0d-135">Special Characters</span></span>  
 <span data-ttu-id="58a0d-136">Aby dopasować lewego nawiasu znaki specjalne (`[`), znak zapytania (`?`), znak (`#`) i gwiazdki (`*`), ujmij ją w nawiasach kwadratowych.</span><span class="sxs-lookup"><span data-stu-id="58a0d-136">To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets.</span></span> <span data-ttu-id="58a0d-137">Prawy nawias (`]`) nie można używać wewnątrz grupy bezpośrednio, ale może być używana poza grupą jako znak indywidualnych.</span><span class="sxs-lookup"><span data-stu-id="58a0d-137">The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.</span></span>  
  
 <span data-ttu-id="58a0d-138">Sekwencja znaków `[]` jest traktowana jako ciąg o zerowej długości (`""`).</span><span class="sxs-lookup"><span data-stu-id="58a0d-138">The character sequence `[]` is considered a zero-length string (`""`).</span></span> <span data-ttu-id="58a0d-139">Nie można go jednak częścią listy znaków w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="58a0d-139">However, it cannot be part of a character list enclosed in brackets.</span></span> <span data-ttu-id="58a0d-140">Jeśli chcesz sprawdzić, czy pozycja w `string` zawiera jeden grupy znaków lub nie znak na pozycji wszystkich, można użyć `Like` dwa razy.</span><span class="sxs-lookup"><span data-stu-id="58a0d-140">If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice.</span></span> <span data-ttu-id="58a0d-141">Na przykład zobacz [porady: dopasowywanie ciągu do wzorca](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="58a0d-141">For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).</span></span>  
  
## <a name="character-ranges"></a><span data-ttu-id="58a0d-142">Zakres znaków</span><span class="sxs-lookup"><span data-stu-id="58a0d-142">Character Ranges</span></span>  
 <span data-ttu-id="58a0d-143">Za pomocą łącznika (`–`) do oddzielania dolną i górną granicą zakresu, `charlist` można określić zakres znaków.</span><span class="sxs-lookup"><span data-stu-id="58a0d-143">By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters.</span></span> <span data-ttu-id="58a0d-144">Na przykład `[A–Z]` wynikiem dopasowania, jeśli odpowiedni znak umieść w `string` zawiera dowolny znak z zakresu `A`—`Z`, i `[!H–L]` wynikiem dopasowania, jeśli pozycja odpowiedni znak zawiera dowolny znak spoza zakresu `H`—`L`.</span><span class="sxs-lookup"><span data-stu-id="58a0d-144">For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.</span></span>  
  
 <span data-ttu-id="58a0d-145">Podczas określania zakresu znaków muszą występować w kolejności rosnącej, czyli z najniższą najwyższe.</span><span class="sxs-lookup"><span data-stu-id="58a0d-145">When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest.</span></span> <span data-ttu-id="58a0d-146">W związku z tym `[A–Z]` jest prawidłowy wzorzec, ale `[Z–A]` nie jest.</span><span class="sxs-lookup"><span data-stu-id="58a0d-146">Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.</span></span>  
  
### <a name="multiple-character-ranges"></a><span data-ttu-id="58a0d-147">Zakresów wielu znaków</span><span class="sxs-lookup"><span data-stu-id="58a0d-147">Multiple Character Ranges</span></span>  
 <span data-ttu-id="58a0d-148">Aby określić wiele zakresów dla tej samej pozycji znaku, umieść je w nawiasach tego samego bez ograniczników.</span><span class="sxs-lookup"><span data-stu-id="58a0d-148">To specify multiple ranges for the same character position, put them within the same brackets without delimiters.</span></span> <span data-ttu-id="58a0d-149">Na przykład `[A–CX–Z]` wynikiem dopasowania, jeśli odpowiedni znak umieść w `string` zawiera dowolny znak, albo z zakresu `A`—`C` lub zakres `X`—`Z`.</span><span class="sxs-lookup"><span data-stu-id="58a0d-149">For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.</span></span>  
  
### <a name="usage-of-the-hyphen"></a><span data-ttu-id="58a0d-150">Użycie łącznik</span><span class="sxs-lookup"><span data-stu-id="58a0d-150">Usage of the Hyphen</span></span>  
 <span data-ttu-id="58a0d-151">Łącznik (`–`) mogą być wyświetlane na początku (po wykrzyknik, jeśli istnieje) lub na końcu `charlist` bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="58a0d-151">A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself.</span></span> <span data-ttu-id="58a0d-152">W dowolnym miejscu łącznik określa zakres znaków rozdzielone znaki po obu stronach łącznik.</span><span class="sxs-lookup"><span data-stu-id="58a0d-152">In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.</span></span>  
  
## <a name="collating-sequence"></a><span data-ttu-id="58a0d-153">Kolejność sortowania</span><span class="sxs-lookup"><span data-stu-id="58a0d-153">Collating Sequence</span></span>  
 <span data-ttu-id="58a0d-154">Znaczenie określony zakres jest zależna od znak kolejności w czasie wykonywania na podstawie `Option``Compare` i ustawień regionalnych systemu kod działa na.</span><span class="sxs-lookup"><span data-stu-id="58a0d-154">The meaning of a specified range depends on the character ordering at run time, as determined by `Option``Compare` and the locale setting of the system the code is running on.</span></span> <span data-ttu-id="58a0d-155">Z `Option``Compare``Binary`, zakres `[A–E]` odpowiada `A`, `B`, `C`, `D`, i `E`.</span><span class="sxs-lookup"><span data-stu-id="58a0d-155">With `Option``Compare``Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`.</span></span> <span data-ttu-id="58a0d-156">Z `Option``Compare``Text`, `[A–E]` odpowiada `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, i `e`.</span><span class="sxs-lookup"><span data-stu-id="58a0d-156">With `Option``Compare``Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`.</span></span> <span data-ttu-id="58a0d-157">Zakres nie pasuje `Ê` lub `ê` ponieważ znaki akcentowane collate po formami znaki w porządku sortowania.</span><span class="sxs-lookup"><span data-stu-id="58a0d-157">The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.</span></span>  
  
## <a name="digraph-characters"></a><span data-ttu-id="58a0d-158">Dwuznaku znaków</span><span class="sxs-lookup"><span data-stu-id="58a0d-158">Digraph Characters</span></span>  
 <span data-ttu-id="58a0d-159">W przypadku niektórych języków istnieją znaki alfabetyczne, które reprezentują odrębne znaki.</span><span class="sxs-lookup"><span data-stu-id="58a0d-159">In some languages, there are alphabetic characters that represent two separate characters.</span></span> <span data-ttu-id="58a0d-160">Na przykład użyć znaku w różnych językach `æ` reprezentujących znaki `a` i `e` gdy pojawią się one ze sobą.</span><span class="sxs-lookup"><span data-stu-id="58a0d-160">For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together.</span></span> <span data-ttu-id="58a0d-161">`Like` Operator rozpoznaje znak pojedynczego dwuznaku i dwa znaki są równoważne.</span><span class="sxs-lookup"><span data-stu-id="58a0d-161">The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.</span></span>  
  
 <span data-ttu-id="58a0d-162">Gdy w języku korzystającym znak dwuznaku jest określona w ustawieniach regionalnych systemu, wystąpienie dwuznaku jednego znaku w albo `pattern` lub `string` odpowiada równoważne sekwencji dwóch znaków w innym ciągu.</span><span class="sxs-lookup"><span data-stu-id="58a0d-162">When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string.</span></span> <span data-ttu-id="58a0d-163">Podobnie, znaku dwuznaku w `pattern` w nawiasach (przez siebie, na liście lub w zakresie) jest zgodna równoważne sekwencję dwóch znaków w `string`.</span><span class="sxs-lookup"><span data-stu-id="58a0d-163">Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="58a0d-164">Przeciążenie</span><span class="sxs-lookup"><span data-stu-id="58a0d-164">Overloading</span></span>  
 <span data-ttu-id="58a0d-165">`Like` Operator może być *przeciążony*, co oznacza, że klasy lub struktury ponownie zdefiniować jego zachowanie, gdy argument operacji ma typ tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="58a0d-165">The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="58a0d-166">Jeśli kod używa tego operatora dla klasy lub struktury, upewnij się, że rozumiesz ponownie zdefiniowany zachowania.</span><span class="sxs-lookup"><span data-stu-id="58a0d-166">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="58a0d-167">Aby uzyskać więcej informacji, zobacz [procedury operatorów](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="58a0d-167">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58a0d-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="58a0d-168">Example</span></span>  
 <span data-ttu-id="58a0d-169">W tym przykładzie użyto `Like` operator należy porównywać ciągi do różnych wzorców.</span><span class="sxs-lookup"><span data-stu-id="58a0d-169">This example uses the `Like` operator to compare strings to various patterns.</span></span> <span data-ttu-id="58a0d-170">Wyniki są kierowane do `Boolean` zmiennej wskazującą, czy każdy ciąg spełnia wzorzec.</span><span class="sxs-lookup"><span data-stu-id="58a0d-170">The results go into a `Boolean` variable indicating whether each string satisfies the pattern.</span></span>  
  
 [!code-vb[VbVbalrOperators#30](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/like-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="58a0d-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58a0d-171">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>  
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>  
 [<span data-ttu-id="58a0d-172">Operatory porównania</span><span class="sxs-lookup"><span data-stu-id="58a0d-172">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [<span data-ttu-id="58a0d-173">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58a0d-173">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="58a0d-174">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="58a0d-174">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="58a0d-175">Option Compare — instrukcja</span><span class="sxs-lookup"><span data-stu-id="58a0d-175">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="58a0d-176">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="58a0d-176">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [<span data-ttu-id="58a0d-177">Porady: dopasowywanie ciągu do wzorca</span><span class="sxs-lookup"><span data-stu-id="58a0d-177">How to: Match a String against a Pattern</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)