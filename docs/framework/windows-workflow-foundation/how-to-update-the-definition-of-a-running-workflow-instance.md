---
title: "Porady: aktualizowanie definicji działania wystąpienia przepływu pracy"
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
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7cb2191482771647bcc2cd1003229e445c320e1a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a><span data-ttu-id="27cda-102">Porady: aktualizowanie definicji działania wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="27cda-102">How to: Update the Definition of a Running Workflow Instance</span></span>
<span data-ttu-id="27cda-103">Aktualizacja dynamiczna udostępnia mechanizm dla przepływu pracy deweloperami aplikacji, aby zaktualizować wystąpienia przepływu pracy utrwalonych definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="27cda-104">Wymagana zmiana można wdrożyć poprawkę, nowe wymagania lub uwzględnienia nieoczekiwane.</span><span class="sxs-lookup"><span data-stu-id="27cda-104">The required change can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="27cda-105">Ten krok samouczka przedstawiono sposób użycia aktualizacji dynamicznej można zmodyfikować wystąpienia utrwalonego `v1` numer odgadnięcie przepływu pracy do dopasowania nowych funkcji wprowadzonych w [porady: wiele wersji hosta przepływu pracy Side-by-Side ](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="27cda-105">This step in the tutorial demonstrates how to use dynamic update to modify  persisted instances of the `v1` number guessing workflow to match the new functionality introduced in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27cda-106">Aby pobrać wersję zakończone lub wyświetlić Przewodnik wideo samouczka, zobacz [Windows Workflow Foundation (WF45) — Samouczek wprowadzający](http://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="27cda-106">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](http://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="27cda-107">W tym temacie:</span><span class="sxs-lookup"><span data-stu-id="27cda-107">In this topic</span></span>  
  
-   [<span data-ttu-id="27cda-108">Aby utworzyć projekt CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="27cda-108">To create the CreateUpdateMaps project</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)  
  
-   [<span data-ttu-id="27cda-109">Aby zaktualizować StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="27cda-109">To update StateMachineNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)  
  
-   [<span data-ttu-id="27cda-110">Aby zaktualizować FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="27cda-110">To update FlowchartNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)  
  
-   [<span data-ttu-id="27cda-111">Aby zaktualizować SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="27cda-111">To update SequentialNumberGuessWorkflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)  
  
-   [<span data-ttu-id="27cda-112">Aby skompilować i uruchomić aplikację CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="27cda-112">To build and run the CreateUpdateMaps application</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)  
  
-   [<span data-ttu-id="27cda-113">Tworzenie zestawu zaktualizowany przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="27cda-113">To build the updated workflow assembly</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)  
  
-   [<span data-ttu-id="27cda-114">Aby zaktualizować WorkflowVersionMap do nowych wersji</span><span class="sxs-lookup"><span data-stu-id="27cda-114">To update WorkflowVersionMap with the new versions</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)  
  
-   [<span data-ttu-id="27cda-115">Aby zastosować aktualizacje dynamiczne</span><span class="sxs-lookup"><span data-stu-id="27cda-115">To apply the dynamic updates</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)  
  
-   [<span data-ttu-id="27cda-116">Aby uruchomić aplikację zaktualizowane przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="27cda-116">To run the application with the updated workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)  
  
-   [<span data-ttu-id="27cda-117">Aby włączyć uruchamianie poprzednich wersji przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="27cda-117">To enable starting previous versions of the workflows</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)  
  
###  <span data-ttu-id="27cda-118"><a name="BKMK_CreateProject"></a>Aby utworzyć projekt CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="27cda-118"><a name="BKMK_CreateProject"></a> To create the CreateUpdateMaps project</span></span>  
  
1.  <span data-ttu-id="27cda-119">Kliknij prawym przyciskiem myszy **WF45GettingStartedTutorial** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="27cda-119">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="27cda-120">W **zainstalowana** węzła, wybierz opcję **Visual C#**, **Windows** (lub **Visual Basic**, **Windows**).</span><span class="sxs-lookup"><span data-stu-id="27cda-120">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27cda-121">W zależności od tego, jaki język programowania jest skonfigurowany jako podstawowy język w programie Visual Studio, **Visual C#** lub **Visual Basic** węzeł może być w obszarze **inne języki** w węźle **zainstalowana** węzła.</span><span class="sxs-lookup"><span data-stu-id="27cda-121">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="27cda-122">Upewnij się, że **.NET Framework 4.5** jest zaznaczony na liście rozwijanej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27cda-122">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="27cda-123">Wybierz **aplikacji konsoli** z **Windows** listy.</span><span class="sxs-lookup"><span data-stu-id="27cda-123">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="27cda-124">Typ **CreateUpdateMaps** do **nazwa** polu i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="27cda-124">Type **CreateUpdateMaps** into the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="27cda-125">Kliknij prawym przyciskiem myszy **CreateUpdateMaps** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="27cda-125">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="27cda-126">Wybierz **Framework** z **zestawy** w węźle **Dodaj odwołanie** listy.</span><span class="sxs-lookup"><span data-stu-id="27cda-126">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="27cda-127">Typ **elementu System.Activities** do **wyszukiwania zestawów** pole, aby filtrować zestawy i ułatwiają wybierz żądany odwołań.</span><span class="sxs-lookup"><span data-stu-id="27cda-127">Type **System.Activities** into the **Search Assemblies** box to filter the assemblies and make the desired references easier to select.</span></span>  
  
5.  <span data-ttu-id="27cda-128">Zaznacz pole wyboru obok **elementu System.Activities** z **wyniki wyszukiwania** listy.</span><span class="sxs-lookup"><span data-stu-id="27cda-128">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>  
  
6.  <span data-ttu-id="27cda-129">Typ **serializacji** do **wyszukiwania zestawów** polu, a następnie zaznacz pole wyboru obok **System.Runtime.Serialization** z **wyniki wyszukiwania**  listy.</span><span class="sxs-lookup"><span data-stu-id="27cda-129">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>  
  
7.  <span data-ttu-id="27cda-130">Typ **System.Xaml** do **wyszukiwania zestawów** polu, a następnie zaznacz pole wyboru obok **System.Xaml** z **wyniki wyszukiwania** listy.</span><span class="sxs-lookup"><span data-stu-id="27cda-130">Type **System.Xaml** into the **Search Assemblies** box, and check the checkbox beside **System.Xaml** from the **Search Results** list.</span></span>  
  
8.  <span data-ttu-id="27cda-131">Kliknij przycisk **OK** zamknąć **Menedżera odwołań** i dodać odwołań.</span><span class="sxs-lookup"><span data-stu-id="27cda-131">Click **OK** to close **Reference Manager** and add the references.</span></span>  
  
9. <span data-ttu-id="27cda-132">Dodaj następujące `using` (lub `Imports`) instrukcje w górnej części pliku z innym `using` (lub `Imports`) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="27cda-132">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities  
    Imports System.Activities.Statements  
    Imports System.Xaml  
    Imports System.Reflection  
    Imports System.IO  
    Imports System.Activities.XamlIntegration  
    Imports System.Activities.DynamicUpdate  
    Imports System.Runtime.Serialization  
    Imports Microsoft.VisualBasic.Activities  
    ```  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.IO;  
    using System.Xaml;  
    using System.Reflection;  
    using System.Activities.XamlIntegration;  
    using System.Activities.DynamicUpdate;  
    using System.Runtime.Serialization;  
    using Microsoft.CSharp.Activities;  
    ```  
  
10. <span data-ttu-id="27cda-133">Dodaj następujące dwa parametry elementy członkowskie `Program` klasy (lub `Module1`).</span><span class="sxs-lookup"><span data-stu-id="27cda-133">Add the following two string members to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Const mapPath = "..\..\..\PreviousVersions"  
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"  
    ```  
  
    ```csharp  
    const string mapPath = @"..\..\..\PreviousVersions";  
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";  
    ```  
  
11. <span data-ttu-id="27cda-134">Dodaj następujące `StartUpdate` metodę `Program` klasy (lub `Module1`).</span><span class="sxs-lookup"><span data-stu-id="27cda-134">Add the following `StartUpdate` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="27cda-135">Ta metoda Ładuje określony xaml definicji przepływu pracy do `ActivityBuilder`, a następnie wywołuje `DynamicUpdate.PrepareForUpdate`.</span><span class="sxs-lookup"><span data-stu-id="27cda-135">This method loads up the specified xaml workflow definition into an `ActivityBuilder`, and then calls `DynamicUpdate.PrepareForUpdate`.</span></span> <span data-ttu-id="27cda-136">`PrepareForUpdate`Tworzy kopię pliku definicji przepływu pracy wewnątrz `ActivityBuilder`.</span><span class="sxs-lookup"><span data-stu-id="27cda-136">`PrepareForUpdate` makes a copy of the workflow definition inside the `ActivityBuilder`.</span></span> <span data-ttu-id="27cda-137">Po zmodyfikowaniu definicji przepływu pracy tej kopii jest używana wraz z definicji przepływu pracy zmodyfikowane do tworzenia mapy aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="27cda-137">After the workflow definition is modified, this copy is used along with the modified workflow definition to create the update map.</span></span>  
  
    ```vb  
    Private Function StartUpdate(name As String) As ActivityBuilder  
        'Create the XamlXmlReaderSettings.  
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()  
        'In the XAML the "local" namespace referes to artifacts that come from   
        'the same project as the XAML. When loading XAML if the currently executing   
        'assembly is not the same assembly that was referred to as "local" in the XAML  
        'LocalAssembly must be set to the assembly containing the artifacts.  
        'Assembly.LoadFile requires an absolute path so convert this relative path  
        'to an absolute path.  
        readerSettings.LocalAssembly = Assembly.LoadFile(  
            Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))  
  
        Dim fullPath As String = Path.Combine(definitionPath, name)  
        Dim xamlReader As XamlXmlReader = New XamlXmlReader(fullPath, readerSettings)  
  
        'Load the workflow definition into an ActivityBuilder.  
        Dim wf As ActivityBuilder = XamlServices.Load(  
            ActivityXamlServices.CreateBuilderReader(xamlReader))  
  
        'PrepareForUpdate makes a copy of the workflow definition in the  
        'ActivityBuilder that is used for comparison when the update  
        'map is created.  
        DynamicUpdateServices.PrepareForUpdate(wf)  
  
        Return wf  
    End Function  
    ```  
  
    ```csharp  
    private static ActivityBuilder StartUpdate(string name)  
    {  
        // Create the XamlXmlReaderSettings.  
        XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()  
        {  
            // In the XAML the "local" namespace referes to artifacts that come from   
            // the same project as the XAML. When loading XAML if the currently executing   
            // assembly is not the same assembly that was referred to as "local" in the XAML  
            // LocalAssembly must be set to the assembly containing the artifacts.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            LocalAssembly = Assembly.LoadFile(  
                Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))  
        };  
  
        string path = Path.Combine(definitionPath, name);  
        XamlXmlReader xamlReader = new XamlXmlReader(path, readerSettings);  
  
        // Load the workflow definition into an ActivityBuilder.  
        ActivityBuilder wf = XamlServices.Load(  
            ActivityXamlServices.CreateBuilderReader(xamlReader))  
            as ActivityBuilder;  
  
        // PrepareForUpdate makes a copy of the workflow definition in the  
        // ActivityBuilder that is used for comparison when the update  
        // map is created.  
        DynamicUpdateServices.PrepareForUpdate(wf);  
  
        return wf;  
    }  
    ```  
  
12. <span data-ttu-id="27cda-138">Następnie dodaj następujące `CreateUpdateMethod` do `Program` klasy (lub `Module1`).</span><span class="sxs-lookup"><span data-stu-id="27cda-138">Next, add the following `CreateUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="27cda-139">Tworzy mapę aktualizacja dynamiczna przez wywołanie DynamicUpdateServices.CreateUpdateMap, a następnie zapisuje mapy aktualizacji przy użyciu określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="27cda-139">This creates a dynamic update map by calling DynamicUpdateServices.CreateUpdateMap, and then saves the update map using the specified name.</span></span> <span data-ttu-id="27cda-140">Ta mapa aktualizacji zawierają informacje wymagane przez środowisko wykonawcze przepływu pracy można zaktualizować wystąpienia utrwalonego przepływu pracy, która została uruchomiona z użyciem zawarte w oryginalnej definicji przepływu pracy `ActivityBuilder` tak, aby ukończy za pomocą definicji zaktualizowany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-140">This update map contains the information needed by the workflow runtime to update a persisted workflow instance that was started using the original workflow definition contained in the `ActivityBuilder` so that it completes using the updated workflow definition.</span></span>  
  
    ```vb  
    Private Sub CreateUpdateMaps(wf As ActivityBuilder, name As String)  
        'Create the UpdateMap.  
        Dim map As DynamicUpdateMap =  
            DynamicUpdateServices.CreateUpdateMap(wf)  
  
        'Serialize it to a file.  
        Dim mapFullPath As String = Path.Combine(mapPath, name)  
        Dim sz As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))  
        Using fs As FileStream = File.Open(mapFullPath, FileMode.Create)  
            sz.WriteObject(fs, map)  
        End Using  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateUpdateMaps(ActivityBuilder wf, string name)  
    {  
        // Create the UpdateMap.  
        DynamicUpdateMap map =  
            DynamicUpdateServices.CreateUpdateMap(wf);  
  
        // Serialize it to a file.  
        string path = Path.Combine(mapPath, name);  
        DataContractSerializer sz = new DataContractSerializer(typeof(DynamicUpdateMap));  
        using (FileStream fs = System.IO.File.Open(path, FileMode.Create))  
        {  
            sz.WriteObject(fs, map);  
        }  
    }  
    ```  
  
