---
title: "Kontenery jako podstawa współpracy opracowywania oprogramowania"
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 24aad577fca0fd540d66f9e037b58f53583d8fbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a><span data-ttu-id="01209-104">Kontenery jako podstawa współpracy opracowywania oprogramowania</span><span class="sxs-lookup"><span data-stu-id="01209-104">Containers as the foundation for DevOps collaboration</span></span>

<span data-ttu-id="01209-105">Przez charakter kontenery i technologii Docker deweloperzy mogą udostępniać ich oprogramowania i zależności łatwo operacji IT i środowisk produkcyjnych dzięki czemu typowe usprawiedliwienia "działa na komputerze".</span><span class="sxs-lookup"><span data-stu-id="01209-105">By the very nature of the containers and Docker technology, developers can share their software and dependencies easily with IT operations and production environments while eliminating the typical "it works on my machine" excuse.</span></span> <span data-ttu-id="01209-106">Kontenery rozwiązać konflikty aplikacji między różnych środowiskach.</span><span class="sxs-lookup"><span data-stu-id="01209-106">Containers solve application conflicts between different environments.</span></span> <span data-ttu-id="01209-107">Pośrednio kontenery i Docker zebrać deweloperów i operacji IT bliżej razem, ułatwiając mu współpracy.</span><span class="sxs-lookup"><span data-stu-id="01209-107">Indirectly, containers and Docker bring developers and IT operations closer together, making it easier for them to collaborate effectively.</span></span> <span data-ttu-id="01209-108">Przyjmowanie przepływu pracy kontenera zapewnia wielu klientów ciągłości DevOps zostały poszukiwane, ale wcześniej było zaimplementować za pomocą bardziej złożonych konfiguracji wydania i tworzenie potoków.</span><span class="sxs-lookup"><span data-stu-id="01209-108">Adopting the container workflow provides many customers with the DevOps continuity they've sought but previously had to implement via more complex configuration for release and build pipelines.</span></span> <span data-ttu-id="01209-109">Kontenery uprościć potoków kompilacji/Testowanie/wdrażania w DevOps.</span><span class="sxs-lookup"><span data-stu-id="01209-109">Containers simplify the build/test/deploy pipelines in DevOps.</span></span>

![](./media/image1.png)

<span data-ttu-id="01209-110">Rysunek 2 — 1: główny obciążeń na "osoby" w cyklu życia aplikacji Docker konteneryzowanych</span><span class="sxs-lookup"><span data-stu-id="01209-110">Figure 2-1: Main workloads per "personas" in the life cycle for containerized Docker applications</span></span>

<span data-ttu-id="01209-111">Z kontenerami Docker, deweloperzy własnych nowości w ramach kontenera (aplikacji i usług i zależności do struktury i składników) i kontenery i usług zachowanie razem jako składane przez kolekcję usług aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01209-111">With Docker containers, developers own what's within the container (application and service, and dependencies to frameworks and components) and how the containers and services behave together as an application composed by a collection of services.</span></span> <span data-ttu-id="01209-112">Zależnościami wielu kontenerów są definiowane w plik docker-compose.yml lub co może być nazwane *manifest rozmieszczenia*.</span><span class="sxs-lookup"><span data-stu-id="01209-112">The interdependencies of the multiple containers are defined in a docker-compose.yml file, or what could be called a *deployment manifest*.</span></span> <span data-ttu-id="01209-113">W tym samym czasie zespoły operacje IT (ZAWODOWYM informatykom i zarządzania) mogą skupić się na zarządzanie środowisk produkcyjnych; infrastruktury. skalowalność; monitorowanie; i ostatecznie zapewnienie, że aplikacje są dostarczane prawidłowo dla użytkowników końcowych, bez konieczności zawartość z różnych kontenerów.</span><span class="sxs-lookup"><span data-stu-id="01209-113">Meanwhile, IT operations teams (IT professionals and management) can focus on the management of production environments; infrastructure; scalability; monitoring; and, ultimately, ensuring that the applications are delivering properly for the end users, without having to know the contents of the various containers.</span></span> <span data-ttu-id="01209-114">W związku z tym nazwy "kontenera," odwołująca odpowiednio do kontenerów wysyłanie rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="01209-114">Hence, the name "container," recalling the analogy to real-world shipping containers.</span></span> <span data-ttu-id="01209-115">W związku z tym Właściciele zawartości kontenera nie musi dotyczyć się z sposób zostanie dostarczona kontenera i wysyłanie transportów firmy kontener z punktu pochodzenia do miejsca docelowego bez uprzedniego uzyskania informacji o lub opiekowanie dotyczące zawartości.</span><span class="sxs-lookup"><span data-stu-id="01209-115">Thus, the owners of a container's content need not concern themselves with how the container will be shipped, and the shipping company transports a container from its point of origin to its destination without knowing or caring about the contents.</span></span> <span data-ttu-id="01209-116">W podobny sposób deweloperzy można tworzyć i właścicielem treści w kontenerze Docker, bez konieczności zajmować się mechanizmów "transportu".</span><span class="sxs-lookup"><span data-stu-id="01209-116">In a similar manner, developers can create and own the contents within a Docker container without the need to concern themselves with the "transport" mechanisms.</span></span>

