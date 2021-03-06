---
title: "ICLRRuntimeHost::SetHostControl — Metoda"
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
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9727144e9504a5a3ad7ae2529286440d07633b2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostsethostcontrol-method"></a>ICLRRuntimeHost::SetHostControl — Metoda
Ustawia wskaźnik interfejsu używanego przez środowisko uruchomieniowe języka wspólnego (CLR) Aby uzyskać implementację hosta [IHostControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pHostControl`  
 [in] Wskaźnik interfejsu do wdrożenia hosta [IHostControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetHostControl`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
|E_CLR_ALREADY_STARTED|Środowisko CLR został już zainicjowany.|  
  
## <a name="remarks"></a>Uwagi  
 Należy wywołać `SetHostControl` przed środowiska CLR został zainicjowany, oznacza to, że przed wywołaniem [Metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) lub użyć innych [interfejsy metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md). Zalecane jest telefoniczne skontaktowanie się z `SetHostControl` natychmiast po wywołaniu [CorBindToCurrentRuntime — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) lub [CorBindToRuntimeEx — funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [IHostControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
