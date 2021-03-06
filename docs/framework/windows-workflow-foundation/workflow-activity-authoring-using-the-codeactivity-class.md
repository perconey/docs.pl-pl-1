---
title: "Za pomocą klasy z typu CodeActivity tworzenia działania przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfe315c1-f86d-43ec-b9ce-2f8c469b1106
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2daec260c1224cd81280c6bf699b70efc2072588
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-activity-authoring-using-the-codeactivity-class"></a>Za pomocą klasy z typu CodeActivity tworzenia działania przepływu pracy
Działania utworzone przez dziedziczenie z <xref:System.Activities.CodeActivity> można zaimplementować podstawowe zachowanie ważnych przez zastąpienie <xref:System.Activities.CodeActivity.Execute%2A> metody.  
  
## <a name="using-codeactivitycontext"></a>Przy użyciu CodeActivityContext  
 Funkcje środowiska uruchomieniowego przepływu pracy są dostępne z poziomu <xref:System.Activities.CodeActivity.Execute%2A> metody przy użyciu elementów członkowskich `context` parametr typu <xref:System.Activities.CodeActivityContext>. Funkcji dostępnych za pośrednictwem <xref:System.Activities.CodeActivityContext> są następujące:  
  
-   Pobieranie i ustawianie wartości zmiennych i argumentów.  
  
-   Funkcje niestandardowe śledzenia przy użyciu <xref:System.Activities.CodeActivityContext.Track%2A>.  
  
-   Dostęp do właściwości wykonania działania za pomocą <xref:System.Activities.CodeActivityContext.GetProperty%2A>.  
  
#### <a name="to-create-a-custom-activity-that-inherits-from-codeactivity"></a>Aby utworzyć niestandardowe działania, który dziedziczy z typu CodeActivity  
  
1.  Otwórz[!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Wybierz **pliku**, **nowe**, a następnie **projektu**. Wybierz **Workflow 4.0** w obszarze **Visual C#** w **typów projektów** okna, a następnie wybierz **v2010** węzła. Wybierz **Biblioteka działań** w **szablony** okna. Nazwa nowego projektu HelloActivity.  
  
3.  Kliknij prawym przyciskiem myszy Activity1.xaml w projekcie HelloActivity i wybierz **usunąć**.  
  
4.  Kliknij prawym przyciskiem myszy projekt HelloActivity i wybierz **Dodaj** , a następnie **klasy**. Nazwa nowej klasy HelloActivity.cs.  
  
5.  W pliku HelloActivity.cs, Dodaj następujący `using` dyrektywy.  
  
    ```csharp  
    using System.Activities;  
    using System.Activities.Statements;  
    ```  
  
6.  Upewnij się nowa klasa dziedziczy <xref:System.Activities.CodeActivity> przez dodanie klasy podstawowej deklaracji klasy.  
  
    ```csharp  
    class HelloActivity : CodeActivity  
    ```  
  
7.  Dodawanie funkcji do klasy, dodając <xref:System.Activities.CodeActivity.Execute%2A> metody.  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
    }  
    ```  
  
8.  Użyj <xref:System.Activities.CodeActivityContext> Aby utworzyć rekord śledzenia.  
  
    ```csharp  
    protected override void Execute(CodeActivityContext context)  
    {  
        Console.WriteLine("Hello World!");  
        CustomTrackingRecord record = new CustomTrackingRecord("MyRecord");  
        record.Data.Add(new KeyValuePair<String, Object>("ExecutionTime", DateTime.Now));  
        context.Track(record);  
    }  
    ```
