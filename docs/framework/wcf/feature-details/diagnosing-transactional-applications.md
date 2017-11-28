---
title: Diagnozowanie aplikacji transakcyjnych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 81c16e8a1b61a408abe92cd346c84d0a4fb6ff44
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="diagnosing-transactional-applications"></a><span data-ttu-id="80e99-102">Diagnozowanie aplikacji transakcyjnych</span><span class="sxs-lookup"><span data-stu-id="80e99-102">Diagnosing Transactional Applications</span></span>
<span data-ttu-id="80e99-103">W tym temacie opisano sposób użycia [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] funkcji zarządzania i diagnostyki rozwiązywać transakcyjnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="80e99-103">This topic describes how to use the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] management and diagnostics feature to troubleshoot a transactional application.</span></span>  
  
## <a name="performance-counters"></a><span data-ttu-id="80e99-104">Liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="80e99-104">Performance Counters</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="80e99-105">zawiera standardowy zestaw liczników wydajności można mierzyć wydajność aplikacji transakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="80e99-105"> provides a standard set of performance counters for you to measure your transactional application's performance.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="80e99-106">[Liczniki wydajności](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md).</span><span class="sxs-lookup"><span data-stu-id="80e99-106"> [Performance Counters](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md).</span></span>  
  
 <span data-ttu-id="80e99-107">Liczniki wydajności są ograniczone do trzech różnych poziomów: Usługa punktu końcowego, a działanie, zgodnie z opisem w poniższych tabelach.</span><span class="sxs-lookup"><span data-stu-id="80e99-107">Performance counters are scoped to three different levels: service, endpoint, and operation, as described in the following tables.</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="80e99-108">Liczniki wydajności usługi</span><span class="sxs-lookup"><span data-stu-id="80e99-108">Service Performance Counters</span></span>  
  
