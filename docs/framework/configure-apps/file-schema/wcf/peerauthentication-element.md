---
title: '&lt;peerAuthentication&gt;, element'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3cc625f5fdb20505f2e36c5a2d37fca0676bbb37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltpeerauthenticationgt-element"></a><span data-ttu-id="65ad1-102">&lt;peerAuthentication&gt;, element</span><span class="sxs-lookup"><span data-stu-id="65ad1-102">&lt;peerAuthentication&gt; Element</span></span>
<span data-ttu-id="65ad1-103">Określa opcje uwierzytelniania dla klientów peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="65ad1-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="65ad1-104">Zobacz programowania, peer-to-peer [sieci Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="65ad1-104"> peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="65ad1-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="65ad1-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="65ad1-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="65ad1-106">\<behaviors></span></span>  
<span data-ttu-id="65ad1-107">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="65ad1-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="65ad1-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="65ad1-108">\<behavior></span></span>  
<span data-ttu-id="65ad1-109">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="65ad1-109">\<clientCredentials></span></span>  
<span data-ttu-id="65ad1-110">\<peer ></span><span class="sxs-lookup"><span data-stu-id="65ad1-110">\<peer></span></span>  
<span data-ttu-id="65ad1-111">\<PeerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="65ad1-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ad1-112">Składnia</span><span class="sxs-lookup"><span data-stu-id="65ad1-112">Syntax</span></span>  
  
