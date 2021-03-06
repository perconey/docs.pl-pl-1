---
title: "Instrukcje: Tworzenie kontraktu „żądanie-odpowiedź”"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f86679d38b8d1a1d6443c1aac37cfa75f426e402
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-request-reply-contract"></a>Instrukcje: Tworzenie kontraktu „żądanie-odpowiedź”
Kontraktu "żądanie-odpowiedź" Określa metodę, która zwraca odpowiedź. Odpowiedź musi być wysyłane i skorelowane żądanie na mocy niniejszej Umowy. Nawet wtedy, gdy metoda nie zwraca żadnej odpowiedzi (`void` w języku C# lub `Sub` w języku Visual Basic), infrastruktury tworzy i wysyła komunikat pusty do obiektu wywołującego. Aby uniemożliwić wysyłanie komunikatu odpowiedzi pusty, należy użyć kontraktu jednokierunkowego dla tej operacji.  
  
### <a name="to-create-a-request-reply-contract"></a>Aby utworzyć kontraktu "żądanie-odpowiedź"  
  
1.  Tworzenie interfejsu w języku programowania wybranych przez użytkownika.  
  
2.  Zastosuj <xref:System.ServiceModel.ServiceContractAttribute> do interfejsu.  
  
3.  Zastosuj <xref:System.ServiceModel.OperationContractAttribute> atrybutu do każdej metody, które może wywołać klientów.  
  
4.  Opcjonalny. Ustaw wartość <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości `true` aby uniemożliwić wysyłanie komunikatu odpowiedzi pusty. Domyślnie wszystkie operacje są kontraktów "żądanie-odpowiedź".  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje kontrakt dla usługi Kalkulator, która zapewnia `Add` i `Subtract` metody. `Multiply` — Metoda nie jest częścią kontraktu, ponieważ nie zostało oznaczone przez <xref:System.ServiceModel.OperationContractAttribute> klasy i dlatego nie jest dostępna dla klientów.  
  
```
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);
    
    [OperationContract]
    int Subtract(int a, int b);
    
    int Multiply(int a, int b)
}
```
  
-   [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Określ kontrakty operacji, zobacz <xref:System.ServiceModel.OperationContractAttribute> klasy i <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> właściwości.  
  
-   Stosowanie <xref:System.ServiceModel.ServiceContractAttribute> i <xref:System.ServiceModel.OperationContractAttribute> atrybuty powoduje automatyczne generowanie definicje kontraktu usługi w dokumencie Web Services Description Language (WSDL), po wdrożeniu usługi. Dokument jest pobierana przez dołączenie `?wsdl` HTTP podstawowy adres usługi. Na przykład:`http://microsoft/CalculatorService?wsdl`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Instrukcje: tworzenie kontraktu dwukierunkowego](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