<span data-ttu-id="01209-117">Słupka po lewej stronie rysunku 2-1 deweloperzy pisać i wykonuje kod lokalnie w kontenerach Docker przy użyciu rozwiązania Docker dla systemu Windows lub na komputerach Mac.</span><span class="sxs-lookup"><span data-stu-id="01209-117">In the pillar on the left side of Figure 2-1, developers write and run code locally in Docker containers by using Docker for Windows or Mac.</span></span> <span data-ttu-id="01209-118">Określają one środowisku operacyjnym kodu za pomocą plik Dockerfile, który określa podstawowego systemu operacyjnego do uruchomienia, a także kroków kompilacji do tworzenia kodu ich w obrazie Docker.</span><span class="sxs-lookup"><span data-stu-id="01209-118">They define the operating environment for the code by using a Dockerfile that specifies the base operating system to run as well as the build steps for building their code into a Docker image.</span></span> <span data-ttu-id="01209-119">Deweloperzy zdefiniuj, jak jeden lub więcej obrazów mogą współdziałać, przy użyciu wyżej wymienionych *docker-compose.yml* manifest wdrażania pliku.</span><span class="sxs-lookup"><span data-stu-id="01209-119">The developers define how the one or more images will interoperate using the aforementioned *docker-compose.yml* file deployment manifest.</span></span> <span data-ttu-id="01209-120">W chwili zakończenia ich lokalne działania projektowe, ich Wypchnij ich kodu aplikacji i Docker pliki konfiguracji do repozytorium kodu wybranych przez nich (czyli repozytorium Git).</span><span class="sxs-lookup"><span data-stu-id="01209-120">As they complete their local development, they push their application code plus the Docker configuration files to the code repository of their choice (that is, Git repository).</span></span>

<span data-ttu-id="01209-121">Słupka DevOps definiuje potoki integracji (CI) kompilacji — ciągły przy użyciu plik Dockerfile w repozytorium kodu.</span><span class="sxs-lookup"><span data-stu-id="01209-121">The DevOps pillar defines the build–Continuous Integration (CI) pipelines using the Dockerfile provided in the code repository.</span></span> <span data-ttu-id="01209-122">CI system pobiera obrazy kontenera podstawowej z wybranych rejestru Docker i tworzy niestandardowe obrazy Docker dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01209-122">The CI system pulls the base container images from the selected Docker registry and builds the custom Docker images for the application.</span></span> <span data-ttu-id="01209-123">Obrazy następnie weryfikacji i przypisany do rejestru Docker używany we wdrożeniach w wielu środowiskach.</span><span class="sxs-lookup"><span data-stu-id="01209-123">The images then are validated and pushed to the Docker registry used for the deployments to multiple environments.</span></span>

