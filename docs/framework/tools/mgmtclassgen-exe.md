---
title: "Mgmtclassgen.exe (Zarządzanie generatorem silnie typizowanej klasy)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0f3e01e54cb60c7da1a57940246c5402ba635778
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="6bce3-102">Mgmtclassgen.exe (Zarządzanie generatorem silnie typizowanej klasy)</span><span class="sxs-lookup"><span data-stu-id="6bce3-102">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>
<span data-ttu-id="6bce3-103">Narzędzie Management Strongly Typed Class Generator umożliwia szybkie generowanie wcześnie powiązanych klas zarządzanych dla określonej klasy Instrumentacji zarządzania Windows (WMI).</span><span class="sxs-lookup"><span data-stu-id="6bce3-103">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="6bce3-104">Wygenerowana klasa upraszcza kod, który trzeba napisać, aby uzyskać dostęp do wystąpienia klasy WMI.</span><span class="sxs-lookup"><span data-stu-id="6bce3-104">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bce3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="6bce3-105">Syntax</span></span>  
  
```  
mgmtclassgen   
WMIClass [options]   
```  
  
|<span data-ttu-id="6bce3-106">Argument</span><span class="sxs-lookup"><span data-stu-id="6bce3-106">Argument</span></span>|<span data-ttu-id="6bce3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6bce3-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6bce3-108">*WMIClass*</span><span class="sxs-lookup"><span data-stu-id="6bce3-108">*WMIClass*</span></span>|<span data-ttu-id="6bce3-109">Klasa Instrumentacji zarządzania Windows, dla której jest generowana wcześnie powiązana klasa zarządzana.</span><span class="sxs-lookup"><span data-stu-id="6bce3-109">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="6bce3-110">Opcja</span><span class="sxs-lookup"><span data-stu-id="6bce3-110">Option</span></span>|<span data-ttu-id="6bce3-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6bce3-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="6bce3-112">**/l***języka* </span><span class="sxs-lookup"><span data-stu-id="6bce3-112">**/l**  *language*</span></span>|<span data-ttu-id="6bce3-113">Określa język, w którym ma zostać wygenerowana wcześnie powiązana klasa zarządzana.</span><span class="sxs-lookup"><span data-stu-id="6bce3-113">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="6bce3-114">Można określić **CS** (C#; domyślna), **VB** (Visual Basic), **MC** (C++), lub **JS** (JScript) jako argumentu języka.</span><span class="sxs-lookup"><span data-stu-id="6bce3-114">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="6bce3-115">**/m***maszyny* </span><span class="sxs-lookup"><span data-stu-id="6bce3-115">**/m**  *machine*</span></span>|<span data-ttu-id="6bce3-116">Określa komputer, z którym należy nawiązać połączenie (na tym komputerze znajduje się klasa WMI).</span><span class="sxs-lookup"><span data-stu-id="6bce3-116">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="6bce3-117">Wartością domyślną jest komputer lokalny.</span><span class="sxs-lookup"><span data-stu-id="6bce3-117">The default is the local computer.</span></span>|  
|<span data-ttu-id="6bce3-118">**/n**  *Ścieżka*</span><span class="sxs-lookup"><span data-stu-id="6bce3-118">**/n**  *path*</span></span>|<span data-ttu-id="6bce3-119">Określa ścieżkę do przestrzeni nazw usługi WMI zawierającej odpowiednią klasę WMI.</span><span class="sxs-lookup"><span data-stu-id="6bce3-119">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="6bce3-120">Jeśli ta opcja nie zostanie określony, narzędzie generuje kod dla *WMIClass* w domyślnym **Root\cimv2** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6bce3-120">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="6bce3-121">**/o***classnamespace* </span><span class="sxs-lookup"><span data-stu-id="6bce3-121">**/o**  *classnamespace*</span></span>|<span data-ttu-id="6bce3-122">Określa przestrzeń nazw platformy .NET, w której ma zostać wygenerowana klasa kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6bce3-122">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="6bce3-123">Jeśli ta opcja nie zostanie określona, narzędzie wygeneruje przestrzeń nazw, używając przestrzeni nazw usługi WMI i prefiksu schematu.</span><span class="sxs-lookup"><span data-stu-id="6bce3-123">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="6bce3-124">Prefiks schematu jest częścią nazwy klasy poprzedzającą znak podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="6bce3-124">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="6bce3-125">Na przykład w przypadku **Win32_OperatingSystem** klasy w **Root\cimv2** przestrzeni nazw, narzędzie może wygenerować klasy w **głównego. CIMV2. Win32**.</span><span class="sxs-lookup"><span data-stu-id="6bce3-125">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="6bce3-126">**/p***filepath* </span><span class="sxs-lookup"><span data-stu-id="6bce3-126">**/p**  *filepath*</span></span>|<span data-ttu-id="6bce3-127">Określa ścieżkę do pliku, w którym ma zostać zapisany wygenerowany kod.</span><span class="sxs-lookup"><span data-stu-id="6bce3-127">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="6bce3-128">Jeśli ta opcja nie zostanie określona, narzędzie utworzy plik w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6bce3-128">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="6bce3-129">Jego nazwy klas i plików, w którym generuje klasy przy użyciu *WMIClass* argumentu.</span><span class="sxs-lookup"><span data-stu-id="6bce3-129">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="6bce3-130">Nazwa klasy i pliku są takie same jak nazwa *WMIClass.*</span><span class="sxs-lookup"><span data-stu-id="6bce3-130">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="6bce3-131">Jeśli *WMIClass* zawiera znak podkreślenia narzędzie korzysta z części nazwy klasy po znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="6bce3-131">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="6bce3-132">Na przykład jeśli *WMIClass* nazwa jest w formacie **Win32_LogicalDisk**, pliku i wygenerowane klasy ma nazwę "dysk logiczny".</span><span class="sxs-lookup"><span data-stu-id="6bce3-132">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="6bce3-133">Jeżeli plik już istnieje, narzędzie zastąpi istniejący plik.</span><span class="sxs-lookup"><span data-stu-id="6bce3-133">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="6bce3-134">**/PW***hasła* </span><span class="sxs-lookup"><span data-stu-id="6bce3-134">**/pw**  *password*</span></span>|<span data-ttu-id="6bce3-135">Określa hasło do użycia podczas logowania na komputerze określonym przez **/m** opcji.</span><span class="sxs-lookup"><span data-stu-id="6bce3-135">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="6bce3-136">**/u***nazwy użytkownika* </span><span class="sxs-lookup"><span data-stu-id="6bce3-136">**/u**  *user name*</span></span>|<span data-ttu-id="6bce3-137">Określa nazwę użytkownika, należy użyć podczas logowania na komputerze określonym przez **/m** opcji.</span><span class="sxs-lookup"><span data-stu-id="6bce3-137">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="6bce3-138">**/?**</span><span class="sxs-lookup"><span data-stu-id="6bce3-138">**/?**</span></span>|<span data-ttu-id="6bce3-139">Wyświetla składnię polecenia i opcje narzędzia.</span><span class="sxs-lookup"><span data-stu-id="6bce3-139">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bce3-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6bce3-140">Remarks</span></span>  
 <span data-ttu-id="6bce3-141">MgmtClassGen.exe używa <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="6bce3-141">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6bce3-142">Dzięki temu można użyć dowolnego niestandardowego dostawcy kodu, aby wygenerować kod w zarządzanych językach innych niż C#, Visual Basic i JScript.</span><span class="sxs-lookup"><span data-stu-id="6bce3-142">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="6bce3-143">Należy zauważyć, że wygenerowane klasy są powiązane ze schematem, dla którego są generowane.</span><span class="sxs-lookup"><span data-stu-id="6bce3-143">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="6bce3-144">Jeśli schemat źródłowy ulegnie zmianie, trzeba ponownie wygenerować klasę, jeśli chce się odzwierciedlić zmiany w schemacie.</span><span class="sxs-lookup"><span data-stu-id="6bce3-144">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="6bce3-145">W poniższej tabeli pokazano mapowanie typów modelu wspólnych informacji (CIM) usługi WMI na typy danych w generowanej klasie:</span><span class="sxs-lookup"><span data-stu-id="6bce3-145">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="6bce3-146">Typ modelu CIM</span><span class="sxs-lookup"><span data-stu-id="6bce3-146">CIM type</span></span>|<span data-ttu-id="6bce3-147">Typ danych w generowanej klasie</span><span class="sxs-lookup"><span data-stu-id="6bce3-147">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="6bce3-148">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="6bce3-148">CIM_SINT8</span></span>|<span data-ttu-id="6bce3-149">**Sbyte —**</span><span class="sxs-lookup"><span data-stu-id="6bce3-149">**SByte**</span></span>|  
