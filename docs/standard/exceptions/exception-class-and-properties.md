---
title: "Właściwości i klasy wyjątków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 253a9846e484aa4e54c3433b0bbc8623519bbb7e
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2017
---
# <a name="exception-class-and-properties"></a><span data-ttu-id="12cf9-102">Właściwości i klasy wyjątków</span><span class="sxs-lookup"><span data-stu-id="12cf9-102">Exception class and properties</span></span>

<span data-ttu-id="12cf9-103"><xref:System.Exception> Klasa jest klasy podstawowej, z której dziedziczy wyjątków.</span><span class="sxs-lookup"><span data-stu-id="12cf9-103">The <xref:System.Exception> class is the base class from which exceptions inherit.</span></span> <span data-ttu-id="12cf9-104">Na przykład <xref:System.InvalidCastException> hierarchii klas jest następujący:</span><span class="sxs-lookup"><span data-stu-id="12cf9-104">For example, the <xref:System.InvalidCastException> class hierarchy is as follows:</span></span>

```
Object
  Exception
    SystemException
       InvalidCastException
```

<span data-ttu-id="12cf9-105"><xref:System.Exception> Klasa ma następujące właściwości ułatwiających opis wyjątku łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="12cf9-105">The <xref:System.Exception> class has the following properties that help make understanding an exception easier.</span></span>

| <span data-ttu-id="12cf9-106">Nazwa właściwości</span><span class="sxs-lookup"><span data-stu-id="12cf9-106">Property Name</span></span> | <span data-ttu-id="12cf9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="12cf9-107">Description</span></span> |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <span data-ttu-id="12cf9-108"><xref:System.Collections.IDictionary> Przechowuje dowolne dane w pary klucz wartość.</span><span class="sxs-lookup"><span data-stu-id="12cf9-108">An <xref:System.Collections.IDictionary> that holds arbitrary data in key-value pairs.</span></span> |
| <xref:System.Exception.HelpLink> | <span data-ttu-id="12cf9-109">Może zawierać adres URL (lub URN) do pliku pomocy, który udostępnia szeroką gamę informacje dotyczące przyczyny wyjątku.</span><span class="sxs-lookup"><span data-stu-id="12cf9-109">Can hold a URL (or URN) to a help file that provides extensive information about the cause of an exception.</span></span> |
| <xref:System.Exception.InnerException> | <span data-ttu-id="12cf9-110">Ta właściwość umożliwia tworzenie i przechowywanie szereg wyjątków podczas obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="12cf9-110">This property can be used to create and preserve a series of exceptions during exception handling.</span></span> <span data-ttu-id="12cf9-111">Aby utworzyć nowy wyjątek, który zawiera wcześniej zgłoszony wyjątków, można użyć go.</span><span class="sxs-lookup"><span data-stu-id="12cf9-111">You can use it to create a new exception that contains previously caught exceptions.</span></span> <span data-ttu-id="12cf9-112">Pierwotny wyjątek mogą być przechwytywane przez drugi wyjątek w <xref:System.Exception.InnerException> właściwości, dzięki czemu kod obsługujący drugi wyjątek, aby sprawdzić dodatkowe informacje.</span><span class="sxs-lookup"><span data-stu-id="12cf9-112">The original exception can be captured by the second exception in the <xref:System.Exception.InnerException> property, allowing code that handles the second exception to examine the additional information.</span></span> <span data-ttu-id="12cf9-113">Na przykład załóżmy, że ma metodę, która odbiera argument, który jest nieprawidłowo sformatowana.</span><span class="sxs-lookup"><span data-stu-id="12cf9-113">For example, suppose you have a method that receives an argument that's improperly formatted.</span></span>  <span data-ttu-id="12cf9-114">Kod próbuje odczytać argument, ale jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="12cf9-114">The code tries to read the argument, but an exception is thrown.</span></span> <span data-ttu-id="12cf9-115">Metoda przechwytuje wyjątek i zgłasza <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="12cf9-115">The method catches the exception and throws a <xref:System.FormatException>.</span></span> <span data-ttu-id="12cf9-116">Aby zwiększyć możliwości wywołującego ustalenie przyczyny, dla której jest zgłaszany wyjątek, czasami jest pożądane dla metody catch wyjątku zgłoszonego przez procedury pomocnika i następnie zgłosić wyjątek więcej świadczy o wystąpieniu tego błędu.</span><span class="sxs-lookup"><span data-stu-id="12cf9-116">To improve the caller's ability to determine the reason an exception is thrown, it is sometimes desirable for a method to catch an exception thrown by a helper routine and then throw an exception more indicative of the error that has occurred.</span></span> <span data-ttu-id="12cf9-117">Można utworzyć wyjątek nowych i bardziej zrozumiałe, gdzie pierwotny wyjątek można ustawić odwołania wyjątek wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="12cf9-117">A new and more meaningful exception can be created, where the inner exception reference can be set to the original exception.</span></span> <span data-ttu-id="12cf9-118">Ten wyjątek bardziej zrozumiałej następnie może zostać zgłoszony do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="12cf9-118">This more meaningful exception can then be thrown to the caller.</span></span> <span data-ttu-id="12cf9-119">Należy pamiętać, że dzięki tej funkcji, można utworzyć serii połączonego wyjątków, która kończy się najpierw zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="12cf9-119">Note that with this functionality, you can create a series of linked exceptions that ends with the exception that was thrown first.</span></span> |
| <xref:System.Exception.Message> | <span data-ttu-id="12cf9-120">Zawiera szczegółowe informacje o przyczynie Wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="12cf9-120">Provides details about the cause of an exception.</span></span>
| <xref:System.Exception.Source> | <span data-ttu-id="12cf9-121">Pobiera lub ustawia nazwę aplikacji lub obiekt, który powoduje błąd.</span><span class="sxs-lookup"><span data-stu-id="12cf9-121">Gets or sets the name of the application or the object that causes the error.</span></span> |
| <xref:System.Exception.StackTrace>| <span data-ttu-id="12cf9-122">Zawiera ślad stosu, który może służyć do określenia, w którym wystąpił błąd.</span><span class="sxs-lookup"><span data-stu-id="12cf9-122">Contains a stack trace that can be used to determine where an error occurred.</span></span> <span data-ttu-id="12cf9-123">Ślad stosu obejmuje plik nazwy i program numer wiersza źródła Jeśli informacje o debugowaniu jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="12cf9-123">The stack trace includes the source file name and program line number if debugging information is available.</span></span> |

