---
title: Eseguire app di Windows Store nel simulatore | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 81b69bf8-ec87-4bb6-9ad4-1fa7b7802d16
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d072f54dfe351d54e3e115dca7a91bec77fbb9e6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844921"
---
# <a name="run-windows-store-apps-in-the-simulator"></a>Eseguire applicazioni Windows Store nel simulatore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il simulatore di Visual Studio per le app di Windows Store è un'applicazione desktop che simula un'app di Windows Store. È possibile eseguire le applicazioni e simulare i comuni eventi di rotazione e tocco nel computer di sviluppo. Si possono anche scegliere le dimensioni fisiche dello schermo e la risoluzione da emulare e simulare le proprietà di connessione di rete.  
  
 Il simulatore offre un ambiente in cui progettare, sviluppare, eseguire il debug e testare le app di Windows Store. Tuttavia, prima di pubblicare l'app in Windows Store, ti consigliamo di testare l'app in un dispositivo reale.  
  
 Il simulatore di Visual Studio per le app di Windows Store non viene eseguito in un ambiente isolato nel computer locale. Di conseguenza, gli errori che si verificano nel simulatore, ad esempio un errore irreversibile a livello di sistema, possono influire anche sull'intero computer.  
  
 Per altre informazioni su Windows Phone vedi [Run Windows Phone apps in the emulator](../debugger/run-windows-phone-apps-in-the-emulator.md) .  
  
> [!IMPORTANT]
> Il simulatore di Visual Studio 2015 non include il pulsante Georilevazione perché il simulatore di Windows 10 non prevede la simulazione di georilevazione. Se è necessario eseguire questo tipo di simulazione, si può usare il simulatore di Visual Studio 2013 in Windows 8.1 o sistemi operativi precedenti.  
  
## <a name="BKMK_Set_the_simulator_as_the_target"></a> Impostare il simulatore come destinazione  
 Per eseguire l'app di Windows Store nel simulatore, scegli **Simulatore** dall'elenco a discesa accanto al pulsante **Avvia debug** sulla barra degli strumenti **Standard** del debugger.  
  
 ![Esecuzione nel simulatore](../debugger/media/vsrun-f5-simulator.png "VSRUN_F5_Simulator")  
  
## <a name="BKMK_Choose_an_interaction_mode"></a> Scegliere una modalità di interazione  
 È possibile scegliere le modalità di interazione seguenti  
  
- ![Pulsante modalità mouse](../debugger/media/simulator-mousemodebtn.png "SIMULATOR_MouseModeBtn") Modalità mouse: imposta la modalità di interazione sui movimenti del mouse. I movimenti del mouse includono clic, doppio clic e trascinamento.  
  
- ![Pulsante di avvio emulazione tocco](../debugger/media/simulator-starttouchemulationbtn.png "SIMULATOR_StartTouchEmulationBtn") Emulazione tocco di avvio: imposta la modalità di interazione sui movimenti tocco di un singolo dito. Gli eventi di un singolo dito includono tocco, trascinamento e scorrimento rapido.  
  
     ![Simulatore di destinazione di un dito](../debugger/media/simulator-onefinger.png "SIMULATOR_OneFinger") La singola icona di destinazione indica la posizione degli eventi nel simulatore. Usa il mouse per posizionare il puntatore.  
  
     ![Destinazione tocco di un dito](../debugger/media/simulator-onefingerengaged.png "SIMULATOR_OneFingerEngaged") Premere il pulsante sinistro del mouse per attivare la modalità tocco. Ad esempio, fai clic sul pulsante per simulare un tocco o premi e tieni premuto il pulsante mentre trascini o scorri rapidamente.  
  
## <a name="pinch-and-zoom"></a>Zoom indietro/avanti  
 Imposta la modalità di interazione per i movimenti zoom indietro e avanti di due dita.  
  
- ![Simulatore di destinazione due dita](../debugger/media/simulator-twofinger.png "SIMULATOR_TwoFinger")  

  - La doppia icona di destinazione indica la posizione di due dita sullo schermo del dispositivo.  

  - Sposta il mouse per posizionare le icone sopra l'oggetto sullo schermo del dispositivo.  

  - Ruota la rotellina del mouse avanti o indietro per modificare la distanza simulata delle due dita prima di eseguire il movimento zoom avanti o indietro.  

- ![Destinazioni Pinch, zoom e rotate](../debugger/media/simulator-twofingerengaged.png "SIMULATOR_TwoFingerEngaged")  

  - Premi il pulsante sinistro e ruota la rotellina indietro (verso di te) per fare zoom avanti.  

  - Premi il pulsante sinistro e ruota la rotellina del mouse in avanti (lontano da te) per fare zoom indietro.  
  