|<span data-ttu-id="80e99-109">Licznik wydajności</span><span class="sxs-lookup"><span data-stu-id="80e99-109">Performance counter</span></span>|<span data-ttu-id="80e99-110">Opis</span><span class="sxs-lookup"><span data-stu-id="80e99-110">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="80e99-111">Przepływ transakcji</span><span class="sxs-lookup"><span data-stu-id="80e99-111">Transactions Flowed</span></span>|<span data-ttu-id="80e99-112">Liczba transakcji przekazanych do operacji w tej usłudze.</span><span class="sxs-lookup"><span data-stu-id="80e99-112">The number of transactions that flowed to operations in this service.</span></span> <span data-ttu-id="80e99-113">Ten licznik jest zwiększany za każdym razem transakcji jest obecny w wiadomości, które są wysyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="80e99-113">This counter is incremented any time a transaction is present in the message that is sent to the service.</span></span>|  
|<span data-ttu-id="80e99-114">Przepływ transakcji na sekundę</span><span class="sxs-lookup"><span data-stu-id="80e99-114">Transactions Flowed Per Second</span></span>|<span data-ttu-id="80e99-115">Liczba transakcji przekazanych do operacji w tej usłudze w ciągu każdej sekundy.</span><span class="sxs-lookup"><span data-stu-id="80e99-115">The number of transactions that flowed to operations in this service within each second.</span></span> <span data-ttu-id="80e99-116">Ten licznik jest zwiększany za każdym razem transakcji jest obecny w wiadomości, które są wysyłane do usługi.</span><span class="sxs-lookup"><span data-stu-id="80e99-116">This counter is incremented any time a transaction is present in the message that is sent to the service.</span></span>|  
|<span data-ttu-id="80e99-117">Zatwierdzone operacje transakcyjne</span><span class="sxs-lookup"><span data-stu-id="80e99-117">Transacted Operations Committed</span></span>|<span data-ttu-id="80e99-118">Liczba operacji transakcyjnych, którego transakcja została zakończona z wynikami zatwierdzone w tej usłudze.</span><span class="sxs-lookup"><span data-stu-id="80e99-118">The number of transacted operations performed, whose transaction has completed with the outcome committed in this service.</span></span> <span data-ttu-id="80e99-119">Praca wykonana w takich operacjach jest w pełni zatwierdzana.</span><span class="sxs-lookup"><span data-stu-id="80e99-119">Work done under such operations is fully committed.</span></span> <span data-ttu-id="80e99-120">Zasoby są aktualizowane zgodnie z wynikami wykonanej operacji.</span><span class="sxs-lookup"><span data-stu-id="80e99-120">Resources are updated in accordance with the work done in the operation.</span></span>|  
|<span data-ttu-id="80e99-121">Zatwierdzone operacje transakcyjne na sekundę</span><span class="sxs-lookup"><span data-stu-id="80e99-121">Transacted Operations Committed Per Second</span></span>|<span data-ttu-id="80e99-122">Liczba operacji transakcyjnych, którego transakcja została zakończona z wynikami zatwierdzone w tej usłudze w ciągu każdej sekundy.</span><span class="sxs-lookup"><span data-stu-id="80e99-122">The number of transacted operations performed, whose transaction has completed with the outcome committed in this service within each second.</span></span> <span data-ttu-id="80e99-123">Praca wykonana w takich operacjach jest w pełni zatwierdzana.</span><span class="sxs-lookup"><span data-stu-id="80e99-123">Work done under such operations is fully committed.</span></span> <span data-ttu-id="80e99-124">Zasoby są aktualizowane zgodnie z wynikami wykonanej operacji.</span><span class="sxs-lookup"><span data-stu-id="80e99-124">Resources are updated in accordance with the work done in the operation.</span></span>|  
|<span data-ttu-id="80e99-125">Przerwane operacje transakcyjne</span><span class="sxs-lookup"><span data-stu-id="80e99-125">Transacted Operations Aborted</span></span>|<span data-ttu-id="80e99-126">Liczba operacji transakcyjnych wykonać, którego transakcja została zakończona z wynikami przerwane w tej usłudze.</span><span class="sxs-lookup"><span data-stu-id="80e99-126">The number of transacted operations performed, whose transaction has completed with the outcome aborted in this service.</span></span> <span data-ttu-id="80e99-127">Praca wykonana w takich operacjach jest wycofywana.</span><span class="sxs-lookup"><span data-stu-id="80e99-127">Work done under such operations is rolled back.</span></span> <span data-ttu-id="80e99-128">Zasoby są przywracane do poprzedniego stanu.</span><span class="sxs-lookup"><span data-stu-id="80e99-128">Resources are reverted to their previous state.</span></span>|  
|<span data-ttu-id="80e99-129">Przerwane operacje transakcyjne na sekundę</span><span class="sxs-lookup"><span data-stu-id="80e99-129">Transacted Operations Aborted Per Second</span></span>|<span data-ttu-id="80e99-130">Liczba operacji transakcyjnych wykonać, którego transakcja została zakończona z wynikami przerwane w tej usłudze w ciągu każdej sekundy.</span><span class="sxs-lookup"><span data-stu-id="80e99-130">The number of transacted operations performed, whose transaction has completed with the outcome aborted in this service within each second.</span></span> <span data-ttu-id="80e99-131">Praca wykonana w takich operacjach jest wycofywana.</span><span class="sxs-lookup"><span data-stu-id="80e99-131">Work done under such operations is rolled back.</span></span> <span data-ttu-id="80e99-132">Zasoby są przywracane do poprzedniego stanu.</span><span class="sxs-lookup"><span data-stu-id="80e99-132">Resources are reverted to their previous state.</span></span>|  
|<span data-ttu-id="80e99-133">Wątpliwe operacje transakcyjne</span><span class="sxs-lookup"><span data-stu-id="80e99-133">Transacted Operations In Doubt</span></span>|<span data-ttu-id="80e99-134">Liczba operacji transakcyjnych wykonać, którego transakcja została zakończona z wynikami, które są wątpliwe, w tej usłudze.</span><span class="sxs-lookup"><span data-stu-id="80e99-134">The number of transacted operations performed, whose transaction has completed with an outcome in doubt in this service.</span></span> <span data-ttu-id="80e99-135">Pracować z wynikami, które są wątpliwe jest w stanie nieokreślonym.</span><span class="sxs-lookup"><span data-stu-id="80e99-135">Work done with an outcome in doubt is in an indeterminate state.</span></span> <span data-ttu-id="80e99-136">Zasoby są wstrzymane w oczekiwaniu na wynik.</span><span class="sxs-lookup"><span data-stu-id="80e99-136">Resources are held pending outcome.</span></span>|  
|<span data-ttu-id="80e99-137">Wątpliwe operacje transakcyjne na sekundę</span><span class="sxs-lookup"><span data-stu-id="80e99-137">Transacted Operations In Doubt Per Second</span></span>|<span data-ttu-id="80e99-138">Liczba operacji transakcyjnych wykonać, którego transakcja została zakończona z wynikami, które są wątpliwe, w tej usłudze w ciągu każdej sekundy.</span><span class="sxs-lookup"><span data-stu-id="80e99-138">The number of transacted operations performed, whose transaction has completed with an outcome in doubt in this service within each second.</span></span> <span data-ttu-id="80e99-139">Pracować z wynikami, które są wątpliwe jest w stanie nieokreślonym.</span><span class="sxs-lookup"><span data-stu-id="80e99-139">Work done with an outcome in doubt is in an indeterminate state.</span></span> <span data-ttu-id="80e99-140">Zasoby są wstrzymane w oczekiwaniu na wynik.</span><span class="sxs-lookup"><span data-stu-id="80e99-140">Resources are held pending outcome.</span></span>|  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="80e99-141">Liczniki wydajności w punkcie końcowym</span><span class="sxs-lookup"><span data-stu-id="80e99-141">Endpoint Performance Counters</span></span>  
  
