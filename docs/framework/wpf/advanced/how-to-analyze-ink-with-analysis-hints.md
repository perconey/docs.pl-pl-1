---
title: "Jak analizować atrament za pomocą wskazówek analizy"
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
- ink [WPF], analyzing
- analyzing ink [WPF]
- ink [WPF], AnalysisHintNode objects [WPF]
- AnalysisHintNode objects [WPF]
ms.assetid: d4421ed4-77f5-4640-829e-9f1de50b2ff2
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b97f7fe0314b6bf839e4e639e32a48f9261def73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-analyze-ink-with-analysis-hints"></a>Jak analizować atrament za pomocą wskazówek analizy
[System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) udostępnia wskazówkę dla [System.Windows.Ink.InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) do której jest dołączona.  Wskazówka ma zastosowanie do obszaru określonego przez [System.Windows.Ink.ContextNode.Location%2A](https://msdn.microsoft.com/library/system.windows.ink.contextnode.location(v=vs.100).aspx) właściwość [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) i zawiera dodatkowy kontekst do analizatora pismo odręczne na zwiększyć dokładność rozpoznawania. [System.Windows.Ink.InkAnalyzer](https://msdn.microsoft.com/library/system.windows.ink.inkanalyzer(v=vs.100).aspx) zastosowanie tego informacje o kontekście podczas analizowania odręczne uzyskane z wewnątrz obszaru wskazówki.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład dotyczy aplikacji, która używa wielu [System.Windows.Ink.AnalysisHintNode](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode(v=vs.100).aspx) obiekty formularza, który akceptuje odręczne. Aplikacja używa [System.Windows.Ink.AnalysisHintNode.Factoid%2A](https://msdn.microsoft.com/library/system.windows.ink.analysishintnode.factoid(v=vs.100)) właściwość, aby podać informacje o kontekście dla każdego wpisu w formularzu.  Aplikacja używa analizy w tle w celu analizowania pismo odręczne i czyści formę odręczne wszystkich pięciu sekund po przesunięciu Dodawanie odręczne.  
  
 [!code-xaml[HowToAnalyzeInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml#1)]  
  
 [!code-csharp[HowToAnalyzeInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAnalyzeInk/CSharp/FormAnalyzer.xaml.cs#2)]
 [!code-vb[HowToAnalyzeInk#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HowToAnalyzeInk/VisualBasic/FormAnalyzer.xaml.vb#2)]
