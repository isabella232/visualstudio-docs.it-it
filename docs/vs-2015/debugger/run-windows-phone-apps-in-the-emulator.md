---
title: Eseguire le app di Windows Phone nell'emulatore | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7590788-beb3-403c-a7dd-18472a9e585e
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7bc85d1a38143e626fc659979eea727a0b41ef00
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58963860"
---
# <a name="run-windows-phone-apps-in-the-emulator"></a>Eseguire app di Windows Phone nell'emulatore
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'emulatore di Windows Phone fornisce un ambiente virtualizzato che ti consente di eseguire debug e test di app Windows Phone nel computer senza un dispositivo fisico. Puoi simulare eventi comuni di tocco e rotazione e scegliere le dimensioni fisiche dello schermo e la risoluzione che vuoi emulare. Puoi anche testare numerose funzionalità comuni, come posizione, rete, notifiche, sensori, accelerometro e scheda SD opzionale.  
  
 Per altre informazioni sulle funzionalità che puoi testare nell'emulatore, vedi [testare le funzionalità delle app nell'emulatore Windows Phone](http://msdn.microsoft.com/c1b2b0ec-b8cc-4a98-84c1-701428e45cb1).  
  
 Insieme a Visual Studio, l'emulatore offre un ambiente completo in cui puoi progettare, sviluppare e testare le app Windows Phone, nonché eseguirne il debug.  
  
##  <a name="BKMK_run"></a> Eseguire un'app Windows Phone nell'emulatore  
 Quando sviluppi un'app Windows Phone, puoi usare l'emulatore Windows Phone per distribuire e testare rapidamente l'app. Ti consigliamo, tuttavia, di testare l'app in un dispositivo Windows Phone reale prima di pubblicarla in Windows Phone Store. In questo modo potrai provare l'app sperimentando la stessa esperienza che proverà l'utente.  
  
 Quando esegui un'app Windows Phone per la prima volta nell'emulatore Windows Phone, si verificano gli eventi seguenti:  
  
1. L'emulatore si avvia.  
  
2. L'emulatore carica il sistema operativo Windows Phone.  
  
3. L'emulatore visualizza la schermata iniziale di Windows Phone.  
  
4. L'app viene distribuita nell'emulatore.  
  
5. L'app viene eseguita nell'emulatore.  
  
   Se l'emulatore selezionato è già in esecuzione, l'app viene distribuita e avviata nell'emulatore in esecuzione. Può essere in esecuzione una sola istanza di ogni emulatore per volta.  
  
> [!TIP]
>  Quando testi l'app nell'emulatore, lascia aperto l'emulatore tra le sessioni di debug per poter eseguire di nuovo l'app rapidamente.  
  
###  <a name="BKMK_vs"></a> Eseguire un'app da Visual Studio  
  
##### <a name="to-deploy-and-run-an-app-from-visual-studio"></a>Per distribuire ed eseguire un'app da Visual Studio  
  
1.  In Visual Studio apri un progetto Windows Phone.  
  
2.  Nel **Standard** sulla barra degli strumenti, selezionare uno degli emulatori disponibili.  
  
     ![Elenco di immagini dell'emulatore Windows Phone](../debugger/media/wp-emulator-list.png "WP_Emulator_list")  
  
3.  Per distribuire ed eseguire l'app con il debug, scegliere il **Debug** menu, fare clic su **Avvia debug**, oppure premere F5.  
  
     Distribuire ed eseguire l'app senza debug, scegliere il **Debug** menu, fare clic su **Avvia senza eseguire debug**, oppure premere Ctrl + F5.  
  
     L'app viene distribuita e avviata.  
  
     Per distribuire l'app senza eseguirla, scegli il **compilare** menu, fare clic su **Distribuisci soluzione**.  
  
##### <a name="to-stop-a-running-app"></a>Per arrestare un'app in esecuzione  
  
- Per arrestare un'app in esecuzione, effettua una delle seguenti operazioni:  
  
  - In Visual Studio sul **eseguire il Debug** menu, fare clic su **arresta debug**, oppure premi MAIUSC+F5.  
  
  - Nell'emulatore, premere il **nuovamente** pulsante per uscire dall'app. Se la pagina attiva dell'app non era pagina iniziale dell'app, si potrebbe essere necessario premere il **nuovamente** pulsante più volte.  
  
    L'app si chiude e viene visualizzata la schermata iniziale. Termina così la sessione di debug corrente.  
  
##### <a name="to-restart-an-app-without-debugging"></a>Per riavviare un'app senza eseguire il debug  
  
1.  Nell'emulatore, nella schermata iniziale, scorri rapidamente verso sinistra per visualizzare l'elenco di app.  
  
2.  Nell'elenco tocca l'icona dell'app. L'app viene riavviata senza eseguire il debug.  
  
##### <a name="to-deactivate-a-running-app"></a>Per disattivare un'app in esecuzione  
  
1.  Prima di eseguire l'app, in Visual Studio, fare clic sul progetto in Esplora soluzioni e quindi selezionare **delle proprietà** per aprire **creazione progetti**.  
  
2.  In **creazione progetti**via il **Debug** pagina, lasciare il **per la rimozione definitiva al momento della disattivazione durante il debug** casella deselezionata se si desidera che l'app passi a un'inattive stato quando disattivata. Seleziona la casella di controllo se desideri che l'app venga rimossa definitivamente quando viene disattivata.  
  
3.  Nel **Debug** menu, fare clic su **Avvia debug**, oppure premere F5 per eseguire l'app.  
  
4.  Nell'emulatore, premere il **avviare** pulsante. Viene visualizzata la schermata iniziale e l'app viene disattivata. L'app passa a uno stato inattivo oppure viene rimossa definitivamente, a seconda dell'impostazione delle **per la rimozione definitiva al momento della disattivazione durante il debug** casella di controllo.  
  
##### <a name="to-reactivate-a-dormant-or-tombstoned-app"></a>Per riattivare un'app inattiva o rimossa definitivamente  
  
-   Nell'emulatore, premere il **nuovamente** per tornare all'app. Se sei passato ad altre pagine o hai aperto un'altra app, si potrebbe essere necessario premere il **nuovamente** pulsante più di una volta per riattivare l'app.  
  
     La sessione di debug viene ripresa. Se il debugger si è scollegato dall'app, potrebbe essere necessario premere F5 per riprendere la sessione di debug.  
  
###  <a name="BKMK_depltool"></a> Eseguire un'app con lo strumento distribuzione applicazione  
 È anche possibile usare lo strumento distribuzione applicazione Windows Phone (**AppDeploy.exe**) per eseguire l'app nell'emulatore. Questo strumento è un'app autonoma che viene installata al momento dell'installazione degli strumenti di sviluppo di Windows Phone.  
  
 Per altre informazioni, vedi [app di distribuzione di Windows Phone 8.1 con lo strumento distribuzione applicazione](http://msdn.microsoft.com/library/23700f82-1399-44d9-bc0c-714be4a48ee6).  
  
##  <a name="BKMK_toolbar"></a> Configurare l'emulatore Windows Phone con la barra degli strumenti dell'emulatore  
 La tabella seguente mostra i pulsanti di configurazione disponibili sulla barra degli strumenti dell'emulatore.  
  
|Pulsanti della barra degli strumenti|Opzioni di configurazione|  
|---------------------|---------------------------|  
|![Immettere le opzioni nella barra degli strumenti dell'emulatore Windows Phone](../debugger/media/wp-emulator.png "WP_Emulator_")|**Configurazione input punto singolo o multipunto**<br /><br /> Abilitando la configurazione dell'input multipunto, puoi fare clic con il pulsante destro del mouse per spostare i punti di tocco senza toccare lo schermo. Puoi quindi fare clic con il pulsante sinistro del mouse per spostare entrambi i punti di tocco simultaneamente.|  
|![Orientamento sulla barra degli strumenti dell'emulatore Windows Phone](../debugger/media/wp-emulator-rotation.png "WP_Emulator_rotation")|**Configurazione dell'orientamento dell'emulatore**<br /><br /> Puoi modificare l'orientamento nell'emulatore Windows Phone scegliendo una delle tre opzioni disponibili: verticale, orizzontale verso sinistra o orizzontale verso destra. Le dimensioni dell'emulatore non cambiano quando modifichi l'orientamento.<br /><br /> Per modificare l'orientamento, scegliere il **Ruota a sinistra** pulsante o il **Ruota a destra** pulsante.|  
|![Ridimensionare le opzioni nella barra degli strumenti dell'emulatore Windows Phone](../debugger/media/wp-emulator-size.png "WP_Emulator_size")|**Configurare le dimensioni dell'emulatore**<br /><br /> Puoi modificare le dimensioni dell'emulatore sullo schermo del computer host. I punti per pollice (DPI, Dots Per Inch) per l'emulatore sono basati sul valore DPI del monitor host, indipendentemente dal valore dello zoom.<br /><br /> -Per adattare l'emulatore allo schermo, scegliere il **adatta allo schermo** pulsante.<br />-Per modificare l'impostazione dello zoom, scegliere il **Zoom** pulsante. Il **Zoom** verrà visualizzata la finestra di dialogo. Nel **Zoom** finestra di dialogo immettere un valore di zoom compreso tra 33 e 100.|  
  
##  <a name="BKMK_buttons"></a> Usare i pulsanti hardware simulati nell'emulatore  
 Per simulare l'utilizzo dei pulsanti hardware di un telefono, puoi usare i pulsanti hardware simulati sul lato destro dello schermo dell'emulatore.  
  
- Scegliere il **Power** pulsante per simulare l'attivazione e disattivare la visualizzazione. Fai clic e tieni premuto per simulare lo spegnimento del telefono.  
  
- Fare clic sui **aumento del Volume** oppure **Volume giù** pulsante per simulare la modifica del volume dell'altoparlante del telefono per le chiamate telefoniche e le notifiche.  
  
- Il **fotocamera** pulsante Avvia l'app della fotocamera. Puoi simulare lo scatto di una foto o l'acquisizione di un video usando i controlli nell'app della fotocamera.  
  
  La schermata seguente mostra i pulsanti hardware simulati.  
  
1. L'immagine a sinistra mostra la schermata iniziale dell'emulatore.  
  
2. L'immagine centrale Mostra l'emulatore dopo avere toccato il **Power** pulsante da disattivare lo schermo.  
  
3. L'immagine a destra mostra lo schermo dell'emulatore dopo avere toccato il **aumento del Volume** pulsante per aumentare il volume.  
  
   ![I pulsanti nell'emulatore Windows Phone](../debugger/media/wp-emulator-buttons.png "WP_Emulator_buttons")  
  
##  <a name="BKMK_tasks_kbd"></a> Usare la tastiera del computer con l'emulatore  
 L'emulatore consente di mappare la tastiera hardware del computer di sviluppo alla tastiera di un dispositivo Windows Phone. Il comportamento dei tasti corrisponde a quello in un dispositivo Windows Phone.  
  
 Per impostazione predefinita, la tastiera hardware non è abilitata. Questa implementazione equivale a una tastiera scorrevole che deve essere distribuita per poter essere usata. Prima di abilitare la tastiera hardware, l'emulatore accetta l'input solo dai tasti CTRL.  
  
 I caratteri speciali sulla tastiera di una versione localizzata di un computer di sviluppo Windows non sono supportati dall'emulatore. Per immettere caratteri speciali presenti su una tastiera localizzata, usa il pannello di input software.  
  
 Per utilizzare la tastiera del computer nell'emulatore, premere il tasto PGSU o il tasto PAUSA/INTERR (emulatore di Windows 8/8.1) oppure F4 (emulatore di Windows 10).  
  
 Per smettere di utilizzare la tastiera del computer nell'emulatore, premere il tasto PGGIÙ o il tasto PAUSA/INTERR (emulatore di Windows 8/8.1) oppure F4 (emulatore di Windows 10).  
  
 La tabella seguente illustra i tasti di una tastiera hardware che puoi usare per emulare i pulsanti e altri controlli di un dispositivo .  
  
|Tasto hardware del computer|Pulsante hardware di Windows Phone|Note|  
|---------------------------|-----------------------------------|-----------|  
|F1|INDIETRO|Le pressioni lunghe funzionano come previsto.|  
|F2|AVVIO|Le pressioni lunghe funzionano come previsto.|  
|F3|CERCA||  
|F4|Nell'emulatore di Windows 10 è possibile utilizzare alternativamente la tastiera del computer locale e non utilizzare tastiera del computer locale.|Non applicabile nell'emulatore di Windows 8/8.1.|  
|F5|Non applicabile.||  
|F6|FOTOCAMERA METÀ|Pulsante dedicato della fotocamera che viene premuto fino a metà.|  
|F7|FOTOCAMERA COMPLETO|Pulsante dedicato della fotocamera.|  
|F8|Non applicabile.||  
|F9|VOLUME SU||  
|F10|VOLUME GIÙ||  
|F11|Non applicabile.||  
|F12|ACCENSIONE|Premi il tasto F12 due volte per abilitare la schermata di blocco.<br /><br /> Le pressioni lunghe funzionano come previsto.|  
|ESC|INDIETRO|Le pressioni lunghe funzionano come previsto.|  
|PAUSA/INTERR|Attiva/disattiva tastiera (solo per l'emulatore di Windows 8/8.1).|Non applicabile per l'emulatore di Windows 10.|  
|PGSU|Abilita la tastiera hardware (solo per l'emulatore di Windows 8/8.1).|Non applicabile per l'emulatore di Windows 10.|  
|PGGIÙ|Disabilita la tastiera hardware (solo per l'emulatore di Windows 8/8.1).|Non applicabile per l'emulatore di Windows 10.|  
  
##  <a name="BKMK_checkpoints"></a> Salvare e caricare checkpoint personalizzati  
 Salvare uno snapshot dello stato dell'emulatore utilizzando il **checkpoint** scheda nell'emulatore **strumenti aggiuntivi**. Questa funzionalità è utile se testi frequentemente l'app con gli stessi dati e le stesse impostazioni.  
  
 Se, ad esempio, l'app richiede diversi contatti, puoi creare i record dei contatti una volta e salvare uno snapshot dell'emulatore. In caso contrario, dovrai ricreare i record dei contatti ogni volta che avvii l'emulatore.  
  
- Fare clic su **nuovo checkpoint** per acquisire un nuovo snapshot dello stato dell'emulatore con i dati e le impostazioni necessarie per testare l'app in un secondo momento. Il nuovo checkpoint viene aggiunto per il **checkpoint** elenco.  
  
   Non puoi acquisire un checkpoint mentre il debugger è collegato all'emulatore.  
  
- Seleziona un checkpoint nel **checkpoint** elenco per visualizzare le relative informazioni di checkpoint.  
  
- Selezionare il pulsante di opzione nel **predefinito** colonna per impostare un checkpoint salvato l'impostazione predefinita per l'emulatore attivo.  
  
- Fare clic su **ripristinare** per riavviare il sistema operativo Windows Phone nell'emulatore e caricare lo snapshot selezionato.  
  
- Fare clic su **eliminare** per eliminare uno snapshot che non è più necessario.  
  
  L'immagine dell'emulatore originale viene sempre visualizzata come primo elemento nel **checkpoint** elencare e non possono essere modificate o eliminate. Puoi tuttavia selezionare uno snapshot diverso come immagine dell'emulatore originale.  
  
  ![Scheda checkpoints dell'emulatore Windows Phone](../debugger/media/wp-emulator-checkpoints.png "WP_Emulator_checkpoints")  
  
##  <a name="BKMK_tasks_shot"></a> Acquisire schermate nell'emulatore  
 Puoi creare schermate delle app Windows Phone usando lo strumento per l'acquisizione delle schermate disponibile nella finestra Strumenti aggiunti. Lo strumento crea file PNG corrispondenti alla risoluzione dell'emulatore in esecuzione.  
  
 ![Screenshot del Windows Phone emulatore](../debugger/media/wp-emulator-screenshots.png "WP_Emulator_screenshots")  
  
#### <a name="to-create-an-app-screenshot-by-using-the-built-in-emulator-screenshot-tool"></a>Per creare una schermata di un'app usando lo strumento integrato nell'emulatore  
  
1. Per ottimizzare la qualità delle schermate, imposta il livello di zoom dell'emulatore su 100%. Maggiore è il livello di zoom, migliore sarà la qualità della schermata.  
  
2. Avvia l'app nell'emulatore.  
  
3. Sulla barra degli strumenti dell'emulatore, fare clic sul pulsante di espansione per aprire la **strumenti aggiuntivi** finestra.  
  
4. Scegliere il **Screenshot** scheda.  
  
5. Quando l'app è pronta, scegliere il **acquisire** pulsante.  
  
    La schermata viene visualizzata nell'area di lavoro.  
  
6. Fare clic sui **salvare** per aprire il **Salva con nome** nella finestra di dialogo.  
  
7. Scegliere la località e **nomefile** che si desidera e quindi fare clic su **salvare**.  
  
8. Se lo desideri, puoi passare ad altre pagine dell'app e acquisire ulteriori schermate.  
  
9. Avvia un emulatore con una risoluzione dello schermo diversa per acquisire la stessa schermata con diverse risoluzioni. Se hai eseguito l'app con il debug, devi arrestare il debug prima di eseguirla di nuovo in un altro emulatore.  
  
   Disabilita i contatori della frequenza dei fotogrammi sullo schermo dell'emulatore prima di acquisire le schermate che verranno inviate a Windows Phone Store.  
  
#### <a name="to-disable-frame-rate-counters-in-the-emulator-before-capturing-screenshots"></a>Per disabilitare i contatori della frequenza dei fotogrammi nell'emulatore prima di acquisire le schermate  
  
-   Specifica una build di rilascio in Visual Studio. Dopo aver specificato una build di rilascio, avviare l'app selezionando il **Deploy _[nome app]_**  sul collegamento di **compilare** menu.  
  
-   In alternativa, puoi impostare come commento la riga di codice nel file app.xaml.cs o app.xaml.vb che imposta il valore di `EnableFrameRateCounter` su `true`.
