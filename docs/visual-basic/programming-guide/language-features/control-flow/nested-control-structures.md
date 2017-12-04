---
title: "Zagnieżdżone struktury sterujące (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 22adf4086cd494202a540b2ec16310072329b6ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="nested-control-structures-visual-basic"></a><span data-ttu-id="e695d-102">Zagnieżdżone struktury sterujące (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e695d-102">Nested Control Structures (Visual Basic)</span></span>
<span data-ttu-id="e695d-103">Możesz na przykład umieścić instrukcji sterowania wewnątrz innych instrukcji sterowania `If...Then...Else` zablokować w `For...Next` pętli.</span><span class="sxs-lookup"><span data-stu-id="e695d-103">You can place control statements inside other control statements, for example an `If...Then...Else` block within a `For...Next` loop.</span></span> <span data-ttu-id="e695d-104">Instrukcji sterowania umieszczony wewnątrz innego instrukcji sterowania jest określany jako *zagnieżdżonych*.</span><span class="sxs-lookup"><span data-stu-id="e695d-104">A control statement placed inside another control statement is said to be *nested*.</span></span>  
  
## <a name="nesting-levels"></a><span data-ttu-id="e695d-105">Poziomów zagnieżdżenia</span><span class="sxs-lookup"><span data-stu-id="e695d-105">Nesting Levels</span></span>  
 <span data-ttu-id="e695d-106">Kontrolowanie struktury w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] można zagnieżdżać dowolną liczbę poziomów.</span><span class="sxs-lookup"><span data-stu-id="e695d-106">Control structures in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] can be nested to as many levels as you want.</span></span> <span data-ttu-id="e695d-107">Jest powszechną praktyką było odczytywać struktury zagnieżdżone przez wcięcia treści każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="e695d-107">It is common practice to make nested structures more readable by indenting the body of each one.</span></span> <span data-ttu-id="e695d-108">Edytor środowiska (IDE) zintegrowanego rozwoju automatycznie robi to.</span><span class="sxs-lookup"><span data-stu-id="e695d-108">The integrated development environment (IDE) editor automatically does this.</span></span>  
  
 <span data-ttu-id="e695d-109">W poniższym przykładzie procedura `sumRows` dodaje razem dodatnią elementy każdego wiersza w macierzy.</span><span class="sxs-lookup"><span data-stu-id="e695d-109">In the following example, the procedure `sumRows` adds together the positive elements of each row of the matrix.</span></span>  
  
