---
title: "Jak utworzyć krzywą Beziera trzeciego stopnia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- curves [WPF], cubic Bezier
- Bezier curves [WPF], cubic
- graphics [WPF], cubic Bezier curves
- cubic Bezier curves [WPF]
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35d4fad0634586d5d0c6ea85f276d6e76edb3f63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-cubic-bezier-curve"></a><span data-ttu-id="d4084-102">Jak utworzyć krzywą Beziera trzeciego stopnia</span><span class="sxs-lookup"><span data-stu-id="d4084-102">How to: Create a Cubic Bezier Curve</span></span>
<span data-ttu-id="d4084-103">W tym przykładzie przedstawiono sposób tworzenia sześcienny krzywą Beziera.</span><span class="sxs-lookup"><span data-stu-id="d4084-103">This example shows how to create a cubic Bezier curve.</span></span> <span data-ttu-id="d4084-104">Aby utworzyć sześcienny krzywej Beziera, użyj <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, i <xref:System.Windows.Media.BezierSegment> klasy.</span><span class="sxs-lookup"><span data-stu-id="d4084-104">To create a cubic Bezier curve, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.BezierSegment> classes.</span></span>  <span data-ttu-id="d4084-105">Aby wyświetlić wynikowe geometry, użyj <xref:System.Windows.Shapes.Path> elementu, lub użyj go przy użyciu <xref:System.Windows.Media.GeometryDrawing> lub <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="d4084-105">To display the resulting geometry, use a <xref:System.Windows.Shapes.Path> element, or use it with a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="d4084-106">W poniższych przykładach sześcienny krzywej Beziera jest przenoszony z (10, 100) do (300, 100).</span><span class="sxs-lookup"><span data-stu-id="d4084-106">In the following examples, a cubic Bezier curve is drawn from (10, 100) to (300, 100).</span></span> <span data-ttu-id="d4084-107">Krzywej ma punkty kontrolne (100, 0) i (200, 200).</span><span class="sxs-lookup"><span data-stu-id="d4084-107">The curve has control points of (100, 0) and (200, 200).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4084-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="d4084-108">Example</span></span>  
 <span data-ttu-id="d4084-109">[xaml]</span><span class="sxs-lookup"><span data-stu-id="d4084-109">[xaml]</span></span>  
  
 <span data-ttu-id="d4084-110">W [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], może użyć składni skróconej znaczników opisujący ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="d4084-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use abbreviated markup syntax to describe a path.</span></span>  
  
 [!code-xaml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 <span data-ttu-id="d4084-111">[xaml]</span><span class="sxs-lookup"><span data-stu-id="d4084-111">[xaml]</span></span>  
  
 <span data-ttu-id="d4084-112">W [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], możesz także rysować sześcienny krzywej Beziera przy użyciu tagów object.</span><span class="sxs-lookup"><span data-stu-id="d4084-112">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you can also draw a cubic Bezier curve using object tags.</span></span> <span data-ttu-id="d4084-113">Poniżej przedstawiono odpowiednikiem poprzedniego [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] przykład.</span><span class="sxs-lookup"><span data-stu-id="d4084-113">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>  
  
 [!code-xaml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 <span data-ttu-id="d4084-114">Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [próbki mają geometrię](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="d4084-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4084-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4084-115">See Also</span></span>  
 [<span data-ttu-id="d4084-116">Utwórz łuku</span><span class="sxs-lookup"><span data-stu-id="d4084-116">Create an Elliptical Arc</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)  
 [<span data-ttu-id="d4084-117">Utwórz obiekt LineSegment w PathGeometry</span><span class="sxs-lookup"><span data-stu-id="d4084-117">Create a LineSegment in a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)  
 [<span data-ttu-id="d4084-118">Tworzenie sześcienny krzywej Beziera</span><span class="sxs-lookup"><span data-stu-id="d4084-118">Create a Cubic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)  
 [<span data-ttu-id="d4084-119">Tworzenie kwadratową krzywej Beziera</span><span class="sxs-lookup"><span data-stu-id="d4084-119">Create a Quadratic Bezier Curve</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)