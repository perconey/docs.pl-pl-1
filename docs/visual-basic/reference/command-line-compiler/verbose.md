---
title: /verbose
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5480f828fa1f0b6d71fa649bf44513ce806bb440
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="verbose"></a><span data-ttu-id="40ace-102">/verbose</span><span class="sxs-lookup"><span data-stu-id="40ace-102">/verbose</span></span>
<span data-ttu-id="40ace-103">Powoduje, że kompilator, aby utworzyć pełne komunikaty o stanie i błędach.</span><span class="sxs-lookup"><span data-stu-id="40ace-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40ace-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40ace-104">Syntax</span></span>  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="40ace-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="40ace-105">Arguments</span></span>  
 <span data-ttu-id="40ace-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="40ace-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="40ace-107">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="40ace-107">Optional.</span></span> <span data-ttu-id="40ace-108">Określanie `/verbose` jest taka sama jak określanie `/verbose+`, co powoduje, że kompilator, aby wysyłać komunikaty pełne.</span><span class="sxs-lookup"><span data-stu-id="40ace-108">Specifying `/verbose` is the same as specifying `/verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="40ace-109">Wartość domyślna dla tej opcji to `/verbose-`.</span><span class="sxs-lookup"><span data-stu-id="40ace-109">The default for this option is `/verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40ace-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40ace-110">Remarks</span></span>  
 <span data-ttu-id="40ace-111">`/verbose` Opcja wyświetla informacje o całkowita liczba błędów wystawiony przez kompilator, raporty, zestawy, które są ładowane przez moduł oraz pliki, które są aktualnie kompilowana.</span><span class="sxs-lookup"><span data-stu-id="40ace-111">The `/verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40ace-112">`/verbose` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="40ace-112">The `/verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40ace-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="40ace-113">Example</span></span>  
 <span data-ttu-id="40ace-114">Poniższy kod kompiluje `In.vb` i kieruje kompilatora, aby wyświetlić informacje o stanie pełne.</span><span class="sxs-lookup"><span data-stu-id="40ace-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="40ace-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="40ace-115">See Also</span></span>  
 [<span data-ttu-id="40ace-116">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40ace-116">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="40ace-117">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="40ace-117">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)