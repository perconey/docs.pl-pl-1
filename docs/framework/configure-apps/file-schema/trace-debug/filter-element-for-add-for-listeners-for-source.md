---
title: "&lt;Filtr&gt; elementu &lt;dodać&gt; dla &lt;odbiorników&gt; dla &lt;źródła&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#filter
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- <filter> element for <add> for <listeners> for <source>
- filter element for <add> for <listeners> for <source>
ms.assetid: 15808b80-4579-4c25-b385-178cfdf154ba
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: ff5acf8edcda68979c04f5e62237464ee6f040a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltergt-element-for-ltaddgt-for-ltlistenersgt-for-ltsourcegt"></a>&lt;Filtr&gt; elementu &lt;dodać&gt; dla &lt;odbiorników&gt; dla &lt;źródła&gt;
Dodaje filtr do odbiornika w `Listeners` kolekcji źródła śledzenia.  
  
 \<Konfiguracja >  
\<System.Diagnostics >  
\<źródeł >  
\<źródło >  
\<obiekty nasłuchujące >  
\<Dodaj >  
\<Filtr >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`type`|Atrybut wymagany.<br /><br /> Określa typ filtr, który powinien dziedziczyć <xref:System.Diagnostics.TraceFilter> klasy. Można użyć nazwa kwalifikowana przestrzeni nazw, typu, który odpowiada na typ <xref:System.Type.FullName%2A> właściwości lub użyć pełni kwalifikowana nazwa typu w tym informacje o zestawie, który odpowiada <xref:System.Type.AssemblyQualifiedName%2A> właściwości. Aby uzyskać informacje dotyczące w pełni kwalifikowane nazwy typów, zobacz [określenie pełni kwalifikowane nazwy typów](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atrybut opcjonalny.<br /><br /> Ciąg przekazany do konstruktora dla klasy określonego filtru.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.diagnostics`|Określa obiektów nasłuchujących śledzenia zbierania, przechowywania i kierowania wiadomości i poziom, gdy jest ustawiona przełącznik śledzenia.|  
|`sources`|Zawiera źródła śledzenia, które inicjują śledzenia wiadomości.|  
|`source`|Określa źródło śledzenia, który inicjuje śledzenia wiadomości.|  
|`listeners`|Zawiera nasłuchujących zbierania, przechowywania i kierowania wiadomości. Odbiorniki bezpośrednie dane wyjściowe śledzenia do odpowiedniego obiektu docelowego.|  
|`add`|Dodaje odbiornika do `Listeners` kolekcji źródła śledzenia.|  
  
## <a name="remarks"></a>Uwagi  
 `<filter>` Elementu muszą być zawarte w `<add>` dla odbiornika źródła śledzenia, która określa typ odbiornika, nie tylko nazwę odbiornik w zdefiniowany element [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md). Jeśli odbiornik jest zdefiniowany w [ \<sharedListeners >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md), filtr dla tego odbiornika musi być zdefiniowana w tym elemencie.  
  
 Ten element może być użyty w pliku konfiguracji komputera (Machine.config) i pliku konfiguracji aplikacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie `<filter>` element, aby dodać filtr do odbiornika `console` w `Listeners` kolekcji źródła śledzenia `myTraceSource`, określając poziom zdarzenia filtru jako `Error`.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" switchName="SourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter"   
              initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="SourceSwitch" value="Warning" />  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceFilter>  
 [Schemat ustawień śledzenia i debugowania](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