## <a name="object-rotation"></a>Rotazione di oggetti  
 Il pulsante **Rotazione emulazione tocco** imposta la modalità di interazione sui movimenti di rotazione usando due dita.  
  
- Sposta il mouse per posizionare le icone sopra l'oggetto sullo schermo del dispositivo.  
  
  - Ruota la rotellina del mouse avanti o indietro per modificare l'orientamento simulato delle due dita prima di ruotare l'oggetto.  

- Premi il pulsante sinistro e ruota la rotellina indietro (verso di te) per ruotare l'oggetto in senso antiorario. Mente ruoti la rotella del mouse, una delle due icone di destinazione ruota intorno all'altra per indicare la dimensione relativa della rotazione.  

  - Premi il pulsante sinistro e ruota la rotellina del mouse avanti (lontano di te) per ruotare l'oggetto in senso orario.  

## <a name="BKMK_Enable_or_disable_Always_on_top_mode"></a> Abilitare o disabilitare la modalità Sempre in primo piano  
 Puoi impostare la finestra del simulatore in modo che sia sempre in primo piano rispetto ad altre finestre. Il pulsante **Attiva/disattiva finestra in primo piano** abilita o disabilita la modalità **Sempre in primo piano** della finestra del simulatore.  
  
## <a name="BKMK_Change_the_device_orientation"></a> Modificare l'orientamento del dispositivo  
 Puoi modificare l'orientamento verticale e orizzontale del dispositivo ruotando il simulatore di 90 gradi in qualsiasi direzione.  
  
