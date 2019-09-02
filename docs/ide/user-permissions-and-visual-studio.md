---
title: Esegui come amministratore
ms.date: 06/05/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 97ecddfa317eb522a8ce29a53482df5581912dad
ms.sourcegitcommit: 673b9364fc9a96b027662dcb4cf5d61cab60ef11
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/21/2019
ms.locfileid: "69891237"
---
# <a name="user-permissions-and-visual-studio"></a>Autorizzazioni utente e Visual Studio

Per motivi di sicurezza, è consigliabile eseguire Visual Studio come utente normale ogni volta che ciò è possibile.

> [!WARNING]
> Accertarsi inoltre di non compilare, avviare o eseguire il debug di una soluzione di Visual Studio che non provenga da una persona o un percorso attendibile.

Un account utente normale consente di possibile eseguire quasi tutte le funzioni dell'IDE di Visual Studio. Sono necessarie autorizzazioni di amministratore per completare le attività seguenti:

|Area|Attività|Per altre informazioni|
|----------|----------| - |
|Installazione|Installare Visual Studio.|[Installare Visual Studio](../install/install-visual-studio.md)|
||Installare, aggiornare o rimuovere contenuto della Guida locale.|[Installare e gestire il contenuto della Guida locale](../help-viewer/install-manage-local-content.md)|
|Casella degli strumenti|Aggiungere controlli COM classici alla **casella degli strumenti**.|[Casella degli strumenti](../ide/reference/toolbox.md)|
|Compilazione|Usare eventi di post-compilazione che registrano un componente.|[Informazioni sulle istruzioni di compilazione personalizzate e sugli eventi di compilazione](/cpp/build/understanding-custom-build-steps-and-build-events)|
||Includere un passaggio di registrazione al momento della compilazione di progetti C++.||
|Debug|Eseguire il debug di applicazioni eseguite con autorizzazioni elevate.|[Impostazioni del debugger e preparazione](../debugger/debugger-settings-and-preparation.md)|
||Eseguire il debug di applicazioni eseguite con un account utente diverso, come i siti Web ASP.NET.|[Eseguire il debug di applicazioni ASP.NET e AJAX](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||Eseguire il debug nell'area di sicurezza per applicazioni browser XAML (XBAP).|[Host WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Usare l'emulatore per eseguire il debug di progetti del servizio cloud per Microsoft Azure.|[Debug di un servizio cloud in Visual Studio](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Configurare un firewall per il debug remoto.|[Debug remoto](../debugger/remote-debugging.md)|
|Strumenti per le prestazioni|Connessione a un'applicazione con privilegi elevati.|[Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md)|
||Usare il profiler GPU.|[Profilatura GPU](../profiling/gpu-usage.md)|
|Distribuzione|Distribuire un'applicazione Web a Internet Information Services (IIS) in un computer locale.|[Distribuire un'app Web ASP.NET con Visual Studio](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Eseguire Visual Studio come amministratore

Se è necessario eseguire Visual Studio come amministratore, seguire questa procedura per aprire l'IDE:

> [!NOTE]
> Queste istruzioni sono relative a Windows 10. Sono simili per le altre versioni di Windows.

::: moniker range="vs-2017"

1. Aprire il menu **Start** e scorrere fino Visual Studio 2017.

1. Dal menu di scelta rapida o contestuale di **Visual Studio 2017** scegliere **Altro** > **Esegui come amministratore**.

   All'avvio di Visual Studio, viene visualizzato **(Amministratore)** dopo il nome del prodotto nella barra del titolo.

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire il menu **Start** e scorrere fino Visual Studio 2019.

1. Dal menu di scelta rapida o contestuale di **Visual Studio 2019** scegliere **Altro** > **Esegui come amministratore**.

   All'avvio di Visual Studio, viene visualizzato **(Amministratore)** dopo il nome del prodotto nella barra del titolo.

::: moniker-end

È anche possibile modificare il collegamento dell'applicazione per eseguirla sempre con autorizzazioni amministrative.

## <a name="see-also"></a>Vedere anche

- [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Installare Visual Studio](../install/install-visual-studio.md)