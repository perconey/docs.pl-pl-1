---
title: "IHostTask::GetPriority — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask.GetPriority
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ba32e8c442042f59c8346d68cef7d9f6678ae7dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="7fc7c-102">IHostTask::GetPriority — Metoda</span><span class="sxs-lookup"><span data-stu-id="7fc7c-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="7fc7c-103">Pobiera poziom priorytetu wątku zadania reprezentowany przez bieżący [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fc7c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7fc7c-104">Syntax</span></span>  
  
```  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7fc7c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7fc7c-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="7fc7c-106">[out] Wskaźnik do liczba całkowita, która wskazuje poziom priorytetu wątku zadania reprezentowany przez bieżący `IHostTask` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fc7c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="7fc7c-107">Return Value</span></span>  
  
|<span data-ttu-id="7fc7c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7fc7c-108">HRESULT</span></span>|<span data-ttu-id="7fc7c-109">Opis</span><span class="sxs-lookup"><span data-stu-id="7fc7c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7fc7c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7fc7c-110">S_OK</span></span>|<span data-ttu-id="7fc7c-111">`GetPriority`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-111">`GetPriority` returned successfully.</span></span>|  
|<span data-ttu-id="7fc7c-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7fc7c-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7fc7c-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7fc7c-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7fc7c-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7fc7c-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-115">The call timed out.</span></span>|  
|<span data-ttu-id="7fc7c-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7fc7c-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7fc7c-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7fc7c-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7fc7c-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7fc7c-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7fc7c-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7fc7c-120">E_FAIL</span></span>|<span data-ttu-id="7fc7c-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7fc7c-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7fc7c-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fc7c-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7fc7c-124">Remarks</span></span>  
 <span data-ttu-id="7fc7c-125">Wartości poziom priorytetu wątku są definiowane przez Win32 `SetThreadPriority` funkcji.</span><span class="sxs-lookup"><span data-stu-id="7fc7c-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fc7c-126">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7fc7c-126">Requirements</span></span>  
 <span data-ttu-id="7fc7c-127">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fc7c-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fc7c-128">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7fc7c-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fc7c-129">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7fc7c-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fc7c-130">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fc7c-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fc7c-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7fc7c-131">See Also</span></span>  
 [<span data-ttu-id="7fc7c-132">ICLRTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="7fc7c-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="7fc7c-133">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="7fc7c-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="7fc7c-134">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="7fc7c-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="7fc7c-135">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="7fc7c-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)