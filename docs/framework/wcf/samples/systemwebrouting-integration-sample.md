---
title: "Przykład integracji elementu SystemWebRouting"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: de8869956a59cb47623dbc4d84763e19d6f181bf
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="systemwebrouting-integration-sample"></a>Przykład integracji elementu SystemWebRouting
W tym przykładzie pokazano integracji hostingu warstwy z klas w <xref:System.Web.Routing> przestrzeni nazw. Klasy w <xref:System.Web.Routing> przestrzeni nazw Zezwalaj aplikacji na używanie adresów URL, które nie odpowiadają bezpośrednio zasób fizyczny. Przy użyciu routingu w sieci Web umożliwia deweloperom tworzenie wirtualnych adresów dla protokołu HTTP, które następnie są mapowane do rzeczywistego [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług. Jest to przydatne, gdy usługa WCF musi być obsługiwana bez konieczności fizycznej plik lub zasób, lub gdy usług muszą być dostępne z adresami URL, które nie zawierają plików, takich jak HTML lub aspx. W tym przykładzie pokazano, jak korzystać z <xref:System.Web.Routing.RouteTable> klasy w celu utworzenia wirtualnego identyfikatorów URI mapowane na uruchamianie usług zdefiniowane w pliku global.asax. 

> [!NOTE]
>  Klasy w <xref:System.Web.Routing> przestrzeni nazw jest prawidłowe tylko dla usługi hostowanej za pośrednictwem protokołu HTTP.  
  
W tym przykładzie użyto WCF do utworzenia dwóch źródeł danych RSS: `movies` źródła danych i `channels` źródła danych. Adresy URL do aktywowania usługi nie zawiera rozszerzenia i są rejestrowane w `Application_Start` metody `Global` klasą pochodną <xref:System.Web.HttpApplication> klasy.  
  
> [!NOTE]
>  W tym przykładzie działa tylko w Internet informacji Services (IIS) 7.0 i nowszy, jako usług IIS 6.0 używa innej metody do obsługi adresów URL bez rozszerzeń.  

#### <a name="to-download-this-sample"></a>Aby pobrać ten przykład
  
W tym przykładzie może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu programu Visual Studio, otwórz plik WebRoutingIntegration.sln.  
  
2.  Aby uruchomić rozwiązanie i uruchomić serwera wdrożeniowego sieci Web, naciśnij klawisz F5.  
  
     Zostanie wyświetlone listę przykładowej katalogów. Należy pamiętać, że nie ma żadnych plików z rozszerzeniem nazwy pliku svc.  
  
3.  Na pasku adresu dodać `movies` więc do adresu URL, którego nie odczytuje http://localhost: [portu] / filmy i naciśnij klawisz ENTER.  
  
     Źródła strumieniowego filmów zostanie wyświetlona w przeglądarce.  
  
4.  Na pasku adresu dodać `channels` do adresu URL, więc to odczyty http://localhost: [portu] / kanałów i naciśnij klawisz ENTER.  
  
     Źródło strumieniowe kanały zostanie wyświetlona w przeglądarce.  
  
5.  Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.  
  
     Jeśli nie zakończył serwera wdrożeniowego programu, kliknij prawym przyciskiem myszy ikonę w obszarze powiadomień i wybierz **zatrzymać**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Aby użyć tego przykładu, podczas udostępniania w usługach IIS  
  
1.  Przy użyciu programu Visual Studio, otwórz plik WebRoutingIntegration.sln.  
  
2.  Skompiluj projekt, naciskając klawisze CTRL + SHIFT + B.  
  
3.  Utwórz aplikację sieci Web w programie Internet Information Services (IIS) Manager.  
  
    1.  W Menedżerze usług IIS kliknij prawym przyciskiem myszy **domyślna witryna sieci Web** i wybierz **Dodawanie aplikacji**.  
  
    2.  Aby uzyskać **alias**, wpisz w `WebRoutingIntegration`.  
  
    3.  Aby uzyskać **ścieżka fizyczna**, wybierz folder usługi wewnątrz projektu.  
  
    4.  Press **OK**.  
  
4.  Uruchom aplikację, klikając prawym przyciskiem myszy aplikację sieci Web i wybierając polecenie **aplikacji Zarządzanie** , a następnie **Przeglądaj**.  
  
5.  Na pasku adresu dodać `movies` do adresu URL, więc to odczyty http://localhost: [portu] / filmy i naciśnij klawisz ENTER.  
  
     Źródła strumieniowego filmów zostanie wyświetlona w przeglądarce.  
  
6.  Na pasku adresu dodać `channels` do adresu URL, więc to odczyty http://localhost: [portu] / kanałów i naciśnij klawisz ENTER.  
  
     Źródło strumieniowe kanały zostanie wyświetlona w przeglądarce.  
  
7.  Zamknij przeglądarkę sieci Web, naciskając klawisze ALT + F4.  
  
 W przykładzie pokazano warstwy obsługi jest w stanie składających się z klas w <xref:System.Web.Routing> przestrzeń nazw dla routingu żądań usług hostowanych za pośrednictwem protokołu HTTP.  
  
> [!NOTE]
>  Należy zaktualizować domyślnej wersji puli aplikacji do [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] Jeśli ustawiono w wersji 2.  
  
## <a name="see-also"></a>Zobacz też  
 [Przykłady trwałości i hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
