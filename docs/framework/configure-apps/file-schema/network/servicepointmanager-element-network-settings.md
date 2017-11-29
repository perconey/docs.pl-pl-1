---
title: '&lt;Element servicePointManager&gt; elementu (ustawienia sieciowe)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 85ccad3e2c3b237e286f3737589a5e58994521bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltservicepointmanagergt-element-network-settings"></a>&lt;Element servicePointManager&gt; elementu (ustawienia sieciowe)
Służy do konfigurowania połączeń z zasobami sieciowymi.  
  
 \<Konfiguracja >  
\<System.NET >  
\<Ustawienia >  
\<Element servicePointManager >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`checkCertificateName`|Określa, czy system powinien Sprawdź, czy nazwa certyfikatu zgodna nazwa hosta serwera przed rozpoczęciem korzystania z certyfikatu. Wartość domyślna to `true`.|  
|`checkCertificateRevocationList`|Określa, czy system należy sprawdzić, czy certyfikat został odwołany przed rozpoczęciem korzystania z certyfikatu. Wartość domyślna to `false`.|  
|`dnsRefreshTimeout`|Określa, jak długo domeny Name Service (DNS) rozwiązania są buforowane w połączeniu z opcją działanie okrężne DNS w milisekundach. Wartość domyślna to 120 000 milisekund (dwie minuty).|  
|`enableDnsRoundRobin`|Określa, czy rozwiązania DNS hosta nazwy z wielu adresów Internet Protocol (IP) zwracany wszystkie adresy lub tylko pierwsza z nich. Wartość domyślna to `false`.|  
|`encryptionPolicy`|Określa zasady szyfrowania zastosować sesji SSL/TLS w <xref:System.Net.ServicePointManager> wystąpienia. Możliwe wartości to odpowiednikiem wartości <xref:System.Net.Security.EncryptionPolicy> wyliczenia. Korzystanie z <xref:System.Security.Authentication.CipherAlgorithmType.Null> jest wymagany w przypadku zasady szyfrowania jest ustawione na `NoEncryption`. Wartość domyślna to `RequireEncryption`.|  
|`expect100Continue`|Określa, czy metody POST powinien oczekiwać `100-continue` odpowiedzi z serwera. Wartość domyślna to `true`.|  
|`useNagleAlgorithm`|Określa, czy połączenia kontrolowany przez Menedżera punktu Usługi używać algorytm Nagle'a. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.ServicePointManager>  
 <xref:System.Net.Security.EncryptionPolicy>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)