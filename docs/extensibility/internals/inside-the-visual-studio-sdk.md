---
title: All'interno Visual Studio SDK | Microsoft Docs
description: Informazioni sulle estensioni in Visual Studio SDK, tra cui Visual Studio, componenti, servizi, schemi e utilità.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: fc4f300e6da070a150903281c6ff3a623576cf836b5fdd05ecb8c2b366a6ff35
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375989"
---
# <a name="inside-the-visual-studio-sdk"></a>All'interno di Visual Studio SDK

In questa sezione vengono fornite informazioni dettagliate sulle estensioni Visual Studio, tra cui Visual Studio, componenti, servizi, schemi, utilità e altro ancora.

## <a name="extensibility-architecture"></a>Architettura di estendibilità
 La figura seguente illustra l'Visual Studio di estendibilità. I pacchetti VSPackage forniscono funzionalità dell'applicazione, condivise nell'IDE come servizi. L'IDE standard offre anche un'ampia gamma di servizi, ad esempio , che consentono <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> l'accesso alla funzionalità di windowing dell'IDE.

 ![Immagine dell'architettura dell'ambiente](../../extensibility/internals/media/environment.gif "ambiente") Visualizzazione generalizzata dell'architettura Visual Studio dati

## <a name="vspackages"></a>VSPackages
 I VSPackage sono moduli software che compongono ed estendono Visual Studio con elementi dell'interfaccia utente, servizi, progetti, editor e finestre di progettazione. I pacchetti VSPackage sono l'unità centrale dell'architettura Visual Studio. Per altre informazioni, vedere [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 La Visual Studio shell fornisce funzionalità di base e supporta la comunicazione incrociata tra i pacchetti VSPackage e le estensioni MEF dei componenti. Per altre informazioni, vedere [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Linee guida sull'esperienza utente
 Se si prevede di progettare nuove funzionalità per Visual Studio, è consigliabile esaminare queste linee guida per suggerimenti sulla progettazione e l'usabilità: Visual Studio linee guida [sull'esperienza utente.](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)

## <a name="commands"></a>Comandi
 I comandi sono funzioni che eseguono attività, ad esempio la stampa di un documento, l'aggiornamento di una visualizzazione o la creazione di un nuovo file.

 Quando si estende Visual Studio, è possibile creare comandi e registrarli con la shell Visual Studio. È possibile specificare la modalità di visualizzazione di questi comandi nell'IDE, ad esempio in un menu o in una barra degli strumenti. In genere un comando personalizzato viene visualizzato nel **menu** Strumenti e un comando per la visualizzazione di una finestra degli strumenti viene visualizzato nel sottomenu Altro **Windows** del **menu** Visualizza.

 Quando si crea un comando, è necessario creare anche un gestore eventi per esso. Il gestore eventi determina quando il comando è visibile o abilitato, consente di modificarne il testo e garantisce che il comando risponda in modo appropriato quando viene attivato. Nella maggior parte dei casi, l'IDE gestisce i comandi usando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia . I comandi Visual Studio vengono gestiti a partire dal contesto di comando più interno, in base alla selezione locale, e procedendo al contesto più esterno, in base alla selezione globale. I comandi aggiunti al menu principale sono immediatamente disponibili per lo scripting.

 Per altre informazioni, vedere [Comandi, menu e barre degli strumenti.](../../extensibility/internals/commands-menus-and-toolbars.md)

