---
title: IDE di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 772b6cf4-cee5-42d0-bc18-b4eb07e22ff0
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 760dc4f859de68040676439d84fea60d23602aeb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49292786"
---
# <a name="visual-studio-ide"></a>IDE di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Microsoft Visual Studio 2015 è una suite di strumenti per la creazione di software, dalla fase di pianificazione fino alla progettazione dell'interfaccia utente, la codifica, i test, il debug, l'analisi della qualità del codice e delle prestazioni, la distribuzione ai clienti e la raccolta di dati di telemetria sull'utilizzo. Questi strumenti sono progettati per integrarsi perfettamente e sono tutti esposti tramite Visual Studio Integrated Development Environment (IDE).

Visual Studio può essere usato per creare diversi tipi di applicazioni, da semplici applicazioni e giochi dello Store per client mobili a sistemi complessi per aziende e data center. È possibile creare:

- Le App e giochi non solo per Windows, ma anche Android e iOS.

- Siti Web e servizi web basati su ASP.NET, JQuery, AngularJS e altri framework comuni.

- Applicazioni per piattaforme e dispositivi destinate a diversi tipi come Azure, Office, Sharepoint, Hololens, Kinect e Internet of Things, per citare solo alcuni esempi.

- Giochi e applicazioni a elevato utilizzo di grafica per un'ampia gamma di dispositivi Windows, tra cui Xbox, usando DirectX.

Per impostazione predefinita, Visual Studio offre supporto per C#, C e C++, JavaScript, F# e Visual Basic. Visual Studio funziona e si integra bene con applicazioni di terze parti come Unity tramite l’estensione [Visual Studio Tools for Unity](../cross-platform/visual-studio-tools-for-unity.md) e con Apache Cordova tramite [Visual Studio Tools per Apache Cordova](http://msdn.microsoft.com/library/db446f2c-6ba4-4c76-aac5-4c66f43b8c42). È possibile estendere manualmente Visual Studio creando strumenti personalizzati in grado di eseguire attività specializzate.

Se non si è mai usato Visual Studio in precedenza, apprendere le nozioni di base con le esercitazioni e le procedure dettagliate della [Get Started Developing with Visual Studio](../ide/get-started-developing-with-visual-studio.md) .

