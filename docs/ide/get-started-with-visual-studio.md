---
redirect_url: /visualstudio/ide/visual-studio-ide
ms.openlocfilehash: 5f1fa39d6e6cde1664a8aaa34aed7cba726b1d56
ms.sourcegitcommit: 64c7682ec3a2cbea684e716803398d4278b591d1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2017
---
# <a name="get-started-with-visual-studio"></a>Introduzione a Visual Studio
Visual Studio è uno strumento potente per lo sviluppo di applicazioni. Se non è ancora stato fatto, scaricare e installare [Visual Studio](https://www.visualstudio.com/vs/). Per altre informazioni su come scaricare Visual Studio e configurarlo in base alle proprie preferenze, vedere il video [Getting Started with Visual Studio - Setting up your IDE](https://www.youtube.com/watch?v=xLCedknQkN0&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=1) (Introduzione a Visual Studio - Configurazione dell'IDE).

## <a name="visual-studio-tour"></a>Presentazione di Visual Studio
Visual Studio include un gruppo di finestre degli strumenti, menu e barre degli strumenti noti come l'ambiente di sviluppo integrato o IDE. L'IDE di Visual Studio consente di eseguire le attività di sviluppo. Ecco una rapida panoramica degli elementi dell'IDE che probabilmente verranno usati più di frequente.

### <a name="code-editor"></a>Editor di codice
Una delle finestre degli strumenti più usate in Visual Studio. Da qui si eseguono attività di scrittura, visualizzazione ed esplorazione del codice.

![Editor di codice](../ide/media/VSIDE_CodeWindow.png)

Quando si immette il codice, l'editor di codice consente di scrivere e di individuare il codice più rapidamente e con maggior facilità, grazie a funzionalità come il completamento delle istruzioni, la colorazione della sintassi, la modalità di mapping e altro ancora. Per altre informazioni, vedere il video [Getting Started with Visual Studio - Editing and navigating your code](https://www.youtube.com/watch?v=4glwwioCVjA&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=5) (Introduzione a Visual Studio - Modifica ed esplorazione del codice)

Alcuni tipi di soluzioni possono includere finestre dette *form*, ad esempio form WPF (Windows Presentation Foundation), Windows Form, form XAML (Extensible Application Markup Language) e altri. In questi casi lo spazio include anche una finestra di progettazione grafica che consente di trascinare e rilasciare nel form controlli, come pulsanti o caselle di riepilogo, con i quali gli utenti interagiscono quando eseguono l'app.

### <a name="solution-explorer"></a>Esplora soluzioni
Una finestra degli strumenti chiamata **Esplora soluzioni** elenca tutti i file di codice. Esplora soluzioni consente di organizzare il codice raggruppando i file in progetti e soluzioni. Il progetto in grassetto viene chiamato *progetto di avvio*. Si tratta del primo codice eseguito all'avvio della soluzione. Il progetto di avvio può essere modificato. Per altre informazioni, vedere il video [Getting Started with Visual Studio - Building blocks of the IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) (Introduzione a Visual Studio - Blocchi predefiniti dell'IDE).

![Nodi compressi di Esplora soluzioni](../ide/media/VSIDE_SolutionExplorer2_callouts.png)

 Oltre alle soluzioni e ai progetti, quando si espande il nodo del progetto, Esplora soluzioni elenca tutti i file in ogni progetto. Ogni progetto contiene uno o più file, ad esempio i file di codice sorgente e i file di risorse quali immagini o librerie.

![Esplora soluzioni](../ide/media/VSIDE_SolutionExplorer3.png)

Per visualizzare le proprietà per soluzioni, progetti e file, scegliere il comando **Proprietà** dal menu di scelta rapida oppure scegliere **Visualizza, finestra Proprietà** dal menu.

![Finestra Proprietà](../ide/media/VSIDE_SolutionExplorer4.png)

Per iniziare a programmare, non è necessario creare una soluzione o un progetto. È possibile semplicemente aprire file di codice in Visual Studio, ad esempio file clonati da un repository Git, e iniziare subito a modificarli. I file verranno visualizzati in Esplora soluzioni, dove sarà possibile eseguire la colorazione della sintassi, il completamento delle istruzioni di base e altro ancora, proprio come per le soluzioni tradizionali. Per altre informazioni, vedere [Sviluppare codice in Visual Studio senza progetti o soluzioni](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md).

### <a name="toolbar-and-menus"></a>Barra degli strumenti e menu
Per eseguire il progetto, creare nuove soluzioni, salvare i file e altro ancora, usare i comandi della barra degli strumenti e dei menu di Visual Studio. Ad esempio, una volta che il codice è pronto per l'esecuzione del debug, è possibile scegliere il pulsante **Avvia** sulla barra degli strumenti, oppure **Debug, Avvia debug** dal menu. Per creare una nuova soluzione, scegliere il pulsante **Nuovo progetto** oppure scegliere **File, Nuovo, Progetto** dal menu e così via.

![Barra degli strumenti di Visual Studio](../ide/media/VSIDE_SolutionExplorer5_callouts.png)

Si noti che le icone della barra degli strumenti e i comandi di menu possono cambiare a seconda del contesto, ovvero dell'elemento attualmente selezionato. Quasi tutti i comandi sono accessibili tramite comandi da tastiera, oltre che con il mouse.

