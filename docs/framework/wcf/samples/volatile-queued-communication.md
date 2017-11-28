---
title: "Komunikacja za pomocą nietrwałych kolejek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a7e6bb57245e9877fe337b86a03565d0197b0084
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="volatile-queued-communication"></a><span data-ttu-id="cae9a-102">Komunikacja za pomocą nietrwałych kolejek</span><span class="sxs-lookup"><span data-stu-id="cae9a-102">Volatile Queued Communication</span></span>
<span data-ttu-id="cae9a-103">W tym przykładzie pokazano, jak wykonać volatile komunikatu w kolejce przez transportu usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="cae9a-103">This sample demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="cae9a-104">W przykładzie użyto <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="cae9a-104">This sample uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="cae9a-105">Usługa jest w tym przypadku aplikacji konsoli siebie umożliwia obserwowanie usługi odbieranie wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="cae9a-105">The service in this case is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cae9a-106">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="cae9a-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="cae9a-107">W kolejce komunikacji klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="cae9a-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="cae9a-108">Mówiąc ściślej klient wysyła wiadomości do kolejki.</span><span class="sxs-lookup"><span data-stu-id="cae9a-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="cae9a-109">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="cae9a-109">The service receives messages from the queue.</span></span> <span data-ttu-id="cae9a-110">Usługi i klienta w związku z tym ma być uruchomiona, w tym samym czasie do komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="cae9a-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="cae9a-111">Podczas wysyłania wiadomości nie gwarancji, MSMQ tylko sprawia, że optymalnego na dostarczenie wiadomości, w przeciwieństwie do dokładnie raz gwarancji gdzie MSMQ zapewnia czy komunikat pobiera wydana lub, jeśli nie można dostarczyć, pozwala dowiedzieć się, że nie można dostarczyć wiadomości.</span><span class="sxs-lookup"><span data-stu-id="cae9a-111">When you send a message with no assurances, MSMQ only makes a best effort to deliver the message, unlike with Exactly Once assurances where MSMQ ensures that the message gets delivered or, if it cannot be delivered, lets you know that the message cannot be delivered.</span></span>  
  
 <span data-ttu-id="cae9a-112">W niektórych scenariuszach można wysłać wiadomość volatile nie gwarancji za pośrednictwem kolejki, gdy czas dostawy ma większe znaczenie niż utraty wiadomości.</span><span class="sxs-lookup"><span data-stu-id="cae9a-112">In certain scenarios, you may want to send a volatile message with no assurances over a queue, when timely delivery is more important than losing messages.</span></span> <span data-ttu-id="cae9a-113">Volatile wiadomości po awarii menedżera kolejki.</span><span class="sxs-lookup"><span data-stu-id="cae9a-113">Volatile messages do not survive queue manager crashes.</span></span> <span data-ttu-id="cae9a-114">Dlatego jeśli wystąpiła awaria menedżera kolejek, nietransakcyjnej kolejki używane do przechowywania wiadomości volatile przeżyje, ale komunikaty się czy nie, ponieważ komunikaty nie są przechowywane na dysku.</span><span class="sxs-lookup"><span data-stu-id="cae9a-114">Therefore if the queue manager crashes, the non-transactional queue used to store volatile messages survives but the messages themselves do not because the messages are not stored on the disk.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cae9a-115">Nie można wysłać wiadomości volatile nie gwarancji w zakresie transakcji za pomocą usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="cae9a-115">You cannot send volatile messages with no assurances within the scope of a transaction using MSMQ.</span></span> <span data-ttu-id="cae9a-116">Należy także utworzyć nietransakcyjnej kolejkę do wysyłania wiadomości volatile.</span><span class="sxs-lookup"><span data-stu-id="cae9a-116">You also must create a non-transactional queue to send volatile messages.</span></span>  
  
 <span data-ttu-id="cae9a-117">Kontrakt usługi, w tym przykładzie jest `IStockTicker` definiuje usługi jednokierunkowe, które są najbardziej odpowiednie do użycia z usługi kolejkowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="cae9a-117">The service contract in this sample is `IStockTicker` that defines one-way services that are best suited for use with queuing.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IStockTicker  
{  
    [OperationContract(IsOneWay = true)]  
    void StockTick(string symbol, float price);  
}  
```  
  
 <span data-ttu-id="cae9a-118">Operacja usługi wyświetla symbol giełdowych i cen, jak pokazano w poniższym kodzie próbki:</span><span class="sxs-lookup"><span data-stu-id="cae9a-118">The service operation displays the stock ticker symbol and price, as shown in the following sample code:</span></span>  
  
```  
public class StockTickerService : IStockTicker  
{  
    public void StockTick(string symbol, float price)  
    {  
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);  
     }  
     …  
}  
```  
  
 <span data-ttu-id="cae9a-119">Usługa jest samodzielnie hostowana.</span><span class="sxs-lookup"><span data-stu-id="cae9a-119">The service is self hosted.</span></span> <span data-ttu-id="cae9a-120">Za pomocą transportu MSMQ, kolejki używane musi zostać utworzona z wyprzedzeniem.</span><span class="sxs-lookup"><span data-stu-id="cae9a-120">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="cae9a-121">Można to zrobić ręcznie lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="cae9a-121">This can be done manually or through code.</span></span> <span data-ttu-id="cae9a-122">W tym przykładzie Usługa zawiera kod, aby sprawdzić obecność kolejki i go utworzyć, jeśli jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="cae9a-122">In this sample, the service contains code to check for the existence of the queue and create it if required.</span></span> <span data-ttu-id="cae9a-123">Nazwa kolejki jest do odczytu z pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cae9a-123">The queue name is read from the configuration file.</span></span> <span data-ttu-id="cae9a-124">Adres podstawowy jest używany przez [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania serwera proxy dla usługi.</span><span class="sxs-lookup"><span data-stu-id="cae9a-124">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy for the service.</span></span>  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName);  
  
    // Create a ServiceHost for the StockTickerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();  
    }  
}  
```  
  
 <span data-ttu-id="cae9a-125">Nazwa kolejki usługi MSMQ jest określona w sekcji appSettings pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cae9a-125">The MSMQ queue name is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="cae9a-126">Punkt końcowy usługi jest zdefiniowany w sekcji system.serviceModel pliku konfiguracji i określa `netMsmqBinding` powiązania.</span><span class="sxs-lookup"><span data-stu-id="cae9a-126">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cae9a-127">Nazwa kolejki używa pojedynczego znaku kropki (.) lokalnego separatory maszyny i ukośnika w jego ścieżki, podczas tworzenia kolejki przy użyciu <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="cae9a-127">The queue name uses a dot (.) for the local machine and backslash separators in its path when creating a queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="cae9a-128">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Net.msmq Określa adres punktu końcowego: schemat, używa "localhost" dla komputera lokalnego i ukośniki pod jego ścieżki.</span><span class="sxs-lookup"><span data-stu-id="cae9a-128">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine and forward slashes in its path.</span></span>  
  
 <span data-ttu-id="cae9a-129">Gwarancje i trwałości lub zmienności wiadomości są również określona w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="cae9a-129">The assurances and durability or volatility of messages are also specified in the configuration.</span></span>  
  