```xml  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="65ad1-113">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="65ad1-113">Attributes and Elements</span></span>  
 <span data-ttu-id="65ad1-114">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="65ad1-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="65ad1-115">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="65ad1-115">Attributes</span></span>  
  
|<span data-ttu-id="65ad1-116">Atrybut</span><span class="sxs-lookup"><span data-stu-id="65ad1-116">Attribute</span></span>|<span data-ttu-id="65ad1-117">Opis</span><span class="sxs-lookup"><span data-stu-id="65ad1-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="65ad1-118">Opcjonalny ciąg.</span><span class="sxs-lookup"><span data-stu-id="65ad1-118">Optional string.</span></span> <span data-ttu-id="65ad1-119">Typ i zestaw używany do walidacji typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="65ad1-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="65ad1-120">Ten atrybut musi być ustawiane podczas `certificateValidationMode` ma ustawioną wartość `Custom`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certifcateValidationMode`|<span data-ttu-id="65ad1-121">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="65ad1-121">Optional enumeration.</span></span> <span data-ttu-id="65ad1-122">Określa jeden z trzech trybów używanych do walidacji poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="65ad1-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="65ad1-123">Jeśli ustawiono `Custom`, a następnie `customCertificateValidator` należy dostarczyć także.</span><span class="sxs-lookup"><span data-stu-id="65ad1-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="65ad1-124">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="65ad1-125">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="65ad1-125">Optional enumeration.</span></span> <span data-ttu-id="65ad1-126">Jeden z trybów użytych do sprawdzenia odwołanych list certyfikatów (CRL).</span><span class="sxs-lookup"><span data-stu-id="65ad1-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="65ad1-127">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="65ad1-128">Opcjonalne wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="65ad1-128">Optional enumeration.</span></span> <span data-ttu-id="65ad1-129">Jeden z dwóch lokalizacji magazynu systemu: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="65ad1-130">Ta wartość jest używana, gdy negocjowane jest certyfikat usługi do klienta.</span><span class="sxs-lookup"><span data-stu-id="65ad1-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="65ad1-131">Sprawdzanie poprawności jest wykonywane przed **zaufane osoby** są przechowywane w lokalizacji określonej magazynu.</span><span class="sxs-lookup"><span data-stu-id="65ad1-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="65ad1-132">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="65ad1-133">customCertificateValidatorType atrybutu</span><span class="sxs-lookup"><span data-stu-id="65ad1-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="65ad1-134">Wartość</span><span class="sxs-lookup"><span data-stu-id="65ad1-134">Value</span></span>|<span data-ttu-id="65ad1-135">Opis</span><span class="sxs-lookup"><span data-stu-id="65ad1-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="65ad1-136">String</span><span class="sxs-lookup"><span data-stu-id="65ad1-136">String</span></span>|<span data-ttu-id="65ad1-137">Określa nazwę typu i zestawu i innych danych można znaleźć typu.</span><span class="sxs-lookup"><span data-stu-id="65ad1-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="65ad1-138">Co najmniej nazwę przestrzeni nazw i typ są wymagane.</span><span class="sxs-lookup"><span data-stu-id="65ad1-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="65ad1-139">Zawiera dodatkowe informacje: Nazwa zestawu, numer wersji, kultury i tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="65ad1-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="65ad1-140">tryb certificateValidationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="65ad1-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="65ad1-141">Wartość</span><span class="sxs-lookup"><span data-stu-id="65ad1-141">Value</span></span>|<span data-ttu-id="65ad1-142">Opis</span><span class="sxs-lookup"><span data-stu-id="65ad1-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="65ad1-143">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="65ad1-143">Enumeration</span></span>|<span data-ttu-id="65ad1-144">Jedną z następujących wartości: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="65ad1-145">Wartość domyślna to `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="65ad1-146">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="65ad1-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="65ad1-147">revocationMode atrybutu</span><span class="sxs-lookup"><span data-stu-id="65ad1-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="65ad1-148">Wartość</span><span class="sxs-lookup"><span data-stu-id="65ad1-148">Value</span></span>|<span data-ttu-id="65ad1-149">Opis</span><span class="sxs-lookup"><span data-stu-id="65ad1-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="65ad1-150">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="65ad1-150">Enumeration</span></span>|<span data-ttu-id="65ad1-151">Jedną z następujących wartości: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="65ad1-152">Wartość domyślna to `Online`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="65ad1-153">Aby uzyskać więcej informacji, zobacz [Praca z certyfikatami](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="65ad1-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="65ad1-154">trustedStoreLocation atrybutu</span><span class="sxs-lookup"><span data-stu-id="65ad1-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="65ad1-155">Wartość</span><span class="sxs-lookup"><span data-stu-id="65ad1-155">Value</span></span>|<span data-ttu-id="65ad1-156">Opis</span><span class="sxs-lookup"><span data-stu-id="65ad1-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="65ad1-157">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="65ad1-157">Enumeration</span></span>|<span data-ttu-id="65ad1-158">Jedną z następujących wartości: `LocalMachine` lub `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="65ad1-159">Wartość domyślna to `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="65ad1-160">Jeśli aplikacja kliencka jest uruchomiona na koncie systemu, a następnie certyfikat jest zwykle w obszarze `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="65ad1-161">Jeśli aplikacja kliencka jest uruchomiona na koncie użytkownika, a następnie certyfikat jest zwykle w `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="65ad1-162">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="65ad1-162">Child Elements</span></span>  
 <span data-ttu-id="65ad1-163">Brak.</span><span class="sxs-lookup"><span data-stu-id="65ad1-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="65ad1-164">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="65ad1-164">Parent Elements</span></span>  
  
|<span data-ttu-id="65ad1-165">Element</span><span class="sxs-lookup"><span data-stu-id="65ad1-165">Element</span></span>|<span data-ttu-id="65ad1-166">Opis</span><span class="sxs-lookup"><span data-stu-id="65ad1-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="65ad1-167">\<peer ></span><span class="sxs-lookup"><span data-stu-id="65ad1-167">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="65ad1-168">Określa poświadczenie używane w celu uwierzytelniania klienta usługi elementu równorzędnego.</span><span class="sxs-lookup"><span data-stu-id="65ad1-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65ad1-169">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65ad1-169">Remarks</span></span>  
 <span data-ttu-id="65ad1-170">`<authentication>` Element odpowiada <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> klasy.</span><span class="sxs-lookup"><span data-stu-id="65ad1-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="65ad1-171">Ten element Określa moduł weryfikacji, który jest wywoływany podczas uwierzytelniania sąsiada sąsiada w siatce.</span><span class="sxs-lookup"><span data-stu-id="65ad1-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="65ad1-172">Próba nawiązania połączenia z elementem sąsiednim przez nowego elementu równorzędnego przekazaniem własną poświadczeń do nieodpowiadający węzłem równorzędnym.</span><span class="sxs-lookup"><span data-stu-id="65ad1-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="65ad1-173">Moduł sprawdzania poprawności obiektu odpowiadającego jest wywoływane w celu Sprawdź poświadczenia strona zdalna.</span><span class="sxs-lookup"><span data-stu-id="65ad1-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="65ad1-174">Zawsze, gdy jest nawiązywane połączenie elementu równorzędnego w sieci, zarówno komputery są wzajemnie uwierzytelnione, znaczenie modułów sprawdzania poprawności po obu stronach są wywoływane.</span><span class="sxs-lookup"><span data-stu-id="65ad1-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65ad1-175">Przykład</span><span class="sxs-lookup"><span data-stu-id="65ad1-175">Example</span></span>  
 <span data-ttu-id="65ad1-176">Poniższy kod ustawia tryb walidacji certyfikatu `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="65ad1-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
     <peerAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
     <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="65ad1-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65ad1-177">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="65ad1-178">Praca z certyfikatami</span><span class="sxs-lookup"><span data-stu-id="65ad1-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="65ad1-179">Sieci peer-to-Peer</span><span class="sxs-lookup"><span data-stu-id="65ad1-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="65ad1-180">Uwierzytelnianie wiadomości kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="65ad1-180">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="65ad1-181">Niestandardowe uwierzytelnianie kanału równorzędnego</span><span class="sxs-lookup"><span data-stu-id="65ad1-181">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="65ad1-182">Zabezpieczanie aplikacji kanałów równorzędnych</span><span class="sxs-lookup"><span data-stu-id="65ad1-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)