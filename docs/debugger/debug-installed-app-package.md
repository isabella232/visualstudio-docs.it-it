---
title: Eseguire il debug di un pacchetto dell'app installato (UWP) | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 07/17/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- uwp
ms.openlocfilehash: 3bb858f2ee20eb65c09dd4979f2bbba1470cbe0d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49908246"
---
# <a name="debug-an-installed-app-package-in-visual-studio-uwp"></a>Eseguire il debug di un pacchetto dell'app installate in Visual Studio (UWP)

È possibile eseguire il debug di qualsiasi pacchetto dell'app installato facendo **Debug > altre destinazioni Debug > Debug pacchetto applicazione installato**. Questo metodo di debug è disponibile per le app di Windows universale (UWP) su questi dispositivi:

* Windows 10 (non supportati nei telefoni)
* XBox
* HoloLens
* IoT

Per altre informazioni su queste funzionalità, vedere il post di blog sugli aggiornamenti per [debug installati i pacchetti dell'app](https://blogs.msdn.microsoft.com/devops/2016/03/30/updates-for-debugging-installed-app-packages-in-visual-studio-2015-update-2/) e il post sul [compilazione di App Windows universali (UWP)](https://blogs.msdn.microsoft.com/visualstudio/2016/08/02/universal-windows-apps-targeting-windows-10-anniversary-sdk/).

## <a name="debug-an-installed-app-package-or-running-app-on-a-local-machine-or-device"></a>Eseguire il debug di un pacchetto dell'App installato o applicazione in esecuzione in un dispositivo o computer locale

1. Nel progetto UWP aperta in Visual Studio, fare clic su **Debug > altre destinazioni Debug > Debug pacchetto applicazione installato**.

2. Selezionare uno **computer locale** oppure **dispositivo**.

     Se si sceglie **dispositivo**, il computer deve essere fisicamente connesso a un dispositivo Windows 10.

     ![DebugInstalledAppPackage](../debugger/media/debug-installed-app-pkg.png "DebugInstalledAppPackage")

     Attualmente in esecuzione installato app i pacchetti vengono visualizzati sotto la **in esecuzione** nodo. Installare i pacchetti dell'app che non sono in esecuzione show backup con **non è in esecuzione**.

3. Selezionare il nome dell'app da sottoporre a debug in **in esecuzione** oppure **non è in esecuzione** e scegliere **avviare** oppure, se l'app è già in esecuzione, scegliere **Attach**.

     Se si seleziona **non devono essere avviate, ma eseguine il debug del codice all'avvio**, in questo modo il debugger di Visual Studio da collegare all'app all'avvio in un momento personalizzato. Si tratta di un metodo efficace per eseguire il debug da percorsi del controllo [metodi di avvio diverse](/windows/uwp/xbox-apps/automate-launching-uwp-apps), ad esempio l'attivazione di protocollo con parametri personalizzati.

> [!NOTE]
> Visual Studio può anche collegare a qualsiasi processo di app UWP in esecuzione selezionando **Debug**e quindi **Connetti a processo**. Connessione a un processo in esecuzione non richiede il progetto di Visual Studio originale, ma il caricamento dei simboli del processo sarà utili in modo significativo quando un processo di cui non si ha il codice originale per il debug.
  
## <a name="remote"></a> Eseguire il debug di un'App installata o in esecuzione in un Computer remoto 

Quando si esegue il debug di un pacchetto dell'app installate in un computer remoto per la prima volta, Visual Studio installa la versione corretta di remote tools per il dispositivo di destinazione. Il dispositivo di destinazione deve essere un computer Windows 10, il dispositivo XBox, HoloLens e IoT.

1. Nel dispositivo Windows 10, attivare [modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development).

2. Se ci si connette a un computer remoto esegue Update versione pre-Creators di Windows 10, prima di tutto manualmente [installare e avviare il debugger remoto](../debugger/remote-debugging.md).

     Per un dispositivo XBox, HoloLens e IoT e i dispositivi Windows che eseguono Update Windows 10 Creators, non devi installare manualmente il debugger remoto. Remote tools verrà installato automaticamente quando si distribuisce l'app.

3. Fare clic su **Debug > altre destinazioni Debug > Debug pacchetto di applicazioni installato**.

4. Dal primo elenco a discesa, scegliere **computer remoto**.

5. Digitare il nome o indirizzo IP del computer in cui che si desidera stabilire una connessione.

     ![ChooseRemoteComputer](../debugger/media/debug-remote-app-pkg.png "ChooseRemoteComputer")

     Se non è possibile collegare usando il nome di computer (dopo aver scelto **avviare**), in alternativa, usare l'indirizzo IP. Usare l'indirizzo IP per i dispositivi XBox, HoloLens e IoT.

6. Scegliere come eseguire l'autenticazione selezionando un'opzione in **modalità di autenticazione**.

    Per la maggior parte delle App, il valore predefinito, mantenere **universale (protocollo non crittografato)**.

7. Selezionare il nome dell'app da sottoporre a debug in **in esecuzione** oppure **non è in esecuzione** e scegliere **avviare** o (per l'esecuzione di App) **Attach**.

     Se si seleziona **non devono essere avviate, ma eseguine il debug del codice all'avvio**, in questo modo il debugger di Visual Studio possa connettersi al pacchetto dell'app all'avvio in un momento personalizzato. Si tratta di un metodo efficace per eseguire il debug da percorsi del controllo [metodi di avvio diverse](/windows/uwp/xbox-apps/automate-launching-uwp-apps), ad esempio l'attivazione di protocollo con parametri personalizzati.

     Quando si esegue il debug di un pacchetto dell'app installate in un dispositivo XBox, HoloLens e IoT collegato per la prima volta, Visual Studio installa la versione corretta del debugger remoto per il dispositivo di destinazione. L'operazione potrebbe richiedere un po' di tempo e verrà visualizzato un messaggio ``Starting remote debugger`` mentre questo è in corso.

     > [!NOTE]
   > È presente, XBox o dispositivo HoloLens verrà riavviato l'app con il debugger collegato se è già in esecuzione.

Per informazioni sulle opzioni avanzate per la distribuzione remota delle App UWP, vedere [apps]((/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options) UWP distribuzione e debug. 
  
## <a name="see-also"></a>Vedere anche  
 [Debug in Visual Studio](../debugger/index.md)  
 [Tour delle funzionalità del debugger](../debugger/debugger-feature-tour.md)  
 [Remote Debugging](../debugger/remote-debugging.md)  
 [Configurare Windows Firewall per il debug remoto](../debugger/configure-the-windows-firewall-for-remote-debugging.md)  
 [Assegnazioni delle porte del debugger remoto](../debugger/remote-debugger-port-assignments.md)  
 [Errori e risoluzione dei problemi relativi al debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)