```xml  
<appSettings>  
  <!-- use appSetting to configure MSMQ queue name -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"  
                binding="netMsmqBinding"  
                bindingConfiguration="volatileBinding"   
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />  
    ...  
          </service>  
  </services>  
  
  <bindings>  
    <netMsmqBinding>  
      <binding name="volatileBinding"   
             durable="false"  
           exactlyOnce="false"/>  
    </netMsmqBinding>  
  </bindings>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="cae9a-130">Ponieważ próbki wysyła wiadomości z kolejki przy użyciu kolejki nietransakcyjnej, wiadomości transakcyjne nie można wysłać do kolejki.</span><span class="sxs-lookup"><span data-stu-id="cae9a-130">Because the sample sends queued messages by using a non-transactional queue, transacted messages cannot be sent to the queue.</span></span>  
  
```  
// Create a client.  
Random r = new Random(137);  
  
StockTickerClient client = new StockTickerClient();  
  
float price = 43.23F;  
for (int i = 0; i < 10; i++)  
{  
    float increment = 0.01f * (r.Next(10));  
    client.StockTick("zzz" + i, price + increment);  
}  
  
//Closing the client gracefully cleans up resources.  
client.Close();  
```  
  
 <span data-ttu-id="cae9a-131">Po uruchomieniu próbki działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="cae9a-131">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="cae9a-132">Można wyświetlić wiadomości receive usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="cae9a-132">You can see the service receive messages from the client.</span></span> <span data-ttu-id="cae9a-133">Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="cae9a-133">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="cae9a-134">Należy zauważyć, że usługi kolejkowania wiadomości jest w użyciu, klient i usługa nie być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="cae9a-134">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="cae9a-135">Możesz z klientem, zamknij go, a następnie uruchom usługi i nadal otrzymuje jej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="cae9a-135">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Stock Tick zzz0:43.25  
Stock Tick zzz1:43.23  
Stock Tick zzz2:43.28  
Stock Tick zzz3:43.3  
Stock Tick zzz4:43.23  
Stock Tick zzz5:43.25  
Stock Tick zzz6:43.25  
Stock Tick zzz7:43.24  
Stock Tick zzz8:43.32  
Stock Tick zzz9:43.3  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cae9a-136">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="cae9a-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cae9a-137">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cae9a-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cae9a-138">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cae9a-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="cae9a-139">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cae9a-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="cae9a-140">Domyślnie z <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczeń transportu jest włączona.</span><span class="sxs-lookup"><span data-stu-id="cae9a-140">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="cae9a-141">Istnieją dwa odpowiednie właściwości zabezpieczeń transportu MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` domyślnie tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="cae9a-141">There are two pertinent properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="cae9a-142">Dla usługi MSMQ w celu zapewnienia uwierzytelniania oraz podpisywania funkcji musi być częścią domeny, a opcja integracji usługi active directory dla usługi MSMQ musi być zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="cae9a-142">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="cae9a-143">Jeśli w tym przykładzie jest uruchomiony na komputerze, który nie spełnia te kryteria, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="cae9a-143">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="cae9a-144">Aby uruchomić na komputerze, na przykład dołączona do grupy roboczej lub bez integracji z usługą active directory</span><span class="sxs-lookup"><span data-stu-id="cae9a-144">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="cae9a-145">Jeśli komputer nie jest częścią domeny lub nie ma zainstalowanych integracji usługi active directory, należy wyłączyć zabezpieczeń transportu przez ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższym kodzie próbki w konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="cae9a-145">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code:</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <services>  
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"  
                   behaviorConfiguration="StockTickerServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="volatileBinding"   
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />  
            <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="volatileBinding"   
                  durable="false"  
                  exactlyOnce="false">  
              <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="StockTickerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="cae9a-146">Sprawdź, czy zmian konfiguracji na serwerze i kliencie, przed uruchomieniem próbki.</span><span class="sxs-lookup"><span data-stu-id="cae9a-146">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="cae9a-147">Ustawienie `security mode` do `None` jest odpowiednikiem ustawienia <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, i `Message` zabezpieczeń do `None`.</span><span class="sxs-lookup"><span data-stu-id="cae9a-147">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cae9a-148">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cae9a-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cae9a-149">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cae9a-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cae9a-150">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="cae9a-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cae9a-151">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cae9a-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`  
  
## <a name="see-also"></a><span data-ttu-id="cae9a-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cae9a-152">See Also</span></span>