|<span data-ttu-id="80e99-142">Licznik wydajności</span><span class="sxs-lookup"><span data-stu-id="80e99-142">Performance counter</span></span>|<span data-ttu-id="80e99-143">Opis</span><span class="sxs-lookup"><span data-stu-id="80e99-143">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="80e99-144">Przepływ transakcji</span><span class="sxs-lookup"><span data-stu-id="80e99-144">Transactions Flowed</span></span>|<span data-ttu-id="80e99-145">Liczba transakcji przekazanych do operacji w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="80e99-145">The number of transactions that flowed to operations at this endpoint.</span></span> <span data-ttu-id="80e99-146">Ten licznik jest zwiększany za każdym razem transakcji jest obecny w wiadomości, które są wysyłane do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="80e99-146">This counter is incremented any time a transaction is present in the message that is sent to the endpoint.</span></span>|  
|<span data-ttu-id="80e99-147">Przepływ transakcji na sekundę</span><span class="sxs-lookup"><span data-stu-id="80e99-147">Transactions Flowed Per Second</span></span>|<span data-ttu-id="80e99-148">Liczba transakcji przekazanych do operacji w tym punkcie końcowym w ciągu każdej sekundy.</span><span class="sxs-lookup"><span data-stu-id="80e99-148">The number of transactions that flowed to operations at this endpoint within each second.</span></span> <span data-ttu-id="80e99-149">Ten licznik jest zwiększany za każdym razem transakcji jest obecny w wiadomości, które są wysyłane do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="80e99-149">This counter is incremented any time a transaction is present in the message that is sent to the endpoint.</span></span>|  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="80e99-150">Liczniki wydajności operacji</span><span class="sxs-lookup"><span data-stu-id="80e99-150">Operation Performance Counters</span></span>  
  
