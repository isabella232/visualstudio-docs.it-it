---
title: Risoluzione dei problemi di Visual Studio Emulator for Android | Microsoft Docs
description: Informazioni utili per risolvere i problemi che possono verificarsi quando si usa Visual Studio Emulator per Android.
ms.custom: SEO-VS-2020
ms.prod: visual-studio-dev15
ms.date: 11/04/2016
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: f3fb5df4-3aae-40e4-9450-bbe15b0c5af5
author: conceptdev
ms.author: crdun
manager: crdun
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 62c2b69edf6868d1559df2a861a85e286f8ffa15
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631661"
---
# <a name="troubleshoot-the-visual-studio-emulator-for-android"></a>Risolvere i problemi di Visual Studio Emulator for Android
Questo argomento contiene informazioni che consentono di risolvere i problemi che possono verificarsi quando si usa Visual Studio Emulator for Android.

> [!WARNING]
> Quando l'emulatore è installato, il programma di installazione verifica i prerequisiti per l'esecuzione del software. Se i prerequisiti non sono presenti, visualizza degli avvisi ma non richiede i prerequisiti per l’installazione.

 In questo argomento sono contenute le sezioni seguenti.

- [Prima di iniziare](#BeforeYouStart)

- [Emulator non è possibile installare](#NoInstall)

- [Non è possibile connettersi a destinazioni di rete in un dominio o in una rete aziendale](#DomainNetwork)

- [Impossibile connettersi alle destinazioni di rete quando le impostazioni di rete richiedono la configurazione manuale](#ManualNetworkConfig)

- [Emulator si avvia lentamente, l'avvio non riesce a causa di un timeout o la distribuzione dell'app non riesce](#SlowStart)

- [Non si avvia emulatore](#NoStart2)

- [Emulator non si avvia (primo utilizzo)](#NoStart)

- [L'avvio del computer non riesce dopo l'installazione del Emulator](#NoBoot)

- [Visual Studio si blocca durante il tentativo di distribuire l'app nell'emulatore o l'emulatore non viene visualizzato come destinazione di debug in altri ID](#ADB)

- [Emulator smette di rispondere perché non è stato possibile configurare la porta UDP](#XamarinPlayer)

- [Non è possibile collegare un debugger a un progetto Xamarin](#Skylake)

- [Emulatore non viene eseguita l'applicazione che utilizza Google Play Services](#GooglePlay)

- [Il trascinamento di un file, APK o file ZIP che supportano il flashing non funziona](#DragAndDrop)

- [Risoluzione dello screenshot non corretta](#Resolution)

- [Emulatore non riesce a eseguire il rendering OpenGL contenuto](#OpenGL)

- [Emulator non risponde ai movimenti multitocco](#Multitouch)

- [Risorse di supporto](#Support)

## <a name="before-you-start"></a><a name="BeforeYouStart"></a> Prima di iniziare
 Prima di iniziare la risoluzione dei problemi, potrebbe essere utile consultare gli argomenti seguenti:

- [Requisiti di sistema per Visual Studio Emulator per Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)

## <a name="emulator-fails-to-install"></a><a name="NoInstall"></a> Non è possibile installare l'emulatore
 Se Hyper-V non è installato, quando si prova a installare l'emulatore verrà visualizzato un messaggio analogo al seguente. È necessario avere un computer che supporta HyperV e che HyperV sia abilitato.

 ![Screenshot di un messaggio Visual Studio che indica che l'installazione è bloccata per Microsoft Visual Studio Emulator for Android perché il computer non esegue il controllo di Hyper-V.](../cross-platform/media/android_emu_install_issue.png "Android_Emu_Install_Issue")

> [!NOTE]
> Questo messaggio è applicabile a Visual Studio Emulator for Android e all'emulatore Windows Phone. Windows 8.1 e Windows 10 supportano l'emulatore.

 Se viene visualizzato questo messaggio, vedere i [Requisiti di sistema per Visual Studio Emulator for Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md) per verificare se è possibile eseguire l'emulatore.

## <a name="cannot-connect-to-network-destinations-on-a-domain-or-corporate-network"></a><a name="DomainNetwork"></a> Impossibile connettersi alle destinazioni di rete in un dominio o di una rete aziendale
 L'emulatore Visual Studio viene visualizzato sulla rete come un dispositivo distinto con il proprio indirizzo IP. Non è stato aggiunto a un dominio Windows e non condivide le credenziali di dominio o gruppo di lavoro con il computer host.

 Se la rete richiede l'autorizzazione di dominio o gruppo di lavoro per la rete di base e la connettività Internet, contattare l'amministratore IT per un'eccezione. Questa eccezione consente al computer di sviluppo per fungere da una macchina di limiti e accettare connessioni dai dispositivi di rete non aggiunto al dominio come l'emulatore.

 Emulatore di Visual Studio per Android utilizza inoltre un proprio set di indirizzi MAC. Se dall'emulatore non è possibile accedere alla rete o alle risorse Internet, rivolgersi all'amministratore IT per assicurarsi che gli indirizzi MAC dell'emulatore siano stati autorizzati sulla rete.

#### <a name="to-view-the-emulators-mac-addresses"></a>Per visualizzare gli indirizzi MAC dell'emulatore

1. Avviare l'emulatore

2. Nella barra degli strumenti dell'emulatore, fare clic sul pulsante freccia di espansione (>>) per aprire la finestra di strumenti aggiuntivi.

3. Nella finestra Strumenti aggiuntivi, fare clic sulla scheda di rete.

4. Nella pagina rete individuare le voci di indirizzo fisico.

## <a name="cannot-connect-to-network-destinations-when-network-settings-require-manual-configuration"></a><a name="ManualNetworkConfig"></a> Impossibile connettersi a destinazioni di rete quando le impostazioni di rete richiedono la configurazione manuale
 Per connettersi alle destinazioni di rete dall'emulatore, la rete deve soddisfare i requisiti seguenti:

- DHCP L'emulatore richiede DHCP perché viene configurato automaticamente come un dispositivo separato sulla rete con il relativo indirizzo IP.

- Impostazioni di DNS e gateway configurate automaticamente Non è possibile configurare manualmente le impostazioni di DNS e gateway per l'emulatore.

  Se la rete richiede impostazioni configurate manualmente, rivolgersi all'amministratore IT di determinare come è possibile abilitare la connettività di rete per l'emulatore.

## <a name="emulator-starts-slowly-fails-to-start-due-to-a-timeout-or-app-deployment-fails"></a><a name="SlowStart"></a> Emulatore viene avviato lentamente, non viene avviato a causa di un timeout o errore di distribuzione di applicazioni
 In determinate condizioni, l'emulatore richiede alcuni minuti per avviare o non viene avviato a causa di un timeout. Se l'emulatore non viene avviato, viene visualizzato il seguente messaggio: Distribuzione dell’applicazione non riuscita:`App deployment failed. Please try again` Le condizioni seguenti possono causare questo errore.

- Attivare l’emulatore di Visual Studio per Android da un VHD bootable. Questa configurazione non è supportata.

- Un disco rigido difettoso. Si consiglia di eseguire il programma chkdsk.

- Un disco rigido che deve essere deframmentato. Eseguire la deframmentazione dell'unità.

- Un disco rigido è quasi completo. Controllare lo spazio disponibile sul disco.

- Memoria insufficiente è disponibile a causa di altre applicazioni in esecuzione. Ridurre il numero di applicazioni che utilizzano la memoria o aumentare la quantità di memoria.

- In generale, qualsiasi fattore che contribuisce a ridurre le prestazioni di sistema. Iniziare la risoluzione dei problemi con il componente con il punteggio secondario più basso nell'indice prestazioni Windows, disponibile nella pagina strumenti e informazioni sulle prestazioni del Pannello di controllo.

## <a name="emulator-fails-to-start"></a><a name="NoStart2"></a>Emulator non viene avviato
 Se l'emulatore funzionava in precedenza ma non funziona più, eseguire le attività seguenti. Se si usa l'emulatore per la prima volta, vedere [Emulator fails to start (first use)](#NoStart) prima di seguire questa procedura.

- Rimuovere eventuali altre istanze Hyper-V dell'emulatore.

    1. Chiudere Visual Studio.

    2. Aprire la Console di gestione di Hyper-V e arrestare eventuali istanze di Hyper-V dell'emulatore (macchine virtuali) già in esecuzione e che potrebbero avere uno stato danneggiato.

    3. Nella Console di gestione di Hyper-V eliminare eventuali altre VM dell'emulatore.

    4. Riavvia il computer.

- Verificare che siano disponibili almeno 4 GB di memoria di sistema e che la memoria non venga usata da altri programmi e processi che richiedono molte risorse (ad esempio, provare a chiudere le finestre del browser).

- Nella Console di gestione di Hyper-V aprire Gestione commutatori virtuali e verificare la disponibilità di due commutatore di rete. Assicurarsi che il primo sia il commutatore interno e che il secondo sia esterno.

     ![Screenshot di Gestione commutatore virtuale nella console di gestione di Hyper-V. Un nuovo commutatore virtuale è evidenziato e le relative proprietà indicano che si tratta di un commutatore di rete esterno.](../cross-platform/media/android_emu_v_switch_man.png "Android_Emu_V_Switch_Man")

     Se l'installazione non è corretta e si usa Windows 10, è possibile provare a [reinstallare i dispositivi di rete con il comando netcfg -d](https://support.microsoft.com/help/10741/windows-fix-network-connection-issues) (sezione 6).

- Se questa procedura non consente di risolvere il problema, vedere [Emulator fails to start (first use)](#NoStart) per informazioni su software di terze parti che potrebbe interferire con l'emulatore.

## <a name="emulator-fails-to-start-first-use"></a><a name="NoStart"></a> Emulator fails to start (first use)
 Se non viene avviato l'emulatore, eseguire le attività seguenti per identificare e risolvere il problema.

- Assicurarsi che vengano soddisfatti i requisiti hardware minimi e che le impostazioni del BIOS siano corrette.

   L'emulatore e Windows 8 Hyper-V richiede un processore a 64 bit con secondo livello SLAT (Address Translation). Per Intel è necessario essenzialmente un processore Core i3, i5 o i7 (o uno dei molti processori Xeon). Un elenco dei chip AMD è disponibile [qui](https://www.amd.com/en/support).

  1. Assicurarsi che il computer in uso soddisfi i [requisiti di sistema](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).

  2. Verificare che lo [strumento SLAT](https://slatstatuscheck.codeplex.com/) indichi che il computer supporta SLAT.

  3. All'interno delle impostazioni del BIOS del computer, assicurarsi che tutte le tecnologie di virtualizzazione sono abilitata. Le descrizioni del BIOS esatte possono variare per ogni produttore di hardware. In generale, abilitare le funzionalità correlate a:

     - SLAT (Conversione indirizzi di secondo livello)

     - Accetta (Extended Page Tables) (Intel)

     - TNP (pagina nidificata tabelle) (AMD)

     - RVI (Rapid Virtualization Indexing) (AMD)

     - VMX (Intel acronimo che indica il supporto per la virtualizzazione hardware assistita)

     - SVM (un acronimo AMD che indica il supporto per la virtualizzazione hardware assistita)

     - XD (Execute Disable) (Intel); questo deve essere abilitato

     - NX (nessuna Execute)(AMD); deve essere abilitato.

  4. Se le opzioni seguenti sono presenti nel BIOS, disabilitarli.

     - Disabilitare la tecnologia Intel VT-d

     - Disabilitare esecuzione Trusted

       Per ulteriori informazioni, vedere l'articolo: Technet: come Hyper-v: per correggere BIOS errori abilitazione di Hyper-V

  5. Assicurarsi di che disporre di almeno 4 GB di memoria di sistema e che non viene utilizzato da altri programmi che richiedono molte risorse e processi.

  6. Assicurarsi che si esegue Windows 8 Professional o migliori (Windows Server 2008 non è supportato). Windows Server 2012 è supportato, ma è necessario abilitare esperienza Desktop.

     È possibile controllare il Visualizzatore eventi per vedere se sono presenti errori di Hypervisor. A tale scopo, aprire Visualizzatore eventi (**Tasto** start R , quindi digitare ) e quindi selezionare Windows + Logs `eventvwr` , **System**.  Quindi filtrare il registro eventi dall'origine evento, impostando l'origine su **Hypervisor Hyper-V**. Controllare gli errori identificare la causa principale.

     Se il soddisfa processore i requisiti minimi ma hypervisor ancora esito negativo, provare a scoprire se è un aggiornamento del BIOS per il computer. Se è presente, e si sceglie di eseguire l'aggiornamento, accertarsi di rispettare tutte le precauzioni dal produttore durante l'aggiornamento del BIOS (ad esempio, per garantire l'aggiornamento del firmware BIOS non è stato interrotto da un'interruzione dell'alimentazione, che può essere danneggiata definitivamente il BIOS).

- Assicurarsi di che disporre di almeno 4 GB di memoria di sistema e che non viene utilizzato da altri programmi che richiedono molte risorse e processi.

- Rimuovere o disabilitare i driver di terze parti o software che potrebbe interferire con la rete virtuale.

   Esistono alcuni problemi noti con alcuni prodotti di terzi installati in Windows 8, ad esempio driver/protocolli di rete che non sono completamente compatibili con lo stack di rete Hyper-V.

   In generale, è compito degli sviluppatori di tali prodotti per l'aggiornamento del software per essere compatibile con Windows 8 e Hyper-V.

   I seguenti prodotti potrebbero richiedere l'aggiornamento per la conformità di Windows 8: VirtualBox, Virtual PC 7, VMWare, alcuni client VPN, i firewall software, alcune versioni di client VPN Cisco e altri sistemi di virtualizzazione. Collaborare con lo sviluppatore del software di virtualizzazione incerta incoraggiarli per aggiornare il software per renderlo compatibile con Windows 8 e Hyper-V.

   Come soluzione *alternativa,* è possibile disabilitare tutti i driver e le applicazioni di terze parti che potrebbero interferire con la rete virtuale usata dal Emulator per comunicare con Visual Studio. Queste applicazioni possono includere:

  - Antivirus applicazioni (hook lo stack di rete)

  - Strumenti di monitoraggio di rete

  - Strumenti di registrazione di rete

  - Altro software di monitoraggio di sistema

    Un'altra possibile soluzione alternativa, se non si disinstallazione dei prodotti nella domanda e che richiede lo sviluppatore di prodotto per rilasciare una versione aggiornata, è necessario eseguire le operazioni seguenti.

  1. Avviare Gestione connessioni di rete (dalla schermata Start digitare `View Network Connections` e selezionare questa opzione per visualizzare le connessioni di rete.)

  2. Per la scheda vEthernet (interno porta Windows Phone emulatore interna Switch Ethernet), scegliere **proprietà** dal menu di scelta rapida.

      ![Scheda virtuale usata da Hyper&#45;V](../cross-platform/media/android_emu_virtual_adapter.png "Android_Emu_Virtual_Adapter")

      Qui vengono visualizzate le proprietà dell'adapter.

      ![Proprietà della scheda virtuale](../cross-platform/media/android_emu_virtual_adapter_properties.png "Android_Emu_Virtual_Adapter_Properties")

  3. Per questo adapter, gli unici elementi che devono essere selezionati in **la connessione utilizza i seguenti elementi** riportato di seguito:

     - Client per reti Microsoft

     - Utilità di pianificazione pacchetti QoS

     - Condivisione file e stampanti per reti Microsoft

     - Driver di protocollo LLDP Microsoft

     - Driver dei / o mapping individuazione topologia livelli di collegamento

     - Risponditore individuazione topologia livelli di collegamento

     - Protocollo Internet versione 6 (TCP/IPv6)

     - Protocollo Internet versione 4 (TCP/IPv4)

  4. Deselezionare tutti gli altri elementi.

     Lo svantaggio di questa tecnica è che ogni volta che un nuovo prodotto di terze parti installa i driver non supportati o ogni volta che viene installato l'emulatore, questi passaggi dovrà essere ripetuta.

     Dopo la disinstallazione di prodotti di terze parti potrebbe essere necessario ripristinare lo Switch interno di Windows Phone emulatore. A tale scopo, eseguire queste operazioni:

  - Aprire Hyper V e andare in Gestione commutatori virtuali. Creare un commutatore virtuale denominato "Windows Phone emulatore interna Switch" e impostarne il tipo di connessione **rete interna**.

     ![Gestione commutatori virtuali](../cross-platform/media/android_emu_virtual_switch_manager.png "Android_Emu_Virtual_Switch_Manager")

    Ora avviare l'emulatore Dovrebbe funzionare.

## <a name="computer-fails-to-boot-after-installing-the-emulator"></a><a name="NoBoot"></a> Computer non riesce a eseguire l'avvio dopo l'installazione dell'emulatore
 Il problema può verificarsi quando vengono soddisfatte le condizioni seguenti:

- Il computer dispone di una scheda madre Gigabyte.

- USB3 è attivato sulla scheda madre.

  Per risolvere questo problema, disabilitare USB3 nelle impostazioni del BIOS della scheda madre e riavviare il computer. Controllare quindi se Gigabyte ha rilasciato un aggiornamento per il BIOS della scheda madre in uso.

  Per altre informazioni, vedere l'articolo della Knowledge Base relativo all' [errore di avvio dopo l'installazione del ruolo Hyper-V in sistemi Gigabyte](https://support.microsoft.com/en-us/kb/2693144).

## <a name="visual-studio-gets-stuck-trying-to-deploy-the-app-to-the-emulator-or-the-emulator-does-not-appear-as-a-debug-target-in-other-ides"></a><a name="ADB"></a> Visual Studio si blocca durante il tentativo di distribuzione dell'app all'emulatore oppure l'emulatore non è visualizzato come destinazione di debug in altri IDE
 Se l'emulatore è in esecuzione, ma non sembra essere connesso ad ADB (Bridge Debug Android) o non è visualizzato negli strumenti di Android che usano ADB, ad esempio Studio Android o Eclipse, potrebbe essere necessario modificare le posizioni in cui l'emulatore cerca ADB. L'emulatore utilizza una chiave del Registro di sistema per identificare il percorso di base dell'Android SDK e cerca il file \platform-tools\adb.exe in tale directory. Per modificare il percorso di Android SDK utilizzato dall'emulatore:

- Aprire l'Editor del Registro di sistema selezionando **eseguire** dall'inizio pulsanti menu di scelta rapida, digitare `regedit` nella finestra di dialogo e scegliendo **OK**.

- Passare a *HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Android SDK Tools* nell'albero delle cartelle a sinistra.

- Modificare il **percorso** variabile del Registro di sistema in base al percorso per il Android SDK.

  Riavviare l'emulatore e a questo punto dovrebbe essere in grado di visualizzare l'emulatore connesso a ADB e relativi strumenti Android.

## <a name="emulator-stops-responding-because-it-couldnt-set-up-the-udp-port"></a><a name="XamarinPlayer"></a>Emulator risponde perché non è stato possibile configurare la porta UDP
 Questo problema può essere dovuto a un'incompatibilità con Xamarin Player. Se l'emulatore sembra bloccarsi o viene visualizzato il messaggio di errore "L'emulatore non è in grado di connettersi al sistema operativo del dispositivo: Non è stato possibile configurare la porta UDP.  quindi alcune funzionalità potrebbero essere disabilitate, è possibile che si stia verificando questo problema. Seguire questa procedura.

1. Disinstallare Xamarin Player.

2. Verificare che la VirtualBox sia stata rimossa. Xamarin Player viene eseguito su una VirtualBox.

3. Passare a Gestione dispositivi, selezionare l'opzione per la visualizzazione dei dispositivi nascosti e quindi eliminare tutti i dispositivi, ad eccezione delle schede di rete fisiche.

4. È possibile provare a disinstallare/reinstallare Hyper-V dopo avere rimosso eventuali schede di rete non fisiche.

## <a name="cannot-attach-debugger-to-a-xamarin-project"></a><a name="Skylake"></a> Impossibile connettere il debugger a un progetto Xamarin
 Se si esegue Windows 10 con processori Intel Skylake, potrebbe essere impossibile eseguire le app Xamarin nell'emulatore o connettere il debugger di Visual Studio a tali app. Questo è dovuto a un problema relativo a Hyper-V e ai processori Skylake. Come soluzione alternativa, eseguire le operazioni seguenti.

1. Aprire la console di gestione di Hyper-V e selezionare la macchina virtuale per il profilo dell'emulatore in uso.

2. Selezionare **Elimina stato salvato** (in basso a destra).

3. Scegliere **Impostazioni...**

4. Espandere il nodo del processore e scegliere **Compatibilità**.

5. Abilitare **Esegui migrazione a un computer fisico con una versione diversa del processore**.

6. Riavviare il servizio (in **Azioni**) e riprovare.

## <a name="emulator-fails-to-run-app-that-uses-google-play-services"></a><a name="GooglePlay"></a>Emulator non riesce a eseguire l'app che usa Google Play Services
 L'emulatore non viene fornito con le librerie per Google Play Services. Tuttavia, l'emulatore supporta l'installazione per trascinamento di file ZIP che supportano il flashing.

## <a name="drag-and-drop-of-a-file-apk-or-flashable-zip-file-does-not-work"></a><a name="DragAndDrop"></a> Il trascinamento della selezione di un file, apk o file ZIP flashable non funziona
 L'emulatore utilizza ADB.exe per facilitare il trasferimento di file quando si trascina un file sullo schermo. Se si verifica un errore durante il tentativo di trascinamento della selezione di un file, ciò probabilmente indica che l'emulatore non è connesso a ADB.exe. Per risolverlo, seguire la procedura descritta in [Visual Studio si blocca durante il tentativo di distribuzione dell'app all'emulatore oppure l'emulatore non è visualizzato come destinazione di debug in altri IDE](#ADB).

## <a name="resolution-of-screenshot-is-incorrect"></a><a name="Resolution"></a> Risoluzione della schermata non è corretta
 Se acquisire una schermata utilizzando la scheda della schermata nel **Strumenti aggiuntivi** finestra e l'immagine risultante è di dimensioni impreviste, potrebbe essere necessario regolare il livello di zoom della schermata prima di scegliere **acquisire**. L'emulatore viene schermate alla risoluzione dello schermo sul monitor del PC host.

## <a name="emulator-fails-to-render-opengl-content"></a><a name="OpenGL"></a>Emulator non riesce a eseguire il rendering del contenuto OpenGL
 L'emulatore esegue il rendering di contenuto OpenGL tramite la GPU del computer host e usa il progetto ANGLE per convertire le chiamate da e verso DirectX. Se l'applicazione esegue correttamente il rendering in un dispositivo, ma in modo non corretto nell'emulatore, è probabile che il dispositivo è ridurre una chiamata di OpenGL errata (ad esempio l'utilizzo di variabili di shader che non corrispondono).

## <a name="emulator-does-not-respond-to-multi-touch-gestures"></a><a name="Multitouch"></a> Emulatore non risponde ai movimenti multitocco
 In alcuni casi, l'emulatore verrà avviare e non rispondere a Multi-touch entrambi l'interazione diretta tramita da schermo abilitato per il tocco o utilizzando lo strumento multi-Touch della barra degli strumenti dell'emulatore. Se questo è il caso, scegliere il **Ruota** pulsante della barra degli strumenti dell'emulatore e tenta di utilizzare nuovamente Multi-touch. Se il problema persiste, leggere il problema [Emulatore non riesce a eseguire il rendering OpenGL contenuto](#OpenGL) .

## <a name="support-resources"></a><a name="Support"></a> Risorse di supporto
 Se il computer host soddisfa i requisiti di sistema e si verifica un problema non incluso in questa guida alla risoluzione dei problemi:

- Porre una domanda su StackOverflow usando i tag [android-emulator](https://stackoverflow.com/questions/tagged/android-emulator) e visual-studio.

- Segnalare un problema usando lo strumento Invia smile in Visual Studio o in Gestione emulatori.
