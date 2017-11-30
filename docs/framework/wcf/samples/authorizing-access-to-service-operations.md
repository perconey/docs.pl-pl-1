---
title: "Autoryzowanie dostępu do operacji usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cfa1eefa9f7bd940baf3796d92ac7b49e0f9843e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="authorizing-access-to-service-operations"></a>Autoryzowanie dostępu do operacji usługi
W tym przykładzie przedstawiono sposób użycia [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) umożliwia korzystanie z <xref:System.Security.Permissions.PrincipalPermissionAttribute> atrybut do autoryzowania dostępu do operacji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) próbki. Usługa i klient skonfigurowanych za pomocą [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `mode` Atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) została ustawiona jako `Message` i `clientCredentialType` została ustawiona jako `Windows`. <xref:System.Security.Permissions.PrincipalPermissionAttribute> Jest stosowane do każdej metody usługi i używany do ograniczania dostępu do każdej operacji. Obiekt wywołujący musi być kontem administratora systemu Windows można uzyskać dostępu do każdej operacji.  
  
 W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Plik konfiguracji usługi używa [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) można ustawić `principalPermissionMode` atrybutu:  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>   
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Ustawienie `principalPermissionMode` do `UseWindowsGroups` umożliwia korzystanie z <xref:System.Security.Permissions.PrincipalPermissionAttribute> na podstawie nazw grupy systemu Windows.  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Jest stosowany do każdej operacji wymagające wywołującego należeć do grupy Administratorzy systemu Windows, jak pokazano w poniższym kodzie próbki.  
  
```  
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Klient pomyślnie komunikuje się z każdej operacji Jeśli została uruchomiona przy użyciu konta należącego do grupy Administratorzy; w przeciwnym razie nastąpi odmowa dostępu. Eksperymentować błąd autoryzacji, uruchom klienta przy użyciu konta, które nie należą do grupy Administratorzy. Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta.  
  
 Usługa może być powiadamiany o błędami autoryzacji zaimplementowanie <xref:System.ServiceModel.Dispatcher.IErrorHandler>. Zobacz [rozszerzanie kontroli nad błąd obsługi i raportowania](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) informacji o implementacji `IErrorHandler`.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też