---
title: /debug (Visual Basic)
ms.date: 03/10/2018
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7430a3ac85a86ed5528af9ea830da530208749eb
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="-debug-visual-basic"></a>-debug (Visual Basic)
Umożliwia kompilatorowi generowanie informacji o debugowaniu i umieść go w plikach wyjściowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Termin|Definicja|  
|---|---|  
|`+` &#124; `-`|Opcjonalny. Określanie `+` lub `/debug` powoduje, że kompilator generuje informacje o debugowaniu i umieść go w pliku PDB. Określanie `-` ma ten sam efekt co nieokreślenie `/debug`.|  
|`full` &#124; `pdbonly`|Opcjonalny. Określa typ informacji dotyczących debugowania generowanych przez kompilator. Jeśli nie określisz `/debug:pdbonly`, wartość domyślna to `full`, co umożliwia dołączanie debugera do działającego programu. `pdbonly` Argument umożliwia debugowanie kodu źródłowego, gdy program jest uruchomiony w debugerze, ale tylko wtedy, gdy jest uruchomiony program jest podłączony do debugera wyświetla kod języka zestawu.|  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja służy do tworzenia kompilacji do debugowania. Jeśli nie określisz `/debug`, `/debug+`, lub `/debug:full`, użytkownik będzie mógł debugowania pliku wyjściowego z programu.  
  
 Domyślnie, informacje o debugowaniu nie emitowanego (`/debug-`). Aby Emituj informacje debugowania, określ `/debug` lub `/debug+`.  
  
 Aby uzyskać informacje na temat konfigurowania wydajność debugowania aplikacji, zobacz [ułatwiając obraz do debugowania](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
|Aby ustawić — debugowania w programie Visual Studio zintegrowane środowisko programistyczne|  
|---|  
|1.  Z projektem wybranym **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**. <br />2.  Kliknij przycisk **skompilować** kartę.<br />3.  Kliknij przycisk **zaawansowane opcje kompilacji**.<br />4.  Zmodyfikuj wartość w **Generuj informacje o debugowaniu** pole.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład umieszcza informacje o debugowaniu w pliku wyjściowym `App.exe`.  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
