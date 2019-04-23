---
title: Eseguire il debug di App UWP in computer remoti | Microsoft Docs
ms.date: 10/05/2018
ms.topic: conceptual
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
ms.openlocfilehash: 50d307cd65bfdf534b6ca3586e69bbc27be25e36
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60055385"
---
# <a name="debug-uwp-apps-on-remote-machines-from-visual-studio"></a>Eseguire il debug di App UWP in un computer remoto da Visual Studio

È possibile usare Visual Studio per eseguire, debug, profilatura e testare un'app Universal Windows Platform (UWP) in un altro computer o dispositivo. Esecuzione dell'app UWP in un computer remoto è particolarmente utile quando il computer di Visual Studio non supporta funzionalità specifiche della piattaforma UWP, ad esempio il tocco, georilevazione o orientamento fisico.

## <a name="BKMK_Prerequisites"></a> Prerequisiti

Eseguire il debug di un'app UWP in un computer remoto da Visual Studio:

- Il progetto di Visual Studio deve essere configurato per il debug remoto.
- Nel computer remoto e il computer di Visual Studio deve essere connesso in rete o collegati direttamente tramite un cavo Ethernet o USB. Il debug tramite Internet non è supportato.
- È necessario [attivare la modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development) sia il computer di Visual Studio nel computer remoto.
- Computer remoto deve eseguire Remote Tools per Visual Studio.
  - Alcune versioni di Windows 10 aprire ed eseguono remote tools automaticamente. In caso contrario, [installare ed eseguire Remote Tools per Visual Studio](#BKMK_download).
  - I dispositivi mobili Windows 10 non richiede o supporta remote tools.

## <a name="BKMK_ConnectVS"></a> Configurare un progetto di Visual Studio per il debug remoto
<a name="BKMK_DirectConnect"></a> Si usa il progetto **proprietà** per specificare il dispositivo remoto a cui connettersi. Le impostazioni variano a seconda del linguaggio di programmazione.

> [!CAUTION]
> Per impostazione predefinita, la pagina delle proprietà imposta **universale (protocollo non crittografato)** come la **tipo di autenticazione** per le connessioni remote di Windows 10. Potrebbe essere necessario impostare **Nessuna autenticazione** per connettersi al debugger remoto. **Universale (protocollo non crittografato)** e **Nessuna autenticazione** protocolli non dispongono di alcuna sicurezza di rete, in modo che i dati passati tra lo sviluppo e i computer remoti sono vulnerabili. Scegliere questi tipi di autenticazione solo per le reti attendibili che si sono certi non sono esposti da traffico ostile o dannoso.
>
>Se si sceglie **Windows autenticazione** per il **tipo di autenticazione**, dovrai accedere al computer remoto durante il debug. Il debugger remoto deve essere eseguito anche con **Windows autenticazione** modalità con lo stesso account utente di nel computer di Visual Studio.

### <a name="BKMK_Choosing_the_remote_device_for_C__and_Visual_Basic_projects"></a> Configurare un C# o un progetto di Visual Basic per il debug remoto

1. Selezionare il C# o un progetto di Visual Basic in Visual Studio **Esplora soluzioni** e selezionare il **proprietà** icona, premere **Alt** +  **Immettere**, o fare clic e scegliere **proprietà**.

1. Selezionare la scheda **Debug**.

1. Sotto **dispositivo di destinazione**, selezionare **computer remoto** per un computer remoto, o **dispositivo** per un dispositivo Windows Mobile 10 connesso a direct.

1. Per un computer remoto, immettere il nome di rete o l'indirizzo IP nel **computer remoto** campo oppure selezionare **trovare** per cercare il dispositivo nel [nella finestra di dialogo connessioni Remote](#remote-connections).

    ![Proprietà del progetto per il debug remoto gestito](../debugger/media/vsrun_managed_projprop_remote.png "le proprietà del progetto di Debug gestito")

### <a name="BKMK_Choosing_the_remote_device_for_JavaScript_and_C___projects"></a> Configurare un C++ progetto per il debug remoto

1. Selezionare il C++ progetto in Visual Studio **Esplora soluzioni** e selezionare il **proprietà** icona, premere **Alt**+**INVIO**, o fare clic e scegliere **proprietà**.

1. Selezionare il **debug** scheda.

3. Sotto **Debugger da avviare**, selezionare **computer remoto** per un computer remoto, o **dispositivo** per un dispositivo Windows Mobile 10 connesso a direct.

1. Per un computer remoto, immettere o selezionare il nome di rete o l'indirizzo IP nel **nome macchina** campo o drop verso il basso e selezionare **individua** per cercare il dispositivo nel [nella finestra di dialogo connessioni Remote ](#remote-connections).

    ![Proprietà del progetto C++ per il debug remoto](../debugger/media/vsrun_cpp_projprop_remote.png "le proprietà del progetto di debug C++")

### <a name="remote-connections"></a> Utilizzare la finestra di dialogo connessioni Remote

Nel **le connessioni Remote** nella finestra di dialogo è possibile cercare un indirizzo IP o un nome specifico del computer remoto o rileva automaticamente le connessioni selezionando l'icona di freccia arrotondato aggiornamento. La finestra di dialogo Cerca solo i dispositivi sulla subnet locale attualmente in esecuzione il debugger remoto. Non tutti i dispositivi possono essere rilevati nel **le connessioni Remote** nella finestra di dialogo.

 ![Finestra di dialogo di connessione remota](../debugger/media/vsrun_selectremotedebuggerdlg.png "finestra di dialogo connessioni Remote")

>[!TIP]
>Se non è possibile connettersi a un dispositivo remoto in base al nome, provare a usare il relativo indirizzo IP. Per determinare l'indirizzo IP, sul dispositivo remoto, immettere **ipconfig** in una finestra di comando. L'indirizzo IP viene visualizzato come **indirizzo IPv4**.

## <a name="BKMK_download"></a> Scaricare e installare Remote Tools per Visual Studio

Per Visual Studio per il debug delle App in un computer remoto, il computer remoto deve eseguire Remote Tools per Visual Studio.

- I dispositivi mobili Windows 10 non richiedono né supporta remote tools.
- I PC Windows 10 che esegue Creators Update (versione 1703) e versioni successive, i dispositivi Windows 10 Xbox, IoT e HoloLens installare remote tools automaticamente quando si distribuisce l'app.
- Nei PC di pre-Creators Update Windows 10, manualmente è necessario scaricare, installare ed essere in esecuzione di remote tools sul computer remoto prima di avviare il debug.

**Per scaricare e installare gli strumenti remoti:**

[!INCLUDE [remote-debugger-download](../debugger/includes/remote-debugger-download.md)]

### <a name="BKMK_setup"></a> Configurare gli strumenti remoti

[!INCLUDE [remote-debugger-configuration](../debugger/includes/remote-debugger-configuration.md)]

## <a name="BKMK_RunRemoteDebug"></a> Il debug remoto di App UWP

Debug remoto funziona esattamente come il debug locale.

1. Nelle versioni di pre-Creators Update di Windows 10, assicurarsi che Remote Debugging Monitor (*msvsmon.exe*) è in esecuzione nel dispositivo remoto.

1. Nel computer di Visual Studio, assicurarsi che la destinazione di debug corretta (**computer remoto** oppure **dispositivo**) viene visualizzato accanto alla freccia verde sulla barra degli strumenti.

1. Avviare il debug scegliendo **Debug** > **Avvia debug**, premendo **F5**, o si seleziona la freccia verde sulla barra degli strumenti.

   Il progetto viene ricompilata, quindi distribuisce e viene avviato sul dispositivo remoto. Il debugger sospende l'esecuzione nei punti di interruzione e può eseguire un'istruzione, failover e fuori dal codice.

1. Se necessario, selezionare **Debug** > **Termina debug** oppure premere **MAIUSC**+**F5** per arrestare il debug e Chiudere l'app remota.

## <a name="see-also"></a>Vedere anche
- [Opzioni di distribuzione remota avanzata](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Test delle app UWP con Visual Studio](/visualstudio/test/create-and-run-unit-tests-for-a-store-app-in-visual-studio/)
- [Eseguire il debug di app UWP in Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
