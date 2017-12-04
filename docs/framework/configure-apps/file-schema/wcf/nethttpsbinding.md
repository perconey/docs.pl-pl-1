---
title: '&lt;netHttpsBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ff122116-6042-4792-9f21-275b4f97a105
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e339066311adf10791c1b6759cc7be6b419320b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltnethttpsbindinggt"></a><span data-ttu-id="3eacd-102">&lt;netHttpsBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="3eacd-102">&lt;netHttpsBinding&gt;</span></span>
<span data-ttu-id="3eacd-103">Reprezentuje powiązanie, które [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usługi można użyć do konfiguracji i ekspozycji punktów końcowych, które mogą się komunikować za pośrednictwem protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3eacd-103">Represents a binding that a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service can use to configure and expose endpoints that are able to communicate over HTTPS.</span></span> <span data-ttu-id="3eacd-104">W przypadku użycia z kontrakt dupleksowy, gniazda sieci Web, który będzie używany, w przeciwnym razie będzie używany protokół HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3eacd-104">When used with a duplex contract, Web Sockets will be used, otherwise HTTPS will be used.</span></span>  
  
 <span data-ttu-id="3eacd-105">Element główny</span><span class="sxs-lookup"><span data-stu-id="3eacd-105">Root Element</span></span>  
<span data-ttu-id="3eacd-106">Następny Element</span><span class="sxs-lookup"><span data-stu-id="3eacd-106">Next Element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eacd-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="3eacd-107">Syntax</span></span>  

```xml
<netHttpsBinding>  
  <binding allowCookies="Boolean"  
           bypassProxyOnLocal="Boolean"  
           closeTimeout="TimeSpan"   
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
           maxBufferPoolSize="Integer"  
           maxBufferSize="Integer"  
           maxReceivedMessageSize="Integer"  
           messageEncoding="Binary/Text/Mtom"  
           name="string"   
           openTimeout="TimeSpan"   
           proxyAddress="URI"  
           receiveTimeout="TimeSpan"  
           sendTimeout="TimeSpan"  
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                 realm="string" />  
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" 
               clientCredentialType="UserName/Certificate"/>  
    </security>  
    <readerQuotas maxArrayLength="Integer" 
                  maxBytesPerRead="Integer" 
                  maxDepth="Integer" 
                  maxNameTableCharCount="Integer" 
                  maxStringContentLength="Integer" />  
  </binding>  
</netHttpsBinding>  
```  
  
## <a name="type"></a><span data-ttu-id="3eacd-108">Typ</span><span class="sxs-lookup"><span data-stu-id="3eacd-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3eacd-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3eacd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3eacd-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3eacd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3eacd-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3eacd-111">Attributes</span></span>  
  
|<span data-ttu-id="3eacd-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3eacd-112">Attribute</span></span>|<span data-ttu-id="3eacd-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3eacd-113">Description</span></span>|  
|---------------|-----------------|  
|`allowCookies`|<span data-ttu-id="3eacd-114">Wartość logiczna wskazująca, czy klient akceptuje pliki cookie i propaguje je do przyszłych żądań.</span><span class="sxs-lookup"><span data-stu-id="3eacd-114">A Boolean value that indicates whether the client accepts cookies and propagates them on future requests.</span></span> <span data-ttu-id="3eacd-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="3eacd-115">The default is `false`.</span></span><br /><br /> <span data-ttu-id="3eacd-116">Tej właściwości można użyć w przypadku interakcji z usługami sieci Web ASMX, które używają plików cookie.</span><span class="sxs-lookup"><span data-stu-id="3eacd-116">You can use this property when you interact with ASMX Web services that use cookies.</span></span> <span data-ttu-id="3eacd-117">W ten sposób można się upewnić, że pliki cookie zwrócony z serwera, automatycznie są kopiowane do wszystkich przyszłych żądań dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="3eacd-117">In this way, you can be sure that the cookies returned from the server are automatically copied to all future client requests for that service.</span></span>|  
|`bypassProxyOnLocal`|<span data-ttu-id="3eacd-118">Wartość logiczna, która wskazuje, czy pominąć serwer proxy dla adresów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="3eacd-118">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="3eacd-119">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="3eacd-119">The default is `false`.</span></span><br /><br /> <span data-ttu-id="3eacd-120">Zasobu internetowego jest lokalny, jeśli ma ona adresu lokalnego.</span><span class="sxs-lookup"><span data-stu-id="3eacd-120">An Internet resource is local if it has a local address.</span></span> <span data-ttu-id="3eacd-121">Lokalny adres jest taki, który znajduje się na tym samym komputerze, lokalnej sieci LAN lub intranet i jest identyfikowany, składniowo, brak kropki (.) jak identyfikatory URI "http://webserver/" i "http://localhost/".</span><span class="sxs-lookup"><span data-stu-id="3eacd-121">A local address is one that is on same computer, the local LAN or intranet and is identified, syntactically, by the lack of a period (.) as in the URIs "http://webserver/" and "http://localhost/".</span></span><br /><br /> <span data-ttu-id="3eacd-122">Ustawienie ten atrybut określa, czy punkty końcowe skonfigurowane z BasicHttpBinding Użyj serwera proxy podczas uzyskiwania dostępu do zasobów lokalnych.</span><span class="sxs-lookup"><span data-stu-id="3eacd-122">Setting this attribute determines whether endpoints configured with the BasicHttpBinding use the proxy server when accessing local resources.</span></span> <span data-ttu-id="3eacd-123">Jeśli ten atrybut jest `true`, żądań lokalnych zasobów w Internecie, nie należy używać serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="3eacd-123">If this attribute is `true`, requests to local Internet resources do not use the proxy server.</span></span> <span data-ttu-id="3eacd-124">Użyj hosta nazw (zamiast localhost), jeśli klienci mają przechodzić przez serwer proxy po rozmowie z usługi na tym samym komputerze, gdy ten atrybut ma ustawioną `true`.</span><span class="sxs-lookup"><span data-stu-id="3eacd-124">Use the host name (rather than localhost) if you want clients to go through a proxy when talking to services on the same machine when this attribute is set to `true`.</span></span><br /><br /> <span data-ttu-id="3eacd-125">Jeśli ten atrybut jest `false`, wszystkie żądania internetowe są nawiązywane przy użyciu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="3eacd-125">When this attribute is `false`, all Internet requests are made through the proxy server.</span></span>|  
|`closeTimeout`|<span data-ttu-id="3eacd-126">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="3eacd-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="3eacd-127">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3eacd-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3eacd-128">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3eacd-128">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="3eacd-129">Określa tryb porównania nazw hostów HTTP używany do przeprowadzenia analizy identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="3eacd-129">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="3eacd-130">Ten atrybut jest typu `HostnameComparisonMode`, która wskazuje, czy nazwa hosta jest używana w celu dotarcia do usługi podczas dopasowywania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="3eacd-130">This attribute is of type `HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="3eacd-131">Wartość domyślna to `StrongWildcard`, który ignoruje nazwy hosta w dopasowania.</span><span class="sxs-lookup"><span data-stu-id="3eacd-131">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="3eacd-132">Wartość całkowita określająca maksymalną ilość pamięci przydzielonej do użycia przez menedżera buforów komunikatów, który odbiera komunikaty z kanału.</span><span class="sxs-lookup"><span data-stu-id="3eacd-132">An integer value that specifies the maximum amount of memory that is allocated for use by the manager of the message buffers that receive messages from the channel.</span></span> <span data-ttu-id="3eacd-133">Wartość domyślna to 524288 (0x80000) bajtów.</span><span class="sxs-lookup"><span data-stu-id="3eacd-133">The default value is 524288 (0x80000) bytes.</span></span><br /><br /> <span data-ttu-id="3eacd-134">Menedżera buforów minimalizację kosztów bufory przy użyciu puli bufora.</span><span class="sxs-lookup"><span data-stu-id="3eacd-134">The Buffer Manager minimizes the cost of using buffers by using a buffer pool.</span></span> <span data-ttu-id="3eacd-135">Bufory są wymagane do przetwarzania komunikatów przez usługę, po znalezieniu poza kanału.</span><span class="sxs-lookup"><span data-stu-id="3eacd-135">Buffers are required to process messages by the service when they come out of the channel.</span></span> <span data-ttu-id="3eacd-136">Jeśli w puli buforów do przetworzenia obciążenia komunikat nie ma wystarczającej ilości pamięci, menedżera buforów musi przydzielić dodatkową pamięć sterty CLR, co zwiększa obciążenie kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="3eacd-136">If there is not sufficient memory in the buffer pool to process the message load, the Buffer Manager must allocate additional memory from the CLR heap, which increases the garbage collection overhead.</span></span> <span data-ttu-id="3eacd-137">Rozbudowana alokacji sterty pamięci CLR jest wskazanie, że rozmiar puli buforów jest za mały, i że można poprawić wydajność z alokacją większych przez odpowiednie zwiększenie limitu określonego przez tego atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3eacd-137">Extensive allocation from the CLR garbage heap is an indication that the buffer pool size is too small and that performance can be improved with a larger allocation by increasing the limit specified by this attribute.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="3eacd-138">Wartość całkowita określająca maksymalny rozmiar w bajtach buforu, który przechowuje komunikaty podczas przetwarzania dla punkt końcowy skonfigurowany dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="3eacd-138">An integer value that specifies the maximum size, in bytes, of a buffer that stores messages while they are processed for an endpoint configured with this binding.</span></span> <span data-ttu-id="3eacd-139">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="3eacd-139">The default value is 65,536 bytes.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="3eacd-140">Dodatnia liczba całkowita, która określa maksymalny rozmiar wiadomości, w bajtach, włącznie z nagłówkami komunikatu, który może zostać odebrany w kanale skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="3eacd-140">A positive integer that defines the maximum message size, in bytes, including headers, for a message that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="3eacd-141">Nadawca otrzymuje błędu protokołu SOAP, jeśli komunikat jest zbyt duży dla odbiornika.</span><span class="sxs-lookup"><span data-stu-id="3eacd-141">The sender receives a SOAP fault if the message is too large for the receiver.</span></span> <span data-ttu-id="3eacd-142">Odbiornik porzuca wiadomości i tworzy wpis zdarzenia w dzienniku śledzenia.</span><span class="sxs-lookup"><span data-stu-id="3eacd-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="3eacd-143">Wartość domyślna to 65 536 bajtów.</span><span class="sxs-lookup"><span data-stu-id="3eacd-143">The default is 65,536 bytes.</span></span>|  
|`messageEncoding`|<span data-ttu-id="3eacd-144">Definiuje koder używany do kodowania komunikatu protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="3eacd-144">Defines the encoder used to encode the SOAP message.</span></span> <span data-ttu-id="3eacd-145">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="3eacd-145">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3eacd-146">-Tekst: Użyj kodera wiadomości tekstowych.</span><span class="sxs-lookup"><span data-stu-id="3eacd-146">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="3eacd-147">-Mtom: Za pomocą kodera wiadomości transmisji organizacji mechanizmu 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="3eacd-147">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="3eacd-148">Wartość domyślna to tekst.</span><span class="sxs-lookup"><span data-stu-id="3eacd-148">The default is Text.</span></span> <span data-ttu-id="3eacd-149">Ten atrybut jest typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="3eacd-149">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|`name`|<span data-ttu-id="3eacd-150">Ciąg zawierający nazwę konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="3eacd-150">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="3eacd-151">Wartość ta powinna być unikatowa, ponieważ jest używany jako identyfikator dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="3eacd-151">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="3eacd-152">Każdego powiązania ma `name` i `namespace` atrybutu niesekwencyjnego razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="3eacd-152">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="3eacd-153">Ponadto ta nazwa jest unikatowa wśród powiązania tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="3eacd-153">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="3eacd-154">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="3eacd-154">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3eacd-155">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3eacd-155">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`namespace`|<span data-ttu-id="3eacd-156">Określa przestrzeń nazw XML powiązania.</span><span class="sxs-lookup"><span data-stu-id="3eacd-156">Specifies the XML namespace of the binding.</span></span> <span data-ttu-id="3eacd-157">Wartość domyślna to "http://tempuri.org/Bindings".</span><span class="sxs-lookup"><span data-stu-id="3eacd-157">The default value is "http://tempuri.org/Bindings".</span></span> <span data-ttu-id="3eacd-158">Każdego powiązania ma `name` i `namespace` atrybutu niesekwencyjnego razem jednoznacznie zidentyfikować je w metadanych usługi.</span><span class="sxs-lookup"><span data-stu-id="3eacd-158">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span>|  
|`openTimeout`|<span data-ttu-id="3eacd-159">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="3eacd-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="3eacd-160">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3eacd-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3eacd-161">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3eacd-161">The default is 00:01:00.</span></span>|  
|`proxyAddress`|<span data-ttu-id="3eacd-162">Identyfikator URI zawierający adres serwera proxy HTTP.</span><span class="sxs-lookup"><span data-stu-id="3eacd-162">A URI that contains the address of the HTTP proxy.</span></span> <span data-ttu-id="3eacd-163">Jeśli `useSystemWebProxy` ustawiono `true`, to ustawienie musi być `null`.</span><span class="sxs-lookup"><span data-stu-id="3eacd-163">If `useSystemWebProxy` is set to `true`, this setting must be `null`.</span></span> <span data-ttu-id="3eacd-164">Wartość domyślna to `null`.</span><span class="sxs-lookup"><span data-stu-id="3eacd-164">The default is `null`.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="3eacd-165">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="3eacd-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="3eacd-166">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3eacd-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3eacd-167">Wartość domyślna to 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="3eacd-167">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="3eacd-168">A <xref:System.TimeSpan> wartość, która określa interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="3eacd-168">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="3eacd-169">Ta wartość powinna być większa lub równa <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="3eacd-169">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3eacd-170">Wartość domyślna to 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3eacd-170">The default is 00:01:00.</span></span>|  
|`textEncoding`|<span data-ttu-id="3eacd-171">Ustawia kodowanie do użycia w celu emisji komunikatów w powiązaniu zestawu znaków.</span><span class="sxs-lookup"><span data-stu-id="3eacd-171">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="3eacd-172">Prawidłowe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="3eacd-172">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3eacd-173">-BigEndianUnicode: Unicode BigEndian kodowanie.</span><span class="sxs-lookup"><span data-stu-id="3eacd-173">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="3eacd-174">-Unicode: 16-bitowego kodowania.</span><span class="sxs-lookup"><span data-stu-id="3eacd-174">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="3eacd-175">-UTF8: 8-bitowego kodowania o</span><span class="sxs-lookup"><span data-stu-id="3eacd-175">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="3eacd-176">Wartość domyślna to UTF8.</span><span class="sxs-lookup"><span data-stu-id="3eacd-176">The default is UTF8.</span></span> <span data-ttu-id="3eacd-177">Ten atrybut jest typu <xref:System.Text.Encoding>.</span><span class="sxs-lookup"><span data-stu-id="3eacd-177">This attribute is of type <xref:System.Text.Encoding>.</span></span>|  
|`transferMode`|<span data-ttu-id="3eacd-178">Prawidłowy <xref:System.ServiceModel.TransferMode> wartość określająca, czy komunikaty są buforowane, czy strumieniowego na żądanie lub odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="3eacd-178">A valid <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed on a request or response.</span></span>|  
|`useDefaultWebProxy`|<span data-ttu-id="3eacd-179">Wartość logiczna określająca, czy ma być używane automatycznie skonfigurowany serwer proxy HTTP systemu, jeśli jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="3eacd-179">A Boolean value that specifies whether the auto-configured HTTP proxy of the system should be used, if available.</span></span> <span data-ttu-id="3eacd-180">Wartość domyślna to `true`.</span><span class="sxs-lookup"><span data-stu-id="3eacd-180">The default is `true`.</span></span>|  
|||  
  
### <a name="child-elements"></a><span data-ttu-id="3eacd-181">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3eacd-181">Child Elements</span></span>  
  
|<span data-ttu-id="3eacd-182">Element</span><span class="sxs-lookup"><span data-stu-id="3eacd-182">Element</span></span>|<span data-ttu-id="3eacd-183">Opis</span><span class="sxs-lookup"><span data-stu-id="3eacd-183">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3eacd-184">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="3eacd-184">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nethttpbinding.md)|<span data-ttu-id="3eacd-185">Definiuje ustawienia zabezpieczeń dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="3eacd-185">Defines the security settings for the binding.</span></span> <span data-ttu-id="3eacd-186">Ten element jest typu <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="3eacd-186">This element is of type <xref:System.ServiceModel.Configuration.BasicHttpsSecurityElement>.</span></span> |  
|[<span data-ttu-id="3eacd-187">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="3eacd-187">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="3eacd-188">Definiuje ograniczenia złożoności wiadomości SOAP, które mogą być przetwarzane przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="3eacd-188">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="3eacd-189">Ten element jest typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="3eacd-189">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3eacd-190">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3eacd-190">Parent Elements</span></span>  
  
|<span data-ttu-id="3eacd-191">Element</span><span class="sxs-lookup"><span data-stu-id="3eacd-191">Element</span></span>|<span data-ttu-id="3eacd-192">Opis</span><span class="sxs-lookup"><span data-stu-id="3eacd-192">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3eacd-193">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="3eacd-193">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="3eacd-194">Ten element przetrzymuje kolekcję powiązań standardowych i niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="3eacd-194">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3eacd-195">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3eacd-195">Remarks</span></span>  
 <span data-ttu-id="3eacd-196">NetHttpsBinding używa protokołu HTTPS jako transportu do wysyłania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="3eacd-196">The NetHttpsBinding uses HTTPS as the transport for sending messages.</span></span> <span data-ttu-id="3eacd-197">W przypadku użycia z kontrakt dupleksowy, będą używane gniazda sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3eacd-197">When used with a duplex contract, Web Sockets will be used.</span></span>  <span data-ttu-id="3eacd-198">W przypadku korzystania z kontraktem "żądanie-odpowiedź", który NetHttpsBinding będą zachowywać się jak BasicHttpsBinding z kodera binarnego.</span><span class="sxs-lookup"><span data-stu-id="3eacd-198">When used with a request-reply contract NetHttpsBinding will behave like a BasicHttpsBinding with a binary encoder.</span></span>  
  
 <span data-ttu-id="3eacd-199">Zabezpieczenia jest domyślnie wyłączona, ale można dodać ustawienie atrybutu tryb [ \<zabezpieczeń >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) element podrzędny, wartość inną niż `None`.</span><span class="sxs-lookup"><span data-stu-id="3eacd-199">Security is turned off by default, but can be added setting the mode attribute of the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) child element to a value other than `None`.</span></span> <span data-ttu-id="3eacd-200">Używa tekst kodowania i UTF-8 komunikatu "Text" kodowaniu.</span><span class="sxs-lookup"><span data-stu-id="3eacd-200">It uses a "Text" message encoding and UTF-8 text encoding by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3eacd-201">Przykład</span><span class="sxs-lookup"><span data-stu-id="3eacd-201">Example</span></span>  
 <span data-ttu-id="3eacd-202">W poniższym przykładzie pokazano użycie <xref:System.ServiceModel.NetHttpBinding> zapewnia współdziałanie komunikacji i maksymalnie HTTPS z pierwszej - i second - generation usług sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3eacd-202">The following example demonstrates the use of <xref:System.ServiceModel.NetHttpBinding> that provides HTTPS communication and maximum interoperability with first- and second-generation Web services.</span></span> <span data-ttu-id="3eacd-203">Powiązanie jest określona w plikach konfiguracji dla klienta i usługi.</span><span class="sxs-lookup"><span data-stu-id="3eacd-203">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="3eacd-204">Typ powiązania jest określona za pomocą `binding` atrybutu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3eacd-204">The binding type is specified using the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="3eacd-205">Jeśli chcesz skonfigurować podstawowe powiązanie i zmieniania jego ustawień należy zdefiniować konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="3eacd-205">If you want to configure the basic binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="3eacd-206">Punkt końcowy musi odwoływać się Konfiguracja powiązania o nazwie przy użyciu `bindingConfiguration` atrybutu `<endpoint>` element, jak pokazano w poniższym kodzie konfiguracji dla usługi.</span><span class="sxs-lookup"><span data-stu-id="3eacd-206">The endpoint must reference the binding configuration by name by using the `bindingConfiguration` attribute of the `<endpoint>` element, as shown in the following configuration code for the service.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
      <endpoint address=""  
                binding="netHttpsBinding"  
                bindingConfiguration="Binding1"   
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
    <netHttpsBinding>  
      <binding name="Binding1"   
               hostNameComparisonMode="StrongWildcard" 
               receiveTimeout="00:10:00" 
               sendTimeout="00:10:00" 
               openTimeout="00:10:00" 
               closeTimeout="00:10:00" 
               maxReceivedMessageSize="65536" 
               maxBufferSize="65536" 
               maxBufferPoolSize="524288" 
               transferMode="Buffered" 
               messageEncoding="Binary" 
               textEncoding="utf-8" 
               bypassProxyOnLocal="false" 
               useDefaultWebProxy="true">  
        <security mode="None" />  
      </binding>  
    </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a><span data-ttu-id="3eacd-207">Przykład</span><span class="sxs-lookup"><span data-stu-id="3eacd-207">Example</span></span>  
 <span data-ttu-id="3eacd-208">Począwszy od [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], powiązania i zachowania nie muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="3eacd-208">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3eacd-209">Funkcje z poprzednim przykładzie można osiągnąć przez usunięcie bindingConfiguration z adres punktu końcowego i frm nazwę powiązania.</span><span class="sxs-lookup"><span data-stu-id="3eacd-209">The functionality from the previous example can be accomplished by removing the bindingConfiguration from the endpoint address and the name frm the binding.</span></span>  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpsBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpsBinding>  
        <binding   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Binary"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpsBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="3eacd-210">Aby uzyskać więcej informacji o konfiguracji domyślnej i bez powiązania i zachowania, zobacz [uproszczony konfiguracji](../../../../../docs/framework/wcf/simplified-configuration.md) i [uproszczona konfiguracja usług WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3eacd-210">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3eacd-211">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3eacd-211">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [<span data-ttu-id="3eacd-212">Powiązania</span><span class="sxs-lookup"><span data-stu-id="3eacd-212">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3eacd-213">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="3eacd-213">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3eacd-214">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="3eacd-214">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="3eacd-215">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="3eacd-215">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)