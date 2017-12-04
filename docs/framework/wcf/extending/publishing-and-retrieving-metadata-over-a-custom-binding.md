---
title: "Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4f66821f38e8915ee93cf5b1b77dd75e32662121
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a><span data-ttu-id="f572b-102">Publikowanie i pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="f572b-102">Publishing and Retrieving Metadata Over a Custom Binding</span></span>
<span data-ttu-id="f572b-103"><xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> Umożliwia dodawanie punktu końcowego metadanych do usługi.</span><span class="sxs-lookup"><span data-stu-id="f572b-103">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> provides support for adding metadata endpoint to a service.</span></span> <span data-ttu-id="f572b-104">Te punkty końcowe metadanych może odpowiadać na żądania HTTP GET pod adresem URL, który ma `?wsdl` querystring i na żądanie GET usługi WS-Transfer zgodnie z definicją w specyfikacji WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="f572b-104">These metadata endpoints can respond to HTTP GET requests at a URL that has a `?wsdl` querystring and to WS-Transfer GET requests as defined in the WS-MetadataExchange (MEX) specification.</span></span> <span data-ttu-id="f572b-105">Punkty końcowe MEX zaimplementować <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f572b-105">MEX endpoints implement the <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> contract.</span></span>  
  
## <a name="publishing-metadata-over-a-custom-binding"></a><span data-ttu-id="f572b-106">Publikowanie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="f572b-106">Publishing Metadata Over a Custom Binding</span></span>  
 <span data-ttu-id="f572b-107">Punkty końcowe metadanych GET protokołu HTTP i HTTPS GET punkty końcowe metadanych są włączone przez ustawienie <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> lub <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="f572b-107">The HTTP GET metadata endpoints and HTTPS GET metadata endpoints are enabled by setting the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> properties to `true`.</span></span> <span data-ttu-id="f572b-108">Nie można skonfigurować powiązania z tymi punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="f572b-108">The bindings for these endpoints cannot be configured.</span></span>  
  
 <span data-ttu-id="f572b-109"><xref:System.ServiceModel.Description.IMetadataExchange> Kontraktu, jednak może być używany z dowolnego punktu końcowego, w tym tych, które korzystają z niestandardowego powiązania, ponieważ <xref:System.ServiceModel.Description.IMetadataExchange> punkty końcowe są takie same jak każdy inny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="f572b-109">The <xref:System.ServiceModel.Description.IMetadataExchange> contract, however, can be used with any endpoint, including those that use custom bindings, because <xref:System.ServiceModel.Description.IMetadataExchange> endpoints are identical to any other [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service endpoint.</span></span> <span data-ttu-id="f572b-110">Jeśli wiesz, jak do modyfikacji konfiguracji powiązania dostarczane przez system, lub wiesz, jak skonfigurować <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, a następnie można skonfigurować powiązania do użycia z <xref:System.ServiceModel.Description.IMetadataExchange> punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="f572b-110">If you know how to modify the configuration of a system-provided binding, or you know how to configure a <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, then you can configure a binding for use with an <xref:System.ServiceModel.Description.IMetadataExchange> endpoint.</span></span>  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a><span data-ttu-id="f572b-111">Pobieranie metadanych za pośrednictwem powiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="f572b-111">Retrieving Metadata Over a Custom Binding</span></span>  
 <span data-ttu-id="f572b-112">Można pobrać metadanych od Get protokołu HTTP i HTTPS Get punkty końcowe metadanych przy użyciu standardowych żądań HTTP lub HTTPS GET.</span><span class="sxs-lookup"><span data-stu-id="f572b-112">Metadata can be retrieved from HTTP Get and HTTPS Get metadata endpoints using standard HTTP or HTTPS GET requests.</span></span>  
  
 <span data-ttu-id="f572b-113">Do pobierania metadanych z punktu końcowego metadanych MEX zazwyczaj służy jedną standardowe powiązania MEX. obsługiwane przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f572b-113">To retrieve metadata from a MEX metadata endpoint you can generally use one of the standard MEX bindings supported by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="f572b-114"> <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f572b-114"> <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f572b-115"><xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> Typu i z narzędzia Svcutil.exe automatycznie wybierz jedną z tych standardowe powiązań MEX na podstawie adresu punktu końcowego określonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="f572b-115">The <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> type and the Svcutil.exe tool automatically select one of these standard MEX bindings based on the address of the specified metadata endpoint.</span></span>  
  
 <span data-ttu-id="f572b-116">Jeśli punkt końcowy metadanych MEX używa inne powiązanie niż standardowe powiązania MEX., można skonfigurować powiązania, używany przez <xref:System.ServiceModel.Description.MetadataExchangeClient> przy użyciu kodu lub przez podanie <xref:System.ServiceModel.Description.IMetadataExchange> konfiguracji punktu końcowego klienta.</span><span class="sxs-lookup"><span data-stu-id="f572b-116">If a MEX metadata endpoint uses a different binding than one of the standard MEX bindings, you can configure the binding used by the <xref:System.ServiceModel.Description.MetadataExchangeClient> using code or by providing an <xref:System.ServiceModel.Description.IMetadataExchange> client endpoint configuration.</span></span> <span data-ttu-id="f572b-117">Narzędzia Svcutil.exe automatycznie ładuje z plikiem konfiguracji <xref:System.ServiceModel.Description.IMetadataExchange> konfiguracji punktu końcowego klienta, który ma taką samą nazwę jak schemat identyfikatora URI dla adresu punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="f572b-117">The Svcutil.exe tool automatically loads from its configuration file an <xref:System.ServiceModel.Description.IMetadataExchange> client endpoint configuration that has the same name as the URI scheme for the metadata endpoint address.</span></span>  
  
## <a name="security"></a><span data-ttu-id="f572b-118">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="f572b-118">Security</span></span>  
 <span data-ttu-id="f572b-119">Podczas publikowania metadanych za pośrednictwem powiązania niestandardowego, upewnij się, że powiązanie zawiera obsługi zabezpieczeń, która wymaga metadanych.</span><span class="sxs-lookup"><span data-stu-id="f572b-119">When publishing metadata over a custom binding, ensure that the binding provides the security support that your metadata requires.</span></span> <span data-ttu-id="f572b-120">Na przykład, aby zapobiec ujawnieniu informacji i upewnij się, klient ma prawo do uzyskania metadanych, można wprowadzeniu metadanych i aplikacji bezpieczniejsze przez skonfigurowanie sieci <xref:System.ServiceModel.Description.IMetadataExchange> punktu końcowego, aby wymagać uwierzytelniania i szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="f572b-120">For example, to prevent information disclosure and ensure your client has the right to obtain the metadata, you can make your metadata and your application more secure by configuring your <xref:System.ServiceModel.Description.IMetadataExchange> endpoint to require authentication and encryption.</span></span> <span data-ttu-id="f572b-121">Przykład [punktu końcowego metadanych niestandardowy bezpieczny](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) pokazano, w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="f572b-121">The sample [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) demonstrates this scenario.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f572b-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f572b-122">See Also</span></span>  
 [<span data-ttu-id="f572b-123">Zabezpieczanie usług</span><span class="sxs-lookup"><span data-stu-id="f572b-123">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="f572b-124">Powiązania WS-MetadataExchange</span><span class="sxs-lookup"><span data-stu-id="f572b-124">WS-MetadataExchange Bindings</span></span>](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)  
 [<span data-ttu-id="f572b-125">Porady: Konfigurowanie niestandardowych WS-Metadata Exchange powiązania</span><span class="sxs-lookup"><span data-stu-id="f572b-125">How to: Configure a Custom WS-Metadata Exchange Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [<span data-ttu-id="f572b-126">Porady: Pobieranie metadanych przez wiązanie inne niż wymiany</span><span class="sxs-lookup"><span data-stu-id="f572b-126">How to: Retrieve Metadata Over a non-MEX Binding</span></span>](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)