> [!NOTE]
> Il simulatore non rispetta la proprietà [DisplayProperties.AutoRotationPreferences](https://msdn.microsoft.com/library/windows/apps/windows.graphics.display.displayproperties.autorotationpreferences.aspx) di un progetto. Ad esempio, se il progetto imposta l'orientamento su `Landscape`e quindi ruoti il simulatore sull'orientamento verticale, anche l'immagine visualizzata dal simulatore sarà ruotata e ridimensionata. Verifica queste impostazioni su un dispositivo reale.  
  
> [!NOTE]
> Se ruoti il simulatore in modo che un suo bordo sia più largo dello schermo su cui viene visualizzato, il simulatore verrà ridimensionato automaticamente in base alle dimensioni dello schermo. Le dimensioni originali non vengono ripristinate se ruoti di nuovo il simulatore.  
  
## <a name="BKMK_Change_the_simulated_screen_size_and_resolution"></a> Modificare le dimensioni e la risoluzione dello schermo simulate  
 Per modificare le dimensioni e la risoluzione dello schermo simulate, scegliere il pulsante **Cambia risoluzione** nella tavolozza e scegliere una nuova dimensione e una nuova risoluzione dall'elenco.  
  
 Le dimensioni e la risoluzione dello schermo sono elencate come *Larghezza schermo in pollici, larghezza in pixel X altezza in pixel*. Come noterai, le dimensioni e la risoluzione dello schermo sono simulate. Le coordinate della posizione nel simulatore vengono convertite nelle coordinate delle dimensioni e della risoluzione del dispositivo selezionato.  
  
> [!NOTE]
> Puoi salvare le versioni ridimensionate delle immagini bitmap nell'app. Windows caricherà l'immagine corretta per la scala corrente. Per altre informazioni, vedere [Tutto sul responsive design per app UWP (Universal Windows Platform)](https://msdn.microsoft.com/library/windows/apps/dn958435.aspx). Tuttavia, se modifichi la risoluzione del simulatore in modo Windows selezioni un'immagine diversa in base alla risoluzione, dovrai arrestare e riavviare la sessione di debug per visualizzare la nuova immagine.  
  
## <a name="BKMK_Capture_a_screenshot_of_your_app_for_submission_to_the_Microsoft_Store"></a> Acquisire una schermata dell'app da inviare a Windows Store  
 Quando si invia un'applicazione all'archivio applicazioni di Windows, è necessario includere alcune schermate dell'app.  
  
> [!NOTE]
> La schermata viene salvata con la risoluzione corrente del simulatore. Per modificare la risoluzione, scegli il pulsante **Cambia risoluzione** .  
  
- Per creare schermate dell'app dal simulatore, scegli il pulsante **Acquisisce la schermata negli Appunti** .  
  
- Per impostare il percorso in cui si trovano la schermate, scegliere il pulsante **Impostazioni cattura di schermata** e scegliere il percorso dal menu di scelta rapida.  
  
     ![Menu di scelta rapida impostazioni screenshot](../debugger/media/simulator-screenshotsettingscntxmnu.png "SIMULATOR_ScreenShotSettingsCntxMnu")  
  
## <a name="BKMK_Simulate_network_connection_properties"></a> Simulare le proprietà di connessione di rete  
 Puoi consentire agli utenti dell'app di gestire il costo delle connessioni di rete a consumo mantenendo il controllo sulle modifiche dello stato relative ai costi della connessione di rete o del piano dati e consentendo all'app di usare queste informazioni per evitare di dover sostenere costi aggiuntivi per il roaming o il superamento di un limite di trasferimento dati specificato. Le API [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx) consentono di rispondere agli eventi [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) e [TriggerType](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.triggertype.aspx) che consentono l'accesso. Vedere [Guida introduttiva: Gestione dei vincoli di costo per le reti a consumo](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx).  
  
 Per eseguire il debug o il test del codice in grado di rilevare i costi di rete, il simulatore può simulare le proprietà di una rete esposte tramite l'oggetto [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) restituito da [GetInternetConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.getinternetconnectionprofile.aspx).  
  
 Per simulare le proprietà di rete:  
  
1. Sulla barra degli strumenti del simulatore scegliere **Modifica proprietà di rete** .  
  
2. Nella finestra di dialogo **Imposta proprietà di rete** selezionare **Usa proprietà di rete simulate**.  
  
    Deseleziona la casella di controllo per rimuovere la simulazione e tornare alle proprietà di rete dell'interfaccia attualmente connessa.  
  
3. Immetti un **Nome profilo** per la rete simulata. È consigliabile usare un nome univoco che consenta di identificare la simulazione nella proprietà [ProfileName](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.profilename.aspx) dell'oggetto [ConnectionProfile](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectionprofile.aspx) .  
  
4. Selezionare il valore [NetworkCostType](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkcosttype.aspx) per il profilo dall'elenco **Tipo costo rete** .  
  
5. Dall'elenco **Flag di stato limite dati** si può impostare la proprietà [ApproachingDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.approachingdatalimit.aspx) o [OverDataLimit](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.overdatalimit.aspx)su true oppure scegliere **Limite dati non superato** per impostare entrambi i valori su false.  
  
6. Dall'elenco **Stato roaming** impostare la proprietà [Roaming](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.connectioncost.roaming.aspx) .  
  
7. Scegliere **Imposta proprietà** per simulare le proprietà di rete generando un evento [NetworkStatusChanged](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.networkinformation.networkstatuschanged.aspx) in primo piano e un [SystemTrigger](https://msdn.microsoft.com/library/windows/apps/windows.applicationmodel.background.systemtrigger.aspx) in background di tipo **NetworkStateChange**.  
  
   **Altre informazioni sulla gestione delle connessioni di rete**  
  
   [Guida introduttiva: Gestione dei vincoli di costo per le reti a consumo](https://msdn.microsoft.com/library/windows/apps/Hh750310.aspx)  
  
   [Esempio di informazioni di rete](https://code.msdn.microsoft.com/windowsapps/Network-Information-Sample-63aaa201)  
  
   [Analizzare il consumo di energia](../profiling/analyze-energy-use-in-store-apps.md)  
    
   [Windows.Networking.Connectivity](https://msdn.microsoft.com/library/windows/apps/windows.networking.connectivity.aspx)  
  
   [Come rispondere agli eventi di sistema con attività in background](https://msdn.microsoft.com/f7c86e86-a7ae-4abb-a923-76b03337a80a)  
  
   [Come attivare eventi di sospensione, ripresa e background nelle app di Windows Store](https://msdn.microsoft.com/library/windows/apps/hh974425.aspx)  
  
## <a name="BKMK_Navigate_the_simulator_with_the_keyboard"></a> Spostarsi nel simulatore con la tastiera  
 Per spostarsi nella barra degli strumenti del simulatore, premere **CTRL+ALT+Freccia SU** per spostare lo stato attivo dalla finestra del simulatore alla barra degli strumenti del simulatore. Utilizza **Freccia su** e **Freccia giù** per spostarti tra i pulsanti della barra degli strumenti.  
  
 È possibile arrestare il simulatore premendo **CTRL+ALT+F4**.  
  
## <a name="see-also"></a>Vedere anche  
 [Eseguire app da Visual Studio](../debugger/run-store-apps-from-visual-studio.md)
