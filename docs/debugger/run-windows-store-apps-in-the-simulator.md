---
title: Eseguire app UWP nel simulatore | Microsoft Docs
description: Informazioni su come eseguire app UWP (Universal Windows Platform) nel simulatore Visual Studio, ovvero un'applicazione desktop che simula un'app UWP.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- uwp
ms.openlocfilehash: a3695aa387e9bb51c7918b95d0092c41f1f894fd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126636667"
---
# <a name="run-uwp-apps-in-the-simulator"></a>Eseguire app UWP nel simulatore

Il Visual Studio simulatore per le app UWP è un'applicazione desktop che simula un'app UWP. In genere, è necessario eseguire il debug nel computer locale, in un dispositivo connesso o in un computer remoto. Tuttavia, in alcuni scenari può essere necessario usare il simulatore di Visual Studio per emulare dimensioni e risoluzione dello schermo fisiche diverse. È anche possibile simulare eventi comuni di tocco e rotazione e simulare le proprietà della connessione di rete.

Il simulatore fornisce un ambiente in cui è possibile progettare, sviluppare, eseguire il debug e testare app UWP. Tuttavia, prima di pubblicare l'app Microsoft Store, è consigliabile testare l'app in un dispositivo effettivo.

Il simulatore Visual Studio per le app UWP non viene eseguito in un ambiente isolato nel computer locale. Di conseguenza, gli errori che si verificano nel simulatore, ad esempio un errore irreversibile a livello di sistema, può influenzare l'intero computer.

> [!IMPORTANT]
> Il simulatore di Visual Studio 2015 non include il pulsante Georilevazione perché il simulatore di Windows 10 non prevede la simulazione di georilevazione.

## <a name="set-the-simulator-as-the-target"></a><a name="BKMK_Set_the_simulator_as_the_target"></a> Impostare il simulatore come destinazione

Per eseguire l'app UWP nel simulatore, selezionare **Simulatore** nell'elenco a discesa accanto al pulsante Avvia **debug** sulla barra degli strumenti **Standard del** debugger. Questa opzione è disponibile solo se il valore **Versione minima piattaforma di destinazione** dell'app è minore o uguale al sistema operativo nel computer di sviluppo.

