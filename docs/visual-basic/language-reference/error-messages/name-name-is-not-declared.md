---
title: Nazwa &#39; &lt;nazwa&gt;&#39; nie jest zadeklarowana
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords: BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a63ae74c7179d71756e2b9b4bf6b41a71ce12a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="name-39ltnamegt39-is-not-declared"></a><span data-ttu-id="dba91-102">Nazwa &#39; &lt;nazwa&gt;&#39; nie jest zadeklarowana</span><span class="sxs-lookup"><span data-stu-id="dba91-102">Name &#39;&lt;name&gt;&#39; is not declared</span></span>
<span data-ttu-id="dba91-103">Oświadczenie odnosi się do elementu programistycznego, ale kompilator nie można odnaleźć elementu o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="dba91-103">A statement refers to a programming element, but the compiler cannot find an element with that exact name.</span></span>  
  
 <span data-ttu-id="dba91-104">**Identyfikator błędu:** BC30451</span><span class="sxs-lookup"><span data-stu-id="dba91-104">**Error ID:** BC30451</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dba91-105">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="dba91-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="dba91-106">Sprawdź pisownię nazwy w instrukcji zawierających odwołania.</span><span class="sxs-lookup"><span data-stu-id="dba91-106">Check the spelling of the name in the referring statement.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="dba91-107">nie uwzględnia wielkości liter, ale inne zmiany w pisowni jest traktowany jako całkowicie inną nazwę.</span><span class="sxs-lookup"><span data-stu-id="dba91-107"> is case-insensitive, but any other variation in the spelling is regarded as a completely different name.</span></span> <span data-ttu-id="dba91-108">Należy pamiętać, że znak podkreślenia (`_`) jest częścią nazwy, a w związku z tym częścią pisowni.</span><span class="sxs-lookup"><span data-stu-id="dba91-108">Note that the underscore (`_`) is part of the name and therefore part of the spelling.</span></span>  
  
2.  <span data-ttu-id="dba91-109">Sprawdź, czy masz operatora dostępu do elementu członkowskiego (`.`) między obiektem i jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="dba91-109">Check that you have the member access operator (`.`) between an object and its member.</span></span> <span data-ttu-id="dba91-110">Na przykład, jeśli masz <xref:System.Windows.Forms.TextBox> formantu o nazwie `TextBox1`, aby uzyskać dostęp do jego <xref:System.Windows.Forms.TextBoxBase.Text%2A> właściwości, należy wpisać `TextBox1.Text`.</span><span class="sxs-lookup"><span data-stu-id="dba91-110">For example, if you have a <xref:System.Windows.Forms.TextBox> control named `TextBox1`, to access its <xref:System.Windows.Forms.TextBoxBase.Text%2A> property you should type `TextBox1.Text`.</span></span> <span data-ttu-id="dba91-111">Jeśli zamiast tego wpisz `TextBox1Text`, utworzono inną nazwę.</span><span class="sxs-lookup"><span data-stu-id="dba91-111">If instead you type `TextBox1Text`, you have created a different name.</span></span>  
  
3.  <span data-ttu-id="dba91-112">Jeśli pisownia jest poprawna oraz składni dostępu do dowolnego obiektu elementu członkowskiego jest poprawny, sprawdź, czy element został zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="dba91-112">If the spelling is correct and the syntax of any object member access is correct, verify that the element has been declared.</span></span> <span data-ttu-id="dba91-113">Aby uzyskać więcej informacji, zobacz [zadeklarowane elementy](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span><span class="sxs-lookup"><span data-stu-id="dba91-113">For more information, see [Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).</span></span>  
  
4.  <span data-ttu-id="dba91-114">Jeśli programowania element został zadeklarowany, sprawdź, czy znajduje się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="dba91-114">If the programming element has been declared, check that it is in scope.</span></span> <span data-ttu-id="dba91-115">W przypadku instrukcji odwołujących się poza obszarem deklarowanie elementu programistycznego, konieczne może być nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="dba91-115">If the referring statement is outside the region declaring the programming element, you might need to qualify the element name.</span></span> <span data-ttu-id="dba91-116">Aby uzyskać więcej informacji, zobacz [zakres w Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="dba91-116">For more information, see [Scope in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba91-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dba91-117">See Also</span></span>  
 [<span data-ttu-id="dba91-118">Deklaracje i stałe — podsumowanie</span><span class="sxs-lookup"><span data-stu-id="dba91-118">Declarations and Constants Summary</span></span>](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [<span data-ttu-id="dba91-119">Visual Basic — konwencje nazewnictwa</span><span class="sxs-lookup"><span data-stu-id="dba91-119">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [<span data-ttu-id="dba91-120">Zadeklarowane nazwy elementów</span><span class="sxs-lookup"><span data-stu-id="dba91-120">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="dba91-121">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="dba91-121">References to Declared Elements</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)