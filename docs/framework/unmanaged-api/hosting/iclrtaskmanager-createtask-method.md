---
title: "ICLRTaskManager::CreateTask — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.CreateTask
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::CreateTask
helpviewer_keywords:
- ICLRTaskManager::CreateTask method [.NET Framework hosting]
- CreateTask method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: eea570d9-2e53-4320-9ea0-eb777bf9dcf3
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fa4607232eedd532456d1ffae6bc3d92e42282f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrtaskmanagercreatetask-method"></a><span data-ttu-id="1d825-102">ICLRTaskManager::CreateTask — Metoda</span><span class="sxs-lookup"><span data-stu-id="1d825-102">ICLRTaskManager::CreateTask Method</span></span>
<span data-ttu-id="1d825-103">Żąda jawnie, czy środowisko uruchomieniowe języka wspólnego (CLR) umożliwia utworzenie nowego zadania.</span><span class="sxs-lookup"><span data-stu-id="1d825-103">Requests explicitly that the common language runtime (CLR) create a new task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d825-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d825-104">Syntax</span></span>  
  
```  
HRESULT CreateTask (  
    [out] ICLRTask **pTask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d825-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1d825-105">Parameters</span></span>  
 `pTask`  
 <span data-ttu-id="1d825-106">[out] Wskaźnik do nowo utworzonego adresu [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), lub wartość null, jeśli nie można utworzyć zadania.</span><span class="sxs-lookup"><span data-stu-id="1d825-106">[out] A pointer to the address of a newly created [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md), or null, if the task could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1d825-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1d825-107">Return Value</span></span>  
  
|<span data-ttu-id="1d825-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1d825-108">HRESULT</span></span>|<span data-ttu-id="1d825-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1d825-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1d825-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1d825-110">S_OK</span></span>|<span data-ttu-id="1d825-111">Metoda zwróciła pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1d825-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="1d825-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1d825-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1d825-113">Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1d825-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1d825-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1d825-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1d825-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1d825-115">The call timed out.</span></span>|  
|<span data-ttu-id="1d825-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1d825-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1d825-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1d825-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1d825-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1d825-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1d825-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1d825-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1d825-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1d825-120">E_FAIL</span></span>|<span data-ttu-id="1d825-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1d825-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1d825-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1d825-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1d825-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1d825-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1d825-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1d825-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1d825-125">Za mało pamięci jest dostępna do przydzielenia do żądanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="1d825-125">Not enough memory is available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d825-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d825-126">Remarks</span></span>  
 <span data-ttu-id="1d825-127">Środowisko CLR jest utworzenie nowego zadania automatycznie po zainicjowaniu, podczas tworzenia wątku przez kod użytkownika przy użyciu typów w <xref:System.Threading> przestrzeni nazw, lub po zwiększeniu rozmiaru puli wątków.</span><span class="sxs-lookup"><span data-stu-id="1d825-127">The CLR creates a new task automatically upon initialization, when user code creates a thread by using types in the <xref:System.Threading> namespace, or when the size of the thread pool is increased.</span></span> <span data-ttu-id="1d825-128">Tworzy również zadania, gdy niezarządzany kod wywołuje funkcją zarządzaną.</span><span class="sxs-lookup"><span data-stu-id="1d825-128">It also creates tasks when unmanaged code makes a call to a managed function.</span></span>  
  
 <span data-ttu-id="1d825-129">`CreateTask`umożliwia hostowi jawnie zażądać, CLR utworzyć nowe zadanie.</span><span class="sxs-lookup"><span data-stu-id="1d825-129">`CreateTask` allows the host to make an explicit request that the CLR create a new task.</span></span> <span data-ttu-id="1d825-130">Na przykład host może wywołać tę metodę, aby wstępnie zainicjować struktury danych.</span><span class="sxs-lookup"><span data-stu-id="1d825-130">For example, the host can invoke this method to preinitialize data structures.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1d825-131">Nowe zadanie jest zwracany w stan zawieszenia i pozostanie wstrzymany, aż do hosta jawnie wywołuje [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span><span class="sxs-lookup"><span data-stu-id="1d825-131">The new task is returned in a suspended state and remains suspended until the host explicitly calls [IHostTask::Start](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d825-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1d825-132">Requirements</span></span>  
 <span data-ttu-id="1d825-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d825-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d825-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1d825-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1d825-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1d825-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d825-136">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d825-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d825-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d825-137">See Also</span></span>  
 [<span data-ttu-id="1d825-138">ICLRTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="1d825-138">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="1d825-139">ICLRTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="1d825-139">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="1d825-140">IHostTask — interfejs</span><span class="sxs-lookup"><span data-stu-id="1d825-140">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="1d825-141">IHostTaskManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="1d825-141">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)