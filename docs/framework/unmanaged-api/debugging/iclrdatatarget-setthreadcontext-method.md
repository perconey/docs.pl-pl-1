---
title: "ICLRDataTarget::SetThreadContext — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.SetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::SetThreadContext
helpviewer_keywords:
- SetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::SetThreadContext method [.NET Framework debugging]
ms.assetid: 103c8502-81fe-40d7-9c1e-9008d8fb19e1
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e51cbafda76933d58bd60be8db7dd163a2dd59d3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetsetthreadcontext-method"></a><span data-ttu-id="61bd8-102">ICLRDataTarget::SetThreadContext — Metoda</span><span class="sxs-lookup"><span data-stu-id="61bd8-102">ICLRDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="61bd8-103">Ustawia bieżący kontekst określonego wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="61bd8-103">Sets the current context of the specified thread in the target process.</span></span> <span data-ttu-id="61bd8-104">Ta metoda jest wywoływana przez wspólne usługi dostępu do danych języka środowiska uruchomieniowego (języka wspólnego CLR).</span><span class="sxs-lookup"><span data-stu-id="61bd8-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61bd8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="61bd8-105">Syntax</span></span>  
  
```  
HRESULT SetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextSize,  
    [in, size_is(contextSize)]   
         BYTE               *context  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="61bd8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="61bd8-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="61bd8-107">[in] System operacyjny identyfikator wątku w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="61bd8-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="61bd8-108">[in] Rozmiar kontekstu.</span><span class="sxs-lookup"><span data-stu-id="61bd8-108">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="61bd8-109">[in] Wskaźnik do bufor zawierający kontekst.</span><span class="sxs-lookup"><span data-stu-id="61bd8-109">[in] Pointer to a buffer containing the context.</span></span>  
  
 <span data-ttu-id="61bd8-110">Dane w `context` buforu będą w formacie Win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="61bd8-110">The data in the `context` buffer will be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="61bd8-111">Kontekst określa dane rejestru specyficznych dla procesora, więc definicji Win32 `CONTEXT` struktury jest zależna od architektury procesora.</span><span class="sxs-lookup"><span data-stu-id="61bd8-111">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="61bd8-112">Zajrzyj do pliku nagłówka pliku WinNT.h definicji Win32 `CONTEXT` struktury.</span><span class="sxs-lookup"><span data-stu-id="61bd8-112">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61bd8-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61bd8-113">Remarks</span></span>  
 <span data-ttu-id="61bd8-114">Ta metoda jest implementowany przez twórcę debugowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="61bd8-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61bd8-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61bd8-115">Requirements</span></span>  
 <span data-ttu-id="61bd8-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61bd8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61bd8-117">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="61bd8-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="61bd8-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61bd8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61bd8-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61bd8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61bd8-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61bd8-120">See Also</span></span>  
 [<span data-ttu-id="61bd8-121">ICLRDataTarget — interfejs</span><span class="sxs-lookup"><span data-stu-id="61bd8-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)