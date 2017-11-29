---
title: "Porady: Generowanie modelu i mapowania plików za pomocą EdmGen.exe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 741da2e7f69d5f8fa54f07046d88fec9cf722dbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Porady: Generowanie modelu i mapowania plików za pomocą EdmGen.exe
W tym temacie pokazano, jak korzystać z narzędzia generatora EDM (EdmGen.exe) do generowania następujące pliki na podstawie bazy danych służbowych:  
  
-   Model koncepcyjny (plik .csdl).  
  
-   Model magazynu (plik ssdl).  
  
-   Mapowanie między modele koncepcyjne i magazynu (pliku MSL).  
  
-   Warstwy obiektu kodu w języku Visual Basic lub C#.  
  
-   Wyświetlanie plików.  
  
 Narzędzie EdmGen.exe używa /mode:FullGeneration generuje pliki wymienione powyżej. Aby uzyskać więcej informacji na temat polecenia EdmGen.exe, zobacz [Generator EDM (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 Jeśli używasz EdmGen.exe do generowania modelu i mapowania plików, nadal należy skonfigurować Twoje [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] projektu do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Aby uzyskać więcej informacji, zobacz [porady: ręczne konfigurowanie projektu programu Entity Framework](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Model koncepcyjny generowane przez EdmGen.exe obejmuje wszystkie obiekty w bazie danych. Jeśli chcesz wygenerować model koncepcyjny, która obejmuje tylko konkretne obiekty, użyj Kreatora modelu danych jednostki. Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreatora modelu danych jednostki](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Aby wygenerować model służbowych przy użyciu EdmGen.exe projektu Visual Basic  
  
1.  Utwórz bazę danych służbowych. Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych służbowych](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Aby wygenerować model służbowe dla projektu C# za pomocą EdmGen.exe  
  
1.  Utwórz bazę danych służbowych. Aby uzyskać więcej informacji, zobacz [tworzenie przykładowej bazy danych służbowych](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  W wierszu polecenia Uruchom następujące polecenie bez podziałów wierszy:  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Mapowanie i modelowania](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Porady: ręczne konfigurowanie projektu programu Entity Framework](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [Porady: wstępnego wygenerowania widoków, aby poprawić wydajność zapytań](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [Porady: używanie EdmGen.exe do walidacji modelu i mapowania plików](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)