|<span data-ttu-id="80e99-151">Licznik wydajności</span><span class="sxs-lookup"><span data-stu-id="80e99-151">Performance counter</span></span>|<span data-ttu-id="80e99-152">Opis</span><span class="sxs-lookup"><span data-stu-id="80e99-152">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="80e99-153">Przepływ transakcji</span><span class="sxs-lookup"><span data-stu-id="80e99-153">Transactions Flowed</span></span>|<span data-ttu-id="80e99-154">Liczba transakcji przekazanych do operacji w tym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="80e99-154">The number of transactions that flowed to operations at this endpoint.</span></span> <span data-ttu-id="80e99-155">Ten licznik jest zwiększany za każdym razem transakcji jest obecny w wiadomości, które są wysyłane do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="80e99-155">This counter is incremented any time a transaction is present in the message that is sent to the endpoint.</span></span>|  
|<span data-ttu-id="80e99-156">Przepływ transakcji na sekundę</span><span class="sxs-lookup"><span data-stu-id="80e99-156">Transactions Flowed Per Second</span></span>|<span data-ttu-id="80e99-157">Liczba transakcji przekazanych do operacji w tym punkcie końcowym w ciągu każdej sekundy.</span><span class="sxs-lookup"><span data-stu-id="80e99-157">The number of transactions that flowed to operations at this endpoint within each second.</span></span> <span data-ttu-id="80e99-158">Ten licznik jest zwiększany za każdym razem transakcji jest obecny w wiadomości, które są wysyłane do punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="80e99-158">This counter is incremented any time a transaction is present in the message that is sent to the endpoint.</span></span>|  
  
## <a name="windows-management-instrumentation"></a><span data-ttu-id="80e99-159">Instrumentacja zarządzania Windows</span><span class="sxs-lookup"><span data-stu-id="80e99-159">Windows Management Instrumentation</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="80e99-160">udostępnia dane inspekcji usługi w czasie wykonywania za pośrednictwem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dostawcy Instrumentacji zarządzania Windows (WMI).</span><span class="sxs-lookup"><span data-stu-id="80e99-160"> exposes inspection data of a service at run time through a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Windows Management Instrumentation (WMI) provider.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="80e99-161">dostęp do danych usługi WMI, zobacz [przy użyciu Instrumentacji zarządzania Windows dla diagnostyki](../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span><span class="sxs-lookup"><span data-stu-id="80e99-161"> accessing WMI data, see [Using Windows Management Instrumentation for Diagnostics](../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
 <span data-ttu-id="80e99-162">Wiele-do-odczytu właściwości WMI wskazują ustawienia zastosowane transakcji dla usługi.</span><span class="sxs-lookup"><span data-stu-id="80e99-162">A number of read-only WMI properties indicate the applied transaction settings for a service.</span></span> <span data-ttu-id="80e99-163">W poniższych tabelach przedstawiono wszystkie te ustawienia.</span><span class="sxs-lookup"><span data-stu-id="80e99-163">The following tables list all of these settings.</span></span>  
  
 <span data-ttu-id="80e99-164">W usłudze `ServiceBehaviorAttribute` ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="80e99-164">On a service, the `ServiceBehaviorAttribute` has the following properties.</span></span>  
  