```  
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 <span data-ttu-id="e695d-110">W powyższym przykładzie pierwszy `Next` instrukcji zamyka wewnętrzny `For` pętli oraz za ostatni `Next` instrukcji zamyka zewnętrznego `For` pętli.</span><span class="sxs-lookup"><span data-stu-id="e695d-110">In the preceding example, the first `Next` statement closes the inner `For` loop and the last `Next` statement closes the outer `For` loop.</span></span>  
  
 <span data-ttu-id="e695d-111">Podobnie, w zagnieżdżonych `If` instrukcji `End If` instrukcje dotyczą automatycznie najbliższej przed `If` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e695d-111">Likewise, in nested `If` statements, the `End If` statements automatically apply to the nearest prior `If` statement.</span></span> <span data-ttu-id="e695d-112">Zagnieżdżone `Do` pętle działa w podobny sposób, z najbardziej wewnętrzną funkcją `Loop` instrukcji dopasowania najbardziej wewnętrzną funkcją `Do` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e695d-112">Nested `Do` loops work in a similar fashion, with the innermost `Loop` statement matching the innermost `Do` statement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e695d-113">Dla wielu struktur kontroli po kliknięciu słowem kluczowym wszystkich słów kluczowych w strukturze wyróżniono.</span><span class="sxs-lookup"><span data-stu-id="e695d-113">For many control structures, when you click a keyword, all of the keywords in the structure are highlighted.</span></span> <span data-ttu-id="e695d-114">Na przykład po kliknięciu `If` w `If...Then...Else` konstrukcji, wszystkie wystąpienia `If`, `Then`, `ElseIf`, `Else`, i `End If` są wyróżniane w konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="e695d-114">For instance, when you click `If` in an `If...Then...Else` construction, all instances of `If`, `Then`, `ElseIf`, `Else`, and `End If` in the construction are highlighted.</span></span> <span data-ttu-id="e695d-115">Aby przejść do następnej lub poprzedniej wyróżnione słowa kluczowego, naciśnij kombinację klawiszy CTRL + SHIFT + Strzałka w dół strzałkę lub CTRL + SHIFT + Strzałka w górę, strzałki.</span><span class="sxs-lookup"><span data-stu-id="e695d-115">To move to the next or previous highlighted keyword, press CTRL+SHIFT+DOWN ARROW or CTRL+SHIFT+UP ARROW.</span></span>  
  
## <a name="nesting-different-kinds-of-control-structures"></a><span data-ttu-id="e695d-116">Zagnieżdżania różnego rodzaju struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="e695d-116">Nesting Different Kinds of Control Structures</span></span>  
 <span data-ttu-id="e695d-117">Można zagnieżdżać jednego rodzaju Struktura kontroli w ramach innego rodzaju.</span><span class="sxs-lookup"><span data-stu-id="e695d-117">You can nest one kind of control structure within another kind.</span></span> <span data-ttu-id="e695d-118">W poniższym przykładzie użyto `With` zablokować wewnątrz `For Each` pętli i zagnieżdżone `If` bloki wewnątrz `With` bloku.</span><span class="sxs-lookup"><span data-stu-id="e695d-118">The following example uses a `With` block inside a `For Each` loop and nested `If` blocks inside the `With` block.</span></span>  
  
```  
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a><span data-ttu-id="e695d-119">Nakładające się struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="e695d-119">Overlapping Control Structures</span></span>  
 <span data-ttu-id="e695d-120">Struktury sterujące nie mogą się nakładać.</span><span class="sxs-lookup"><span data-stu-id="e695d-120">You cannot overlap control structures.</span></span> <span data-ttu-id="e695d-121">Oznacza to, wszystkie zagnieżdżone struktury musi być całkowicie zawarty w strukturze najbardziej dalej.</span><span class="sxs-lookup"><span data-stu-id="e695d-121">This means that any nested structure must be completely contained within the next innermost structure.</span></span> <span data-ttu-id="e695d-122">Na przykład następujące rozmieszczenia jest nieprawidłowy ponieważ `For` pętli kończy się przed wewnętrzny `With` kończy bloku.</span><span class="sxs-lookup"><span data-stu-id="e695d-122">For example, the following arrangement is invalid because the `For` loop terminates before the inner `With` block terminates.</span></span>  
  
 <span data-ttu-id="e695d-123">![Graficzny diagram nieprawidłowego zagnieżdżenia](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span><span class="sxs-lookup"><span data-stu-id="e695d-123">![Graphic diagram of invalid nesting](../../../../visual-basic/programming-guide/language-features/control-flow/media/nestexampleinvalid.gif "NestExampleInvalid")</span></span>  
<span data-ttu-id="e695d-124">Nieprawidłowy zagnieżdżanie do i z struktury</span><span class="sxs-lookup"><span data-stu-id="e695d-124">Invalid nesting of For and With structures</span></span>  
  
 <span data-ttu-id="e695d-125">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora wykrywa takiej kontroli nakładające się struktury i sygnalizuje błąd kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e695d-125">The [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler detects such overlapping control structures and signals a compile-time error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e695d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e695d-126">See Also</span></span>  
 [<span data-ttu-id="e695d-127">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="e695d-127">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="e695d-128">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="e695d-128">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="e695d-129">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="e695d-129">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="e695d-130">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="e695d-130">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)