![Esecuzione nel simulatore](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")

## <a name="choose-an-interaction-mode"></a><a name="BKMK_Choose_an_interaction_mode"></a> Scegliere una modalità di interazione

È possibile scegliere le modalità di interazione seguenti:

- ![Pulsante modalità mouse](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") Modalità mouse: imposta la modalità di interazione per i movimenti del mouse. I movimenti del mouse includono clic, doppio clic e trascinamento.

- ![Pulsante Avvia emulazione tocco](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Avviare l'emulazione del tocco: imposta la modalità di interazione per i movimenti di tocco di un singolo dito. Gli eventi di un singolo dito includono tocco, trascinamento e scorrimento rapido.

   ![Destinazione un solo dito sul simulatore](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger")
   
   L'icona di bersaglio singolo indica la posizione degli eventi nel simulatore. Usa il mouse per posizionare il puntatore.

   ![Destinazione touch un solo dito](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged")
   
   Premere il pulsante sinistro del mouse per attivare la modalità tocco. Ad esempio, fai clic sul pulsante per simulare un tocco o premi e tieni premuto il pulsante mentre trascini o scorri rapidamente.

## <a name="pinch-and-zoom"></a>Zoom indietro/avanti

Imposta la modalità di interazione per i movimenti zoom indietro e avanti di due dita.

![Simulatore di destinazione a due dita](../debugger/media/simulator_twofinger.png)

La doppia icona di destinazione indica la posizione di due dita sullo schermo del dispositivo.

- Sposta il mouse per posizionare le icone sopra l'oggetto sullo schermo del dispositivo.

- Ruota la rotellina del mouse avanti o indietro per modificare la distanza simulata delle due dita prima di eseguire il movimento zoom avanti o indietro.

![Destinazioni di rotazione, zoom indietro e zoom avanti](../debugger/media/simulator_twofingerengaged.png)

- Premi il pulsante sinistro e ruota la rotellina indietro (verso di te) per fare zoom avanti.

- Premi il pulsante sinistro e ruota la rotellina del mouse in avanti (lontano da te) per fare zoom indietro.

## <a name="object-rotation"></a>Rotazione di oggetti

Il pulsante **Rotazione emulazione tocco** imposta la modalità di interazione sui movimenti di rotazione usando due dita.

- Sposta il mouse per posizionare le icone sopra l'oggetto sullo schermo del dispositivo. Ruota la rotellina del mouse avanti o indietro per modificare l'orientamento simulato delle due dita prima di ruotare l'oggetto.

- Premi il pulsante sinistro e ruota la rotellina indietro (verso di te) per ruotare l'oggetto in senso antiorario. Mente ruoti la rotella del mouse, una delle due icone di destinazione ruota intorno all'altra per indicare la dimensione relativa della rotazione.

- Premi il pulsante sinistro e ruota la rotellina del mouse avanti (lontano di te) per ruotare l'oggetto in senso orario.

## <a name="enable-or-disable-always-on-top-mode"></a><a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Abilitare o disabilitare la modalità Sempre in primo piano
 Puoi impostare la finestra del simulatore in modo che sia sempre in primo piano rispetto ad altre finestre. Il pulsante **Attiva/disattiva finestra in primo piano** abilita o disabilita la modalità **Sempre in primo piano** della finestra del simulatore.

## <a name="change-the-device-orientation"></a><a name="BKMK_Change_the_device_orientation"></a> Modificare l'orientamento del dispositivo
 Puoi modificare l'orientamento verticale e orizzontale del dispositivo ruotando il simulatore di 90 gradi in qualsiasi direzione.

> [!NOTE]
> Il simulatore non rispetta la proprietà [DisplayProperties.AutoRotationPreferences](/uwp/api/windows.graphics.display.displayproperties.autorotationpreferences) di un progetto. Ad esempio, se il progetto imposta l'orientamento su `Landscape`e quindi ruoti il simulatore sull'orientamento verticale, anche l'immagine visualizzata dal simulatore sarà ruotata e ridimensionata. Verifica queste impostazioni su un dispositivo reale.

> [!NOTE]
> Se ruoti il simulatore in modo che un suo bordo sia più largo dello schermo su cui viene visualizzato, il simulatore verrà ridimensionato automaticamente alle dimensioni dello schermo. Il simulatore non viene ripristinato alla dimensione originale se lo ruoti di nuovo.

## <a name="change-the-simulated-screen-size-and-resolution"></a><a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Modificare le dimensioni e la risoluzione dello schermo simulate
 Per modificare le dimensioni e la risoluzione dello schermo simulate, scegliere il pulsante **Cambia risoluzione** nella tavolozza e scegliere una nuova dimensione e una nuova risoluzione dall'elenco.

 Le dimensioni e la risoluzione dello schermo sono elencate come *Larghezza schermo in pollici, larghezza in pixel X altezza in pixel*. Come noterai, le dimensioni e la risoluzione dello schermo sono simulate. Le coordinate di posizione nel simulatore vengono convertite nelle dimensioni e nella risoluzione del dispositivo selezionate.

> [!NOTE]
> Puoi salvare le versioni ridimensionate delle immagini bitmap nell'app. Windows caricherà l'immagine corretta per la scala corrente. Per altre informazioni, vedere Introduzione alla progettazione [e all'interfaccia utente.](/windows/uwp/layout/design-and-ui-intro) Tuttavia, se modifichi la risoluzione del simulatore in modo Windows selezioni un'immagine diversa in base alla risoluzione, dovrai arrestare e riavviare la sessione di debug per visualizzare la nuova immagine.

## <a name="capture-a-screenshot-of-your-app-for-submission-to-microsoft-store"></a><a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Acquisire uno screenshot dell'app per l'invio a Microsoft Store
 Quando si invia un'app Microsoft Store, è necessario includere screenshot dell'app.

> [!NOTE]
> La schermata viene salvato con la risoluzione corrente del simulatore. Per modificare la risoluzione, scegli il pulsante **Cambia risoluzione** .

- Per creare schermate dell'app dal simulatore, scegli il pulsante **Acquisisce la schermata negli Appunti** .

- Per impostare il percorso in cui si trovano la schermate, scegliere il pulsante **Impostazioni cattura di schermata** e scegliere il percorso dal menu di scelta rapida.

   ![Menu di scelta rapida Impostazioni cattura di schermata](../debugger/media/simulator_screenshotsettingscntxmnu.png)

## <a name="simulate-network-connection-properties"></a><a name="BKMK_Simulate_network_connection_properties"></a> Simulare le proprietà di connessione di rete

È possibile consentire agli utenti dell'app di gestire il costo delle connessioni di rete a consumo mantenendo il controllo sulle modifiche dello stato relative ai costi della connessione di rete o del piano dati e consentendo all'app di usare queste informazioni per evitare di dover sostenere costi aggiuntivi per il roaming o il superamento di un limite di trasferimento dati specificato. Le API [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) consentono di rispondere agli eventi [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) e [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) che consentono l'accesso. Vedere [Guida introduttiva: Gestione dei vincoli di costo per le reti a consumo](/previous-versions/windows/apps/hh750310(v=win.10)).

Per eseguire il debug o il test del codice in grado di rilevare i costi di rete, il simulatore può simulare le proprietà di una rete esposte tramite l'oggetto [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) restituito da [GetInternetConnectionProfile](/uwp/api/windows.networking.connectivity.networkinformation).

Per simulare le proprietà di rete:

1. Sulla barra degli strumenti del simulatore scegliere **Modifica proprietà di rete** .

2. Nella finestra di dialogo **Imposta proprietà di rete** selezionare **Usa proprietà di rete simulate**.

    Deseleziona la casella di controllo per rimuovere la simulazione e tornare alle proprietà di rete dell'interfaccia attualmente connessa.

3. Immetti un **Nome profilo** per la rete simulata. È consigliabile usare un nome univoco che consenta di identificare la simulazione nella proprietà [ProfileName](/uwp/api/windows.networking.connectivity.connectionprofile) dell'oggetto [ConnectionProfile](/uwp/api/windows.networking.connectivity.connectionprofile) .

4. Selezionare il valore [NetworkCostType](/uwp/api/windows.networking.connectivity.networkcosttype) per il profilo dall'elenco **Tipo costo rete** .

5. Dall'elenco **Flag di stato limite dati** si può impostare la proprietà [ApproachingDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) o [OverDataLimit](/uwp/api/windows.networking.connectivity.connectioncost) su true oppure scegliere **Limite dati non superato** per impostare entrambi i valori su false.

6. Dall'elenco **Stato roaming** impostare la proprietà [Roaming](/uwp/api/windows.networking.connectivity.connectioncost) .

7. Scegliere **Imposta proprietà** per simulare le proprietà di rete generando un evento [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) in primo piano e un [SystemTrigger](/uwp/api/windows.applicationmodel.background.systemtrigger) in background di tipo **NetworkStateChange**.

Per altre informazioni sulla gestione delle connessioni di rete, vedere:

[Guida introduttiva: Gestione dei vincoli di costo per le reti a consumo](/previous-versions/windows/apps/hh750310(v=win.10))

[Esempio di informazioni di rete](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)

::: moniker range="vs-2017"
[Analizzare il consumo di energia](../profiling/analyze-energy-use-in-store-apps.md)
::: moniker-end

[Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)

[Come rispondere agli eventi di sistema con attività in background](/previous-versions/windows/apps/hh977058(v=win.10))

[Come attivare eventi di sospensione, ripresa e background nelle app UWP](how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

## <a name="navigate-the-simulator-with-the-keyboard"></a><a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Spostarsi nel simulatore con la tastiera

È possibile spostarsi sulla barra degli strumenti del simulatore premendo **CTRL+ALT+FRECCIA** SU per spostare lo stato attivo dalla finestra del simulatore alla barra degli strumenti del simulatore. Utilizza **Freccia su** e **Freccia giù** per spostarti tra i pulsanti della barra degli strumenti.

È possibile arrestare il simulatore premendo **CTRL+ALT+F4.**

## <a name="see-also"></a>Vedi anche

- [Eseguire app da Visual Studio](debugging-windows-store-and-windows-universal-apps.md)