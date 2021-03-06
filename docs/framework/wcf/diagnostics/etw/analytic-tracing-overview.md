---
title: "Omówienie śledzenia analitycznego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- analytic tracing [WCF], overview
ms.assetid: ae55e9cc-0809-442f-921f-d644290ebf15
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3492821d56f7089c2aa53bba566690ded02f8a5b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="analytic-tracing-overview"></a>Omówienie śledzenia analitycznego
Śledzenie analityczne w [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] jest wysoka wydajność i niski poziom szczegółowości śledzenia skonfigurowaną na górze zdarzenia śledzenia dla systemu Windows (ETW). ETW. działa na poziomie jądra można znacznie zmniejszyć koszty operacji śledzenia. Go efektywnego buforuje zdarzenia trybu jądra i użytkownika i umożliwia dynamiczne Włączanie rejestrowania bez konieczności ponownego uruchomienia usługi. Dane śledzenia są dostępne w dziennikach zdarzeń po nim ma zostały wyemitowane i odebranych.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]ETW, zobacz [poprawy debugowania i dostrajania wydajności za pomocą funkcji ETW](http://go.microsoft.com/fwlink/?LinkId=164781).  
  
 Oprócz przy użyciu dzienników zdarzeń systemu Windows, zabezpieczeń i aplikacji do analizowania aplikacji, [!INCLUDE[wv](../../../../../includes/wv-md.md)] i [!INCLUDE[lserver](../../../../../includes/lserver-md.md)] wprowadzono dodatkowe dzienniki w węźle Dzienniki aplikacji i usług najwyższego poziomu. Te nowe dzienniki ma na celu przechowywania zdarzeń dla określonej aplikacji lub określonego składnika zamiast zdarzenia globalne, które mają wpływ systemowe (takie jak typ zdarzenia, które mogą rejestrować w dzienniku zdarzeń zabezpieczeń). [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)]łączy i uzależnia rejestrowanie [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zdarzeń śledzenia [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] dzienników wiadomości i [!INCLUDE[wf1](../../../../../includes/wf1-md.md)] śledzenie rekordów Dzienniki aplikacji i usług.  
  
## <a name="concepts-and-capabilities"></a>Pojęcia i możliwości  
 Następujące pojęcia i możliwości dotyczą [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] śledzenie danych analitycznych.  
  
### <a name="enabling-wcf-diagnostics-settings"></a>Włączanie ustawień diagnostycznych WCF  
 Diagnostyka WCF są włączane w \<system.serviceModel >\<diagnostyki > sekcji konfiguracji.  
  
```xml  
<system.serviceModel>  
  <diagnostics>  
```  
  
 Ustawienia diagnostyki WCF hostowanych w sieci Web usług IIS aplikacji wirtualnej są włączone w jego "pliku Web.config. Innym rozwiązaniem jest, aby utworzyć plik Web.config w podkatalogu w aplikacji.  Ten wybór stosuje ustawienia do wszystkich usług w podkatalogu.  Upewnij się, że ustawienia diagnostyczne są inicjowane spójnie dla wszystkich usług w aplikacji, ustawienia należy w pliku Web.config w katalogu aplikacji, a nie w poszczególnych podkatalogów w tej aplikacji.  
  
### <a name="channels"></a>Kanały  
 ETW umożliwia składniki oprogramowania do zdarzenia śledzenia bezpośrednio do określonej grupy odbiorców przy użyciu kanałów. Na przykład możesz wysłać zdarzenia, aby administratorzy systemu mogli jeden kanał i że opieki deweloperzy aplikacji o do innego kanału. Kanały są nazwane i zarejestrowane w systemie Windows, dzięki czemu odbiorcy mogą wyświetlać zdarzenia kanału, za pomocą Podglądu zdarzeń.  
  
 Funkcja śledzenie analityczne dla [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] w [!INCLUDE[netfx_current_short](../../../../../includes/netfx-current-short-md.md)] zapisuje do kanału aplikacji firmy Microsoft-Windows-aplikacji-serwera —. Ten kanał został zaprojektowany specjalnie dla użytkowników, którzy chcą monitorować kondycję [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usług w środowisku produkcyjnym. Definiuje niewielki zestaw zdarzeń, które mogą być używane w wielu monitorowanie kondycji i rozwiązywaniu problemów.  
  
 Aby włączyć manifestu śledzenia zdarzeń dla systemu Windows tak, aby komunikaty są prawidłowo zdekodować w dzienniku zdarzeń, należy użyć narzędzia ServiceModelReg w wierszu polecenia w następujący sposób:  
  
 `ServiceModelReg.exe -i -c:etw`  
  
### <a name="dynamic-configuration"></a>Konfiguracji dynamicznej  
 Infrastruktura ETW umożliwia śledzenie, aby być włączona i skonfigurowana dynamicznie przy użyciu standardowych narzędzi systemu Windows. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Dynamiczne Włączanie śledzenia danych analitycznych](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).  
  
### <a name="message-flow-tracing"></a>Śledzenia przepływu komunikatów  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]jak włączyć śledzenie przepływu wiadomości, zobacz [Konfigurowanie śledzenia przepływu komunikatów](../../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md).  
  
### <a name="keywords"></a>Słowa kluczowe  
 Słowa kluczowe są używane do filtrowania komunikatów śledzenia i zdefiniuj którym składnikiem [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] wysyłanego zdarzenia. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Dynamiczne Włączanie śledzenia danych analitycznych](../../../../../docs/framework/wcf/diagnostics/etw/dynamically-enabling-analytic-tracing.md).
