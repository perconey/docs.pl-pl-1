---
title: "Porady: dodawanie kolumn do formantu ListView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7223fc47c885b7e659b9bab00c276759410d2567
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Porady: dodawanie kolumn do formantu ListView formularzy systemu Windows przy użyciu narzędzia Projektant
Formularze systemu Windows <xref:System.Windows.Forms.ListView> formant może wyświetlać wiele kolumn dla każdej listy elementów w **szczegóły** widoku. Kolumny służy do wyświetlania kilka typów informacji na temat każdego elementu listy. Na przykład można wyświetlić listę plików, nazwy pliku, typu pliku, rozmiar i datę ostatniej modyfikacji pliku. Informacji o wprowadzaniu kolumny po ich utworzeniu można zobaczyć [porady: wyświetlanie podelementów w kolumnach za pomocą formantu ListView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.ListView> formantu. Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-add-columns-in-the-designer"></a>Aby dodać kolumny w Projektancie  
  
1.  W **właściwości** okna, ustaw dla formantu <xref:System.Windows.Forms.ListView.View%2A> właściwości <xref:System.Windows.Forms.View.Details>.  
  
2.  W **właściwości** okna, kliknij przycisk **wielokropka** przycisk (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) obok pozycji <xref:System.Windows.Forms.ListView.Columns%2A> właściwości.  
  
     **Edytora kolekcji ColumnHeader** pojawi się.  
  
3.  Użyj **Dodaj** przycisk, aby dodać nowe kolumny. Następnie można wybrać nagłówek kolumny i Ustaw tekst (podpis kolumny), wyrównanie tekstu i szerokość.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje o formancie ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Porady: Dodawanie i usuwanie elementów za pomocą systemu Windows formantu ListView formularzy](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Porady: wyświetlanie podelementów w kolumnach z systemu Windows formantu ListView formularzy](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [Porady: wyświetlanie ikon dla formantu ListView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Porady: Dodawanie niestandardowych informacji do formantu TreeView lub ListView (formularze systemu Windows)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)