|<span data-ttu-id="80e99-165">Nazwa</span><span class="sxs-lookup"><span data-stu-id="80e99-165">Name</span></span>|<span data-ttu-id="80e99-166">Typ</span><span class="sxs-lookup"><span data-stu-id="80e99-166">Type</span></span>|<span data-ttu-id="80e99-167">Opis</span><span class="sxs-lookup"><span data-stu-id="80e99-167">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="80e99-168">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="80e99-168">ReleaseServiceInstanceOnTransactionComplete</span></span>|<span data-ttu-id="80e99-169">Boolean</span><span class="sxs-lookup"><span data-stu-id="80e99-169">Boolean</span></span>|<span data-ttu-id="80e99-170">Określa, czy obiekt usługi jest ponownie przetwarzany po zakończeniu bieżącej transakcji.</span><span class="sxs-lookup"><span data-stu-id="80e99-170">Specifies whether the service object is recycled when the current transaction completes.</span></span>|  
|<span data-ttu-id="80e99-171">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="80e99-171">TransactionAutoCompleteOnSessionClose</span></span>|<span data-ttu-id="80e99-172">Boolean</span><span class="sxs-lookup"><span data-stu-id="80e99-172">Boolean</span></span>|<span data-ttu-id="80e99-173">Określa, czy transakcje oczekujące są kończone podczas zamykania bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="80e99-173">Specifies whether pending transactions are completed when the current session closes.</span></span>|  
|<span data-ttu-id="80e99-174">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="80e99-174">TransactionIsolationLevel</span></span>|<span data-ttu-id="80e99-175">Ciąg, który znajduje się nieprawidłowa wartość <xref:System.Transactions.IsolationLevel> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="80e99-175">A string that contains a valid value of the <xref:System.Transactions.IsolationLevel> enumeration.</span></span>|<span data-ttu-id="80e99-176">Określa poziom izolacji transakcji, która obsługuje tę usługę.</span><span class="sxs-lookup"><span data-stu-id="80e99-176">Specifies the transaction isolation level that this service supports.</span></span>|  
|<span data-ttu-id="80e99-177">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="80e99-177">TransactionTimeout</span></span>|<xref:System.DateTime>|<span data-ttu-id="80e99-178">Określa okres, w ramach którego transakcja musi zostać zakończona.</span><span class="sxs-lookup"><span data-stu-id="80e99-178">Specifies the period within which a transaction must complete.</span></span>|  
  
 <span data-ttu-id="80e99-179">`ServiceTimeoutsBehavior` Ma następującą właściwość.</span><span class="sxs-lookup"><span data-stu-id="80e99-179">The `ServiceTimeoutsBehavior` has the following property.</span></span>  
  
|<span data-ttu-id="80e99-180">Nazwa</span><span class="sxs-lookup"><span data-stu-id="80e99-180">Name</span></span>|<span data-ttu-id="80e99-181">Typ</span><span class="sxs-lookup"><span data-stu-id="80e99-181">Type</span></span>|<span data-ttu-id="80e99-182">Opis</span><span class="sxs-lookup"><span data-stu-id="80e99-182">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="80e99-183">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="80e99-183">TransactionTimeout</span></span>|<xref:System.DateTime>|<span data-ttu-id="80e99-184">Określa okres, w ramach którego transakcja musi zostać zakończona.</span><span class="sxs-lookup"><span data-stu-id="80e99-184">Specifies the period within which a transaction must complete.</span></span>|  
  
 <span data-ttu-id="80e99-185">W powiązaniu `TransactionFlowBindingElement` ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="80e99-185">On a binding, the `TransactionFlowBindingElement` has the following properties.</span></span>  
  
|<span data-ttu-id="80e99-186">Nazwa</span><span class="sxs-lookup"><span data-stu-id="80e99-186">Name</span></span>|<span data-ttu-id="80e99-187">Typ</span><span class="sxs-lookup"><span data-stu-id="80e99-187">Type</span></span>|<span data-ttu-id="80e99-188">Opis</span><span class="sxs-lookup"><span data-stu-id="80e99-188">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="80e99-189">Element TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="80e99-189">TransactionProtocol</span></span>|<span data-ttu-id="80e99-190">Ciąg, który znajduje się nieprawidłowa wartość <xref:System.ServiceModel.TransactionProtocol> typu.</span><span class="sxs-lookup"><span data-stu-id="80e99-190">A string that contains a valid value of the <xref:System.ServiceModel.TransactionProtocol> type.</span></span>|<span data-ttu-id="80e99-191">Określa protokół transakcji używany do transmisji.</span><span class="sxs-lookup"><span data-stu-id="80e99-191">Specifies the transaction protocol to use in flowing a transaction.</span></span>|  
|<span data-ttu-id="80e99-192">TransactionFlow</span><span class="sxs-lookup"><span data-stu-id="80e99-192">TransactionFlow</span></span>|<span data-ttu-id="80e99-193">Boolean</span><span class="sxs-lookup"><span data-stu-id="80e99-193">Boolean</span></span>|<span data-ttu-id="80e99-194">Określa, czy ruch przychodzący transakcji jest włączony.</span><span class="sxs-lookup"><span data-stu-id="80e99-194">Specifies whether incoming transaction flow is enabled.</span></span>|  
  
 <span data-ttu-id="80e99-195">W przypadku operacji `OperationBehaviorAttribute` ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="80e99-195">On an operation, the `OperationBehaviorAttribute` has the following properties:</span></span>  
  
