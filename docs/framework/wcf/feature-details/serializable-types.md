---
title: "Typy z możliwością serializowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4e368472db3bdca73661586821106174e13d4d24
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="serializable-types"></a><span data-ttu-id="2c048-102">Typy z możliwością serializowania</span><span class="sxs-lookup"><span data-stu-id="2c048-102">Serializable Types</span></span>
<span data-ttu-id="2c048-103">Domyślnie <xref:System.Runtime.Serialization.DataContractSerializer> serializuje wszystkich typów publicznie widoczna.</span><span class="sxs-lookup"><span data-stu-id="2c048-103">By default, the <xref:System.Runtime.Serialization.DataContractSerializer> serializes all publicly visible types.</span></span> <span data-ttu-id="2c048-104">Wszystkie właściwości publiczne odczytu/zapisu i pól typu są serializowane.</span><span class="sxs-lookup"><span data-stu-id="2c048-104">All public read/write properties and fields of the type are serialized.</span></span>  
  
 <span data-ttu-id="2c048-105">Domyślne zachowanie można zmienić, stosując <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty dla typów i członków tej funkcji mogą być przydatne w sytuacjach, w których mają typy, które nie są pod kontrolą i nie można zmodyfikować, aby dodać atrybuty.</span><span class="sxs-lookup"><span data-stu-id="2c048-105">You can change the default behavior by applying the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to the types and members This feature can be useful in situations in which you have types that are not under your control and cannot be modified to add attributes.</span></span> <span data-ttu-id="2c048-106"><xref:System.Runtime.Serialization.DataContractSerializer> Rozpoznaje takie typy "nieoznaczone".</span><span class="sxs-lookup"><span data-stu-id="2c048-106">The <xref:System.Runtime.Serialization.DataContractSerializer> recognizes such "unmarked" types.</span></span>  
  
## <a name="serialization-defaults"></a><span data-ttu-id="2c048-107">Ustawienia domyślne serializacji</span><span class="sxs-lookup"><span data-stu-id="2c048-107">Serialization Defaults</span></span>  
 <span data-ttu-id="2c048-108">Możesz zastosować <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> atrybuty jawnie kontrolować lub dostosowanie serializacji typów i członków.</span><span class="sxs-lookup"><span data-stu-id="2c048-108">You can apply the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes to explicitly control or customize the serialization of types and members.</span></span> <span data-ttu-id="2c048-109">Ponadto można stosować te atrybuty do pól prywatnych.</span><span class="sxs-lookup"><span data-stu-id="2c048-109">In addition, you can apply these attributes to private fields.</span></span> <span data-ttu-id="2c048-110">Jednak nawet typy, które nie są oznaczone ikoną z tych atrybutów są serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="2c048-110">However, even types that are not marked with these attributes are serialized and deserialized.</span></span> <span data-ttu-id="2c048-111">Zastosuj poniższe reguły i wyjątków:</span><span class="sxs-lookup"><span data-stu-id="2c048-111">The following rules and exceptions apply:</span></span>  
  
-   <span data-ttu-id="2c048-112"><xref:System.Runtime.Serialization.DataContractSerializer> Wnioskuje bez atrybutów przy użyciu domyślnych właściwości nowo utworzone typy z typów kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="2c048-112">The <xref:System.Runtime.Serialization.DataContractSerializer> infers a data contract from types without attributes using the default properties of the newly created types.</span></span>  
  
-   <span data-ttu-id="2c048-113">Wszystkie publiczne pola i właściwości z publicznych `get` i `set` metody są serializowane, jeśli nie zostanie zastosowana <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atrybutu do tego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="2c048-113">All public fields, and properties with public `get` and `set` methods are serialized, unless you apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
-   <span data-ttu-id="2c048-114">Semantyka podobne do serializacji <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2c048-114">The serialization semantics are similar to those of the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
-   <span data-ttu-id="2c048-115">Nieoznaczone typy serializacji są tylko typy publiczne z konstruktorów bez parametrów.</span><span class="sxs-lookup"><span data-stu-id="2c048-115">In unmarked types, only public types with constructors that do not have parameters are serialized.</span></span> <span data-ttu-id="2c048-116">Wyjątkiem od tej reguły jest <xref:System.Runtime.Serialization.ExtensionDataObject> używane z <xref:System.Runtime.Serialization.IExtensibleDataObject> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2c048-116">The exception to this rule is <xref:System.Runtime.Serialization.ExtensionDataObject> used with the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface.</span></span>  
  
