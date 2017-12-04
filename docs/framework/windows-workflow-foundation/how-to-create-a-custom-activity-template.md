---
title: "Porady: Tworzenie szablonu niestandardowego działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ae81b96a348712af58c5e8527f0f04a59689368
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="51478-102">Porady: Tworzenie szablonu niestandardowego działania</span><span class="sxs-lookup"><span data-stu-id="51478-102">How to: Create a Custom Activity Template</span></span>
<span data-ttu-id="51478-103">Szablony niestandardowe działania są używane do dostosowywania konfiguracji działania, w tym niestandardowych działań złożonych, dzięki czemu użytkownicy nie mają utworzyć każde działanie oddzielnie i skonfigurować ich właściwości i inne ustawienia ręcznie.</span><span class="sxs-lookup"><span data-stu-id="51478-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="51478-104">Te szablony niestandardowe mogą być udostępniane w **przybornika** na [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] lub przy użyciu projektanta rehosted, z którego użytkownicy mogą przeciągnij je na powierzchnię projektu wstępnie skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="51478-104">These custom templates can be made available in the **Toolbox** on the [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]<span data-ttu-id="51478-105">jest dostarczany z dobrym przykładem takich szablonów: [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) i [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) w [wiadomości projektantów działań](/visualstudio/workflow-designer/messaging-activity-designers) kategorii.</span><span class="sxs-lookup"><span data-stu-id="51478-105"> ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>  
  
 <span data-ttu-id="51478-106">Pierwsza procedura w tym temacie opisano sposób tworzenia szablonu działań niestandardowych do **opóźnienie** działania, a druga procedura krótko opisano sposób udostępnić go w [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] Aby sprawdzić, czy działa szablonu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="51478-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] to verify that the custom template works.</span></span>  
  
 <span data-ttu-id="51478-107">Szablony niestandardowe działania musi implementować <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span><span class="sxs-lookup"><span data-stu-id="51478-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="51478-108">Interfejs ma jeden <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> metody tworzenia i konfigurowania wystąpienia działania używane w szablonie.</span><span class="sxs-lookup"><span data-stu-id="51478-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>  
  
### <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="51478-109">Aby utworzyć szablon działania opóźnienia</span><span class="sxs-lookup"><span data-stu-id="51478-109">To create a template for the Delay activity</span></span>  
  
