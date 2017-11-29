---
title: "Dodawanie odwołania usługi w projekcie obsługującym podzestaw przenośny"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ccfe0f-a34b-40ca-8f5e-725fa1b8095e
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d7bd456b8c89c315321ad23683708d9dacc1dda2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="add-service-reference-in-a-portable-subset-project"></a>Dodawanie odwołania usługi w projekcie obsługującym podzestaw przenośny
Projekty obsługującym podzestaw przenośny umożliwiają programistom zestawu .NET Obsługa drzewa jednego źródła i kompilacji systemu nadal obsługuje wiele implementacji .NET (pulpitu, Silverlight, Windows Phone i XBOX). Projekty obsługującym podzestaw przenośny odwoływać się tylko przenośnych bibliotek .NET, które są zestawem .NET framework, używanym w implementacji .NET.  
  
## <a name="add-service-reference-details"></a>Dodaj szczegóły usługi  
 Podczas dodawania odwołania do usługi w projekcie obsługującym podzestaw przenośny są wymuszane następujące ograniczenia:  
  
1.  Aby uzyskać <xref:System.Xml.Serialization.XmlSerializer>, dozwolone są tylko kodowania literału. Kodowania SOAP Generowanie wystąpił błąd podczas importowania.  
  
2.  Dla usługi używające <xref:System.Runtime.Serialization.DataContractSerializer> scenariuszy, danych zastępcza Umowa jest dostarczany w celu upewnij się, że ponownie typów pochodzą tylko z obsługującym podzestaw przenośny.  
  
3.  Punkty końcowe, które są zależne od powiązania nie jest obsługiwany w przenośnych bibliotek (wszystkie powiązania z wyjątkiem <xref:System.ServiceModel.BasicHttpBinding>, <xref:System.ServiceModel.WSHttpBinding> bez przepływu transakcji, niezawodnej sesji lub kodowanie MTOM i równoważne powiązań niestandardowych), są ignorowane.  
  
4.  Nagłówki komunikatów są usuwane z wszystkie opisy wiadomości we wszystkich operacjach przed rozpoczęciem importowania.  
  
5.  Atrybuty nieprzenośne <xref:System.ComponentModel.DesignerCategoryAttribute>, <xref:System.SerializableAttribute>, i <xref:System.ServiceModel.TransactionFlowAttribute> są usuwane z kodu serwera proxy wygenerowanego klienta.  
  
6.  Nieprzenośne właściwości ProtectionLevel, SessionMode, IsInitiating i IsTerminating są usuwane z <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, i <xref:System.ServiceModel.FaultContractAttribute>.  
  
7.  Wszystkie operacje usług są generowane jako asynchroniczne operacje na serwerze proxy klienta.  
  
8.  Konstruktor wygenerowanego klienta, który używa nieprzenośne typy są usuwane.  
  
9. A <xref:System.Net.CookieContainer> wystąpienia jest narażony na wygenerowanego klienta.  
  
10. Komentarz dodaje się u góry pliku zestawu i wersji generatora kodu.`// This code was auto-generated by Microsoft.VisualStudio.Portable.AddServiceReference, version 1.0.0.0`  
  
11. <xref:System.Runtime.Serialization.ISerializable> Interfejs nie jest obsługiwany.  
  
12. Powiązania Net.Tcp i PollingDuplex nie są obsługiwane.  
  
13. <xref:System.Runtime.Serialization.DataContractSerializer> Będzie zawsze używana dla błędów.  
  
14. <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A>nie jest obsługiwana w projektach obsługującym podzestaw przenośny.  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do usług za pomocą klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [Biblioteka klas przenośnych](http://msdn.microsoft.com/library/gg597391\(v=vs.110\))