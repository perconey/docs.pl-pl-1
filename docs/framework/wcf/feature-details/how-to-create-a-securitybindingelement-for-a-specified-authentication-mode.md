---
title: "Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania"
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
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 29cbe3c10ac68d508dc22781e46a6041f2d7eab7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Instrukcje: Tworzenie elementu SecurityBindingElement dla określonego trybu uwierzytelniania
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]udostępnia kilka metod za pomocą których klienci usług uwierzytelniać się na siebie. Można utworzyć zabezpieczeń elementy powiązania dla tych trybach uwierzytelniania przy użyciu metod statycznych na <xref:System.ServiceModel.Channels.SecurityBindingElement> klasy lub przy użyciu konfiguracji, jak pokazano w poniższym przykładzie.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tryby uwierzytelniania 18, zobacz [tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje metody tworzenia powiązań dla różnych metod uwierzytelniania.  
  
> [!NOTE]
>  Raz wystąpienia <xref:System.ServiceModel.Channels.SecurityBindingElement> obiekt jest tworzony, wiele właściwości są niezmienne, takich jak <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> i <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>. Wywoływanie `set` takich właściwości nie je zmienić.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Zobacz też  
 [Tryby uwierzytelniania elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [Instrukcje: tworzenie niestandardowego powiązania za pomocą elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
