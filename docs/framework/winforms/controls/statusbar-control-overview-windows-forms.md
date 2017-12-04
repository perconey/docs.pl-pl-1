---
title: "StatusBar — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9c26463fae5beca23026a71dd83b19bf3eb52875
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="statusbar-control-overview-windows-forms"></a><span data-ttu-id="8e6c7-102">StatusBar — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="8e6c7-102">StatusBar Control Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="8e6c7-103"><xref:System.Windows.Forms.StatusStrip> i <xref:System.Windows.Forms.ToolStripStatusLabel> formanty Zastąp oraz dodawać funkcje do <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> steruje; jednak <xref:System.Windows.Forms.StatusBar> i <xref:System.Windows.Forms.StatusBarPanel> formanty są zachowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli możesz Wybierz.</span><span class="sxs-lookup"><span data-stu-id="8e6c7-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="8e6c7-104">Formularze systemu Windows [formantu StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) jest używany w formularzach jako obszaru, zwykle wyświetlane w dolnej części okna, w którym aplikacja może wyświetlać różne rodzaje informacji o stanie.</span><span class="sxs-lookup"><span data-stu-id="8e6c7-104">The Windows Forms [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) is used on forms as an area, usually displayed at the bottom of a window, in which an application can display various kinds of status information.</span></span> <span data-ttu-id="8e6c7-105"><xref:System.Windows.Forms.StatusBar>Formanty mogą mieć paneli paska stanu na nich zawierające tekst lub ikony, aby wskazać, stanu lub serii ikon animacji, które wskazują, czy proces działa; na przykład [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] wskazujący, że dokument jest zapisywany.</span><span class="sxs-lookup"><span data-stu-id="8e6c7-105"><xref:System.Windows.Forms.StatusBar> controls can have status bar panels on them that display text or icons to indicate state, or a series of icons in an animation that indicate a process is working; for example, [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] indicating that the document is being saved.</span></span>  
  
## <a name="using-the-statusbar-control"></a><span data-ttu-id="8e6c7-106">Używanie formantu StatusBar</span><span class="sxs-lookup"><span data-stu-id="8e6c7-106">Using the StatusBar Control</span></span>  
 <span data-ttu-id="8e6c7-107">Program Internet Explorer używa paska stanu w celu wskazywać adres URL strony, gdy wskaźnik myszy jest przesuwany nad hiperłącze. [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] dostarcza informacji o lokalizacji strony, lokalizacji sekcji i tryby, takie jak zastępowania i śledzenie; poprawek edycji i [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] używa zapewniające informacje kontekstowe, takich jak informujący sposobu modyfikowania dokującego paska stanu System Windows jako zadokowanych lub zmiennoprzecinkową.</span><span class="sxs-lookup"><span data-stu-id="8e6c7-107">Internet Explorer uses a status bar to indicate the URL of a page when the mouse rolls over the hyperlink; [!INCLUDE[ofprword](../../../../includes/ofprword-md.md)] gives you information on page location, section location, and editing modes such as overtype and revision tracking; and [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] uses the status bar to give context-sensitive information, such as telling you how to manipulate dockable windows as either docked or floating.</span></span>  
  
 <span data-ttu-id="8e6c7-108">Pojedynczym komunikacie można wyświetlić na pasku stanu, ustawiając <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwości `false` (ustawienie domyślne) i ustawienie <xref:System.Windows.Forms.StatusBar.Text%2A> właściwości paska stanu tekst, który ma być wyświetlany w pasku stanu.</span><span class="sxs-lookup"><span data-stu-id="8e6c7-108">You can display a single message on the status bar by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `false` (the default) and setting the <xref:System.Windows.Forms.StatusBar.Text%2A> property of the status bar to the text you want to appear in the status bar.</span></span> <span data-ttu-id="8e6c7-109">Pasek stanu można podzielić na panele, aby wyświetlić więcej niż jeden typ informacji przez ustawienie <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> właściwości `true` i przy użyciu <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> metody <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span><span class="sxs-lookup"><span data-stu-id="8e6c7-109">You can divide the status bar into panels to display more than one type of information by setting the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true` and using the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> method of <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e6c7-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e6c7-110">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="8e6c7-111">Porady: Określanie, które panelu w formancie StatusBar formularzy systemu Windows został kliknięty</span><span class="sxs-lookup"><span data-stu-id="8e6c7-111">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)