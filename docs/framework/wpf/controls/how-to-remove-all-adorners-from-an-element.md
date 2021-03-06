---
title: "Jak usunąć wszystkie moduły definiowania układów z elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f7bb16c2cd641579706609ff14ca16cc57bd620
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-remove-all-adorners-from-an-element"></a>Jak usunąć wszystkie moduły definiowania układów z elementu
W tym przykładzie pokazano, jak programowane usuwanie wszystkich modułu definiowania układu kodu z określonej <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie kodu verbose powoduje usunięcie wszystkich modułów definiowania układu w tablicy definiowania układu zwrócony przez <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>.  W tym przykładzie stanie się pobrać modułu definiowania układu kodu na <xref:System.Windows.UIElement> o nazwie *myTextBox*.  Jeśli element określony w wywołaniu <xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A> nie ma takich modułów, `null` jest zwracany.  Ten kod jawnie sprawdza tablicy o wartości null i jest najbardziej odpowiednie dla aplikacji, gdzie powinien być stosunkowo wspólnej tablicy o wartości null.  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a>Przykład  
 W tym przykładzie kodu skrócone jest funkcjonalnym odpowiednikiem pełne przykładzie przedstawionym powyżej. Ten kod nie sprawdza jawnie dla tablicy o wartości null, więc istnieje możliwość, że <xref:System.NullReferenceException> może zostać zgłoszony wyjątek.  Ten kod jest najbardziej odpowiednie dla aplikacji, gdzie powinien być rzadko tablicy o wartości null.  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a>Zobacz też  
 [Moduły indeksowania układu — omówienie](../../../../docs/framework/wpf/controls/adorners-overview.md)
