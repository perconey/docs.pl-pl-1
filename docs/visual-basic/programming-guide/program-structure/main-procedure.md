---
title: "Procedura główna w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90550ce3e62e4afbc94e2d383fa73db7178633d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="3acb4-102">Procedura główna w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3acb4-102">Main Procedure in Visual Basic</span></span>
<span data-ttu-id="3acb4-103">Każda aplikacja Visual Basic musi zawierać wywołuje procedurę `Main`.</span><span class="sxs-lookup"><span data-stu-id="3acb4-103">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="3acb4-104">Ta procedura służy jako początkowy punkt i ogólnej kontroli aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3acb4-104">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="3acb4-105">Wywołania .NET Framework z `Main` procedury po załadowaniu aplikacji i jest gotowy do przekazania do formantu.</span><span class="sxs-lookup"><span data-stu-id="3acb4-105">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="3acb4-106">Jeśli tworzysz aplikacji formularzy systemu Windows, należy napisać `Main` procedury dla aplikacji działających na ich własnych.</span><span class="sxs-lookup"><span data-stu-id="3acb4-106">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>  
  
 <span data-ttu-id="3acb4-107">`Main`zawiera kod, który jest uruchamiany pierwszy.</span><span class="sxs-lookup"><span data-stu-id="3acb4-107">`Main` contains the code that runs first.</span></span> <span data-ttu-id="3acb4-108">W `Main`, można określić postać, która ma być załadowany najpierw, po uruchomieniu programu, dowiedzieć się, czy kopia aplikacji już działa w systemie, ustanowić zestaw zmiennych dla aplikacji lub otworzyć bazy danych, która wymaga aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3acb4-108">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>  
  
## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="3acb4-109">Wymagania dotyczące procedury głównej</span><span class="sxs-lookup"><span data-stu-id="3acb4-109">Requirements for the Main Procedure</span></span>  
 <span data-ttu-id="3acb4-110">Plik, który jest uruchamiany na jego własnej (zwykle z rozszerzeniem .exe) musi zawierać `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="3acb4-110">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="3acb4-111">Nie działa w jego własnej biblioteki (na przykład z rozszerzeniem dll) i nie wymaga `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="3acb4-111">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="3acb4-112">Wymagania dla różnych typów projektów można utworzyć są następujące:</span><span class="sxs-lookup"><span data-stu-id="3acb4-112">The requirements for the different types of projects you can create are as follows:</span></span>  
  
-   <span data-ttu-id="3acb4-113">Aplikacje konsoli Uruchom na ich własnych i musisz podać co najmniej jeden `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="3acb4-113">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span> <span data-ttu-id="3acb4-114">.</span><span class="sxs-lookup"><span data-stu-id="3acb4-114">.</span></span>  
  
-   <span data-ttu-id="3acb4-115">Uruchom ich własnych aplikacji formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3acb4-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="3acb4-116">Jednak kompilator Visual Basic automatycznie generuje `Main` procedury w taki aplikacji, a nie trzeba zapisać jeden.</span><span class="sxs-lookup"><span data-stu-id="3acb4-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>  
  
-   <span data-ttu-id="3acb4-117">Biblioteki klas nie wymagają `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="3acb4-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="3acb4-118">Obejmują one biblioteki formantów systemu Windows i biblioteki formantów sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3acb4-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="3acb4-119">Aplikacje sieci Web są wdrażane jako biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="3acb4-119">Web applications are deployed as class libraries.</span></span>  
  
## <a name="declaring-the-main-procedure"></a><span data-ttu-id="3acb4-120">Deklarowanie procedury głównej</span><span class="sxs-lookup"><span data-stu-id="3acb4-120">Declaring the Main Procedure</span></span>  
 <span data-ttu-id="3acb4-121">Istnieją cztery metody, aby zadeklarować `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="3acb4-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="3acb4-122">Lub nie może upłynąć argumentów i lub nie może zwracać wartości.</span><span class="sxs-lookup"><span data-stu-id="3acb4-122">It can take arguments or not, and it can return a value or not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3acb4-123">W przypadku `Main` w klasie, należy użyć `Shared` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3acb4-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="3acb4-124">W module `Main` musi być `Shared`.</span><span class="sxs-lookup"><span data-stu-id="3acb4-124">In a module, `Main` does not need to be `Shared`.</span></span>  
  
-   <span data-ttu-id="3acb4-125">Najprostszym sposobem jest zadeklarować `Sub` procedury, która nie przyjmuje argumentów ani nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="3acb4-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   <span data-ttu-id="3acb4-126">`Main`można także wrócić `Integer` wartość, która korzysta z systemu operacyjnego jako kod zakończenia programu do.</span><span class="sxs-lookup"><span data-stu-id="3acb4-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="3acb4-127">Inne programy można przetestować tego kodu, sprawdzając wartość ERRORLEVEL systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="3acb4-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="3acb4-128">Aby przywrócić kod zakończenia, należy zadeklarować `Main` jako `Function` procedury zamiast `Sub` procedury.</span><span class="sxs-lookup"><span data-stu-id="3acb4-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>  
  
    ```  
    Module mainModule  
        Function Main() As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   <span data-ttu-id="3acb4-129">`Main`możliwe jest również `String` tablic jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="3acb4-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="3acb4-130">Każdy ciąg w tablicy zawiera jeden z argumentów wiersza polecenia używane do wywołania programu.</span><span class="sxs-lookup"><span data-stu-id="3acb4-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="3acb4-131">Można wykonać różne akcje zależnie od ich wartości.</span><span class="sxs-lookup"><span data-stu-id="3acb4-131">You can take different actions depending on their values.</span></span>  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            ' On return, assign appropriate value to returnValue.  
            ' 0 usually means successful completion.  
            MsgBox("The application is terminating with error level " &  
                 CStr(returnValue) & ".")  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
-   <span data-ttu-id="3acb4-132">Można zadeklarować `Main` do zbadania argumenty wiersza polecenia, ale zwraca kod zakończenia w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="3acb4-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
            End If  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3acb4-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3acb4-133">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>  
 <xref:System.Array.Length%2A>  
 <xref:Microsoft.VisualBasic.Information.UBound%2A>  
 [<span data-ttu-id="3acb4-134">Struktura programu w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3acb4-134">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [<span data-ttu-id="3acb4-135">NIB: wersja języka Visual Basic Hello, World</span><span class="sxs-lookup"><span data-stu-id="3acb4-135">NIB: Visual Basic Version of Hello, World</span></span>](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)  
 [<span data-ttu-id="3acb4-136">/ main</span><span class="sxs-lookup"><span data-stu-id="3acb4-136">/main</span></span>](../../../visual-basic/reference/command-line-compiler/main.md)  
 [<span data-ttu-id="3acb4-137">Udostępnione</span><span class="sxs-lookup"><span data-stu-id="3acb4-137">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="3acb4-138">Sub — instrukcja</span><span class="sxs-lookup"><span data-stu-id="3acb4-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="3acb4-139">Function — instrukcja</span><span class="sxs-lookup"><span data-stu-id="3acb4-139">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="3acb4-140">Integer — typ danych</span><span class="sxs-lookup"><span data-stu-id="3acb4-140">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="3acb4-141">String — typ danych</span><span class="sxs-lookup"><span data-stu-id="3acb4-141">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)