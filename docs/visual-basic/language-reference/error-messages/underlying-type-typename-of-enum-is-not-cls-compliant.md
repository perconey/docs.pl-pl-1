---
title: "Typ podstawowy &lt;typename&gt; Enum nie jest zgodne ze specyfikacją CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e054f8d992154f66ab1d48a477a7e04900aa5b4d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a>Typ podstawowy &lt;typename&gt; Enum nie jest zgodne ze specyfikacją CLS
Typ danych określony dla tego wyliczenia nie jest częścią [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS). Nie jest to błąd w ramach składnika, ponieważ [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] i [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] obsługuje tego typu danych. Jednak inny składnik napisana ściśle kodu zgodne ze specyfikacją CLS nie może obsługiwać ten typ danych. Takie składnika nie można pomyślnie interakcyjnie składnika.  
  
 Następujące [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] typy danych nie są zgodne ze specyfikacją CLS:  
  
-   [SByte, typ danych](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [UInteger, typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [ULong, typ danych](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [UShort, typ danych](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 Domyślnie ten komunikat jest ostrzeżenie. Aby uzyskać więcej informacji na ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Identyfikator błędu:** BC40032  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
-   Jeśli składnik interfejsy tylko z innymi [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] składniki lub nie nie interfejsu z innymi składnikami, jest konieczne wprowadzanie zmian.  
  
-   Jeśli są relacje ze składnikiem nie napisane dla [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], może być możliwe ustalenie, albo za pomocą odbicia lub z dokumentacji, czy ten typ danych. Jeśli tak, nie jest konieczne wprowadzanie zmian.  
  
-   Jeśli użytkownik są relacje ze składnikiem, który nie obsługuje tego typu danych, należy ją zastąpić najbliższego CLS typu. Na przykład zamiast z `UInteger` można użyć `Integer` Jeśli nie potrzebujesz zakres wartości powyżej 2 147 483 647. Jeśli potrzebujesz rozszerzonej zakresu, można zastąpić `UInteger` z `Long`.  
  
-   Jeśli użytkownik są relacje z obiektami automatyzacji lub COM, należy pamiętać, że niektóre typy szerokości danych innego niż w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Na przykład `uint` jest często 16 bitów w innych środowiskach. Jeśli argument 16-bitowych jest przekazywany do takich składników, Zadeklaruj ją jako `UShort` zamiast `UInteger` w sieci zarządzanej [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kodu.  
  
## <a name="see-also"></a>Zobacz też  
 [Odbicie (Visual Basic)](../../programming-guide/concepts/reflection.md)  
 [Odbicie](../../../framework/reflection-and-codedom/reflection.md)  
 