|<span data-ttu-id="80e99-196">Nazwa</span><span class="sxs-lookup"><span data-stu-id="80e99-196">Name</span></span>|<span data-ttu-id="80e99-197">Typ</span><span class="sxs-lookup"><span data-stu-id="80e99-197">Type</span></span>|<span data-ttu-id="80e99-198">Opis</span><span class="sxs-lookup"><span data-stu-id="80e99-198">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="80e99-199">Wartość TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="80e99-199">TransactionAutoComplete</span></span>|<span data-ttu-id="80e99-200">Boolean</span><span class="sxs-lookup"><span data-stu-id="80e99-200">Boolean</span></span>|<span data-ttu-id="80e99-201">Określa, czy ma być automatycznie przekazywana bieżącej transakcji, jeśli wystąpi żaden nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="80e99-201">Specifies whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>|  
|<span data-ttu-id="80e99-202">Właściwości TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="80e99-202">TransactionScopeRequired</span></span>|<span data-ttu-id="80e99-203">Boolean</span><span class="sxs-lookup"><span data-stu-id="80e99-203">Boolean</span></span>|<span data-ttu-id="80e99-204">Określa, czy operacja wymaga transakcji.</span><span class="sxs-lookup"><span data-stu-id="80e99-204">Specifies whether the operation requires a transaction.</span></span>|  
  
 <span data-ttu-id="80e99-205">W przypadku operacji `TransactionFlowAttribute` ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="80e99-205">On an operation, the `TransactionFlowAttribute` has the following properties.</span></span>  
  
|<span data-ttu-id="80e99-206">Nazwa</span><span class="sxs-lookup"><span data-stu-id="80e99-206">Name</span></span>|<span data-ttu-id="80e99-207">Typ</span><span class="sxs-lookup"><span data-stu-id="80e99-207">Type</span></span>|<span data-ttu-id="80e99-208">Opis</span><span class="sxs-lookup"><span data-stu-id="80e99-208">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="80e99-209">Właściwość TransactionFlowOption</span><span class="sxs-lookup"><span data-stu-id="80e99-209">TransactionFlowOption</span></span>|<span data-ttu-id="80e99-210">Ciąg, który znajduje się nieprawidłowa wartość <xref:System.ServiceModel.TransactionFlowOption> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="80e99-210">A string that contains a valid value of the <xref:System.ServiceModel.TransactionFlowOption> enumeration.</span></span>|<span data-ttu-id="80e99-211">Określa zakres przepływu transakcji, które jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="80e99-211">Specifies the extent to which transaction flow is required.</span></span>|  
  
## <a name="tracing"></a><span data-ttu-id="80e99-212">Śledzenie</span><span class="sxs-lookup"><span data-stu-id="80e99-212">Tracing</span></span>  
 <span data-ttu-id="80e99-213">Ślady umożliwiają monitorowanie i analizowanie błędów w transakcyjnych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="80e99-213">Traces enable you to monitor and analyze faults in your transactional applications.</span></span> <span data-ttu-id="80e99-214">Można włączyć śledzenie przy użyciu następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="80e99-214">You can enable tracing using the following ways:</span></span>  
  
