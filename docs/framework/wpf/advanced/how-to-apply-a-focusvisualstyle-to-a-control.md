---
title: "Jak zastosować FocusVisualStyle do formantu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f614e244293d08cd836edaf82496ca9e7b51423e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a><span data-ttu-id="58af1-102">Jak zastosować FocusVisualStyle do formantu</span><span class="sxs-lookup"><span data-stu-id="58af1-102">How to: Apply a FocusVisualStyle to a Control</span></span>
<span data-ttu-id="58af1-103">W tym przykładzie przedstawiono sposób tworzenia stylu wizualnego fokusu w zasobach i zastosować go do formantu, za pomocą <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="58af1-103">This example shows you how to create a focus visual style in resources and apply the style to a control, using the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58af1-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="58af1-104">Example</span></span>  
 <span data-ttu-id="58af1-105">W poniższym przykładzie zdefiniowano styl, który tworzy dodatkową kontrolę składania, które tylko wtedy, gdy formant jest klawiatury w [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="58af1-105">The following example defines a style that creates additional control compositing that only applies when that control is keyboard focused in the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)].</span></span> <span data-ttu-id="58af1-106">Jest to osiągane przez definiowanie styl o <xref:System.Windows.Controls.ControlTemplate>, a następnie odwołuje się do tego stylu jako zasób podczas ustawiania <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="58af1-106">This is accomplished by defining a style with a <xref:System.Windows.Controls.ControlTemplate>, then referencing that style as a resource when setting the <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> property.</span></span>  
  
 <span data-ttu-id="58af1-107">Prostokąt zewnętrznych przypominającą obramowanie znajduje się poza prostokątnym obszarem.</span><span class="sxs-lookup"><span data-stu-id="58af1-107">An external rectangle resembling a border is placed outside of the rectangular area.</span></span> <span data-ttu-id="58af1-108">Chyba, że zmodyfikowany, rozmiar styl używa <xref:System.Windows.FrameworkElement.ActualHeight%2A> i <xref:System.Windows.FrameworkElement.ActualWidth%2A> prostokątny formantu, których stosowane jest stylu wizualnego fokus.</span><span class="sxs-lookup"><span data-stu-id="58af1-108">Unless otherwise modified, the sizing of the style uses the <xref:System.Windows.FrameworkElement.ActualHeight%2A> and <xref:System.Windows.FrameworkElement.ActualWidth%2A> of the rectangular control where the focus visual style is applied.</span></span> <span data-ttu-id="58af1-109">W tym przykładzie wartości ujemnych dla <xref:System.Windows.FrameworkElement.Margin%2A> aby pojawiają się nieco poza kontrolą ukierunkowanych obramowanie.</span><span class="sxs-lookup"><span data-stu-id="58af1-109">This example sets negative values for the <xref:System.Windows.FrameworkElement.Margin%2A> to make the border appear slightly outside the focused control.</span></span>  
  
 [!code-xaml[FEFocusVisualStyle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 <span data-ttu-id="58af1-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> jest dodatek do stylu szablonu żadnych kontroli, wchodzącej z jawnym styl lub style kompozycji; podstawowy styl formantu nadal można utworzyć przy użyciu <xref:System.Windows.Controls.ControlTemplate> i ustawienie stylu <xref:System.Windows.FrameworkElement.Style%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="58af1-110">A <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A> is additive to any control template style that comes either from an explicit style or a theme style; the primary style for a control can still be created by using a <xref:System.Windows.Controls.ControlTemplate> and setting that style to the <xref:System.Windows.FrameworkElement.Style%2A> property.</span></span>  
  
 <span data-ttu-id="58af1-111">Fokus style wizualne powinien być używany spójnie motyw lub interfejsu użytkownika, zamiast użyć innego dla każdego elementu focusable.</span><span class="sxs-lookup"><span data-stu-id="58af1-111">Focus visual styles should be used consistently across a theme or a UI, rather than using a different one for each focusable element.</span></span> <span data-ttu-id="58af1-112">Aby uzyskać więcej informacji, zobacz [style dla zespołu w formantach i FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).</span><span class="sxs-lookup"><span data-stu-id="58af1-112">For details, see [Styling for Focus in Controls, and FocusVisualStyle](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58af1-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58af1-113">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>  
 [<span data-ttu-id="58af1-114">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="58af1-114">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="58af1-115">Style dla zespołu w formantach i FocusVisualStyle</span><span class="sxs-lookup"><span data-stu-id="58af1-115">Styling for Focus in Controls, and FocusVisualStyle</span></span>](../../../../docs/framework/wpf/advanced/styling-for-focus-in-controls-and-focusvisualstyle.md)