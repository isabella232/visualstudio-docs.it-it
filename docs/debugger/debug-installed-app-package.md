---
title: Eseguire il debug di un pacchetto di app UWP installato | Microsoft Docs
description: Eseguire il debug di un pacchetto di app UWP (Universal Windows Platform) installato in Visual Studio in computer Windows 10, Xbox e dispositivi Internet delle cose (IoT).
ms.custom: SEO-VS-2020
ms.date: 11/07/2018
ms.topic: how-to
f1_keywords:
- vs.debug.installedapppackagelauncher
- vs.debug.remote.connection
dev_langs:
- C++
- FSharp
- CSharp
- JScript
- VB
helpviewer_keywords:
- app package, debug
ms.assetid: 5a94ad64-100d-43ca-9779-16cb5af86f97
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: 3d398dd937bad3af548f1a32a4b9a5964ddb31fb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630791"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Eseguire il debug di un pacchetto di app UWP installato in Visual Studio

Visual Studio possibile eseguire il debug di pacchetti di app UWP (Universal Windows Platform) installati in computer Windows 10 e dispositivi Xbox, HoloLens e IoT.

>[!NOTE]
>Visual Studio il debug per le app UWP installate non è supportato nei telefoni.

Per altre informazioni sul debug delle app UWP, vedi i post di blog sul debug dei pacchetti di [app](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) installati e sulla creazione [di app UWP (Universal Windows Apps).](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/)

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Eseguire il debug di un'app UWP installata in un computer locale

1. Nella Visual Studio debug **di** altre destinazioni di debug  >  **Eseguire** il  >  **debug del pacchetto dell'app installato.**

1. Nella finestra **di dialogo Debug pacchetto app** installato selezionare Computer locale in **Tipo** **di connessione.**

1. In **Pacchetti dell'app installati** selezionare l'app di cui si vuole eseguire il debug o digitarne il nome nella casella di ricerca. I pacchetti di app installati non in esecuzione vengono visualizzati in **Non in esecuzione** e le app in esecuzione sono in **esecuzione**.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. Se necessario, modificare il tipo di codice in **Esegui debug di questo tipo di codice** e selezionare altre opzioni.
   - Selezionare **Non avviare, ma eseguire il debug del codice all'avvio** del debug all'avvio dell'app. L'avvio del debug all'avvio dell'app è un modo efficace per eseguire il debug dei percorsi di controllo da diversi metodi di [avvio,](/windows/uwp/xbox-apps/automate-launching-uwp-apps)ad esempio l'attivazione del protocollo con parametri personalizzati.

1. Selezionare **Avvia oppure,** se l'app è in esecuzione, selezionare **Collega.**

> [!NOTE]
> È anche possibile connettersi a qualsiasi UWP in esecuzione o a un altro processo dell'app selezionando Debug Attach to Process (Esegui **debug**  >  **connessione** a processo) Visual Studio. Il progetto Visual Studio originale non è necessario per connettersi a un processo in esecuzione, ma il caricamento dei simboli dell'app sarà molto utile quando si esegue il debug di un processo per cui non si dispone del codice originale. Vedere [Specificare i file di simboli e di origine nel debugger.](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

## <a name="debug-an-installed-uwp-app-on-a-remote-computer-or-device"></a><a name="remote"></a> Eseguire il debug di un'app UWP installata in un computer o un dispositivo remoto

La prima volta Visual Studio esegue il debug di un'app UWP installata in un dispositivo Windows 10 o in un computer remoto Windows 10 Post-Creators Update, installa gli strumenti di debug remoto nel dispositivo di destinazione.

1. [Abilitare la modalità](/windows/uwp/get-started/enable-your-device-for-development) sviluppatore nel computer Visual Studio e nel dispositivo o nel computer remoto.

1. Se ci si connette a un computer remoto che esegue il Windows 10 Di Creators Update, installare e avviare manualmente il [debugger](../debugger/remote-debugging.md) remoto nel computer remoto.

1. Nel computer Visual Studio selezionare Debug **altre** destinazioni  >  **di debug**  >  **Debug Pacchetto app installato**.

1. Nella finestra **di dialogo Debug pacchetto app** installato selezionare **Computer** remoto o Dispositivo in **Tipo** **di connessione.**

   Se si seleziona **Dispositivo**, il computer deve essere fisicamente connesso a un Windows 10 dispositivo.

   Per un computer remoto, se l'indirizzo del computer non viene visualizzato accanto a **Indirizzo**, selezionare **Cambia**.

   1. Nella finestra **di dialogo** Connessione remota , accanto a **Indirizzo**, digitare il nome o l'indirizzo IP del computer a cui connettersi.

      ![ScegliereRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ScegliereRemoteComputer")

      Se il debugger non è in grado di connettersi a un computer remoto usando il nome del computer, usare l'indirizzo IP. Usare l'indirizzo IP per i dispositivi Xbox, HoloLens o IoT.
   1. Selezionare un'opzione di autenticazione accanto a **Modalità di autenticazione.**

      Per la maggior parte delle app, mantenere il valore **predefinito Universal (Unencrypted Protocol)**.
   1. Scegliere **Seleziona**.

1. In **Pacchetti dell'app installati** selezionare l'app di cui si vuole eseguire il debug o digitarne il nome nella casella di ricerca. I pacchetti di app installati non in esecuzione vengono visualizzati in **Non in esecuzione** e le app in esecuzione sono in **esecuzione**.

1. Se necessario, modificare il tipo di codice in **Esegui debug di questo tipo di codice** e selezionare altre opzioni.
   - Selezionare **Non avviare, ma eseguire il debug del codice all'avvio** del debug all'avvio dell'app. L'avvio del debug all'avvio dell'app è un modo efficace per eseguire il debug dei percorsi di controllo da diversi metodi di [avvio,](/windows/uwp/xbox-apps/automate-launching-uwp-apps)ad esempio l'attivazione del protocollo con parametri personalizzati.

1. Selezionare **Avvia oppure,** se l'app è in esecuzione, selezionare **Collega.**

Quando si avvia il debug di un pacchetto dell'app installato in un dispositivo Xbox, HoloLens o IoT connesso per la prima volta, Visual Studio installa la versione corretta del debugger remoto per il dispositivo di destinazione. L'installazione del debugger remoto può richiedere del tempo e viene visualizzato il messaggio **Avvio del debugger** remoto in corso.

>[!NOTE]
>Attualmente, un dispositivo Xbox o HoloLens riavvia l'app con il debugger collegato se era già in esecuzione.

Per altre informazioni sulla distribuzione remota delle app UWP, vedere Distribuire ed eseguire il debug di app [UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) ed Eseguire il debug di app [UWP in computer remoti.](run-windows-store-apps-on-a-remote-machine.md)

## <a name="see-also"></a>Vedi anche

- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Debug remoto](../debugger/remote-debugging.md)
- [Configurare Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Assegnazioni di porte del debugger remoto](../debugger/remote-debugger-port-assignments.md)
- [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)