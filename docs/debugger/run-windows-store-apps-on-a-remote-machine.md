---
title: Eseguire il debug di app UWP in computer | Microsoft Docs
description: Vedere come usare Visual Studio eseguire, eseguire il debug, profilare e testare un'app UWP (Universal Windows Platform) in modalità remota in un altro computer o dispositivo.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: e48422f3e73802a56a24db3febf8128dad78efe3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636668"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Eseguire il debug di app UWP in computer remoti da Visual Studio

È possibile usare Visual Studio eseguire, eseguire il debug, profilare e testare un'app UWP (Universal Windows Platform) in un altro computer o dispositivo. L'esecuzione dell'app UWP in un computer remoto è particolarmente utile quando il computer Visual Studio non supporta funzionalità specifiche della UWP, ad esempio tocco, posizione geografica o orientamento fisico.

## <a name="prerequisites"></a><a name="BKMK_Prerequisites"></a> Prerequisiti

Per eseguire il debug di un'app UWP in un dispositivo remoto da Visual Studio:

- Il Visual Studio deve essere configurato per il debug remoto.
- Il computer remoto e il Visual Studio devono essere connessi tramite una rete o direttamente tramite un cavo USB o Ethernet. Il debug tramite Internet non è supportato.
- È necessario [attivare la modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development) sia nel computer Visual Studio che nel computer remoto.
- I computer remoti devono eseguire il Remote Tools per Visual Studio.
  - Alcune Windows 10 avviano ed eseguono automaticamente gli strumenti remoti. In caso [contrario, installare ed eseguire il Remote Tools per Visual Studio](#BKMK_download).
  - Windows I dispositivi mobili 10 non richiedono o supportano gli strumenti remoti.

## <a name="configure-a-visual-studio-project-for-remote-debugging"></a><a name="BKMK_ConnectVS"></a>Configurare un progetto Visual Studio per il debug remoto
<a name="BKMK_DirectConnect"></a> Usare le proprietà **del progetto** per specificare il dispositivo remoto a cui connettersi. Le impostazioni variano a seconda del linguaggio di programmazione.

> [!CAUTION]
> Per impostazione predefinita, la pagina delle proprietà imposta **Universal (Unencrypted Protocol)** come **tipo di** autenticazione per Windows 10 remote. Potrebbe essere necessario impostare **Nessuna autenticazione** per connettersi al debugger remoto. **I protocolli Universal (Unencrypted Protocol)** e **No Authentication** non hanno sicurezza di rete, quindi i dati passati tra i computer di sviluppo e remoti sono vulnerabili. Scegliere questi tipi di autenticazione solo per le reti attendibili che non sono a rischio di traffico dannoso o ostile.
>
>Se si sceglie **Windows autenticazione** per **Tipo** di autenticazione , sarà necessario accedere al computer remoto durante il debug. Il debugger remoto deve essere in esecuzione anche **Windows di** autenticazione, con lo stesso account utente del computer Visual Studio remoto.

### <a name="configure-a-c-or-visual-basic-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a>Configurare un progetto C# o Visual Basic per il debug remoto

1. Selezionare il progetto C# o Visual Basic in Visual Studio **Esplora soluzioni** e  selezionare l'icona Proprietà, premere **ALT INVIO** oppure fare clic con il pulsante destro del mouse e scegliere +  **Proprietà**.

1. Selezionare la scheda **Debug**.

1. In **Dispositivo di destinazione** selezionare Computer **remoto** per un computer remoto o Dispositivo per un dispositivo Windows Mobile 10. 

1. Per un computer remoto, immettere il nome di rete o  l'indirizzo IP nel campo **Computer** remoto oppure selezionare Trova per cercare il dispositivo nella finestra di [dialogo Connessioni remote](#remote-connections).

    ![Proprietà del progetto gestito per il debug remoto](../debugger/media/vsrun_managed_projprop_remote.png "Proprietà del progetto di debug gestito")

### <a name="configure-a-c-project-for-remote-debugging"></a><a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Configurare un progetto C++ per il debug remoto

1. Selezionare il progetto C++ in Visual Studio **Esplora soluzioni** e  selezionare l'icona Proprietà, premere **ALT** INVIO oppure fare clic con il pulsante destro del mouse e + scegliere **Proprietà**.

1. Selezionare la **scheda** Debug.

3. In **Debugger da avviare** selezionare Computer **remoto**  per un computer remoto o Dispositivo per un dispositivo Windows Mobile 10.

1. Per un computer remoto, immettere o selezionare il  nome di rete o  l'indirizzo IP nel campo Nome computer oppure selezionare Individua per cercare il dispositivo nella finestra di dialogo [Connessioni remote](#remote-connections).

    ![Proprietà del progetto C++ per il debug remoto](../debugger/media/vsrun_cpp_projprop_remote.png "Proprietà del progetto debug C++")

### <a name="use-the-remote-connections-dialog-box"></a><a name="remote-connections"></a> Usare la finestra di dialogo Connessioni remote

Nella finestra **di dialogo** Connessioni remote è possibile cercare un nome di computer remoto o un indirizzo IP specifico oppure rilevare automaticamente le connessioni selezionando l'icona di aggiornamento della freccia arrotondata. La finestra di dialogo cerca solo i dispositivi nella subnet locale che eseguono il debugger remoto. Non tutti i dispositivi possono essere rilevati nella **finestra di dialogo Connessioni** remote .

 ![Finestra di dialogo Connessione remota](../debugger/media/vsrun_selectremotedebuggerdlg.png "Finestra di dialogo Connessioni remote")

>[!TIP]
>Se non è possibile connettersi a un dispositivo remoto in base al nome, provare a usare il relativo indirizzo IP. Per determinare l'indirizzo IP, nel dispositivo remoto immettere **ipconfig** in una finestra di comando. L'indirizzo IP viene visualizzato **come Indirizzo IPv4.**

## <a name="download-and-install-the-remote-tools-for-visual-studio"></a><a name="BKMK_download"></a> Scaricare e installare Remote Tools per Visual Studio

Per Visual Studio eseguire il debug delle app in un computer remoto, il computer remoto deve eseguire il Remote Tools per Visual Studio.

- Windows I dispositivi Mobili 10 non richiedono o supportano gli strumenti remoti.
- Windows 10 I PC che eseguono Creator's Update (versione 1703) e versioni successive Windows 10 dispositivi Xbox, IoT e HoloLens installano automaticamente gli strumenti remoti quando si distribuisce l'app.
- Nei PC di aggiornamento Windows 10 pre-Creator è necessario scaricare, installare ed eseguire manualmente gli strumenti remoti nel computer remoto prima di avviare il debug.

**Per scaricare e installare gli strumenti remoti:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="configure-the-remote-tools"></a><a name="BKMK_setup"></a> Configurare gli strumenti remoti

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="debug-uwp-apps-remotely"></a><a name="BKMK_RunRemoteDebug"></a> Eseguire il debug di app UWP in modalità remota

Il debug remoto funziona come il debug locale.

1. Nelle versioni di pre-Creator's Update Windows 10 assicurarsi che il Remote Debugging Monitor (*msvsmon.exe*) sia in esecuzione nel dispositivo remoto.

1. Nel computer Visual Studio verificare che accanto alla freccia verde sulla barra degli strumenti sia visualizzata la destinazione di debug corretta **(** Computer remoto o Dispositivo ).

1. Avviare il debug selezionando **Debug**  >  **Avvia debug**, premendo **F5** o selezionando la freccia verde sulla barra degli strumenti.

   Il progetto viene ricompilato, quindi viene distribuito e avviato nel dispositivo remoto. Il debugger sospende l'esecuzione in corrispondenza dei punti di interruzione ed è possibile eseguire istruzioni, eseguire e uscire dal codice.

1. Se necessario, selezionare **Debug Arresta** debug o premere MAIUSC F5 per arrestare il  >   debug e  +  chiudere l'app remota.

## <a name="see-also"></a>Vedi anche
- [Opzioni avanzate di distribuzione remota](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Test delle app UWP con Visual Studio](../test/unit-test-your-code.md)
- [Eseguire il debug di app UWP in Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