|<span data-ttu-id="6bce3-150">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="6bce3-150">CIM_UINT8</span></span>|<span data-ttu-id="6bce3-151">**Bajtów**</span><span class="sxs-lookup"><span data-stu-id="6bce3-151">**Byte**</span></span>|  
|<span data-ttu-id="6bce3-152">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="6bce3-152">CIM_SINT16</span></span>|<span data-ttu-id="6bce3-153">**Int16**</span><span class="sxs-lookup"><span data-stu-id="6bce3-153">**Int16**</span></span>|  
|<span data-ttu-id="6bce3-154">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="6bce3-154">CIM_UINT16</span></span>|<span data-ttu-id="6bce3-155">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="6bce3-155">**UInt16**</span></span>|  
|<span data-ttu-id="6bce3-156">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="6bce3-156">CIM_SINT32</span></span>|<span data-ttu-id="6bce3-157">**Int32**</span><span class="sxs-lookup"><span data-stu-id="6bce3-157">**Int32**</span></span>|  
|<span data-ttu-id="6bce3-158">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="6bce3-158">SIM_UINT32</span></span>|<span data-ttu-id="6bce3-159">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="6bce3-159">**UInt32**</span></span>|  
|<span data-ttu-id="6bce3-160">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="6bce3-160">CIM_SINT64</span></span>|<span data-ttu-id="6bce3-161">**Int64**</span><span class="sxs-lookup"><span data-stu-id="6bce3-161">**Int64**</span></span>|  
|<span data-ttu-id="6bce3-162">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="6bce3-162">CIM_UINT64</span></span>|<span data-ttu-id="6bce3-163">**UInt64 —**</span><span class="sxs-lookup"><span data-stu-id="6bce3-163">**UInt64**</span></span>|  
|<span data-ttu-id="6bce3-164">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="6bce3-164">CIM_REAL32</span></span>|<span data-ttu-id="6bce3-165">**Pojedynczy**</span><span class="sxs-lookup"><span data-stu-id="6bce3-165">**Single**</span></span>|  
|<span data-ttu-id="6bce3-166">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="6bce3-166">CIM_REAL64</span></span>|<span data-ttu-id="6bce3-167">**O podwójnej precyzji**</span><span class="sxs-lookup"><span data-stu-id="6bce3-167">**Double**</span></span>|  
|<span data-ttu-id="6bce3-168">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="6bce3-168">CIM_BOOLEAN</span></span>|<span data-ttu-id="6bce3-169">**Wartość logiczna**</span><span class="sxs-lookup"><span data-stu-id="6bce3-169">**Boolean**</span></span>|  
|<span data-ttu-id="6bce3-170">CIM_String</span><span class="sxs-lookup"><span data-stu-id="6bce3-170">CIM_String</span></span>|<span data-ttu-id="6bce3-171">**Ciąg**</span><span class="sxs-lookup"><span data-stu-id="6bce3-171">**String**</span></span>|  
|<span data-ttu-id="6bce3-172">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="6bce3-172">CIM_DATETIME</span></span>|<span data-ttu-id="6bce3-173">**Data i godzina** lub **TimeSpan**</span><span class="sxs-lookup"><span data-stu-id="6bce3-173">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="6bce3-174">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="6bce3-174">CIM_REFERENCE</span></span>|<span data-ttu-id="6bce3-175">**Element ManagementPath**</span><span class="sxs-lookup"><span data-stu-id="6bce3-175">**ManagementPath**</span></span>|  
|<span data-ttu-id="6bce3-176">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="6bce3-176">CIM_CHAR16</span></span>|<span data-ttu-id="6bce3-177">**Char**</span><span class="sxs-lookup"><span data-stu-id="6bce3-177">**Char**</span></span>|  
|<span data-ttu-id="6bce3-178">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="6bce3-178">CIM_OBJECT</span></span>|<span data-ttu-id="6bce3-179">**ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="6bce3-179">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="6bce3-180">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="6bce3-180">CIM_IUNKNOWN</span></span>|<span data-ttu-id="6bce3-181">**Obiekt**</span><span class="sxs-lookup"><span data-stu-id="6bce3-181">**Object**</span></span>|  
|<span data-ttu-id="6bce3-182">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="6bce3-182">CIM_ARRAY</span></span>|<span data-ttu-id="6bce3-183">Tablica wymienionych powyżej obiektów</span><span class="sxs-lookup"><span data-stu-id="6bce3-183">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="6bce3-184">Podczas generowania klasy WMI należy zwrócić uwagę na następujące zachowania:</span><span class="sxs-lookup"><span data-stu-id="6bce3-184">Note the following behaviors when you generate a WMI class:</span></span>  
  
