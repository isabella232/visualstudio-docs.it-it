---
title: Acquisizione di informazioni grafiche | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.graphics.frame
- vs.graphics.capturewindow
- VS.ToolsOptionsPages.Graphics_Diagnostics.Capture
ms.assetid: 187ce86e-e340-4f6c-8937-8e8f1027a17f
caps.latest.revision: 44
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3c3adcfb4da1ddfba51c162fd541bda302bd2d86
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520132"
---
# <a name="capturing-graphics-information"></a>Acquisizione di informazioni grafiche
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [acquisizione di informazioni grafiche](https://docs.microsoft.com/visualstudio/debugger/graphics/capturing-graphics-information).  
  
Acquisire informazioni grafiche dall'app Direct3D così da poter usare Analizzatore grafica di Visual Studio per diagnosticare i problemi di rendering e di prestazioni.  
  
## <a name="capturing-graphics-information"></a>Acquisizione di informazioni grafiche  
 L'acquisizione di informazioni grafiche è un processo costituito da due fasi. Innanzitutto, eseguire l'applicazione nella diagnostica grafica, quindi specificare uno o più frame da cui acquisire informazioni dettagliate.  
  
#### <a name="to-run-your-app-under-graphics-diagnostics"></a>Per eseguire l'applicazione nella diagnostica della grafica  
  
-   Nella barra dei menu scegliere **Debug**, **Grafica**, **Avvia diagnostica**. Tastiera: premere ALT+F5.  
  
-   Nel **grafica** sulla barra degli strumenti, scegliere il **avvia diagnostica** pulsante.  
  
 Se un'app è in esecuzione nella diagnostica della grafica, verranno costantemente acquisiti determinati tipi di informazioni grafiche, tra cui la configurazione dei dispositivi, la creazione della catena di scambio e di oggetti grafici e risorse, nonché altri eventi importanti che influiscono su più di un frame. Contemporaneamente, è possibile acquisire informazioni dettagliate su frame specifici; tali informazioni includono chiamate di disegno e invii di compute shader, oltre a risorse e oggetti Direct3D che li supportano.  
  
#### <a name="to-capture-a-frame"></a>Per acquisire un frame  
  
-   In Visual Studio sul **grafica** sulla barra degli strumenti, scegliere il **Acquisisci Frame** pulsante![icona pulsante acquisizione grafica](../debugger/media/debuggingdirectxgraphics.png "DebuggingDirectXGraphics").  
  
-   Premere STAMP sulla tastiera.  
  
    > [!NOTE]
    >  Durante l'esecuzione di un'app in **diagnostica della grafica**, il tasto Stamp solo può essere usato per acquisire un frame di informazioni grafiche; e non per eseguire la funzione standard. Questa condizione rimarrà attiva finché non si deciderà di interrompere l'acquisizione delle informazioni grafiche, in genere arrestando il debug o chiudendo l'app, anche se un'altra app presenta lo stato attivo.  
  
-   Nell'interfaccia di acquisizione di Visual Studio, scegliere il **Acquisisci Frame** pulsante che si trova sopra il **sessione di diagnostica** sequenza temporale, o scegliere di grande **Acquisisci Frame** pulsante che si trova sotto il **fotogrammi al secondo** corsia e a destra dei frame acquisiti in precedenza. Entrambi i pulsanti sono evidenziati nell'immagine seguente.  
  
     ![Acquisire frame con lo strumento utilizzo GPU. ](../debugger/media/pix-gpu-usage-tool-capture-frame.png "pix_gpu_usage_tool_capture_frame")  
  
     Quando si è pronti per esaminare i frame acquisiti, avviare il **Visual Studio Graphics Analyzer** seguendo la **Frame...** collegamento sopra le anteprime delle immagini oppure facendo doppio clic su Anteprima.  
  
 È possibile acquisire solo frame interi e quindi, all'avvio di un'acquisizione, verranno effettivamente registrate le informazioni grafiche dal frame successivo. La registrazione inizierà immediatamente dopo aver verificato il frame in cui è stata avviata l'acquisizione e terminerà dopo aver verificato il frame acquisito. È possibile acquisire un numero indefinito di frame mentre l'app è in esecuzione nella diagnostica grafica. In assenza di frame acquisiti, il log di grafica verrà rimosso.  
  
 Durante l'acquisizione dei frame, Visual Studio visualizza la finestra della sessione di diagnostica (con estensione diagsession). Se si chiude questa finestra, si arresta il debug o si chiude l'app, non sarà possibile acquisire altri frame nel log. Per acquisire più informazioni grafiche, è necessario eseguire nuovamente l'app in Diagnostica grafica per avviare un nuovo log di grafica.  
  
### <a name="graphics-diagnostics-capture-options"></a>Opzioni di acquisizione di diagnostica grafica  
 È possibile configurare l'acquisizione per raccogliere stack di chiamate per tutti gli eventi grafici o per un subset limitato, per disabilitare l'HUD per l'acquisizione e per abilitare o disabilitare l'acquisizione in modalità di compatibilità.  
  
##### <a name="to-configure-graphics-diagnostics-capture-options"></a>Per configurare le opzioni di acquisizione di diagnostica della grafica  
  
1.  Nella barra dei menu scegliere Strumenti, Opzioni. Verrà visualizzata la finestra di dialogo Opzioni.  
  
2.  Nell'elenco di categorie delle opzioni a sinistra scegliere Diagnostica della grafica, quindi configurare le opzioni desiderate di Diagnostica della grafica.  
  
     **Raccogli stack di chiamate durante l'acquisizione (rallenta l'acquisizione)**  
     Selezionare questa casella per raccogliere gli stack di chiamate. Per impostazione predefinita, gli stack di chiamate non vengono raccolti. Per acquisire gli stack di chiamate, assicurarsi che il **Raccogli stack di chiamate durante l'acquisizione (rallenta l'acquisizione** casella di controllo è impostato per abilitare la raccolta e quindi impostare il **per indicatori draw, dispatch, present e perf**opzione (predefinito) per raccogliere solo i più importanti gli stack di chiamate, o il **per tutti gli elementi** opzione per raccogliere tutti gli stack di chiamate. Per interrompere la raccolta di stack di chiamate in un secondo momento, deselezionare il **Raccogli stack di chiamate durante l'acquisizione (rallenta l'acquisizione** casella di controllo.  
  
     **Disabilita HUD di gioco durante l'acquisizione**  
     Selezionare questa casella per disabilitare l'hud in sovraimpressione visualizzato in genere da un'app in esecuzione nella diagnostica della grafica. Deselezionarla per visualizzare l'hud in sovraimpressione.  
  
     **Acquisisci in modalità di compatibilità**  
     Selezionare questa casella per acquisire le informazioni grafiche in modalità di compatibilità. L'acquisizione in modalità di compatibilità è l'impostazione predefinita. In modalità di compatibilità Direct3D non segnalerà che la GPU supporta tutte le funzionalità aggiuntive oltre a quelle definite nel livello funzionalità di base. Ciò impedisce all'app da acquisire di usare le estensioni specifiche dell'hardware della GPU su cui viene acquisita e assicura che il log di grafica possa essere riprodotto con qualsiasi GPU che supporta lo stesso livello funzionalità o un livello superiore. Deselezionare questa casella per disabilitare la modalità di compatibilità. I log acquisiti con la modalità di compatibilità disabilitata non verranno riprodotti su una GPU che non supporta le stesse funzionalità aggiuntive usate dall'app durante l'acquisizione.  
  
     **Arrestare l'acquisizione se vengono rilevati errori livelli SDK**  
     Selezionare questa casella per interrompere immediatamente l'acquisizione se vengono rilevati errori.  
  