Se si desidera scoprire nuove funzionalità di Visual Studio 2015, vedere [What ' s New in Visual Studio 2015](../what-s-new-in-visual-studio-2015.md).

## <a name="visual-studio-setup"></a>Configurazione di Visual Studio
 Per scoprire l'edizione di Visual Studio più adatta alle proprie esigenze, vedere [Edizioni di Visual Studio](http://www.visualstudio.com/products/visual-studio-with-msdn-overview-vs).

 Per installare Visual Studio 2015, scaricarlo dalla pagina [Download di Visual Studio](http://www.visualstudio.com/downloads/download-visual-studio-vs.aspx). Se si desidera saperne di più sul processo di installazione, vedere [installazione di Visual Studio 2015](../install/install-visual-studio-2015.md).

## <a name="ide-basics"></a>Nozioni di base sull'IDE
 L'immagine seguente mostra l'IDE di Visual Studio con un progetto aperto, la finestra Esplora soluzioni per la navigazione nei file di progetto e la finestra Team Explorer per spostarsi tra gli elementi rilevati del controllo del codice sorgente e della gestione degli elementi di lavoro. Le funzionalità indicate nella barra del titolo vengono spiegate di seguito in modo più dettagliato.

 ![IDE di Visual Studio](../ide/media/visualstudioide.png "VisualStudioIDE")

### <a name="signing-in"></a>Accesso
 Quando si avvia Visual Studio per la prima volta, è possibile accedere usano l'account Microsoft o l'account aziendale o dell'istituto di istruzione. L'accesso consente di sincronizzare le impostazioni, ad esempio i layout delle finestre, tra più dispositivi e di connettersi automaticamente ai servizi richiesti, ad esempio le sottoscrizioni di Azure e Visual Studio Team Services. Se si ha una licenza basata sulla sottoscrizione, è necessario accedere a Visual Studio a intervalli regolari per mantenere aggiornati i token di licenza. Se si ha una licenza con codice Product Key, l'accesso non è necessario, ma consente di connettersi più facilmente a Visual Studio Team Services e agli account con Azure, Office 365, Salesforce.com. Per altre informazioni, vedere [Accesso a Visual Studio](../ide/signing-in-to-visual-studio.md).

 Se si hanno più account di Visual Studio Team Services, account di Azure o sottoscrizioni MSDN, è possibile collegarli e accedere alle risorse e ai servizi in tutti gli account con un unico accesso. Per altre informazioni, vedere [Work with multiple user accounts](../ide/work-with-multiple-user-accounts.md).

### <a name="staying-up-to-date"></a>Rimanere aggiornati
 L'icona di notifica nell'angolo superiore destro della barra del titolo segnala la disponibilità di aggiornamenti per Visual Studio o per i relativi componenti installati. È possibile scegliere se ignorare queste notifiche o eseguire gli aggiornamenti. Per altre informazioni, vedere [Notifiche di Visual Studio](../ide/visual-studio-notifications.md).

### <a name="finding-things-and-getting-help"></a>Operazioni di ricerca e richieste di supporto
 La finestra [Avvio veloce](../ide/reference/quick-launch-environment-options-dialog-box.md) visualizzata di seguito permette di trovare rapidamente comandi, strumenti, funzionalità e altri elementi di Visual Studio quando non si conoscono i tasti di scelta rapida o la posizione dei menu. È sufficiente digitare la propria ricerca per ottenere un collegamento da Avvio veloce.

 ![Risultati di avvio veloce per 'nuovo progetto'](../ide/media/productivity-quicklaunch.png "Productivity_QuickLaunch")

 MSDN è il sito web Microsoft per la documentazione tecnica. La pagina che si sta leggendo è di MSDN. In Visual Studio è possibile premere **F1** per passare alla pagina della Guida MSDN per la finestra attiva. È anche possibile premere **F1** nell'editor del codice per passare alla pagina della Guida MSDN per l'API o la parola chiave nella posizione corrente del punto di inserimento. Ad esempio, in un file c#, posizionare il cursore all'interno o alla fine di una `System.String` dichiarazione e premere **F1** per passare alla pagina della Guida MSDN per <xref:System.String>.

### <a name="giving-feedback"></a>Commenti e suggerimenti
 In Visual Studio i commenti e i suggerimenti possono essere inseriti in modo facile e in qualsiasi momento. Fare clic sull'icona relativa ai commenti sulla barra del titolo accanto a **Avvio veloce** , quindi su **Segnala un problema** o **Suggerimento**. Le edizioni provvisorie di Visual Studio offrono anche un'opzione **Valuta questo prodotto** . Microsoft esaminerà questi commenti e li userà per migliorare il prodotto. Per altre informazioni, vedere [Talk to Us](../ide/talk-to-us.md).

### <a name="personalizing-the-ide"></a>Personalizzazione dell'IDE
 È possibile personalizzare il layout della finestra per adattarlo al proprio stile di sviluppo. È possibile ancorare, rendere mobili o nascondere tutte le finestre in qualsiasi momento ed è anche possibile eseguire l'editor in modalità schermo intero. È possibile creare e salvare più layout di finestra personalizzati che visualizzano solo le finestre necessarie per contesti specifici. Ad esempio, si può creare un layout a schermo intero in modo che venga visualizzato solo l'editor di codice. Inoltre, si possono creare diversi layout per il debug e per le operazioni del team. Per altre informazioni, vedere [Personalizzazione del layout delle finestre](../ide/customizing-window-layouts-in-visual-studio.md).

 È possibile personalizzare Visual Studio in molti altri modi ed eseguire il roaming delle impostazioni se si lavora su più computer. Per altre informazioni, vedere [Personalizzazione dell'IDE](../ide/personalizing-the-visual-studio-ide.md).

 Per quasi tutte le funzioni sono disponibili scelte rapide da tastiera che è anche possibile personalizzare. Per creare nuove scelte rapide, digitare "Tastiera" in Avvio veloce per aprire la finestra di dialogo della tastiera. Per altre informazioni sulle opzioni, premere F1 per passare alla pagina della Guida MSDN. Per altre informazioni, vedere [Tasti di scelta rapida predefiniti in Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="connecting-to-visual-studio-team-services-and-team-foundation-server"></a>Connessione a Visual Studio Team Services e Team Foundation Server
 Visual Studio Team Services (VSTS) è un servizio basato sul cloud progettato per ospitare progetti software e consentire la collaborazione nei team. Visual Studio Team Services supporta sistemi Git e di controllo del codice sorgente di Team Foundation, nonché metodologie di sviluppo Scrum, CMMI e Agile. Controllo della versione di Team Foundation (TFVC) usa un unico repository del server centralizzato per tenere traccia e gestire le versioni dei file. Le modifiche locali vengono sempre archiviate nel server centrale, in modo che gli altri sviluppatori possano disporre delle modifiche più recenti. Team Foundation Server (TFS) 2015 è l'hub di gestione del ciclo di vita delle applicazioni per Visual Studio. Consente a tutte le parti interessate di partecipare al processo di sviluppo usando un'unica soluzione. TFS è utile anche per la gestione di team e progetti eterogenei.

 Se si ha un account di Visual Studio Team Services o di Team Foundation Server nella rete, è possibile connettersi tramite la finestra Team Explorer. Da questa finestra è possibile archiviare o estrarre il codice dal controllo del codice sorgente, gestire gli elementi di lavoro, avviare le compilazioni e accedere alle chat team e alle aree di lavoro. È possibile aprire Team Explorer **avvio veloce** o nel menu principale da **visualizzazione &#124; Team Explorer** o dal **Team &#124; Gestisci connessioni**.  Per altre informazioni su Visual Studio Team Services, vedere [www.visualstudio.com](https://www.visualstudio.com/). Per altre informazioni su Team Foundation Server, vedere [Team Foundation Server](https://www.visualstudio.com/products/tfs-overview-vs).

 L'immagine seguente mostra il riquadro Team Explorer per una soluzione ospitata in Visual Studio Team Services:

 ![Visual Studio Team Explorer](../ide/media/vs2015-teamexplorer.png "VS2015_TeamExplorer")

## <a name="creating-solutions-and-projects"></a>Creazione di soluzioni e progetti
 Sebbene sia possibile usare Visual Studio per esplorare i singoli file di codice, di solito viene usato su *progetti*. Un progetto Visual Studio è una raccolta di file e risorse che vengono compilati in un file eseguibile binario singolo per le applicazioni (ad esempio con estensione EXE, DLL, APPX). Per i siti Web non ASP.NET non vengono generati file eseguibili e il progetto contiene solo i file HTML, JavaScript e le immagini. Poiché in alcuni casi potrebbe essere necessario creare più file binari o siti Web strettamente correlati, in Visual Studio è presente il concetto di "soluzione", che può contenere più progetti o siti Web. Un progetto, in realtà, viene creato all'interno di una soluzione, alla quale è possibile aggiungere altri progetti successivamente, se necessario. Ad esempio, se si ha un progetto DLL, è possibile aggiungere un progetto EXE alla soluzione che carica e utilizza il file DLL.

 Un *modello di progetto* è una raccolta di file di codice e di impostazioni di configurazione già popolati che velocizza il processo di creazione di un tipo specifico di applicazione. Visual Studio viene fornito con molti modelli di progetto da cui scegliere e, se nessuno dei modelli predefiniti è adatto alle proprie esigenze, è possibile crearne di personalizzati. Dopo aver creato un progetto con un modello, è possibile iniziare a scrivere il proprio codice nei file forniti o nei nuovi file aggiunti. Per altre informazioni, vedere [Soluzioni e progetti](../ide/solutions-and-projects-in-visual-studio.md). La figura seguente mostra la finestra di dialogo Nuovo progetto con i modelli di progetto disponibili per le applicazioni ASP.NET.

 ![Finestra di dialogo Nuovo progetto di Visual Studio](../ide/media/vs2015-newprojectdialog.png "VS2015_NewProjectDialog")

## <a name="designing-the-user-interface"></a>Progettazione dell'interfaccia utente
 Una finestra di progettazione è uno strumento intuitivo che consente di creare un'interfaccia utente senza scrivere codice. È possibile trascinare i controlli dell'interfaccia utente, ad esempio le caselle di riepilogo, i calendari e i pulsanti dalla finestra [Toolbox](../ide/reference/toolbox.md) , in un'area di progettazione che rappresenta la finestra o la finestra di dialogo. È possibile ridimensionare e ridisporre gli elementi senza scrivere alcun codice. Le finestre di progettazione sono incluse per qualsiasi tipo di progetto con un'interfaccia utente.

 Se il progetto contiene un'interfaccia utente basata su XAML, la finestra di progettazione predefinita è Blend per Visual Studio, un sofisticato strumento di grafica perfettamente integrato con Visual Studio.

 ![Tavola da disegno](../ide/media/b5-artboard.png "b5_artboard")

|||
|-|-|
|![](../designers/media/b1-1.png "B1_1")|**Visualizzazione progettazione** Visualizza la progettazione visiva del documento. In questa visualizzazione è possibile creare o modificare oggetti nell'area di progettazione.|
|![](../designers/media/b1-2.png "B1_2")|**Breadcrumb** Consente di spostarsi rapidamente tra modalità di modifica del modello, modalità di modifica dello stile e ambito di modifica dell'oggetto per un oggetto selezionato.|
|![](../designers/media/b1-3.png "B1_3")|**Zoom** Consente di ingrandire l'area di progettazione o gli oggetti presenti su di essa.|
|![](../designers/media/b1-4.png "B1_4")|**Controlli dell'area di progettazione** Utilizzare questi controlli (**Mostra griglia di allineamento**, **Blocca sulla griglia** e **Attiva o disattiva allineamento sulla griglia**) per impostare le opzioni di allineamento. L'allineamento è utile per disporre gli oggetti uno sull'altro o su linee spaziate uniformemente nell'area di progettazione.|
|![](../designers/media/b1-5.png "B1_5")|**Editor di codice** Modificare il codice XAML, C#, C++ o Visual Basic manualmente nell'editor di codice.|

 Per altre informazioni, vedere [la progettazione di XAML in Visual Studio e Blend per Visual Studio](../designers/designing-xaml-in-visual-studio.md).

## <a name="writing-navigating-and-understanding-code"></a>Scrittura, esplorazione e comprensione del codice
 È probabile che la finestra dell'editor sarà la finestra più usata dagli sviluppatori. Visual Studio include editor per C#, C++, Visual Basic, JavaScript, XML, HTML, CSS e F#, mentre società di terze parti offrono editor di plug-in e compilatori per molti altri linguaggi.

 È possibile modificare singoli file nell'editor di testo facendo **File &#124; Apri &#124; File.** Per modificare i file in un progetto aperto, fare clic sul nome del file in Esplora soluzioni. Il codice viene colorato ed è possibile personalizzare la combinazione di colori digitando "Colori" in Avvio veloce. È possibile avere diverse finestre a schede dell'editor di testo aperte allo stesso momento. È possibile suddividere ogni finestra in modo indipendente. È anche possibile eseguire l'editor di testo in modalità schermo intero.

 ![Greetingsconsoleapp. cpp nell'editor di codice](../ide/media/c-ide-editorlinenumberswordwrapon.png "IDE_EditorLineNumbersWordWrapOn C + +")

 L'editor di testo ha un alto livello di interazione (se richiesto) e molte funzionalità per la produttività che consentono di scrivere codice in modo più rapido ed efficace. Le funzionalità variano in base al linguaggio e non è necessario usare alcun linguaggio (digitando "Editor" in Avvio veloce) per attivarle o disattivarle. Alcune delle funzionalità di produttività usate più di frequente sono:

1.  [Refactoring](../ide/refactoring-in-visual-studio.md) include operazioni come la ridenominazione intelligente delle variabili, lo spostamento delle righe di codice selezionate in funzioni separate, lo spostamento di codice in altre posizioni, il riordinamento dei parametri di funzione e molto altro.

2.  *IntelliSense* è un termine generico che comprende diverse funzionalità comuni che visualizzano le informazioni sul tipo di codice direttamente nell'editor e, in alcuni casi, scrivono automaticamente piccole parti di codice. È come se si avesse a disposizione la documentazione di base all'interno dell'editor, senza dover cercare le informazioni sul tipo in una finestra della Guida separata. Le funzionalità di IntelliSense variano a seconda del linguaggio. Per altre informazioni, vedere [Visual C# IntelliSense](../ide/visual-csharp-intellisense.md), [Visual C++ Intellisense](../ide/visual-cpp-intellisense.md), [JavaScript IntelliSense](../ide/javascript-intellisense.md), [Visual Basic-Specific IntelliSense](../ide/visual-basic-specific-intellisense.md). La figura seguente illustra alcune funzionalità di IntelliSense:

     ![Elenco dei membri di Visual Studio](../ide/media/vs2015-intellisense.png "vs2015_Intellisense")

3.  **Linee a zigzag** : segnalano errori o potenziali problemi nel codice in tempo reale durante la digitazione e consentono di risolverli immediatamente senza attendere che vengano rilevati durante la fase di compilazione o di esecuzione. Se si passa il mouse su una linea a zigzag, vengono visualizzate informazioni aggiuntive sull'errore. Sul margine sinistro può essere visualizzata anche una lampadina con i suggerimenti su come risolvere l'errore. Per altre informazioni, vedere [Perform quick actions with light bulbs](../ide/perform-quick-actions-with-light-bulbs.md).

     ![Lampadina con passaggio del mouse](../ide/media/vs2015-lightbulb-hover.png "VS2015_LightBulb_Hover")

4.  I [segnalibri](../ide/setting-bookmarks-in-code.md) consentono di passare rapidamente a righe specifiche dei file in uso.

5.  Nel menu di scelta rapida dell'editor di testo è possibile richiamare la finestra [Call Hierarchy](../ide/reference/call-hierarchy.md) per visualizzare i metodi che chiamano e vengono chiamati dal metodo sotto il punto di inserimento.

6.  **CodeLens** : consente di trovare i riferimenti e le modifiche al codice, i bug collegati, gli elementi di lavoro, le revisioni del codice e gli unit test senza uscire dall'editor. Per altre informazioni, vedere [Trovare le modifiche apportate al codice e altri elementi della cronologia](../ide/find-code-changes-and-other-history-with-codelens.md).

7.  La finestra **Visualizza definizione** mostra un metodo o una definizione di tipo inline senza uscire dal contesto corrente. Questa finestra ora funziona anche con XAML.

8.  L'opzione del menu di scelta rapida **Vai a definizione** visualizza direttamente la posizione in cui è definita la funzione o l'oggetto. Facendo clic con il pulsante destro del mouse nell'editor sono disponibili anche altri comandi di spostamento.

9. Uno strumento correlato, [Visualizzatore oggetti](http://msdn.microsoft.com/en-us/f89acfc5-1152-413d-9f56-3dc16e3f0470), consente di controllare gli assembly .NET o Windows Runtime nel sistema per vedere quali tipi contengono e quali metodi e proprietà contengono questi tipi.

     ![Visualizzatore oggetti con System.Timer](../ide/media/objectbrowser.png "ObjectBrowser")

 Molte voci dei menu Modifica e Visualizza sono collegate in qualche modo all'editor di codice. Per altre informazioni sull'editor, vedere [Scrittura di codice nell'editor di testo e del codice](../ide/writing-code-in-the-code-and-text-editor.md) e [Modifica del codice](https://www.visualstudio.com/features/ide-vs).

## <a name="compiling-and-building-your-code"></a>Creazione e compilazione del codice

Creare un progetto significa compilare il codice sorgente ed eseguire tutti i passaggi necessari per generare il file eseguibile. I diversi linguaggi hanno operazioni di compilazione distinte, mentre i normali siti Web non vengono compilati. Indipendentemente dal tipo di progetto, il menu Compila è la posizione standard in cui si trovano questi comandi. Per compilare ed eseguire il codice con un'unica operazione, premere F5. Ogni compilatore può essere completamente configurato tramite l'IDE. La barra degli strumenti di compilazione consente di specificare se si vuole creare una versione di debug del programma, con simboli e controllo degli errori aggiuntivo abilitato per supportare i punti di interruzione e l'esecuzione di istruzioni singole nel debugger, oppure una build di rilascio, ossia ciò che viene effettivamente fornito ai clienti al termine della compilazione. Nella pagina delle proprietà di un progetto è possibile configurare ulteriori impostazioni di compilazione e di altro tipo. Fare clic con il pulsante destro del mouse sul nodo del progetto in Esplora soluzioni, quindi scegliere Proprietà. Le compilazioni possono essere eseguite anche dalla riga di comando.

L'output di compilazione, tra cui un messaggio di errore o di completamento, viene visualizzato nei **Output** finestra. Il **elenco errori** Mostra informazioni dettagliate sugli errori di compilazione.

## <a name="debugging-your-code"></a>Debug del codice
 Il debugger avanzato di Visual Studio consente di eseguire il debug di codice in esecuzione nel progetto locale, in un dispositivo remoto o in un emulatore, ad esempio quelli per Android o Windows Phone. È possibile esaminare il codice un'istruzione alla volta e controllare le variabili man mano, eseguire applicazioni multithread e impostare punti di interruzione raggiunti solo quando una determinata condizione è true. Tutte queste funzionalità possono essere configurate nell'editor di codice, senza uscire dal contesto del codice.

 ![Finestra di anteprima impostazioni punto di interruzione](../ide/media/dbg-breakpoints-peekwindow.png "DBG_Breakpoints_PeekWindow")

 Il debugger stesso ha a disposizione più finestre che consentono di visualizzare e modificare le variabili locali, lo stack di chiamate e altri aspetti dell'ambiente di runtime. Le finestre sono disponibili nel menu **Debug** .

 La [Immediate Window](../ide/reference/immediate-window.md) consente di digitare un'espressione e visualizzare immediatamente il risultato.

 La finestra [IntelliTrace](http://msdn.microsoft.com/en-us/629e9660-c59a-446b-8c30-290059158f61) registra ogni chiamata al metodo e altri eventi in un programma .NET in esecuzione e aiuta a individuare rapidamente la causa di un problema.

 Per altre informazioni, vedere [Debug in Visual Studio](../debugger/debugging-in-visual-studio.md).

## <a name="testing-your-code"></a>Test del codice
 Visual Studio include un framework unit test per il codice gestito (.NET) e uno per C++ nativo. Per creare gli unit test, aggiungere semplicemente un progetto di test alla soluzione, scrivere i test, quindi eseguirli nella finestra Esplora test. Per altre informazioni, vedere [Eseguire unit test del codice](../test/unit-test-your-code.md).

 ![Esplora unit test](../ide/media/ute-failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")

## <a name="analyzing-code-quality-and-performance"></a>Analisi delle prestazioni e della qualità del codice
 Visual Studio include potenti strumenti per l'analisi statica e di runtime. Gli strumenti di analisi statica consentono di identificare potenziali errori di progettazione, globalizzazione, interoperabilità, prestazioni, sicurezza e altre categorie. Il test delle prestazioni, o profilatura, comporta la misurazione della modalità di esecuzione del programma. Per accedere a questi strumenti, usare il menu **Analizza** . Per altre informazioni, vedere [Miglioramento della qualità con gli strumenti di diagnostica di Visual Studio](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945).

## <a name="connecting-to-cloud-services-and-databases"></a>Connessione ai database e ai servizi cloud
 La finestra [Esplora server](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) di Visual Studio include le risorse di tutti gli account gestiti con l'account di personalizzazione (l'account usato per la connessione), tra cui le istanze di SQL Server, Azure, Salesforce.com, Office 365 e i siti Web.

 ![Esplora server](../ide/media/vs2015-serverexplorer3.png "vs2015_ServerExplorer3")

 Visual Studio include [Microsoft SQL Server Data Tools](https://msdn.microsoft.com/data/tools.aspx) (SSDT), che consente di compilare, eseguire il debug, mantenere ed eseguire il refactoring dei database. È possibile usare un progetto di database o direttamente un'istanza del database connesso locale o remota.

 Esplora oggetti di SQL Server in Visual Studio offre una visualizzazione degli oggetti di database simile a quella di SQL Server Management Studio. Esplora oggetti di SQL Server consente di eseguire operazioni semplici di progettazione e amministrazione del database, tra cui la modifica dei dati della tabella, il confronto di schemi e l'esecuzione di query, usando i menu di scelta rapida direttamente da Esplora oggetti di SQL Server. SQL Server Data Tools include anche strumenti e tipi di progetto specifici per lo sviluppo di SQL Server 2012 Analysis Services, Reporting Services e soluzioni di Integration Services Business Intelligence (precedentemente noto come Business Intelligence Development Studio).

 ![Esplora oggetti di SQL Server](../ide/media/vs2015-sqlobjectexplorer.png "vs2015_SQLObjectExplorer")

## <a name="deploying-your-finished-application"></a>Distribuzione dell'applicazione completata
 Quando l'applicazione è pronta per la distribuzione ai clienti, Visual Studio fornisce gli strumenti appropriati, a seconda che si tratti di una distribuzione per Windows Store, per un sito Sharepoint o tramite tecnologie InstallShield o Windows Installer. Tutti gli strumenti sono accessibili dall'IDE. Per altre informazioni, vedere [Distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md).

## <a name="architecture-and-modeling-tools-enterprise-only"></a>Strumenti di architettura e modellazione (solo Enterprise)
 È possibile usare gli strumenti di architettura e modellazione di Visual Studio per progettare e modellare l'applicazione. Questi strumenti consentono di visualizzare la struttura, il comportamento e le relazioni del codice. È possibile creare modelli con diversi livelli di dettaglio in tutto il ciclo di vita dell'applicazione nel contesto del processo di sviluppo. È possibile tenere traccia di requisiti, attività, test case, bug e altre operazioni associate ai modelli collegando gli elementi del modello agli elementi di lavoro di Team Foundation Server e al piano di sviluppo. Per altre informazioni, vedere [Progettare e modellare l'applicazione](../modeling/analyze-and-model-your-architecture.md).

## <a name="extending-visual-studio-through-the-visual-studio-sdk"></a>Estensione di Visual Studio tramite Visual Studio SDK
 Visual Studio è una piattaforma estendibile. Un'estensione di Visual Studio è uno strumento personalizzato che si integra con l'IDE. È possibile aggiungere estensioni di terze parti o crearne di proprie. Per altre informazioni, vedere [Sviluppo di estensioni di Visual Studio](http://msdn.microsoft.com/library/5b1b5db3-6005-44cf-83b0-e608d7764d14).

 Le [Visual Studio User Experience Guidelines](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md) costituiscono un riferimento essenziale per chiunque scriva estensioni per Visual Studio. Queste linee guida specifiche della piattaforma includono informazioni sulla progettazione di finestre di dialogo, tipi di carattere, colori, icone, controlli comuni e altri modelli di interazione che consentono l’integrazione della nuova funzionalità con Visual Studio.

## <a name="in-this-guide"></a>In questa guida

|||
|-|-|
|[Account utente e aggiornamenti](../ide/user-accounts-and-updates.md)|[Personalizzazione dell'IDE](../ide/personalizing-the-visual-studio-ide.md)|
|[How to: Move Around in the IDE](../ide/how-to-move-around-in-the-visual-studio-ide.md) (Procedura: Spostarsi all'interno dell'IDE)|[Introduzione allo sviluppo con Visual Studio](../ide/get-started-developing-with-visual-studio.md)|
|[Ricerca e uso delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|[Solutions and Projects](../ide/solutions-and-projects-in-visual-studio.md) (Soluzioni e progetti)|
|[Writing Code](../ide/writing-code-in-the-code-and-text-editor.md) (Scrittura di codice)|[Debug in Visual Studio](../debugger/debugging-in-visual-studio.md)|
|[Profiling Tools](../profiling/profiling-tools.md) (Strumenti di profilatura)|[Migliorare la qualità del codice](http://msdn.microsoft.com/library/73baa961-c21f-43fe-bb92-3f59ae9b5945)|
|[Progettazione delle interfacce utente](../designers/designing-user-interfaces.md)|[Analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md)|
|[Compiling and Building](../ide/compiling-and-building-in-visual-studio.md) (Compilazione e creazione)|[Distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md)|
|[Supporto a 64 bit per l'IDE di Visual Studio](../ide/visual-studio-ide-64-bit-support.md)|[Sicurezza](../ide/security-in-visual-studio.md)|
|[Esempi di Visual Studio](../ide/visual-studio-samples.md)|[Microsoft Help Viewer](../ide/microsoft-help-viewer.md)|
|[Globalizzazione e localizzazione di applicazioni](../ide/globalizing-and-localizing-applications.md)|[Riferimento all'interfaccia utente](../ide/reference/general-user-interface-elements-visual-studio.md)|

## <a name="see-also"></a>Vedere anche

- [Installazione di Visual Studio 2015](../install/install-visual-studio-2015.md)
- [Modifica del codice](https://www.visualstudio.com/features/ide-vs)
- [Novità di Visual Studio 2015](../what-s-new-in-visual-studio-2015.md)
- [Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
- [Talk to Us](../ide/talk-to-us.md) (Comunicazioni con Microsoft)