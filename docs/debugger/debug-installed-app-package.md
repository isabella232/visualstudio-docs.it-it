---
title: Eseguire il debug di un pacchetto dell'app UWP installato | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/07/2018
ms.topic: conceptual
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
ms.openlocfilehash: 84d2296a467bb1fc2c3e1466b715578c94c7d0d8
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/15/2019
ms.locfileid: "56317936"
---
# <a name="debug-an-installed-uwp-app-package-in-visual-studio"></a>Eseguire il debug di un pacchetto dell'app UWP installato in Visual Studio

Visual Studio può eseguire il debug di pacchetti di app Universal Windows Platform (UWP) installati nei computer Windows 10 e dispositivi Xbox, HoloLens e IoT.

>[!NOTE]
>Debug per le app UWP installate di Visual Studio non è supportato nei telefoni.
   
Per altre informazioni sul debug di App UWP, vedere il post di blog sul [debug installati i pacchetti dell'app](https://devblogs.microsoft.com/devops/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) e [compilazione di App Windows universali (UWP)](https://devblogs.microsoft.com/visualstudio/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-uwp-app-on-a-local-machine"></a>Eseguire il debug di un'app UWP installata in un computer locale

1. In Visual Studio, selezionare **Debug** > **altre destinazioni Debug** > **Debug pacchetto applicazione installato**.

1. Nel **Debug pacchetto applicazione installato** finestra di dialogo, sotto **tipo di connessione**, selezionare **macchina locale**.

1. Sotto **pacchetti applicazione installati**, selezionare l'app da sottoporre a debug o digitarne il nome nella casella di ricerca. Pacchetto applicazione installato non in esecuzione vengono visualizzati nella **non è in esecuzione**, e le App in esecuzione nella **esecuzione**.

   ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

1. Se necessario, modificare il tipo di codice sotto **eseguire il Debug di questo tipo di codice**, selezionare le altre opzioni.
   - Selezionare **non devono essere avviate, ma eseguine il debug del codice all'avvio** per avviare il debug all'avvio dell'app. Avviare il debug quando viene avviata l'app è un metodo efficace per eseguire il debug da percorsi del controllo [metodi di avvio diverse](/windows/uwp/xbox-apps/automate-launching-uwp-apps), ad esempio l'attivazione di protocollo con parametri personalizzati.

1. Selezionare **avviare**, o se l'app è in esecuzione, selezionare **Attach**.

> [!NOTE]
> È anche possibile collegare a qualsiasi piattaforma UWP in esecuzione o un altro processo app selezionando **Debug** > **Connetti a processo** in Visual Studio. Non è necessario il progetto originale di Visual Studio per connettersi a un processo in esecuzione, ma il caricamento dei simboli dell'app sarà utile in modo significativo quando il debug di un processo che non si è il codice originale per. Visualizzare [specificare i file di simboli e origine nel debugger](specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="remote"></a> Eseguire il debug di un'app UWP installata in un dispositivo o computer remoto

La prima volta che Visual Studio esegue il debug di un'app UWP installata in un dispositivo Windows 10 o un remoto post-computer del creatore aggiornamento Windows 10, installa gli strumenti di debug remoti nel dispositivo di destinazione.

1. [Abilitare la modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development) sul computer di Visual Studio e il computer o dispositivo remoto.

1. Se ci si connette a un computer remoto che eseguono Windows 10 di pre-Creators Update, [installare e avviare il debugger remoto manualmente](../debugger/remote-debugging.md) nel computer remoto.

1. Nel computer di Visual Studio, selezionare **Debug** > **altre destinazioni Debug** > **Debug pacchetto applicazione installato**.

1. Nel **Debug pacchetto applicazione installato** finestra di dialogo, in **tipo di connessione**, selezionare **computer remoto** oppure **dispositivo**.

   Se si seleziona **dispositivo**, il computer deve essere fisicamente connesso a un dispositivo Windows 10.

   Per un computer remoto, se l'indirizzo del computer non viene visualizzata accanto a **indirizzi**, selezionare **modifica**.

   1. Nel **connessione remota** accanto alla finestra di dialogo **indirizzo**, digitare il nome o indirizzo IP del computer si desidera connettersi.

      ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

      Se il debugger non è possibile connettersi a un computer remoto utilizzando il nome del computer, usare invece l'indirizzo IP. Usare l'indirizzo IP per i dispositivi Xbox, HoloLens e IoT.
   1. Selezionare un'opzione di autenticazione accanto a **modalità di autenticazione**.

      Per la maggior parte delle App, il valore predefinito, mantenere **universale (protocollo non crittografato)**.
   1. Selezionare **seleziona**.

1. Sotto **pacchetti applicazione installati**, selezionare l'app da sottoporre a debug o digitarne il nome nella casella di ricerca. Pacchetto applicazione installato non in esecuzione vengono visualizzati nella **non è in esecuzione**, e le App in esecuzione nella **esecuzione**.

1. Se necessario, modificare il tipo di codice sotto **eseguire il Debug di questo tipo di codice**, selezionare le altre opzioni.
   - Selezionare **non devono essere avviate, ma eseguine il debug del codice all'avvio** per avviare il debug all'avvio dell'app. Avviare il debug quando viene avviata l'app è un metodo efficace per eseguire il debug da percorsi del controllo [metodi di avvio diverse](/windows/uwp/xbox-apps/automate-launching-uwp-apps), ad esempio l'attivazione di protocollo con parametri personalizzati.

1. Selezionare **avviare**, o se l'app è in esecuzione, selezionare **Attach**.

Quando si avvia il debug di un pacchetto dell'app installate in un dispositivo Xbox, HoloLens e IoT collegato per la prima volta, Visual Studio installa la versione corretta del debugger remoto per il dispositivo di destinazione. Installazione del debugger remoto potrebbe richiedere qualche minuto e il messaggio **avvio del debugger remoto** Visualizza in corso.

>[!NOTE]
>Attualmente, un dispositivo HoloLens o Xbox riavvia l'app con il debugger collegato se è stato già in esecuzione.

Per altre informazioni sulla distribuzione remota delle App UWP, vedere [distribuire ed eseguire il debug delle App UWP](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) e [le app UWP di eseguire il Debug nei computer remoti](run-windows-store-apps-on-a-remote-machine.md).

## <a name="see-also"></a>Vedere anche

- [Debug in Visual Studio](../debugger/index.md)
- [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)
- [Debug remoto](../debugger/remote-debugging.md)
- [Configurare Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)
- [Assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md)
- [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)