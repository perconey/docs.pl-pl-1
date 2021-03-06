---
title: "Jak animować obiekt na ścieżce (animacja punktu)"
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
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399d6b8028b8715f38335089a723707657df4a98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a>Jak animować obiekt na ścieżce (animacja punktu)
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.PointAnimationUsingPath> obiektu do animowania <xref:System.Windows.Point> wzdłuż ścieżki.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie <xref:System.Windows.Media.EllipseGeometry> wzdłuż ścieżki zdefiniowane przez <xref:System.Windows.Media.PathGeometry>. Geometria elipsy <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwość, która przyjmuje <xref:System.Windows.Point> wartość, określa jej położenie; Przenieś geometrii elipsy, możesz Animacja jego <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwości. W przykładzie użyto <xref:System.Windows.Media.Animation.PointAnimationUsingPath> do animowania <xref:System.Windows.Media.EllipseGeometry> obiektu <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwości.  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 Pełny przykład, zobacz [próbki animacji ścieżki](http://go.microsoft.com/fwlink/?LinkID=160028).  
  
 Wersja kodu powyższego przykładu używane <xref:System.Windows.Media.Animation.Storyboard> do animowania <xref:System.Windows.Media.EllipseGeometry>, mimo że tylko jeden animacja została zastosowana. A <xref:System.Windows.Media.Animation.Storyboard> jest często Najłatwiejszym sposobem zastosować wielu animacji, ponieważ te animacje mogą być kontrolowane przez ten sam <xref:System.Windows.Media.Animation.Storyboard>. Jednak prostsze dotyczą jednej animacji właściwość przy użyciu kodu jest użycie <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody. Na przykład zobacz [animowania właściwości bez Using scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ścieżka animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [Animacja — przegląd](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animacja ścieżki — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
