---
title: Migrowanie do scenariuszy hybrydowych chmury
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Migrowanie do scenariuszy hybrydowych chmury"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/2/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6216068786745ac4ebc00263a14b4afe247193f5
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
---
# <a name="migrate-to-hybrid-cloud-scenarios"></a>Migrowanie do scenariuszy hybrydowych chmury

Niektóre organizacje i przedsiębiorstwa nie może przeprowadzić migracji niektórych aplikacji do chmur publicznych, takich jak Microsoft Azure lub innych chmur publicznych ze względu na przepisy lub ich własnych zasad. Istnieje prawdopodobieństwo, że każda organizacja może korzystać z o niektórych aplikacji w chmurze publicznej i innych aplikacji lokalnych. Ale środowisku mieszanym może prowadzić do nadmiernej złożoności w środowiskach z powodu różnych platform i technologii używanych w chmur publicznych i lokalnych środowisk.

Firma Microsoft udostępnia najlepsze rozwiązanie chmury hybrydowej, jeden, w którym można zoptymalizować istniejących zasobów lokalnych i w chmurze publicznej, gdy zapewnienia spójności w chmurze hybrydowe platformy Azure. Można zmaksymalizować posiadane umiejętności i uzyskać elastyczną i ujednoliconego podejście do tworzenia aplikacji, które można uruchomić w chmurze lub lokalnie, dzięki użyciu stosu Azure (lokalnego) i Azure (w chmurze publicznej).

Jeśli chodzi o zabezpieczeń, można scentralizować zarządzania i bezpieczeństwo w chmurze hybrydowej. Możesz uzyskać kontrolę nad wszystkie zasoby z centrum danych w chmurze, zapewniając rejestracji jednokrotnej do lokalnego i aplikacji w chmurze. Można to zrobić przez rozszerzenie usługi Active Directory do chmury hybrydowej i za pomocą zarządzania tożsamościami.

Na koniec można dystrybuować i bezproblemowo analizowanie danych, użyj te same języki zapytania dla zasobów w chmurze i lokalnie i stosować analizy i bezpośrednie learning na platformie Azure wzbogacić, niezależnie od tego źródła danych.

## <a name="azure-stack"></a>Azure Stack

Stos Azure jest hybrydowe platformy w chmurze, który pozwala dostarczyć usług platformy Azure z centrum danych w organizacji. Stos Azure umożliwia obsługę nowych opcji dla nowoczesnych aplikacji w różnych kluczowych scenariuszy, takich jak edge i środowisk odłączony lub spotkania szczególne wymagania zabezpieczeń i zgodności.

Rysunek 4-13 przedstawiono przegląd platformy chmury hybrydowego wartość true, które firma Microsoft oferuje.

![Platforma firmy Microsoft hybrydowego chmurze ze stosu Azure i na platformie Azure](./media/image13.jpg)

> **Rysunek 4-13.** Platforma firmy Microsoft hybrydowego chmurze ze stosu Azure i na platformie Azure

Azure stosu jest oferowany dwie opcje wdrażania, dostosowane do potrzeb:

-   Stos Azure zintegrowanych systemów

-   Azure stosu Development Kit

### <a name="azure-stack-integrated-systems"></a>Stos Azure zintegrowanych systemów

Azure stosu zintegrowanych systemów są oferowane przez powiązanie partnerów firmy Microsoft i sprzętu. Powiązanie tworzy rozwiązania, które oferuje innowacje realizowanych chmury na konto uproszczenie procesu zarządzania. Ponieważ stos Azure jest oferowany jako zintegrowany system sprzętu i oprogramowania, należy pobrać jednostkom elastyczność i kontroli, podczas nadal przyjmowanie innowacji z chmury. Azure stosu zintegrowanych systemów należeć do zakresu o rozmiarze od 4 do 12 węzłów i wspólnie są obsługiwane przez partnera sprzętu i firmy Microsoft. Użycie stosu Azure zintegrowanych systemów do zaimplementowania nowych scenariuszy dla obciążeń produkcyjnych.

### <a name="azure-stack-development-kit"></a>Azure stosu Development Kit

Microsoft Azure stosu Development Kit to wdrożenie jednowęzłowej stosu Azure, której można użyć do oceny i Dowiedz się więcej o stosu Azure. Umożliwia także zestaw deweloperski stosu Azure jako Środowisko deweloperskie, w którym można tworzyć przy użyciu interfejsów API i narzędzi, które są zgodne z platformy Azure. Azure stosu Development Kit nie jest przeznaczony do użycia jako środowiska produkcyjnego.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Chmura hybrydowa Azure**

    [https://www.microsoft.com/cloud-platform/hybrid-cloud](https://www.microsoft.com/cloud-platform/hybrid-cloud)

-   **Azure Stack**

    [https://azure.microsoft.com/overview/azure-stack/](https://azure.microsoft.com/overview/azure-stack/)

-   **Konta usługi Active Directory dla Windows kontenerów**

    [https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/manage-serviceaccounts)

-   **Tworzenie kontenera z obsługą usługi Active Directory**

    [https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/](https://blogs.msdn.microsoft.com/containerstuff/2017/01/30/create-a-container-with-active-directory-support/)

-   **Azure licencjonowania korzyści hybrydowego**

    [https://azure.microsoft.com/pricing/hybrid-use-benefit/](https://azure.microsoft.com/pricing/hybrid-use-benefit/)

>[!div class="step-by-step"]
[Poprzednie](modernize-your-apps-lifecycle-with-ci-cd-pipelines-and-devops-tools-in-the-cloud.md)
[dalej](../walkthroughs-technical-get-started-overview.md)
