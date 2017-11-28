---
title: 'Transport: UDP'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
caps.latest.revision: "48"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ae7df5531abf2efcb7ba0059da1d8393e5a3f7c4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="transport-udp"></a><span data-ttu-id="2700f-102">Transport: UDP</span><span class="sxs-lookup"><span data-stu-id="2700f-102">Transport: UDP</span></span>
<span data-ttu-id="2700f-103">Przykładowe transportu UDP pokazano, jak wdrażanie UDP emisji pojedynczej i multiemisji jako niestandardowego [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transportu.</span><span class="sxs-lookup"><span data-stu-id="2700f-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transport.</span></span> <span data-ttu-id="2700f-104">Próbka opisuje zalecaną procedurą tworzenia niestandardowych transportu w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], przy użyciu platformy kanału i wykonując [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] najlepsze rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="2700f-104">The sample describes the recommended procedure for creating a custom transport in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], by using the channel framework and following [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] best practices.</span></span> <span data-ttu-id="2700f-105">Kroki, aby utworzyć niestandardowe transportu są następujące:</span><span class="sxs-lookup"><span data-stu-id="2700f-105">The steps to create a custom transport are as follows:</span></span>  
  
1.  <span data-ttu-id="2700f-106">Decyzji, które kanału [wzorce wymiany wiadomości](#MessageExchangePatterns) (IOutputChannel IInputChannel, IDuplexChannel, IRequestChannel albo IReplyChannel) z elementu ChannelFactory i ChannelListener będzie obsługiwać.</span><span class="sxs-lookup"><span data-stu-id="2700f-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="2700f-107">Następnie zdecydować, czy będzie obsługiwać zamykania zmian tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="2700f-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2.  <span data-ttu-id="2700f-108">Tworzenie fabryki kanałów i odbiornik, który obsługuje Twojej wymiany komunikatów.</span><span class="sxs-lookup"><span data-stu-id="2700f-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3.  <span data-ttu-id="2700f-109">Upewnij się, że wszelkie wyjątki dotyczące sieci są znormalizowane do odpowiedniej klasy pochodnej z <xref:System.ServiceModel.CommunicationException>.</span><span class="sxs-lookup"><span data-stu-id="2700f-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4.  <span data-ttu-id="2700f-110">Dodaj [ \<powiązania >](../../../../docs/framework/misc/binding.md) element, który dodaje niestandardowy transportu do stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="2700f-110">Add a [\<binding>](../../../../docs/framework/misc/binding.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="2700f-111">Aby uzyskać więcej informacji, zobacz [Dodawanie elementu powiązania](#AddingABindingElement).</span><span class="sxs-lookup"><span data-stu-id="2700f-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5.  <span data-ttu-id="2700f-112">Dodaj sekcję rozszerzenia elementu powiązania do udostępnienia element powiązania do konfiguracji systemu.</span><span class="sxs-lookup"><span data-stu-id="2700f-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6.  <span data-ttu-id="2700f-113">Dodawanie rozszerzeń metadanych do komunikowania się funkcji do innych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="2700f-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7.  <span data-ttu-id="2700f-114">Dodaj powiązanie, które wstępnie konfiguruje stos elementy wiązania zgodnie z dobrze zdefiniowanego profilu.</span><span class="sxs-lookup"><span data-stu-id="2700f-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="2700f-115">Aby uzyskać więcej informacji, zobacz [Dodawanie Powiązanie standardowe](#AddingAStandardBinding).</span><span class="sxs-lookup"><span data-stu-id="2700f-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8.  <span data-ttu-id="2700f-116">Dodaj powiązanie sekcji i elementu konfiguracji powiązania do udostępnienia powiązania system konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2700f-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="2700f-117">Aby uzyskać więcej informacji, zobacz [dodanie obsługi konfiguracji](#AddingConfigurationSupport).</span><span class="sxs-lookup"><span data-stu-id="2700f-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a><span data-ttu-id="2700f-118">Wzorce wymiany komunikatów</span><span class="sxs-lookup"><span data-stu-id="2700f-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="2700f-119">Pierwszy krok Pisanie niestandardowych transportu jest podjęcie decyzji, które wzorce wymiany wiadomości (MEPs) są wymagane dla transportu.</span><span class="sxs-lookup"><span data-stu-id="2700f-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="2700f-120">Istnieją trzy MEPs do wyboru:</span><span class="sxs-lookup"><span data-stu-id="2700f-120">There are three MEPs to choose from:</span></span>  
  
-   <span data-ttu-id="2700f-121">Datagramów (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="2700f-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="2700f-122">Korzystając z datagram MEP, klient wysyła wiadomości przy użyciu "wyzwalać i zapomnij" programu exchange.</span><span class="sxs-lookup"><span data-stu-id="2700f-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="2700f-123">Uruchomienie a zapomnieć exchange to taki, który wymaga potwierdzenia poza pasmem pomyślnie dostawy.</span><span class="sxs-lookup"><span data-stu-id="2700f-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="2700f-124">Komunikat mogą zostać utracone podczas przesyłania i nigdy nie dotarcia do usługi.</span><span class="sxs-lookup"><span data-stu-id="2700f-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="2700f-125">Jeśli operacja wysyłania zakończy się pomyślnie po stronie klienta, nie gwarantuje to, że zdalny punkt końcowy odebrał komunikat.</span><span class="sxs-lookup"><span data-stu-id="2700f-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="2700f-126">Datagram jest bloku konstrukcyjnego podstawowych do obsługi wiadomości, ponieważ można tworzyć własne protokoły na nim — łącznie z protokołów bezpieczne i niezawodne protokoły.</span><span class="sxs-lookup"><span data-stu-id="2700f-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="2700f-127">Wdrożenie klienta datagram kanałów <xref:System.ServiceModel.Channels.IOutputChannel> implementuje interfejs i Usługa datagramów kanałów <xref:System.ServiceModel.Channels.IInputChannel> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2700f-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
-   <span data-ttu-id="2700f-128">Żądanie odpowiedź (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="2700f-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="2700f-129">W tym MEP jest wysyłany komunikat i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2700f-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="2700f-130">Wzorzec składa się z pary żądanie / odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="2700f-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="2700f-131">Przykłady wywołań żądań i odpowiedzi są zdalnych wywołań procedur (RPC) i przeglądarka pobiera.</span><span class="sxs-lookup"><span data-stu-id="2700f-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="2700f-132">Ten wzorzec jest nazywany również półdupleks.</span><span class="sxs-lookup"><span data-stu-id="2700f-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="2700f-133">W tym MEP wdrożenia klienta kanałów <xref:System.ServiceModel.Channels.IRequestChannel> i wdrożenie usługi kanałów <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="2700f-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
-   <span data-ttu-id="2700f-134">Dupleks (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="2700f-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="2700f-135">Dupleks MEP umożliwia dowolnej liczby wiadomości wysłane przez klienta i odbieranie w dowolnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="2700f-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="2700f-136">Dupleks MEP przypomina rozmowy telefonicznej każdego wyrazu jest używany w przypadku komunikatu.</span><span class="sxs-lookup"><span data-stu-id="2700f-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="2700f-137">Ponieważ obie strony może wysyłać i odbierać w tym MEP, interfejs implementowany przez kanały klient i usługa jest <xref:System.ServiceModel.Channels.IDuplexChannel>.</span><span class="sxs-lookup"><span data-stu-id="2700f-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="2700f-138">Każdy z tych MEPs również obsługuje sesji.</span><span class="sxs-lookup"><span data-stu-id="2700f-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="2700f-139">Dodano funkcje udostępniane przez kanał obsługujący sesji jest ona są powiązane wszystkich wiadomości wysłanych i odebranych na kanale.</span><span class="sxs-lookup"><span data-stu-id="2700f-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="2700f-140">Wzorzec żądań i odpowiedzi się sesję komunikat dwa autonomiczne skorelowanych żądania i odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2700f-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="2700f-141">Z kolei wzorzec żądań i odpowiedzi, który obsługuje sesji oznacza skorelowanych wszystkie pary żądanie/odpowiedź w tym kanale ze sobą.</span><span class="sxs-lookup"><span data-stu-id="2700f-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="2700f-142">Daje łączną liczbę sześć MEPs — dupleks Datagram, żądanie-odpowiedź, Datagram z sesji i żądań i odpowiedzi z sesji i z sesji dupleksowej — do wyboru.</span><span class="sxs-lookup"><span data-stu-id="2700f-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2700f-143">Dla transportu UDP Datagram, jest tylko MEP, która jest obsługiwana, ponieważ protokół UDP jest z założenia protokołem "wyzwalać i zapomnij".</span><span class="sxs-lookup"><span data-stu-id="2700f-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="2700f-144">Interfejs ICommunicationObject i cyklem życia obiektów WCF</span><span class="sxs-lookup"><span data-stu-id="2700f-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2700f-145">Typowe maszyna stanu, używany do zarządzania cyklem życia obiektów, takich jak <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, i <xref:System.ServiceModel.Channels.IChannelListener> używanych do komunikacji.</span><span class="sxs-lookup"><span data-stu-id="2700f-145"> has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="2700f-146">Brak pięć Państwa, w których te obiekty komunikacji może istnieć.</span><span class="sxs-lookup"><span data-stu-id="2700f-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="2700f-147">Te stany są reprezentowane przez <xref:System.ServiceModel.CommunicationState> wyliczenie i są w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2700f-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
-   <span data-ttu-id="2700f-148">Utworzona: Jest to stan <xref:System.ServiceModel.ICommunicationObject> po raz pierwszy zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="2700f-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="2700f-149">Nie wejścia/wyjścia (We/Wy) występuje w tym stanie.</span><span class="sxs-lookup"><span data-stu-id="2700f-149">No input/output (I/O) occurs in this state.</span></span>  
  
-   <span data-ttu-id="2700f-150">Otwieranie: Obiektów przejścia do tego stanu, kiedy <xref:System.ServiceModel.ICommunicationObject.Open%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="2700f-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="2700f-151">W tym momencie właściwości są wprowadzane niezmienne i można rozpocząć operacji wejścia/wyjścia.</span><span class="sxs-lookup"><span data-stu-id="2700f-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="2700f-152">Ten proces przejścia jest prawidłowy tylko w stanie Created.</span><span class="sxs-lookup"><span data-stu-id="2700f-152">This transition is valid only from the Created state.</span></span>  
  
-   <span data-ttu-id="2700f-153">Otwarta: Przejście obiekty do tego stanu po zakończeniu procesu otwierania.</span><span class="sxs-lookup"><span data-stu-id="2700f-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="2700f-154">Ten proces przejścia jest prawidłowy tylko w stanie otwarcia.</span><span class="sxs-lookup"><span data-stu-id="2700f-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="2700f-155">W tym momencie obiekt jest w pełni gotowa do przeniesienia.</span><span class="sxs-lookup"><span data-stu-id="2700f-155">At this point, the object is fully usable for transfer.</span></span>  
  
-   <span data-ttu-id="2700f-156">Zamknięcia: Obiekty przejścia do tego stanu, kiedy <xref:System.ServiceModel.ICommunicationObject.Close%2A> jest wywoływana dla łagodne zamykanie.</span><span class="sxs-lookup"><span data-stu-id="2700f-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="2700f-157">Ten proces przejścia jest prawidłowy tylko w stanie otwartym.</span><span class="sxs-lookup"><span data-stu-id="2700f-157">This transition is valid only from the Opened state.</span></span>  
  
-   <span data-ttu-id="2700f-158">Zamknięte: W polu Zamknięto obiekty stanu nie są już używać.</span><span class="sxs-lookup"><span data-stu-id="2700f-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="2700f-159">Ogólnie rzecz biorąc większość konfiguracji jest nadal dostępne dla kontroli, ale nie można komunikować.</span><span class="sxs-lookup"><span data-stu-id="2700f-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="2700f-160">Ten stan jest odpowiednikiem zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="2700f-160">This state is equivalent to being disposed.</span></span>  
  
-   <span data-ttu-id="2700f-161">Faulted: W stanie Faulted obiekty są dostępne do wglądu, ale można już używać.</span><span class="sxs-lookup"><span data-stu-id="2700f-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="2700f-162">W przypadku nieodwracalny błąd przejścia obiektu, w tym stanie.</span><span class="sxs-lookup"><span data-stu-id="2700f-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="2700f-163">To jedyne prawidłowe przejścia z tego stanu do `Closed` stanu.</span><span class="sxs-lookup"><span data-stu-id="2700f-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="2700f-164">Brak zdarzeń, które dla każdej zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="2700f-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="2700f-165"><xref:System.ServiceModel.ICommunicationObject.Abort%2A> Metody można wywołać w dowolnej chwili i spowoduje, że obiekt przejście bezpośrednio z bieżącego stanu w stanie zamkniętym.</span><span class="sxs-lookup"><span data-stu-id="2700f-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="2700f-166">Wywoływanie <xref:System.ServiceModel.ICommunicationObject.Abort%2A> kończy pracę niedokończone.</span><span class="sxs-lookup"><span data-stu-id="2700f-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="2700f-167">Fabryka kanałów i odbiornika kanałów</span><span class="sxs-lookup"><span data-stu-id="2700f-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="2700f-168">Następny krok w Pisanie niestandardowych transportu jest utworzenie implementacja <xref:System.ServiceModel.Channels.IChannelFactory> dla kanałów klienta oraz <xref:System.ServiceModel.Channels.IChannelListener> kanałów usługi.</span><span class="sxs-lookup"><span data-stu-id="2700f-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="2700f-169">Warstwie kanału korzysta ze wzorca fabrykę do tworzenia kanałów.</span><span class="sxs-lookup"><span data-stu-id="2700f-169">The channel layer uses a factory pattern for constructing channels.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2700f-170">udostępnia pomocników klasę podstawową dla tego procesu.</span><span class="sxs-lookup"><span data-stu-id="2700f-170"> provides base class helpers for this process.</span></span>  
  
-   <span data-ttu-id="2700f-171"><xref:System.ServiceModel.Channels.CommunicationObject> Klasa implementuje <xref:System.ServiceModel.ICommunicationObject> i wymusza automatu stanów opisany w kroku 2.</span><span class="sxs-lookup"><span data-stu-id="2700f-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span> 

-   <span data-ttu-id="2700f-172">"<xref:System.ServiceModel.Channels.ChannelManagerBase> Klasa implementuje <xref:System.ServiceModel.Channels.CommunicationObject> i zapewnia ujednolicone klasa podstawowa dla <xref:System.ServiceModel.Channels.ChannelFactoryBase> i <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span><span class="sxs-lookup"><span data-stu-id="2700f-172">The``<xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="2700f-173"><xref:System.ServiceModel.Channels.ChannelManagerBase> Klasa działa w połączeniu z <xref:System.ServiceModel.Channels.ChannelBase>, która jest klasy podstawowej, która implementuje <xref:System.ServiceModel.Channels.IChannel>.</span><span class="sxs-lookup"><span data-stu-id="2700f-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
-   <span data-ttu-id="2700f-174">"<xref:System.ServiceModel.Channels.ChannelFactoryBase> Klasa implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> i <xref:System.ServiceModel.Channels.IChannelFactory> i konsoliduje `CreateChannel` overloads do jednego `OnCreateChannel` metody abstrakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="2700f-174">The``<xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
-   <span data-ttu-id="2700f-175"><xref:System.ServiceModel.Channels.ChannelListenerBase> Klasa implementuje <xref:System.ServiceModel.Channels.IChannelListener>.</span><span class="sxs-lookup"><span data-stu-id="2700f-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="2700f-176">Odpowiada on za podstawowy zarządzania.</span><span class="sxs-lookup"><span data-stu-id="2700f-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="2700f-177">W tym przykładzie wdrożenie fabryki znajduje się w UdpChannelFactory.cs i implementacji odbiornika znajduje się w UdpChannelListener.cs.</span><span class="sxs-lookup"><span data-stu-id="2700f-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="2700f-178"><xref:System.ServiceModel.Channels.IChannel> Implementacje znajdują się w UdpOutputChannel.cs i UdpInputChannel.cs.</span><span class="sxs-lookup"><span data-stu-id="2700f-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="2700f-179">Fabryka kanałów UDP</span><span class="sxs-lookup"><span data-stu-id="2700f-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="2700f-180">`UdpChannelFactory` Pochodną <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span><span class="sxs-lookup"><span data-stu-id="2700f-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="2700f-181">Zastępuje próbki <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> zapewniające dostęp do wersji kodera wiadomości wiadomości.</span><span class="sxs-lookup"><span data-stu-id="2700f-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="2700f-182">Zastępuje również próbki <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> tak, aby firma Microsoft zerwanie naszych wystąpienie <xref:System.ServiceModel.Channels.BufferManager> podczas przejścia komputera stanu.</span><span class="sxs-lookup"><span data-stu-id="2700f-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="2700f-183">Kanał wyjściowy UDP</span><span class="sxs-lookup"><span data-stu-id="2700f-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="2700f-184">`UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>.</span><span class="sxs-lookup"><span data-stu-id="2700f-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="2700f-185">Konstruktor sprawdza poprawność argumentów i tworzy miejsce docelowe <xref:System.Net.EndPoint> na podstawie obiektu <xref:System.ServiceModel.EndpointAddress> przekazanego pakietu.</span><span class="sxs-lookup"><span data-stu-id="2700f-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="2700f-186">Kanał może zostać zamknięty, bezpiecznie lub ungracefully.</span><span class="sxs-lookup"><span data-stu-id="2700f-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="2700f-187">Jeśli bezpiecznie zamknięcie kanału gniazda zostanie zamknięte, a połączenie jest nawiązywane w klasie podstawowej `OnClose` metody.</span><span class="sxs-lookup"><span data-stu-id="2700f-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="2700f-188">Jeśli to zgłasza wyjątek, wywołuje metodę infrastruktury `Abort` zapewnienie kanał jest wyczyszczone.</span><span class="sxs-lookup"><span data-stu-id="2700f-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="2700f-189">Następnie wdrożymy `Send()` i `BeginSend()` / `EndSend()`.</span><span class="sxs-lookup"><span data-stu-id="2700f-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="2700f-190">To dzieli się na dwóch głównych sekcji.</span><span class="sxs-lookup"><span data-stu-id="2700f-190">This breaks down into two main sections.</span></span> <span data-ttu-id="2700f-191">Najpierw możemy serializować komunikat do tablicy typu byte.</span><span class="sxs-lookup"><span data-stu-id="2700f-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="2700f-192">Firma Microsoft wyśle danych w sieci.</span><span class="sxs-lookup"><span data-stu-id="2700f-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="2700f-193">UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="2700f-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="2700f-194">"UdpChannelListener implementujący próbki jest pochodną <xref:System.ServiceModel.Channels.ChannelListenerBase> klasy.</span><span class="sxs-lookup"><span data-stu-id="2700f-194">The``UdpChannelListener that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="2700f-195">Użyto jednego gniazda UDP do odbierania datagramów.</span><span class="sxs-lookup"><span data-stu-id="2700f-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="2700f-196">`OnOpen` Metody odbiera dane przy użyciu gniazda UDP w pętli asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="2700f-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="2700f-197">Dane są następnie konwertowane na wiadomości przy użyciu platformy Kodowanie komunikatu.</span><span class="sxs-lookup"><span data-stu-id="2700f-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="2700f-198">Ponieważ ten sam kanał datagram reprezentuje komunikaty przychodzące z różnych źródeł, `UdpChannelListener` odbiornik singleton.</span><span class="sxs-lookup"><span data-stu-id="2700f-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="2700f-199">Na większości, jeden aktywny <xref:System.ServiceModel.Channels.IChannel>'' skojarzone z tym odbiorniku naraz.</span><span class="sxs-lookup"><span data-stu-id="2700f-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel>``associated with this listener at a time.</span></span> <span data-ttu-id="2700f-200">Przykład generuje kolejnego tylko wtedy, gdy kanału, który jest zwracany przez `AcceptChannel` metody później został usunięty.</span><span class="sxs-lookup"><span data-stu-id="2700f-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="2700f-201">Po otrzymaniu komunikatu jest dodawanych do kolejki w tym kanale singleton.</span><span class="sxs-lookup"><span data-stu-id="2700f-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="2700f-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="2700f-202">UdpInputChannel</span></span>  
 <span data-ttu-id="2700f-203">`UdpInputChannel` Klasa implementuje `IInputChannel`.</span><span class="sxs-lookup"><span data-stu-id="2700f-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="2700f-204">Składa się z kolejki wiadomości przychodzących, które jest wypełniana `UdpChannelListener`do gniazda.</span><span class="sxs-lookup"><span data-stu-id="2700f-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="2700f-205">Komunikaty te są usuniętej przez `IInputChannel.Receive` metody.</span><span class="sxs-lookup"><span data-stu-id="2700f-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a><span data-ttu-id="2700f-206">Dodawanie elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="2700f-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="2700f-207">Teraz, kiedy są tworzone i fabryki kanałów, firma Microsoft musi ujawniać je do środowiska wykonawczego ServiceModel za pośrednictwem powiązania.</span><span class="sxs-lookup"><span data-stu-id="2700f-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="2700f-208">Powiązanie to kolekcja elementów powiązań reprezentujący stosu komunikacji skojarzony z adresem usługi.</span><span class="sxs-lookup"><span data-stu-id="2700f-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="2700f-209">Każdy element na stosie jest reprezentowana przez [ \<powiązania >](../../../../docs/framework/misc/binding.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="2700f-209">Each element in the stack is represented by a [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span>  
  
 <span data-ttu-id="2700f-210">W przykładzie jest element powiązania `UdpTransportBindingElement`, która jest pochodną <xref:System.ServiceModel.Channels.TransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="2700f-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="2700f-211">Zastępuje on następujące metody umożliwiające tworzenie fabryki skojarzony z powiązaniem naszych.</span><span class="sxs-lookup"><span data-stu-id="2700f-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 <span data-ttu-id="2700f-212">Zawiera także członków do klonowania `BindingElement` i zwracanie naszych schematu (soap.udp).</span><span class="sxs-lookup"><span data-stu-id="2700f-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="2700f-213">Dodawanie obsługi metadanych elementu powiązania transportu</span><span class="sxs-lookup"><span data-stu-id="2700f-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="2700f-214">Integrowanie naszych transportu w metadanych systemu, firma Microsoft obsługuje importu i eksportu zasad.</span><span class="sxs-lookup"><span data-stu-id="2700f-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="2700f-215">Pozwala to Generowanie klientów naszych powiązania za pośrednictwem [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2700f-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="2700f-216">Dodawanie obsługi WSDL</span><span class="sxs-lookup"><span data-stu-id="2700f-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="2700f-217">Element powiązania transportu w powiązaniu jest odpowiedzialny za eksportowanie i importowanie informacji o adresach w metadanych.</span><span class="sxs-lookup"><span data-stu-id="2700f-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="2700f-218">Korzystając z powiązaniem SOAP, element powiązania transportu należy również eksportować poprawne transportu identyfikatora URI w metadanych.</span><span class="sxs-lookup"><span data-stu-id="2700f-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="2700f-219">Eksportu WSDL</span><span class="sxs-lookup"><span data-stu-id="2700f-219">WSDL Export</span></span>  
 <span data-ttu-id="2700f-220">Aby wyeksportować informacje adresowania `UdpTransportBindingElement` implementuje `IWsdlExportExtension` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2700f-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="2700f-221">`ExportEndpoint` Metoda dodaje poprawne informacje adresowania do portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="2700f-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="2700f-222">`UdpTransportBindingElement` Implementacja `ExportEndpoint` metody Eksportuje również transportu identyfikatora URI gdy punkt końcowy korzysta z powiązaniem SOAP.</span><span class="sxs-lookup"><span data-stu-id="2700f-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="2700f-223">Importu WSDL</span><span class="sxs-lookup"><span data-stu-id="2700f-223">WSDL Import</span></span>  
 <span data-ttu-id="2700f-224">Rozszerzenie importu WSDL systemu do obsługi importowanie adresów, możemy dodać następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="2700f-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2700f-225">Podczas uruchamiania Svcutil.exe, istnieją dwa sposoby uzyskania Svcutil.exe można załadować rozszerzenia importu WSDL:</span><span class="sxs-lookup"><span data-stu-id="2700f-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1.  <span data-ttu-id="2700f-226">Punkt Svcutil.exe naszych pliku konfiguracji za pomocą /SvcutilConfig:\<pliku >.</span><span class="sxs-lookup"><span data-stu-id="2700f-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="2700f-227">Dodaj sekcję konfiguracyjną do Svcutil.exe.config w tym samym katalogu co Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="2700f-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="2700f-228">`UdpBindingElementImporter` Typ implementuje `IWsdlImportExtension` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="2700f-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="2700f-229">`ImportEndpoint` Metoda importuje adres z portu WSDL.</span><span class="sxs-lookup"><span data-stu-id="2700f-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="2700f-230">Dodawanie obsługi zasad</span><span class="sxs-lookup"><span data-stu-id="2700f-230">Adding Policy Support</span></span>  
 <span data-ttu-id="2700f-231">Element powiązania niestandardowego można wyeksportować potwierdzenia zasad w powiązaniu WSDL dla punktu końcowego usługi Express możliwości tego elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="2700f-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="2700f-232">Eksportowanie zasad</span><span class="sxs-lookup"><span data-stu-id="2700f-232">Policy Export</span></span>  
 <span data-ttu-id="2700f-233">`UdpTransportBindingElement` Typ implementuje `IPolicyExportExtension` Aby dodać obsługę eksportowania zasady.</span><span class="sxs-lookup"><span data-stu-id="2700f-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="2700f-234">W związku z tym `System.ServiceModel.MetadataExporter` obejmuje `UdpTransportBindingElement` generacji zasady dla żadnego powiązania, która go zawiera.</span><span class="sxs-lookup"><span data-stu-id="2700f-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="2700f-235">W `IPolicyExportExtension.ExportPolicy`, możemy Dodawanie potwierdzenie dla protokołów UDP i potwierdzenia innego Jeśli firma Microsoft pracuje w trybie multiemisji.</span><span class="sxs-lookup"><span data-stu-id="2700f-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="2700f-236">Wynika to tryb multiemisji ma wpływ na sposób stosu komunikacji jest tworzony i w związku z tym musi być między obie strony.</span><span class="sxs-lookup"><span data-stu-id="2700f-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix, 
        UdpPolicyStrings.MulticastAssertion, 
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="2700f-237">Ponieważ elementy powiązania transportu niestandardowy jest odpowiedzialny za obsługę adresowania, `IPolicyExportExtension` implementacji na `UdpTransportBindingElement` również musi obsługiwać eksportowanie zasad potwierdzenia WS-Addressing odpowiednie wskazująca wersji WS-Addressing używana.</span><span class="sxs-lookup"><span data-stu-id="2700f-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="2700f-238">Importowanie zasad</span><span class="sxs-lookup"><span data-stu-id="2700f-238">Policy Import</span></span>  
 <span data-ttu-id="2700f-239">Rozszerzenie systemu zaimportować zasad, możemy Dodaj następującą konfigurację do pliku konfiguracji dla Svcutil.exe jak pokazano w pliku Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="2700f-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2700f-240">Następnie wdrożymy `IPolicyImporterExtension` z naszych zarejestrowanych klasy (`UdpBindingElementImporter`).</span><span class="sxs-lookup"><span data-stu-id="2700f-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="2700f-241">W `ImportPolicy()`, firma Microsoft za pośrednictwem potwierdzenia w naszym przestrzeni nazw i przetworzyć te generowania transportu i sprawdź, czy multiemisji.</span><span class="sxs-lookup"><span data-stu-id="2700f-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="2700f-242">Możemy również usunąć potwierdzenia, które chronimy z listy powiązania potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="2700f-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="2700f-243">Ponownie uruchamiając Svcutil.exe, dostępne są dwie opcje do integracji:</span><span class="sxs-lookup"><span data-stu-id="2700f-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1.  <span data-ttu-id="2700f-244">Punkt Svcutil.exe naszych pliku konfiguracji za pomocą /SvcutilConfig:\<pliku >.</span><span class="sxs-lookup"><span data-stu-id="2700f-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2.  <span data-ttu-id="2700f-245">Dodaj sekcję konfiguracyjną do Svcutil.exe.config w tym samym katalogu co Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="2700f-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a><span data-ttu-id="2700f-246">Dodawanie Powiązanie standardowe</span><span class="sxs-lookup"><span data-stu-id="2700f-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="2700f-247">Nasze element powiązania mogą być używane na dwa sposoby:</span><span class="sxs-lookup"><span data-stu-id="2700f-247">Our binding element can be used in the following two ways:</span></span>  
  
-   <span data-ttu-id="2700f-248">Za pomocą niestandardowego powiązania: niestandardowego powiązania umożliwia użytkownikom tworzenie własnych powiązania na podstawie dowolnego zestawu elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="2700f-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
-   <span data-ttu-id="2700f-249">Za pomocą powiązania dostarczane przez system, która zawiera naszych elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="2700f-249">By using a system-provided binding that includes our binding element.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="2700f-250">udostępnia wiele tych powiązań zdefiniowanych przez system, taką jak `BasicHttpBinding`, `NetTcpBinding`, i `WsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="2700f-250"> provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="2700f-251">Każdy z tych powiązań jest skojarzona z profilem dobrze zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="2700f-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="2700f-252">Przykład implementuje powiązanie profilu w `SampleProfileUdpBinding`, która jest pochodną <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="2700f-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="2700f-253">`SampleProfileUdpBinding` Zawiera maksymalnie cztery elementy powiązania w nim: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, i `ReliableSessionBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="2700f-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="2700f-254">Dodawanie niestandardowego powiązania importera Standard</span><span class="sxs-lookup"><span data-stu-id="2700f-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="2700f-255">Svcutil.exe i `WsdlImporter` typu domyślnie rozpoznaje i importuje powiązań zdefiniowanych przez system.</span><span class="sxs-lookup"><span data-stu-id="2700f-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="2700f-256">W przeciwnym razie zaimportowany, ponieważ pobiera powiązania `CustomBinding` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="2700f-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="2700f-257">Aby włączyć Svcutil.exe i `WsdlImporter` do zaimportowania `SampleProfileUdpBinding` `UdpBindingElementImporter` działa również jako importer niestandardowe Powiązanie standardowe.</span><span class="sxs-lookup"><span data-stu-id="2700f-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="2700f-258">Implementuje importera niestandardowe Powiązanie standardowe `ImportEndpoint` metoda `IWsdlImportExtension` interfejs do sprawdzenia `CustomBinding` wystąpienia zaimportowane z metadanych, aby zobaczyć, czy może on zostać wygenerowane przez określone powiązanie standardowe.</span><span class="sxs-lookup"><span data-stu-id="2700f-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="2700f-259">Ogólnie rzecz biorąc importera niestandardowego powiązania standardowa implementacja polega na sprawdzanie właściwości elementów importowanych powiązanie, aby sprawdzić, czy zostały zmienione tylko właściwości, które można ustawić przez powiązanie standardowe i inne właściwości są ich wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="2700f-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="2700f-260">Podstawowe strategię implementowania importera Powiązanie standardowe jest do utworzenia wystąpienia Powiązanie standardowe, propagowanie powiązania właściwości z elementów wiążących wystąpienie Powiązanie standardowe obsługującej Powiązanie standardowe i porównania elementy z Powiązanie standardowe elementami importowanych powiązania.</span><span class="sxs-lookup"><span data-stu-id="2700f-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a><span data-ttu-id="2700f-261">Dodawanie obsługi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2700f-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="2700f-262">Do udostępnienia naszych transportu za pomocą konfiguracji, musimy zaimplementować dwie sekcje konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2700f-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="2700f-263">Pierwsza to `BindingElementExtensionElement` dla `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="2700f-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="2700f-264">Jest to, aby `CustomBinding` implementacje może odwoływać się naszego elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="2700f-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="2700f-265">Druga `Configuration` dla naszych `SampleProfileUdpBinding`.</span><span class="sxs-lookup"><span data-stu-id="2700f-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="2700f-266">Element rozszerzenia elementu powiązania</span><span class="sxs-lookup"><span data-stu-id="2700f-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="2700f-267">Sekcja `UdpTransportElement` jest `BindingElementExtensionElement` który uwidacznia `UdpTransportBindingElement` do konfiguracji systemu.</span><span class="sxs-lookup"><span data-stu-id="2700f-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="2700f-268">Z kilku podstawowych zastąpień definiujemy naszych nazwę sekcji konfiguracji, naszych elementu powiązania oraz sposobu tworzenia naszych elementu powiązania.</span><span class="sxs-lookup"><span data-stu-id="2700f-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="2700f-269">Firma Microsoft można zarejestrować naszej sekcji rozszerzeń w pliku konfiguracji, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2700f-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="2700f-270">Rozszerzenia mogą być przywoływane z niestandardowego powiązania do użycia jako transportu UDP.</span><span class="sxs-lookup"><span data-stu-id="2700f-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a><span data-ttu-id="2700f-271">Sekcja powiązania</span><span class="sxs-lookup"><span data-stu-id="2700f-271">Binding Section</span></span>  
 <span data-ttu-id="2700f-272">Sekcja `SampleProfileUdpBindingCollectionElement` jest `StandardBindingCollectionElement` który uwidacznia `SampleProfileUdpBinding` do konfiguracji systemu.</span><span class="sxs-lookup"><span data-stu-id="2700f-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="2700f-273">Delegowane do zbiorczego wdrożenia `SampleProfileUdpBindingConfigurationElement`, która jest pochodną `StandardBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="2700f-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="2700f-274">`SampleProfileUdpBindingConfigurationElement` Ma właściwości, które odpowiadają właściwościom na `SampleProfileUdpBinding`i funkcji do mapowania z `ConfigurationElement` powiązania.</span><span class="sxs-lookup"><span data-stu-id="2700f-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="2700f-275">Ponadto Zastąp `OnApplyConfiguration` metody w naszym `SampleProfileUdpBinding`, jak pokazano w poniższym kodzie próbki.</span><span class="sxs-lookup"><span data-stu-id="2700f-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 <span data-ttu-id="2700f-276">Aby zarejestrować ten program obsługi przy użyciu systemu konfiguracji, dodania do pliku konfiguracji związanych z poniższej sekcji.</span><span class="sxs-lookup"><span data-stu-id="2700f-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="2700f-277">Można go następnie odwoływać z sekcji konfiguracji serviceModel.</span><span class="sxs-lookup"><span data-stu-id="2700f-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="2700f-278">Usługa badania UDP i klienta</span><span class="sxs-lookup"><span data-stu-id="2700f-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="2700f-279">Za pomocą tego transportu przykładowy kod testu jest dostępny w katalogach UdpTestService i UdpTestClient.</span><span class="sxs-lookup"><span data-stu-id="2700f-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="2700f-280">Kod usługi składa się z dwóch testów — jeden test ustawia punktów końcowych i powiązania z kodu i innych zrobi to za pomocą konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2700f-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="2700f-281">Zarówno testy Użyj dwa punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="2700f-281">Both tests use two endpoints.</span></span> <span data-ttu-id="2700f-282">Jeden punkt końcowy używa `SampleUdpProfileBinding` z [ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) ustawioną `true`.</span><span class="sxs-lookup"><span data-stu-id="2700f-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) set to `true`.</span></span> <span data-ttu-id="2700f-283">Innych punktów końcowych używa niestandardowego powiązania z `UdpTransportBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="2700f-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="2700f-284">Jest to równoważne przy użyciu `SampleUdpProfileBinding` z [ \<reliableSession >](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) ustawioną `false`.</span><span class="sxs-lookup"><span data-stu-id="2700f-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) set to `false`.</span></span> <span data-ttu-id="2700f-285">Zarówno testy Tworzenie usługi, dodawanie punktu końcowego dla każdego powiązania, otwórz usługę i poczekaj, aż użytkownik trafienie ENTER przed zamknięciem usługi.</span><span class="sxs-lookup"><span data-stu-id="2700f-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="2700f-286">Podczas uruchamiania aplikacji testu usługi powinny być widoczne następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="2700f-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="2700f-287">Następnie można uruchomić aplikacji klienckiej testu dla opublikowanych punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="2700f-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="2700f-288">Aplikacja testowa klienta tworzy klienta dla każdego punktu końcowego i wysyła komunikaty pięciu do każdego punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="2700f-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="2700f-289">Następujące dane wyjściowe znajduje się na kliencie.</span><span class="sxs-lookup"><span data-stu-id="2700f-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="2700f-290">Poniżej znajduje się pełne dane wyjściowe w usłudze.</span><span class="sxs-lookup"><span data-stu-id="2700f-290">The following is the full output on the service.</span></span>  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 <span data-ttu-id="2700f-291">Aby uruchomić aplikację klienta przed opublikowane za pomocą konfiguracji punktów końcowych, kliknij przycisk ENTER w usłudze, a następnie ponownie uruchom klienta testowego.</span><span class="sxs-lookup"><span data-stu-id="2700f-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="2700f-292">Następujące dane wyjściowe powinny być widoczne w usłudze.</span><span class="sxs-lookup"><span data-stu-id="2700f-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="2700f-293">Ponowne uruchomienie klienta daje takie same jak w poprzednim.</span><span class="sxs-lookup"><span data-stu-id="2700f-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="2700f-294">Można ponownie wygenerować kod klienta i konfiguracji przy użyciu Svcutil.exe, uruchom aplikację usługi, a następnie uruchom następujące Svcutil.exe z katalogu głównego próbki.</span><span class="sxs-lookup"><span data-stu-id="2700f-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="2700f-295">Należy pamiętać, że Svcutil.exe nie generuje konfiguracji rozszerzenia powiązania dla `SampleProfileUdpBinding`, więc należy ją dodać ręcznie.</span><span class="sxs-lookup"><span data-stu-id="2700f-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>      
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2700f-296">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="2700f-296">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="2700f-297">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2700f-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="2700f-298">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2700f-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="2700f-299">Zapoznaj się z poprzedniej sekcji "UDP testu i klient usługi".</span><span class="sxs-lookup"><span data-stu-id="2700f-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2700f-300">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2700f-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2700f-301">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2700f-301">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2700f-302">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="2700f-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2700f-303">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2700f-303">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`