<span data-ttu-id="12cf9-124">Większość klas, które dziedziczą z <xref:System.Exception> nie implementuje dodatkowych członków lub oferowanie dodatkowych funkcji; dziedziczą po prostu z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="12cf9-124">Most of the classes that inherit from <xref:System.Exception> do not implement additional members or provide additional functionality; they simply inherit from <xref:System.Exception>.</span></span> <span data-ttu-id="12cf9-125">W związku z tym najważniejsze informacje dla wyjątku znajdują się w hierarchii klasy wyjątków, nazwa wyjątku i informacje zawarte w wyjątek.</span><span class="sxs-lookup"><span data-stu-id="12cf9-125">Therefore, the most important information for an exception can be found in the hierarchy of exception classes, the exception name, and the information contained in the exception.</span></span>

<span data-ttu-id="12cf9-126">Zalecamy throw i catch tylko te obiekty, które pochodzą z <xref:System.Exception>, ale może zgłosić dowolnego obiektu, która jest pochodną <xref:System.Object> klasy jako wyjątek.</span><span class="sxs-lookup"><span data-stu-id="12cf9-126">We recommend that you throw and catch only objects that derive from <xref:System.Exception>, but you can throw any object that derives from the <xref:System.Object> class as an exception.</span></span> <span data-ttu-id="12cf9-127">Należy pamiętać, że nie obsługuje wszystkich języków zgłaszanie i przechwytywanie obiektów, które nie pochodzą z <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="12cf9-127">Note that not all languages support throwing and catching objects that do not derive from <xref:System.Exception>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="12cf9-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="12cf9-128">See Also</span></span>  
[<span data-ttu-id="12cf9-129">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="12cf9-129">Exceptions</span></span>](index.md)