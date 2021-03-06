---
title: "ICLRTask2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8701cff3400e46660fac90486cf5648d29aa9972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask2-interface"></a>ICLRTask2 — Interfejs
Zawiera wszystkie funkcje [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interfejsu; ponadto udostępnia metody umożliwiające przerwanie wątku opóźnionych w bieżącym wątku.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginPreventAsyncAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|Opóźnienia nowego wątku przerwać żądania w bieżącym wątku.|  
|[EndPreventAsyncAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|Zezwala na nowe lub oczekujące żądania przerwania wątku w wątku przerywa w bieżącym wątku.|  
  
## <a name="remarks"></a>Uwagi  
 `ICLRTask2` Dziedziczy interfejs `ICLRTask` interfejsu i dodaje metod umożliwiających hosta opóźnienia wątku jest przerywana, aby chronić region kodu, który musi zakończyć się niepowodzeniem. Wywoływanie `BeginPreventAsyncAbort` zwiększa licznik opóźnienie wątku przerwania dla bieżącego wątku i wywoływania `EndPreventAsyncAbort` zmniejsza go. Wywołuje się `BeginPreventAsyncAbort` i `EndPreventAsyncAbort` mogą być zagnieżdżone. Tak długo, jak wartość licznika jest większa niż zero, opóźnienia przerwania wątku dla bieżącego wątku.  
  
 Jeśli wywołań `BeginPreventAsyncAbort` i `EndPreventAsyncAbort` są nie łączyć, istnieje możliwość przejścia w wątku, który przerwań nie może zostać dostarczona do bieżącego wątku.  
  
 Opóźnienie nie jest honorowana dla wątku, który przerywa samej siebie.  
  
 Funkcje, które jest udostępniane przez tę funkcję jest używana wewnętrznie przez maszynę wirtualną (VM). Nieprawidłowe użycie tych metod może spowodować nieokreślony zachowanie w maszynie Wirtualnej. Na przykład wywołanie elementu `EndPreventAsyncAbort` bez wywoływania pierwszego elementu `BeginPreventAsyncAbort` można ustawić licznik do zera, gdy maszyna wirtualna wcześniej ma zwiększany. Podobnie wewnętrzny licznik nie jest sprawdzany pod kątem przepełnienia. W razie przekroczenia limitu całkowitej, ponieważ jest zwiększany przez hosta i maszyny Wirtualnej, efekty jest nieokreślony.  
  
 Dla informacji o elementach członkowskich odziedziczone `ICLRTask` i informacji na temat innych celów tego interfejsu, zobacz [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) interfejsu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
