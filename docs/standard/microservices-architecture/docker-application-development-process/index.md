---
title: Aplikacje oparte na proces Docker
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Aplikacje oparte na proces Docker"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 97dfa3261c8ddc7a869b0991673b7a8d298972dd
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="35999-104">Proces tworzenia aplikacji opartych na Docker</span><span class="sxs-lookup"><span data-stu-id="35999-104">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="35999-105">*Opracowywanie konteneryzowanych aplikacji .NET lubisz, IDE fokus z programu Visual Studio i narzędzi Visual Studio tools for Docker lub interfejsu wiersza polecenia/Edytor fokus z interfejsu wiersza polecenia Docker i Visual Studio Code.*</span><span class="sxs-lookup"><span data-stu-id="35999-105">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="35999-106">Środowisko projektowe dla aplikacji Docker</span><span class="sxs-lookup"><span data-stu-id="35999-106">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="35999-107">Opcje narzędzia opracowywania: IDE lub edytora</span><span class="sxs-lookup"><span data-stu-id="35999-107">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="35999-108">Czy wolisz pełne i wydajne środowiska IDE lub edytora nieskomplikowane i elastyczne, firma Microsoft udostępnia narzędzia, które służą do tworzenia aplikacji platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="35999-108">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="35999-109">**Visual Studio (dla systemu Windows)**.</span><span class="sxs-lookup"><span data-stu-id="35999-109">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="35999-110">Do tworzenia aplikacji opartych na Docker, użyj programu Visual Studio 2017 lub nowsze wersje, które jest dostarczany z tools for Docker już wbudowanych.</span><span class="sxs-lookup"><span data-stu-id="35999-110">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="35999-111">Tools for Docker umożliwiają tworzenie, uruchamianie i sprawdzanie poprawności aplikacji bezpośrednio w środowisku docelowym Docker.</span><span class="sxs-lookup"><span data-stu-id="35999-111">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="35999-112">Naciśnij klawisz F5, aby uruchomić i debugowania aplikacji (jeden kontener lub wielu kontenerów) bezpośrednio do hostów Docker lub naciśnij klawisze CTRL + F5, edytowanie i odświeżanie aplikacji bez konieczności odbudować kontenera.</span><span class="sxs-lookup"><span data-stu-id="35999-112">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="35999-113">Jest to najbardziej zaawansowanych wybór programowanie dla aplikacji opartych na Docker.</span><span class="sxs-lookup"><span data-stu-id="35999-113">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="35999-114">**Visual Studio for Mac**.</span><span class="sxs-lookup"><span data-stu-id="35999-114">**Visual Studio for Mac**.</span></span> <span data-ttu-id="35999-115">Jest IDE ewolucja platformy Xamarin Studio uruchomionym w macOS i obsługuje tworzenie aplikacji opartej na Docker.</span><span class="sxs-lookup"><span data-stu-id="35999-115">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="35999-116">Powinno to być preferowany wybór dla deweloperów pracujących w komputerach Mac, również chcą korzystać z zaawansowanych IDE.</span><span class="sxs-lookup"><span data-stu-id="35999-116">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="35999-117">**Visual Studio Code i Docker CLI**.</span><span class="sxs-lookup"><span data-stu-id="35999-117">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="35999-118">Jeśli wolisz nieskomplikowane i Międzyplatformowe edytorze, który obsługuje dowolnego języka programowania, można użyć programu Microsoft Visual Studio (kod VS) i interfejsu wiersza polecenia Docker.</span><span class="sxs-lookup"><span data-stu-id="35999-118">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="35999-119">To podejście wiele platform dla komputerów Mac, Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="35999-119">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="35999-120">Instalując [Docker Community Edition (CE)](https://www.docker.com/community-edition) narzędzi, można użyć jednego interfejsu wiersza polecenia Docker umożliwia tworzenie aplikacji dla systemu Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="35999-120">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="35999-121">Ponadto program Visual Studio Code obsługuje rozszerzenia Docker, takie jak IntelliSense dla zadań Dockerfiles i skrót do uruchamiania polecenia Docker w edytorze.</span><span class="sxs-lookup"><span data-stu-id="35999-121">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="35999-122">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="35999-122">Additional resources</span></span>

-   <span data-ttu-id="35999-123">**Visual Studio Tools for Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="35999-123">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="35999-124">**Visual Studio Code**.</span><span class="sxs-lookup"><span data-stu-id="35999-124">**Visual Studio Code**.</span></span> <span data-ttu-id="35999-125">Oficjalna witryna.</span><span class="sxs-lookup"><span data-stu-id="35999-125">Official site.</span></span>
    [<span data-ttu-id="35999-126">*https://code.VisualStudio.com/download*</span><span class="sxs-lookup"><span data-stu-id="35999-126">*https://code.visualstudio.com/download*</span></span>](https://code.visualstudio.com/download)

-   <span data-ttu-id="35999-127">**Docker Community Edition (CE) dla systemów Mac i systemu Windows**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="35999-127">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="35999-128">.NET języków i struktur dla kontenerów Docker</span><span class="sxs-lookup"><span data-stu-id="35999-128">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="35999-129">Jak wspomniano we wcześniejszych sekcjach tego przewodnika, można użyć .NET Framework .NET Core i Mono projekt open source podczas opracowywania Docker konteneryzowanych aplikacji .NET.</span><span class="sxs-lookup"><span data-stu-id="35999-129">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="35999-130">Można tworzyć w języku C\#, F\#, lub Visual Basic, jeśli Linux lub kontenery systemu Windows, w zależności od tego, które .NET framework jest używana.</span><span class="sxs-lookup"><span data-stu-id="35999-130">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="35999-131">W przypadku języków about.NET więcej szczegółów, zobacz wpis w blogu [strategii języka .NET](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span><span class="sxs-lookup"><span data-stu-id="35999-131">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="35999-132">[Poprzednie] (.. / architect-microservice-container-applications/using-azure-service-fabric.md) [dalej] (docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="35999-132">[Previous] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)</span></span>