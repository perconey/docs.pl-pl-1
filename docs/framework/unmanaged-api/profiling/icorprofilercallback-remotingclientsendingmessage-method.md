---
title: "ICorProfilerCallback::RemotingClientSendingMessage — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RemotingClientSendingMessage
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RemotingClientSendingMessage
helpviewer_keywords:
- RemotingClientSendingMessage method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientSendingMessage method [.NET Framework profiling]
ms.assetid: 54d9a5a5-3877-49c1-a503-ce7c7943bc2a
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a77acb736cec02da6839335e981016469eeb42b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackremotingclientsendingmessage-method"></a><span data-ttu-id="90bd6-102">ICorProfilerCallback::RemotingClientSendingMessage — Metoda</span><span class="sxs-lookup"><span data-stu-id="90bd6-102">ICorProfilerCallback::RemotingClientSendingMessage Method</span></span>
<span data-ttu-id="90bd6-103">Powiadamia profilera, że klient wysyła żądanie do serwera.</span><span class="sxs-lookup"><span data-stu-id="90bd6-103">Notifies the profiler that the client is sending a request to the server.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90bd6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="90bd6-104">Syntax</span></span>  
  
```  
HRESULT RemotingClientSendingMessage(  
    [in] GUID *pCookie,  
    [in] BOOL fIsAsync);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90bd6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="90bd6-105">Parameters</span></span>  
 `pCookie`  
 <span data-ttu-id="90bd6-106">[in] Wartość uniemożliwiająca z podanej wartości w [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) w tych warunkach:</span><span class="sxs-lookup"><span data-stu-id="90bd6-106">[in] A value that corresponds with the value provided in [ICorProfilerCallback::RemotingServerReceivingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md) under these conditions:</span></span>  
  
-   <span data-ttu-id="90bd6-107">Pliki cookie GUID komunikacji zdalnej są aktywne.</span><span class="sxs-lookup"><span data-stu-id="90bd6-107">Remoting GUID cookies are active.</span></span>  
  
-   <span data-ttu-id="90bd6-108">Kanał pomyślnie przesyła komunikat.</span><span class="sxs-lookup"><span data-stu-id="90bd6-108">The channel succeeds in transmitting the message.</span></span>  
  
-   <span data-ttu-id="90bd6-109">Identyfikator GUID pliki cookie są aktywne w procesie po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="90bd6-109">GUID cookies are active on the server-side process.</span></span>  
  
 <span data-ttu-id="90bd6-110">Umożliwia łatwe parowanie wywołań zdalnych i Tworzenie stosu wywołań logiczne.</span><span class="sxs-lookup"><span data-stu-id="90bd6-110">This allows easy pairing of remoting calls and the creation of a logical call stack.</span></span>  
  
 `fIsAsync`  
 <span data-ttu-id="90bd6-111">[in] Wartość, która jest `true` Jeśli wywołanie jest asynchroniczne, a w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="90bd6-111">[in] A value that is `true` if the call is asynchronous; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90bd6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90bd6-112">Requirements</span></span>  
 <span data-ttu-id="90bd6-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90bd6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90bd6-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="90bd6-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90bd6-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90bd6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90bd6-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90bd6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90bd6-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90bd6-117">See Also</span></span>  
 [<span data-ttu-id="90bd6-118">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="90bd6-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)