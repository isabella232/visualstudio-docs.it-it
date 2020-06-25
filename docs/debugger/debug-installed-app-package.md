---
title: Eseguire il debug di un pacchetto dell'app UWP installato | Microsoft Docs
ms.custom: ''
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
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: eabc694665bede7d193a360a01c42366568e33c5
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350732"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Eseguire il debug di un pacchetto dell'app UWP installato in Visual Studio

Visual Studio è in grado di eseguire il debug dei pacchetti di app piattaforma UWP (Universal Windows Platform) (UWP) installati nei computer Windows 10 e nei dispositivi Xbox, HoloLens e Internet.

>[!NOTE]
>Il debug di Visual Studio per le app UWP installate non è supportato nei telefoni.

Per altre informazioni sul debug di app UWP, vedere il post di Blog sul [debug dei pacchetti di app installate](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) e la [compilazione di app di Windows universale (UWP)](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Eseguire il debug di un'app UWP installata in un computer locale

1. In Visual Studio selezionare **debug**  >  **altre destinazioni**di debug  >  **debug pacchetto app installato**.

1. Nella finestra di dialogo **debug pacchetto app installato** in **tipo di connessione**Selezionare **computer locale**.

1. In **pacchetti di app installate**selezionare l'app di cui si vuole eseguire il debug o digitarne il nome nella casella di ricerca. I pacchetti dell'app installata non in esecuzione vengono visualizzati in **non in esecuzione**e le applicazioni in esecuzione sono in **esecuzione**.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. Se necessario, modificare il tipo di codice in **debug questo tipo di codice**e selezionare altre opzioni.
   - Selezionare non **avviare, ma eseguire il debug del codice quando** inizia a avviare il debug all'avvio dell'app. Avviare il debug quando l'app viene avviata è un modo efficace per eseguire il debug dei percorsi di controllo da [metodi di avvio diversi](/windows/uwp/xbox-apps/automate-launching-uwp-apps), ad esempio l'attivazione del protocollo con parametri personalizzati.

1. Selezionare **Start**oppure, se l'app è in esecuzione, selezionare **Connetti**.

> [!NOTE]
> È anche possibile connettersi a qualsiasi UWP in esecuzione o a un altro processo dell'app selezionando **debug**  >  **Connetti a processo** in Visual Studio. Non è necessario il progetto di Visual Studio originale per connettersi a un processo in esecuzione, ma il caricamento dei simboli dell'app contribuirà in modo significativo durante il debug di un processo per cui non si ha il codice originale. Vedere [specificare i file di simboli e di origine nel debugger](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="debug-an-installed-uwp-app-on-a-remote-computer-or-device"></a><a name="remote"></a>Eseguire il debug di un'app UWP installata in un computer o dispositivo remoto

La prima volta che Visual Studio esegue il debug di un'app UWP installata in un dispositivo Windows 10 o in un computer Windows 10 con aggiornamento di un post-autore remoto, installa gli strumenti di debug remoto sul dispositivo di destinazione.

1. [Abilitare la modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development) nel computer Visual Studio e nel dispositivo o nel computer remoto.

1. Se ci si connette a un computer remoto che esegue l'aggiornamento di Windows 10 di pre-autore, [installare e avviare manualmente il debugger remoto](../debugger/remote-debugging.md) nel computer remoto.

1. Nel computer Visual Studio selezionare **debug**  >  **altre destinazioni**di debug  >  **debug pacchetto app installato**.

1. Nella finestra di dialogo **debug pacchetto app installato** in **tipo di connessione**Selezionare **computer remoto** o **dispositivo**.

   Se si seleziona **dispositivo**, il computer deve essere fisicamente connesso a un dispositivo Windows 10.

   Per un computer remoto, se l'indirizzo del computer non viene visualizzato accanto a **Indirizzo**, selezionare **Cambia**.

   1. Nella finestra di dialogo **connessione remota** , accanto a **Indirizzo**, digitare il nome o l'indirizzo IP del computer a cui si desidera connettersi.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      Se il debugger non è in grado di connettersi a un computer remoto utilizzando il nome del computer, utilizzare invece l'indirizzo IP. Usare l'indirizzo IP per i dispositivi Xbox, HoloLens o Internet.
   1. Selezionare un'opzione di autenticazione accanto alla **modalità di autenticazione**.

      Per la maggior parte delle app, Mantieni il valore predefinito **universale (protocollo non crittografato)**.
   1. Scegliere **Seleziona**.

1. In **pacchetti di app installate**selezionare l'app di cui si vuole eseguire il debug o digitarne il nome nella casella di ricerca. I pacchetti dell'app installata non in esecuzione vengono visualizzati in **non in esecuzione**e le applicazioni in esecuzione sono in **esecuzione**.

1. Se necessario, modificare il tipo di codice in **debug questo tipo di codice**e selezionare altre opzioni.
   - Selezionare non **avviare, ma eseguire il debug del codice quando** inizia a avviare il debug all'avvio dell'app. Avviare il debug quando l'app viene avviata è un modo efficace per eseguire il debug dei percorsi di controllo da [metodi di avvio diversi](/windows/uwp/xbox-apps/automate-launching-uwp-apps), ad esempio l'attivazione del protocollo con parametri personalizzati.

1. Selezionare **Start**oppure, se l'app è in esecuzione, selezionare **Connetti**.

Quando si avvia il debug di un pacchetto dell'app installato in un dispositivo Xbox, HoloLens o Internet per la prima volta, Visual Studio installa la versione corretta del debugger remoto per il dispositivo di destinazione. L'installazione del debugger remoto può richiedere del tempo e il messaggio **avvio del debugger remoto** viene visualizzato mentre è in corso.

>[!NOTE]
>Attualmente, un dispositivo Xbox o HoloLens riavvia l'app con il debugger collegato, se era già in esecuzione.

Per altre informazioni sulla distribuzione remota di app UWP, vedere [distribuire ed eseguire il debug](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) di app UWP ed [eseguire il debug di app UWP in computer remoti](run-windows-store-apps-on-a-remote-machine.md).

## <a name="see-also"></a>Vedi anche

- [Debug in Visual Studio](../debugger/index.yml)
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Debug remoto](../debugger/remote-debugging.md)
- [Configurare la Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md)
- [Errori e risoluzione dei problemi di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)