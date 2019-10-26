---
title: Eseguire app UWP nel simulatore | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: ae0b559f4684fd4fd8b9eabff4b46b1defb5ef1f
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911333"
---
# <a name="run-uwp-apps-in-the-simulator"></a>Eseguire app UWP nel simulatore

Il simulatore di Visual Studio per le app UWP è un'applicazione desktop che simula un'app UWP. In genere, è necessario eseguire il debug nel computer locale, in un dispositivo connesso o in un computer remoto. Tuttavia, in alcuni scenari, può essere utile usare il simulatore di Visual Studio per emulare una dimensione e una risoluzione dello schermo fisico diverse. È anche possibile simulare eventi di tocco e rotazione comuni e simulare le proprietà di connessione di rete.

Il simulatore offre un ambiente in cui è possibile progettare, sviluppare, eseguire il debug e testare le app UWP. Tuttavia, prima di pubblicare l'app in Microsoft Store, è necessario testare l'app in un dispositivo reale.

Il simulatore di Visual Studio per le app UWP non viene eseguito in un ambiente isolato nel computer locale. Di conseguenza, gli errori che si verificano nel simulatore, ad esempio un errore irreversibile a livello di sistema, può influenzare l'intero computer.

> [!IMPORTANT]
> Il simulatore di Visual Studio 2015 non include il pulsante Georilevazione perché il simulatore di Windows 10 non prevede la simulazione di georilevazione.

## <a name="BKMK_Set_the_simulator_as_the_target"></a> Impostare il simulatore come destinazione

Per eseguire l'app UWP nel simulatore, selezionare **simulatore** nell'elenco a discesa accanto al pulsante **Avvia debug** sulla barra degli strumenti **standard** del debugger. Questa opzione è disponibile solo se la **versione minima della piattaforma di destinazione** dell'app è inferiore o uguale al sistema operativo del computer di sviluppo.

![Esecuzione nel simulatore](../debugger/media/vsrun_f5_simulator.png "VSRUN_F5_Simulator")

## <a name="BKMK_Choose_an_interaction_mode"></a> Scegliere una modalità di interazione

È possibile scegliere le modalità di interazione seguenti:

- ![Pulsante modalità mouse](../debugger/media/simulator_mousemodebtn.png "SIMULATOR_MouseModeBtn") Modalità mouse: imposta la modalità di interazione sui movimenti del mouse. I movimenti del mouse includono clic, doppio clic e trascinamento.

