---
title: "Jak zmienić FlowDirection zawartości za pomocą programowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- FlowDirection property [WPF], changing programmatically
- documents [WPF], changing FlowDirection property programmatically
ms.assetid: 02f5a8ba-f8c0-4e5a-84b9-4c5bf12922a2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3670deceb2c06e58d859fae15fbf9ee791819dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-flowdirection-of-content-programmatically"></a>Jak zmienić FlowDirection zawartości za pomocą programowania
W tym przykładzie pokazano, jak programowo zmienić <xref:System.Windows.FrameworkElement.FlowDirection%2A> właściwość <xref:System.Windows.Controls.FlowDocumentReader>.  
  
## <a name="example"></a>Przykład  
 Dwa <xref:System.Windows.Controls.Button> elementy są tworzone, każdy reprezentuje jedną z możliwych wartości <xref:System.Windows.FlowDirection>. Kliknięcie przycisku wartości właściwości skojarzonej, ponieważ jest stosowany do zawartości <xref:System.Windows.Controls.FlowDocumentReader> o nazwie `tf1`.  Wartość właściwości są równocześnie zapisywane w <xref:System.Windows.Controls.TextBlock> o nazwie `txt1`.  
  
 [!code-xaml[FlowDirectionSnippets#_FlowDirectionXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml#_flowdirectionxaml)]  
  
## <a name="example"></a>Przykład  
 Zdarzenia powiązane z kliknięcia przycisków zdefiniowanych powyżej są obsługiwane w [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] pliku CodeBehind.  
  
 [!code-csharp[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDirectionSnippets/CSharp/Window1.xaml.cs#_flowdirection)]
 [!code-vb[FlowDirectionSnippets#_FlowDirection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDirectionSnippets/VisualBasic/Window1.xaml.vb#_flowdirection)]
