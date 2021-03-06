---
title: "Włączanie debugowania dołączania JIT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71b2e95076edbda3a67a84c9185d8b689c158e12
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="enabling-jit-attach-debugging"></a>Włączanie debugowania dołączania JIT
Debugowanie dołączania JIT jest hasło używane do opisywania dołączanie debugera do procesu, gdy wystąpią błędy, lub mogą być wyzwalane przez określone metody lub funkcji.  
  
 Debugowanie dołączania JIT jest używany w następujących warunkach błędów:  
  
-   Nieobsługiwane wyjątki (w kodzie natywnych i zarządzanych).  
  
-   <xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Metoda lub [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) — funkcja (rodziny Windows 7).  
  
-   Błędy krytyczne podczas wykonywania.  
  
 Debugowanie dołączania JIT również jest wyzwalany przez wywołania z funkcji i następujących metod:  
  
-   <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>Metoda.  
  
-   <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>Metoda.  
  
-   [Debugbreak —](http://go.microsoft.com/fwlink/?LinkId=182106) — funkcja (Win32).  
  
 Przed [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework podane klucze rejestru oddzielne do sterowania zachowaniem debugery natywnych i zarządzanych. Począwszy od [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], sterowania są konsolidowane w kluczu rejestru pojedynczego: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. Wartości, które można ustawić dla tego klucza określają, czy debuger jest wywoływany, a jeśli tak, czy jest wywoływana z okna dialogowego wymaga interakcji użytkownika. Aby uzyskać informacje o ustawieniu tego klucza rejestru, zobacz [Konfigurowanie automatycznego debugowania](http://go.microsoft.com/fwlink/?LinkId=181767).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, śledzenie i profilowanie](../../../docs/framework/debug-trace-profile/index.md)  
 [Ułatwianie debugowania obrazu](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [Włączenie profilowania](http://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