## <a name="menus-and-toolbars"></a>Menu e barre degli strumenti
 I menu e le barre degli strumenti consentono agli utenti di richiamare i comandi. I menu sono righe o colonne di comandi che in genere vengono visualizzati come singole voci di testo nella parte superiore di una finestra degli strumenti. I sottomenu sono menu secondari che vengono visualizzati quando un utente fa clic su comandi che includono una piccola freccia. I menu di scelta rapida vengono visualizzati quando un utente fa clic con il pulsante destro del mouse su determinati elementi dell'interfaccia utente. Alcuni nomi di menu comuni **sono File**, **Modifica**, **Visualizza** e **Finestra**. Per altre informazioni, vedere [Estensione di menu e comandi.](../../extensibility/extending-menus-and-commands.md)

 Le barre degli strumenti sono righe o colonne di pulsanti e altri controlli, ad esempio caselle combinate, caselle di riepilogo e caselle di testo. I pulsanti della barra degli strumenti includono in genere immagini icona, ad esempio un'icona di cartella per un **comando Apri file** o una stampante per un **comando** Stampa. Tutti gli elementi della barra degli strumenti sono associati ai comandi. Quando si fa clic su un pulsante della barra degli strumenti, viene eseguito il comando associato. Nel caso di un controllo a discesa, ogni elemento nell'elenco a discesa è associato a un comando diverso. Alcuni controlli della barra degli strumenti, ad esempio un controllo barra di divisione, sono ibridi. Un lato del controllo è un pulsante della barra degli strumenti e l'altro lato è una freccia verso il basso che visualizza diversi comandi quando si fa clic su di esso.

## <a name="tool-windows"></a>Finestre degli strumenti
 Le finestre degli strumenti vengono usate nell'IDE per visualizzare informazioni. **Casella** degli **Esplora soluzioni,** **finestra** Proprietà e **Web browser sono** esempi di finestre degli strumenti.

 Le finestre degli strumenti offrono in genere vari controlli con cui l'utente può interagire. Ad esempio, la **finestra Proprietà** consente all'utente di impostare le proprietà degli oggetti che servono a uno scopo specifico. La **finestra** Proprietà è specializzata in questo senso, ma anche generale perché può essere usata in molte situazioni diverse. Analogamente, la finestra **Output** è specializzata perché fornisce output basato su testo, ma generale perché molti sottosistemi in Visual Studio possono usarlo per fornire l'output all'utente Visual Studio.

 Si consideri l'immagine Visual Studio, che contiene diverse finestre degli strumenti:

 ![Screenshot](../../extensibility/internals/media/t1gui.png "T1gui")

 Alcune delle finestre degli strumenti sono ancorate insieme in un singolo riquadro che visualizza la finestra degli strumenti Esplora soluzioni e nasconde le altre finestre degli strumenti, ma le rende disponibili facendo clic sulle schede. L'immagine mostra altre due finestre degli strumenti, **Elenco** errori e **Output,** ancorate insieme in un singolo riquadro.

 Viene anche visualizzato il riquadro principale del documento, che mostra diverse finestre dell'editor. Anche se le finestre degli strumenti hanno in genere una sola istanza (ad esempio, è possibile aprire una sola **Esplora soluzioni),** le finestre dell'editor possono avere più istanze, ognuna delle quali viene usata per modificare un documento separato, ma tutte ancorate nello stesso riquadro. L'immagine mostra un riquadro del documento con due finestre dell'editor, una finestra di progettazione form. Tutte le finestre nel riquadro del documento sono disponibili facendo clic sulle schede, ma la finestra dell'editor che contiene il file EditorPane.cs è visibile e attiva.

 Quando si estendono Visual Studio, è possibile creare finestre degli strumenti che consentono agli Visual Studio utenti di interagire con l'estensione. È anche possibile creare editor personalizzati che consentono agli utenti Visual Studio modificare i documenti. Poiché le finestre degli strumenti e gli editor verranno integrati in Visual Studio, non è necessario programmarli per ancorarli o essere visualizzati correttamente in una scheda. Quando vengono registrati correttamente in Visual Studio, avranno automaticamente le funzionalità tipiche delle finestre degli strumenti e delle finestre dei documenti in Visual Studio. Per altre informazioni, vedere [Estensione e personalizzazione degli strumenti Windows](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Finestre dei documenti
 Una finestra del documento è una finestra figlio incorniciata di una finestra dell'interfaccia a documenti multipli. Le finestre dei documenti vengono in genere usate per ospitare editor di testo, editor di form (noti anche come finestre di progettazione) o controlli di modifica, ma possono anche ospitare altri tipi funzionali. La **finestra di dialogo** Nuovo file include esempi di finestre di documento Visual Studio disponibili.

 La maggior parte degli editor è specifica di un linguaggio di programmazione o di un tipo di file, ad esempio pagine HTML, set di frame, file C++ o file di intestazione. Selezionando un modello nella finestra di dialogo Nuovo **file,** un utente crea dinamicamente una finestra del documento per l'editor per il tipo di file associato al modello. Quando un utente apre un file esistente, viene creata anche una finestra del documento.

 Le finestre dei documenti sono limitate all'area client MDI. Ogni finestra del documento ha una scheda nella parte superiore e l'ordine di tabulazione è collegato ad altre finestre che possono essere aperte nell'area MDI. Facendo clic con il pulsante destro del mouse sulla scheda di una finestra del documento viene visualizzato un menu di scelta rapida che include opzioni per suddividere l'area MDI in più gruppi di schede orizzontali o verticali. La suddivisione dell'area MDI consente la visualizzazione di più file contemporaneamente. Per altre informazioni, vedere [Document Windows](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Editor
 L Visual Studio editor consente di personalizzarlo e usarlo per il proprio tipo di contenuto tramite il Managed Extensibility Framework (MEF). In molti casi non è necessario creare un VSPackage per estendere l'editor, anche se si vogliono includere funzionalità dalla shell (ad esempio, un comando di menu o un tasto di scelta rapida), è possibile combinare un'estensione MEF con un VSPackage.

 È anche possibile creare un editor personalizzato, ad esempio se si vuole leggere e scrivere in un database o se si vuole usare una finestra di progettazione. È anche possibile usare un editor esterno, ad esempio Blocco note o Microsoft WordPad. Per altre informazioni, vedere [Editor e estensioni del servizio di linguaggio.](../../extensibility/editor-and-language-service-extensions.md)

