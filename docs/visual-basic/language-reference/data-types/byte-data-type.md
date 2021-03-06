---
title: "Byte — Typ danych (Visual Basic)"
ms.date: 01/31/2018
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Byte
helpviewer_keywords:
- Byte data type
- data types [Visual Basic], assigning
ms.assetid: eed44dff-eaee-4937-a89f-444e418e74f6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 02234afc0dc51a2c1338cdd16d1f97765f64b45e
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="byte-data-type-visual-basic"></a>Byte — typ danych (Visual Basic)
Przechowuje 8-bitową (1-bajtowy) liczb całkowitych bez znaku z zakresu wartości od 0 do 255.

## <a name="remarks"></a>Uwagi

Użyj `Byte` — typ danych zawierający dane binarne.  
  
Wartość domyślna `Byte` ma wartość 0.

## <a name="literal-assignments"></a>Przydziały literału

Można zadeklarować i zainicjuj `Byte` zmiennej przez przypisanie dziesiętną literału, literałem szesnastkowe ósemkowe literał lub (począwszy od 2017 Visual Basic) literał binarny. Jeśli całkowity literału jest poza zakresem `Byte` (to znaczy, jeśli jest mniejszy niż <xref:System.Byte.MinValue?displayProperty=nameWithType> lub większa niż <xref:System.Byte.MaxValue?displayProperty=nameWithType>), występuje błąd kompilacji.

W poniższym przykładzie liczb całkowitych równa 201, które są reprezentowane jako dziesiętne szesnastkowych, i literały binarne są niejawnie konwertowane z [całkowitą](integer-data-type.md) do `byte` wartości.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Byte)]

> [!NOTE]
> Użyj prefiksu `&h` lub `&H` do oznaczania literałem szesnastkowe prefiks `&b` lub `&B` do oznaczania literał binarny i prefiks `&o` lub `&O` do oznaczania ósemkowe literału. Literałów dziesiętnych mają nie ma prefiksu.

Począwszy od 2017 Visual Basic, umożliwia także znaku podkreślenia `_`, jako separator cyfr w celu zwiększenia czytelności, jak w poniższym przykładzie pokazano.

[!code-vb[Byte](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ByteS)]  

Począwszy od programu Visual Basic 15,5 cala, umożliwia także znaku podkreślenia (`_`) jako separator wiodące między prefiks i cyfr szesnastkowych, binarne lub ósemkowo. Na przykład:

```vb
Dim number As Byte = &H_6A
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

## <a name="programming-tips"></a>Porady dotyczące programowania

-   **Wartości ujemne.** Ponieważ `Byte` jest typu unsigned, nie może reprezentować wartość ujemną. Jeśli używasz jednoargumentowy minus (`-`) operator na wyrażenie obliczane do typu `Byte`, Visual Basic konwertuje wyrażenie `Short` pierwszy.
  
-   **Konwersje formatu.** Gdy Visual Basic odczytuje i zapisuje pliki lub gdy wywołuje bibliotek DLL, metod i właściwości, może automatycznie przekonwertować między formatami danych. Dane binarne przechowywane w `Byte` zmiennych i tablic są zachowywane w trakcie konwersji taki format. Nie należy używać `String` zmiennej dla danych binarnych, ponieważ jego zawartość może być uszkodzony podczas konwersji między formatami ANSI i Unicode.

-   **Rozszerzanie.** `Byte` Rozszerzenie typu danych do `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, lub `Double`. Oznacza to, że można przekonwertować `Byte` do żadnego z tych typów bez napotkania <xref:System.OverflowException?displayProperty=nameWithType> błędu.
  
-   **Znaki typu.** `Byte`nie ma znak literalny typu ani znak typu identyfikator.

-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.Byte?displayProperty=nameWithType> struktury.

## <a name="example"></a>Przykład

 W poniższym przykładzie `b` jest `Byte` zmiennej. Instrukcje pokazują zakresu zmiennej i stosowania operatory przesunięcia bitowego do niego.

[!code-vb[VbVbalrDataTypes#16](../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/byte-data-type_1.vb)]  

## <a name="see-also"></a>Zobacz też

 <xref:System.Byte?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
