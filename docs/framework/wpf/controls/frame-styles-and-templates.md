---
title: Style i szablony klatek
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parts [WPF], Frame
- templates [WPF], Frame
- ControlTemplate [WPF], Frame
- Frame [WPF], styles and templates
- states [WPF], Frame
- styles [WPF], Frame
ms.assetid: a01c32e2-c951-46a0-a82f-2614ca241f0b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 603c4f766b836c7a301cc151112457ddb0972d10
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="frame-styles-and-templates"></a><span data-ttu-id="47566-102">Style i szablony klatek</span><span class="sxs-lookup"><span data-stu-id="47566-102">Frame Styles and Templates</span></span>
<span data-ttu-id="47566-103">W tym temacie opisano, style i szablonów dla <xref:System.Windows.Controls.Frame> formantu.</span><span class="sxs-lookup"><span data-stu-id="47566-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Frame> control.</span></span> <span data-ttu-id="47566-104">Można zmodyfikować domyślne <xref:System.Windows.Controls.ControlTemplate> umożliwiają unikatowego wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="47566-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="47566-105">Aby uzyskać więcej informacji, zobacz [Dostosowywanie wyglądu formant tworząc ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span><span class="sxs-lookup"><span data-stu-id="47566-105">For more information, see [Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).</span></span>  
  
## <a name="frame-parts"></a><span data-ttu-id="47566-106">Części ramki</span><span class="sxs-lookup"><span data-stu-id="47566-106">Frame Parts</span></span>  
 <span data-ttu-id="47566-107">W poniższej tabeli wymieniono nazwanego części dla <xref:System.Windows.Controls.Frame> formantu.</span><span class="sxs-lookup"><span data-stu-id="47566-107">The following table lists the named parts for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="47566-108">Część</span><span class="sxs-lookup"><span data-stu-id="47566-108">Part</span></span>|<span data-ttu-id="47566-109">Typ</span><span class="sxs-lookup"><span data-stu-id="47566-109">Type</span></span>|<span data-ttu-id="47566-110">Opis</span><span class="sxs-lookup"><span data-stu-id="47566-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="47566-111">PART_FrameCP</span><span class="sxs-lookup"><span data-stu-id="47566-111">PART_FrameCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="47566-112">Obszar zawartości.</span><span class="sxs-lookup"><span data-stu-id="47566-112">The content area.</span></span>|  
  
## <a name="frame-states"></a><span data-ttu-id="47566-113">Stany ramek</span><span class="sxs-lookup"><span data-stu-id="47566-113">Frame States</span></span>  
 <span data-ttu-id="47566-114">W poniższej tabeli wymieniono stany wizualne dla <xref:System.Windows.Controls.Frame> formantu.</span><span class="sxs-lookup"><span data-stu-id="47566-114">The following table lists the visual states for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
|<span data-ttu-id="47566-115">Nazwa stanu wizualnego</span><span class="sxs-lookup"><span data-stu-id="47566-115">VisualState Name</span></span>|<span data-ttu-id="47566-116">Nazwa VisualStateGroup</span><span class="sxs-lookup"><span data-stu-id="47566-116">VisualStateGroup Name</span></span>|<span data-ttu-id="47566-117">Opis</span><span class="sxs-lookup"><span data-stu-id="47566-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="47566-118">Prawidłowe</span><span class="sxs-lookup"><span data-stu-id="47566-118">Valid</span></span>|<span data-ttu-id="47566-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="47566-119">ValidationStates</span></span>|<span data-ttu-id="47566-120">Używa kontrolki <xref:System.Windows.Controls.Validation> klasy i <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> jest dołączona właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="47566-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="47566-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="47566-121">InvalidFocused</span></span>|<span data-ttu-id="47566-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="47566-122">ValidationStates</span></span>|<span data-ttu-id="47566-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="47566-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="47566-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="47566-124">InvalidUnfocused</span></span>|<span data-ttu-id="47566-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="47566-125">ValidationStates</span></span>|<span data-ttu-id="47566-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> Jest dołączona właściwość `true` ma formant nie ma fokusa.</span><span class="sxs-lookup"><span data-stu-id="47566-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="frame-controltemplate-example"></a><span data-ttu-id="47566-127">Przykład ControlTemplate ramki</span><span class="sxs-lookup"><span data-stu-id="47566-127">Frame ControlTemplate Example</span></span>  
 <span data-ttu-id="47566-128">Poniższy przykład przedstawia sposób definiowania <xref:System.Windows.Controls.ControlTemplate> dla <xref:System.Windows.Controls.Frame> formantu.</span><span class="sxs-lookup"><span data-stu-id="47566-128">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Frame> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Frame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/frame.xaml#frame)]  
  
 <span data-ttu-id="47566-129">Powyższy przykład korzysta z co najmniej jeden z następujących zasobów.</span><span class="sxs-lookup"><span data-stu-id="47566-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="47566-130">Pełny przykład, zobacz [style próbki ControlTemplates](http://go.microsoft.com/fwlink/?LinkID=160041).</span><span class="sxs-lookup"><span data-stu-id="47566-130">For the complete sample, see [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47566-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47566-131">See Also</span></span>  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [<span data-ttu-id="47566-132">Style formantu i szablony</span><span class="sxs-lookup"><span data-stu-id="47566-132">Control Styles and Templates</span></span>](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [<span data-ttu-id="47566-133">Dostosowywanie formantu</span><span class="sxs-lookup"><span data-stu-id="47566-133">Control Customization</span></span>](../../../../docs/framework/wpf/controls/control-customization.md)  
 [<span data-ttu-id="47566-134">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="47566-134">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="47566-135">Dostosowywanie wyglądu formant tworząc ControlTemplate</span><span class="sxs-lookup"><span data-stu-id="47566-135">Customizing the Appearance of an Existing Control by Creating a ControlTemplate</span></span>](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)