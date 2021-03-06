---
title: "TextBox — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d7312246c43157ca9cd6c7b41d2b110586721c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="textbox-control-overview-windows-forms"></a>TextBox — Informacje o formancie [Formularze systemu Windows]
Pola tekstowe formularzy systemu Windows są używane, aby pobrać dane wejściowe użytkownika lub do wyświetlania tekstu. <xref:System.Windows.Forms.TextBox> Kontroli jest zazwyczaj używana do edycji tekstu, mimo że można również on tylko do odczytu. Pola tekstowe można wyświetlać wiele wierszy, zawijać tekst, który ma rozmiar formantu i dodać podstawowe formatowanie. <xref:System.Windows.Forms.TextBox> Kontrola zapewnia styl jeden format tekstu wyświetlane lub wprowadzone w formancie. Aby wyświetlić wiele typów tekst sformatowany, użyj <xref:System.Windows.Forms.RichTextBox> formantu. Aby uzyskać więcej informacji, zobacz [informacje o formancie RichTextBox](../../../../docs/framework/winforms/controls/richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>Praca z formantu TextBox  
 Tekst wyświetlany przez formant znajduje się w <xref:System.Windows.Forms.TextBox.Text%2A> właściwości. Domyślnie możesz wprowadzić maksymalnie 2048 znaków w polu tekstowym. Jeśli ustawisz <xref:System.Windows.Forms.TextBox.Multiline%2A> właściwości `true`, możesz wprowadzić maksymalnie 32 KB tekstu. <xref:System.Windows.Forms.TextBox.Text%2A> Właściwość można ustawić w czasie projektowania, w oknie właściwości w czasie wykonywania w kodzie, lub dane wejściowe użytkownika w czasie wykonywania. W czasie wykonywania można pobrać bieżącą zawartość pola tekstowego odczytując <xref:System.Windows.Forms.TextBox.Text%2A> właściwości.  
  
 Poniższy przykład kodu ustawia tekst w formancie w czasie wykonywania. `InitializeMyControl` Procedury nie będą automatycznie wykonywane; musi zostać wywołana.  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TextBox>  
 [Instrukcje: kontrolowanie punktu wstawiania w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [Instrukcje: tworzenie pola tekstowego hasła za pomocą kontrolki TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [Instrukcje: tworzenie pola tekstowego tylko do odczytu](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [Instrukcje: umieszczanie cudzysłowu w ciągu](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [Instrukcje: zaznaczanie tekstu w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [Instrukcje: wyświetlanie wielu wierszy w kontrolce TextBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [TextBox, kontrolka](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
