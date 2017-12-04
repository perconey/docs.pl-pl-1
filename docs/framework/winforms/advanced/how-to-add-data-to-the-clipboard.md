---
title: 'Porady: dodawanie danych do schowka'
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
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47858af6d4e3dc5f29632c5a74f2431a2cc200b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-data-to-the-clipboard"></a><span data-ttu-id="a5b1e-102">Porady: dodawanie danych do schowka</span><span class="sxs-lookup"><span data-stu-id="a5b1e-102">How to: Add Data to the Clipboard</span></span>
<span data-ttu-id="a5b1e-103"><xref:System.Windows.Forms.Clipboard> Klasa dostarcza metody, które służy do interakcji z funkcją Schowka systemu operacyjnego Windows.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-103">The <xref:System.Windows.Forms.Clipboard> class provides methods that you can use to interact with the Windows operating system Clipboard feature.</span></span> <span data-ttu-id="a5b1e-104">Wiele aplikacji korzysta Schowka jako tymczasowy repozytorium dla danych.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-104">Many applications use the Clipboard as a temporary repository for data.</span></span> <span data-ttu-id="a5b1e-105">Na przykład edytory użyć Schowka podczas operacji kopiowania i wklejania.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-105">For example, word processors use the Clipboard during cut-and-paste operations.</span></span> <span data-ttu-id="a5b1e-106">Schowek jest również przydatne w przypadku transferu danych między aplikacjami na inny.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-106">The Clipboard is also useful for transferring data from one application to another.</span></span>  
  
 <span data-ttu-id="a5b1e-107">Podczas dodawania danych do Schowka, można określić format danych tak, aby inne aplikacje mogą rozpoznaje danych, jeśli będzie mógł używać tego formatu.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-107">When you add data to the Clipboard, you can indicate the data format so that other applications can recognize the data if they can use that format.</span></span> <span data-ttu-id="a5b1e-108">Można również dodać dane do Schowka w wielu różnych formatach, aby zwiększyć liczbę inne aplikacje, które mogą za pomocą danych.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-108">You can also add data to the Clipboard in multiple different formats to increase the number of other applications that can potentially use the data.</span></span>  
  
 <span data-ttu-id="a5b1e-109">Format Schowka jest ciągiem, który określa format, dzięki czemu aplikacji korzystającej z tego formatu można pobrać skojarzonych danych.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-109">A Clipboard format is a string that identifies the format so that an application that uses that format can retrieve the associated data.</span></span> <span data-ttu-id="a5b1e-110"><xref:System.Windows.Forms.DataFormats> Klasy udostępnia wstępnie zdefiniowane format nazwy do użycia.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-110">The <xref:System.Windows.Forms.DataFormats> class provides predefined format names for your use.</span></span> <span data-ttu-id="a5b1e-111">Możesz również użyć nazwy formatu lub typ obiektu jako jego format.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-111">You can also use your own format names or use the type of an object as its format.</span></span>  
  
 <span data-ttu-id="a5b1e-112">Aby dodać dane do Schowka w jednej lub wielu formatów, należy użyć <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-112">To add data to the Clipboard in one or multiple formats, use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method.</span></span> <span data-ttu-id="a5b1e-113">Dowolny obiekt można przekazać do tej metody, ale można dodać danych w wielu formatach, należy najpierw dodać dane do oddzielny obiekt przeznaczony do pracy w wielu formatach.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-113">You can pass any object to this method, but to add data in multiple formats, you must first add the data to a separate object designed to work with multiple formats.</span></span> <span data-ttu-id="a5b1e-114">Zazwyczaj spowoduje dodanie danych do <xref:System.Windows.Forms.DataObject>, ale można użyć dowolnego typu, który implementuje <xref:System.Windows.Forms.IDataObject> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-114">Typically, you will add your data to a <xref:System.Windows.Forms.DataObject>, but you can use any type that implements the <xref:System.Windows.Forms.IDataObject> interface.</span></span>  
  
 <span data-ttu-id="a5b1e-115">W [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], dane bezpośrednio do Schowka można dodać przy użyciu nowych metod, które umożliwiają wykonywanie podstawowych zadań Schowka.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-115">In [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)], you can add data directly to the Clipboard by using new methods designed to make basic Clipboard tasks easier.</span></span> <span data-ttu-id="a5b1e-116">Podczas pracy z danymi w formacie jednej, wspólnej, taki jak tekst za pomocą tych metod.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-116">Use these methods when you work with data in a single, common format such as text.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5b1e-117">Wszystkie aplikacje systemu Windows Udostępnianie Schowka.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-117">All Windows-based applications share the Clipboard.</span></span> <span data-ttu-id="a5b1e-118">W związku z tym zawartość mogą ulec zmianie po przełączeniu do innej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-118">Therefore, the contents are subject to change when you switch to another application.</span></span>  