-   <span data-ttu-id="6bce3-185">Możliwe jest, że standardowa publiczna właściwość lub metoda będzie miała taką samą nazwę jak istniejąca właściwość lub metoda.</span><span class="sxs-lookup"><span data-stu-id="6bce3-185">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="6bce3-186">Jeśli tak się zdarzy, narzędzie zmieni nazwę właściwości lub metody w generowanej klasie w celu uniknięcia konfliktu nazw.</span><span class="sxs-lookup"><span data-stu-id="6bce3-186">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
-   <span data-ttu-id="6bce3-187">Możliwe jest, że nazwa właściwości lub metody w generowanej klasie będzie słowem kluczowym w docelowym języku programowania.</span><span class="sxs-lookup"><span data-stu-id="6bce3-187">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="6bce3-188">Jeśli tak się zdarzy, narzędzie zmieni nazwę właściwości lub metody w generowanej klasie w celu uniknięcia konfliktu nazw.</span><span class="sxs-lookup"><span data-stu-id="6bce3-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
-   <span data-ttu-id="6bce3-189">W usłudze WMI kwalifikatory to modyfikatory zawierające informacje opisujące klasę, wystąpienie, właściwość lub metodę.</span><span class="sxs-lookup"><span data-stu-id="6bce3-189">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="6bce3-190">Usługa WMI korzysta kwalifikatory standardowe **odczytu**, **zapisu**, i **klucza** do opisywania właściwość wygenerowanej klasy.</span><span class="sxs-lookup"><span data-stu-id="6bce3-190">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="6bce3-191">Na przykład właściwość, która jest modyfikowane za pomocą **odczytu** kwalifikator jest zdefiniowana tylko z właściwością **uzyskać** dostępu w wygenerowanej klasy.</span><span class="sxs-lookup"><span data-stu-id="6bce3-191">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="6bce3-192">Ponieważ właściwość oznaczona **odczytu** kwalifikator jest przeznaczony tylko do odczytu do **ustawić** metoda dostępu nie jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="6bce3-192">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
-   <span data-ttu-id="6bce3-193">Właściwość numeryczna może być modyfikowany przez **wartości** i **ValueMaps** kwalifikatory, aby wskazać, że właściwość można ustawić tylko określone dopuszczalnej wartości.</span><span class="sxs-lookup"><span data-stu-id="6bce3-193">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="6bce3-194">Wyliczenie jest generowana z tych **wartości** i **ValueMaps** i właściwość jest zamapowana do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="6bce3-194">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
-   <span data-ttu-id="6bce3-195">Usługa WMI używa pojedynczego terminu w celu opisania klasy, która ma tylko jedno wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="6bce3-195">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="6bce3-196">Dlatego też konstruktor domyślny klasy pojedynczej będzie inicjował klasę wyłącznie do jednego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="6bce3-196">Therefore, the default constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
-   <span data-ttu-id="6bce3-197">Klasa WMI może mieć właściwości, które są obiektami.</span><span class="sxs-lookup"><span data-stu-id="6bce3-197">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="6bce3-198">Podczas generowania silnie typizowanej klasy dla klasy WMI tego typu należy wziąć pod uwagę wygenerowanie silnie typizowanych klas dla typów właściwości osadzonych obiektów.</span><span class="sxs-lookup"><span data-stu-id="6bce3-198">When you generate a strongly-typed class for this type of WMI class, you should consider generating strongly-typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="6bce3-199">Umożliwi to dostęp do osadzonych obiektów w silnie typizowany sposób.</span><span class="sxs-lookup"><span data-stu-id="6bce3-199">This will allow you to access the embedded objects in a strongly-typed manner.</span></span> <span data-ttu-id="6bce3-200">Należy zauważyć, że wygenerowany kod może nie być w stanie wykryć typu osadzonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="6bce3-200">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="6bce3-201">W takim przypadku w wygenerowanym kodzie zostanie utworzony komentarz powiadamiający o problemie.</span><span class="sxs-lookup"><span data-stu-id="6bce3-201">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="6bce3-202">Następnie można zmodyfikować wygenerowany kod, tak aby właściwość miała typ innej generowanej klasy.</span><span class="sxs-lookup"><span data-stu-id="6bce3-202">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
-   <span data-ttu-id="6bce3-203">W usłudze WMI wartość danych typu CIM_DATETIME może przedstawiać określoną datę i godzinę albo interwał czasu.</span><span class="sxs-lookup"><span data-stu-id="6bce3-203">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="6bce3-204">Jeśli wartość danych reprezentuje datę i godzinę, jest typ danych w wygenerowana klasa **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="6bce3-204">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="6bce3-205">Jeśli wartość danych reprezentuje przedział czasu, typ danych w wygenerowanej klasy jest **TimeSpan**.</span><span class="sxs-lookup"><span data-stu-id="6bce3-205">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="6bce3-206">Alternatywnie można wygenerować silnie typizowaną klasę, używając rozszerzenia zarządzania Eksploratora serwera w programie Visual Studio .NET.</span><span class="sxs-lookup"><span data-stu-id="6bce3-206">You can alternately generate a strongly-typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="6bce3-207">Aby uzyskać więcej informacji dotyczących usługi WMI, zobacz **Instrumentacji zarządzania Windows** tematu w dokumentacji zestawu SDK platformy.</span><span class="sxs-lookup"><span data-stu-id="6bce3-207">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="6bce3-208">Przykłady</span><span class="sxs-lookup"><span data-stu-id="6bce3-208">Examples</span></span>  
 <span data-ttu-id="6bce3-209">Polecenie generuje zarządzanej klasy w kodzie języka C# dla **Win32_LogicalDisk** klasy usługi WMI w **Root\cimv2** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6bce3-209">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="6bce3-210">Narzędzie zapisuje zarządzanej klasy w pliku źródłowego w c:\disk.cs w **głównego. CIMV2. Win32** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6bce3-210">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="6bce3-211">W poniższym przykładzie kodu pokazano, w jaki sposób można programowo używać wygenerowanej klasy.</span><span class="sxs-lookup"><span data-stu-id="6bce3-211">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="6bce3-212">Najpierw jest wyliczane wystąpienie klasy i jest drukowana ścieżka.</span><span class="sxs-lookup"><span data-stu-id="6bce3-212">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="6bce3-213">Następnie za pomocą wystąpienia usługi WMI jest tworzone wystąpienie wygenerowanej klasy, które ma zostać zainicjowane.</span><span class="sxs-lookup"><span data-stu-id="6bce3-213">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="6bce3-214">`Process`jest to klasa wygenerowany dla **Win32_Process** i `LogicalDisk` jest generowane dla klasy **Win32_LogicalDisk** w **Root\cimv2** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="6bce3-214">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App     
   Public Shared Sub Main()        
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process     
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6bce3-215">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6bce3-215">See Also</span></span>  
 <xref:System.Management>  
 <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>  
 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>  
 [<span data-ttu-id="6bce3-216">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="6bce3-216">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="6bce3-217">Wiersz polecenia</span><span class="sxs-lookup"><span data-stu-id="6bce3-217">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)