13. <span data-ttu-id="27cda-141">Dodaj następujące `SaveUpdatedDefinition` metodę `Program` klasy (lub `Module1`).</span><span class="sxs-lookup"><span data-stu-id="27cda-141">Add the following `SaveUpdatedDefinition` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="27cda-142">Taka metoda ogranicza definicji zaktualizowany przepływ pracy po utworzeniu Mapa aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="27cda-142">This method saves the updated workflow definition once the update map is created.</span></span>  
  
    ```vb  
    Private Sub SaveUpdatedDefinition(wf As ActivityBuilder, name As String)  
        Dim xamlPath As String = Path.Combine(definitionPath, name)  
        Dim sw As StreamWriter = File.CreateText(xamlPath)  
        Dim xw As XamlWriter = ActivityXamlServices.CreateBuilderWriter(  
            New XamlXmlWriter(sw, New XamlSchemaContext()))  
        XamlServices.Save(xw, wf)  
        sw.Close()  
    End Sub  
    ```  
  
    ```csharp  
    private static void SaveUpdatedDefinition(ActivityBuilder wf, string name)  
    {  
        string xamlPath = Path.Combine(definitionPath, name);  
        StreamWriter sw = File.CreateText(xamlPath);  
        XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(  
            new XamlXmlWriter(sw, new XamlSchemaContext()));  
        XamlServices.Save(xw, wf);  
        sw.Close();  
    }  
    ```  
  
