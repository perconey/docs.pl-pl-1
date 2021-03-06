---
title: "Zręczność kryptograficzna w zabezpieczeniach WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 7d99ada67255d0ced8bbabc2ab6fc645e6ba9e35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cryptographic-agility-in-wcf-security"></a>Zręczność kryptograficzna w zabezpieczeniach WCF
W tym przykładzie pokazano, jak określić w algorytmie standard/niestandardowe do implementacji agile kryptograficznych w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta i usługi. Próbka składa się z następujących projektów:  
  
 Usługa  
 To jest hostowany na własnym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa, która implementuje `ICalculator` interfejsu i zabezpiecza punktu końcowego za pomocą <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> z bezpiecznej sesji i niezawodnej sesji wyłączone. Usługa definiuje niestandardowego `SecurityAlgorithmSuite` klasę, aby określić algorytmów kryptograficznych używanego do zabezpieczenia komunikatów.  
  
 Klient  
 Jest to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]klienta, który uzyskuje dostęp do usługi, po pomyślnym uwierzytelnieniu. Wywołuje operacji udostępnianych przez `ICalculator` interfejsu i zaimplementowanych przez usługę. Klient również definiuje niestandardowe tej samej `SecurityAlgorithmSuite` klasę, aby określić algorytmów kryptograficznych używanego do zabezpieczenia komunikatów.  
  
### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Otwórz rozwiązanie CryptoAgility.sln w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
3.  Otwórz [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] i przejdź do katalogu \WCF\Basic\Security\CryptoAgility\Service\bin i uruchom plik service.exe z uprawnieniami administratora, klikając prawym przyciskiem myszy service.exe i wybierając **Uruchom jako administrator**.  
  
4.  Przejdź do katalogu \WCF\Basic\Security\CryptoAgility\Client\bin i uruchom plik client.exe normalnie.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)
