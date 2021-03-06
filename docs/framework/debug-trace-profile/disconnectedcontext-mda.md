---
title: disconnectedContext MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90e840fc24361735b65879702293daadce0bc90e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="disconnectedcontext-mda"></a>disconnectedContext MDA
`disconnectedContext` Zarządzany Asystent debugowania (MDA) została aktywowana, podczas próby przejścia do odłączonego apartamentu lub kontekstu podczas obsługi żądania dotyczące obiektu COM środowiska CLR.  
  
## <a name="symptoms"></a>Symptomy  
 Wywołania [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (otoki RCW) są dostarczane do podstawowy składnik modelu COM w bieżącego apartamentu lub kontekstu zamiast takie istnieją. Może to spowodować uszkodzenie i lub utratę danych, jeśli składnik modelu COM nie jest wielowątkowe, tak jak w przypadku składników jednowątkowego apartamentu (STA). Alternatywnie, jeśli Otoka RCW jest serwer proxy, wywołanie może spowodować przerzucane o <xref:System.Runtime.InteropServices.COMException> z HRESULT RPC_E_WRONG_THREAD.  
  
## <a name="cause"></a>Przyczyna  
 OLE apartamentu lub kontekstu została zamknięta podczas próby przejścia do niego środowiska CLR. Najczęściej jest to spowodowane apartamentach STA, zamykana przed wszystkie składniki COM własnością apartamencie całkowicie zostały zwolnione, to może wystąpić w wyniku jawnym wywołaniem z kodu użytkownika otoki RCW lub gdy sam CLR jest manipulowanie składnika modelu COM , na przykład podczas CLR udostępnia składnika modelu COM, gdy skojarzona Otoka RCW została wyrzucona jako element bezużyteczny.  
  
## <a name="resolution"></a>Rozwiązanie  
 Aby uniknąć tego problemu, upewnij się, że wątek, który jest właścicielem STA nie kończy się przed wszystkie obiekty, które znajdują się w apartamencie aplikacji zostało zakończone. To samo dotyczy kontekstów; Upewnij się, że kontekstach nie są zamknięte przed całkowicie zakończono z wszystkie składniki modelu COM, które na żywo w kontekście aplikacji.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Zwraca tylko dane o rozłączona kontekście.  
  
## <a name="output"></a>Dane wyjściowe  
 Raporty cookie kontekstu odłączonego apartamentu lub kontekstu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