###  <span data-ttu-id="27cda-143"><a name="BKMK_StateMachine"></a>Aby zaktualizować StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="27cda-143"><a name="BKMK_StateMachine"></a> To update StateMachineNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="27cda-144">Dodaj `CreateStateMachineUpdateMap` do `Program` klasy (lub `Module1`).</span><span class="sxs-lookup"><span data-stu-id="27cda-144">Add a `CreateStateMachineUpdateMap` to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Private Sub CreateStateMachineUpdateMap()  
  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateStateMachineUpdateMap()  
    {    
    }  
    ```  
  
2.  <span data-ttu-id="27cda-145">Wywoływania `StartUpdate` , a następnie pobrać odwołanie do elementu głównego `StateMachine` działania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-145">Make a call to `StartUpdate` and then get a reference to the root `StateMachine` activity of the workflow.</span></span>  
  
    ```vb  
    Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")  
  
    'Get a reference to the root StateMachine activity.  
    Dim sm As StateMachine = wf.Implementation  
    ```  
  
    ```csharp  
    ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");  
  
    // Get a reference to the root StateMachine activity.  
    StateMachine sm = wf.Implementation as StateMachine;  
    ```  
  
3.  <span data-ttu-id="27cda-146">Następnie zaktualizuj wyrażenia dwóch `WriteLine` działań, które stwierdzenie, czy wynik użytkownika jest za duży lub za mały, aby były one zgodne aktualizacje wprowadzone w [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="27cda-146">Next, update the expressions of the two `WriteLine` activities that display whether the user's guess is too high or too low so that they match the updates made in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
    ```vb  
    'Update the Text of the two WriteLine activities that write the  
    'results of the user's guess. They are contained in the workflow as the  
    'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
    Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action  
  
    'Update the "too low" message.  
    Dim tooLow As WriteLine = guessLow.Then  
    tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
  
    'Update the "too high" message.  
    Dim tooHigh As WriteLine = guessLow.Else  
    tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
    ```  
  
    ```csharp  
    // Update the Text of the two WriteLine activities that write the  
    // results of the user's guess. They are contained in the workflow as the  
    // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
    If guessLow = sm.States[1].Transitions[1].Action as If;  
  
    // Update the "too low" message.  
    WriteLine tooLow = guessLow.Then as WriteLine;  
    tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
  
    // Update the "too high" message.  
    WriteLine tooHigh = guessLow.Else as WriteLine;  
    tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
    ```  
  
4.  <span data-ttu-id="27cda-147">Następnie dodaj nowe `WriteLine` działania, w którym jest wyświetlany komunikat zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="27cda-147">Next, add the new `WriteLine` activity that displays the closing message.</span></span>  
  
    ```vb  
    'Create the new WriteLine that displays the closing message.  
    Dim wl As New WriteLine() With  
    {  
        .Text = New VisualBasicValue(Of String) _  
            ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
    }  
  
    'Add it as the Action for the Guess Correct transition. The Guess Correct  
    'transition is the first transition of States[1]. The transitions are listed  
    'at the bottom of the State activity designer.  
    sm.States(1).Transitions(0).Action = wl  
    ```  
  
    ```csharp  
    // Create the new WriteLine that displays the closing message.  
    WriteLine wl = new WriteLine  
    {  
        Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
    };  
  
    // Add it as the Action for the Guess Correct transition. The Guess Correct  
    // transition is the first transition of States[1]. The transitions are listed  
    // at the bottom of the State activity designer.  
    sm.States[1].Transitions[0].Action = wl;  
    ```  
  
5.  <span data-ttu-id="27cda-148">Po zaktualizowaniu przepływu pracy Wywołaj `CreateUpdateMaps` i `SaveUpdatedDefinition`.</span><span class="sxs-lookup"><span data-stu-id="27cda-148">After the workflow is updated, call `CreateUpdateMaps` and `SaveUpdatedDefinition`.</span></span> <span data-ttu-id="27cda-149">`CreateUpdateMaps`Tworzy i zapisuje `DynamicUpdateMap`, i `SaveUpdatedDefinition` zapisuje definicji zaktualizowany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-149">`CreateUpdateMaps` creates and saves the `DynamicUpdateMap`, and `SaveUpdatedDefinition` saves the updated workflow definition.</span></span>  
  
    ```vb  
    'Create the update map.  
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")  
  
    'Save the updated workflow definition.  
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")  
    ```  
  
    ```csharp  
    // Create the update map.  
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");  
  
    // Save the updated workflow definition.  
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");  
    ```  
  
     <span data-ttu-id="27cda-150">Poniższy przykład jest wypełniony `CreateStateMachineUpdateMap` metody.</span><span class="sxs-lookup"><span data-stu-id="27cda-150">The following example is the completed `CreateStateMachineUpdateMap` method.</span></span>  
  
    ```vb  
    Private Sub CreateStateMachineUpdateMap()  
        Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")  
  
        'Get a reference to the root StateMachine activity.  
        Dim sm As StateMachine = wf.Implementation  
  
        'Update the Text of the two WriteLine activities that write the  
        'results of the user's guess. They are contained in the workflow as the  
        'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
        Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action  
  
        'Update the "too low" message.  
        Dim tooLow As WriteLine = guessLow.Then  
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
  
        'Update the "too high" message.  
        Dim tooHigh As WriteLine = guessLow.Else  
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
  
        'Create the new WriteLine that displays the closing message.  
        Dim wl As New WriteLine() With  
        {  
            .Text = New VisualBasicValue(Of String) _  
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
        }  
  
        'Add it as the Action for the Guess Correct transition. The Guess Correct  
        'transition is the first transition of States[1]. The transitions are listed  
        'at the bottom of the State activity designer.  
        sm.States(1).Transitions(0).Action = wl  
  
        'Create the update map.  
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")  
  
        'Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateStateMachineUpdateMap()  
    {  
        ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");  
  
        // Get a reference to the root StateMachine activity.  
        StateMachine sm = wf.Implementation as StateMachine;  
  
        // Update the Text of the two WriteLine activities that write the  
        // results of the user's guess. They are contained in the workflow as the  
        // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.  
        If guessLow = sm.States[1].Transitions[1].Action as If;  
  
        // Update the "too low" message.  
        WriteLine tooLow = guessLow.Then as WriteLine;  
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
  
        // Update the "too high" message.  
        WriteLine tooHigh = guessLow.Else as WriteLine;  
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
  
        // Create the new WriteLine that displays the closing message.  
        WriteLine wl = new WriteLine  
        {  
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
        };  
  
        // Add it as the Action for the Guess Correct transition. The Guess Correct  
        // transition is the first transition of States[1]. The transitions are listed  
        // at the bottom of the State activity designer.  
        sm.States[1].Transitions[0].Action = wl;  
  
        // Create the update map.  
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");  
  
        // Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");  
    }  
    ```  
  
###  <span data-ttu-id="27cda-151"><a name="BKMK_Flowchart"></a>Aby zaktualizować FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="27cda-151"><a name="BKMK_Flowchart"></a> To update FlowchartNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="27cda-152">Dodaj następujące `CreateFlowchartUpdateMethod` do `Program` klasy (lub `Module1`).</span><span class="sxs-lookup"><span data-stu-id="27cda-152">Add the following `CreateFlowchartUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="27cda-153">Ta metoda jest podobna do `CreateStateMachineUpdateMap`.</span><span class="sxs-lookup"><span data-stu-id="27cda-153">This method is similar to `CreateStateMachineUpdateMap`.</span></span> <span data-ttu-id="27cda-154">Rozpoczyna się wywołanie `StartUpdate`, aktualizacje definicji przepływu pracy schemat blokowy i zakończeniu zapisując mapy aktualizacji, jak i definicja zaktualizowany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-154">It starts with a call to `StartUpdate`, updates the flowchart workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>  
  
    ```vb  
    Private Sub CreateFlowchartUpdateMap()  
        Dim wf As ActivityBuilder = StartUpdate("FlowchartNumberGuessWorkflow.xaml")  
  
        'Get a reference to the root Flowchart activity.  
        Dim fc As Flowchart = wf.Implementation  
  
        'Update the Text of the two WriteLine activities that write the  
        'results of the user's guess. They are contained in the workflow as the  
        'True and False action of the "Guess < Target" FlowDecision, which is  
        'Nodes[4].  
        Dim guessLow As FlowDecision = fc.Nodes(4)  
  
        'Update the "too low" message.  
        Dim trueStep As FlowStep = guessLow.True  
        Dim tooLow As WriteLine = trueStep.Action  
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
  
        'Update the "too high" message.  
        Dim falseStep As FlowStep = guessLow.False  
        Dim tooHigh As WriteLine = falseStep.Action  
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
  
        'Create the new WriteLine that displays the closing message.  
        Dim wl As New WriteLine() With  
        {  
            .Text = New VisualBasicValue(Of String) _  
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
        }  
  
        'Create a FlowStep to hold the WriteLine.  
        Dim closingStep As New FlowStep() With  
        {  
            .Action = wl  
        }  
  
        'Add this new FlowStep to the True action of the   
        '"Guess = Guess" FlowDecision  
        Dim guessCorrect As FlowDecision = fc.Nodes(3)  
        guessCorrect.True = closingStep  
  
        'Add the new FlowStep to the Nodes collection.  
        'If closingStep was replacing an existing node then  
        'we would need to remove that Step from the collection.  
        'In this example there was no existing True step to remove.  
        fc.Nodes.Add(closingStep)  
  
        'Create the update map.  
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map")  
  
        'Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml")  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateFlowchartUpdateMap()  
    {  
        ActivityBuilder wf = StartUpdate("FlowchartNumberGuessWorkflow.xaml");  
  
        // Get a reference to the root Flowchart activity.  
        Flowchart fc = wf.Implementation as Flowchart;  
  
        // Update the Text of the two WriteLine activities that write the  
        // results of the user's guess. They are contained in the workflow as the  
        // True and False action of the "Guess < Target" FlowDecision, which is  
        // Nodes[4].  
        FlowDecision guessLow = fc.Nodes[4] as FlowDecision;  
  
        // Update the "too low" message.  
        FlowStep trueStep = guessLow.True as FlowStep;  
        WriteLine tooLow = trueStep.Action as WriteLine;  
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
  
        // Update the "too high" message.  
        FlowStep falseStep = guessLow.False as FlowStep;  
        WriteLine tooHigh = falseStep.Action as WriteLine;  
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
  
        // Add the new WriteLine that displays the closing message.  
        WriteLine wl = new WriteLine  
        {  
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
        };  
  
        // Create a FlowStep to hold the WriteLine.  
        FlowStep closingStep = new FlowStep  
        {  
            Action = wl  
        };  
  
        // Add this new FlowStep to the True action of the   
        // "Guess == Guess" FlowDecision  
        FlowDecision guessCorrect = fc.Nodes[3] as FlowDecision;  
        guessCorrect.True = closingStep;  
  
        // Add the new FlowStep to the Nodes collection.  
        // If closingStep was replacing an existing node then  
        // we would need to remove that Step from the collection.  
        // In this example there was no existing True step to remove.  
        fc.Nodes.Add(closingStep);  
  
        // Create the update map.  
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map");  
  
        //  Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml");  
    }  
    ```  
  
###  <span data-ttu-id="27cda-155"><a name="BKMK_Sequential"></a>Aby zaktualizować SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="27cda-155"><a name="BKMK_Sequential"></a> To update SequentialNumberGuessWorkflow</span></span>  
  
1.  <span data-ttu-id="27cda-156">Dodaj następujące `CreateSequentialUpdateMethod` do `Program` klasy (lub `Module1`).</span><span class="sxs-lookup"><span data-stu-id="27cda-156">Add the following `CreateSequentialUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="27cda-157">Ta metoda jest podobna do innych metod.</span><span class="sxs-lookup"><span data-stu-id="27cda-157">This method is similar to the other two methods.</span></span> <span data-ttu-id="27cda-158">Rozpoczyna się wywołanie `StartUpdate`, aktualizacje definicji sekwencyjnego przepływu pracy i zakończeniu zapisując mapy aktualizacji, jak i definicja zaktualizowany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-158">It starts with a call to `StartUpdate`, updates the sequential workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>  
  
    ```vb  
    Private Sub CreateSequentialUpdateMap()  
        Dim wf As ActivityBuilder = StartUpdate("SequentialNumberGuessWorkflow.xaml")  
  
        'Get a reference to the root activity in the workflow.  
        Dim rootSequence As Sequence = wf.Implementation  
  
        'Update the Text of the two WriteLine activities that write the  
        'results of the user's guess. They are contained in the workflow as the  
        'Then and Else action of the "Guess < Target" If activity.  
        'Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If  
        Dim gameLoop As Statements.DoWhile = rootSequence.Activities(1)  
        Dim gameBody As Sequence = gameLoop.Body  
        Dim guessCorrect As Statements.If = gameBody.Activities(2)  
        Dim guessLow As Statements.If = guessCorrect.Then  
        Dim tooLow As WriteLine = guessLow.Then  
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")  
        Dim tooHigh As WriteLine = guessLow.Else  
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")  
  
        'Create the new WriteLine that displays the closing message.  
        Dim wl As New WriteLine() With  
        {  
            .Text = New VisualBasicValue(Of String) _  
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")  
        }  
  
        'Insert it as the third activity in the root sequence  
        rootSequence.Activities.Insert(2, wl)  
  
        'Create the update map.  
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map")  
  
        'Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml")  
    End Sub  
    ```  
  
    ```csharp  
    private static void CreateSequentialUpdateMap()  
    {  
        ActivityBuilder wf = StartUpdate("SequentialNumberGuessWorkflow.xaml");  
  
        // Get a reference to the root activity in the workflow.  
        Sequence rootSequence = wf.Implementation as Sequence;  
  
        // Update the Text of the two WriteLine activities that write the  
        // results of the user's guess. They are contained in the workflow as the  
        // Then and Else action of the "Guess < Target" If activity.  
        // Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If  
        DoWhile gameLoop = rootSequence.Activities[1] as DoWhile;  
        Sequence gameBody = gameLoop.Body as Sequence;  
        If guessCorrect = gameBody.Activities[2] as If;  
        If guessLow = guessCorrect.Then as If;  
        WriteLine tooLow = guessLow.Then as WriteLine;  
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");  
        WriteLine tooHigh = guessLow.Else as WriteLine;  
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");  
  
        // Add the new WriteLine that displays the closing message.  
        WriteLine wl = new WriteLine  
        {  
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")  
        };  
  
        // Insert it as the third activity in the root sequence  
        rootSequence.Activities.Insert(2, wl);  
  
        // Create the update map.  
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map");  
  
        // Save the updated workflow definition.  
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml");  
    }  
    ```  
  
###  <span data-ttu-id="27cda-159"><a name="BKMK_CreateUpdateMaps"></a>Aby skompilować i uruchomić aplikację CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="27cda-159"><a name="BKMK_CreateUpdateMaps"></a> To build and run the CreateUpdateMaps application</span></span>  
  
1.  <span data-ttu-id="27cda-160">Aktualizacja `Main` — metoda i dodaj następujące wywołania trzy metody.</span><span class="sxs-lookup"><span data-stu-id="27cda-160">Update the `Main` method and add the following three method calls.</span></span> <span data-ttu-id="27cda-161">Te metody są dodawane w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="27cda-161">These methods are added in the following sections.</span></span> <span data-ttu-id="27cda-162">Każda metoda aktualizacji odpowiedniego przepływu pracy numer argumentu i tworzy `DynamicUpdateMap` opisujący aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="27cda-162">Each method updates the corresponding number guess workflow and creates a `DynamicUpdateMap` that describes the updates.</span></span>  
  
    ```vb  
    Sub Main()  
        'Create the update maps for the changes needed to the v1 activities  
        'so they match the v2 activities.  
        CreateSequentialUpdateMap()  
        CreateFlowchartUpdateMap()  
        CreateStateMachineUpdateMap()  
    End Sub  
    ```  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        // Create the update maps for the changes needed to the v1 activities  
        // so they match the v2 activities.  
        CreateSequentialUpdateMap();  
        CreateFlowchartUpdateMap();  
        CreateStateMachineUpdateMap();  
    }  
    ```  
  
