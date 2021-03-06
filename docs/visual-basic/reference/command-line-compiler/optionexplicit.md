---
title: -optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39ad78c82303d3655d5dda9e2286df0a55b8bf3e
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-optionexplicit"></a>-optionexplicit
Powoduje, że kompilator może raportować błędy zmiennych nie jest zadeklarowana, zanim zostaną użyte.  
  
## <a name="syntax"></a>Składnia  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Opcjonalny. Określ `-optionexplicit+` wymagające jawnej deklaracji zmiennych. `-optionexplicit+` Opcja jest ustawieniem domyślnym i jest taki sam jak `-optionexplicit`. `-optionexplicit-` Opcja umożliwia niejawne deklaracji zmiennych.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli plik kodu źródłowego zawiera [instrukcji Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), zastępuje instrukcji `-optionexplicit` Ustawienia kompilatora wiersza polecenia.  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>Aby ustawić - optionexplicit w środowisku IDE programu Visual Studio  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.   
  
2.  Kliknij przycisk **skompilować** kartę.  
  
3.  Zmodyfikuj wartość w **Option Explicit** pole.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje kiedy `-optionexplicit-` jest używany.  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Explicit, instrukcja](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Okno dialogowe Opcje domyślne, projektów, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
