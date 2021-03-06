---
title: "Wskazówki: hosing zawartości Direct3D9 w WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5ad6ac99a77e3477499a871e269cc7faa7a59f12
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a>Wskazówki: hosing zawartości Direct3D9 w WPF
W tym przewodniku pokazano, jak udostępnić zawartość Direct3D9 w aplikacji Windows Presentation Foundation (WPF).  
  
 W tym przewodniku należy wykonać następujące zadania:  
  
-   Utwórz projekt WPF do hostowania zawartości Direct3D9.  
  
-   Importuj zawartość Direct3D9.  
  
-   Wyświetl zawartość Direct3D9 przy użyciu <xref:System.Windows.Interop.D3DImage> klasy.  
  
 Po ukończeniu będzie wiadomo, jak udostępniać zawartość Direct3D9 w aplikacji WPF.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)].  
  
-   Program DirectX SDK 9 lub nowszy.  
  
-   Biblioteki DLL zawierającej Direct3D9 zawartość w formacie zgodnym z WPF. Aby uzyskać więcej informacji, zobacz [WPF i współdziałanie Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) i [wskazówki: tworzenie zawartości Direct3D9 dla hostingu na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).  
  
## <a name="creating-the-wpf-project"></a>Tworzenie projektu WPF  
 Pierwszym krokiem jest utworzenie projektu aplikacji WPF.  
  
#### <a name="to-create-the-wpf-project"></a>Aby utworzyć projekt WPF  
  
-   Utwórz nowy projekt aplikacji WPF języka Visual C# o nazwie `D3DHost`. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](http://msdn.microsoft.com/library/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).  
  
     Otwiera MainWindow.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].  
  
## <a name="importing-the-direct3d9-content"></a>Importowanie zawartości Direct3D9  
 Możesz zaimportować zawartość Direct3D9 niezarządzanej dll przy użyciu `DllImport` atrybutu.  
  
#### <a name="to-import-direct3d9-content"></a>Aby zaimportować zawartość Direct3D9  
  
1.  Otwórz MainWindow.xaml.cs w edytorze kodu.  
  
2.  Zastąp następujący kod automatycznie wygenerowanego kodu.  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a>Hostowanie zawartości Direct3D9  
 Na koniec użyj <xref:System.Windows.Interop.D3DImage> klasy obsługujące zawartość Direct3D9.  
  
#### <a name="to-host-the-direct3d9-content"></a>Aby udostępnić zawartość Direct3D9  
  
1.  W MainWindow.xaml Zamień następujące XAML XAML wygenerowanej automatycznie.  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  Skompiluj projekt.  
  
3.  Skopiuj biblioteki DLL zawierającej Direct3D9 zawartość do folderu bin/Debug.  
  
4.  Naciśnij klawisz F5, aby uruchomić projekt.  
  
     Zawartość Direct3D9 jest wyświetlana w aplikacji WPF.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Interop.D3DImage>  
 [Zagadnienia dotyczące współdziałania Direct3D9 i WPF](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)
