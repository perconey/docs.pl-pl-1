---
title: "Porady: modyfikowanie pliku konfiguracji komputera, aby włączyć obsługę protokołu IPv6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5611b677-b9cc-43b8-a434-60e18d89aada
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 696aeb619f14a5ebe9a760cbd78a0d0fa876edc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-modify-the-computer-configuration-file-to-enable-ipv6-support"></a>Porady: modyfikowanie pliku konfiguracji komputera, aby włączyć obsługę protokołu IPv6
Poniższy przykład kodu pokazuje sposób modyfikowania pliku konfiguracji komputera, *machine.config*, aby włączyć obsługę protokołu IPv6. *Machine.config* plik jest przechowywany w *%Windir%\Microsoft.NET\Framework* folder w katalogu, w którym zainstalowano system Windows. Brak oddzielnej *machine.config* plików w folderach w obszarze *%Windir%\Microsoft.NET\Framework* dla każdej wersji platformy .NET zainstalowany na komputerze (na przykład *C:\ WINDOWS\Microsoft.NET\Framework\v2.0.50727\machine.config*).  
  
 Ustawienia te można również wprowadzić w pliku konfiguracyjnym aplikacji. Ma on priorytet nad plikiem konfiguracyjnym komputera.  
  
 Dla programu .NET Framework w wersji 1.1 i starszych wersjach wartość **ipv6 włączone** przełącznik konfiguracji określa czy członkami <xref:System.Net.Dns?displayProperty=nameWithType> klasy Zwróć adresy IPv6.  
  
 Dla programu .NET Framework w wersji 2.0 lub nowszej, jeśli system Windows obsługuje protokół IPv6, a następnie wszystkie elementy członkowskie <xref:System.Net.Dns?displayProperty=nameWithType> klasy (na przykład <xref:System.Net.Dns.GetHostEntry%2A?displayProperty=nameWithType> — metoda), którą będzie zwracać adresów IPv6 z jednym z ograniczeń. Przestarzali członkowie <xref:System.Net.Dns?displayProperty=nameWithType> klasy (na przykład <xref:System.Net.Dns.Resolve%2A?displayProperty=nameWithType> metody) odczytuje i rozpoznać wartości w pliku konfiguracji.  
  
> [!NOTE]
>  Dla programu .NET Framework w wersji 2.0 lub nowszej domyślnie jest włączony protokół IPv6. Dla programu .NET Framework w wersji 1.1 i starsze wersje protokołu IPv6 jest domyślnie wyłączona.  
  
## <a name="example"></a>Przykład  
  
```xml  
<system.net>  
    …………  
    <settings>  
        …………  
        <ipv6 enabled="true"/>   
    ……………  
    </settings>  
    ………………  
<system.net>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Adresowanie IPv6](../../../docs/framework/network-programming/ipv6-addressing.md)  
 [Schemat ustawień sieci](../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [\<IPv6 > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)