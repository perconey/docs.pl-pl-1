---
title: "StrongNameKeyGen — Funkcja"
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
- StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen function [.NET Framework strong naming]
ms.assetid: 883e413a-ad2f-4f7f-b1b9-aeb8fe5b65f8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e3bb9530884f61345d439ec8662a088e1d152de7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeygen-function"></a>StrongNameKeyGen — Funkcja
Tworzy nową parę kluczy publicznych/prywatnych do użytku silnej nazwy.  
  
 Ta funkcja jest przestarzała. Użyj [ICLRStrongName::StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) metody zamiast tego.  
  
## <a name="syntax"></a>Składnia  
  
```  
BOOLEAN StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszKeyContainer`  
 [in] Nazwa żądanego kontenera kluczy. `wszKeyContainer`musi być niepustym ciągiem, lub wartość null, można wygenerować tymczasowej nazwy.  
  
 `dwFlags`  
 [in] Określa, czy należy pozostawić klawisz zarejestrowany. Obsługiwane są następujące wartości:  
  
-   0x00000000 — używany, gdy `wszKeyContainer` ma wartość null, można wygenerować nazwy kontenera kluczy tymczasowych.  
  
-   0x00000001 (`SN_LEAVE_KEY`) — określa, czy klucz powinien być zarejestrowany po lewej.  
  
 `ppbKeyBlob`  
 [out] Zwrócony pary kluczy publiczny/prywatny.  
  
 `pcbKeyBlob`  
 [out] Rozmiar w bajtach z `ppbKeyBlob`.  
  
## <a name="return-value"></a>Wartość zwracana  
 `true`Po pomyślnym ukończeniu; w przeciwnym razie `false`.  
  
## <a name="remarks"></a>Uwagi  
 `StrongNameKeyGen` Funkcja tworzy 1024-bitowego klucza. Po pobraniu klucza, należy wywołać [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) funkcji, aby zwolnić alokacji pamięci.  
  
 Jeśli `StrongNameKeyGen` funkcji nie powiodło się, wywołania [strongnameerrorinfo —](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkcji, aby pobrać ostatniego wygenerowany błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** StrongName.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [StrongNameKeyGen, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)  
 [StrongNameKeyGenEx, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)  
 [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