-   <span data-ttu-id="80e99-215">Standardowe [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] śledzenia</span><span class="sxs-lookup"><span data-stu-id="80e99-215">Standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tracing</span></span>  
  
     <span data-ttu-id="80e99-216">Ten rodzaj śledzenia jest taka sama jak śledzenie żadnego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="80e99-216">This type of tracing is the same as tracing any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="80e99-217">[Konfigurowanie śledzenia](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="80e99-217"> [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md).</span></span>  
  
-   <span data-ttu-id="80e99-218">Śledzenie protokołu WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="80e99-218">WS-AtomicTransaction tracing</span></span>  
  
     <span data-ttu-id="80e99-219">WS-AtomicTransaction śledzenie można włączyć za pomocą [narzędzia konfiguracji WS-AtomicTransaction (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).</span><span class="sxs-lookup"><span data-stu-id="80e99-219">WS-AtomicTransaction tracing can be enabled by using the [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md).</span></span> <span data-ttu-id="80e99-220">Takie śledzenie zapewnia wgląd w stan transakcji i uczestników w systemie.</span><span class="sxs-lookup"><span data-stu-id="80e99-220">Such tracing provides insight into the state of transactions and participants within a system.</span></span> <span data-ttu-id="80e99-221">Należy również włączyć wewnętrznego śledzenia modelu usługi, można ustawić `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` klucza rejestru na prawidłową wartość <xref:System.Diagnostics.SourceLevels> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="80e99-221">To also enable internal Service Model tracing, you can set the `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` registry key to a valid value of the <xref:System.Diagnostics.SourceLevels> enumeration.</span></span> <span data-ttu-id="80e99-222">Możesz włączyć rejestrowanie w taki sam sposób jak inne komunikatów [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="80e99-222">You can enable message logging in the same way as other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications.</span></span>  
  
-   <span data-ttu-id="80e99-223">`System.Transactions`Śledzenie</span><span class="sxs-lookup"><span data-stu-id="80e99-223">`System.Transactions` tracing</span></span>  
  
     <span data-ttu-id="80e99-224">Podczas korzystania z protokołu OleTransactions, nie może być śledzony wiadomości protokołu.</span><span class="sxs-lookup"><span data-stu-id="80e99-224">When using the OleTransactions protocol, protocol messages cannot be traced.</span></span> <span data-ttu-id="80e99-225">Obsługa śledzenia <xref:System.Transactions> zapewnia infrastrukturę (który używa OleTransactions) umożliwia użytkownikom wyświetlanie zdarzenia do transakcji.</span><span class="sxs-lookup"><span data-stu-id="80e99-225">The tracing support the <xref:System.Transactions> infrastructure provides (which uses OleTransactions) allows users to view events that occurred to the transactions.</span></span> <span data-ttu-id="80e99-226">Aby włączyć śledzenie dla <xref:System.Transactions> aplikacji, zawierać następujący kod w `App.config` pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="80e99-226">To enable tracing for a <xref:System.Transactions> application, include the following code in the `App.config` configuration file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
         <sources>  
            <source name="System.Transactions" switchValue="Verbose, ActivityTracing">  
               <listeners>  
                  <add name="Text"  
                     type="System.Diagnostics.XmlWriterTraceListener"  
                     initializeData="SysTx.log"  
                     traceOutputOptions="Callstack" />  
               </listeners>  
            </source>  
         </sources>  
         <trace autoflush="true" indentsize="4">  
         </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     <span data-ttu-id="80e99-227">Dzięki temu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] śledzenia, jako [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] korzysta również <xref:System.Transactions> infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="80e99-227">This also enables [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tracing, as [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] also utilizes the <xref:System.Transactions> infrastructure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80e99-228">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80e99-228">See Also</span></span>  
 [<span data-ttu-id="80e99-229">Administracja i Diagnostyka</span><span class="sxs-lookup"><span data-stu-id="80e99-229">Administration and Diagnostics</span></span>](../../../../docs/framework/wcf/diagnostics/index.md)  
 [<span data-ttu-id="80e99-230">Konfigurowanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="80e99-230">Configuring Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="80e99-231">Narzędzie konfiguracji WS-AtomicTransaction (wsatConfig.exe)</span><span class="sxs-lookup"><span data-stu-id="80e99-231">WS-AtomicTransaction Configuration Utility (wsatConfig.exe)</span></span>](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)