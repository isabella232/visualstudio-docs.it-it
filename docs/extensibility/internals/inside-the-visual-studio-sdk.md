---
title: All'interno di Visual Studio SDK Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e72020795bc3181e11f0f90eff580a2365d4000
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707579"
---
# <a name="inside-the-visual-studio-sdk"></a>All'interno di Visual Studio SDK

In questa sezione vengono fornite informazioni approfondite sulle estensioni di Visual Studio, tra cui l'architettura di Visual Studio, i componenti, i servizi, gli schemi, le utilità e così via.

## <a name="extensibility-architecture"></a>Architettura di estensibilitàExtensibility Architecture
 Nella figura seguente viene illustrata l'architettura di estensibilità di Visual Studio.The following illustration shows the Visual Studio extensibility architecture. VSPackage forniscono funzionalità dell'applicazione, che viene condiviso tra l'IDE come servizi. L'IDE standard offre inoltre un'ampia <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>gamma di servizi, ad esempio , che consentono di accedere alla funzionalità di windowing dell'IDE.

 ![Rappresentazione grafica dell'architettura dell'ambiente](../../extensibility/internals/media/environment.gif "environment") Visualizzazione generalizzata dell'architettura di Visual Studio

## <a name="vspackages"></a>VSPackages
 I VSPackage sono moduli software che compongono ed estendono Visual Studio con elementi dell'interfaccia utente, servizi, progetti, editor e finestre di progettazione. VSPackage sono l'unità architetturale centrale di Visual Studio. Per altre informazioni, vedere [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 La shell di Visual Studio fornisce funzionalità di base e supporta la comunicazione incrociata tra i relativi componenti VSPackage ed estensioni MEF. Per ulteriori informazioni, vedere [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Linee guida sull'esperienza utente
 Se si prevede di progettare nuove funzionalità per Visual Studio, è necessario esaminare queste linee guida per la progettazione e suggerimenti sull'usabilità: Linee guida per l'esperienza utente di [Visual Studio.](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="commands"></a>Comandi:
 I comandi sono funzioni che eseguono attività, ad esempio la stampa di un documento, l'aggiornamento di una visualizzazione o la creazione di un nuovo file.

 Quando si estende Visual Studio, è possibile creare comandi e registrarli con la shell di Visual Studio.When you extend Visual Studio, you can create commands and register them with the Visual Studio shell. È possibile specificare la modalità di visualizzazione di questi comandi nell'IDE, ad esempio in un menu o una barra degli strumenti. In genere viene visualizzato un comando personalizzato nel menu **Strumenti** e nel sottomenu Altre finestre del menu **Visualizza** viene visualizzato un comando per la visualizzazione di una finestra degli **strumenti.**

 Quando si crea un comando, è necessario creare anche un gestore eventi per tale comando. Il gestore eventi determina quando il comando è visibile o abilitato, consente di modificarne il testo e garantisce che il comando risponda in modo appropriato quando viene attivato. Nella maggior parte dei casi, l'IDE gestisce i comandi utilizzando l'interfaccia. <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> I comandi in Visual Studio vengono gestiti a partire dal contesto di comando più interno, in base alla selezione locale e procedendo al contesto più esterno, in base alla selezione globale. I comandi aggiunti al menu principale sono immediatamente disponibili per lo scripting.

 Per ulteriori informazioni, consultate [Comandi, Menu e Barre degli strumenti.](../../extensibility/internals/commands-menus-and-toolbars.md)

## <a name="menus-and-toolbars"></a>Menu e barre degli strumenti
 Menu e barre degli strumenti consentono agli utenti di richiamare i comandi. I menu sono righe o colonne di comandi che in genere vengono visualizzati come singoli elementi di testo nella parte superiore di una finestra degli strumenti. I sottomenu sono menu secondari che vengono visualizzati quando un utente fa clic su comandi che includono una piccola freccia. I menu di scelta rapida vengono visualizzati quando un utente fa clic con il pulsante destro del mouse su determinati elementi dell'interfaccia utente. Alcuni nomi di menu comuni sono **File**, **Modifica**, **Visualizza**e **Finestra**. Per ulteriori informazioni, consultate [Estensione di menu e comandi.](../../extensibility/extending-menus-and-commands.md)

 Le barre degli strumenti sono righe o colonne di pulsanti e altri controlli, ad esempio caselle combinate, caselle di riepilogo e caselle di testo. I pulsanti della barra degli strumenti conscano in genere immagini icona, ad esempio un'icona di cartella per un comando **Apri file** o una stampante per un comando **Stampa.** Tutti gli elementi della barra degli strumenti sono associati ai comandi. Quando si fa clic su un pulsante della barra degli strumenti, viene eseguito il comando associato. Nel caso di un controllo a discesa, ogni elemento nell'elenco a discesa è associato a un comando diverso. Alcuni controlli della barra degli strumenti, ad esempio un controllo barra di divisione, sono ibridi. Un lato del controllo è un pulsante della barra degli strumenti e l'altro lato è una freccia rivolta verso il basso che visualizza diversi comandi quando si fa clic su di esso.

## <a name="tool-windows"></a>Finestre degli strumenti
 Le finestre degli strumenti vengono utilizzate nell'IDE per visualizzare informazioni. **Casella degli strumenti**, **Esplora soluzioni**, finestra **Proprietà** e **Browser Web** sono esempi di finestre degli strumenti.

 Finestre degli strumenti offrono in genere vari controlli con cui l'utente può interagire. Ad esempio, il **proprietà** finestra consente all'utente di impostare le proprietà degli oggetti che servono a uno scopo particolare. Il **proprietà** finestra è specializzata in questo senso, ma anche generale perché può essere utilizzato in molte situazioni diverse. Analogamente, il Output finestra è specializzata perché fornisce l'output basato su testo, ma generale perché molti sottosistemi in Visual Studio può utilizzare per fornire l'output per l'utente di Visual Studio.Similarly, the **Output** window is specialized because it provides text-based output, but general because many subsystems in Visual Studio can use it to provide output to the Visual Studio user.

 Si consideri l'immagine seguente di Visual Studio, che contiene diverse finestre degli strumenti:Consider the following picture of Visual Studio, which contains several tool windows:

 ![Screenshot](../../extensibility/internals/media/t1gui.png "T1gui")

 Alcune delle finestre degli strumenti sono ancorate insieme in un singolo riquadro che visualizza la finestra degli strumenti Esplora soluzioni e nasconde le altre finestre degli strumenti, ma le rende disponibili facendo clic sulle schede. L'immagine mostra altre due finestre degli strumenti, la finestra **Elenco errori** e **Output,** ancorate insieme in un unico riquadro.

 Viene inoltre visualizzato il riquadro principale del documento, che mostra diverse finestre dell'editor. Sebbene le finestre degli strumenti abbiano in genere una sola istanza (ad esempio, è possibile aprire una sola **Esplora soluzioni),** le finestre dell'editor possono avere più istanze, ognuna delle quali viene utilizzata per modificare un documento separato ma tutte ancorate nello stesso riquadro. L'immagine mostra un riquadro del documento con due finestre dell'editor, una finestra di progettazione di form. Tutte le finestre nel riquadro del documento sono disponibili facendo clic sulle schede, ma la finestra dell'editor che contiene EditorPane.cs file è visibile e attiva.

 Quando si estende Visual Studio, è possibile creare finestre degli strumenti che consentono agli utenti di Visual Studio di interagire con l'estensione. È anche possibile creare editor personalizzati che consentono agli utenti di Visual Studio di modificare i documenti. Poiché le finestre degli strumenti e gli editor verranno integrati in Visual Studio, non è necessario programmarli per ancorare o visualizzarli correttamente in una scheda. Quando sono registrati correttamente in Visual Studio, avranno automaticamente le funzionalità tipiche delle finestre degli strumenti e delle finestre di documento in Visual Studio. Per ulteriori informazioni, vedere [Estensione e personalizzazione delle finestre degli strumenti](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Finestre dei documenti
 Una finestra di documento è una finestra figlio con frame di una finestra di interfaccia a documenti multipli (MDI). Le finestre di documento vengono in genere utilizzate per ospitare editor di testo, editor di moduli (noti anche come finestre di progettazione) o controlli di modifica, ma possono anche ospitare altri tipi di funzionalità. La finestra di dialogo Nuovo file include esempi di finestre di documento fornite da Visual Studio.The **New File** dialog box includes examples of document windows that Visual Studio provides.

 La maggior parte degli editor sono specifici di un linguaggio di programmazione o di un tipo di file, ad esempio pagine HTML, set di frame, file di C , o file di intestazione. Selezionando un modello nella finestra di dialogo **Nuovo file,** un utente crea dinamicamente una finestra di documento per l'editor per il tipo di file associato al modello. Una finestra del documento viene creata anche quando un utente apre un file esistente.

 Le finestre di documento sono limitate all'area client MDI. Ogni finestra del documento ha una scheda nella parte superiore e l'ordine di tabulazione è collegato ad altre finestre che possono essere aperte nell'area MDI. Facendo clic con il pulsante destro del mouse sulla scheda di una finestra del documento viene visualizzato un menu di scelta rapida che include opzioni per dividere l'area MDI in più gruppi di schede orizzontali o verticali. La divisione dell'area MDI consente di visualizzare più file contemporaneamente. Per ulteriori informazioni, consultate [Documentare Windows.](../../extensibility/internals/document-windows.md)

## <a name="editors"></a>Editor
 L'editor di Visual Studio consente di personalizzarlo e utilizzarlo per il proprio tipo di contenuto tramite Managed Extensibility Framework (MEF). In molti casi non sarà necessario creare un VSPackage per estendere l'editor, anche se se si desidera includere funzionalità dalla shell (ad esempio, un comando di menu o un tasto di scelta rapida), è possibile combinare un'estensione MEF con un VSPackage.

 È inoltre possibile creare un editor personalizzato, ad esempio se si desidera leggere e scrivere in un database o se si desidera utilizzare una finestra di progettazione. È inoltre possibile utilizzare un editor esterno, ad esempio Blocco note o Microsoft WordPad. Per ulteriori informazioni, vedere [Editor ed Estensioni del servizio](../../extensibility/editor-and-language-service-extensions.md)di linguaggio .

## <a name="language-services"></a>Servizi linguistici
 Se si desidera che l'editor di Visual Studio supporti nuove parole chiave di programmazione o anche un nuovo linguaggio di programmazione, creare un servizio di linguaggio. Ogni servizio di linguaggio può implementare alcune funzionalità dell'editor completamente, parzialmente o affatto. A seconda della configurazione, il servizio di linguaggio può fornire l'evidenziazione della sintassi, la corrispondenza tra parentesi graffe, il supporto IntelliSense e altre funzionalità dell'editor.

 Il cuore di un servizio di linguaggio sono un parser e uno scanner. Uno scanner (o lexer) divide un file di origine in elementi noti come token e un parser stabilisce le relazioni tra tali token. Quando si crea un servizio di linguaggio, è necessario implementare il parser e lo scanner in modo che Visual Studio possa comprendere i token e la grammatica della lingua. È possibile creare servizi di linguaggio gestiti o non gestiti. Per ulteriori informazioni, vedere [Estensibilità del servizio di linguaggio Legacy](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Progetti

In Visual Studio i progetti sono i contenitori utilizzati dagli sviluppatori per organizzare e compilare il codice sorgente e altre risorse. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire codice sorgente, riferimenti a servizi Web e database e altre risorse. VSPackage possono estendere il sistema di progetto di Visual Studio fornendo tipi di progetto, sottotipi di progetto e strumenti personalizzati.

I progetti possono anche essere riuniti in una *soluzione*, ovvero un raggruppamento di uno o più progetti che lavorano insieme per creare un'applicazione. Le informazioni sul progetto e sullo stato relative alla soluzione vengono archiviate in due file di soluzione, il file della soluzione basata su testo (con estensione [sln)](solution-dot-sln-file.md) e il file di opzione utente della soluzione binaria [(con estensione suo).](solution-user-options-dot-suo-file.md) Questi file sono simili ai file di gruppo (con estensione vbg) utilizzati nelle versioni precedenti di Visual Basic e ai file dell'area di lavoro (con estensione dsw) e delle opzioni utente (con estensione opt) utilizzati nelle versioni precedenti di C.

Per ulteriori informazioni, vedere [Progetti](../../extensibility/internals/projects.md) e [soluzioni](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Modelli di progetti e di elementi
 Visual Studio include modelli di progetto predefiniti e modelli di elemento di progetto. È inoltre possibile creare modelli personalizzati o acquisire modelli dalla community e quindi integrarli in Visual Studio.You can also make your own templates or acquire templates from the community, and then integrate them into Visual Studio. [MSDN Code Gallery](https://code.msdn.microsoft.com/site/search?query=visual%20studio) è la posizione in cui cercare modelli ed estensioni.

 I modelli contengono la struttura del progetto e i file di base necessari per compilare un particolare tipo di applicazione, controllo, libreria o classe. Quando si desidera sviluppare software simile a uno dei modelli, creare un progetto basato sul modello e quindi modificare i file in tale progetto.

> [!NOTE]
> Questa architettura di modello [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] non è supportata per i progetti.

 Per ulteriori informazioni, vedere Aggiunta di modelli di [progetto e di elemento](../../extensibility/internals/adding-project-and-project-item-templates.md)di progetto .

## <a name="properties-and-options"></a>Proprietà e opzioni
 Nella finestra **Proprietà** vengono visualizzate le proprietà di uno o più elementi selezionati: l'estensione delle pagine [Delle opzioni delle proprietà](../../extensibility/internals/extending-properties.md) contiene set di opzioni relative a un componente specifico, ad esempio un linguaggio di programmazione o un VSPackage: Pagine Opzioni e [Opzioni](../../extensibility/internals/options-and-options-pages.md). Le impostazioni sono in genere funzionalità relative all'interfaccia utente che possono essere importate ed esportate: [Supporto per le impostazioni utente](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Servizi di Visual Studio
 Un servizio fornisce un set specifico di interfacce per i componenti da utilizzare. Visual Studio fornisce un set di servizi che possono essere utilizzati da qualsiasi componente, incluse le estensioni. Ad esempio, i servizi di Visual Studio consentono di visualizzare o nascondere le finestre degli strumenti in modo dinamico, abilitare l'accesso alla Guida, alla barra di stato o agli eventi dell'interfaccia utente. L'editor di Visual Studio fornisce anche servizi che possono essere importati dalle estensioni dell'editor. Per ulteriori informazioni, vedere [Utilizzo e fornitura di servizi](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Debugger
 Il debugger è l'interfaccia utente per i componenti di debug specifici del linguaggio. Se è stato creato un nuovo servizio di linguaggio, sarà necessario creare un motore di debug specifico per eseguire l'hook al debugger. Per ulteriori informazioni, vedere [Estensibilità del debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md)di Visual Studio .

## <a name="source-control"></a>Controllo del codice sorgente
 Per informazioni sull'implementazione di un plug-in del controllo del codice sorgente o VSPackage, vedere [controllo del codice sorgente](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Procedure guidate
 È possibile creare una procedura guidata in combinazione con un nuovo tipo di progetto, in modo che la procedura guidata possa consentire agli utenti di prendere le decisioni giuste quando creano un nuovo progetto di quel tipo. Per ulteriori informazioni, vedere [Wizards](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Strumenti personalizzati
 Gli strumenti personalizzati consentono di associare uno strumento a un elemento in un progetto ed eseguire tale strumento ogni volta che il file viene salvato. Per ulteriori informazioni, vedere [Strumenti personalizzati](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Utilità VSSDK
 VSSDK include un set di utilità che potrebbe essere necessario per lavorare con diversi aspetti di VSPackage. Per ulteriori informazioni, vedere [Utilità VSSDK](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Utilizzo di Windows Installer
 In alcuni casi potrebbe essere necessario utilizzare Windows Installer anziché il programma di installazione VSIX: ad esempio, potrebbe essere necessario scrivere nel Registro di sistema. Per informazioni sull'utilizzo di Windows Installer con le estensioni, vedere [Installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Visualizzatore della Guida
 È possibile integrare le proprie pagine della Guida e F1 nel Visualizzatore della Guida. Per ulteriori informazioni, vedere [SDK del Visualizzatore della Guida Microsoft](../../extensibility/internals/microsoft-help-viewer-sdk.md).
