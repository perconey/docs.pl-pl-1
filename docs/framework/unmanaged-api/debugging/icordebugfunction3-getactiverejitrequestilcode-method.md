---
title: Metoda ICorDebugFunction3::GetActiveReJitRequestILCode
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: cpp
api_name: ICorDebugFunction3.GetActiveReJitRequestILCode
api_location: mscordbi.dll
api_type: COM
ms.assetid: 88584574-ade5-45b2-9778-489ed5c4dd7f
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6459297a2a04728ca87801bfc8484acec384a45c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugfunction3getactiverejitrequestilcode-method"></a><span data-ttu-id="a18ad-102">Metoda ICorDebugFunction3::GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="a18ad-102">ICorDebugFunction3::GetActiveReJitRequestILCode Method</span></span>
<span data-ttu-id="a18ad-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="a18ad-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a18ad-104">Pobiera wskaźnika interfejsu do [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) zawierający IL z aktywne żądanie ReJIT.</span><span class="sxs-lookup"><span data-stu-id="a18ad-104">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a18ad-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="a18ad-105">Syntax</span></span>  
  
```cpp
HRESULT GetActiveReJitRequestILCode(  
   ICorDebugILCode **ppReJitedILCode  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a18ad-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="a18ad-106">Parameters</span></span>  
 `ppReJitedILCode`  
 <span data-ttu-id="a18ad-107">Wskaźnik do IL z aktywne żądanie ReJIT.</span><span class="sxs-lookup"><span data-stu-id="a18ad-107">A pointer to the IL from an active ReJIT request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a18ad-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a18ad-108">Remarks</span></span>  
 <span data-ttu-id="a18ad-109">Jeśli metoda reprezentowany przez to `ICorDebugFunction3` obiekt ma aktywne żądanie ReJIT `ppReJitedILCode` zwraca wskaźnik do jego IL.</span><span class="sxs-lookup"><span data-stu-id="a18ad-109">If the method represented by this `ICorDebugFunction3` object has an active ReJIT request, `ppReJitedILCode` returns a pointer to its IL.</span></span> <span data-ttu-id="a18ad-110">Jeśli nie istnieje żadne aktywne żądanie, który jest następnie typowych przypadkach, `ppReJitedILCode` jest **null**.</span><span class="sxs-lookup"><span data-stu-id="a18ad-110">If there is no active request, which is a common case, then `ppReJitedILCode` is **null**.</span></span>  
  
 <span data-ttu-id="a18ad-111">Żądanie ReJIT staje się aktywny tuż po wykonywania zwraca z [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="a18ad-111">A ReJIT request becomes active just after execution returns from the [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) method call.</span></span> <span data-ttu-id="a18ad-112">Nie może jeszcze być skompilowany JIT i wątków nadal mogą być wykonywane w oryginalnej wersji kodu.</span><span class="sxs-lookup"><span data-stu-id="a18ad-112">It may not yet be JIT-compiled, and threads may still be executing in the original version of the code.</span></span> <span data-ttu-id="a18ad-113">Żądanie ReJIT staje się nieaktywny podczas wywołania profilera [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a18ad-113">A ReJIT request becomes inactive during the profiler's call to the [ICorProfilerInfo4::RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) method.</span></span> <span data-ttu-id="a18ad-114">Nawet po IL zostanie przywrócony, wątek nadal można wykonywane w kodzie ponownie kompilowana JIT (ReJIT).</span><span class="sxs-lookup"><span data-stu-id="a18ad-114">Even after the IL is reverted, a thread can still be executing in the JIT-recompiled (ReJIT) code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a18ad-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a18ad-115">Requirements</span></span>  
 <span data-ttu-id="a18ad-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a18ad-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a18ad-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a18ad-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a18ad-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a18ad-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a18ad-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a18ad-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a18ad-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a18ad-120">See Also</span></span>  
 [<span data-ttu-id="a18ad-121">Interfejs ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="a18ad-121">ICorDebugFunction3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 [<span data-ttu-id="a18ad-122">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="a18ad-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a18ad-123">ReJIT: Przewodnik</span><span class="sxs-lookup"><span data-stu-id="a18ad-123">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)