<span data-ttu-id="01209-124">W słupka po prawej stronie Operacje, które zespoły Zarządzanie wdrożenie aplikacji i infrastruktury w środowisku produkcyjnym, podczas monitorowania środowiska i aplikacji, dzięki czemu zapewniają opinie i szczegółowe informacje o jak aplikacja może być zespół deweloperów Ulepszona.</span><span class="sxs-lookup"><span data-stu-id="01209-124">In the pillar on the right, operations teams manage deployed applications and infrastructure in production while monitoring the environment and applications so that they can provide feedback and insights to the development team about how the application might be improved.</span></span> <span data-ttu-id="01209-125">Aplikacje kontenera są zazwyczaj uruchamiane w środowisku produkcyjnym za pomocą orchestrators kontenera.</span><span class="sxs-lookup"><span data-stu-id="01209-125">Container apps are typically run in production using container orchestrators.</span></span>

<span data-ttu-id="01209-126">Dwóch zespołach współpracują za pośrednictwem podstawowych platforma (kontenery Docker), która zapewnia separacji jako kontraktu, podczas znacznie poprawia dwóch zespołach współpraca w cyklu życia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="01209-126">The two teams are collaborating through a foundational platform (Docker containers) that provides a separation of concerns as a contract, while greatly improving the two teams' collaboration in the application life cycle.</span></span> <span data-ttu-id="01209-127">Deweloperzy właścicielem zawartości kontenera, jego środowisku operacyjnym i zależnościami kontenera zespołów operacyjnych zająć obrazów zbudowanych wraz z manifestu i uruchamia je w ich systemie aranżacji.</span><span class="sxs-lookup"><span data-stu-id="01209-127">The developers own the container contents, its operating environment, and the container interdependencies, whereas the operations teams take the built images along with the manifest and runs them in their orchestration system.</span></span>

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a><span data-ttu-id="01209-128">Wprowadzenie do ogólnego przepływu cyklu życia aplikacji Docker end-to-end</span><span class="sxs-lookup"><span data-stu-id="01209-128">Introduction to a generic end-to-end Docker application life cycle workflow</span></span>

<span data-ttu-id="01209-129">Rysunek 2-2 przedstawia bardziej szczegółowy przepływ pracy dla cyklu życia aplikacji Docker koncentrujących się w tym wystąpieniu na konkretne działania DevOps i zasoby.</span><span class="sxs-lookup"><span data-stu-id="01209-129">Figure 2-2 presents a more detailed workflow for a Docker application life cycle, focusing in this instance on specific DevOps activities and assets.</span></span>

![](./media/image2.png)

<span data-ttu-id="01209-130">Rysunek 2-2: ogólny przepływ pracy Docker konteneryzowanych cyklu życia aplikacji</span><span class="sxs-lookup"><span data-stu-id="01209-130">Figure 2-2: High-level workflow for the Docker containerized application life cycle</span></span>

<span data-ttu-id="01209-131">Wszystko, co rozpoczyna się od projektanta, który rozpoczyna się pisanie kodu w przepływie pracy wewnętrzny pętli.</span><span class="sxs-lookup"><span data-stu-id="01209-131">Everything begins with the developer, who starts writing code in the inner-loop workflow.</span></span> <span data-ttu-id="01209-132">Etap wewnętrzny pętli to, gdy deweloperzy zdefiniuj wszystko, co się stanie, przed wypchnięciem kod do repozytorium kodu (na przykład systemu kontroli źródła np. Git).</span><span class="sxs-lookup"><span data-stu-id="01209-132">The inner-loop stage is where developers define everything that happens before pushing code into the code repository (for example, a source control system such as Git).</span></span> <span data-ttu-id="01209-133">Po zobowiązuje się repozytorium wyzwala ciągłej integracji (CI) i pozostałej części przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="01209-133">After it is committed, the repository triggers Continuous Integration (CI) and the rest of the workflow.</span></span>