2.  <span data-ttu-id="27cda-163">Kliknij prawym przyciskiem myszy **CreateUpdateMaps** w **Eksploratora rozwiązań** i wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="27cda-163">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
3.  <span data-ttu-id="27cda-164">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania, a następnie klawisz CTRL + F5, aby uruchomić `CreateUpdateMaps` aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27cda-164">Press CTRL+SHIFT+B to build the solution, and then CTRL+F5 to run the `CreateUpdateMaps` application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27cda-165">`CreateUpdateMaps` Aplikacji nie są wyświetlane wszystkie informacje o stanie podczas uruchamiania, ale dostępne **NumberGuessWorkflowActivities_du** folderu i **PreviousVersions** folderu zostanie wyświetlony pliki definicji zaktualizowany przepływ pracy i mapowania aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="27cda-165">The `CreateUpdateMaps` application does not display any status information while running, but if you look in the **NumberGuessWorkflowActivities_du** folder and the **PreviousVersions** folder you will see the updated workflow definition files and the update maps.</span></span>  
  
     <span data-ttu-id="27cda-166">Po mapy aktualizacji są tworzone i definicji przepływu pracy, zaktualizować, następnym krokiem jest zaktualizowany przepływ pracy zestawu zawierającego aktualizacji definicji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="27cda-166">Once the update maps are created and the workflow definitions updated, the next step is to build an updated workflow assembly containing the updated definitions.</span></span>  
  
###  <span data-ttu-id="27cda-167"><a name="BKMK_BuildAssembly"></a>Tworzenie zestawu zaktualizowany przepływ pracy</span><span class="sxs-lookup"><span data-stu-id="27cda-167"><a name="BKMK_BuildAssembly"></a> To build the updated workflow assembly</span></span>  
  
1.  <span data-ttu-id="27cda-168">Otwórz drugie wystąpienie parametru [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27cda-168">Open a second instance of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="27cda-169">Wybierz **Otwórz**, **projektu/rozwiązania** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="27cda-169">Choose **Open**, **Project/Solution** from the **File** menu.</span></span>  
  
3.  <span data-ttu-id="27cda-170">Przejdź do **NumberGuessWorkflowActivities_du** folder utworzony w [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), wybierz pozycję **NumberGuessWorkflowActivities.csproj**  (lub **vbproj**) i kliknij przycisk **Otwórz**.</span><span class="sxs-lookup"><span data-stu-id="27cda-170">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md), select **NumberGuessWorkflowActivities.csproj** (or **vbproj**), and click **Open**.</span></span>  
  
4.  <span data-ttu-id="27cda-171">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **SequentialNumberGuessWorkflow.xaml** i wybierz polecenie **wykluczyć z projektu**.</span><span class="sxs-lookup"><span data-stu-id="27cda-171">In **Solution Explorer**, right click **SequentialNumberGuessWorkflow.xaml** and choose **Exclude From Project**.</span></span> <span data-ttu-id="27cda-172">Tak samo postąpić w **FlowchartNumberGuessWorkflow.xaml** i **StateMachineNumberGuessWorkflow.xaml**.</span><span class="sxs-lookup"><span data-stu-id="27cda-172">Do the same thing for **FlowchartNumberGuessWorkflow.xaml** and **StateMachineNumberGuessWorkflow.xaml**.</span></span> <span data-ttu-id="27cda-173">Ten krok powoduje usunięcie poprzednich wersji definicji przepływu pracy z projektu.</span><span class="sxs-lookup"><span data-stu-id="27cda-173">This step removes the previous versions of the workflow definitions from the project.</span></span>  
  
5.  <span data-ttu-id="27cda-174">Wybierz **Dodaj istniejący element** z **projektu** menu.</span><span class="sxs-lookup"><span data-stu-id="27cda-174">Choose **Add Existing Item** from the **Project** menu.</span></span>  
  
