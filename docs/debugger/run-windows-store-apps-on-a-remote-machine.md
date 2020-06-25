---
title: Eseguire il debug di app UWP nei computer remoti | Microsoft Docs
ms.date: 10/05/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 0f6814d6-cd0d-49f3-b501-dea8c094b8ef
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3d208c59f08ddeb5a322d174a2c6b56dd901c2c4
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348119"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Eseguire il debug di app UWP nei computer remoti da Visual Studio

È possibile usare Visual Studio per eseguire, eseguire il debug, profilare e testare un'app piattaforma UWP (Universal Windows Platform) (UWP) in un altro computer o dispositivo. L'esecuzione dell'app UWP in un computer remoto è particolarmente utile quando il computer che esegue Visual Studio non supporta funzionalità specifiche di UWP come il tocco, la posizione geografica o l'orientamento fisico.

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Prerequisiti

Per eseguire il debug di un'app UWP in un dispositivo remoto da Visual Studio:

- Il progetto di Visual Studio deve essere configurato per il debug remoto.
- Il computer remoto e il computer di Visual Studio devono essere connessi in rete o collegati direttamente tramite un cavo USB o Ethernet. Il debug tramite Internet non è supportato.
- È necessario [attivare la modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development) sia nel computer Visual Studio sia nel computer remoto.
- I computer remoti devono eseguire il Remote Tools per Visual Studio.
  - Alcune versioni di Windows 10 avviano ed eseguono automaticamente Remote Tools. In caso contrario, [installare ed eseguire il Remote Tools per Visual Studio](#BKMK_download).
  - I dispositivi Windows Mobile 10 non richiedono o supportano Remote Tools.

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a>Configurare un progetto di Visual Studio per il debug remoto
<a name="BKMK_DirectConnect"></a>Usare le **Proprietà** del progetto per specificare il dispositivo remoto a cui connettersi. Le impostazioni variano a seconda del linguaggio di programmazione.

> [!CAUTION]
> Per impostazione predefinita, la pagina delle proprietà imposta il **protocollo universale (non crittografato)** come **tipo di autenticazione** per le connessioni remote di Windows 10. Potrebbe essere necessario impostare **Nessuna autenticazione** per la connessione al debugger remoto. **Universale (protocollo non crittografato)** e nessun protocollo di **autenticazione** non dispone di sicurezza di rete, quindi i dati passati tra lo sviluppo e i computer remoti sono vulnerabili. Scegliere questi tipi di autenticazione solo per le reti attendibili che non sono a rischio da traffico dannoso o ostile.
>
>Se si sceglie l' **autenticazione di Windows** per il tipo di **autenticazione**, sarà necessario accedere al computer remoto durante il debug. Il debugger remoto deve essere in esecuzione anche in modalità di **autenticazione di Windows** , con lo stesso account utente del computer che esegue Visual Studio.

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a>Configurare un progetto C# o Visual Basic per il debug remoto

1. Selezionare il progetto C# o Visual Basic in Visual Studio **Esplora soluzioni** e selezionare l'icona delle **Proprietà** , premere **ALT** + **invio**oppure fare clic con il pulsante destro del mouse e scegliere **Proprietà**.

1. Selezionare la scheda **Debug**.

1. In **dispositivo di destinazione**selezionare **computer remoto** per un computer remoto o **dispositivo** per un dispositivo Windows Mobile 10 connesso direttamente.

1. Per un computer remoto, immettere il nome di rete o l'indirizzo IP nel campo **computer remoto** oppure selezionare **trova** per cercare il dispositivo nella finestra di [dialogo connessioni remote](#remote-connections).

    ![Proprietà del progetto gestito per il debug remoto](../debugger/media/vsrun_managed_projprop_remote.png "Proprietà del progetto di debug gestito")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a>Configurare un progetto C++ per il debug remoto

1. Selezionare il progetto C++ in Visual Studio **Esplora soluzioni** e selezionare l'icona delle **Proprietà** , premere **ALT** + **invio**oppure fare clic con il pulsante destro del mouse e scegliere **Proprietà**.

1. Selezionare la scheda **debug** .

3. In **debugger da avviare**selezionare computer **remoto** per un computer remoto o **dispositivo** per un dispositivo Windows Mobile 10 connesso direttamente.

1. Per un computer remoto, immettere o selezionare il nome di rete o l'indirizzo IP nel campo **nome computer** oppure elenco a discesa e selezionare **individua** per cercare il dispositivo nella finestra di [dialogo connessioni remote](#remote-connections).

    ![Proprietà del progetto C++ per il debug remoto](../debugger/media/vsrun_cpp_projprop_remote.png "Proprietà del progetto di debug C++")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a>Utilizzare la finestra di dialogo connessioni remote

Nella finestra di dialogo **connessioni remote** è possibile cercare un nome di computer remoto o un indirizzo IP specifico oppure rilevare automaticamente le connessioni selezionando l'icona di aggiornamento a freccia arrotondata. La finestra di dialogo Cerca solo i dispositivi della subnet locale che eseguono attualmente il debugger remoto. Non tutti i dispositivi possono essere rilevati nella finestra di dialogo **connessioni remote** .

 ![Finestra di dialogo connessione remota](../debugger/media/vsrun_selectremotedebuggerdlg.png "Finestra di dialogo connessioni remote")

>[!TIP]
>Se non è possibile connettersi a un dispositivo remoto in base al nome, provare a usare il proprio indirizzo IP. Per determinare l'indirizzo IP, nel dispositivo remoto immettere **ipconfig** in una finestra di comando. L'indirizzo IP viene visualizzato come **indirizzo IPv4**.

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a> Scaricare e installare Remote Tools per Visual Studio

Per eseguire il debug di app in un computer remoto, in Visual Studio è necessario che nel computer remoto sia in esecuzione il Remote Tools per Visual Studio.

- I dispositivi Windows Mobile 10 non richiedono o supportano Remote Tools.
- I PC Windows 10 che eseguono l'aggiornamento del creatore (versione 1703) e versioni successive, i dispositivi Xbox, Internet e HoloLens di Windows 10 installano automaticamente gli strumenti remoti quando si distribuisce l'app.
- Nei PC Windows 10 di aggiornamento del pre-creatore è necessario scaricare, installare ed eseguire manualmente Remote Tools nel computer remoto prima di avviare il debug.

**Per scaricare e installare Remote Tools:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a>Configurare Remote Tools

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a>Eseguire il debug di app UWP in modalità remota

Il debug remoto funziona allo stesso modo del debug locale.

1. Nelle versioni di aggiornamento di Windows 10 del pre-creatore assicurarsi che il Remote Debugging Monitor (*msvsmon.exe*) sia in esecuzione nel dispositivo remoto.

1. Nel computer Visual Studio, assicurarsi che venga visualizzata la destinazione di debug corretta (computer o **dispositivo****remoto** ) accanto alla freccia verde sulla barra degli strumenti.

1. Avviare il debug selezionando **debug**  >  **Avvia debug**, premendo **F5**o selezionando la freccia verde sulla barra degli strumenti.

   Il progetto viene ricompilato, quindi distribuito e avviato sul dispositivo remoto. Il debugger sospende l'esecuzione in corrispondenza dei punti di interruzione ed è possibile eseguire istruzioni, over e out di codice.

1. Se necessario, selezionare **debug**  >  **Interrompi debug** o premere **MAIUSC** + **F5** per arrestare il debug e chiudere l'app remota.

## <a name="see-also"></a>Vedi anche
- [Opzioni di distribuzione remota avanzata](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Test delle app UWP con Visual Studio](/visualstudio/test/create-and-run-unit-tests-for-a-store-app-in-visual-studio/)
- [Eseguire il debug di app UWP in Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
