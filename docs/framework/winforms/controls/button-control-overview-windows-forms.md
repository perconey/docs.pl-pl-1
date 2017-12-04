---
title: Informacje o kontrolce przycisku (Formularze systemu Windows)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff98eb39113a2fa8117d091645ac04526e2983c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="button-control-overview-windows-forms"></a><span data-ttu-id="95ce5-102">Informacje o kontrolce przycisku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="95ce5-102">Button Control Overview (Windows Forms)</span></span>
<span data-ttu-id="95ce5-103">Formularze systemu Windows <xref:System.Windows.Forms.Button> formant umożliwia użytkownikowi kliknij go, aby wykonać akcję.</span><span class="sxs-lookup"><span data-stu-id="95ce5-103">The Windows Forms <xref:System.Windows.Forms.Button> control allows the user to click it to perform an action.</span></span> <span data-ttu-id="95ce5-104">Po kliknięciu przycisku wygląda, jakby trwa spoczywa i wydane.</span><span class="sxs-lookup"><span data-stu-id="95ce5-104">When the button is clicked, it looks as if it is being pushed in and released.</span></span> <span data-ttu-id="95ce5-105">Gdy użytkownik kliknie przycisk <xref:System.Windows.Forms.Control.Click> jest wywoływana procedura obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="95ce5-105">Whenever the user clicks a button, the <xref:System.Windows.Forms.Control.Click> event handler is invoked.</span></span> <span data-ttu-id="95ce5-106">Umieść kod w <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń do wykonywania dowolnych akcji wybierzesz.</span><span class="sxs-lookup"><span data-stu-id="95ce5-106">You place code in the <xref:System.Windows.Forms.Control.Click> event handler to perform any action you choose.</span></span>  
  
 <span data-ttu-id="95ce5-107">Tekst wyświetlany na przycisku zawarty w <xref:System.Windows.Forms.Control.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="95ce5-107">The text displayed on the button is contained in the <xref:System.Windows.Forms.Control.Text%2A> property.</span></span> <span data-ttu-id="95ce5-108">Jeśli tekst jest większa niż szerokość przycisku, będzie zawijany do następnego wiersza.</span><span class="sxs-lookup"><span data-stu-id="95ce5-108">If your text exceeds the width of the button, it will wrap to the next line.</span></span> <span data-ttu-id="95ce5-109">Jednak zostanie obcięta, jeśli formant nie może obsłużyć całkowita wysokość.</span><span class="sxs-lookup"><span data-stu-id="95ce5-109">However, it will be clipped if the control cannot accommodate its overall height.</span></span> <span data-ttu-id="95ce5-110">Aby uzyskać więcej informacji, zobacz [porady: Ustawianie tekst wyświetlany przez formant formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="95ce5-110">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span> <span data-ttu-id="95ce5-111"><xref:System.Windows.Forms.Control.Text%2A> Właściwość może zawierać klucz dostępu, który umożliwia użytkownikowi "kliknij" formantu, naciskając klawisz ALT z kluczem dostępu.</span><span class="sxs-lookup"><span data-stu-id="95ce5-111">The <xref:System.Windows.Forms.Control.Text%2A> property can contain an access key, which allows a user to "click" the control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="95ce5-112">Aby uzyskać więcej informacji, zobacz [porady: tworzenie dostępu do kluczy dla formantów formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span><span class="sxs-lookup"><span data-stu-id="95ce5-112">For details, see [How to: Create Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).</span></span> <span data-ttu-id="95ce5-113">Steruje wyglądem tekst <xref:System.Windows.Forms.Control.Font%2A> właściwości i <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="95ce5-113">The appearance of the text is controlled by the <xref:System.Windows.Forms.Control.Font%2A> property and the <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> property.</span></span>  
  
 <span data-ttu-id="95ce5-114"><xref:System.Windows.Forms.Button> Formant może również wyświetlać obrazów za pomocą <xref:System.Windows.Forms.ButtonBase.Image%2A> i <xref:System.Windows.Forms.ButtonBase.ImageList%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="95ce5-114">The <xref:System.Windows.Forms.Button> control can also display images using the <xref:System.Windows.Forms.ButtonBase.Image%2A> and <xref:System.Windows.Forms.ButtonBase.ImageList%2A> properties.</span></span> <span data-ttu-id="95ce5-115">Aby uzyskać więcej informacji, zobacz [porady: Ustawianie obrazu wyświetlanego przez formantu formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="95ce5-115">For more information, see [How to: Set the Image Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95ce5-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95ce5-116">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="95ce5-117">Porady: odpowiadanie na kliknięcia przycisków formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="95ce5-117">How to: Respond to Windows Forms Button Clicks</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [<span data-ttu-id="95ce5-118">Sposoby wyboru formantu przycisku formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="95ce5-118">Ways to Select a Windows Forms Button Control</span></span>](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [<span data-ttu-id="95ce5-119">Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Akceptuj przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="95ce5-119">How to: Designate a Windows Forms Button as the Accept Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [<span data-ttu-id="95ce5-120">Porady: wyznaczanie przycisku formularzy systemu Windows na przycisk Anuluj przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="95ce5-120">How to: Designate a Windows Forms Button as the Cancel Button Using the Designer</span></span>](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [<span data-ttu-id="95ce5-121">Button — formant</span><span class="sxs-lookup"><span data-stu-id="95ce5-121">Button Control</span></span>](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)