<span data-ttu-id="01209-134">Fragment pętli zasadniczo składa się z typowe etapy, takich jak 'code' "," "test", "debug", a także dodatkowe kroki bezpośrednio przed uruchomieniem uruchomić aplikację lokalnie.</span><span class="sxs-lookup"><span data-stu-id="01209-134">The inner loop basically consists of typical steps like "code," "run," "test," and "debug," plus additional steps directly before running the app locally.</span></span> <span data-ttu-id="01209-135">Jest to, gdy dewelopera testów aplikacji jako kontener Docker.</span><span class="sxs-lookup"><span data-stu-id="01209-135">This is when the developer runs and tests the app as a Docker container.</span></span> <span data-ttu-id="01209-136">W poniższych sekcjach opisano pętli wewnętrzny przepływ pracy.</span><span class="sxs-lookup"><span data-stu-id="01209-136">The inner-loop workflow will be explained in the sections that follow.</span></span>

<span data-ttu-id="01209-137">Odebraniem krok aby przyjrzeć się przepływu pracy — do zakończenia, metodyki DevOps przepływu pracy jest większa niż technologii lub zestawu narzędzi: jest mindset, wymagającego ewolucji kultury.</span><span class="sxs-lookup"><span data-stu-id="01209-137">Taking a step back to look at the end-to end workflow, the DevOps workflow is more than a technology or a tool set: it's a mindset that requires cultural evolution.</span></span> <span data-ttu-id="01209-138">Jest osób, procesów i odpowiednie narzędzia, aby cyklu życia aplikacji szybsze i bardziej przewidywalne.</span><span class="sxs-lookup"><span data-stu-id="01209-138">It is people, processes, and the appropriate tools to make your application life cycle faster and more predictable.</span></span> <span data-ttu-id="01209-139">Przedsiębiorstw, które przyjmują konteneryzowanych przepływu pracy zwykle restrukturyzacji organizacji do reprezentowania osoby i procesy, które spełniają konteneryzowanych przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="01209-139">Enterprises that adopt a containerized workflow typically restructure their organizations to represent people and processes that match the containerized workflow.</span></span>

<span data-ttu-id="01209-140">Ćwiczenia opracowywania oprogramowania może pomóc zespoły uwzględniał szybciej razem nacisk konkurencji przez zamianę procesów ręcznych podatnych automatyzacji, co powoduje ulepszona możliwość śledzenia i powtarzalne przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="01209-140">Practicing DevOps can help teams respond faster together to competitive pressures by replacing error-prone manual processes with automation, which results in improved traceability and repeatable workflows.</span></span> <span data-ttu-id="01209-141">Organizacje można również efektywniej zarządzać środowiskami i osiągnięcia oszczędności z kombinacją lokalnych i dostępnych zasobów w chmurze, a także ściśle zintegrowane narzędzia.</span><span class="sxs-lookup"><span data-stu-id="01209-141">Organizations also can manage environments more efficiently and realize cost savings with a combination of on-premises and cloud resources as well as tightly integrated tooling.</span></span>

<span data-ttu-id="01209-142">Podczas wykonywania przepływu pracy opracowywania oprogramowania dla aplikacji Docker, zobaczysz, że technologie Docker na znajdują się w niemal każdego etapu przepływu pracy, z Twojego pola programowanie podczas pracy w pętli wewnętrzny (code, uruchamianie, debugowania), do fazy kompilacji test-CI i, Oczywiście w produkcyjne i przejściowe środowisk i wdrażanie kontenerów do tych środowisk.</span><span class="sxs-lookup"><span data-stu-id="01209-142">When implementing your DevOps workflow for Docker applications, you'll see that Docker's technologies are present in almost every stage of the workflow, from your development box while working in the inner loop (code, run, debug), to the build-test-CI phase, and, of course, at the production and staging environments and when deploying your containers to those environments.</span></span>

