---
title: "Wskazówki: wdrażanie dziedziczenia z obiektami COM (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d6906c58431a0e844e8f430ade10ae819e77ff2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a><span data-ttu-id="db526-102">Wskazówki: wdrażanie dziedziczenia z obiektami COM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db526-102">Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)</span></span>
<span data-ttu-id="db526-103">Mogą pochodzić klas języka Visual Basic z `Public` klasy obiektów COM, nawet te utworzone we wcześniejszych wersjach [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db526-103">You can derive Visual Basic classes from `Public` classes in COM objects, even those created in earlier versions of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="db526-104">Zastąpiona lub przeciążony podobnie jak właściwości właściwości i metody dziedziczone z obiektami COM klasy i metody innych klasy podstawowej można zastąpić lub przeciążony.</span><span class="sxs-lookup"><span data-stu-id="db526-104">The properties and methods of classes inherited from COM objects can be overridden or overloaded just as properties and methods of any other base class can be overridden or overloaded.</span></span> <span data-ttu-id="db526-105">Dziedziczenia z obiektami COM jest przydatne w przypadku istniejącej biblioteki klas, którego chcesz ponownie skompilować.</span><span class="sxs-lookup"><span data-stu-id="db526-105">Inheritance from COM objects is useful when you have an existing class library that you do not want to recompile.</span></span>  
  
 <span data-ttu-id="db526-106">Poniższa procedura pokazuje, jak Visual Basic 6.0 do utworzenia obiektu COM, który zawiera klasę, a następnie użyć jej jako klasę podstawową.</span><span class="sxs-lookup"><span data-stu-id="db526-106">The following procedure shows how to use Visual Basic 6.0 to create a COM object that contains a class, and then use it as a base class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a><span data-ttu-id="db526-107">Aby utworzyć obiekt COM, który jest używany w tym przewodniku</span><span class="sxs-lookup"><span data-stu-id="db526-107">To build the COM object that is used in this walkthrough</span></span>  
  
1.  <span data-ttu-id="db526-108">Otwórz nowy projekt ActiveX biblioteki DLL w Visual Basic 6.0.</span><span class="sxs-lookup"><span data-stu-id="db526-108">In Visual Basic 6.0, open a new ActiveX DLL project.</span></span> <span data-ttu-id="db526-109">Projekt o nazwie `Project1` jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="db526-109">A project named `Project1` is created.</span></span> <span data-ttu-id="db526-110">Ma klasę o nazwie `Class1`.</span><span class="sxs-lookup"><span data-stu-id="db526-110">It has a class named `Class1`.</span></span>  
  
2.  <span data-ttu-id="db526-111">W **Eksplorator projektów**, kliknij prawym przyciskiem myszy **Project1**, a następnie kliknij przycisk **Project1 właściwości**.</span><span class="sxs-lookup"><span data-stu-id="db526-111">In the **Project Explorer**, right-click **Project1**, and then click **Project1 Properties**.</span></span> <span data-ttu-id="db526-112">**Właściwości projektu** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="db526-112">The **Project Properties** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="db526-113">Na **ogólne** karcie **właściwości projektu** okno dialogowe Zmień nazwę projektu, wpisując `ComObject1` w **Nazwa projektu** pola.</span><span class="sxs-lookup"><span data-stu-id="db526-113">On the **General** tab of the **Project Properties** dialog box, change the project name by typing `ComObject1` in the **Project Name** field.</span></span>  
  
4.  <span data-ttu-id="db526-114">W **Eksplorator projektów**, kliknij prawym przyciskiem myszy `Class1`, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="db526-114">In the **Project Explorer**, right-click `Class1`, and then click **Properties**.</span></span> <span data-ttu-id="db526-115">**Właściwości** zostanie wyświetlone okno klasy.</span><span class="sxs-lookup"><span data-stu-id="db526-115">The **Properties** window for the class is displayed.</span></span>  
  
5.  <span data-ttu-id="db526-116">Zmień `Name` właściwości `MathFunctions`.</span><span class="sxs-lookup"><span data-stu-id="db526-116">Change the `Name` property to `MathFunctions`.</span></span>  
  
6.  <span data-ttu-id="db526-117">W **Eksplorator projektów**, kliknij prawym przyciskiem myszy `MathFunctions`, a następnie kliknij przycisk **kod widoku**.</span><span class="sxs-lookup"><span data-stu-id="db526-117">In the **Project Explorer**, right-click `MathFunctions`, and then click **View Code**.</span></span> <span data-ttu-id="db526-118">**Edytora kodu** jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="db526-118">The **Code Editor** is displayed.</span></span>  
  
7.  <span data-ttu-id="db526-119">Dodawanie zmiennej lokalnej do przechowywania wartości właściwości:</span><span class="sxs-lookup"><span data-stu-id="db526-119">Add a local variable to hold the property value:</span></span>  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  <span data-ttu-id="db526-120">Dodaj właściwość `Let` i właściwość `Get` procedury właściwości:</span><span class="sxs-lookup"><span data-stu-id="db526-120">Add Property `Let` and Property `Get` property procedures:</span></span>  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. <span data-ttu-id="db526-121">Dodaj funkcję:</span><span class="sxs-lookup"><span data-stu-id="db526-121">Add a function:</span></span>  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. <span data-ttu-id="db526-122">Tworzenie i zarejestrować obiektu COM, klikając **upewnij ComObject1.dll** na **pliku** menu.</span><span class="sxs-lookup"><span data-stu-id="db526-122">Create and register the COM object by clicking **Make ComObject1.dll** on the **File** menu.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="db526-123">Mimo że można również ujawniać utworzone za pomocą klasy [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] jako obiekt COM nie jest obiektem COM. wartość true i nie można użyć w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="db526-123">Although you can also expose a class created with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] as a COM object, it is not a true COM object and cannot be used in this walkthrough.</span></span> <span data-ttu-id="db526-124">Aby uzyskać więcej informacji, zobacz [współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span><span class="sxs-lookup"><span data-stu-id="db526-124">For details, see [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).</span></span>  
  
## <a name="interop-assemblies"></a><span data-ttu-id="db526-125">Zestawy międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="db526-125">Interop Assemblies</span></span>  
 <span data-ttu-id="db526-126">W poniższej procedury spowoduje utworzenie zestawu międzyoperacyjnego, który działa jako mostka między kodu niezarządzanego (np. obiekt COM) i kod zarządzany [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] używa.</span><span class="sxs-lookup"><span data-stu-id="db526-126">In the following procedure, you will create an interop assembly, which acts as a bridge between unmanaged code (such as a COM object) and the managed code [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] uses.</span></span> <span data-ttu-id="db526-127">Zestaw międzyoperacyjny który [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tworzy uchwytów wielu szczegółów pracy z COM obiekty, takie jak *przekazywanie międzyoperacyjne*, proces tworzenia pakietów parametrów i zwracanych wartości na dane równoważne typy jako przechodzą do i z modelu COM obiektów.</span><span class="sxs-lookup"><span data-stu-id="db526-127">The interop assembly that [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] creates handles many of the details of working with COM objects, such as *interop marshaling*, the process of packaging parameters and return values into equivalent data types as they move to and from COM objects.</span></span> <span data-ttu-id="db526-128">Odwołania w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] punktów aplikacji do zestawu międzyoperacyjnego, a nie rzeczywiste obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="db526-128">The reference in the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] application points to the interop assembly, not the actual COM object.</span></span>  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a><span data-ttu-id="db526-129">Aby użyć obiektów COM z Visual Basic 2005 lub nowszym</span><span class="sxs-lookup"><span data-stu-id="db526-129">To use a COM object with Visual Basic 2005 and later versions</span></span>  
  