- ![Pulsante di avvio emulazione tocco](../debugger/media/simulator_starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Emulazione tocco di avvio: imposta la modalità di interazione sui movimenti tocco di un singolo dito. Gli eventi di un singolo dito includono tocco, trascinamento e scorrimento rapido.

   ![Simulatore di destinazione di un dito](../debugger/media/simulator_onefinger.png "SIMULATOR_OneFinger")
   
   L'icona di bersaglio singolo indica la posizione degli eventi nel simulatore. Usa il mouse per posizionare il puntatore.

   ![Destinazione tocco di un dito](../debugger/media/simulator_onefingerengaged.png "SIMULATOR_OneFingerEngaged")
   
   Premere il pulsante sinistro del mouse per attivare la modalità tocco. Ad esempio, fai clic sul pulsante per simulare un tocco o premi e tieni premuto il pulsante mentre trascini o scorri rapidamente.

## <a name="pinch-and-zoom"></a>Zoom indietro/avanti

Imposta la modalità di interazione per i movimenti zoom indietro e avanti di due dita.

![Simulatore di destinazione due dita](../debugger/media/simulator_twofinger.png)

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

## <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Abilitare o disabilitare la modalità Sempre in primo piano
 Puoi impostare la finestra del simulatore in modo che sia sempre in primo piano rispetto ad altre finestre. Il pulsante **Attiva/disattiva finestra in primo piano** abilita o disabilita la modalità **Sempre in primo piano** della finestra del simulatore.

## <a name="BKMK_Change_the_device_orientation"></a> Modificare l'orientamento del dispositivo
 Puoi modificare l'orientamento verticale e orizzontale del dispositivo ruotando il simulatore di 90 gradi in qualsiasi direzione.

> [!NOTE]
> Il simulatore non rispetta la proprietà [DisplayProperties.AutoRotationPreferences](/uwp/api/Windows.Graphics.Display.DisplayProperties#Windows_Graphics_Display_DisplayProperties_AutoRotationPreferences) di un progetto. Ad esempio, se il progetto imposta l'orientamento su `Landscape`e quindi ruoti il simulatore sull'orientamento verticale, anche l'immagine visualizzata dal simulatore sarà ruotata e ridimensionata. Verifica queste impostazioni su un dispositivo reale.

> [!NOTE]
> Se ruoti il simulatore in modo che un suo bordo sia più largo dello schermo su cui viene visualizzato, il simulatore verrà ridimensionato automaticamente alle dimensioni dello schermo. Il simulatore non viene ripristinato alla dimensione originale se lo ruoti di nuovo.

## <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Modificare le dimensioni e la risoluzione dello schermo simulate
 Per modificare le dimensioni e la risoluzione dello schermo simulate, scegliere il pulsante **Cambia risoluzione** nella tavolozza e scegliere una nuova dimensione e una nuova risoluzione dall'elenco.

 Le dimensioni e la risoluzione dello schermo sono elencate come *Larghezza schermo in pollici, larghezza in pixel X altezza in pixel*. Come noterai, le dimensioni e la risoluzione dello schermo sono simulate. Le coordinate della posizione nel simulatore vengono convertite nelle dimensioni e nella risoluzione selezionate del dispositivo.

> [!NOTE]
> Puoi salvare le versioni ridimensionate delle immagini bitmap nell'app. Windows caricherà l'immagine corretta per la scala corrente. Per altre informazioni, vedere [Introduzione alla progettazione e all'interfaccia utente](/windows/uwp/layout/design-and-ui-intro). Tuttavia, se modifichi la risoluzione del simulatore in modo Windows selezioni un'immagine diversa in base alla risoluzione, dovrai arrestare e riavviare la sessione di debug per visualizzare la nuova immagine.

## <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a>Acquisire una schermata dell'app per l'invio a Microsoft Store
 Quando si invia un'app a Microsoft Store, è necessario includere screenshot dell'app.

> [!NOTE]
> La schermata viene salvato con la risoluzione corrente del simulatore. Per modificare la risoluzione, scegli il pulsante **Cambia risoluzione** .

- Per creare schermate dell'app dal simulatore, scegli il pulsante **Acquisisce la schermata negli Appunti** .

- Per impostare il percorso in cui si trovano la schermate, scegliere il pulsante **Impostazioni cattura di schermata** e scegliere il percorso dal menu di scelta rapida.

   ![Menu di scelta rapida Impostazioni cattura di schermata](../debugger/media/simulator_screenshotsettingscntxmnu.png)

## <a name="BKMK_Simulate_network_connection_properties"></a> Simulare le proprietà di connessione di rete

È possibile consentire agli utenti dell'app di gestire il costo delle connessioni di rete a consumo mantenendo il controllo sulle modifiche dello stato relative ai costi della connessione di rete o del piano dati e consentendo all'app di usare queste informazioni per evitare di dover sostenere costi aggiuntivi per il roaming o il superamento di un limite di trasferimento dati specificato. Le API [Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity) consentono di rispondere agli eventi [NetworkStatusChanged](/uwp/api/windows.networking.connectivity.networkinformation) e [TriggerType](/uwp/api/windows.applicationmodel.background.systemtrigger) che consentono l'accesso. Vedere [Guida introduttiva: Gestione dei vincoli di costo per le reti a consumo](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).

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

Per ulteriori informazioni sulla gestione delle connessioni di rete, vedere:

[Guida introduttiva: Gestione dei vincoli di costo per le reti a consumo](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)

[Esempio di informazioni di rete](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)

[Analizzare il consumo di energia](../profiling/analyze-energy-use-in-store-apps.md)

[Windows.Networking.Connectivity](/uwp/api/windows.networking.connectivity)

[Come rispondere agli eventi di sistema con attività in background](/previous-versions/windows/apps/hh977058(v=win.10))

[Come attivare eventi di sospensione, ripresa e background nelle app UWP](how-to-trigger-suspend-resume-and-background-events-for-windows-store-apps-in-visual-studio.md)

## <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Spostarsi nel simulatore con la tastiera

È possibile spostarsi sulla barra degli strumenti del simulatore premendo **CTRL + ALT + freccia su** per spostare lo stato attivo dalla finestra del simulatore alla barra degli strumenti del simulatore. Utilizza **Freccia su** e **Freccia giù** per spostarti tra i pulsanti della barra degli strumenti.

È possibile arrestare il simulatore premendo **CTRL + ALT + F4**.

## <a name="see-also"></a>Vedere anche

- [Eseguire app da Visual Studio](/visualstudio/debugger/debugging-windows-store-and-windows-universal-apps)
