---
title: "Rozwiązywanie problemów związanych z tablicami (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0417ae8d37642a65b14cc81ae9dcf3a3c32d63ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-arrays-visual-basic"></a>Rozwiązywanie problemów związanych z tablicami (Visual Basic)
Ta strona zawiera listę typowych problemów, które mogą wystąpić podczas pracy z tablicami.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Błędy kompilacji deklarowanie i Inicjowanie tablicy  
 Błędy kompilacji mogą wynikać z nieporozumienia zasady deklarowanie, tworzenie i Inicjowanie tablic. Najczęstszymi przyczynami błędów są następujące:  
  
-   Dostarczanie [operatora New](../../../../visual-basic/language-reference/operators/new-operator.md) klauzuli po określeniu długości wymiaru w deklaracji zmiennej tablicy. Poniższe wiersze kodu pokazują nieprawidłowy deklaracje tego typu.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
-   Określanie długości wymiaru więcej niż tablicy nieregularnej tablicy najwyższego poziomu. Następujący wiersz kodu zawiera nieprawidłową deklaracją tego typu.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
-   Pominięcie `New` — słowo kluczowe podczas określania wartości elementu. Następujący wiersz kodu zawiera nieprawidłową deklaracją tego typu.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
-   Dostarczanie `New` klauzuli bez nawiasów klamrowych (`{}`). Poniższe wiersze kodu pokazują nieprawidłowy deklaracje tego typu.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Uzyskiwanie dostępu do tablicy poza zakresem  
 Proces inicjowania tablicy przypisuje górną i dolną granicę każdego wymiaru. Nieprawidłowy indeks lub indeks, dla każdego wymiaru, należy określić co dostępu do elementu tablicy. W przypadku indeksu poniżej dolna lub powyżej górnej granicy, <xref:System.IndexOutOfRangeException> wyników wyjątku. Kompilator nie może wykryć wystąpił błąd, więc wystąpi błąd w czasie wykonywania.  
  
### <a name="determining-bounds"></a>Określanie granic  
 Jeśli inny składnik przekazuje tablicy do kodu, na przykład jako argument procedury nie znasz rozmiaru tablicy lub długości jej wymiarów. Zawsze należy określić górną granicę każdego wymiaru tablicy można było uzyskać dostępu do żadnych elementów. Jeśli tablica został utworzony w sposób inny niż [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `New` klauzuli, dolna granica może być inną niż 0 i jest najbezpieczniejszy określić, że dolna granica również.  
  
### <a name="specifying-the-dimension"></a>Określanie wymiaru  
 Podczas określania granice tablicy wielowymiarowej, należy zadbać określania wymiaru. `dimension` Parametry <xref:System.Array.GetLowerBound%2A> i <xref:System.Array.GetUpperBound%2A> metody są oparte na 0, podczas `Rank` parametry [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Information.LBound%2A> i <xref:Microsoft.VisualBasic.Information.UBound%2A> funkcje są oparte na 1.  
  
## <a name="see-also"></a>Zobacz też  
 [Tablice](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Porady: inicjowanie zmiennej tablicy w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
