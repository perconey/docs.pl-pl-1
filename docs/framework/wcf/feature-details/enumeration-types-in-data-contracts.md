---
title: Typy wyliczeniowe w kontraktach danych
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
helpviewer_keywords: data contracts [WCF], enumeration types
ms.assetid: b5d694da-68cb-4b74-a5fb-75108a68ec3b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 13b3d19c8e71d7bd6a37362b1ac1b5e23e8ff24a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="enumeration-types-in-data-contracts"></a><span data-ttu-id="647ea-102">Typy wyliczeniowe w kontraktach danych</span><span class="sxs-lookup"><span data-stu-id="647ea-102">Enumeration Types in Data Contracts</span></span>
<span data-ttu-id="647ea-103">Wyliczenia mogą być wyrażone w modelu kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="647ea-103">Enumerations can be expressed in the data contract model.</span></span> <span data-ttu-id="647ea-104">W tym temacie przedstawiono kilka przykładów objaśniające modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="647ea-104">This topic walks through several examples that explain the programming model.</span></span>  
  
## <a name="enumeration-basics"></a><span data-ttu-id="647ea-105">Podstawy — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="647ea-105">Enumeration Basics</span></span>  
 <span data-ttu-id="647ea-106">Sposób użycia Typy wyliczeniowe w modelu kontraktu danych ma zastosowanie <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu typu.</span><span class="sxs-lookup"><span data-stu-id="647ea-106">One way to use enumeration types in the data contract model is to apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type.</span></span> <span data-ttu-id="647ea-107">Następnie należy zastosować <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu do każdego elementu członkowskiego, który musi być uwzględniona w kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="647ea-107">You must then apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to each member that must be included in the data contract.</span></span>  
  
 <span data-ttu-id="647ea-108">W poniższym przykładzie przedstawiono dwie klasy.</span><span class="sxs-lookup"><span data-stu-id="647ea-108">The following example shows two classes.</span></span> <span data-ttu-id="647ea-109">Wyliczenia używa pierwszego i drugiego definiuje wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="647ea-109">The first uses the enumeration and the second defines the enumeration.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#1)]
 [!code-vb[c_DataContractEnumerations#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#1)]  
  
 <span data-ttu-id="647ea-110">Wystąpienie `Car` klasy, które mogą być wysyłane lub odbierane tylko wtedy, gdy `condition` pole jest ustawione na jedną z wartości `New`, `Used`, lub `Rental`.</span><span class="sxs-lookup"><span data-stu-id="647ea-110">An instance of the `Car` class can be sent or received only if the `condition` field is set to one of the values `New`, `Used`, or `Rental`.</span></span> <span data-ttu-id="647ea-111">Jeśli `condition` jest `Broken` lub `Stolen`, <xref:System.Runtime.Serialization.SerializationException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="647ea-111">If the `condition` is `Broken` or `Stolen`, a <xref:System.Runtime.Serialization.SerializationException> is thrown.</span></span>  
  
 <span data-ttu-id="647ea-112">Można użyć <xref:System.Runtime.Serialization.DataContractAttribute> właściwości (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> i <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) dla kontraktów danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="647ea-112">You can use the <xref:System.Runtime.Serialization.DataContractAttribute> properties (<xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> and <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>) as usual for enumeration data contracts.</span></span>  
  
### <a name="enumeration-member-values"></a><span data-ttu-id="647ea-113">Wartości elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="647ea-113">Enumeration Member Values</span></span>  
 <span data-ttu-id="647ea-114">Kontrakt danych obejmuje zazwyczaj wyliczenie nazwy elementów członkowskich, nie wartości liczbowe.</span><span class="sxs-lookup"><span data-stu-id="647ea-114">Generally the data contract includes enumeration member names, not numerical values.</span></span> <span data-ttu-id="647ea-115">Jednak jeśli przy użyciu danych kontraktu modelu, jeśli po stronie odbierającej jest [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, wyeksportowanego schematu zachowuje wartości liczbowe.</span><span class="sxs-lookup"><span data-stu-id="647ea-115">However, when using the data contract model, if the receiving side is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client, the exported schema preserves the numerical values.</span></span> <span data-ttu-id="647ea-116">Należy pamiętać, że to nie jest to przy użyciu [przy użyciu klasy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span><span class="sxs-lookup"><span data-stu-id="647ea-116">Note that this is not the case when using the [Using the XmlSerializer Class](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).</span></span>  
  
 <span data-ttu-id="647ea-117">W poprzednim przykładzie Jeśli `condition` ustawiono `Used` i jest serializowany danych do pliku XML, wynikowy kod XML jest `<condition>Used</condition>` i nie `<condition>1</condition>`.</span><span class="sxs-lookup"><span data-stu-id="647ea-117">In the preceding example, if `condition` is set to `Used` and the data is serialized to XML, the resulting XML is `<condition>Used</condition>` and not `<condition>1</condition>`.</span></span> <span data-ttu-id="647ea-118">W związku z tym następujące kontrakt danych jest odpowiednikiem z kontraktem danych `CarConditionEnum`.</span><span class="sxs-lookup"><span data-stu-id="647ea-118">Therefore, the following data contract is equivalent to the data contract of `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#2)]
 [!code-vb[c_DataContractEnumerations#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#2)]  
  
 <span data-ttu-id="647ea-119">Na przykład można użyć `CarConditionEnum` po stronie wysyłającej i `CarConditionWithNumbers` po stronie odbierającej.</span><span class="sxs-lookup"><span data-stu-id="647ea-119">For example, you can use `CarConditionEnum` on the sending side and `CarConditionWithNumbers` on the receiving side.</span></span> <span data-ttu-id="647ea-120">Chociaż po stronie wysyłającej korzysta z wartości "1" dla `Used` i używa po stronie odbierania, wartość "20" reprezentację XML jest `<condition>Used</condition>` po obu stronach.</span><span class="sxs-lookup"><span data-stu-id="647ea-120">Although the sending side uses the value "1" for `Used` and the receiving side uses the value "20," the XML representation is `<condition>Used</condition>` for both sides.</span></span>  
  
 <span data-ttu-id="647ea-121">Do uwzględnienia w kontraktu danych, należy najpierw zastosować <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="647ea-121">To be included in the data contract, you must apply the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="647ea-122">W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], zawsze można zastosować specjalna wartość 0 (zero) do wyliczenia, która jest również wartością domyślną dla dowolnego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="647ea-122">In the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], you can always apply the special value 0 (zero) to an enumeration, which is also the default value for any enumeration.</span></span> <span data-ttu-id="647ea-123">Jednak nawet to specjalne wartości zerowej nie można serializować, chyba że jest on oznaczony <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="647ea-123">However, even this special zero value cannot be serialized unless it is marked with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="647ea-124">Istnieją dwa wyjątki od tej reguły:</span><span class="sxs-lookup"><span data-stu-id="647ea-124">There are two exceptions to this:</span></span>  
  
-   <span data-ttu-id="647ea-125">Flaga wyliczenia (omówione w dalszej części tego tematu).</span><span class="sxs-lookup"><span data-stu-id="647ea-125">Flag enumerations (discussed later in this topic).</span></span>  
  
-   <span data-ttu-id="647ea-126">Elementy członkowskie danych wyliczenia z <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> ustawioną właściwość `false` (w takim przypadku wyliczenie o wartości zero pominięto w danych serializacji).</span><span class="sxs-lookup"><span data-stu-id="647ea-126">Enumeration data members with the <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> property set to `false` (in which case, the enumeration with the value zero is omitted from the serialized data).</span></span>  
  
### <a name="customizing-enumeration-member-values"></a><span data-ttu-id="647ea-127">Dostosowywanie wartości elementu członkowskiego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="647ea-127">Customizing Enumeration Member Values</span></span>  
 <span data-ttu-id="647ea-128">Można dostosować wartość elementu członkowskiego wyliczenia, która jest częścią kontraktu danych przy użyciu <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> właściwość <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="647ea-128">You can customize the enumeration member value that forms a part of the data contract by using the <xref:System.Runtime.Serialization.EnumMemberAttribute.Value%2A> property of the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="647ea-129">Na przykład następujące kontraktu danych również jest odpowiednikiem z kontraktem danych `CarConditionEnum`.</span><span class="sxs-lookup"><span data-stu-id="647ea-129">For example, the following data contract is also equivalent to the data contract of the `CarConditionEnum`.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#3)]
 [!code-vb[c_DataContractEnumerations#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#3)]  
  
 <span data-ttu-id="647ea-130">Podczas serializacji wartości `PreviouslyOwned` jej reprezentacji XML `<condition>Used</condition>`.</span><span class="sxs-lookup"><span data-stu-id="647ea-130">When serialized, the value of `PreviouslyOwned` has the XML representation `<condition>Used</condition>`.</span></span>  
  
## <a name="simple-enumerations"></a><span data-ttu-id="647ea-131">Proste wyliczenia</span><span class="sxs-lookup"><span data-stu-id="647ea-131">Simple Enumerations</span></span>  
 <span data-ttu-id="647ea-132">Można również serializacji typów wyliczenia, do którego <xref:System.Runtime.Serialization.DataContractAttribute> nie zastosowano atrybutu.</span><span class="sxs-lookup"><span data-stu-id="647ea-132">You can also serialize enumeration types to which the <xref:System.Runtime.Serialization.DataContractAttribute> attribute has not been applied.</span></span> <span data-ttu-id="647ea-133">Takie wyliczenie typy są traktowane dokładnie jak opisano wcześniej, z wyjątkiem każdy członek (, która nie ma <xref:System.NonSerializedAttribute> atrybut zastosowany) jest traktowana tak, jakby <xref:System.Runtime.Serialization.EnumMemberAttribute> zastosowano atrybut.</span><span class="sxs-lookup"><span data-stu-id="647ea-133">Such enumeration types are treated exactly as previously described, except that every member (that does not have the <xref:System.NonSerializedAttribute> attribute applied) is treated as if the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute has been applied.</span></span> <span data-ttu-id="647ea-134">Na przykład następujące wyliczenie niejawnie określono kontraktu danych odpowiednikiem poprzedniego `CarConditionEnum` przykład.</span><span class="sxs-lookup"><span data-stu-id="647ea-134">For example, the following enumeration implicitly has a data contract equivalent to the preceding `CarConditionEnum` example.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#6)]
 [!code-vb[c_DataContractEnumerations#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#6)]  
  
 <span data-ttu-id="647ea-135">Można użyć prostego wyliczenia, gdy nie chcesz dostosować nazwy kontraktu danych wyliczenia i przestrzeni nazw i wartości elementu członkowskiego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="647ea-135">You can use simple enumerations when you do not need to customize the enumeration's data contract name and namespace and the enumeration member values.</span></span>  
  
#### <a name="notes-on-simple-enumerations"></a><span data-ttu-id="647ea-136">Uwagi dotyczące prostego wyliczenia</span><span class="sxs-lookup"><span data-stu-id="647ea-136">Notes on Simple Enumerations</span></span>  
 <span data-ttu-id="647ea-137">Stosowanie <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybut do prostych wyliczenia nie ma znaczenia.</span><span class="sxs-lookup"><span data-stu-id="647ea-137">Applying the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute to simple enumerations has no effect.</span></span>  
  
 <span data-ttu-id="647ea-138">Nie ma różnicy czy <xref:System.SerializableAttribute> atrybut jest stosowany do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="647ea-138">It makes no difference whether or not the <xref:System.SerializableAttribute> attribute is applied to the enumeration.</span></span>  
  
 <span data-ttu-id="647ea-139">Fakt który <xref:System.Runtime.Serialization.DataContractSerializer> klasy uwzględniane są <xref:System.NonSerializedAttribute> atrybut zastosowany do elementy członkowskie wyliczenia różni się od zachowania <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span><span class="sxs-lookup"><span data-stu-id="647ea-139">The fact that the <xref:System.Runtime.Serialization.DataContractSerializer> class honors the <xref:System.NonSerializedAttribute> attribute applied to enumeration members is different from the behavior of the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="647ea-140">Oba te serializatorów Ignoruj <xref:System.NonSerializedAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="647ea-140">Both of those serializers ignore the <xref:System.NonSerializedAttribute> attribute.</span></span>  
  
## <a name="flag-enumerations"></a><span data-ttu-id="647ea-141">Flaga wyliczenia</span><span class="sxs-lookup"><span data-stu-id="647ea-141">Flag Enumerations</span></span>  
 <span data-ttu-id="647ea-142">Możesz zastosować <xref:System.FlagsAttribute> atrybutu do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="647ea-142">You can apply the <xref:System.FlagsAttribute> attribute to enumerations.</span></span> <span data-ttu-id="647ea-143">W takim przypadku listę zero lub więcej wartości wyliczenia mogą być wysyłane lub odbierane jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="647ea-143">In that case, a list of zero or more enumeration values can be sent or received simultaneously.</span></span>  
  
 <span data-ttu-id="647ea-144">Aby to zrobić, należy zastosować <xref:System.Runtime.Serialization.DataContractAttribute> atrybutu wyliczanie flag, a następnie Oznacz wszystkie elementy członkowskie, które są potęgami liczby dwa z <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="647ea-144">To do so, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the flag enumeration and then mark all the members that are powers of two with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute.</span></span> <span data-ttu-id="647ea-145">Należy pamiętać, że aby użyć wyliczanie flag, postęp musi być nieprzerwaną sekwencji potęgami liczby 2 (na przykład 1, 2, 4, 8, 16, 32, 64).</span><span class="sxs-lookup"><span data-stu-id="647ea-145">Note that to use a flag enumeration, the progression must be an uninterrupted sequence of powers of 2 (for example, 1, 2, 4, 8, 16, 32, 64).</span></span>  
  
 <span data-ttu-id="647ea-146">Poniższe kroki dotyczą wysyłania wartości wyliczenia flagi:</span><span class="sxs-lookup"><span data-stu-id="647ea-146">The following steps apply to sending a flag's enumeration value:</span></span>  
  
1.  <span data-ttu-id="647ea-147">Próba odnalezienia elementu członkowskiego wyliczenia (z <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybut zastosowany) która jest mapowana na wartość liczbową.</span><span class="sxs-lookup"><span data-stu-id="647ea-147">Attempt to find an enumeration member (with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that maps to the numeric value.</span></span> <span data-ttu-id="647ea-148">Jeśli znaleziono, Wyślij listę, która zawiera tylko ten element członkowski.</span><span class="sxs-lookup"><span data-stu-id="647ea-148">If found, send a list that contains just that member.</span></span>  
  
2.  <span data-ttu-id="647ea-149">Próba Podziel wartość liczbową na sumę w taki sposób, że istnieją elementy członkowskie wyliczenia (każde z nich <xref:System.Runtime.Serialization.EnumMemberAttribute> atrybut zastosowany) mapowania każdej części suma.</span><span class="sxs-lookup"><span data-stu-id="647ea-149">Attempt to break the numeric value into a sum such that there are enumeration members (each with the <xref:System.Runtime.Serialization.EnumMemberAttribute> attribute applied) that map to each part of the sum.</span></span> <span data-ttu-id="647ea-150">Wysyłanie listy wszystkich tych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="647ea-150">Send the list of all these members.</span></span> <span data-ttu-id="647ea-151">Należy pamiętać, że *zachłanne algorytm* jest używana do znajdowania tych sum i w związku z tym nie ma gwarancji, że takie Suma zostanie znaleziony, nawet jeśli jest obecny.</span><span class="sxs-lookup"><span data-stu-id="647ea-151">Note that the *greedy algorithm* is used to find such a sum, and thus there is no guarantee that such a sum is found even if it is present.</span></span> <span data-ttu-id="647ea-152">Aby uniknąć tego problemu, upewnij się, że wartości liczbowych elementy członkowskie wyliczenia są potęgami liczby dwa.</span><span class="sxs-lookup"><span data-stu-id="647ea-152">To avoid this problem, make sure that the numeric values of the enumeration members are powers of two.</span></span>  
  
3.  <span data-ttu-id="647ea-153">Jeśli dwa poprzednie kroki zakończyć się niepowodzeniem, a wartość liczbowa jest różna od zera, throw <xref:System.Runtime.Serialization.SerializationException>.</span><span class="sxs-lookup"><span data-stu-id="647ea-153">If the preceding two steps fail, and the numeric value is nonzero, throw a <xref:System.Runtime.Serialization.SerializationException>.</span></span> <span data-ttu-id="647ea-154">Jeśli wartość liczbowa jest zero, należy wysłać pustej listy.</span><span class="sxs-lookup"><span data-stu-id="647ea-154">If the numeric value is zero, send the empty list.</span></span>  
  
### <a name="example"></a><span data-ttu-id="647ea-155">Przykład</span><span class="sxs-lookup"><span data-stu-id="647ea-155">Example</span></span>  
 <span data-ttu-id="647ea-156">W poniższym przykładzie wyliczenie można użyć w operacji flagi.</span><span class="sxs-lookup"><span data-stu-id="647ea-156">The following enumeration example can be used in a flag operation.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#4)]
 [!code-vb[c_DataContractEnumerations#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#4)]  
  
 <span data-ttu-id="647ea-157">Następujące przykładowe wartości są serializowane wskazane.</span><span class="sxs-lookup"><span data-stu-id="647ea-157">The following example values are serialized as indicated.</span></span>  
  
 [!code-csharp[c_DataContractEnumerations#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractenumerations/cs/source.cs#5)]
 [!code-vb[c_DataContractEnumerations#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractenumerations/vb/source.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="647ea-158">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="647ea-158">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [<span data-ttu-id="647ea-159">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="647ea-159">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="647ea-160">Określanie transferu danych w kontraktach usług</span><span class="sxs-lookup"><span data-stu-id="647ea-160">Specifying Data Transfer in Service Contracts</span></span>](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)