## <a name="language-services"></a>Servizi di linguaggio
 Se si vuole che l Visual Studio editor supporti nuove parole chiave di programmazione o anche un nuovo linguaggio di programmazione, si crea un servizio di linguaggio. Ogni servizio di linguaggio può implementare determinate funzionalità dell'editor completamente, parzialmente o non affatto. A seconda della configurazione, il servizio di linguaggio può fornire evidenziazione della sintassi, corrispondenza delle parentesi graffe, supporto intelliSense e altre funzionalità nell'editor.

 Alla base di un servizio di linguaggio sono presenti un parser e uno scanner. Uno scanner (o lexer) divide un file di origine in elementi noti come token e un parser stabilisce le relazioni tra tali token. Quando si crea un servizio di linguaggio, è necessario implementare il parser e lo scanner in modo che Visual Studio possa comprendere i token e la grammatica del linguaggio. È possibile creare servizi di linguaggio gestiti o non gestiti. Per altre informazioni, vedere [Estendibilità del servizio di linguaggio legacy.](../../extensibility/internals/legacy-language-service-extensibility.md)

## <a name="projects"></a>Progetti

In Visual Studio i progetti sono i contenitori che gli sviluppatori usano per organizzare e compilare il codice sorgente e altre risorse. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire il codice sorgente, i riferimenti a database e servizi Web e altre risorse. I pacchetti VSPackage possono estendere il Visual Studio di progetto fornendo tipi di progetto, sottotipi di progetto e strumenti personalizzati.

I progetti possono anche essere raccolti insieme in una soluzione *,* ovvero un raggruppamento di uno o più progetti che lavorano insieme per creare un'applicazione. Project informazioni sullo stato relative alla soluzione vengono archiviate in due file di soluzione, il file di soluzione basato su testo (con estensione [sln)](solution-dot-sln-file.md) e il file dell'opzione utente della soluzione binaria (con estensione [suo).](solution-user-options-dot-suo-file.md) Questi file sono simili ai file di gruppo (con estensione vbg) usati nelle versioni precedenti di Visual Basic e ai file dell'area di lavoro (con estensione dsw) e alle opzioni utente (con estensione opt) usati nelle versioni precedenti di C++.

