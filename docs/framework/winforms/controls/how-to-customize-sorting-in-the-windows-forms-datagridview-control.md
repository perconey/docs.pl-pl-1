---
title: 'Porady: dostosowywanie sortowania w formancie DataGridView formularzy systemu Windows'
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
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1fd70aea1dec618a324d271d5bab34ac58ce85a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Porady: dostosowywanie sortowania w formancie DataGridView formularzy systemu Windows
<xref:System.Windows.Forms.DataGridView> Kontrola zapewnia automatyczne sortowanie, ale w zależności od potrzeb, może być konieczne dostosowanie operacji sortowania. Na przykład można sortowanie programowe tworzenie alternatywny interfejs użytkownika (UI). Alternatywnie można obsługiwać <xref:System.Windows.Forms.DataGridView.SortCompare> zdarzenia lub wywołanie `Sort(IComparer)` przeciążenia z <xref:System.Windows.Forms.DataGridView.Sort%2A> metodę większą elastyczność sortowania, takich jak sortowania wielu kolumn.  
  
 W poniższych przykładach kodu pokazano te trzy sposoby sortowanie niestandardowe. Aby uzyskać więcej informacji, zobacz [Tryb sortowania kolumn w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Sortowanie programowe  
 Poniższy przykład kodu pokazuje programowe sortowania za pomocą <xref:System.Windows.Forms.DataGridView.SortOrder%2A> i <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> właściwości, aby określić kierunek sortowania i <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> właściwości na ręczne ustawienie sortowania symbolu. `Sort(DataGridViewColumn,ListSortDirection)` Przeciążenia z <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda jest używana do sortowania danych tylko w jednej kolumnie.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Za pomocą tego zdarzenia SortCompare sortowanie niestandardowe  
 Poniższy przykład kodu pokazuje sortowanie niestandardowe przy użyciu <xref:System.Windows.Forms.DataGridView.SortCompare> obsługi zdarzeń. Wybrane <xref:System.Windows.Forms.DataGridViewColumn> jest sortowana i, jeśli występują zduplikowane wartości w kolumnie, w kolumnie Identyfikator służy do określania kolejności końcowego.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Sortowanie niestandardowe przy użyciu interfejsu IComparer  
 Poniższy przykład kodu pokazuje sortowanie niestandardowe przy użyciu `Sort(IComparer)` przeciążenia z <xref:System.Windows.Forms.DataGridView.Sort%2A> metodę, która przyjmuje implementacja <xref:System.Collections.IComparer> interfejs do wykonania sortowania wiele kolumn.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wymagaj te przykłady:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
 Informacji dotyczących tworzenia tych przykładów z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.DataGridView>  
 [Sortowanie danych w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 [Tryb sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
 [Instrukcje: ustawianie trybów sortowania kolumn w kontrolce DataGridView formularzy Windows Forms](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)
