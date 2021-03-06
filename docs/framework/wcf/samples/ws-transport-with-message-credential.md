---
title: "Transport WS z poświadczeniami komunikatu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d092f3a-b309-439b-920b-66d8f46a0e3c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f782ac12c92755eb26eddd30c5d8c15168c35858
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ws-transport-with-message-credential"></a>Transport WS z poświadczeniami komunikatu
W przykładzie pokazano użycie zabezpieczenia transportowe protokołu SSL w połączeniu z poświadczeniami klienta odbywa się w komunikacie. W przykładzie użyto `wsHttpBinding` powiązania.  
  
 Domyślnie `wsHttpBinding` powiązania zapewnia komunikację HTTP. Gdy skonfigurowany pod kątem zabezpieczeń transportu, wiązanie obsługuje komunikację HTTPS. Protokół HTTPS oferuje poufności i ochrony integralność komunikatów, które są przesyłane przez sieć. Jednakże zestaw mechanizmów uwierzytelniania, które mogą służyć do uwierzytelniania klienta do usługi jest ograniczone do obsługuje transportu HTTPS. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]oferuje `TransportWithMessageCredential` tryb zabezpieczeń, której celem jest obejść to ograniczenie. Po skonfigurowaniu tego trybu zabezpieczeń transportu używane zabezpieczenia zapewnienie poufności i integralności wiadomości przesyłane i do uwierzytelniania usługi. Jednak uwierzytelnianie klienta jest wykonywane przez wprowadzenie poświadczeń klienta bezpośrednio w komunikacie. Dzięki temu można użyć dowolnego typu poświadczeń, która jest obsługiwana przez tryb zabezpieczeń wiadomości do uwierzytelniania klientów przy zachowaniu wydajności zaletą tryb zabezpieczeń transport.  
  
 W tym przykładzie `UserName` typ poświadczeń jest używany do uwierzytelniania klienta do usługi.  
  
 Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator. `wsHttpBinding` Powiązania jest określona i skonfigurowany w plikach konfiguracji aplikacji dla klienta i usługi.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Kod programu w próbce jest niemal identyczna ze [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) usługi. Brak jednej operacji dodatkowe podał kontraktu usługi - `GetCallerIdentity`. Ta operacja zwraca nazwę tożsamości obiektu wywołującego do obiektu wywołującego.  
  
```  
public string GetCallerIdentity()  
{  
    // Use ServiceSecurityContext.WindowsIdentity to get the name of the caller.  
    return ServiceSecurityContext.Current.WindowsIdentity.Name;  
}  
```  
  
 Należy utworzyć certyfikat i przypisz go za pomocą kreatora certyfikatu serwera sieci Web przed tworzenia i uruchamiania przykładowych. Definicja punktu końcowego i definicji powiązania w konfiguracji pliku ustawienia umożliwiające `TransportWithMessageCredential` tryb zabezpieczeń, jak pokazano w poniższych Przykładowa konfiguracja klienta.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint name=""  
              address="https://localhost/servicemodelsamples/service.svc"   
              binding="wsHttpBinding"   
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
        This configuration defines the security mode as TransportWithMessageCredential.  
        and the clientCredentialType as UserName.  
        -->  
      <binding name="Binding1">  
        <security mode ="TransportWithMessageCredential">  
          <message clientCredentialType="UserName" />  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Określony adres wykorzystuje schemat https://. Konfiguracja powiązania Ustawia tryb zabezpieczeń `TransportWithMessageCredential`. Należy określić ten sam tryb zabezpieczeń w pliku Web.config tej usługi.  
  
 Ponieważ certyfikat użyty w tym przykładzie jest certyfikatu testowego utworzone za pomocą Makecert.exe, alert zabezpieczeń zostanie wyświetlony podczas próby uzyskania dostępu https: adres, takie jak https://localhost/servicemodelsamples/service.svc z przeglądarki. Aby umożliwić [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, aby pracować przy użyciu certyfikatu testowego w miejscu, dodatkowy kod został dodany do klienta dla pomijania alertu zabezpieczeń. Ten kod i towarzyszące klasy nie jest wymagana, podczas korzystania z certyfikatów w środowisku produkcyjnym.  
  
```  
// WARNING: This code is only needed for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Username authentication required.  
Provide a valid machine or domain account. [domain\\user]  
   Enter username:   
YourDomainName\YourAccountName  
   Enter password:   
********  
YourDomainName\YourAccountName  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Upewnij się, że wykonano procedurę [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).  
  
3.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też
