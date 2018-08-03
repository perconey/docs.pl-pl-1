---
title: 'Zainstaluj język F #'
description: 'Dowiedz się, jak zainstalować zależności od używanego środowiska F #.'
ms.date: 07/03/2018
ms.openlocfilehash: 142265a95e1d3ee1603a89f650a24c6a45709181
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37878771"
---
# <a name="install-f"></a>Zainstaluj język F # #

Można zainstalować F # na wiele sposobów, w zależności od środowiska.

## <a name="install-f-with-visual-studio"></a>Instalowanie języka F # za pomocą programu Visual Studio

Jeśli masz pobieranie [programu Visual Studio](https://visualstudio.microsoft.com/) po raz pierwszy zostanie najpierw zainstalować Instalatora programu Visual Studio. Zainstaluj odpowiednie jednostki SKU programu Visual Studio z poziomu Instalatora. Jeśli masz już zainstalowany, kliknij przycisk **Modyfikuj**.

Następnie zobaczysz listę obciążeń. Wybierz **ASP.NET i tworzenie aplikacji internetowych**, którego zostanie zainstalowana obsługa języka F #, Obsługa platformy .NET Core oraz projekty F # — Obsługa platformy ASP.NET Core.

Następnie kliknij przycisk **Modyfikuj** w dolnym po prawej stronie.  Spowoduje to zainstalowanie wszystko, co jest wybrane. Następnie możesz otworzyć programu Visual Studio 2017 z obsługą języka F #, klikając **Uruchom**.

## <a name="install-f-with-visual-studio-for-mac"></a>Zainstaluj język F # za pomocą programu Visual Studio dla komputerów Mac

F # jest instalowany domyślnie w [programu Visual Studio dla komputerów Mac](https://visualstudio.microsoft.com/vs/mac/), niezależnie od tego, jaka konfiguracja wybierzesz.

Po zakończeniu instalacji wybierz pozycję "Uruchom Visual Studio". Można również uruchomić go za pomocą wyszukiwania w systemie macOS.

## <a name="install-f-with-visual-studio-code"></a>Instalowanie języka F # za pomocą programu Visual Studio Code

Konieczne jest posiadanie [zainstalowane narzędzie git](https://git-scm.com/download) i dostępne w zmiennej PATH, aby korzystanie z szablonów projektów w Ionide. Możesz sprawdzić, czy jest poprawnie zainstalowany, wpisując `git --version` w wierszu polecenia i naciskając klawisz **Enter**.

### <a name="macostabmacos"></a>[macOS](#tab/macos)

Używa Ionide [Mono](http://www.mono-project.com). Najprostszym sposobem zainstalowania platformy Mono w systemie macOS jest za pośrednictwem Homebrew. Po prostu wpisz następujące polecenie w terminalu:

```console
brew install mono
```

Należy również zainstalować [zestawu .NET Core SDK](https://www.microsoft.com/net/download).

### <a name="linuxtablinux"></a>[Linux](#tab/linux)

W systemie Linux, używa również Ionide [Mono](https://www.mono-project.com). W przypadku systemie Debian lub Ubuntu, można użyć następujących czynności:

```console
sudo apt-get update
sudo apt-get install mono-complete fsharp
```

Należy również zainstalować [zestawu .NET Core SDK](https://www.microsoft.com/net/download).

### <a name="windowstabwindows"></a>[Windows](#tab/windows)

Jeśli używasz Windows, musisz najpierw [instalacji programu Visual Studio z obsługą języka F #](#install-f-with-visual-studio). Spowoduje to zainstalowanie wszystkich składników niezbędnych do zapisu, skompilowania i wykonania kodu F #.

Należy również zainstalować [zestawu .NET Core SDK](https://www.microsoft.com/net/download/).

---

Następnie należy [programu Visual Studio Code](https://code.visualstudio.com) zainstalowane.

Następnie kliknij ikonę rozszerzenia i poszukaj pozycji "Ionide":

Tylko dodatek typu plug-in, wymagana jest obsługa języka F # w programie Visual Studio Code [Ionide fsharp](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-fsharp). Jednakże można także zainstalować [SFAŁSZOWANA Ionide](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-FAKE) można pobrać [FAŁSZYWE](https://fsharp.github.io/FAKE/) pomocy technicznej i [Ionide Paket](https://marketplace.visualstudio.com/items?itemName=Ionide.Ionide-Paket) można pobrać [Paket](https://fsprojects.github.io/Paket/) pomocy technicznej. FAŁSZYWE i Paket dodatkowych narzędzi społeczności F # do kompilowania projektów i zarządzanie zależnościami, odpowiednio.