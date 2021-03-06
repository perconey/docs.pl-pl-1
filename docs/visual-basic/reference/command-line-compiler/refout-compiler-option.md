---
title: -refout (Visual Basic)
ms.date: 03/16/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6075b92efd1eec9797fca248e97a325bd5df4bb
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="-refout-visual-basic"></a>-refout (Visual Basic)

**- Refout** opcja określa ścieżkę pliku, w którym zestaw odwołania powinny być danymi wyjściowymi.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Składnia

```console
-refout:filepath
```

## <a name="arguments"></a>Argumenty

 `filepath` Ścieżka i nazwa pliku zestawu odwołania. Ogólnie należy w podfolderze podstawowego zestawu. Zalecane Konwencji (używane przez program MSBuild) jest umieszczenie zestawu odwołania w "ref /" podfolderu względem podstawowego zestawu. Wszystkie foldery w `filepath` musi istnieć; kompilator nie je utworzyć. 

## <a name="remarks"></a>Uwagi

Obsługa języka Visual Basic `-refout` przełącznika, począwszy od wersji 15 ustęp 3.

Zestawy referencyjne są tylko metadane zestawy, które zawierają metadanych, ale żaden kod implementacji. Obejmują one informacje o wszystkim poza typy anonimowe typu i element członkowski. Ich treści metody są zamieniane na jeden `throw null` instrukcji. Przyczyna przy użyciu `throw null` treści metody (w przeciwieństwie do treści) jest tak, aby PEVerify można uruchomić i przekazywania (w związku z tym sprawdzanie poprawności kompletności metadanych).

Zestawy referencyjne obejmuje dane poziomu zestawu [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atrybutu. Ten atrybut można określić w źródle (następnie kompilator nie będzie trzeba go syntetyzowania). Z powodu tego atrybutu środowisk uruchomieniowych odmówić załadować zestawów odwołań do wykonania (ale nadal może być załadowany w kontekstu reflection-only). Narzędzia, które odzwierciedlać zestawów konieczne upewnij się, że są ładowane zestawów odwołań jako tylko do odbicia. w przeciwnym razie zwraca środowiska uruchomieniowego <xref:System.BadImageFormatException>.

`-refout` i [ `-refonly` ](refonly-compiler-option.md) wykluczają się wzajemnie.

## <a name="see-also"></a>Zobacz też
[-refonly](refonly-compiler-option.md)   
[Kompilator w wierszu polecenia programu Visual Basic](index.md)  
[Przykłady kompilacji — wiersze poleceń](sample-compilation-command-lines.md)  

