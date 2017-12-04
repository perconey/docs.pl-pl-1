---
title: "ICorProfilerInfo3::EnumJITedFunctions — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.EnumJITedFunctions Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2c367ae29cc0daa406356a245f3dc16a671d3c54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a><span data-ttu-id="81131-102">ICorProfilerInfo3::EnumJITedFunctions — Metoda</span><span class="sxs-lookup"><span data-stu-id="81131-102">ICorProfilerInfo3::EnumJITedFunctions Method</span></span>
<span data-ttu-id="81131-103">Zwraca moduł wyliczający dla wszystkich funkcji, które były wcześniej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="81131-103">Returns an enumerator for all functions that were previously JIT-compiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81131-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81131-104">Syntax</span></span>  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81131-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81131-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="81131-106">[out] Wskaźnik do [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="81131-106">[out] A pointer to the [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) enumerator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81131-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81131-107">Remarks</span></span>  
 <span data-ttu-id="81131-108">Ta metoda może nakładać się na `JITCompilation` wywołań zwrotnych, takich jak [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="81131-108">This method may overlap with `JITCompilation` callbacks such as the [ICorProfilerCallback::JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) method.</span></span> <span data-ttu-id="81131-109">Moduł wyliczający zwracane przez tę metodę nie obejmuje funkcje, które są ładowane z obrazów macierzystych wygenerowane z Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="81131-109">The enumerator returned by this method does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81131-110">Wyliczenie zwrócony obejmuje tylko "0" dla wartości `COR_PRF_FUNCTION::reJitId` pola.</span><span class="sxs-lookup"><span data-stu-id="81131-110">The returned enumeration includes only "0" for the value of the `COR_PRF_FUNCTION::reJitId` field.</span></span>  <span data-ttu-id="81131-111">Jeśli potrzebujesz prawidłową `COR_PRF_FUNCTION::reJitId` wartości, użyj [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="81131-111">If you require valid `COR_PRF_FUNCTION::reJitId` values, use the [ICorProfilerInfo4::EnumJITedFunctions2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81131-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81131-112">Requirements</span></span>  
 <span data-ttu-id="81131-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81131-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81131-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="81131-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="81131-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81131-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81131-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81131-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81131-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81131-117">See Also</span></span>  
 [<span data-ttu-id="81131-118">ICorProfilerInfo3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="81131-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="81131-119">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="81131-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="81131-120">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="81131-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)