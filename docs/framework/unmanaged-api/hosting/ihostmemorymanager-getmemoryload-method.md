---
title: "IHostMemoryManager::GetMemoryLoad — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager.GetMemoryLoad
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7296790eb80fe90cd115150749e533ce1800834b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="905e2-102">IHostMemoryManager::GetMemoryLoad — Metoda</span><span class="sxs-lookup"><span data-stu-id="905e2-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="905e2-103">Pobiera ilość pamięci fizycznej, która jest obecnie w użyciu i w związku z tym niedostępny jako zgłoszonego przez hosta.</span><span class="sxs-lookup"><span data-stu-id="905e2-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="905e2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="905e2-104">Syntax</span></span>  
  
```  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="905e2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="905e2-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="905e2-106">[out] Wskaźnik do przybliżonej procent całkowitej pamięci fizycznej, która jest aktualnie używany.</span><span class="sxs-lookup"><span data-stu-id="905e2-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="905e2-107">[out] Wskaźnik do liczby bajtów dostępne środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="905e2-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="905e2-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="905e2-108">Return Value</span></span>  
  
|<span data-ttu-id="905e2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="905e2-109">HRESULT</span></span>|<span data-ttu-id="905e2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="905e2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="905e2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="905e2-111">S_OK</span></span>|<span data-ttu-id="905e2-112">`GetMemoryLoad`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="905e2-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="905e2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="905e2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="905e2-114">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="905e2-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="905e2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="905e2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="905e2-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="905e2-116">The call timed out.</span></span>|  
|<span data-ttu-id="905e2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="905e2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="905e2-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="905e2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="905e2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="905e2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="905e2-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="905e2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="905e2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="905e2-121">E_FAIL</span></span>|<span data-ttu-id="905e2-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="905e2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="905e2-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="905e2-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="905e2-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="905e2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="905e2-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="905e2-125">Remarks</span></span>  
 <span data-ttu-id="905e2-126">`GetMemoryLoad`opakowuje Win32 `GlobalMemoryStatus` funkcji.</span><span class="sxs-lookup"><span data-stu-id="905e2-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="905e2-127">Wartość `pMemoryLoad` jest odpowiednikiem `dwMemoryLoad` w `MEMORYSTATUS` struktury zwrócony z `GlobalMemoryStatus`.</span><span class="sxs-lookup"><span data-stu-id="905e2-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="905e2-128">Środowisko uruchomieniowe używa wartości zwracanej jako heurystyki dla modułu zbierającego elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="905e2-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="905e2-129">Na przykład jeśli host zgłasza, że większość pamięci jest używany, moduł zbierający elementy bezużyteczne może wybrać mają być zbierane z wielu generacji, aby zwiększyć ilość pamięci, która potencjalnie może stać się dostępne.</span><span class="sxs-lookup"><span data-stu-id="905e2-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="905e2-130">Wymagania</span><span class="sxs-lookup"><span data-stu-id="905e2-130">Requirements</span></span>  
 <span data-ttu-id="905e2-131">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="905e2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="905e2-132">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="905e2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="905e2-133">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="905e2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="905e2-134">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="905e2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="905e2-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="905e2-135">See Also</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
 [<span data-ttu-id="905e2-136">IHostMemoryManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="905e2-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)