6.  <span data-ttu-id="27cda-175">Przejdź do **NumberGuessWorkflowActivities_du** folder utworzony w [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="27cda-175">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
7.  <span data-ttu-id="27cda-176">Wybierz **plików XAML (\*.xaml;\*. xoml)** z **pliki typu** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="27cda-176">Choose **XAML Files (\*.xaml;\*.xoml)** from the **Files of type** drop-down list.</span></span>  
  
8.  <span data-ttu-id="27cda-177">Wybierz **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, i **StateMachineNumberGuessWorkflow_du.xaml** i kliknij przycisk  **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="27cda-177">Select **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, and **StateMachineNumberGuessWorkflow_du.xaml** and click **Add**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27cda-178">CTRL + kliknięcie, aby zaznaczyć wiele elementów naraz.</span><span class="sxs-lookup"><span data-stu-id="27cda-178">CTRL+Click to select multiple items at a time.</span></span>  
  
     <span data-ttu-id="27cda-179">Ten krok powoduje dodanie zaktualizowanych wersji definicji przepływu pracy do projektu.</span><span class="sxs-lookup"><span data-stu-id="27cda-179">This step adds the updated versions of the workflow definitions to the project.</span></span>  
  
9. <span data-ttu-id="27cda-180">Naciśnij kombinację klawiszy CTRL+SHIFT+B. Projekt zostanie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="27cda-180">Press CTRL+SHIFT+B to build the project.</span></span>  
  
10. <span data-ttu-id="27cda-181">Wybierz **Zamknij rozwiązanie** z **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="27cda-181">Choose **Close Solution** from the **File** menu.</span></span> <span data-ttu-id="27cda-182">Plik rozwiązania dla projektu nie jest wymagana, więc klikamy **nr** zamknąć [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] bez zapisywania pliku rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="27cda-182">A solution file for the project is not required, so click **No** to close [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] without saving a solution file.</span></span> <span data-ttu-id="27cda-183">Wybierz **zakończenia** z **pliku** menu, aby zamknąć [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27cda-183">Choose **Exit** from the **File** menu to close [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)].</span></span>  
  
11. <span data-ttu-id="27cda-184">Otwórz Eksploratora Windows i przejdź do **NumberGuessWorkflowActivities_du\bin\Debug** folder (lub **bin\Release** w zależności od ustawienia projektu).</span><span class="sxs-lookup"><span data-stu-id="27cda-184">Open Windows Explorer and navigate to the **NumberGuessWorkflowActivities_du\bin\Debug** folder (or **bin\Release** depending on your project settings).</span></span>  
  
12. <span data-ttu-id="27cda-185">Zmień nazwę **NumberGuessWorkflowActivities.dll** do **NumberGuessWorkflowActivities_v15.dll**i skopiuj go do **PreviousVersions** folder utworzony w [Porady: hostowanie wielu wersji przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="27cda-185">Rename **NumberGuessWorkflowActivities.dll** to **NumberGuessWorkflowActivities_v15.dll**, and copy it to the **PreviousVersions** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>  
  
###  <span data-ttu-id="27cda-186"><a name="BKMK_UpdateWorkflowVersionMap"></a>Aby zaktualizować WorkflowVersionMap do nowych wersji</span><span class="sxs-lookup"><span data-stu-id="27cda-186"><a name="BKMK_UpdateWorkflowVersionMap"></a> To update WorkflowVersionMap with the new versions</span></span>  
  
1.  <span data-ttu-id="27cda-187">Wrócić do początkowej wystąpienie [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27cda-187">Switch back to the initial instance of [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="27cda-188">Kliknij dwukrotnie **WorkflowVersionMap.cs** (lub **WorkflowVersionMap.vb**) w obszarze **NumberGuessWorkflowHost** projektu, aby go otworzyć.</span><span class="sxs-lookup"><span data-stu-id="27cda-188">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>  
  
3.  <span data-ttu-id="27cda-189">Dodaj trzy nowe tożsamości przepływu pracy poniżej sześciu istniejących deklaracji tożsamości przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-189">Add three new workflow identities just below the six existing workflow identity declarations.</span></span> <span data-ttu-id="27cda-190">W tym samouczku `1.5.0.0` jest używany jako `WorkflowIdentity.Version` tożsamości aktualizacji dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="27cda-190">In this tutorial, `1.5.0.0` is used as the `WorkflowIdentity.Version` for the dynamic update identities.</span></span> <span data-ttu-id="27cda-191">Te nowe `v15` tożsamości będą używane w przepływie pracy zawierają definicje poprawne przepływu pracy dla wystąpień aktualizowany dynamicznie utrwalonych przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-191">These new `v15` workflow identities will be used provide the correct workflow definition for the dynamically updated persisted workflow instances.</span></span>  
  
    ```vb  
    'Current version identities.  
    Public StateMachineNumberGuessIdentity As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity As WorkflowIdentity  
    Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
    'v1 identities.  
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
    'v1.5 (Dynamimc Update) identities.  
    Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity  
    Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity  
    Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity  
    ```  
  
    ```csharp  
    // Current version identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity;  
    static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
    // v1 identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;  
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;  
  
    // v1.5 (Dynamic Update) identities.  
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;  
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;  
    static public WorkflowIdentity SequentialNumberGuessIdentity_v15;  
    ```  
  
4.  <span data-ttu-id="27cda-192">Dodaj następujący kod na końcu konstruktora.</span><span class="sxs-lookup"><span data-stu-id="27cda-192">Add the following code at the end of the constructor.</span></span> <span data-ttu-id="27cda-193">Ten kod inicjuje tożsamości przepływu pracy aktualizacji dynamicznej, ładuje odpowiedniej definicji przepływu pracy i dodaje je do słownika wersji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-193">This code initializes the dynamic update workflow identities, loads the corresponding workflow definitions, and adds them to the workflow version dictionary.</span></span>  
  
    ```vb  
    'Initialize the dynamic update workflow identities.  
    StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With  
    {  
        .Name = "StateMachineNumberGuessWorkflow",  
        .Version = New Version(1, 5, 0, 0)  
    }  
  
    FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With  
    {  
        .Name = "FlowchartNumberGuessWorkflow",  
        .Version = New Version(1, 5, 0, 0)  
    }  
  
    SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With  
    {  
        .Name = "SequentialNumberGuessWorkflow",  
        .Version = New Version(1, 5, 0, 0)  
    }  
  
    'Add the dynamic update workflow identities to the dictionary along with  
    'the corresponding workflow definitions loaded from the v15 assembly.  
    'Assembly.LoadFile requires an absolute path so convert this relative path  
    'to an absolute path.  
    Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"  
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)  
    Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)  
  
    map.Add(StateMachineNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
    map.Add(SequentialNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
    map.Add(FlowchartNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
    ```  
  
    ```csharp  
    // Initialize the dynamic update workflow identities.  
    StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity  
    {  
        Name = "StateMachineNumberGuessWorkflow",  
        Version = new Version(1, 5, 0, 0)  
    };  
  
    FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity  
    {  
        Name = "FlowchartNumberGuessWorkflow",  
        Version = new Version(1, 5, 0, 0)  
    };  
  
    SequentialNumberGuessIdentity_v15 = new WorkflowIdentity  
    {  
        Name = "SequentialNumberGuessWorkflow",  
        Version = new Version(1, 5, 0, 0)  
    };  
  
    // Add the dynamic update workflow identities to the dictionary along with  
    // the corresponding workflow definitions loaded from the v15 assembly.  
    // Assembly.LoadFile requires an absolute path so convert this relative path  
    // to an absolute path.  
    string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";  
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);  
    Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);  
  
    map.Add(StateMachineNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
    map.Add(SequentialNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
    map.Add(FlowchartNumberGuessIdentity_v15,  
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
    ```  
  
     <span data-ttu-id="27cda-194">Poniższy przykład jest wypełniony `WorkflowVersionMap` klasy.</span><span class="sxs-lookup"><span data-stu-id="27cda-194">The following example is the completed `WorkflowVersionMap` class.</span></span>  
  
    ```vb  
    Public Module WorkflowVersionMap  
        Dim map As Dictionary(Of WorkflowIdentity, Activity)  
  
        'Current version identities.  
        Public StateMachineNumberGuessIdentity As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity As WorkflowIdentity  
        Public SequentialNumberGuessIdentity As WorkflowIdentity  
  
        'v1 identities.  
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity  
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity  
  
        'v1.5 (Dynamimc Update) identities.  
        Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity  
        Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity  
        Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity  
  
        Sub New()  
            map = New Dictionary(Of WorkflowIdentity, Activity)  
  
            'Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(2, 0, 0, 0)  
            }  
  
            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())  
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())  
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())  
  
            'Initialize the previous workflow version identities.  
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 0, 0, 0)  
            }  
  
            'Add the previous version workflow identities to the dictionary along with  
            'the corresponding workflow definitions loaded from the v1 assembly.  
            'Assembly.LoadFile requires an absolute path so convert this relative path  
            'to an absolute path.  
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"  
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)  
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)  
  
            map.Add(StateMachineNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
            map.Add(SequentialNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
            map.Add(FlowchartNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
  
            'Initialize the dynamic update workflow identities.  
            StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With  
            {  
                .Name = "StateMachineNumberGuessWorkflow",  
                .Version = New Version(1, 5, 0, 0)  
            }  
  
            FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With  
            {  
                .Name = "FlowchartNumberGuessWorkflow",  
                .Version = New Version(1, 5, 0, 0)  
            }  
  
            SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With  
            {  
                .Name = "SequentialNumberGuessWorkflow",  
                .Version = New Version(1, 5, 0, 0)  
            }  
  
            'Add the dynamic update workflow identities to the dictionary along with  
            'the corresponding workflow definitions loaded from the v15 assembly.  
            'Assembly.LoadFile requires an absolute path so convert this relative path  
            'to an absolute path.  
            Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"  
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)  
            Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)  
  
            map.Add(StateMachineNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))  
  
            map.Add(SequentialNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))  
  
            map.Add(FlowchartNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))  
        End Sub  
  
        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity  
            Return map(identity)  
        End Function  
  
        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String  
            Return identity.ToString()  
        End Function  
    End Module  
    ```  
  
    ```csharp  
    public static class WorkflowVersionMap  
    {  
        static Dictionary<WorkflowIdentity, Activity> map;  
  
        // Current version identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity;  
        static public WorkflowIdentity SequentialNumberGuessIdentity;  
  
        // v1 identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;  
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;  
  
        // v1.5 (Dynamic Update) identities.  
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;  
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;  
        static public WorkflowIdentity SequentialNumberGuessIdentity_v15;  
  
        static WorkflowVersionMap()  
        {  
            map = new Dictionary<WorkflowIdentity, Activity>();  
  
            // Add the current workflow version identities.  
            StateMachineNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                // Version = new Version(1, 0, 0, 0),  
                Version = new Version(2, 0, 0, 0)  
            };  
  
            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());  
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());  
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());  
  
            // Initialize the previous workflow version identities.  
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 0, 0, 0)  
            };  
  
            // Add the previous version workflow identities to the dictionary along with  
            // the corresponding workflow definitions loaded from the v1 assembly.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";  
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);  
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);  
  
            map.Add(StateMachineNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
            map.Add(SequentialNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
            map.Add(FlowchartNumberGuessIdentity_v1,  
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
  
            // Initialize the dynamic update workflow identities.  
            StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity  
            {  
                Name = "StateMachineNumberGuessWorkflow",  
                Version = new Version(1, 5, 0, 0)  
            };  
  
            FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity  
            {  
                Name = "FlowchartNumberGuessWorkflow",  
                Version = new Version(1, 5, 0, 0)  
            };  
  
            SequentialNumberGuessIdentity_v15 = new WorkflowIdentity  
            {  
                Name = "SequentialNumberGuessWorkflow",  
                Version = new Version(1, 5, 0, 0)  
            };  
  
            // Add the dynamic update workflow identities to the dictionary along with  
            // the corresponding workflow definitions loaded from the v15 assembly.  
            // Assembly.LoadFile requires an absolute path so convert this relative path  
            // to an absolute path.  
            string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";  
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);  
            Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);  
  
            map.Add(StateMachineNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);  
  
            map.Add(SequentialNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);  
  
            map.Add(FlowchartNumberGuessIdentity_v15,  
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);  
        }  
  
        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)  
        {  
            return map[identity];  
        }  
  
        public static string GetIdentityDescription(WorkflowIdentity identity)  
        {  
            return identity.ToString();  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="27cda-195">Naciśnij kombinację klawiszy CTRL+SHIFT+B. Projekt zostanie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="27cda-195">Press CTRL+SHIFT+B to build the project.</span></span>  
  
###  <span data-ttu-id="27cda-196"><a name="BKMK_ApplyUpdate"></a>Aby zastosować aktualizacje dynamiczne</span><span class="sxs-lookup"><span data-stu-id="27cda-196"><a name="BKMK_ApplyUpdate"></a> To apply the dynamic updates</span></span>  
  
1.  <span data-ttu-id="27cda-197">Kliknij prawym przyciskiem myszy **WF45GettingStartedTutorial** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="27cda-197">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="27cda-198">W **zainstalowana** węzła, wybierz opcję **Visual C#**, **Windows** (lub **Visual Basic**, **Windows**).</span><span class="sxs-lookup"><span data-stu-id="27cda-198">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27cda-199">W zależności od tego, jaki język programowania jest skonfigurowany jako podstawowy język w programie Visual Studio, **Visual C#** lub **Visual Basic** węzeł może być w obszarze **inne języki** w węźle **zainstalowana** węzła.</span><span class="sxs-lookup"><span data-stu-id="27cda-199">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>  
  
     <span data-ttu-id="27cda-200">Upewnij się, że **.NET Framework 4.5** jest zaznaczony na liście rozwijanej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27cda-200">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="27cda-201">Wybierz **aplikacji konsoli** z **Windows** listy.</span><span class="sxs-lookup"><span data-stu-id="27cda-201">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="27cda-202">Typ **ApplyDynamicUpdate** do **nazwa** polu i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="27cda-202">Type **ApplyDynamicUpdate** into the **Name** box and click **OK**.</span></span>  
  
3.  <span data-ttu-id="27cda-203">Kliknij prawym przyciskiem myszy **ApplyDynamicUpdate** w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="27cda-203">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Add Reference**.</span></span>  
  
4.  <span data-ttu-id="27cda-204">Kliknij przycisk **rozwiązania** i zaznacz pole wyboru obok pozycji **NumberGuessWorkflowHost**.</span><span class="sxs-lookup"><span data-stu-id="27cda-204">Click **Solution** and check the box next to **NumberGuessWorkflowHost**.</span></span> <span data-ttu-id="27cda-205">To odwołanie jest wymagane, aby `ApplyDynamicUpdate` można użyć `NumberGuessWorkflowHost.WorkflowVersionMap` klasy.</span><span class="sxs-lookup"><span data-stu-id="27cda-205">This reference is needed so that `ApplyDynamicUpdate` can use the `NumberGuessWorkflowHost.WorkflowVersionMap` class.</span></span>  
  
5.  <span data-ttu-id="27cda-206">Wybierz **Framework** z **zestawy** w węźle **Dodaj odwołanie** listy.</span><span class="sxs-lookup"><span data-stu-id="27cda-206">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="27cda-207">Typ **elementu System.Activities** do **wyszukiwania zestawów** pole.</span><span class="sxs-lookup"><span data-stu-id="27cda-207">Type **System.Activities** into the **Search Assemblies** box.</span></span> <span data-ttu-id="27cda-208">Spowoduje to Filtrowanie zestawów i ułatwiają wybierz żądane odwołania.</span><span class="sxs-lookup"><span data-stu-id="27cda-208">This will filter the assemblies and make the desired references easier to select.</span></span>  
  
6.  <span data-ttu-id="27cda-209">Zaznacz pole wyboru obok **elementu System.Activities** z **wyniki wyszukiwania** listy.</span><span class="sxs-lookup"><span data-stu-id="27cda-209">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>  
  
7.  <span data-ttu-id="27cda-210">Typ **serializacji** do **wyszukiwania zestawów** polu, a następnie zaznacz pole wyboru obok **System.Runtime.Serialization** z **wyniki wyszukiwania**  listy.</span><span class="sxs-lookup"><span data-stu-id="27cda-210">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>  
  
8.  <span data-ttu-id="27cda-211">Typ **DurableInstancing** do **wyszukiwania zestawów** polu, a następnie zaznacz pole wyboru obok **System.Activities.DurableInstancing** i  **System.Runtime.DurableInstancing** z **wyniki wyszukiwania** listy.</span><span class="sxs-lookup"><span data-stu-id="27cda-211">Type **DurableInstancing** into the **Search Assemblies** box, and check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list.</span></span>  
  
9. <span data-ttu-id="27cda-212">Kliknij przycisk **OK** zamknąć **Menedżera odwołań** i dodać odwołań.</span><span class="sxs-lookup"><span data-stu-id="27cda-212">Click **OK** to close **Reference Manager** and add the references.</span></span>  
  
10. <span data-ttu-id="27cda-213">Kliknij prawym przyciskiem myszy **ApplyDynamicUpdate** w Eksploratorze rozwiązań i wybierz polecenie **Dodaj**, **klasy**.</span><span class="sxs-lookup"><span data-stu-id="27cda-213">Right-click **ApplyDynamicUpdate** in Solution Explorer and choose **Add**, **Class**.</span></span> <span data-ttu-id="27cda-214">Typ `DynamicUpdateInfo` do **nazwa** polu i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="27cda-214">Type `DynamicUpdateInfo` into the **Name** box and click **Add**.</span></span>  
  
11. <span data-ttu-id="27cda-215">Dodaj następujące dwa elementy członkowskie `DynamicUpdateInfo` klasy.</span><span class="sxs-lookup"><span data-stu-id="27cda-215">Add the following two members to the `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="27cda-216">Poniższy przykład jest wypełniony `DynamicUpdateInfo` klasy.</span><span class="sxs-lookup"><span data-stu-id="27cda-216">The following example is the completed `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="27cda-217">Ta klasa zawiera informacje na temat mapy aktualizacji i nowy identyfikator przepływu pracy używane po zaktualizowaniu wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-217">This class contains information on the update map and new workflow identity used when a workflow instance is updated.</span></span>  
  
    ```vb  
    Public Class DynamicUpdateInfo  
        Public updateMap As DynamicUpdateMap  
        Public newIdentity As WorkflowIdentity  
    End Class  
    ```  
  
    ```csharp  
    class DynamicUpdateInfo  
    {  
        public DynamicUpdateMap updateMap;  
        public WorkflowIdentity newIdentity;  
    }  
    ```  
  
12. <span data-ttu-id="27cda-218">Dodaj następujące `using` (lub `Imports`) instrukcje w górnej części pliku z innym `using` (lub `Imports`) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="27cda-218">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities  
    Imports System.Activities.DynamicUpdate  
    ```  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.DynamicUpdate;  
    ```  
  
13. <span data-ttu-id="27cda-219">Kliknij dwukrotnie **Program.cs** (lub **Module1.vb**) w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="27cda-219">Double-click **Program.cs** (or **Module1.vb**) in Solution Explorer.</span></span>  
  
14. <span data-ttu-id="27cda-220">Dodaj następujące `using` (lub `Imports`) instrukcje w górnej części pliku z innym `using` (lub `Imports`) instrukcje.</span><span class="sxs-lookup"><span data-stu-id="27cda-220">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports NumberGuessWorkflowHost  
    Imports System.Data.SqlClient  
    Imports System.Activities.DynamicUpdate  
    Imports System.IO  
    Imports System.Runtime.Serialization  
    Imports System.Activities  
    Imports System.Activities.DurableInstancing  
    ```  
  
    ```csharp  
    using NumberGuessWorkflowHost;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Activities;  
    using System.Activities.DynamicUpdate;  
    using System.IO;  
    using System.Runtime.Serialization;  
    using System.Activities.DurableInstancing;  
    ```  
  
15. <span data-ttu-id="27cda-221">Dodaj następujący element członkowski ciąg połączenia do `Program` klasy (lub `Module1`).</span><span class="sxs-lookup"><span data-stu-id="27cda-221">Add the following connection string member to the `Program` class (or `Module1`).</span></span>  
  
    ```vb  
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"  
    ```  
  
    ```csharp  
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="27cda-222">W zależności od posiadanej wersji programu SQL Server nazwę serwera w ciągu połączenia może być różne.</span><span class="sxs-lookup"><span data-stu-id="27cda-222">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>  
  
16. <span data-ttu-id="27cda-223">Dodaj następujące `GetIDs` metodę `Program` klasy (lub `Module1`).</span><span class="sxs-lookup"><span data-stu-id="27cda-223">Add the following `GetIDs` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="27cda-224">Ta metoda zwraca listę identyfikatorów wystąpienia utrwalonego przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-224">This method returns a list of persisted workflow instance ids.</span></span>  
  
    ```vb  
    Function GetIds() As IList(Of Guid)  
        Dim Ids As New List(Of Guid)  
        Dim localCmd = _  
            String.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]")  
        Using localCon = New SqlConnection(connectionString)  
            Dim cmd As SqlCommand = localCon.CreateCommand()  
            cmd.CommandText = localCmd  
            localCon.Open()  
            Using reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)  
                While reader.Read()  
                    'Get the InstanceId of the persisted Workflow  
                    Dim id As Guid = Guid.Parse(reader(0).ToString())  
  
                    'Add it to the list.  
                    Ids.Add(id)  
                End While  
            End Using  
        End Using  
  
        Return Ids  
    End Function  
    ```  
  
    ```csharp  
    static IList<Guid> GetIds()  
    {  
        List<Guid> Ids = new List<Guid>();  
        string localCmd = string.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]");  
        using (SqlConnection localCon = new SqlConnection(connectionString))  
        {  
            SqlCommand cmd = localCon.CreateCommand();  
            cmd.CommandText = localCmd;  
            localCon.Open();  
            using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))  
            {  
                while (reader.Read())  
                {  
                    // Get the InstanceId of the persisted Workflow  
                    Guid id = Guid.Parse(reader[0].ToString());  
  
                    // Add it to the list.  
                    Ids.Add(id);  
                }  
            }  
        }  
  
        return Ids;  
    }  
    ```  
  
17. <span data-ttu-id="27cda-225">Dodaj następujące `LoadMap` metodę `Program` klasy (lub `Module1`).</span><span class="sxs-lookup"><span data-stu-id="27cda-225">Add the following `LoadMap` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="27cda-226">Ta metoda tworzy słownik, który mapuje `v1` tożsamości mapy aktualizacji przepływu pracy i nowej tożsamości przepływu pracy używane do aktualizowania odpowiadającego utrwalone wystąpienia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-226">This method creates a dictionary that maps `v1` workflow identities to the update maps and new workflow identities used to update the corresponding persisted workflow instances.</span></span>  
  
    ```vb  
    Function LoadMap(mapName As String) As DynamicUpdateMap  
        Dim mapPath As String = Path.Combine("..\..\..\PreviousVersions", mapName)  
  
        Dim map As DynamicUpdateMap  
        Using fs As FileStream = File.Open(mapPath, FileMode.Open)  
            Dim serializer As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))  
            Dim updateMap = serializer.ReadObject(fs)  
            If updateMap Is Nothing Then  
                Throw New ApplicationException("DynamicUpdateMap is null.")  
            End If  
  
            map = updateMap  
        End Using  
  
        Return map  
    End Function  
    ```  
  
    ```csharp  
    static DynamicUpdateMap LoadMap(string mapName)  
    {  
        string path = Path.Combine(@"..\..\..\PreviousVersions", mapName);  
  
        DynamicUpdateMap map;  
        using (FileStream fs = File.Open(path, FileMode.Open))  
        {  
            DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));  
            object updateMap = serializer.ReadObject(fs);  
            if (updateMap == null)  
            {  
                throw new ApplicationException("DynamicUpdateMap is null.");  
            }  
  
            map = updateMap as DynamicUpdateMap;  
        }  
  
        return map;  
    }  
    ```  
  
18. <span data-ttu-id="27cda-227">Dodaj następujące `LoadMaps` metodę `Program` klasy (lub `Module1`).</span><span class="sxs-lookup"><span data-stu-id="27cda-227">Add the following `LoadMaps` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="27cda-228">Ta metoda ładuje trzy mapy aktualizacji i tworzy słownik mapujący `v1` tożsamości mapy aktualizacji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-228">This method loads the three update maps and creates a dictionary that maps `v1` workflow identities to the update maps.</span></span>  
  
    ```vb  
    Function LoadMaps() As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo)  
        'There are 3 update maps to describe the changes to update v1 workflows,  
        'one for reach of the 3 workflow types in the tutorial.  
        Dim maps = New Dictionary(Of WorkflowIdentity, DynamicUpdateInfo)()  
  
        Dim sequentialMap As DynamicUpdateMap = LoadMap("SequentialNumberGuessWorkflow.map")  
        Dim sequentialInfo = New DynamicUpdateInfo With  
        {  
            .updateMap = sequentialMap,  
            .newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15  
        }  
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo)  
  
        Dim stateMap As DynamicUpdateMap = LoadMap("StateMachineNumberGuessWorkflow.map")  
        Dim stateInfo = New DynamicUpdateInfo With  
        {  
            .updateMap = stateMap,  
            .newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15  
        }  
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo)  
  
        Dim flowchartMap As DynamicUpdateMap = LoadMap("FlowchartNumberGuessWorkflow.map")  
        Dim flowchartInfo = New DynamicUpdateInfo With  
        {  
            .updateMap = flowchartMap,  
            .newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15  
        }  
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo)  
  
        Return maps  
    End Function  
    ```  
  
    ```csharp  
    static IDictionary<WorkflowIdentity, DynamicUpdateInfo> LoadMaps()  
    {  
        // There are 3 update maps to describe the changes to update v1 workflows,  
        // one for reach of the 3 workflow types in the tutorial.  
        Dictionary<WorkflowIdentity, DynamicUpdateInfo> maps =  
            new Dictionary<WorkflowIdentity, DynamicUpdateInfo>();  
  
        DynamicUpdateMap sequentialMap = LoadMap("SequentialNumberGuessWorkflow.map");  
        DynamicUpdateInfo sequentialInfo = new DynamicUpdateInfo  
        {  
            updateMap = sequentialMap,  
            newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15  
        };  
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo);  
  
        DynamicUpdateMap stateMap = LoadMap("StateMachineNumberGuessWorkflow.map");  
        DynamicUpdateInfo stateInfo = new DynamicUpdateInfo  
        {  
            updateMap = stateMap,  
            newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15  
        };  
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo);  
  
        DynamicUpdateMap flowchartMap = LoadMap("FlowchartNumberGuessWorkflow.map");  
        DynamicUpdateInfo flowchartInfo = new DynamicUpdateInfo  
        {  
            updateMap = flowchartMap,  
            newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15  
        };  
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo);  
  
        return maps;              
    }  
    ```  
  
19. <span data-ttu-id="27cda-229">Dodaj następujący kod do `Main`.</span><span class="sxs-lookup"><span data-stu-id="27cda-229">Add the following code to `Main`.</span></span> <span data-ttu-id="27cda-230">Ten kod iteruje utrwalonych przepływów pracy wystąpień i sprawdza, czy każdy `WorkflowIdentity`.</span><span class="sxs-lookup"><span data-stu-id="27cda-230">This code iterates the persisted workflow instances and examines each `WorkflowIdentity`.</span></span> <span data-ttu-id="27cda-231">Jeśli `WorkflowIdentity` mapuje `v1` wystąpienia przepływu pracy `WorkflowApplication` skonfigurowano definicji zaktualizowany przepływ pracy i tożsamością zaktualizowany przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-231">If the `WorkflowIdentity` maps to a `v1` workflow instance, a `WorkflowApplication` is configured with the updated workflow definition and an updated workflow identity.</span></span> <span data-ttu-id="27cda-232">Następnie `WorkflowApplication.Load` nosi nazwę wystąpienia i Mapa aktualizacji, która ma zastosowanie mapy aktualizacji dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="27cda-232">Next, `WorkflowApplication.Load` is called with the instance and the update map, which applies the dynamic update map.</span></span> <span data-ttu-id="27cda-233">Po zastosowaniu aktualizacji zaktualizowane wystąpienie jest utrwalone w wyniku wywołania `Unload`.</span><span class="sxs-lookup"><span data-stu-id="27cda-233">Once the update is applied, the updated instance is persisted with a call to `Unload`.</span></span>  
  
    ```vb  
    Dim store = New SqlWorkflowInstanceStore(connectionString)  
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)  
  
    Dim updateMaps As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo) = LoadMaps()  
  
    For Each id As Guid In GetIds()  
        'Get a proxy to the instance.   
        Dim instance As WorkflowApplicationInstance = WorkflowApplication.GetInstance(id, store)  
  
        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity)  
  
        'Only update v1 workflows.  
        If Not instance.DefinitionIdentity Is Nothing AndAlso _  
            instance.DefinitionIdentity.Version.Equals(New Version(1, 0, 0, 0)) Then  
  
            Dim info As DynamicUpdateInfo = updateMaps(instance.DefinitionIdentity)  
  
            'Associate the persisted WorkflowApplicationInstance with  
            'a WorkflowApplication that is configured with the updated  
            'definition and updated WorkflowIdentity.  
            Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity)  
            Dim wfApp = New WorkflowApplication(wf, info.newIdentity)  
  
            'Apply the Dynamic Update.               
            wfApp.Load(instance, info.updateMap)  
  
            'Persist the updated instance.  
            wfApp.Unload()  
  
            Console.WriteLine("Updated to: {0}", info.newIdentity)  
        Else  
            'Not updating this instance, so unload it.  
            instance.Abandon()  
        End If  
    Next  
    ```  
  
    ```csharp  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);  
  
    IDictionary<WorkflowIdentity, DynamicUpdateInfo> updateMaps = LoadMaps();  
  
    foreach (Guid id in GetIds())  
    {  
        // Get a proxy to the instance.   
        WorkflowApplicationInstance instance =  
            WorkflowApplication.GetInstance(id, store);  
  
        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity);  
  
        // Only update v1 workflows.  
        if (instance.DefinitionIdentity != null &&  
            instance.DefinitionIdentity.Version.Equals(new Version(1, 0, 0, 0)))  
        {  
            DynamicUpdateInfo info = updateMaps[instance.DefinitionIdentity];  
  
            // Associate the persisted WorkflowApplicationInstance with  
            // a WorkflowApplication that is configured with the updated  
            // definition and updated WorkflowIdentity.  
            Activity wf = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity);  
            WorkflowApplication wfApp =  
                new WorkflowApplication(wf, info.newIdentity);  
  
            // Apply the Dynamic Update.               
            wfApp.Load(instance, info.updateMap);  
  
            // Persist the updated instance.  
            wfApp.Unload();  
  
            Console.WriteLine("Updated to: {0}", info.newIdentity);  
        }  
        else  
        {  
            // Not updating this instance, so unload it.  
            instance.Abandon();  
        }  
    }  
    ```  
  
20. <span data-ttu-id="27cda-234">Kliknij prawym przyciskiem myszy **ApplyDynamicUpdate** w **Eksploratora rozwiązań** i wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="27cda-234">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
21. <span data-ttu-id="27cda-235">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania, a następnie naciśnij kombinację klawiszy CTRL + F5, aby uruchomić `ApplyDynamicUpdate` aplikacji i zaktualizować wystąpień utrwalonych przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-235">Press CTRL+SHIFT+B to build the solution, and then press CTRL+F5 to run the `ApplyDynamicUpdate` application and update the persisted workflow instances.</span></span> <span data-ttu-id="27cda-236">Powinny pojawić się dane wyjściowe podobne do następującego.</span><span class="sxs-lookup"><span data-stu-id="27cda-236">You should see output similar to the following.</span></span> <span data-ttu-id="27cda-237">Przepływy pracy w wersji 1.0.0.0 są zaktualizowany do wersji 1.5.0.0, gdy wersji 2.0.0.0 przepływy pracy nie zostały zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="27cda-237">The version 1.0.0.0 workflows are updated to version 1.5.0.0, while the version 2.0.0.0 workflows are not updated.</span></span>  
  
 <span data-ttu-id="27cda-238">**Sprawdzanie: StateMachineNumberGuessWorkflow; W wersji = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="27cda-238">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>  
<span data-ttu-id="27cda-239">**Zaktualizowano w celu: StateMachineNumberGuessWorkflow; Wersja = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-239">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="27cda-240">**Sprawdzanie: StateMachineNumberGuessWorkflow; W wersji = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-240">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="27cda-241">**Zaktualizowano w celu: StateMachineNumberGuessWorkflow; Wersja = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-241">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="27cda-242">**Sprawdzanie: FlowchartNumberGuessWorkflow; W wersji = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-242">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="27cda-243">**Zaktualizowano w celu: FlowchartNumberGuessWorkflow; Wersja = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-243">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="27cda-244">**Sprawdzanie: FlowchartNumberGuessWorkflow; W wersji = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-244">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="27cda-245">**Zaktualizowano w celu: FlowchartNumberGuessWorkflow; Wersja = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-245">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="27cda-246">**Sprawdzanie: SequentialNumberGuessWorkflow; W wersji = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-246">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="27cda-247">**Zaktualizowano w celu: SequentialNumberGuessWorkflow; Wersja = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-247">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="27cda-248">**Sprawdzanie: SequentialNumberGuessWorkflow; W wersji = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-248">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="27cda-249">**Zaktualizowano w celu: SequentialNumberGuessWorkflow; Wersja = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-249">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="27cda-250">**Sprawdzanie: SequentialNumberGuessWorkflow; W wersji = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-250">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="27cda-251">**Zaktualizowano w celu: SequentialNumberGuessWorkflow; Wersja = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-251">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="27cda-252">**Sprawdzanie: StateMachineNumberGuessWorkflow; W wersji = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-252">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="27cda-253">**Zaktualizowano w celu: StateMachineNumberGuessWorkflow; Wersja = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-253">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="27cda-254">**Sprawdzanie: FlowchartNumberGuessWorkflow; W wersji = 1.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-254">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0** </span></span>  
<span data-ttu-id="27cda-255">**Zaktualizowano w celu: FlowchartNumberGuessWorkflow; Wersja = 1.5.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-255">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0** </span></span>  
<span data-ttu-id="27cda-256">**Sprawdzanie: StateMachineNumberGuessWorkflow; Wersja = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-256">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="27cda-257">**Sprawdzanie: StateMachineNumberGuessWorkflow; Wersja = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-257">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="27cda-258">**Sprawdzanie: FlowchartNumberGuessWorkflow; Wersja = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-258">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="27cda-259">**Sprawdzanie: FlowchartNumberGuessWorkflow; Wersja = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-259">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="27cda-260">**Sprawdzanie: SequentialNumberGuessWorkflow; Wersja = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-260">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="27cda-261">**Sprawdzanie: SequentialNumberGuessWorkflow; Wersja = 2.0.0.0** </span><span class="sxs-lookup"><span data-stu-id="27cda-261">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0** </span></span>  
<span data-ttu-id="27cda-262">**Naciśnij dowolny klawisz, aby kontynuować...**</span><span class="sxs-lookup"><span data-stu-id="27cda-262">**Press any key to continue . . .**</span></span>  
  
###  <span data-ttu-id="27cda-263"><a name="BKMK_BuildAndRun"></a>Aby uruchomić aplikację zaktualizowane przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="27cda-263"><a name="BKMK_BuildAndRun"></a> To run the application with the updated workflows</span></span>  
  
1.  <span data-ttu-id="27cda-264">Kliknij prawym przyciskiem myszy **NumberGuessWorkflowHost** w **Eksploratora rozwiązań** i wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="27cda-264">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>  
  
2.  <span data-ttu-id="27cda-265">Naciśnij klawisze CTRL + F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="27cda-265">Press CTRL+F5 to run the application.</span></span>  
  
3.  <span data-ttu-id="27cda-266">Kliknij przycisk **nowej gry** można uruchomić nowego przepływu pracy i Zapisz informacje o wersji poniżej okno stanu, która wskazuje przepływu pracy jest `v2` przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-266">Click **New Game** to start a new workflow and note the version information below the status window that indicates the workflow is a `v2` workflow.</span></span>  
  
4.  <span data-ttu-id="27cda-267">Wybierz jedną z `v1` przepływy pracy na początku [porady: wiele wersji hosta przepływu pracy Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="27cda-267">Select one of the `v1` workflows you started at the beginning of the [How to: Host Multiple Versions of a Workflow Side-by-Side](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md) topic.</span></span> <span data-ttu-id="27cda-268">Należy pamiętać, że informacje o wersji w obszarze okno stanu wskazuje, że przepływ pracy jest wersja **1.5.0.0** przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-268">Note that the version information under the status window indicates that the workflow is a version **1.5.0.0** workflow.</span></span> <span data-ttu-id="27cda-269">Należy pamiętać, że nie ma żadnych informacji wskazane o poprzednich prób innych niż czy był zbyt duży lub za mały.</span><span class="sxs-lookup"><span data-stu-id="27cda-269">Note that there is no information indicated about previous guesses other than whether they were too high or too low.</span></span>  
  
 <span data-ttu-id="27cda-270">**Wprowadź liczbę z przedziału od 1 do 10**</span><span class="sxs-lookup"><span data-stu-id="27cda-270">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="27cda-271">**Twoje wynik jest za mała.**</span><span class="sxs-lookup"><span data-stu-id="27cda-271">**Your guess is too low.**</span></span>  
  
5.  <span data-ttu-id="27cda-272">Zanotuj `InstanceId` , a następnie wprowadź liczbę prób do momentu ukończenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-272">Make a note of the `InstanceId` and then enter guesses until the workflow completes.</span></span> <span data-ttu-id="27cda-273">Okno stanu wyświetla informacje o zawartości argumentu, ponieważ `WriteLine` działania zostały zaktualizowane przez aktualizację dynamiczną.</span><span class="sxs-lookup"><span data-stu-id="27cda-273">The status window displays information about the content of the guess because the `WriteLine` activities were updated by the dynamic update.</span></span>  
  
 <span data-ttu-id="27cda-274">**Wprowadź liczbę z przedziału od 1 do 10**</span><span class="sxs-lookup"><span data-stu-id="27cda-274">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="27cda-275">**Twoje wynik jest za mała.** </span><span class="sxs-lookup"><span data-stu-id="27cda-275">**Your guess is too low.** </span></span>  
<span data-ttu-id="27cda-276">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="27cda-276">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="27cda-277">**5 jest zbyt niski.** </span><span class="sxs-lookup"><span data-stu-id="27cda-277">**5 is too low.** </span></span>  
<span data-ttu-id="27cda-278">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="27cda-278">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="27cda-279">**7 jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="27cda-279">**7 is too high.** </span></span>  
<span data-ttu-id="27cda-280">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="27cda-280">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="27cda-281">**Gratulacje, odgadnąć numer w włącza 4.**</span><span class="sxs-lookup"><span data-stu-id="27cda-281">**Congratulations, you guessed the number in 4 turns.**</span></span>  
  
6.  <span data-ttu-id="27cda-282">Otwórz Eksploratora Windows i przejdź do **NumberGuessWorkflowHost\bin\debug** folder (lub **bin\release** w zależności od ustawienia projektu), a następnie otwórz plik śledzenia za pomocą Notatnika, który odpowiada Ukończono przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-282">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="27cda-283">Jeśli nie wprowadzono uwagę `InstanceId` można zidentyfikować przy użyciu pliku śledzenia poprawne **Data modyfikacji** informacji w Eksploratorze Windows.</span><span class="sxs-lookup"><span data-stu-id="27cda-283">If you did not make a note of the `InstanceId` you may be able to identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span> <span data-ttu-id="27cda-284">Informacje o śledzeniu ostatni wiersz zawiera dane wyjściowe nowo dodanego `WriteLine` działania.</span><span class="sxs-lookup"><span data-stu-id="27cda-284">The last line of the tracking information contains the output of the newly added `WriteLine` activity.</span></span>  
  
 <span data-ttu-id="27cda-285">**Wprowadź liczbę z przedziału od 1 do 10**</span><span class="sxs-lookup"><span data-stu-id="27cda-285">**Please enter a number between 1 and 10**</span></span>  
<span data-ttu-id="27cda-286">**Twoje wynik jest za mała.** </span><span class="sxs-lookup"><span data-stu-id="27cda-286">**Your guess is too low.** </span></span>  
<span data-ttu-id="27cda-287">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="27cda-287">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="27cda-288">**5 jest zbyt niski.** </span><span class="sxs-lookup"><span data-stu-id="27cda-288">**5 is too low.** </span></span>  
<span data-ttu-id="27cda-289">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="27cda-289">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="27cda-290">**7 jest zbyt duża.** </span><span class="sxs-lookup"><span data-stu-id="27cda-290">**7 is too high.** </span></span>  
<span data-ttu-id="27cda-291">**Wprowadź liczbę z przedziału od 1 do 10** </span><span class="sxs-lookup"><span data-stu-id="27cda-291">**Please enter a number between 1 and 10** </span></span>  
<span data-ttu-id="27cda-292">**6 jest poprawna. Odgadnięto go w włącza 4.**</span><span class="sxs-lookup"><span data-stu-id="27cda-292">**6 is correct. You guessed it in 4 turns.**</span></span>  
  
###  <span data-ttu-id="27cda-293"><a name="BKMK_StartPreviousVersions"></a>Aby włączyć uruchamianie poprzednich wersji przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="27cda-293"><a name="BKMK_StartPreviousVersions"></a> To enable starting previous versions of the workflows</span></span>  
 <span data-ttu-id="27cda-294">Po uruchomieniu poza przepływy pracy do aktualizacji, można zmodyfikować `NumberGuessWorkflowHost` aplikacji, aby umożliwić uruchamianie poprzednich wersji przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-294">If you run out of workflows to update, you can modify the `NumberGuessWorkflowHost` application to enable starting previous versions of the workflows.</span></span>  
  
1.  <span data-ttu-id="27cda-295">Kliknij dwukrotnie **WorkflowHostForm** w **Eksploratora rozwiązań**i wybierz **WorkflowType** pola kombi.</span><span class="sxs-lookup"><span data-stu-id="27cda-295">Double-click **WorkflowHostForm** in **Solution Explorer**, and select the **WorkflowType** combo box.</span></span>  
  
2.  <span data-ttu-id="27cda-296">W **właściwości** wybierz **elementów** właściwości i kliknij przycisk wielokropka, aby edytować **elementów** kolekcji.</span><span class="sxs-lookup"><span data-stu-id="27cda-296">In the **Properties** window, select the **Items** property and click the ellipsis button to edit the **Items** collection.</span></span>  
  
3.  <span data-ttu-id="27cda-297">Dodaj następujące trzy elementy do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="27cda-297">Add the following three items to the collection.</span></span>  
  
    ```
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
     <span data-ttu-id="27cda-298">Wypełniony `Items` kolekcji będą mieć sześć elementów.</span><span class="sxs-lookup"><span data-stu-id="27cda-298">The completed `Items` collection will have six items.</span></span>  
  
    ```
    StateMachineNumberGuessWorkflow  
    FlowchartNumberGuessWorkflow  
    SequentialNumberGuessWorkflow  
    StateMachineNumberGuessWorkflow v1  
    FlowchartNumberGuessWorkflow v1  
    SequentialNumberGuessWorkflow v1  
    ```  
  
