---
title: "ICorDebugRemote::DebugActiveProcessEx — Metoda"
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
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09bc98b477231eb1466300451585f4569aff222c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx — Metoda
Uruchamia proces na komputerze zdalnym w debugerze.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRemoteTarget`  
 [in] Wskaźnik do [ICorDebugRemoteTarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Ten parametr jest używany do określenia maszyny, na którym jest uruchomiony proces.  
  
 `id`  
 [in] Identyfikator procesu, do którego ma zostać dołączony debuger.  
  
 `win32Attach`  
 [in] `true` Jeśli debuger powinna zachowywać się jako debuger Win32 dla procesu i wysłać niezarządzane wywołania zwrotne; w przeciwnym razie `false`.  
  
 `ppProcess`  
 [out] Wskaźnik do adresu obiektu "ICorDebugProcess", który reprezentuje proces, do którego został dołączony debuger.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Pomyślnie dołączono do procesu na komputerze zdalnym.  
  
 E_FAIL (lub inne kody powrotu E_)  
 Nie można dołączyć do procesu na komputerze zdalnym.  
  
## <a name="remarks"></a>Uwagi  
 Debugowanie w trybie mieszanym nie jest obsługiwane w programie Silverlight.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** 4.5, 4, 3.5 z dodatkiem SP1  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugRemote, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
