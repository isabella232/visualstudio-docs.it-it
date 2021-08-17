---
title: Esegui come amministratore
description: Informazioni su come eseguire Visual Studio come amministratore.
ms.date: 03/09/2021
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 03338da39eb9be3d080839c4c0cd567e3162da7e871bb449f08242c49eed6f5a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386615"
---
# <a name="user-permissions-and-visual-studio"></a>Autorizzazioni utente e Visual Studio

Per motivi di sicurezza, è consigliabile eseguire Visual Studio come utente tipico quando possibile.

> [!WARNING]
> Accertarsi inoltre di non compilare, avviare o eseguire il debug di una soluzione di Visual Studio che non provenga da una persona o un percorso attendibile.

È possibile eseguire quasi tutte le attività nell'IDE Visual Studio come utente tipico. Sono necessarie autorizzazioni di amministratore per completare le attività seguenti:

|Area|Attività|Per ulteriori informazioni|
|----------|----------| - |
|Installazione|Installare o modificare Visual Studio.|[Installare Visual Studio](../install/install-visual-studio.md), [Modificare Visual Studio](../install/modify-visual-studio.md)|
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

1. Dal menu di scelta rapida o dal menu di scelta rapida Visual Studio **2017,** selezionare **Altro** > **Esegui come amministratore**.

   All'avvio di Visual Studio, viene visualizzato **(Amministratore)** dopo il nome del prodotto nella barra del titolo.

::: moniker-end

::: moniker range=">=vs-2019"

1. Aprire il menu **Start** e scorrere fino Visual Studio 2019.

1. Dal menu di scelta rapida o dal menu di scelta rapida Visual Studio **2019,** selezionare **Altro** > **Esegui come amministratore**.

   All'avvio di Visual Studio, viene visualizzato **(Amministratore)** dopo il nome del prodotto nella barra del titolo.

::: moniker-end

È anche possibile modificare il collegamento all'applicazione in modo che sia sempre eseguito con autorizzazioni amministrative:

1. Aprire il menu **Start,** scorrere fino alla versione del Visual Studio in uso e quindi selezionare **Altro**  >  **percorso file aperto**.

1. In **Esplora file** individuare il **Visual Studio** collegamento per la versione in uso. Fare quindi clic con il pulsante destro del mouse sul collegamento e scegliere **Invia al**  >  **desktop (crea collegamento)**.

1. Nel desktop **Windows** fare clic con  il pulsante destro del mouse sul collegamento Visual Studio e quindi scegliere **Proprietà**.

1. Selezionare il **pulsante** Avanzate e quindi selezionare la **casella di controllo Esegui** come amministratore.

1. Selezionare **OK** e quindi di nuovo **OK**.

## <a name="see-also"></a>Vedi anche

- [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Installa Visual Studio](../install/install-visual-studio.md)
