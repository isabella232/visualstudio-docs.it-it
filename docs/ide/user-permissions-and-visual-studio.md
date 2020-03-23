---
title: Esegui come amministratore
ms.date: 01/06/2020
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 927031b4755644aeac553367a4f8a08faa0c0992
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75718636"
---
# <a name="user-permissions-and-visual-studio"></a>Autorizzazioni utente e Visual Studio

Per motivi di sicurezza, è consigliabile eseguire Visual Studio come utente tipico quando possibile.

> [!WARNING]
> Accertarsi inoltre di non compilare, avviare o eseguire il debug di una soluzione di Visual Studio che non provenga da una persona o un percorso attendibile.

È possibile eseguire quasi tutte le operazioni nell'IDE di Visual Studio come utente tipico. Sono necessarie autorizzazioni di amministratore per completare le attività seguenti:

|Area|Attività|Per ulteriori informazioni|
|----------|----------| - |
|Installazione|Installare o modificare Visual Studio.Install or modify Visual Studio.|[Installare Visual Studio,](../install/install-visual-studio.md) [Modificare Visual Studio](../install/modify-visual-studio.md)|
||Installare, aggiornare o rimuovere contenuto della Guida locale.|[Installare e gestire il contenuto della Guida locale](../help-viewer/install-manage-local-content.md)|
|Casella degli strumenti|Aggiungere controlli COM classici alla **casella degli strumenti**.|[Casella degli strumenti](../ide/reference/toolbox.md)|
|Compilazione|Usare eventi di post-compilazione che registrano un componente.|[Informazioni sulle istruzioni di compilazione personalizzate e sugli eventi di compilazione](/cpp/build/understanding-custom-build-steps-and-build-events)|
||Includere un passaggio di registrazione al momento della compilazione di progetti C++.||
|Debug|Eseguire il debug di applicazioni eseguite con autorizzazioni elevate.|[Impostazioni del debugger e preparazione](../debugger/debugger-settings-and-preparation.md)|
||Eseguire il debug di applicazioni eseguite con un account utente diverso, come i siti Web ASP.NET.|[Eseguire il debug di applicazioni ASP.NET e AJAX](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||Eseguire il debug nell'area di sicurezza per applicazioni browser XAML (XBAP).|[Host WPF (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Usare l'emulatore per eseguire il debug di progetti del servizio cloud per Microsoft Azure.|[Debug di un servizio cloud in Visual Studio](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Configurare un firewall per il debug remoto.|[Debug remoto](../debugger/remote-debugging.md)|
|Strumenti per le prestazioni|Connessione a un'applicazione con privilegi elevati.|[Guida per i principianti alla profilazione delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md)|
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
