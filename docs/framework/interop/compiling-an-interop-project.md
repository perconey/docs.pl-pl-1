---
title: "Kompilowanie projektu międzyoperacyjnego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc541911670c533caa97c645085ad09bde5eefdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="compiling-an-interop-project"></a><span data-ttu-id="8c82f-102">Kompilowanie projektu międzyoperacyjnego</span><span class="sxs-lookup"><span data-stu-id="8c82f-102">Compiling an Interop Project</span></span>
<span data-ttu-id="8c82f-103">COM interop projektów, odwołujące się do jednego lub więcej zestawów zawierających importowanych typów COM są kompilowane jak zarządzanego projektu.</span><span class="sxs-lookup"><span data-stu-id="8c82f-103">COM interop projects that reference one or more assemblies containing imported COM types are compiled like any other managed project.</span></span> <span data-ttu-id="8c82f-104">Możesz odwoływać się do zestawów międzyoperacyjnych w środowisku programowania, takiego jak Visual Studio, lub możesz odwoływać się do ich używania kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="8c82f-104">You can reference interop assemblies in a development environment such as Visual Studio, or you can reference them when you use a command-line compiler.</span></span> <span data-ttu-id="8c82f-105">W obu przypadkach skompilować poprawnie, zestawu międzyoperacyjnego musi być w tym samym katalogu co plik projektu.</span><span class="sxs-lookup"><span data-stu-id="8c82f-105">In either case, to compile properly, the interop assembly must be in the same directory as the other project files.</span></span>  
  
 <span data-ttu-id="8c82f-106">Istnieją dwa sposoby odwołania zestawów międzyoperacyjnych:</span><span class="sxs-lookup"><span data-stu-id="8c82f-106">There are two ways to reference interop assemblies:</span></span>  
  
-   <span data-ttu-id="8c82f-107">Osadzone typy współdziałania: począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] i [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], można nakazać kompilatorowi osadzanie informacji o typie z zestawu międzyoperacyjnego do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="8c82f-107">Embedded interop types: Beginning with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] and [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], you can instruct the compiler to embed type information from an interop assembly into your executable.</span></span> <span data-ttu-id="8c82f-108">Jest to zalecana technika.</span><span class="sxs-lookup"><span data-stu-id="8c82f-108">This is the recommended technique.</span></span>  
  
-   <span data-ttu-id="8c82f-109">Zestawy międzyoperacyjne wdrażania: można utworzyć standardowe odwołanie do zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8c82f-109">Deploying interop assemblies: You can create a standard reference to an interop assembly.</span></span> <span data-ttu-id="8c82f-110">W takim przypadku należy wdrożyć zestawu międzyoperacyjnego z aplikacją.</span><span class="sxs-lookup"><span data-stu-id="8c82f-110">In this case, the interop assembly must be deployed with your application.</span></span>  
  
 <span data-ttu-id="8c82f-111">Różnice między te dwie metody omówiono bardziej szczegółowo w [przy użyciu typów COM w kod zarządzany](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).</span><span class="sxs-lookup"><span data-stu-id="8c82f-111">The differences between these two techniques are discussed in greater detail in [Using COM Types in Managed Code](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66).</span></span>  
  
 <span data-ttu-id="8c82f-112">Osadzanie typów międzyoperacyjnych z programem Visual Studio jest przedstawiona w [wskazówki: osadzanie informacji o typie z zestawów Microsoft Office](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) i [wskazówki: osadzanie typów z zarządzanych zestawów](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span><span class="sxs-lookup"><span data-stu-id="8c82f-112">Embedding interop types with Visual Studio is demonstrated in [Walkthrough: Embedding Type Information from Microsoft Office Assemblies](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3) and [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
 <span data-ttu-id="8c82f-113">Odwołanie do zestawu międzyoperacyjnego z wiersza polecenia kompilatora i osadzanie informacji o typie w Twoje pliki wykonywalne, użyj [/Link (opcje kompilatora C#)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) lub [/Link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) przełącznika kompilatora i Określ nazwę zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8c82f-113">To reference an interop assembly with a command-line compiler and embed type information in your executables, use the [/link (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/link-compiler-option.md) or the [/link (Visual Basic)](~/docs/visual-basic/reference/command-line-compiler/link.md) compiler switch and specify the name of the interop assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8c82f-114">Aplikacje programu Visual C++ nie można osadzić typu informacji, ale mogą współdziałać aplikacji lub dodatki, które wykonują.</span><span class="sxs-lookup"><span data-stu-id="8c82f-114">Visual C++ applications cannot embed type information, but they can interoperate with applications or add-ins that do.</span></span>  
  
 <span data-ttu-id="8c82f-115">Aby skompilować aplikację, która zawiera podstawowy zestaw międzyoperacyjny po jej wdrożeniu, należy użyć **/reference** kompilatora przełącznika i określ nazwę zestawu międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8c82f-115">To compile an application that includes a primary interop assembly when it is deployed, use the **/reference** compiler switch and specify the name of the interop assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c82f-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c82f-116">See Also</span></span>  
 [<span data-ttu-id="8c82f-117">Udostępnianie składników modelu COM aplikacji .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8c82f-117">Exposing COM Components to the .NET Framework</span></span>](../../../docs/framework/interop/exposing-com-components.md)  
 [<span data-ttu-id="8c82f-118">Niezależność od języka i elementy niezależne od języka</span><span class="sxs-lookup"><span data-stu-id="8c82f-118">Language Independence and Language-Independent Components</span></span>](../../../docs/standard/language-independence-and-language-independent-components.md)  
 [<span data-ttu-id="8c82f-119">Używanie typów COM w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="8c82f-119">Using COM Types in Managed Code</span></span>](http://msdn.microsoft.com/en-us/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)  
 [<span data-ttu-id="8c82f-120">Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="8c82f-120">Walkthrough: Embedding Type Information from Microsoft Office Assemblies</span></span>](http://msdn.microsoft.com/library/85b55e05-bc5e-4665-b6ae-e1ada9299fd3)  
 [<span data-ttu-id="8c82f-121">Wskazówki: Osadzanie typów z zarządzanych zestawów</span><span class="sxs-lookup"><span data-stu-id="8c82f-121">Walkthrough: Embedding Types from Managed Assemblies</span></span>](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)  
 [<span data-ttu-id="8c82f-122">Importowanie biblioteki typów jako zestawu</span><span class="sxs-lookup"><span data-stu-id="8c82f-122">Importing a Type Library as an Assembly</span></span>](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)