1.  <span data-ttu-id="db526-130">Otwórz nowe [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projekt aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="db526-130">Open a new [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows Application project.</span></span>  
  
2.  <span data-ttu-id="db526-131">Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="db526-131">On the **Project** menu, click **Add Reference**.</span></span>  
  
     <span data-ttu-id="db526-132">**Dodaj odwołanie** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="db526-132">The **Add Reference** dialog box is displayed.</span></span>  
  
3.  <span data-ttu-id="db526-133">Na **COM** karcie, kliknij dwukrotnie `ComObject1` w **nazwa składnika** listy i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="db526-133">On the **COM** tab, double-click `ComObject1` in the **Component Name** list and click **OK**.</span></span>  
  
4.  <span data-ttu-id="db526-134">Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.</span><span class="sxs-lookup"><span data-stu-id="db526-134">On the **Project** menu, click **Add New Item**.</span></span>  
  
     <span data-ttu-id="db526-135">**Dodaj nowy element** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="db526-135">The **Add New Item** dialog box is displayed.</span></span>  
  
5.  <span data-ttu-id="db526-136">W **szablony** okienku, kliknij przycisk **klasy**.</span><span class="sxs-lookup"><span data-stu-id="db526-136">In the **Templates** pane, click **Class**.</span></span>  
  
     <span data-ttu-id="db526-137">Domyślna nazwa pliku `Class1.vb`, zostanie wyświetlony w **nazwa** pola.</span><span class="sxs-lookup"><span data-stu-id="db526-137">The default file name, `Class1.vb`, appears in the **Name** field.</span></span> <span data-ttu-id="db526-138">Zmień to pole na MathClass.vb i kliknij przycisk **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="db526-138">Change this field to MathClass.vb and click **Add**.</span></span> <span data-ttu-id="db526-139">Spowoduje to utworzenie klasy o nazwie `MathClass`i wyświetla jego kod.</span><span class="sxs-lookup"><span data-stu-id="db526-139">This creates a class named `MathClass`, and displays its code.</span></span>  
  
6.  <span data-ttu-id="db526-140">Dodaj następujący kod do góry `MathClass` dziedziczona z klasy COM.</span><span class="sxs-lookup"><span data-stu-id="db526-140">Add the following code to the top of `MathClass` to inherit from the COM class.</span></span>  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  <span data-ttu-id="db526-141">Przeciążenia publicznej metody klasy podstawowej, dodając następujący kod do `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="db526-141">Overload the public method of the base class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  <span data-ttu-id="db526-142">Rozszerzenie klasy dziedziczonej, dodając następujący kod do `MathClass`:</span><span class="sxs-lookup"><span data-stu-id="db526-142">Extend the inherited class by adding the following code to `MathClass`:</span></span>  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 <span data-ttu-id="db526-143">Nowa klasa dziedziczy właściwości klasy podstawowej w obiekcie COM, overloads metody i definiuje nową metodę rozszerzenie klasy.</span><span class="sxs-lookup"><span data-stu-id="db526-143">The new class inherits the properties of the base class in the COM object, overloads a method, and defines a new method to extend the class.</span></span>  
  
#### <a name="to-test-the-inherited-class"></a><span data-ttu-id="db526-144">Aby przetestować dziedziczonej klasie</span><span class="sxs-lookup"><span data-stu-id="db526-144">To test the inherited class</span></span>  
  
1.  <span data-ttu-id="db526-145">Dodawanie przycisku do formularza uruchamiania, a następnie kliknij dwukrotnie, aby wyświetlić jego kod.</span><span class="sxs-lookup"><span data-stu-id="db526-145">Add a button to your startup form, and then double-click it to view its code.</span></span>  
  
2.  <span data-ttu-id="db526-146">Przycisk `Click` procedury obsługi zdarzeń, Dodaj następujący kod, aby utworzyć wystąpienie `MathClass` i wywoływać przeciążenia metody:</span><span class="sxs-lookup"><span data-stu-id="db526-146">In the button's `Click` event handler procedure, add the following code to create an instance of `MathClass` and call the overloaded methods:</span></span>  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  <span data-ttu-id="db526-147">Uruchom projekt, naciskając klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="db526-147">Run the project by pressing F5.</span></span>  
  
 <span data-ttu-id="db526-148">Po kliknięciu przycisku w formularzu `AddNumbers` najpierw wywoływana jest metoda o `Short` typ danych liczb, i [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wybiera odpowiednią metodę z klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="db526-148">When you click the button on the form, the `AddNumbers` method is first called with `Short` data type numbers, and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] chooses the appropriate method from the base class.</span></span> <span data-ttu-id="db526-149">Drugie wywołanie `AddNumbers` zostaje skierowany do przeciążenia metody z `MathClass`.</span><span class="sxs-lookup"><span data-stu-id="db526-149">The second call to `AddNumbers` is directed to the overload method from `MathClass`.</span></span> <span data-ttu-id="db526-150">Trzeci wywołania wywołania `SubtractNumbers` metodę, która rozszerza klasę.</span><span class="sxs-lookup"><span data-stu-id="db526-150">The third call calls the `SubtractNumbers` method, which extends the class.</span></span> <span data-ttu-id="db526-151">Ustawiono właściwości w klasie podstawowej, a wartość jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="db526-151">The property in the base class is set, and the value is displayed.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="db526-152">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="db526-152">Next Steps</span></span>  
 <span data-ttu-id="db526-153">Można zauważyć, że przeciążenia `AddNumbers` funkcja wydaje się mają ten sam typ jako metody dziedziczona z klasy podstawowej obiektu COM danych.</span><span class="sxs-lookup"><span data-stu-id="db526-153">You may have noticed that the overloaded `AddNumbers` function appears to have the same data type as the method inherited from the base class of the COM object.</span></span> <span data-ttu-id="db526-154">Wynika to z faktu, argumentów i parametrów metody klasy podstawowej są zdefiniowane jako 16-bitowych liczb całkowitych w Visual Basic 6.0, ale są one widoczne jako 16-bitowych liczb całkowitych typu `Short` w nowszych wersjach programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="db526-154">This is because the arguments and parameters of the base class method are defined as 16-bit integers in Visual Basic 6.0, but they are exposed as 16-bit integers of type `Short` in later versions of Visual Basic.</span></span> <span data-ttu-id="db526-155">Nowa funkcja akceptuje 32-bitowych liczb całkowitych i overloads funkcji klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="db526-155">The new function accepts 32-bit integers, and overloads the base class function.</span></span>  
  
 <span data-ttu-id="db526-156">Podczas pracy z obiektami COM, upewnij się, że należy sprawdzić rozmiar i danych typów parametrów.</span><span class="sxs-lookup"><span data-stu-id="db526-156">When working with COM objects, make sure that you verify the size and data types of parameters.</span></span> <span data-ttu-id="db526-157">Na przykład jeśli używasz obiektu COM, który akceptuje obiekt kolekcji Visual Basic 6.0 jako argument nie może dostarczyć kolekcji z nowszej wersji programu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="db526-157">For example, when you are using a COM object that accepts a Visual Basic 6.0 collection object as an argument, you cannot provide a collection from a later version of Visual Basic.</span></span>  
  
 <span data-ttu-id="db526-158">Właściwości i metody odziedziczona z klasy COM może zostać zastąpiona, co oznacza, że można zadeklarować lokalnego właściwości lub metody, które zastępuje właściwość lub dziedziczone z podstawową klasę com.</span><span class="sxs-lookup"><span data-stu-id="db526-158">Properties and methods inherited from COM classes can be overridden, meaning that you can declare a local property or method that replaces a property or method inherited from a base COM class.</span></span> <span data-ttu-id="db526-159">Zasady zastępowania odziedziczone właściwości modelu COM są podobne do reguły zastępowania inne właściwości i metody z następującymi wyjątkami:</span><span class="sxs-lookup"><span data-stu-id="db526-159">The rules for overriding inherited COM properties are similar to the rules for overriding other properties and methods with the following exceptions:</span></span>  
  
-   <span data-ttu-id="db526-160">Należy zastąpić wszystkie właściwości lub metody odziedziczona z klasy COM, należy zastąpić wszystkie odziedziczone właściwości i metody.</span><span class="sxs-lookup"><span data-stu-id="db526-160">If you override any property or method inherited from a COM class, you must override all the other inherited properties and methods.</span></span>  
  
-   <span data-ttu-id="db526-161">Właściwości, które używają `ByRef` parametrów nie może zostać zastąpiona.</span><span class="sxs-lookup"><span data-stu-id="db526-161">Properties that use `ByRef` parameters cannot be overridden.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db526-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="db526-162">See Also</span></span>  
 [<span data-ttu-id="db526-163">Współdziałanie COM w aplikacjach .NET Framework</span><span class="sxs-lookup"><span data-stu-id="db526-163">COM Interoperability in .NET Framework Applications</span></span>](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [<span data-ttu-id="db526-164">Inherits — instrukcja</span><span class="sxs-lookup"><span data-stu-id="db526-164">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="db526-165">Short — typ danych</span><span class="sxs-lookup"><span data-stu-id="db526-165">Short Data Type</span></span>](../../../visual-basic/language-reference/data-types/short-data-type.md)