<span data-ttu-id="01209-143">Poprawa jakości rozwiązania pomaga w identyfikacji wady wczesnym etapie cyklu projektowania, co zmniejsza koszty ich rozwiązywania.</span><span class="sxs-lookup"><span data-stu-id="01209-143">Improvement of quality practices helps to identify defects early in the development cycle, which reduces the cost of fixing them.</span></span> <span data-ttu-id="01209-144">W tym środowisku i zależności w obrazie i przyjęcia zasady wdrażania ten sam obraz w wielu środowiskach, podwyższyć poziom dyscypliny wyodrębniania konfiguracje specyficzne dla środowiska wprowadzania wdrożeń bardziej niezawodne.</span><span class="sxs-lookup"><span data-stu-id="01209-144">By including the environment and dependencies in the image and adopting a philosophy of deploying the same image across multiple environments, you promote a discipline of extracting the environment-specific configurations making deployments more reliable.</span></span>

<span data-ttu-id="01209-145">Zaawansowanych danych uzyskanych przy użyciu Instrumentacji skuteczne (monitorowania i diagnostyki) zapewnia wgląd w problemy z wydajnością i zachowania użytkowników prowadzące przyszłych priorytetów i inwestycji.</span><span class="sxs-lookup"><span data-stu-id="01209-145">Rich data obtained through effective instrumentation (monitoring and diagnostics) provides insight into performance issues and user behavior to guide future priorities and investments.</span></span>

<span data-ttu-id="01209-146">Należy rozważyć DevOps podróży, a nie miejsca docelowego.</span><span class="sxs-lookup"><span data-stu-id="01209-146">DevOps should be considered a journey, not a destination.</span></span> <span data-ttu-id="01209-147">Powinien on implementowane przyrostowo za pośrednictwem odpowiednio zakresie projektów, z których można pokazują sukces, Dowiedz się więcej i rozwijać.</span><span class="sxs-lookup"><span data-stu-id="01209-147">It should be implemented incrementally through appropriately scoped projects from which you can demonstrate success, learn, and evolve.</span></span>

## <a name="benefits-of-devops-for-containerized-applications"></a><span data-ttu-id="01209-148">Zalety opracowywania oprogramowania dla aplikacji konteneryzowanych</span><span class="sxs-lookup"><span data-stu-id="01209-148">Benefits of DevOps for containerized applications</span></span>

<span data-ttu-id="01209-149">Oto niektóre z najważniejszych zalet stałe DevOps przepływu pracy:</span><span class="sxs-lookup"><span data-stu-id="01209-149">Here are some of the most important benefits provided by a solid DevOps workflow:</span></span>

-   <span data-ttu-id="01209-150">Dostarczanie oprogramowania lepszą jakość szybsze i lepszą zgodność</span><span class="sxs-lookup"><span data-stu-id="01209-150">Deliver better-quality software, faster and with better compliance</span></span>

-   <span data-ttu-id="01209-151">Poprawa ciągłych i dostosowania dysków wcześniej i bardziej ekonomicznego</span><span class="sxs-lookup"><span data-stu-id="01209-151">Drive continuous improvement and adjustments earlier and more economically</span></span>

-   <span data-ttu-id="01209-152">Zwiększenia przejrzystości i współpracę uczestników objętego dostarczania i obsługi oprogramowania</span><span class="sxs-lookup"><span data-stu-id="01209-152">Increase transparency and collaboration among stakeholders involved in delivering and operating software</span></span>

-   <span data-ttu-id="01209-153">Kontrolę kosztów i wykorzystania zasobów elastycznie efektywniej przy jednoczesnym zmniejszeniu zagrożenia bezpieczeństwa</span><span class="sxs-lookup"><span data-stu-id="01209-153">Control costs and utilize provisioned resources more effectively while minimizing security risks</span></span>

-   <span data-ttu-id="01209-154">Plug and play również z wieloma dotychczasowych inwestycji DevOps, w tym inwestycji w typu open source</span><span class="sxs-lookup"><span data-stu-id="01209-154">Plug and play well with many of your existing DevOps investments, including investments in open source</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="01209-155">[Poprzednie] (index.md) [dalej] (.. /Microsoft-Platform-Tools-containerized-Apps/index.MD)</span><span class="sxs-lookup"><span data-stu-id="01209-155">[Previous] (index.md) [Next] (../Microsoft-platform-tools-containerized-apps/index.md)</span></span>