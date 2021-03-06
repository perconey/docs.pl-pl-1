---
title: "Instrukcje: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3dc0e44e7f561e39128e32d3af5fbd495316fdd3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a>Instrukcje: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji
Przy użyciu tokenu kontekstu zabezpieczeń stanową (SCT) w ramach bezpiecznej sesji, sesja może wytrzymać odtwarzane usługi. Na przykład gdy bezstanowych SCT jest używany w ramach bezpiecznej sesji i Internet Information Services (IIS) jest resetowany, następnie dane sesji, który jest skojarzony z usługą zostaną utracone. Te dane sesji obejmuje pamięci podręcznej SCT tokenu. Tak przy następnym klient wyśle usługi bezstanowej SCT, zwracany jest błąd, ponieważ nie można pobrać klucza, który jest skojarzony z SCT. Jeśli jednak stanowe SCT jest używany, klucz, który jest skojarzony z SCT jest zawarty w SCT. Ponieważ klucz jest zawarty w SCT i w związku z tym zawarte w wiadomości, bezpiecznej sesji nie ma wpływu na usługi odtwarzane. Domyślnie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] używa bezstanowych SCTs w ramach bezpiecznej sesji. W tym temacie zawiera szczegóły dotyczące sposobu używania stanowe SCTs w ramach bezpiecznej sesji.  
  
> [!NOTE]
>  Stanowe SCTs nie można użyć w ramach bezpiecznej sesji, która obejmuje kontraktu, która jest pochodną <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
> [!NOTE]
>  Dla aplikacji używających stanowe SCTs w ramach bezpiecznej sesji tożsamości wątku dla usługi musi być kontem użytkownika mającą profil użytkownika skojarzony. Po uruchomieniu usługi przy użyciu konta, który nie ma profilu użytkownika, takich jak `Local Service`, może zostać zgłoszony wyjątek.  
  
> [!NOTE]
>  Podczas personifikacji jest wymagane w systemie Windows XP, należy użyć bezpiecznej sesji bez SCT stanowych. Gdy stanowe SCTs są używane z personifikacji, <xref:System.InvalidOperationException> jest generowany. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nieobsługiwanych scenariuszy](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a>Aby użyć stanowe SCTs w ramach bezpiecznej sesji  
  
-   Tworzenie niestandardowego powiązania, które określa, że wiadomości SOAP są chronione przez bezpiecznej sesji, która używa SCT stanowych.  
  
    1.  Definiowanie niestandardowego powiązania, dodając [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) do pliku konfiguracji dla usługi.  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  Dodaj [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu podrzędnego do [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Określ nazwę powiązania, ustawiając `name` atrybutu unikatową nazwę w pliku konfiguracji.  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  Określ tryb uwierzytelniania wiadomości wysyłane do i z tej usługi, dodając [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu podrzędnego do [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
         Określ, że bezpiecznej sesji jest używana przez ustawienie `authenticationMode` atrybutu `SecureConversation`. Określ, czy stanowe SCTs są używane przez ustawienie `requireSecurityContextCancellation` atrybutu `false`.  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  Określ sposób klienta jest uwierzytelniania podczas nawiązywania bezpiecznej sesji zostanie nawiązane, dodając [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elementu podrzędnego do [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).  
  
         Określ, jak klient jest uwierzytelniany przez ustawienie `authenticationMode` atrybutu.  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  Określ kodowanie komunikatu przez dodanie elementu kodowania, takich jak [ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  Określ transportu, dodając element transportu, takich jak [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).  
  
        ```xml  
        <httpTransport />  
        ```  
  
     Poniższy przykład kodu wykorzystuje konfiguracji do określenia niestandardowego powiązania, które wiadomości za pomocą stanowe SCTs w ramach bezpiecznej sesji.  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu tworzy niestandardowego powiązania, który używa <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> tryb uwierzytelniania do ładowania początkowego bezpiecznej sesji.  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 Gdy jest używane uwierzytelnianie systemu Windows w połączeniu z SCT stanowe, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie wypełnia <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwości z funkcją wywołującą rzeczywistej tożsamości użytkownika, ale zamiast tego ustawia tę właściwość na anonimowe. Ponieważ [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń należy ponownie utworzyć zawartość usługi kontekstu zabezpieczeń dla każdego żądania z przychodzącego SCT, serwer nie przechowywać informacji o sesji zabezpieczeń w pamięci. Ponieważ nie jest możliwe do serializacji <xref:System.Security.Principal.WindowsIdentity> wystąpienia na SCT <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> właściwość zwraca Tożsamość anonimowa.  
  
 Następująca konfiguracja wykazuje to zachowanie.  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security   
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
      </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
