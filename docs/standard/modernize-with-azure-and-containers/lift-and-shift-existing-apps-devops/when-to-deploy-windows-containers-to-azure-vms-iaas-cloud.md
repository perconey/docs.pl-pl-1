---
title: "Kiedy należy wdrożyć kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Kiedy należy wdrożyć kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 37a37f91bb910004128c96511f585bea03a51d3a
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Kiedy należy wdrożyć kontenery systemu Windows na maszynach wirtualnych platformy Azure (IaaS w chmurze)

Jeśli organizacja używa maszynach wirtualnych platformy Azure, nawet jeśli używana jest również kontenery systemu Windows, to nadal zajmowanie IaaS. Oznacza to tej obsłudze operacje infrastruktury, poprawek systemu operacyjnego maszyny Wirtualnej i złożoności infrastruktury dla aplikacji o wysokiej skalowalności gdy należy wdrożyć na wiele maszyn wirtualnych w infrastrukturze równoważeniem obciążenia. Główne scenariusze przy użyciu kontenery systemu Windows w maszynie Wirtualnej platformy Azure są:

-   **Tworzenie/testowanie środowiska**: A maszyna wirtualna w chmurze jest idealne w przypadku projektowania i testowania w chmurze. Można szybko utworzyć lub Zatrzymaj środowisko, w zależności od potrzeb.

-   **Skalowalność małych i średnich musi**: W scenariuszach, w którym mogą być wymagane kilka maszyn wirtualnych do środowiska produkcyjnego, zarządzanie niewielkiej liczby maszyn wirtualnych może być ekonomiczny dopóki nie można przenieść do bardziej zaawansowanych środowisk PaaS, takich jak orchestrators.

-   **Środowisku produkcyjnym z użyciem istniejących narzędzi wdrażania**: użytkownik może przenoszenie ze środowiska lokalnego, w którym zainwestowały w menu Narzędzia, aby złożone wdrożenia maszyn wirtualnych i serwery bez systemu operacyjnego (na przykład Puppet lub podobne narzędzia). Można przenieść do chmury przy minimalnych zmianach do procedur wdrażania środowiska produkcyjnego, można nadal używać tych narzędzi do wdrażania na maszynach wirtualnych platformy Azure. Jednak należy używanie kontenerów Windows jednostką wdrożenia celu usprawnienie obsługi wdrożenia.

>[!div class="step-by-step"]
[Poprzednie](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
[dalej](when-to-deploy-windows-containers-to-service-fabric.md)