## <a name="capturing-graphics-information-remotely"></a>Acquisizione remota di informazioni grafiche  
 È possibile acquisire informazioni grafiche da un'app in esecuzione nel computer locale o in un computer o dispositivo remoto. L'acquisizione remota è supportata per i computer [!INCLUDE[winblue_client_2](../includes/winblue-client-2-md.md)] e i dispositivi [!INCLUDE[winblue_winrt_2](../includes/winblue-winrt-2-md.md)]. Per acquisire informazioni grafiche da un'app in esecuzione in remoto, configurare il progetto per il debug remoto e quindi eseguire l'app nella diagnostica grafica come descritto in precedenza. L'app viene eseguita nel computer remoto e le informazioni grafiche acquisite vengono registrate nel computer di sviluppo.  
  
 La modalità di configurazione del progetto per il debug remoto varia a seconda del tipo di app sviluppata e dal linguaggio di programmazione in uso. Per informazioni su come configurare il debug remoto per un'app Windows Store, vedere [Run Windows Store App in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md). Per informazioni su come configurare il debug remoto per un'app desktop di Windows, vedere [Set Up Remote Debugging per un progetto di Visual Studio](http://msdn.microsoft.com/library/ec332dc4-400a-498b-a0e6-c8dcf10fef8a).  
  
 Successivamente sarà possibile usare un computer o un dispositivo remoto per riprodurre le informazioni grafiche, indipendentemente dall'origine dell'acquisizione. Per altre informazioni, vedere [procedura: modificare il computer di riproduzione di diagnostica della grafica](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## <a name="capturing-graphics-information-from-the-command-line"></a>Acquisizione di informazioni grafiche dalla riga di comando  
 È possibile acquisire le informazioni grafiche da un'app con uno strumento da riga di comando. Questo strumento, DXCap.exe, può acquisire e riprodurre rapidamente le informazioni grafiche senza usare Visual Studio o l'acquisizione a livello di codice. In particolare, è possibile usare DXCap.exe per l'automazione o in un ambiente di test. Per altre informazioni sulle DXCap.exe, vedere [strumento di acquisizione da riga di comando](../debugger/command-line-capture-tool.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: cattura delle informazioni grafica](../debugger/walkthrough-capturing-graphics-information.md)



