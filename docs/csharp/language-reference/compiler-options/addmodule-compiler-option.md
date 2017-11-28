---
title: -addmodule (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /addmodule
helpviewer_keywords:
- /addmodule compiler option [C#]
- -addmodule compiler option [C#]
- addmodule compiler option [C#]
ms.assetid: ed604546-0dc2-4bd4-9a3e-610a8d973e58
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2652102682de9dff24c66180dde36f33b4b6bbfc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="addmodule-c-compiler-options"></a><span data-ttu-id="54e90-102">/addmodule (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="54e90-102">/addmodule (C# Compiler Options)</span></span>
<span data-ttu-id="54e90-103">Ta opcja dodaje moduł, który został utworzony z opcją docelowych: moduł do bieżącej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="54e90-103">This option adds a module that was created with the target:module switch to the current compilation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54e90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54e90-104">Syntax</span></span>  
  
```console  
/addmodule:file[;file2]  
```  
  
## <a name="arguments"></a><span data-ttu-id="54e90-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="54e90-105">Arguments</span></span>  
 <span data-ttu-id="54e90-106">`file`, `file2`</span><span class="sxs-lookup"><span data-stu-id="54e90-106">`file`, `file2`</span></span>  
 <span data-ttu-id="54e90-107">Plik wyjściowy, który zawiera metadanych.</span><span class="sxs-lookup"><span data-stu-id="54e90-107">An output file that contains metadata.</span></span> <span data-ttu-id="54e90-108">Plik nie zawiera manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="54e90-108">The file cannot contain an assembly manifest.</span></span> <span data-ttu-id="54e90-109">Aby zaimportować więcej niż jeden plik, Rozdziel nazwy pliku przecinkami lub średnikami.</span><span class="sxs-lookup"><span data-stu-id="54e90-109">To import more than one file, separate file names with either a comma or a semicolon.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54e90-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54e90-110">Remarks</span></span>  
 <span data-ttu-id="54e90-111">Wszystkie moduły dodawane z **/addmodule** musi być w tym samym katalogu co plik wyjściowy w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="54e90-111">All modules added with **/addmodule** must be in the same directory as the output file at run time.</span></span> <span data-ttu-id="54e90-112">Oznacza to można określić modułu w dowolnym katalogu w czasie kompilacji, ale moduł musi znajdować się w katalogu aplikacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="54e90-112">That is, you can specify a module in any directory at compile time but the module must be in the application directory at run time.</span></span> <span data-ttu-id="54e90-113">Jeśli moduł nie jest w katalogu aplikacji w czasie wykonywania, otrzymasz <xref:System.TypeLoadException>.</span><span class="sxs-lookup"><span data-stu-id="54e90-113">If the module is not in the application directory at run time, you will get a <xref:System.TypeLoadException>.</span></span>  
  
 <span data-ttu-id="54e90-114">`file`nie może zawierać zestawu.</span><span class="sxs-lookup"><span data-stu-id="54e90-114">`file` cannot contain an assembly.</span></span> <span data-ttu-id="54e90-115">Na przykład, jeśli utworzono plik wyjściowy [/target: module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), jego metadane mogą być importowane przy **/addmodule**.</span><span class="sxs-lookup"><span data-stu-id="54e90-115">For example, if the output file was created with [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), its metadata can be imported with **/addmodule**.</span></span>  
  
 <span data-ttu-id="54e90-116">Jeśli utworzono plik wyjściowy **/target** opcji innych niż **/target: module**, nie można zaimportować metadanych z **/addmodule** , ale mogą być importowane przy [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="54e90-116">If the output file was created with a **/target** option other than **/target:module**, its metadata cannot be imported with **/addmodule** but can be imported with [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md).</span></span>  
  
 <span data-ttu-id="54e90-117">Ta opcja kompilatora jest niedostępna w programie Visual Studio; Projekt nie może odwoływać się do modułu.</span><span class="sxs-lookup"><span data-stu-id="54e90-117">This compiler option is unavailable in Visual Studio; a project cannot reference a module.</span></span> <span data-ttu-id="54e90-118">Ponadto kompilatora nie można zmienić tej opcji programowo.</span><span class="sxs-lookup"><span data-stu-id="54e90-118">In addition, this compiler option cannot be changed programmatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54e90-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="54e90-119">Example</span></span>  
 <span data-ttu-id="54e90-120">Kompiluj plik źródłowy `input.cs` i Dodaj metadane z `metad1.netmodule` i `metad2.netmodule` do produkcji `out.exe`:</span><span class="sxs-lookup"><span data-stu-id="54e90-120">Compile source file `input.cs` and add metadata from `metad1.netmodule` and `metad2.netmodule` to produce `out.exe`:</span></span>  
  
```console  
csc /addmodule:metad1.netmodule;metad2.netmodule /out:out.exe input.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="54e90-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54e90-121">See Also</span></span>  
 [<span data-ttu-id="54e90-122">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="54e90-122">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="54e90-123">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="54e90-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="54e90-124">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="54e90-124">Multifile Assemblies</span></span>](../../../framework/app-domains/multifile-assemblies.md)  
 [<span data-ttu-id="54e90-125">Porady: kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="54e90-125">How to: Build a Multifile Assembly</span></span>](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)