1.  <span data-ttu-id="51478-110">Uruchom [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="51478-110">Start [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="51478-111">Na **pliku** menu wskaż **nowy**, a następnie wybierz **projektu**.</span><span class="sxs-lookup"><span data-stu-id="51478-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>  
  
     <span data-ttu-id="51478-112">**Nowy projekt** zostanie otwarte okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="51478-112">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="51478-113">W **typów projektów** okienku wybierz **przepływu pracy** z jednej **Visual C#** projektów lub **Visual Basic** grupowania w zależności od sieci Preferencje językowe.</span><span class="sxs-lookup"><span data-stu-id="51478-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>  
  
4.  <span data-ttu-id="51478-114">W **szablony** okienku wybierz **Biblioteka działań**.</span><span class="sxs-lookup"><span data-stu-id="51478-114">In the **Templates** pane, select **Activity Library**.</span></span>  
  
5.  <span data-ttu-id="51478-115">W **nazwa** wprowadź `DelayActivityTemplate`.</span><span class="sxs-lookup"><span data-stu-id="51478-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>  
  
6.  <span data-ttu-id="51478-116">Zaakceptuj ustawienia domyślne w **lokalizacji** i **Nazwa rozwiązania** pola tekstowe, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="51478-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="51478-117">Kliknij prawym przyciskiem myszy katalogu odwołania projektu DelayActivityTemplate w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj odwołanie** otworzyć **Dodaj odwołanie** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="51478-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
8.  <span data-ttu-id="51478-118">Przejdź do **.NET** i wybierz **PresentationFramework** z **nazwa składnika** kolumnę po lewej i kliknij przycisk **OK** można dodać odwołania w pliku PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="51478-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>  
  
9. <span data-ttu-id="51478-119">Powtórz tę procedurę, aby dodać odwołania do plików WindowsBase.dll i System.Activities.Presentation.dll.</span><span class="sxs-lookup"><span data-stu-id="51478-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>  
  
10. <span data-ttu-id="51478-120">Kliknij prawym przyciskiem myszy projekt DelayActivityTemplate w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** , a następnie **nowy element** otworzyć **Dodaj nowy element**okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="51478-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>  
  
11. <span data-ttu-id="51478-121">Wybierz **klasy** szablonu, nadaj jej nazwę MyDelayTemplate, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="51478-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="51478-122">Otwórz plik MyDelayTemplate.cs i dodaj następujące instrukcje.</span><span class="sxs-lookup"><span data-stu-id="51478-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>  
  
    ```  
    //Namespaces added  
    using System.Activities;  
    using System.Activities.Statements;  
    using System.Activities.Presentation;  
    using System.Windows;  
    ```  
  
13. <span data-ttu-id="51478-123">Implementowanie <xref:System.Activities.Presentation.IActivityTemplateFactory> z `MyDelayActivity` klasy następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="51478-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="51478-124">Spowoduje to skonfigurowanie opóźnienia na czas trwania 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="51478-124">This configures the delay to have a duration of 10 seconds.</span></span>  
  
    ```  
    public sealed class MyDelayActivity : IActivityTemplateFactory  
    {  
        public Activity Create(System.Windows.DependencyObject target)  
        {  
            return new System.Activities.Statements.Delay  
            {  
                DisplayName = "DelayActivityTemplate",  
                Duration = new TimeSpan(0, 0, 10)  
  
            };  
        }  
    }  
    ```  
  
14. <span data-ttu-id="51478-125">Wybierz **Kompiluj rozwiązanie** z **kompilacji** menu, aby wygenerować plik DelayActivityTemplate.dll.</span><span class="sxs-lookup"><span data-stu-id="51478-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>  
  
### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="51478-126">Aby udostępnić szablon w Projektancie przepływów pracy</span><span class="sxs-lookup"><span data-stu-id="51478-126">To make the template available in a Workflow Designer</span></span>  
  
1.  <span data-ttu-id="51478-127">Kliknij prawym przyciskiem myszy rozwiązanie DelayActivityTemplate w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** , a następnie **nowy projekt** otworzyć **Dodawanie nowego projektu** okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="51478-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>  
  
2.  <span data-ttu-id="51478-128">Wybierz **Aplikacja konsoli przepływu pracy** szablonu, nadaj jej nazwę `CustomActivityTemplateApp`, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="51478-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="51478-129">Kliknij prawym przyciskiem myszy katalogu odwołania projektu CustomActivityTemplateApp w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj odwołanie** otworzyć **Dodaj odwołanie** okna dialogowego pole.</span><span class="sxs-lookup"><span data-stu-id="51478-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>  
  
4.  <span data-ttu-id="51478-130">Przejdź do **projekty** i wybierz **DelayActivityTemplate** z **Nazwa projektu** kolumnę po lewej i kliknij przycisk **OK** do dodania Odwołanie do pliku DelayActivityTemplate.dll utworzonego w ramach pierwszej procedury.</span><span class="sxs-lookup"><span data-stu-id="51478-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>  
  
5.  <span data-ttu-id="51478-131">Kliknij prawym przyciskiem myszy projekt CustomActivityTemplateApp w **Eksploratora rozwiązań** i wybierz polecenie **kompilacji** do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51478-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>  
  
6.  <span data-ttu-id="51478-132">Kliknij prawym przyciskiem myszy projekt CustomActivityTemplateApp w **Eksploratora rozwiązań** i wybierz polecenie **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="51478-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>  
  
7.  <span data-ttu-id="51478-133">Wybierz **uruchomić bez debugowania** z **debugowania** menu i naciśnij dowolny klawisz, aby kontynuować po wyświetleniu monitu z okna cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="51478-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>  
  
8.  <span data-ttu-id="51478-134">Otwórz plik Workflow1.xaml a **przybornika**.</span><span class="sxs-lookup"><span data-stu-id="51478-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>  
  
9. <span data-ttu-id="51478-135">Zlokalizuj **MyDelayActivity** szablonu w **DelayActivityTemplate** kategorii.</span><span class="sxs-lookup"><span data-stu-id="51478-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="51478-136">Przeciągnij go na powierzchnię projektu.</span><span class="sxs-lookup"><span data-stu-id="51478-136">Drag it onto the design surface.</span></span> <span data-ttu-id="51478-137">Upewnij się, w **właściwości** okna który `Duration` właściwość została ustawiona na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="51478-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51478-138">Przykład</span><span class="sxs-lookup"><span data-stu-id="51478-138">Example</span></span>  
 <span data-ttu-id="51478-139">Plik MyDelayActivity.cs powinien zawierać następujący kod.</span><span class="sxs-lookup"><span data-stu-id="51478-139">The MyDelayActivity.cs file should contain the following code.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
//Namespaces added  
using System.Activities;  
using System.Activities.Statements;  
using System.Activities.Presentation;  
using System.Windows;  
  
namespace DelayActivityTemplate  
{  
    public sealed class MyDelayActivity : IActivityTemplateFactory  
    {  
        public Activity Create(System.Windows.DependencyObject target)  
        {  
            return new System.Activities.Statements.Delay  
            {  
                DisplayName = "DelayActivityTemplate",  
                Duration = new TimeSpan(0, 0, 10)  
  
            };  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="51478-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51478-140">See Also</span></span>  
 <xref:System.Activities.Presentation.IActivityTemplateFactory>  
 [<span data-ttu-id="51478-141">Dostosowywanie projektu przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="51478-141">Customizing the Workflow Design Experience</span></span>](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md)