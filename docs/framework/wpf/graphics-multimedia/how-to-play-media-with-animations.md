---
title: "Jak odtworzyć z nośnika z animacjami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multimedia [WPF], playback with animations
- playback of media [WPF], with animations
- animation [WPF], media playback with
- media [WPF], playback with animations
ms.assetid: 8982b7b7-1c6c-4b24-8801-b328862975f5
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fb5fd3575a0caa692e4a4013452e3069210c9a4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-play-media-with-animations"></a><span data-ttu-id="5efe7-102">Jak odtworzyć z nośnika z animacjami</span><span class="sxs-lookup"><span data-stu-id="5efe7-102">How to: Play Media with Animations</span></span>
<span data-ttu-id="5efe7-103">W tym przykładzie pokazano, jak odtwarzanie multimediów i animacji w tym samym czasie przy użyciu <xref:System.Windows.Media.MediaTimeline> i <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> klas w tym samym <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="5efe7-103">This example shows how to play media and animations at the same time by using the <xref:System.Windows.Media.MediaTimeline> and <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> classes in the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5efe7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="5efe7-104">Example</span></span>  
 <span data-ttu-id="5efe7-105">Można użyć co najmniej jeden <xref:System.Windows.Media.MediaTimeline> obiekty w <xref:System.Windows.Media.Animation.Storyboard> wraz z innymi <xref:System.Windows.Media.Animation.Timeline> obiekty, takie jak animacji.</span><span class="sxs-lookup"><span data-stu-id="5efe7-105">You can use one or more <xref:System.Windows.Media.MediaTimeline> objects in a <xref:System.Windows.Media.Animation.Storyboard> together with other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span>  
  
 <span data-ttu-id="5efe7-106">W poniższym przykładzie <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> właściwość <xref:System.Windows.Media.Animation.Storyboard> wartość `Slip`, który określa, że animacja nie postępu aż do realizowany nośnika (klip wideo w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="5efe7-106">The following example sets the <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A> property of the <xref:System.Windows.Media.Animation.Storyboard> to a value of `Slip`, which specifies that the animation does not progress until the media (video in this example) progresses.</span></span> <span data-ttu-id="5efe7-107">Ta funkcja może być konieczna, jeśli odtwarzanie multimediów jest opóźnione z powodu czasu ładowania.</span><span class="sxs-lookup"><span data-stu-id="5efe7-107">This functionality might be needed if media playback is delayed because of loading time.</span></span>  
  
 [!code-xaml[MediaGallery_snippet#MediaTimelinePlusAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snippet/CSharp/MediaTimelinePlusAnimationExample.xaml#mediatimelineplusanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="5efe7-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5efe7-108">See Also</span></span>  
 <xref:System.Windows.Media.MediaTimeline>  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 <xref:System.Windows.Media.Animation.ParallelTimeline.SlipBehavior%2A>  
 [<span data-ttu-id="5efe7-109">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="5efe7-109">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/audio-and-video-how-to-topics.md)  
 [<span data-ttu-id="5efe7-110">Scenorys — omówienie</span><span class="sxs-lookup"><span data-stu-id="5efe7-110">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [<span data-ttu-id="5efe7-111">Omówienie klucza poklatkowych</span><span class="sxs-lookup"><span data-stu-id="5efe7-111">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="5efe7-112">Animacja — omówienie</span><span class="sxs-lookup"><span data-stu-id="5efe7-112">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="5efe7-113">Grafika i Multimedia</span><span class="sxs-lookup"><span data-stu-id="5efe7-113">Graphics and Multimedia</span></span>](../../../../docs/framework/wpf/graphics-multimedia/index.md)