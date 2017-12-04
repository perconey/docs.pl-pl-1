---
title: "Porady: uruchamianie przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f814ff82-fe2b-4614-aebb-b768c3e61179
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3467b9319a883445d95978e0c167a5552211afe
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-run-a-workflow"></a><span data-ttu-id="8b476-102">Porady: uruchamianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8b476-102">How to: Run a Workflow</span></span>
<span data-ttu-id="8b476-103">W tym temacie jest to kontynuacja Samouczek Windows Workflow Foundation wprowadzenie oraz opisano, jak utworzyć hosta przepływów pracy i Uruchom przepływ pracy określone w poprzedniej [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="8b476-103">This topic is a continuation of the Windows Workflow Foundation Getting Started tutorial and discusses how to create a workflow host and run the workflow defined in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b476-104">Każdego tematu w samouczku wprowadzenie zależy od poprzednich tematów.</span><span class="sxs-lookup"><span data-stu-id="8b476-104">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="8b476-105">Do ukończenia tego tematu, należy najpierw wykonać [jak: utworzyć działanie](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) i [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8b476-105">To complete this topic you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) and [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b476-106">Aby pobrać ukończoną wersję tego samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="8b476-106">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
### <a name="to-create-the-workflow-host-project"></a><span data-ttu-id="8b476-107">Aby utworzyć projekt hosta przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8b476-107">To create the workflow host project</span></span>  
  
1.  <span data-ttu-id="8b476-108">Otwórz rozwiązanie z poprzedniej [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tematu przy użyciu [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8b476-108">Open the solution from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic by using [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="8b476-109">Kliknij prawym przyciskiem myszy **WF45GettingStartedTutorial** rozwiązania **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="8b476-109">Right-click the **WF45GettingStartedTutorial** solution in **Solution Explorer** and select **Add**, **New Project**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="8b476-110">Jeśli **Eksploratora rozwiązań** nie zostanie wyświetlone okno, wybierz **Eksploratora rozwiązań** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="8b476-110">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="8b476-111">W **zainstalowana** węzła, wybierz opcję **Visual C#**, **przepływu pracy** (lub **Visual Basic**, **przepływu pracy**).</span><span class="sxs-lookup"><span data-stu-id="8b476-111">In the **Installed** node, select **Visual C#**, **Workflow** (or **Visual Basic**, **Workflow**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8b476-112">W zależności od tego, jaki język programowania jest skonfigurowany jako podstawowy język w programie Visual Studio, **Visual C#** lub **Visual Basic** węzeł może być w obszarze **inne języki** w węźle **zainstalowana** węzła.</span><span class="sxs-lookup"><span data-stu-id="8b476-112">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="8b476-113">Upewnij się, że **.NET Framework 4.5** jest zaznaczony na liście rozwijanej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b476-113">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="8b476-114">Wybierz **Aplikacja konsoli przepływu pracy** z **przepływu pracy** listy.</span><span class="sxs-lookup"><span data-stu-id="8b476-114">Select **Workflow Console Application** from the **Workflow** list.</span></span> <span data-ttu-id="8b476-115">Typ `NumberGuessWorkflowHost` do **nazwa** polu i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="8b476-115">Type `NumberGuessWorkflowHost` into the **Name** box and click **OK**.</span></span> <span data-ttu-id="8b476-116">Spowoduje to utworzenie aplikacji przepływu pracy starter z hostingu Obsługa podstawowy przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="8b476-116">This creates a starter workflow application with basic workflow hosting support.</span></span> <span data-ttu-id="8b476-117">Ten kod obsługi podstawowych został zmodyfikowany i używane do uruchamiania aplikacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8b476-117">This basic hosting code is modified and used to run the workflow application.</span></span>  
  
4.  <span data-ttu-id="8b476-118">Kliknij prawym przyciskiem myszy nowo dodanego **NumberGuessWorkflowHost** projektu w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="8b476-118">Right-click the newly added **NumberGuessWorkflowHost** project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="8b476-119">Wybierz **rozwiązania** z **Dodaj odwołanie** listy, zaznacz pole wyboru obok **NumberGuessWorkflowActivities**, a następnie kliknij przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="8b476-119">Select **Solution** from the **Add Reference** list, check the checkbox beside **NumberGuessWorkflowActivities**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="8b476-120">Kliknij prawym przyciskiem myszy **Workflow1.xaml** w **Eksploratora rozwiązań** i wybierz polecenie **usunąć**.</span><span class="sxs-lookup"><span data-stu-id="8b476-120">Right-click **Workflow1.xaml** in **Solution Explorer** and choose **Delete**.</span></span> <span data-ttu-id="8b476-121">Kliknij przycisk **OK** o potwierdzenie.</span><span class="sxs-lookup"><span data-stu-id="8b476-121">Click **OK** to confirm.</span></span>  
  
### <a name="to-modify-the-workflow-hosting-code"></a><span data-ttu-id="8b476-122">Aby zmodyfikować kod obsługującym przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="8b476-122">To modify the workflow hosting code</span></span>  
  
1.  <span data-ttu-id="8b476-123">Kliknij dwukrotnie **Program.cs** lub **Module1.vb** w **Eksploratora rozwiązań** Aby wyświetlić kod.</span><span class="sxs-lookup"><span data-stu-id="8b476-123">Double-click **Program.cs** or **Module1.vb** in **Solution Explorer** to display the code.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="8b476-124">Jeśli **Eksploratora rozwiązań** nie zostanie wyświetlone okno, wybierz **Eksploratora rozwiązań** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="8b476-124">If the **Solution Explorer** window is not displayed, select **Solution Explorer** from the **View** menu.</span></span>  
  
     <span data-ttu-id="8b476-125">Ponieważ ten projekt został utworzony przy użyciu **Aplikacja konsoli przepływu pracy** szablonu, **Program.cs** lub **Module1.vb** zawiera następujące hosting podstawowy przepływ pracy Kod.</span><span class="sxs-lookup"><span data-stu-id="8b476-125">Because this project was created by using the **Workflow Console Application** template, **Program.cs** or **Module1.vb** contains the following basic workflow hosting code.</span></span>  
  
    ```vb  
    ' Create and cache the workflow definition  
    Activity workflow1 = new Workflow1()  
    WorkflowInvoker.Invoke(workflow1)  
    ```  
  
    ```csharp  
    // Create and cache the workflow definition  
    Activity workflow1 = new Workflow1();  
    WorkflowInvoker.Invoke(workflow1);  
    ```  
  
     <span data-ttu-id="8b476-126">To wygenerowany hostingu używa kod <xref:System.Activities.WorkflowInvoker>.</span><span class="sxs-lookup"><span data-stu-id="8b476-126">This generated hosting code uses <xref:System.Activities.WorkflowInvoker>.</span></span> <span data-ttu-id="8b476-127"><xref:System.Activities.WorkflowInvoker>zapewnia prostą metodę do wywoływania przepływu pracy, tak, jakby były wywołanie metody i można używać tylko w przypadku przepływów pracy, które nie korzystają z trwałości.</span><span class="sxs-lookup"><span data-stu-id="8b476-127"><xref:System.Activities.WorkflowInvoker> provides a simple way for invoking a workflow as if it were a method call and can be used only for workflows that do not use persistence.</span></span> <span data-ttu-id="8b476-128"><xref:System.Activities.WorkflowApplication>zapewnia bardziej rozbudowane model do wykonywania przepływów pracy, które zawiera powiadomienia o zdarzenia cyklu życia, kontrola wykonywania wznowienie zakładek i trwałości.</span><span class="sxs-lookup"><span data-stu-id="8b476-128"><xref:System.Activities.WorkflowApplication> provides a richer model for executing workflows that includes notification of life-cycle events, execution control, bookmark resumption, and persistence.</span></span> <span data-ttu-id="8b476-129">W tym przykładzie użyto zakładek i <xref:System.Activities.WorkflowApplication> służy do obsługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8b476-129">This example uses bookmarks and <xref:System.Activities.WorkflowApplication> is used for hosting the workflow.</span></span> <span data-ttu-id="8b476-130">Dodaj następujące `using` lub **importów** instrukcji w górnej części **Program.cs** lub **Module1.vb** poniżej istniejące **przy użyciu** lub **importów** instrukcje.</span><span class="sxs-lookup"><span data-stu-id="8b476-130">Add the following `using` or **Imports** statement at the top of **Program.cs** or **Module1.vb** below the existing **using** or **Imports** statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowActivities  
    Imports System.Threading  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowActivities;  
    using System.Threading;  
    ```  
  
     <span data-ttu-id="8b476-131">Zamień wiersze kodu, które używają <xref:System.Activities.WorkflowInvoker> za pomocą następujących basic <xref:System.Activities.WorkflowApplication> hosting kodu.</span><span class="sxs-lookup"><span data-stu-id="8b476-131">Replace the lines of code that use <xref:System.Activities.WorkflowInvoker> with the following basic <xref:System.Activities.WorkflowApplication> hosting code.</span></span> <span data-ttu-id="8b476-132">Ten przykładowy kod hostowania przedstawiono podstawowe czynności w przypadku obsługi i wywoływania przepływu pracy, ale nie zawiera jeszcze funkcji do pomyślnego uruchomienia przepływu pracy z tego tematu.</span><span class="sxs-lookup"><span data-stu-id="8b476-132">This sample hosting code demonstrates the basic steps for hosting and invoking a workflow, but does not yet contain the functionality to successfully run the workflow from this topic.</span></span> <span data-ttu-id="8b476-133">W poniższych krokach ten podstawowy kod jest modyfikowany, a dodatkowe funkcje zostaną dodane do czasu ukończenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b476-133">In the following steps, this basic code is modified and additional features are added until the application is complete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8b476-134">Zamień `Workflow1` w tych przykładach z `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, zależnie od przepływu pracy zakończona w poprzedniej [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku.</span><span class="sxs-lookup"><span data-stu-id="8b476-134">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="8b476-135">Jeśli nie zastępują `Workflow1` , a następnie po spróbuj i kompilacji lub Uruchom przepływ pracy zostanie wyświetlone błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8b476-135">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#4](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#4)]
     [!code-vb[CFX_WF_GettingStarted#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#4)]  
  
     <span data-ttu-id="8b476-136">Ten kod tworzy <xref:System.Activities.WorkflowApplication>, subskrybuje trzech zdarzeń cyklu życia przepływu pracy, uruchamia przepływ pracy z wywołaniem do <xref:System.Activities.WorkflowApplication.Run%2A>, a następnie czeka na zakończenie przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8b476-136">This code creates a <xref:System.Activities.WorkflowApplication>, subscribes to three workflow life-cycle events, starts the workflow with a call to <xref:System.Activities.WorkflowApplication.Run%2A>, and then waits for the workflow to complete.</span></span> <span data-ttu-id="8b476-137">Po zakończeniu przepływu pracy, <xref:System.Threading.AutoResetEvent> jest ustawiony, a host zakończeniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8b476-137">When the workflow completes, the <xref:System.Threading.AutoResetEvent> is set and the host application completes.</span></span>  
  
### <a name="to-set-input-arguments-of-a-workflow"></a><span data-ttu-id="8b476-138">Aby ustawić argumenty wejściowe przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8b476-138">To set input arguments of a workflow</span></span>  
  
1.  <span data-ttu-id="8b476-139">Dodaj następującą instrukcję w górnej części **Program.cs** lub **Module1.vb** poniżej istniejące `using` lub `Imports` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="8b476-139">Add the following statement at the top of **Program.cs** or **Module1.vb** below the existing `using` or `Imports` statements.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#5](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#5)]
     [!code-vb[CFX_WF_GettingStarted#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#5)]  
  
2.  <span data-ttu-id="8b476-140">Zastąp wiersz kodu, która tworzy nowy <xref:System.Activities.WorkflowApplication> następującym kodem, które tworzy i przekazuje słownika parametry do przepływu pracy podczas jego tworzenia.</span><span class="sxs-lookup"><span data-stu-id="8b476-140">Replace the line of code that creates the new <xref:System.Activities.WorkflowApplication> with the following code that creates and passes a dictionary of parameters to the workflow when it is created.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8b476-141">Zamień `Workflow1` w tych przykładach z `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, zależnie od przepływu pracy zakończona w poprzedniej [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku.</span><span class="sxs-lookup"><span data-stu-id="8b476-141">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="8b476-142">Jeśli nie zastępują `Workflow1` , a następnie po spróbuj i kompilacji lub Uruchom przepływ pracy zostanie wyświetlone błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8b476-142">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     <span data-ttu-id="8b476-143">Ten słownik zawiera jeden element z kluczem `MaxNumber`.</span><span class="sxs-lookup"><span data-stu-id="8b476-143">This dictionary contains one element with a key of `MaxNumber`.</span></span> <span data-ttu-id="8b476-144">Klucze w słowniku wejściowe odpowiadają wejściowych argumentów działania głównego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8b476-144">Keys in the input dictionary correspond to input arguments on the root activity of the workflow.</span></span> <span data-ttu-id="8b476-145">`MaxNumber`jest używany przez przepływ pracy do określenia górna granica losowo generowany numer.</span><span class="sxs-lookup"><span data-stu-id="8b476-145">`MaxNumber` is used by the workflow to determine the upper bound for the randomly generated number.</span></span>  
  
### <a name="to-retrieve-output-arguments-of-a-workflow"></a><span data-ttu-id="8b476-146">Aby pobrać dane wyjściowe argumenty przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8b476-146">To retrieve output arguments of a workflow</span></span>  
  
1.  <span data-ttu-id="8b476-147">Modyfikowanie <xref:System.Activities.WorkflowApplication.Completed%2A> programu obsługi pobierania i wyświetlania liczba włącza używany przez przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="8b476-147">Modify the <xref:System.Activities.WorkflowApplication.Completed%2A> handler to retrieve and display the number of turns used by the workflow.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#7](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#7)]
     [!code-vb[CFX_WF_GettingStarted#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#7)]  
  
### <a name="to-resume-a-bookmark"></a><span data-ttu-id="8b476-148">Aby wznowić zakładki</span><span class="sxs-lookup"><span data-stu-id="8b476-148">To resume a bookmark</span></span>  
  
1.  <span data-ttu-id="8b476-149">Dodaj następujący kod w górnej części `Main` metody zaraz po istniejącej <xref:System.Threading.AutoResetEvent> deklaracji.</span><span class="sxs-lookup"><span data-stu-id="8b476-149">Add the following code at the top of the `Main` method just after the existing <xref:System.Threading.AutoResetEvent> declaration.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#8](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#8)]
     [!code-vb[CFX_WF_GettingStarted#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#8)]  
  
2.  <span data-ttu-id="8b476-150">Dodaj następujące <xref:System.Activities.WorkflowApplication.Idle%2A> obsługi poniżej istniejących obsługi cyklu życia trzy przepływu pracy w w `Main`.</span><span class="sxs-lookup"><span data-stu-id="8b476-150">Add the following <xref:System.Activities.WorkflowApplication.Idle%2A> handler just below the existing three workflow life-cycle handlers in `Main`.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#9](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#9)]
     [!code-vb[CFX_WF_GettingStarted#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#9)]  
  
     <span data-ttu-id="8b476-151">Zawsze przepływu pracy, staje się bezczynności oczekiwanie na następny dopasowanie, ten program obsługi jest nazywany i `idleAction` <xref:System.Threading.AutoResetEvent> jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="8b476-151">Each time the workflow becomes idle waiting for the next guess, this handler is called and the `idleAction` <xref:System.Threading.AutoResetEvent> is set.</span></span> <span data-ttu-id="8b476-152">Kod w następnym kroku używa `idleEvent` i `syncEvent` czy oczekuje na następny wynik przepływu pracy, czy została ukończona.</span><span class="sxs-lookup"><span data-stu-id="8b476-152">The code in the following step uses `idleEvent` and `syncEvent` to determine whether the workflow is waiting for the next guess or is complete.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8b476-153">W tym przykładzie korzysta z resetowaniem automatycznym zdarzenia w aplikacji hosta <xref:System.Activities.WorkflowApplication.Completed%2A> i <xref:System.Activities.WorkflowApplication.Idle%2A> obsługi synchronizacji aplikacji hosta z postęp przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8b476-153">In this example, the host application uses auto-reset events in the <xref:System.Activities.WorkflowApplication.Completed%2A> and <xref:System.Activities.WorkflowApplication.Idle%2A> handlers to synchronize the host application with the progress of the workflow.</span></span> <span data-ttu-id="8b476-154">Nie jest konieczne zablokować i poczekaj, aż przejdzie w stan bezczynności przed wznowieniem zakładki przepływu pracy, ale w tym przykładzie zdarzenia synchronizacji są wymagane, będzie wówczas traktował hosta, czy przepływ pracy jest pełny lub czy oczekuje na więcej danych wejściowych użytkownika przy użyciu <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="8b476-154">It is not necessary to block and wait for the workflow to become idle before resuming a bookmark, but in this example the synchronization events are required so the host knows whether the workflow is complete or whether it is waiting on more user input by using the <xref:System.Activities.Bookmark>.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="8b476-155">[Zakładki](../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span><span class="sxs-lookup"><span data-stu-id="8b476-155"> [Bookmarks](../../../docs/framework/windows-workflow-foundation/bookmarks.md).</span></span>  
  
3.  <span data-ttu-id="8b476-156">Usuń wywołanie `WaitOne`i Zastąp kod w celu zbierania danych wejściowych od użytkownika i Wznów <xref:System.Activities.Bookmark>.</span><span class="sxs-lookup"><span data-stu-id="8b476-156">Remove the call to `WaitOne`, and replace it with code to gather input from the user and resume the <xref:System.Activities.Bookmark>.</span></span>  
  
     <span data-ttu-id="8b476-157">Usuń następujący wiersz kodu.</span><span class="sxs-lookup"><span data-stu-id="8b476-157">Remove the following line of code.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#10](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/extrasnippets.cs#10)]
     [!code-vb[CFX_WF_GettingStarted#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/extrasnippets.vb#10)]  
  
     <span data-ttu-id="8b476-158">Zastąp go następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8b476-158">Replace it with the following example.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#11](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#11)]
     [!code-vb[CFX_WF_GettingStarted#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#11)]  
  
##  <a name="BKMK_ToRunTheApplication"></a><span data-ttu-id="8b476-159">Aby skompilować i uruchomić aplikację</span><span class="sxs-lookup"><span data-stu-id="8b476-159">To build and run the application</span></span>  
  
1.  <span data-ttu-id="8b476-160">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="8b476-160">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and select **Set as StartUp Project**.</span></span>  
  
2.  <span data-ttu-id="8b476-161">Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="8b476-161">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="8b476-162">Próbuje odgadnąć numer w jak najmniejszej liczby włącza, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="8b476-162">Try to guess the number in as few turns as possible.</span></span>  
  
     <span data-ttu-id="8b476-163">Próby zastosowania jednego z innych stylów przepływu pracy, należy zastąpić `Workflow1` w kodzie, który tworzy <xref:System.Activities.WorkflowApplication> z `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`w oparciu o który chcesz styl przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="8b476-163">To try the application with one of the other styles of workflow, replace `Workflow1` in the code that creates the <xref:System.Activities.WorkflowApplication> with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow style you desire.</span></span>  
  
     [!code-csharp[CFX_WF_GettingStarted#6](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#6)]
     [!code-vb[CFX_WF_GettingStarted#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#6)]  
  
     <span data-ttu-id="8b476-164">Instrukcje dotyczące sposobu dodawania trwałości do przepływu pracy aplikacji, można znaleźć następnego tematu [porady: tworzenie i uruchamianie długiego przepływu pracy systemem](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="8b476-164">For instructions about how to add persistence to a workflow application, see the next topic, [How to: Create and Run a Long Running Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b476-165">Przykład</span><span class="sxs-lookup"><span data-stu-id="8b476-165">Example</span></span>  
 <span data-ttu-id="8b476-166">Poniższy przykład jest kompletny kod dla `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="8b476-166">The following example is the complete code listing for the `Main` method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b476-167">Zamień `Workflow1` w tych przykładach z `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, lub `StateMachineNumberGuessWorkflow`, zależnie od przepływu pracy zakończona w poprzedniej [porady: tworzenie przepływów pracy](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) kroku.</span><span class="sxs-lookup"><span data-stu-id="8b476-167">Please replace `Workflow1` in these examples with `FlowchartNumberGuessWorkflow`, `SequentialNumberGuessWorkflow`, or `StateMachineNumberGuessWorkflow`, depending on which workflow you completed in the previous [How to: Create a Workflow](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md) step.</span></span> <span data-ttu-id="8b476-168">Jeśli nie zastępują `Workflow1` , a następnie po spróbuj i kompilacji lub Uruchom przepływ pracy zostanie wyświetlone błędy kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8b476-168">If you do not replace `Workflow1` then you will get build errors when you try and build or run the workflow.</span></span>  
  
 [!code-csharp[CFX_WF_GettingStarted#12](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_wf_gettingstarted/cs/program.cs#12)]
 [!code-vb[CFX_WF_GettingStarted#12](../../../samples/snippets/visualbasic/VS_Snippets_CFX/cfx_wf_gettingstarted/vb/module1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="8b476-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b476-169">See Also</span></span>  
 <xref:System.Activities.WorkflowApplication>  
 <xref:System.Activities.Bookmark>  
 [<span data-ttu-id="8b476-170">Windows Workflow Foundation programowania</span><span class="sxs-lookup"><span data-stu-id="8b476-170">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)  
 [<span data-ttu-id="8b476-171">Wprowadzenie — samouczek</span><span class="sxs-lookup"><span data-stu-id="8b476-171">Getting Started Tutorial</span></span>](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md)  
 [<span data-ttu-id="8b476-172">Porady: tworzenie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="8b476-172">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 [<span data-ttu-id="8b476-173">Porady: tworzenie i uruchamianie długi uruchamiania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="8b476-173">How to: Create and Run a Long Running Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 [<span data-ttu-id="8b476-174">Trwa oczekiwanie na dane wejściowe w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="8b476-174">Waiting for Input in a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/waiting-for-input-in-a-workflow.md)  
 [<span data-ttu-id="8b476-175">Hosting przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="8b476-175">Hosting Workflows</span></span>](../../../docs/framework/windows-workflow-foundation/hosting-workflows.md)