-   <span data-ttu-id="2c048-117">Pola tylko do odczytu, właściwości bez `get` lub `set` metody i właściwości z wewnętrznego lub prywatnego `set` lub `get` metod nie są serializowane.</span><span class="sxs-lookup"><span data-stu-id="2c048-117">Read-only fields, properties without a `get` or `set` method, and properties with internal or private `set` or `get` methods are not serialized.</span></span> <span data-ttu-id="2c048-118">Tych właściwości są ignorowane, a nie wyjątek, chyba że w przypadku kolekcji tylko do pobrania.</span><span class="sxs-lookup"><span data-stu-id="2c048-118">Such properties are ignored and no exception is thrown, except in the case of get-only collections.</span></span>  
  
-   <span data-ttu-id="2c048-119"><xref:System.Xml.Serialization.XmlSerializer>atrybuty (takich jak `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`i tak dalej), są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="2c048-119"><xref:System.Xml.Serialization.XmlSerializer> attributes (such as `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, and so on) are ignored.</span></span>  
  
-   <span data-ttu-id="2c048-120">Jeśli nie mają zastosowania <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do danego typu serializatora ignoruje członków w danym typie, do którego <xref:System.Runtime.Serialization.DataMemberAttribute> atrybut jest stosowany.</span><span class="sxs-lookup"><span data-stu-id="2c048-120">If you do not apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a given type, the serializer ignores any member in that type to which the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute is applied.</span></span>  
  
-   <span data-ttu-id="2c048-121"><xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> Właściwość jest obsługiwana w typach nie oznaczony atrybutem <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2c048-121">The <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> property is supported in types not marked with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute.</span></span> <span data-ttu-id="2c048-122">Obejmuje to obsługę <xref:System.Runtime.Serialization.KnownTypeAttribute> atrybutu nieoznaczone typy.</span><span class="sxs-lookup"><span data-stu-id="2c048-122">This includes support for the <xref:System.Runtime.Serialization.KnownTypeAttribute> attribute on unmarked types.</span></span>  
  
-   <span data-ttu-id="2c048-123">"Wykluczyć" procesu serializacji dla publicznych elementów członkowskich, właściwości lub pól, zastosuj <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atrybutu do tego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="2c048-123">To "opt out" of the serialization process for public members, properties, or fields, apply the <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> attribute to that member.</span></span>  
  
## <a name="inheritance"></a><span data-ttu-id="2c048-124">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="2c048-124">Inheritance</span></span>  
 <span data-ttu-id="2c048-125">Nieoznaczone typy (typy bez <xref:System.Runtime.Serialization.DataContractAttribute> atrybut) może dziedziczyć z typów, które mają atrybut; jednak odwrotnej nie jest dozwolona: typy z atrybutem nie może dziedziczyć po nieoznaczone typy.</span><span class="sxs-lookup"><span data-stu-id="2c048-125">Unmarked types (types without the <xref:System.Runtime.Serialization.DataContractAttribute> attribute) can inherit from types that do have this attribute; however, the reverse is not permitted: types with the attribute cannot inherit from unmarked types.</span></span> <span data-ttu-id="2c048-126">Ta reguła jest wymuszone głównie w celu zapewnienia zgodności z poprzednimi wersjami z kod napisany w starszych wersjach [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2c048-126">This rule is enforced primarily to ensure backward compatibility with code written in earlier versions of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c048-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c048-127">See Also</span></span>  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="2c048-128">Typy obsługiwane przez serializator kontraktu danych</span><span class="sxs-lookup"><span data-stu-id="2c048-128">Types Supported by the Data Contract Serializer</span></span>](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)