Per altre informazioni, vedere [Progetti](../../extensibility/internals/projects.md) e [soluzioni.](../../extensibility/internals/solutions-overview.md)

## <a name="project-and-item-templates"></a>Modelli di progetti e di elementi
 Visual Studio modelli di progetto predefiniti e modelli di elemento di progetto. È anche possibile creare modelli personalizzati o acquisire modelli dalla community e quindi integrarli in Visual Studio. MSDN [Code Gallery è](https://code.msdn.microsoft.com/site/search?query=visual%20studio) la posizione ideale per modelli ed estensioni.

 I modelli contengono la struttura del progetto e i file di base necessari per compilare un particolare tipo di applicazione, controllo, libreria o classe. Quando si vuole sviluppare software simile a uno dei modelli, creare un progetto basato sul modello e quindi modificare i file in tale progetto.

> [!NOTE]
> Questa architettura del modello non è supportata per i [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetti.

 Per altre informazioni, vedere [Aggiunta di Project e Project di elementi](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Proprietà e opzioni
 Nella  finestra Proprietà vengono visualizzate le proprietà di uno o più elementi [selezionati:](../../extensibility/internals/extending-properties.md) le pagine Opzioni estensione proprietà contengono set di opzioni relative a un componente specifico, ad esempio un linguaggio di programmazione o un VSPackage: opzioni e pagine delle [opzioni](../../extensibility/internals/options-and-options-pages.md). Impostazioni sono in genere funzionalità correlate all'interfaccia utente che possono essere importate ed esportate: [supporto per l'Impostazioni](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Visual Studio Servizi
 Un servizio fornisce un set specifico di interfacce da utilizzare per i componenti. Visual Studio fornisce un set di servizi che possono essere usati da qualsiasi componente, incluse le estensioni. Ad esempio, i Visual Studio consentono di visualizzare o nascondere dinamicamente le finestre degli strumenti, abilitare l'accesso alla Guida, alla barra di stato o agli eventi dell'interfaccia utente. L Visual Studio editor fornisce anche servizi che possono essere importati dalle estensioni dell'editor. Per altre informazioni, vedere [Uso e fornitura di servizi](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Debugger
 Il debugger è l'interfaccia utente per i componenti di debug specifici del linguaggio. Se è stato creato un nuovo servizio di linguaggio, sarà necessario creare un motore di debug specifico per eseguire l'hook al debugger. Per altre informazioni, vedere [estendibilità Visual Studio debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Controllo del codice sorgente
 Per informazioni sull'implementazione di un plug-in del controllo del codice sorgente o di un pacchetto VSPackage, vedere [Controllo del codice sorgente](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Procedure guidate
 È possibile creare una procedura guidata in combinazione con un nuovo tipo di progetto, in modo che la procedura guidata possa aiutare gli utenti a prendere le decisioni giuste quando creano un nuovo progetto di tale tipo. Per altre informazioni, vedere [Procedure guidate](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Strumenti personalizzati
 Gli strumenti personalizzati consentono di associare uno strumento a un elemento di un progetto ed eseguire tale strumento ogni volta che il file viene salvato. Per altre informazioni, vedere [Strumenti personalizzati](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Utilità VSSDK
 VSSDK include un set di utilità che potrebbero essere necessarie per lavorare con diversi aspetti dei pacchetti VSPackage. Per altre informazioni, vedere [Utilità VSSDK](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Uso del Windows di installazione
 In alcuni casi potrebbe essere necessario usare il programma di installazione Windows anziché il programma di installazione VSIX: ad esempio, potrebbe essere necessario scrivere nel Registro di sistema. Per informazioni sull'uso Windows installer con le estensioni, vedere Installazione di [VSPackage con](../../extensibility/internals/installing-vspackages-with-windows-installer.md)Windows Installer .

## <a name="help-viewer"></a>Visualizzatore della Guida
 È possibile integrare le proprie pagine della Guida e F1 in Help Viewer. Per altre informazioni, vedere [Microsoft Help Viewer SDK.](../../extensibility/internals/microsoft-help-viewer-sdk.md)