>   
>  <span data-ttu-id="a5b1e-119"><xref:System.Windows.Forms.Clipboard> Klasy można używać tylko w wątkach ustawiony na tryb Jednowątkowego apartamentu wątku pojedynczego.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-119">The <xref:System.Windows.Forms.Clipboard> class can only be used in threads set to single thread apartment (STA) mode.</span></span> <span data-ttu-id="a5b1e-120">Aby korzystać z tej klasy, upewnij się, że Twoje `Main` metoda jest oznaczona atrybutem <xref:System.STAThreadAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-120">To use this class, ensure that your `Main` method is marked with the <xref:System.STAThreadAttribute> attribute.</span></span>  
>   
>  <span data-ttu-id="a5b1e-121">Obiekt musi być możliwy do serializacji dla niego do umieszczenia w Schowku.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-121">An object must be serializable for it to be put on the Clipboard.</span></span> <span data-ttu-id="a5b1e-122">Aby typ możliwy do serializacji, oznacz go z <xref:System.SerializableAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-122">To make a type serializable, mark it with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="a5b1e-123">Nie można serializować obiektu są przekazywane do metody Schowka, metoda zakończy się niepowodzeniem bez generowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-123">If you pass a non-serializable object to a Clipboard method, the method will fail without throwing an exception.</span></span> <span data-ttu-id="a5b1e-124">Aby uzyskać więcej informacji na temat serializacji, zobacz <xref:System.Runtime.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-124">For more information about serialization, see <xref:System.Runtime.Serialization>.</span></span>  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a><span data-ttu-id="a5b1e-125">Aby dodać dane do Schowka w formacie jednej, wspólnej</span><span class="sxs-lookup"><span data-stu-id="a5b1e-125">To add data to the Clipboard in a single, common format</span></span>  
  
1.  <span data-ttu-id="a5b1e-126">Użyj <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, lub <xref:System.Windows.Forms.Clipboard.SetText%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-126">Use the <xref:System.Windows.Forms.Clipboard.SetAudio%2A>, <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>, <xref:System.Windows.Forms.Clipboard.SetImage%2A>, or <xref:System.Windows.Forms.Clipboard.SetText%2A> method.</span></span> <span data-ttu-id="a5b1e-127">Te metody są dostępne tylko w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5b1e-127">These methods are available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a><span data-ttu-id="a5b1e-128">Aby dodać dane do Schowka w niestandardowym formacie</span><span class="sxs-lookup"><span data-stu-id="a5b1e-128">To add data to the Clipboard in a custom format</span></span>  
  
1.  <span data-ttu-id="a5b1e-129">Użyj <xref:System.Windows.Forms.Clipboard.SetData%2A> metodę o nazwie formatu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-129">Use the <xref:System.Windows.Forms.Clipboard.SetData%2A> method with a custom format name.</span></span> <span data-ttu-id="a5b1e-130">Ta metoda jest dostępna tylko w [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5b1e-130">This method is available only in [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)].</span></span>  
  
     <span data-ttu-id="a5b1e-131">Można również użyć nazwy formatu wstępnie zdefiniowane z <xref:System.Windows.Forms.Clipboard.SetData%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-131">You can also use predefined format names with the <xref:System.Windows.Forms.Clipboard.SetData%2A> method.</span></span> <span data-ttu-id="a5b1e-132">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.DataFormats>.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-132">For more information, see <xref:System.Windows.Forms.DataFormats>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a><span data-ttu-id="a5b1e-133">Aby dodać dane do Schowka w wielu formatach</span><span class="sxs-lookup"><span data-stu-id="a5b1e-133">To add data to the Clipboard in multiple formats</span></span>  
  
1.  <span data-ttu-id="a5b1e-134">Użyj <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> — metoda i przekaż <xref:System.Windows.Forms.DataObject> zawierający dane.</span><span class="sxs-lookup"><span data-stu-id="a5b1e-134">Use the <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> method and pass in a <xref:System.Windows.Forms.DataObject> that contains your data.</span></span> <span data-ttu-id="a5b1e-135">Tej metody należy użyć, aby dodać dane do Schowka w wersjach wcześniejszych niż [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5b1e-135">You must use this method to add data to the Clipboard on versions earlier than [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span>  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="a5b1e-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5b1e-136">See Also</span></span>  
 [<span data-ttu-id="a5b1e-137">Operacje przeciągania i upuszczania oraz Obsługa schowka</span><span class="sxs-lookup"><span data-stu-id="a5b1e-137">Drag-and-Drop Operations and Clipboard Support</span></span>](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [<span data-ttu-id="a5b1e-138">Porady: pobieranie danych ze Schowka</span><span class="sxs-lookup"><span data-stu-id="a5b1e-138">How to: Retrieve Data from the Clipboard</span></span>](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)