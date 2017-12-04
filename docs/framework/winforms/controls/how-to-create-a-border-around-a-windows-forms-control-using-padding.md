---
title: "Porady: tworzenie obramowania wokoło formantu formularzy systemu Windows za pomocą wypełnienia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins
- controls [Windows Forms], Margin property
- padding [Windows Forms], Windows Forms
- controls [Windows Forms], Padding property
- controls [Windows Forms], outlining
- Padding property [Windows Forms]
- margins [Windows Forms], Windows Forms
- Margin property [Windows Forms]
ms.assetid: bac7ed4d-a163-4259-98bd-155a36345890
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 573a27343a15ef12ad955295c3beb3fef9130023
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a><span data-ttu-id="39749-102">Porady: tworzenie obramowania wokoło formantu formularzy systemu Windows za pomocą wypełnienia</span><span class="sxs-lookup"><span data-stu-id="39749-102">How to: Create a Border Around a Windows Forms Control Using Padding</span></span>
<span data-ttu-id="39749-103">W poniższym przykładzie pokazano, jak utworzyć obramowanie lub konspektu wokół <xref:System.Windows.Forms.RichTextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="39749-103">The following code example demonstrates how to create a border or outline around a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="39749-104">W przykładzie wartość <xref:System.Windows.Forms.Panel> formantu <xref:System.Windows.Forms.Padding> 5 i ustawia dla właściwości <xref:System.Windows.Forms.Control.Dock%2A> właściwości podrzędnej <xref:System.Windows.Forms.RichTextBox> formant <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="39749-104">The example sets the value of a <xref:System.Windows.Forms.Panel> control’s <xref:System.Windows.Forms.Padding> property to 5 and sets the <xref:System.Windows.Forms.Control.Dock%2A> property of a child <xref:System.Windows.Forms.RichTextBox> control to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span> <span data-ttu-id="39749-105"><xref:System.Windows.Forms.Control.BackColor%2A> z <xref:System.Windows.Forms.Panel> kontrola jest ustawiona na <xref:System.Drawing.Color.Blue%2A>, co powoduje niebieskie obramowanie wokół <xref:System.Windows.Forms.RichTextBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="39749-105">The <xref:System.Windows.Forms.Control.BackColor%2A> of the <xref:System.Windows.Forms.Panel> control is set to <xref:System.Drawing.Color.Blue%2A>, which creates a blue border around the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39749-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="39749-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.Padding#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="39749-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="39749-107">See Also</span></span>  
 <xref:System.Windows.Forms.Padding>  
 [<span data-ttu-id="39749-108">Margines i wypełnienie w formularzach systemu Windows formantów</span><span class="sxs-lookup"><span data-stu-id="39749-108">Margin and Padding in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/margin-and-padding-in-windows-forms-controls.md)