---
title: Uso di Strumenti di Visual Studio Tools per Unity | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: e67ec9a2-a449-413e-8930-9a471bd43a06
author: dantogno
ms.author: v-davian
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: d1c68db8282a74ce230d573450a359060bb0d12c
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/19/2018
ms.locfileid: "39155581"
---
# <a name="using-visual-studio-tools-for-unity"></a>Uso di Visual Studio Tools per Unity

In questa sezione verrà illustrato come usare le funzionalità per l'integrazione e la produttività di Visual Studio Tools per Unity e come usare il debugger di Visual Studio per lo sviluppo di Unity.

## <a name="opening-unity-scripts-in-visual-studio"></a>Apertura di script Unity in Visual Studio

Dopo aver impostato Visual Studio [come editor di script esterno per Unity](getting-started-with-visual-studio-tools-for-unity.md#configure-unity-for-use-with-visual-studio), l'apertura di qualsiasi script dall'editor di Unity causa automaticamente l'avvio o il passaggio a Visual Studio, dove viene aperto lo script scelto. È sufficiente fare doppio clic su uno script nel progetto Unity.

In alternativa, Visual Studio può essere aperto senza aprire alcuno script nell'editor standard selezionando **Open C# Project (Apri progetto C#)** dal menu **Asset** in Unity.

![Open C# project (Apri progetto C#)](media/vstu_open-csharp-project.png)

## <a name="unity-documentation-access"></a>Accesso della documentazione di Unity

 È possibile accedere rapidamente alla documentazione di Unity da Visual Studio. Se Visual Studio Tools per Unity non trova la documentazione dell'API in locale, proverà a individuarla online.

- In Visual Studio evidenziare o posizionare il cursore sull'API di Unity su cui visualizzare maggiori informazioni e quindi premere **CTRL+ALT+M, CTRL+H**

## <a name="intellisense-for-unity-api-messages"></a>IntelliSense per messaggi dell'API Unity

 Ciò semplifica l'implementazione di messaggi dell'API Unity negli script MonoBehaviour e assiste nell'apprendimento dell'API Unity. Per usare IntelliSense per i messaggi Unity:

1. Posizionare il cursore su una nuova riga nel corpo di una classe che deriva da `MonoBehaviour`.

1. Iniziare digitando il nome di un messaggio Unity, ad esempio `OnTriggerEnter`.

1. Dopo aver digitato le lettere "**ontri**", viene visualizzato un elenco di suggerimenti di IntelliSense.

  ![Using IntelliSense](media/vstu_intellisense1.png)

1. La selezione nell'elenco può essere modificata in tre modi:

    - Con le frecce **su** e **giù**.

    - Facendo clic con il mouse sull'elemento desiderato.

    - Continuando a digitare il nome dell'elemento desiderato.

1. IntelliSense può inserire il messaggio di Unity selezionato, includendo gli eventuali parametri necessari:

    - Premendo **Tab**.

    - Premendo **Invio**.

    - Facendo doppio clic sull'elemento selezionato.

  ![Inserire un messaggio Unity da IntelliSense](media/vstu_intellisense2.png)

## <a name="unity-monobehavior-scripting-wizard"></a>Procedura guidata MonoBehaviour di Unity per la creazione di script

È possibile usare la procedura guidata Monobehaviour per visualizzare un elenco di tutti i metodi dell'API di Unity e implementare rapidamente una definizione vuota. Questa funzionalità, in particolare se è attivata l'opzione **Genera commenti del metodo**, è utile se si sta ancora imparando cosa è disponibile nell'API di Unity.

Per creare definizioni vuote di metodi MonoBehaviour con la procedura guidata MonoBehaviour:

1. In Visual Studio posizionare il cursore nel punto in cui si vogliono inserire i metodi e quindi premere **CTRL+MAIUSC+M** per avviare la procedura guidata MonoBehaviour.

1. Nella finestra **Create script methods** (Crea metodi script) selezionare la casella di controllo accanto al nome dei singoli metodi da aggiungere.

1. Usare l'elenco a discesa **Framework version** (Versione framework) per selezionare la versione desiderata.

1. Per impostazione predefinita, i metodi vengono inseriti in corrispondenza del cursore. In alternativa, è possibile inserirli dopo tutti i metodi già implementati nella classe modificando il valore del **punto di inserimento** con la posizione desiderata.

1. Se si vuole che la procedura guidata generi commenti per i metodi selezionati, selezionare la casella di controllo **Genera commenti del metodo**. Questi commenti vengono usati per facilitare l'individuazione del punto in cui viene chiamato il metodo e chiarirne le responsabilità generali.

1. Fare clic su **OK** per chiudere la procedura guidata e inserire i metodi nel codice.

 ![Finestra di dialogo della procedura guidata MonoBehavior.](../cross-platform/media/vstu_monobehavior_wizard_full.png "vstu_monobehavior_wizard_full")

## <a name="unity-project-explorer"></a>Esplora progetti Unity

 ![Finestra di Esplora progetti Unity.](../cross-platform/media/vstu_unity_project_explorer.png "vstu_unity_project_explorer")

 Esplora progetti Unity visualizza tutti i file di progetto Unity e tutte le directory nella stessa gerarchia usata dall'editor di Unity. Si differenzia dall'esplorazione degli script Unity con Esplora soluzioni Visual Studio standard, che li organizza in progetti e in una soluzione generata da Visual Studio.

- Nel menu principale di Visual Studio scegliere **Visualizza > Esplora progetti Unity**. Tasto di scelta rapida: **Alt+Maiusc+E**

     ![Visualizzare la finestra Esplora progetti Unity.](../cross-platform/media/vstu_view_unity_project_explorer.png "vstu_view_unity_project_explorer")

## <a name="unity-error-list"></a>Elenco errori di Unity

 È possibile visualizzare i messaggi della console Unity all'interno di Visual Studio quando questo è connesso a un'istanza di Unity. Sono inclusi anche errori e avvisi di Unity. I messaggi vengono visualizzati nella finestra **Elenco errori** di Visual Studio; in particolare, i messaggi di errore di Unity vengono visualizzati nella scheda **Errori**, i messaggi di avviso nella scheda **Avvisi** e gli altri messaggi, ad esempio quelli inviati tramite l'API Debug.Log di Unity, nella scheda **Messaggi**.

 Per visualizzare i messaggi, il progetto Unity deve essere collegato a Visual Studio come descritto nella sezione [Debug di Unity](#unity-debugging).

 Se non si vogliono visualizzare errori, avvisi e messaggi di Unity nella finestra **Elenco errori** di Visual Studio, è possibile disabilitarli nel menu Configurazione.

## <a name="unity-debugging"></a>Debug di Unity

 Visual Studio Tools per Unity consente di eseguire il debug di script dell'editor e di gioco del progetto Unity usando il potente debugger di Visual Studio.

### <a name="debugging-in-the-unity-editor"></a>Debug nell'editor di Unity

#### <a name="start-debugging"></a>Avvia debug

1. Collegare Visual Studio a Unity facendo clic sul pulsante **Riproduci** etichettato **Collega a Unity**, o usare la scelta rapida da tastiera **F5**.

  ![Fare clic su Riproduci in Visual Studio](media/vstu_play-button.png)

1. Passare a Unity e fare clic sul pulsante **Riproduci** per eseguire il gioco nell'editor.

  ![Fare clic su Riproduci in Unity](media/vstu_unity-play-button.png)

1. Quando il gioco è in esecuzione nell'editor di Unity mentre è connesso a Visual Studio, qualsiasi punto di interruzione incontrato causa la sospensione dell'esecuzione del gioco e la visualizzazione della riga di codice dove il gioco ha incontrato il punto di interruzione in Visual Studio.

#### <a name="stop-debugging"></a>Arrestare il debug

- Scegliere il pulsante **Interrompi** in Visual Studio oppure usare la scelta rapida da tastiera **Maiusc+F5**.

  ![Fare clic su Interrompi in Visual Studio](media/vstu_stop-debugger.png)

Per altre informazioni sul debug in Visual Studio, vedere [First look at the Visual Studio Debugger](../debugger/debugger-feature-tour.md) (Introduzione al debugger di Visual Studio).

#### <a name="attach-to-unity-and-play"></a>Collega a Unity e gioca

Per maggiore praticità, è possibile modificare il pulsante **Collega a Unity** in **Collega a Unity e gioca**.

1. Fare clic sulla piccola **freccia GIÙ** accanto al pulsante **Collega a Unity**.

1. Selezionare **Collega a Unity e gioca** nel menu a discesa.

    ![Collega e gioca](media/vstu_attach-and-play.png)

Il pulsante per il gioco acquisisce l'etichetta **Collega a Unity e gioca**. Fare clic su questo pulsante o usare il tasto di scelta rapida **F5** consente di passare automaticamente all'editor di Unity e di eseguire il gioco nell'editor, oltre a collegare il debugger di Visual Studio.

Fare clic sul pulsante **Interrompi** in Visual Studio o usare la scelta rapida da tastiera **Maiusc+F5** arresta automaticamente il gioco nell'editor di Unity.

### <a name="debugging-unity-player-builds"></a>Debug di compilazioni del lettore Unity

È possibile eseguire il debug di compilazioni di sviluppo di diversi lettori di Unity con Visual Studio.

#### <a name="enable-script-debugging-in-a-unity-player"></a>Per abilitare il debug di script in un lettore Unity

1. In Unity, aprire le impostazioni di compilazione selezionando **File > Impostazioni di compilazione**.

1. Nella finestra Impostazioni di compilazione del progetto Unity selezionare le caselle di controllo **Development Build** (Build di sviluppo) e **Script Debugging** (Debug di script).

 ![Configurare le impostazioni di compilazione Unity per il debug.](../cross-platform/media/vstu_debugging_build_settings.png "vstu_debugging_build_settings")

#### <a name="select-a-unity-instance-to-attach-the-debugger-to"></a>Selezionare un'istanza di Unity alla quale connettere il debugger

- Nel menu principale di Visual Studio scegliere **Debug > Collega debugger Unity**.

     ![Collegare il debugger di Unity.](../cross-platform/media/vstu_debugging_attach_unity_debugger.png "vstu_debugging_attach_unity_debugger")

    Nella finestra di dialogo **Seleziona istanza di Unity** sono visualizzate alcune informazioni sulle singole istanze di Unity a cui è possibile connettersi.

     ![Scegliere un'istanza di Unity a cui connettersi.](../cross-platform/media/vstu_attach-debugger.png "vstu_connection_to_unity")

 **Progetto** Nome del progetto Unity in esecuzione in questa istanza di Unity.

 **Computer** Nome del computer o del dispositivo in cui è in esecuzione questa istanza di Unity.

 **Digitare**
 **Editor** se questa istanza di Unity viene eseguita come parte dell'editor di Unity; **Lettore** se l'istanza di Unity è un lettore autonomo.

 **Porta** Numero di porta del socket UDP usata da questa istanza di Unity per comunicare.

> [!IMPORTANT]
> Dal momento che Visual Studio Tools per Unity e l'istanza di Unity comunicano tramite un socket di rete UDP, è possibile che il firewall non lo riconosca. In tal caso, è necessario autorizzare la connessione per consentire a VSTU e Unity di comunicare.

### <a name="debugging-a-dll-in-your-unity-project"></a>Debug di una DLL nel progetto Unity

 Molti sviluppatori Unity scrivono componenti di codice sotto forma di DLL esterne in modo da facilitare la condivisione della funzionalità sviluppata con altri progetti. Visual Studio Tools per Unity semplifica il debug del codice in queste DLL con altro codice del progetto Unity.

> [!NOTE]
> Al momento Visual Studio Tools per Unity supporta solo le DLL gestite. Non è invece supportato il debug di DLL di codice nativo, ad esempio quelle scritte in C++.

 Lo scenario descritto in questo articolo presuppone che l'utente sia proprietario del codice sorgente disponibile, ovvero che si stia sviluppando o riutilizzando il proprio codice oppure che il codice sorgente sia inserito in una libreria di terze parti e si intenda distribuirlo nel progetto Unity sotto forma di DLL. Lo scenario non illustra il debug di una DLL di cui l'utente non è proprietario del codice sorgente.

#### <a name="to-debug-a-managed-dll-project-used-in-your-unity-project"></a>Per eseguire il debug di un progetto di DLL gestita usato nel progetto Unity

1. Aggiungere il progetto di DLL esistente alla soluzione di Visual Studio generata da Visual Studio Tools per Unity. Può capitare meno frequentemente di avviare un nuovo progetto di DLL gestita per contenere i componenti di codice nel progetto Unity. In questo caso, è possibile aggiungere un nuovo progetto di DLL gestita alla soluzione Visual Studio. Per altre informazioni sull'aggiunta di un progetto nuovo o esistente a una soluzione, vedere [Procedura: Aggiungere progetti a una soluzione](https://msdn.microsoft.com/library/vstudio/ff460187.aspx).

     ![Aggiungere il progetto esistente per una DLL alla soluzione.] (../cross-platform/media/vstu_debugging_dll_add_existing.png "vstu_debugging_dll_add_existing")

     In entrambi i casi, Visual Studio Tools per Unity mantiene il riferimento al progetto, anche se deve rigenerare nuovamente i file di progetto e soluzione, di conseguenza è necessario eseguire questi passaggi una sola volta.

1. Fare riferimento al profilo del framework Unity corretto nel progetto di DLL. Nelle proprietà del progetto di DLL in Visual Studio impostare la proprietà **Framework di destinazione** sulla versione del framework Unity usata. Si tratta della libreria di classi base Unity corrispondente alla compatibilità API di destinazione del progetto, ad esempio le librerie di classi base complete, micro o Web di Unity. In questo modo la DLL non potrà chiamare metodi del framework esistenti in  altri framework o livelli di compatibilità ma che potrebbero non esistere nella versione del framework Unity usata.

     ![Impostare il framework di destinazione della DLL sul framework Unity.] (../cross-platform/media/vstu_debugging_dll_target_framework.png "vstu_debugging_dll_target_framework")

1. Copiare la DLL nella cartella Assets del progetto Unity. In Unity gli asset sono file che vengono inseriti nel pacchetto dell'app Unity e distribuiti con questa per consentirne il caricamento al runtime. Dal momento che le DLL vengono collegate al runtime, devono essere distribuite come asset. Per distribuire le DLL come asset, l'editor di Unity richiede che vengano inserite nella cartella Assets del progetto Unity. Questa operazione può essere eseguita nei due modi seguenti:

   - Modificare le impostazioni di compilazione del progetto di DLL in modo da includere un'attività di post-compilazione che copi la DLL di output e i file PDB dalla cartella di output alla cartella **Assets** (Asset) del progetto Unity.

   - Modificare le impostazioni di compilazione del progetto di DLL in modo da impostare come cartella di output la cartella **Assets** (Asset) del progetto Unity. La DLL e i file PDB verranno entrambi inseriti nella cartella **Assets** (Asset).

     I file PDB sono necessari per il debug perché contengono i simboli di debug della DLL e consentono di eseguire il mapping del codice della DLL al formato del relativo codice sorgente. Visual Studio Tools per Unity userà le informazioni della DLL e dei file PDB per creare un file DLL.MDB, che corrisponde al formato dei simboli di debug usato dal motore di scripting di Unity.

1. Eseguire il debug del codice. È ora possibile eseguire il debug del codice sorgente della DLL con il codice sorgente del progetto Unity e usare tutte le funzionalità di debug a cui si è abituati, ad esempio punti di interruzione ed esecuzione del codice un'istruzione alla volta.

## <a name="keyboard-shortcuts"></a>Scelte rapide da tastiera

 Per accedere rapidamente alle funzionalità degli strumenti Unity per Visual Studio, è possibile usare i tasti di scelta rapida elencati di seguito.

|Comando|Collegamento|Nome del comando associato al tasto di scelta rapida|
|-------------|--------------|---------------------------|
|Apri procedura guidata MonoBehaviour|**CTRL+MAIUSC+M**|**EditorContextMenus.CodeWindow.ImplementMonoBehaviours**|
|Apri Esplora progetti Unity|**ALT+MAIUSC+E**|**View.UnityProjectExplorer**|
|Accedi alla documentazione di Unity|**CTRL+ALT+M, CTRL+H**|**Help.UnityAPIReference**|
|Connetti al debugger Unity (lettore o editor)|***Non sono previsti valori predefiniti***|**Debug.AttachUnityDebugger**|

 Se si preferisce non usarle, è possibile modificare le combinazioni di tasti di scelta rapida predefinite. Per informazioni su come modificarle, vedere [Identificazione e personalizzazione dei tasti di scelta rapida in Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).
