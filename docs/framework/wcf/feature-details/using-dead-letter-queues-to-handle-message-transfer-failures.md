---
title: "Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem"
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
ms.assetid: 9e891c6a-d960-45ea-904f-1a00e202d61a
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1b02d1d826e78d7f324e638d7e2baac96bb8bbaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-dead-letter-queues-to-handle-message-transfer-failures"></a>Używanie utraconych kolejek na potrzeby obsługi transferów komunikatów zakończonych niepowodzeniem
Wiadomości w kolejce może zakończyć się niepowodzeniem dostarczania. Te komunikaty nie powiodło się są rejestrowane w kolejce wiadomości utraconych. Nie powiodło się dostarczania może być spowodowane powodów, takich jak awarie sieci, usunięto kolejki, pełną kolejkę, niepowodzenie uwierzytelniania lub niepowodzenie dostarczyć na czas.  
  
 Wiadomości w kolejce może pozostawać w kolejce przez długi czas, jeśli aplikacja odbierająca nie czytania z kolejki w odpowiednim czasie. To zachowanie nie może być odpowiednie dla komunikatów o określonym terminie ważności. Komunikaty o określonym terminie ważności mają czasu wygaśnięcia (TTL) ustawiona w kolejce powiązanie, która wskazuje, jak długo komunikaty mogą znajdować się w kolejce przed wygaśnięciem. Wygasłe komunikaty są wysyłane do specjalnego kolejki o nazwie Kolejka utraconych wiadomości. Komunikaty możesz także umieścić w kolejce wiadomości utraconych z innych przyczyn, takich jak przekracza przydział kolejki lub z powodu błędu uwierzytelniania.  
  
 Ogólnie rzecz biorąc aplikacje zapisu kompensacji logiki, aby odczytać wiadomości z kolejki utraconych wiadomości i przyczyny niepowodzenia. Logika kompensacji jest zależna od przyczynę niepowodzenia. Można na przykład w przypadku niepowodzenia uwierzytelniania, popraw certyfikatu załączonego z komunikatem i ponownie wysłać wiadomość. Dostarczenie nie powiodło się, ponieważ osiągnięto limit przydziału kolejki docelowej, można następnie ponów próbę dostarczania w nadzieję, że przydział problem został rozwiązany.  
  
 Najbardziej kolejkowania systemy mają systemowe kolejki utraconych wiadomości, gdzie są przechowywane wszystkie komunikaty nie powiodło się z tego systemu. Usługi kolejkowania komunikatów (MSMQ) zawiera dwie kolejki utraconych wiadomości systemowe: transakcyjnej kolejki utraconych wiadomości całego systemu, który przechowuje komunikaty, których nie powiodła się dostarczania transakcyjne kolejki i nietransakcyjnej kolejki utraconych wiadomości całego systemu, która przechowuje komunikaty, których nie powiodła się dostawy do kolejki nietransakcyjnej. Jeśli dwóch klientów są wysyłanie komunikatów do dwóch różnych usług i w związku z tym różnych kolejek w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] korzystają z tej samej usługi MSMQ do wysłania, a następnie można mieć kombinację wiadomości w kolejce wiadomości utraconych systemu. Nie zawsze jest optymalna. W niektórych przypadkach (np. zabezpieczeń) nie może być jednego klienta, aby odczytać innego klienta wiadomości z kolejki utraconych wiadomości. Udostępnione kolejki utraconych wiadomości wymaga także klientów przeglądać kolejki znalezienie wiadomości, które są wysyłane, może być zbyt duży na podstawie liczby wiadomości w kolejce wiadomości utraconych. W związku z tym w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `NetMsmqBinding`, `MsmqIntegrationBinding,` i usługi MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)] Podaj niestandardowej kolejki utraconych wiadomości (nazywane czasami kolejki utraconych wiadomości specyficzne dla aplikacji).  
  
 Niestandardowej kolejki utraconych wiadomości zapewnia izolację między klientami, które mają tej samej usługi MSMQ do wysyłania wiadomości.  
  
 Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wxp](../../../../includes/wxp-md.md)], [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] udostępnia systemowe kolejki utraconych wiadomości dla wszystkich aplikacji klienckich w kolejce. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zapewnia kolejki utraconych wiadomości dla każdej aplikacji klienta umieszczonych w kolejce.  
  
## <a name="specifying-use-of-the-dead-letter-queue"></a>Określanie Użyj kolejki utraconych wiadomości  
 Kolejki utraconych wiadomości jest do menedżera kolejki aplikację wysyłającą. Przechowuje komunikaty wygasłe, lub które nie przeszły przesłanie bądź dostarczenie.  
  
 Powiązanie ma następujące właściwości kolejki utraconych wiadomości:  
  
-   <xref:System.ServiceModel.MsmqBindingBase.DeadLetterQueue%2A>  
  