4.  <span data-ttu-id="27cda-299">Kliknij dwukrotnie **WorkflowHostForm** w **Eksploratora rozwiązań**i wybierz **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="27cda-299">Double-click **WorkflowHostForm** in **Solution Explorer**, and select **View Code**.</span></span>  
  
5.  <span data-ttu-id="27cda-300">Dodaj trzy nowych przypadków `switch` (lub `Select Case`) instrukcji w `NewGame_Click` obsługi do mapowania nowych elementów w **WorkflowType** pola kombi do dopasowania tożsamości przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="27cda-300">Add three new cases to the `switch` (or `Select Case`) statement in the `NewGame_Click` handler to map the new items in the **WorkflowType** combo box to the matching workflow identities.</span></span>  
  
    ```vb  
    Case "SequentialNumberGuessWorkflow v1"  
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1  
  
    Case "StateMachineNumberGuessWorkflow v1"  
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1  
  
    Case "FlowchartNumberGuessWorkflow v1"  
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1  
    ```  
  
    ```csharp  
    case "SequentialNumberGuessWorkflow v1":  
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;  
        break;  
  
    case "StateMachineNumberGuessWorkflow v1":  
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;  
        break;  
  
    case "FlowchartNumberGuessWorkflow v1":  
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;  
        break;  
    ```  
  
     <span data-ttu-id="27cda-301">Poniższy przykład zawiera pełną `switch` (lub `Select Case`) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="27cda-301">The following example contains the complete `switch` (or `Select Case`) statement.</span></span>  
  
    ```vb  
    Select Case WorkflowType.SelectedItem.ToString()  
        Case "SequentialNumberGuessWorkflow"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity  
  
        Case "StateMachineNumberGuessWorkflow"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity  
  
        Case "FlowchartNumberGuessWorkflow"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity  
  
        Case "SequentialNumberGuessWorkflow v1"  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1  
  
        Case "StateMachineNumberGuessWorkflow v1"  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1  
  
        Case "FlowchartNumberGuessWorkflow v1"  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1  
    End Select  
    ```  
  
    ```csharp  
    switch (WorkflowType.SelectedItem.ToString())  
    {  
        case "SequentialNumberGuessWorkflow":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;  
            break;  
  
        case "StateMachineNumberGuessWorkflow":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;  
            break;  
  
        case "FlowchartNumberGuessWorkflow":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;  
            break;  
  
        case "SequentialNumberGuessWorkflow v1":  
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;  
            break;  
  
        case "StateMachineNumberGuessWorkflow v1":  
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;  
            break;  
  
        case "FlowchartNumberGuessWorkflow v1":  
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;  
            break;  
    };  
    ```  
  
6.  <span data-ttu-id="27cda-302">Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="27cda-302">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="27cda-303">Można teraz uruchomić `v1` wersji przepływu pracy, jak również w bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="27cda-303">You can now start the `v1` versions of the workflow as well as the current versions.</span></span> <span data-ttu-id="27cda-304">Aby dynamicznie aktualizować te nowe wystąpienia, należy uruchomić **ApplyDynamicUpdate** aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27cda-304">To dynamically update these new instances, run the **ApplyDynamicUpdate** application.</span></span>