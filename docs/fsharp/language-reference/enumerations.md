---
title: Wyliczenia (F#)
description: "Dowiedz się, jak używać wyliczenia F # zamiast literały aby kod był bardziej czytelny i łatwy w obsłudze."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 9272bf5a-9a9f-4314-9e34-a3248e5244f5
ms.openlocfilehash: de0273900b707c99e6fb1bcc84e5c2b9ef2bc725
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="enumerations"></a>Wyliczenia

*Wyliczenia*, znanej także jako *wyliczenia*,, są typy całkowite, gdy etykiety są przypisane do podzbioru wartości. Można używać ich zamiast literały Aby bardziej czytelny i łatwy w obsłudze kodu.


## <a name="syntax"></a>Składnia

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Uwagi
Wyliczenie wygląda podobne jak w przypadku Unii rozłącznej zawierającego wartości prostego, z wyjątkiem tego, czy można określić wartości. Wartości są zwykle liczb całkowitych, które są liczone od 0 lub 1 lub liczby całkowite będące pozycji z bitowego. Wyliczenie jest przeznaczony do reprezentowania pozycji z bitowego, należy również użyć [flagi](xref:System.FlagsAttribute) atrybutu.

Podstawowy typ wyliczenia zależy od literal, która jest używana, tak, aby na przykład można literały z sufiksem, takich jak `1u`, `2u`i tak dalej dla całkowitą bez znaku (`uint32`) typu.

W przypadku odwoływania się do nazwanych wartości, należy użyć nazwy samego typu wyliczenia jako kwalifikator, czyli `enum-name.value1`, nie tylko `value1`. To zachowanie różni się od rozłączne. Wynika to z faktu wyliczenia mają zawsze [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atrybutu.

Poniższy kod przedstawia deklaracji i korzystania z wyliczenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

Można z łatwością przekształcić wyliczenia z typem podstawowym za pomocą odpowiednich operatora, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

Typy wyliczane może mieć jeden z następujących typów podstawowych: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, i `char`. Typy wyliczeniowe są reprezentowane w programie .NET Framework jako typy, które są dziedziczone z `System.Enum`, który z kolei jest dziedziczona `System.ValueType`. W związku z tym są typy wartości, które znajdują się w stos lub tekście obiektu zawierającego, a żadnej wartości Typ podstawowy jest prawidłową wartością wyliczenia. Jest to znaczące po dopasowania wzorca w wyliczenia wartości, ponieważ musisz podać wzorzec, który przechwytuje wartości bez nazwy.

`enum` Funkcji w bibliotece języka F # może służyć do generowania wartości wyliczenia, nawet wartość inną niż wstępnie zdefiniowane, nazwane wartości. Możesz użyć `enum` działają w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

Wartość domyślna `enum` funkcja działa z typem `int32`. W związku z tym nie można używać z typów wyliczenia, które mają inne typy podstawowe. Zamiast tego należy użyć.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]
    
## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F #](index.md)

[Rzutowanie i konwersje](casting-and-conversions.md)