-   <xref:System.ServiceModel.MsmqBindingBase.CustomDeadLetterQueue%2A>  
  
## <a name="reading-messages-from-the-dead-letter-queue"></a>Odczytywanie wiadomości z kolejki utraconych wiadomości  
 Aplikacja, która odczytuje wiadomości z kolejki utraconych wiadomości jest podobny do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, która odczytuje z kolejki aplikacji, z wyjątkiem następujących niewielkie różnice:  
  
-   Aby odczytać wiadomości z kolejki utraconych wiadomości transakcyjnych systemu, jednolity identyfikator zasobów (URI) musi mieć postać: net.msmq://localhost/system$; DeadXact.  
  
-   Aby odczytać wiadomości z kolejki utraconych wiadomości nietransakcyjnej systemu, identyfikator URI musi być w formie: net.msmq://localhost/system$; utraconych wiadomości.  
  
-   Aby odczytać wiadomości z niestandardowej kolejki utraconych wiadomości, identyfikator URI musi być formularza: net.msmq://localhost/private/\<*niestandardowy dlq nazwy*> gdzie *niestandardowy dlq nazwy* jest nazwą niestandardowego Kolejka utraconych wiadomości.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]jak adresów kolejek, zobacz [punkty końcowe usługi i adresowanie kolejki](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md).  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Stosu adresów dopasowań odbiornika, które nasłuchuje usługa z adresem w komunikacie. Jeśli adresy są zgodne, jest wysyłany komunikat; Jeśli nie, nie jest wysyłany komunikat. Może to spowodować problemy podczas czytania z kolejki utraconych wiadomości, ponieważ wiadomości w kolejce wiadomości utraconych zwykle są wysyłane do usługi i nie usługi kolejki utraconych wiadomości. W związku z tym usługa czytania z kolejki utraconych wiadomości, należy zainstalować filtr adresów `ServiceBehavior` który powoduje, że stos, aby dopasować wszystkich wiadomości w kolejce niezależnie od adresata. W szczególności należy dodać `ServiceBehavior` z <xref:System.ServiceModel.AddressFilterMode.Any> parametru do odczytywania wiadomości z kolejki utraconych wiadomości usługi.  
  
## <a name="poison-message-handling-from-the-dead-letter-queue"></a>Obsługa z kolejki utraconych komunikatów zanieczyszczonych  
 Trująca wiadomość została obsługa jest dostępna na kolejki utraconych wiadomości, w niektórych warunkach. Ponieważ nie można utworzyć kolejki podrzędne z kolejek systemu podczas czytania z kolejki utraconych wiadomości systemu `ReceiveErrorHandling` nie można ustawić `Move`. Należy pamiętać, że podczas czytania z niestandardowej kolejki utraconych wiadomości, może mieć podrzędnej kolejki i w związku z tym `Move` jest prawidłowy dyspozycji skażone wiadomości.  
  
 Gdy `ReceiveErrorHandling` ma ustawioną wartość `Reject`podczas czytania z kolejki utraconych komunikatów Trująca wiadomość jest umieszczana w kolejce wiadomości utraconych systemu. Jeśli czytania z kolejki utraconych wiadomości systemu, komunikat zostanie usunięte (usunięty). Odrzuć z kolejki utraconych wiadomości systemu w porzucania MSMQ (Przeczyszcza) wiadomości.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia kolejki utraconych wiadomości i jak z niego korzystać do przetwarzania komunikatów wygasła. Przykład jest oparty na przykład w [porady: wymiany wiadomości w kolejce z punktami końcowymi WCF](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md). Poniższy przykład pokazuje, jak napisać kod klienta kolejność przetwarzania usługę korzystającą z kolejki utraconych wiadomości dla każdej aplikacji. W przykładzie przedstawiono również sposób do przetwarzania komunikatów z kolejki utraconych wiadomości.  
  
 Poniżej znajduje się kod dla klienta, który określa kolejki utraconych wiadomości dla każdej aplikacji.  
  
 [!code-csharp[S_DeadLetter#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/client.cs#1)]
 [!code-vb[S_DeadLetter#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/client.vb#1)]  
  
 Poniżej znajduje się kod do pliku konfiguracji klienta.  
  
  
  
 Poniżej znajduje się kod usługi, przetwarzanie wiadomości z kolejki utraconych wiadomości.  
  
 [!code-csharp[S_DeadLetter#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_deadletter/cs/dlservice.cs#3)]
 [!code-vb[S_DeadLetter#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_deadletter/vb/dlservice.vb#3)]  
  
 Poniżej znajduje się kod do pliku konfiguracji usługi kolejki utraconych wiadomości.  
  
  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie kolejek](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [Porady: wymiana komunikatów z punktami końcowymi WCF umieszczonych w kolejce](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 [Obsługa komunikatów zanieczyszczonych](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)