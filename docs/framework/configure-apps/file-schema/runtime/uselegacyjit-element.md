---
title: "&lt;useLegacyJit&gt; — Element"
ms.custom: 
ms.date: 04/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 735733fc33a21c2f275c1ea9894c43558f01626e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltuselegacyjitgt-element"></a>&lt;useLegacyJit&gt; — Element

Określa, czy środowisko uruchomieniowe języka wspólnego używa starszej wersji kompilatora JIT 64-bitowej w czasie kompilacji.  
  
\<Konfiguracja >  
\<Runtime >  
\<useLegacyJit >
  
## <a name="syntax"></a>Składnia  
  
```xml
<useLegacyJit enabled=0|1 />
```

Nazwa elementu `useLegacyJit` jest rozróżniana wielkość liter.
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
| Atrybut | Opis                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | Atrybut wymagany.<br><br>Określa, czy środowisko uruchomieniowe używa starszej wersji kompilatora JIT 64-bitowych. |  
  
### <a name="enabled-attribute"></a>Atrybut enabled  
  
| Wartość | Opis                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | Środowisko uruchomieniowe języka wspólnego używa nowego 64-bitowym przy użyciu kompilatora JIT uwzględnione w programie .NET Framework 4.6 i nowszymi wersjami. |  
| 1     | Środowisko uruchomieniowe języka wspólnego używa starszego kompilatora JIT 64-bitowych.                                                     |  
  
### <a name="child-elements"></a>Elementy podrzędne

Brak
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
| Element         | Opis                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |  
| `runtime`       | Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.                                                        |  
  
## <a name="remarks"></a>Uwagi  

Począwszy od programu .NET Framework 4.6, środowisko uruchomieniowe języka wspólnego nowy kompilator 64-bitowy dla kompilacji just in Time (JIT) domyślnie używa. W niektórych przypadkach może to spowodować różnice w zachowaniu z kodu aplikacji, który został skompilowany JIT w poprzedniej wersji kompilatora JIT 64-bitowych. Przez ustawienie `enabled` atrybutu `<useLegacyJit>` elementu `1`, można wyłączyć kompilator JIT 64-bitowe i zamiast tego Kompilowanie aplikacji za pomocą starszego kompilatora JIT 64-bitowych.  
  
> [!NOTE]
> `<useLegacyJit>` Elementu dotyczy tylko kompilacji JIT 64-bitowych. Kompilacja z kompilatorem JIT 32-bitowych nie mają wpływu.  
  
Zamiast pliku ustawień konfiguracji, można włączyć starszej wersji 64-bitowej przy użyciu kompilatora JIT dwa inne sposoby:  
  
- Ustawienie zmiennej środowiskowej

  Ustaw `COMPLUS_useLegacyJit` albo zmienną środowiskową `0` (Użyj kompilator JIT 64-bitowe) lub `1` (należy użyć starszego kompilatora JIT 64-bitowe):
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  Zmienna środowiskowa ma *globalne*, co oznacza, że ma to wpływ na wszystkie aplikacje uruchamiane na tym komputerze. Jeśli ustawiona, jej mogą zostać zastąpione przez ustawienie pliku konfiguracji aplikacji. Nazwa zmiennej środowiskowej nie jest rozróżniana wielkość liter.
  
- Dodawanie klucza rejestru

  Można włączyć starszego kompilatora JIT 64-bitowych, dodając `REG_DWORD` wartość jednej `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` lub `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza w rejestrze. Wartość jest o nazwie `useLegacyJit`. Jeśli wartość wynosi 0, jest używany nowy kompilator. Jeśli wartość wynosi 1, starszego kompilatora JIT 64-bitowych jest włączone. Nazwa wartości rejestru nie jest rozróżniana wielkość liter.
  
  Dodaj wartość do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucz ma wpływ na wszystkie aplikacje uruchomione na maszynie. Dodaj wartość do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucz ma wpływ na wszystkie aplikacje uruchamiane przez bieżącego użytkownika. Jeśli maszyna jest skonfigurowana z wieloma kontami użytkowników, tylko aplikacje uruchamiane przez bieżącego użytkownika jest narażony, chyba że wartość jest dodawana do kluczy rejestru, jak również innych użytkowników. Dodawanie `<useLegacyJit>` elementu do pliku konfiguracji zastępuje ustawienia rejestru, jeśli są one obecne.  
  
## <a name="example"></a>Przykład  

Następującego pliku konfiguracji powoduje wyłączenie kompilacji przez kompilator JIT 64-bitowe i zamiast tego używa starszej wersji kompilatora JIT 64-bitowych.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

[\<środowisko uruchomieniowe > — Element](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)   
[\<Konfiguracja > — Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)   
[Środki zaradcze: Nowy kompilator JIT 64-bitowych](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)