---
title: "Porady: definiowanie właściwości abstrakcyjnych (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cd8a42c1040180c19bc58627ab0c6a21ace77773
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Porady: definiowanie właściwości abstrakcyjnych (Przewodnik programowania w języku C#)
Poniższy przykład przedstawia sposób definiowania [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md) właściwości. Deklaracja właściwości abstrakcyjne nie dostarcza implementację metody dostępu właściwości — deklaruje obsługuje właściwości klasy, ale pozostawia implementacji metody dostępu dla klasy pochodnej. W poniższym przykładzie pokazano sposób implementacji właściwości abstrakcyjne dziedziczona z klasy podstawowej.  
  
 W tym przykładzie składa się z trzech plików, z których każdy jest kompilowany indywidualnie i jego Wynikowy zestaw odwołuje się do niego następnej kompilacji:  
  
-   abstractshape.CS: `Shape` klasę, która zawiera abstrakcyjnego `Area` właściwości.  
  
-   Shapes.CS: podklasy `Shape` klasy.  
  
-   shapetest.CS: program test, aby wyświetlić obszary niektórych `Shape`-pochodnych obiektów.  
  
 Aby skompilować w przykładzie, użyj następującego polecenia:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Spowoduje to utworzenie shapetest.exe pliku wykonywalnego.  
  
## <a name="example"></a>Przykład  
 Ten plik deklaruje `Shape` klasę, która zawiera `Area` właściwość typu `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   Modyfikatory we właściwości są umieszczane w deklaracji właściwości samej siebie. Na przykład:  
  
    ```  
    public abstract double Area  
    ```  
  
-   Gdy deklarowanie właściwości abstrakcyjnych (takich jak `Area` w tym przykładzie), możesz po prostu wskazują, jakie metody dostępu właściwości są dostępne, ale nie ich wdrażania. W tym przykładzie, tylko [uzyskać](../../../csharp/language-reference/keywords/get.md) metody dostępu jest dostępna, więc właściwość jest tylko do odczytu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia trzy podklasy `Shape` i jak zastąpienie `Area` właściwości do własnej implementacji.  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia program test, który tworzy szereg `Shape`-pochodnych obiektów i drukuje ich obszarów.  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Klasy abstrakcyjne i zapieczętowane oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)
