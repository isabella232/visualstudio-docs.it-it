---
title: Distribuire app UWP | Microsoft Docs
description: Distribuire piattaforma UWP (Universal Windows Platform) (UWP) da Visual Studio. Specificare un dispositivo di destinazione locale o remoto per la distribuzione. Informazioni su opzioni di distribuzione.
ms.custom: SEO-VS-2020
ms.date: 01/16/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 0a1c1802d92beb436bbd2ac87bd1e7a39f6086f1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387866"
---
# <a name="deploy-uwp-apps-from-visual-studio"></a>Distribuire app UWP da Visual Studio

La Visual Studio di distribuzione compila e registra le app UWP create con Visual Studio in un dispositivo di destinazione. Il modo in cui viene registrata l'app è determinato dal tipo di dispositivo, ovvero se è locale o remoto:

- Quando la destinazione è il computer Visual Studio locale, Visual Studio registra l'app dalla cartella della build dell'app stessa.

- Quando la destinazione è un dispositivo remoto, Visual Studio copia i file necessari nel computer remoto e registra l'app su questo dispositivo.

La distribuzione avviene automaticamente quando si esegue il debug dell'app da Visual Studio usando l'opzione **Avvia debug** (tastiera: F5) oppure l'opzione **Avvia senza eseguire debug** (tastiera: CTRL+F5). Puoi distribuire l'app anche manualmente. Ecco gli scenari in cui la distribuzione manuale può essere utile:

- Test ad hoc su un computer locale o remoto.

- Distribuzione di un'app che avvia un'altra app di cui vuoi eseguire il debug.

- Distribuzione di un'app di cui viene eseguito il debug quando viene avviata da un'altra app o da un altro metodo.

## <a name="how-to-deploy-a-uwp-app"></a><a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Come distribuire un'app UWP
 La distribuzione manuale di un'app è un processo facile:

1. Se esegui la distribuzione in un dispositivo remoto, specifica il nome o l'indirizzo IP del dispositivo nella pagina delle proprietà del progetto di avvio dell'app. I passaggi necessari sono elencati più avanti in questo argomento.

2. Sulla barra degli strumenti Visual Studio del debugger seleziona la destinazione di distribuzione nell'elenco a discesa accanto al pulsante **Avvia debug** .

     ![Effettuare l'esecuzione nel computer locale](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")

3. Scegli **Distribuzione** dal menu **Compilazione**.

## <a name="how-to-specify-a-remote-device"></a><a name="BKMK_How_to_specify_a_remote_device"></a> Come specificare un dispositivo remoto

**Prerequisiti**

In un Windows 10 remoto è necessario abilitare la [modalità sviluppatore](/windows/uwp/get-started/enable-your-device-for-development). Nei Windows 10 che eseguono Creator's Update o versioni successive, gli strumenti remoti vengono installati automaticamente quando si distribuisce l'app. Per altre informazioni, vedere Eseguire [il debug di un pacchetto dell'app installato.](../debugger/debug-installed-app-package.md)

> [!NOTE]
> Nelle versioni precedenti all'aggiornamento di Windows 10, il Remote Tools per Visual Studio deve essere installato nel dispositivo remoto e il debugger remoto deve essere in esecuzione.

La distribuzione usa il canale di rete del debugger remoto per inviare i file dell'app al dispositivo remoto.

#### <a name="to-specify-a-remote-device"></a>Per specificare un dispositivo remoto

1. Nella pagina delle proprietà Debug del progetto di avvio specifica il nome o l'indirizzo IP di una destinazione di distribuzione remota.

2. Per aprire la pagina delle proprietà Debug, seleziona il progetto in Esplora soluzioni e scegli **Proprietà** dal menu di scelta rapida.

3. Seleziona il nodo **Debug** nella finestra della pagina delle proprietà.

4. Per **Dispositivo di destinazione** selezionare Computer **remoto.**

5. In **Computer remoto fare** clic su **Trova.**

6. È possibile digitare il nome o l'indirizzo IP del dispositivo remoto oppure scegliere il dispositivo dalla **finestra di dialogo** Connessione remota.

    ![Finestra di dialogo per la selezione della connessione del debugger remoto](../debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN_SelectRemoteDebuggerDlg")

    Nella **finestra di dialogo** Connessione remota vengono visualizzati i dispositivi nella subnet della rete locale e tutti i dispositivi connessi direttamente al computer Visual Studio tramite un cavo Ethernet.

   **Specifica del dispositivo remoto in una pagina di progetto C++**

   ![Proprietà del&#43;&#43; C per il debug remoto](../debugger/media/vsrun_cpp_projprop_remote.png "VSRUN_CPP_ProjProp_Remote")

7. Scegli **Debugger remoto** dall'elenco **Debugger da avviare** .

8. Immetti il nome di rete del dispositivo remoto nella casella **Nome computer** . In alternativa, puoi fare clic sulla freccia in giù della casella per selezionare il dispositivo nella finestra di dialogo Seleziona connessione debugger remoto.

   **Indicazione del dispositivo remoto nella pagina di un progetto Visual C# o Visual Basic**

   ![Proprietà del progetto gestito per il debug remoto](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN_Managed_ProjProp_Remote")

9. Scegli **Computer remoto** dall'elenco **Dispositivo di destinazione** .

10. Immetti il nome di rete del dispositivo remoto nella casella **Computer remoto** o fai clic su **Trova** per scegliere il dispositivo nella finestra di dialogo **Seleziona connessione debugger remoto** .

## <a name="deployment-options"></a><a name="BKMK_Deployment_options"></a> Opzioni di distribuzione

Di seguito sono indicate le opzioni di distribuzione che puoi impostare nella pagina delle proprietà Debug del progetto di avvio.

**Consenti loopback della rete locale**

Per motivi di sicurezza, una UWP o un'app installata in modo standard non è autorizzata a effettuare chiamate di rete al dispositivo in [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] cui è installata. Per impostazione predefinita, per l'app distribuita la distribuzione di Visual Studio crea un'esenzione da questa regola. Questa esenzione ti consente di testare le procedure di comunicazione in un unico computer. Prima di inviare l'app a [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], dovrai testarla senza l'esenzione.

Per rimuovere l'esenzione relativa al loopback della rete dall'app:

- Nella pagina delle proprietà Debug Visual Basic C# e rete deselezionare la casella di controllo **Consenti loopback** di rete .

- Nella pagina delle proprietà Debug di C++ impostare il **valore Consenti loopback di** rete su **No.**

**Non avviare, ma eseguire il debug del codice all'avvio (C# e Visual Basic) / Avviare l'applicazione (C++)**

Per configurare la distribuzione in modo che venga avviata automaticamente una sessione di debug all'avvio dell'app:

- Nella pagina delle proprietà Debug C# e Visual Basic debug selezionare la casella di controllo Non avviare, ma esegui il debug del codice **all'avvio.**

- Nella pagina delle proprietà Debug di C++ impostare il **valore Avvia** applicazione su **Sì.**

## <a name="see-also"></a>Vedi anche

- [Opzioni avanzate di distribuzione remota](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#advanced-remote-deployment-options)
- [Eseguire il debug di un pacchetto dell'app installato](../debugger/debug-installed-app-package.md)
- [Eseguire app da Visual Studio](debugging-windows-store-and-windows-universal-apps.md)