### <a name="team-explorer"></a>Team Explorer
**Team Explorer** consente di connettersi agli strumenti di controllo del codice sorgente, come ad esempio [Git](https://git-scm.com/) e [Controllo della versione di Team Foundation](https://www.visualstudio.com/en-us/docs/tfvc/overview) per archiviare il codice in locale o condividerlo con altri utenti su un servizio ospitato. È possibile usarlo anche per tenere traccia delle attività e altro ancora.

Per altre informazioni, vedere i video [Getting Started with Visual Studio - Building blocks of the IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) (Introduzione a Visual Studio - Blocchi predefiniti dell'IDE) e [Getting Started with Visual Studio - Opening a project from Source Control](https://www.youtube.com/watch?v=pc9vX_4RGV4&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=3) (Introduzione a Visual Studio - Aprire un progetto dal controllo del codice sorgente).

![Team Explorer](../ide/media/TeamExplorer.png)

### <a name="output-window"></a>Output (finestra)
La finestra **Output** è la finestra in cui Visual Studio invia le notifiche, ad esempio messaggi di errore e di debug, avvisi del compilatore, messaggi di stato di pubblicazione e altro. Ogni tipo di messaggio ha una propria scheda.

![Output (finestra)](../ide/media/VSIDE_OutputWindow.png)

Per altre informazioni su come usare la finestra di Output per il debug, vedere [The Output window while debugging with Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2015/02/09/the-output-window-while-debugging-with-visual-studio/) (Finestra Output per il debug con Visual Studio).

## <a name="first-steps"></a>Primi passaggi
- **Informazioni generali**: eseguire una presentazione per ottenere una panoramica di molte delle principali funzionalità in Visual Studio. Vedere [Panoramica delle funzionalità IDE di Visual Studio](../ide/visual-studio-ide.md).
- **Installazione**: per informazioni su come scaricare e installare Visual Studio, vedere [Installare Visual Studio 2017](../install/install-visual-studio.md).
- **Le nozioni di base**: per altre informazioni sul funzionamento di Visual Studio, vedere [Introduzione allo sviluppo con Visual Studio](../ide/get-started-developing-with-visual-studio.md).
- **Impostazioni**: scoprire come personalizzare Visual Studio in base alle modalità di lavoro personali. Vedere [Personalizzazione dell'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).
- **Esercitazioni**: per altre informazioni su come sviluppare codice in Visual Studio, eseguire un'esercitazione, ad esempio [Guida introduttiva a Visual C# e Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) o [Guida introduttiva a C++ in Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md).
- **Video**: per altre informazioni su altri aspetti e funzionalità di Visual Studio, guardare i video sul [canale Microsoft Visual Studio](https://www.youtube.com/user/VisualStudio/videos) su YouTube o i video di Visual Studio su [Channel 9](https://channel9.msdn.com/Tags/visual+studio) o in [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!jobf=Developer).

## <a name="access-cloud-based-resources"></a>Accedere alle risorse basate su cloud
Se si vogliono usare risorse basate su cloud nell'app o nel gioco che si sta sviluppando, è possibile farlo includendo i [servizi di Azure](https://azure.microsoft.com/en-us/services/). Installando il carico di lavoro **Sviluppo di Azure** tramite il nuovo programma di installazione di Visual Studio, è possibile ottenere Azure SDK per .NET. I pacchetti installati sono allo stesso livello di funzionalità della versione 2.9.5 dell'SDK. Per questa versione di Visual Studio e tutte le versioni future, Azure SDK per .NET sarà disponibile solo dal programma di installazione di Visual Studio.

Dopo aver installato il carico di lavoro Sviluppo di Azure, in Visual Studio diventa disponibile una nuova finestra degli strumenti denominata **Cloud Explorer**. Cloud Explorer consente di cercare e gestire le risorse di Azure da Visual Studio. Se una particolare operazione richiede il portale di Azure, Cloud Explorer specifica i collegamenti che consentono di accedere ai percorsi da seguire nel portale di Azure.

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

Per altre informazioni sull'uso di Cloud Explorer, vedere [Gestione delle risorse di Azure con Cloud Explorer](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/).
L'installazione del carico di lavoro Sviluppo di Azure offre anche gli [strumenti di Visual Studio per Azure](https://www.visualstudio.com/vs/azure-tools/), oltre ad altri strumenti correlati.

## <a name="tips-and-tricks"></a>Suggerimenti
Vedere gli argomenti seguenti per collegamenti e suggerimenti utili su come sfruttare al meglio Visual Studio.
- [Getting Started with Visual Studio - Tips & Tricks](https://www.youtube.com/watch?v=vmXqGwn1Glk&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=4) (Introduzione a Visual Studio - Suggerimenti)
- [Suggerimenti relativi alla produttività per Visual Studio](../ide/productivity-tips-for-visual-studio.md)
- [Visual Studio Tips and Tricks](https://channel9.msdn.com/events/TechEd/2013/DEV-B353) (Suggerimenti su Visual Studio)
- [C++ Debugging Tips and Tricks](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/C-Plus-Plus-Debugging-Tips-and-Tricks) (Suggerimenti sul debug in C++)
- [Visual Studio's most useful (and underused) tips [Scott Hanselman blog] (I suggerimenti più utili e meno usati per Visual Studio [Blog di Scott Hanselman])](https://www.hanselman.com/blog/VisualStudiosMostUsefulAndUnderusedTips.aspx)
- [Getting Started with Visual Studio - Installing Visual Studio extensions](https://www.youtube.com/watch?v=MWLLQaknRZY&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=7) (Introduzione a Visual Studio - Installazione delle estensioni di Visual Studio)
