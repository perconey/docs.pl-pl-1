---
title: "Zdarzenie &#39; &lt;eventname1&gt;&#39; nie może implementować zdarzenia &#39;&lt; eventname2&gt;&#39; na interfejs &#39;&lt; interfejs&gt;&#39; ponieważ ich typy delegowane &#39;&lt; delegate1&gt;&#39; i &#39;&lt; delegate2&gt;&#39; nie są zgodne"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords: BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0fcbbf8a6e23270e4dcbf9d813c773e1522a92a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a><span data-ttu-id="e7f52-102">Zdarzenie &#39; &lt;eventname1&gt;&#39; nie może implementować zdarzenia &#39;&lt; eventname2&gt;&#39; na interfejs &#39;&lt; interfejs&gt;&#39; ponieważ ich typy delegowane &#39;&lt; delegate1&gt;&#39; i &#39;&lt; delegate2&gt;&#39; nie są zgodne</span><span class="sxs-lookup"><span data-stu-id="e7f52-102">Event &#39;&lt;eventname1&gt;&#39; cannot implement event &#39;&lt;eventname2&gt;&#39; on interface &#39;&lt;interface&gt;&#39; because their delegate types &#39;&lt;delegate1&gt;&#39; and &#39;&lt;delegate2&gt;&#39; do not match</span></span>
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="e7f52-103">nie może implementować zdarzenia, ponieważ typ delegata zdarzenia nie pasuje do typu delegata zdarzenia w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="e7f52-103"> cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="e7f52-104">Ten błąd może wystąpić, gdy zdefiniować wiele zdarzeń w interfejsie, a następnie ponów próbę wykonania wraz z tego samego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e7f52-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="e7f52-105">Zdarzenia można zaimplementować dwa lub więcej zdarzeń tylko wtedy, gdy wszystko jest implementowane zdarzenia są zadeklarowane za pomocą `As` składni i określ ten sam typ delegata.</span><span class="sxs-lookup"><span data-stu-id="e7f52-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="e7f52-106">**Identyfikator błędu:** BC31423</span><span class="sxs-lookup"><span data-stu-id="e7f52-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e7f52-107">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="e7f52-107">To correct this error</span></span>  
  
-   <span data-ttu-id="e7f52-108">Zdarzenia należy wdrożyć osobno.</span><span class="sxs-lookup"><span data-stu-id="e7f52-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="e7f52-109">—lub—</span><span class="sxs-lookup"><span data-stu-id="e7f52-109">—or—</span></span>  
  
-   <span data-ttu-id="e7f52-110">Definiowanie zdarzeń za pomocą interfejsu `As` składni i określ ten sam typ delegata.</span><span class="sxs-lookup"><span data-stu-id="e7f52-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7f52-111">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e7f52-111">See Also</span></span>  
 [<span data-ttu-id="e7f52-112">Event — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e7f52-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="e7f52-113">Delegate — instrukcja</span><span class="sxs-lookup"><span data-stu-id="e7f52-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [<span data-ttu-id="e7f52-114">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="e7f52-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)