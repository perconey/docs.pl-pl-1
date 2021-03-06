---
title: "Wyjątki: try...finally — Wyrażenie (F#)"
description: "Dowiedz się, jak F # \"try... finally\" wyrażenie umożliwia wykonywanie czyszczenia kodu nawet wtedy, gdy blok kodu zgłasza wyjątek."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: af06b20c-8d87-4496-a0aa-6fdfe8b3a786
ms.openlocfilehash: 2e2445c42bf8129ea81beef56cb725ac0e37d202
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-tryfinally-expression"></a>Wyjątki: try...finally — Wyrażenie

`try...finally` Wyrażenie umożliwia wykonywanie czyszczenia kodu nawet wtedy, gdy blok kodu zgłasza wyjątek.


## <a name="syntax"></a>Składnia

```fsharp
try
    expression1
finally
    expression2
```

## <a name="remarks"></a>Uwagi
`try...finally` Wyrażenie może służyć do wykonywania kodu w *wyrażenie2* w powyższej składni niezależnie od tego, czy wyjątek jest generowany podczas wykonywania *wyrażenie1*.

Typ *wyrażenie2* nie wpływa na wartość całego wyrażenia; typ zwracany, gdy występuje wyjątek jest ostatnią wartość *wyrażenie1*. Po wystąpieniu wyjątku, jest zwracana wartość nie i przesyła przepływu sterowania do następnego dopasowania obsługi wyjątków górę stosu wywołań. Jeśli zostanie znaleziony żaden moduł obsługi wyjątku, program zakończy się. Przed wykonywany jest kod obsługi zgodnych lub program zakończy kod w `finally` gałęzi jest wykonywana.

Poniższy kod przedstawia użycie `try...finally` wyrażenia.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5701.fs)]

Poniżej przedstawiono dane wyjściowe do konsoli.

```
Closing stream
Exception handled.
```

Jak widać z danych wyjściowych, strumień został zamknięty przed zewnętrzne wyjątek został obsłużony, a plik `test.txt` zawiera tekst `test1`, co oznacza, że bufory zostały opróżnione i zapisywane na dysku, nawet jeśli wyjątek transferu kontrolowanie do obsługi Wyjątek zewnętrzny.

Należy pamiętać, że `try...with` konstrukcja jest osobnym konstrukcja z `try...finally` utworzenia. W związku z tym jeśli kod wymaga obu `with` bloku i `finally` bloku, trzeba zagnieździć dwóch konstrukcje, jak w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5702.fs)]

W kontekście wyrażenia obliczeń, w tym wyrażeniach sekwencji i asynchroniczne przepływy pracy, **try... finally** wyrażenia może mieć niestandardowej implementacji. Aby uzyskać więcej informacji, zobacz [wyrażenia obliczeń](../computation-expressions.md).


## <a name="see-also"></a>Zobacz też
[Obsługa wyjątków](index.md)

[Wyjątki: `try...with` wyrażenia](the-try-with-expression.md)
