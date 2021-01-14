---
title: All'interno di Visual Studio SDK | Microsoft Docs
description: Informazioni sulle estensioni in Visual Studio SDK, tra cui l'architettura, i componenti, i servizi, gli schemi e le utilità di Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 73bbb1beb30677711b8b517262b48465e7529585
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205333"
---
# <a name="inside-the-visual-studio-sdk"></a>All'interno di Visual Studio SDK

In questa sezione vengono fornite informazioni approfondite sulle estensioni di Visual Studio, tra cui l'architettura di Visual Studio, i componenti, i servizi, gli schemi, le utilità e simili.

## <a name="extensibility-architecture"></a>Architettura di estendibilità
 La figura seguente illustra l'architettura di estendibilità di Visual Studio. I pacchetti VSPackage forniscono la funzionalità dell'applicazione, che viene condivisa nell'IDE come servizi. L'IDE standard offre inoltre un'ampia gamma di servizi, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> , che consentono di accedere alla funzionalità della finestra dell'IDE.

 ![Rappresentazione grafica dell'architettura dell'ambiente](../../extensibility/internals/media/environment.gif "ambiente") Visualizzazione generalizzata dell'architettura di Visual Studio

## <a name="vspackages"></a>VSPackages
 I VSPackage sono moduli software che compongono ed estendono Visual Studio con elementi dell'interfaccia utente, servizi, progetti, editor e finestre di progettazione. I pacchetti VSPackage rappresentano l'unità centrale dell'architettura di Visual Studio. Per altre informazioni, vedere [VSPackages](../../extensibility/internals/vspackages.md).

## <a name="visual-studio-shell"></a>Visual Studio Shell
 La shell di Visual Studio offre funzionalità di base e supporta la comunicazione incrociata tra i VSPackage dei componenti e le estensioni MEF. Per ulteriori informazioni, vedere [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).

## <a name="user-experience-guidelines"></a>Linee guida sull'esperienza utente
 Se si prevede di progettare nuove funzionalità per Visual Studio, è consigliabile consultare queste linee guida per suggerimenti sulla progettazione e sull'usabilità: [linee guida sull'esperienza utente di Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).

## <a name="commands"></a>Comandi
 I comandi sono funzioni che eseguono attività, ad esempio la stampa di un documento, l'aggiornamento di una visualizzazione o la creazione di un nuovo file.

 Quando si estende Visual Studio, è possibile creare comandi e registrarli con la shell di Visual Studio. È possibile specificare il modo in cui questi comandi verranno visualizzati nell'IDE, ad esempio, in un menu o una barra degli strumenti. Un comando personalizzato viene in genere visualizzato nel menu **strumenti** e viene visualizzato un comando per la visualizzazione di una finestra degli strumenti nel sottomenu **altre finestre** del menu **Visualizza** .

 Quando si crea un comando, è necessario creare anche un gestore eventi. Il gestore eventi determina quando il comando è visibile o abilitato, consente di modificarne il testo e garantisce che il comando risponda in modo appropriato quando viene attivato. Nella maggior parte dei casi, l'IDE gestisce i comandi usando l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. I comandi in Visual Studio vengono gestiti a partire dal contesto del comando più interno, in base alla selezione locale, e procedendo verso il contesto più esterno, in base alla selezione globale. I comandi aggiunti al menu principale sono immediatamente disponibili per lo scripting.

 Per ulteriori informazioni, vedere [comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md).

## <a name="menus-and-toolbars"></a>Menu e barre degli strumenti
 I menu e le barre degli strumenti offrono agli utenti un modo per richiamare i comandi. I menu sono righe o colonne di comandi che in genere vengono visualizzati come singoli elementi di testo nella parte superiore di una finestra degli strumenti. I sottomenu sono menu secondari che vengono visualizzati quando un utente fa clic su comandi che includono una piccola freccia. I menu di scelta rapida vengono visualizzati quando un utente fa clic con il pulsante destro del mouse su determinati elementi Alcuni nomi di menu comuni sono **file**, **modifica**, **Visualizza** e **finestra**. Per altre informazioni, vedere [estensione di menu e comandi](../../extensibility/extending-menus-and-commands.md).

 Le barre degli strumenti sono righe o colonne di pulsanti e altri controlli, ad esempio caselle combinate, caselle di riepilogo e caselle di testo. I pulsanti della barra degli strumenti in genere contengono immagini icona, ad esempio un'icona di cartella per un comando **Apri file** o una stampante per un comando **stampa** . Tutti gli elementi della barra degli strumenti sono associati a comandi. Quando si fa clic su un pulsante della barra degli strumenti, viene eseguito il comando associato. Nel caso di un controllo a discesa, ogni elemento nell'elenco a discesa è associato a un comando diverso. Alcuni controlli della barra degli strumenti, ad esempio un controllo Splitter, sono ibridi. Un lato del controllo è un pulsante della barra degli strumenti e l'altro lato è una freccia rivolta verso il basso che visualizza diversi comandi quando viene selezionato.

## <a name="tool-windows"></a>Finestre degli strumenti
 Le finestre degli strumenti vengono usate nell'IDE per visualizzare le informazioni. **Casella degli strumenti**, **Esplora soluzioni**, finestra **proprietà** e **Web browser** sono esempi di finestre degli strumenti.

 Le finestre degli strumenti offrono in genere diversi controlli con cui l'utente può interagire. Ad esempio, la finestra **Proprietà** consente all'utente di impostare le proprietà degli oggetti che svolgono un particolare scopo. La finestra **Proprietà** è specializzata in questo senso, ma anche in generale perché può essere usata in diverse situazioni. Analogamente, la finestra di **output** è specializzata perché fornisce un output basato su testo, ma generale perché molti sottosistemi in Visual Studio possono usarlo per fornire l'output all'utente di Visual Studio.

 Si consideri la figura seguente di Visual Studio, che contiene diverse finestre degli strumenti:

 ![Screenshot](../../extensibility/internals/media/t1gui.png "T1gui")

 Alcune delle finestre degli strumenti sono ancorate insieme in un unico riquadro che visualizza la finestra degli strumenti Esplora soluzioni e nasconde le altre finestre degli strumenti, ma le rende disponibili facendo clic sulle schede. L'immagine mostra due altre finestre degli strumenti, la **Elenco errori** e la finestra di **output** , ancorate insieme in un unico riquadro.

 Viene visualizzato anche il riquadro principale del documento, che mostra diverse finestre dell'editor. Anche se le finestre degli strumenti hanno in genere una sola istanza (ad esempio, è possibile aprire solo un **Esplora soluzioni**), le finestre dell'editor possono avere più istanze, ciascuna delle quali viene usata per modificare un documento separato, ma tutte sono ancorate nello stesso riquadro. L'immagine mostra un riquadro del documento con due finestre dell'editor, una finestra di progettazione del form. Tutte le finestre nel riquadro del documento sono disponibili facendo clic sulle schede, ma la finestra dell'editor che contiene il file EditorPane.cs è visibile e attiva.

 Quando si estende Visual Studio, è possibile creare finestre degli strumenti che consentono agli utenti di Visual Studio di interagire con l'estensione. È anche possibile creare editor personalizzati che consentono agli utenti di Visual Studio di modificare i documenti. Poiché le finestre degli strumenti e gli editor saranno integrati in Visual Studio, non è necessario programmarli per ancorarli o visualizzarli correttamente in una scheda. Quando vengono registrati correttamente in Visual Studio, avranno automaticamente le funzionalità tipiche delle finestre degli strumenti e dei documenti in Visual Studio. Per ulteriori informazioni, vedere [estensione e personalizzazione delle finestre degli strumenti](../../extensibility/extending-and-customizing-tool-windows.md).

## <a name="document-windows"></a>Finestre dei documenti
 Una finestra del documento è una finestra figlio incorniciata di una finestra interfaccia a documenti multipli (MDI). Le finestre di documento vengono in genere usate per ospitare editor di testo, editor di moduli (noti anche come finestre di progettazione) o controlli di modifica, ma possono anche ospitare altri tipi funzionali. Nella finestra di dialogo **nuovo file** sono inclusi esempi di finestre di documento fornite da Visual Studio.

 La maggior parte degli editor è specifica di un linguaggio di programmazione o di un tipo di file, ad esempio pagine HTML, frame, file C++ o file di intestazione. Selezionando un modello nella finestra di dialogo **nuovo file** , un utente crea dinamicamente una finestra del documento per l'editor per il tipo di file associato al modello. Una finestra del documento viene creata anche quando un utente apre un file esistente.

 Le finestre dei documenti sono limitate all'area client MDI. Ogni finestra del documento dispone di una scheda nella parte superiore e l'ordine di tabulazione è collegato ad altre finestre che possono essere aperte nell'area MDI. Facendo clic con il pulsante destro del mouse sulla scheda di una finestra del documento viene visualizzato un menu di scelta rapida che include opzioni per suddividere l'area MDI in più gruppi di schede orizzontali o verticali. La suddivisione dell'area MDI consente la visualizzazione di più file contemporaneamente. Per altre informazioni, vedere [finestre dei documenti](../../extensibility/internals/document-windows.md).

## <a name="editors"></a>Editor
 L'editor di Visual Studio consente di personalizzarlo e usarlo per il proprio tipo di contenuto per mezzo del Managed Extensibility Framework (MEF). In molti casi non sarà necessario creare un pacchetto VSPackage per estendere l'editor, anche se si desidera includere funzionalità dalla shell, ad esempio un comando di menu o un tasto di scelta rapida, è possibile combinare un'estensione MEF con un pacchetto VSPackage.

 È inoltre possibile creare un editor personalizzato, ad esempio se si desidera leggere e scrivere in un database o se si desidera utilizzare una finestra di progettazione. È anche possibile usare un editor esterno, ad esempio Blocco note o Microsoft WordPad. Per ulteriori informazioni, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).

## <a name="language-services"></a>Servizi di linguaggio
 Se si vuole che l'editor di Visual Studio supporti le nuove parole chiave di programmazione o anche un nuovo linguaggio di programmazione, è possibile creare un servizio di linguaggio. Ogni servizio di linguaggio può implementare determinate funzionalità dell'editor in modo completo, parziale o non completo. A seconda di come è configurato, il servizio di linguaggio può fornire evidenziazione della sintassi, corrispondenza delle parentesi graffe, supporto IntelliSense e altre funzionalità nell'editor.

 Al centro di un servizio di linguaggio si trovano un parser e uno scanner. Uno scanner (o lexer) divide un file di origine in elementi noti come token e un parser stabilisce le relazioni tra tali token. Quando si crea un servizio di linguaggio, è necessario implementare il parser e lo scanner in modo che Visual Studio possa comprendere i token e la grammatica del linguaggio. È possibile creare servizi di linguaggio gestiti o non gestiti. Per altre informazioni, vedere [estendibilità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md).

## <a name="projects"></a>Progetti

In Visual Studio i progetti sono i contenitori usati dagli sviluppatori per organizzare e compilare il codice sorgente e altre risorse. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire codice sorgente, riferimenti a servizi Web e database e altre risorse. I pacchetti VSPackage possono estendere il sistema di progetto di Visual Studio fornendo tipi di progetto, sottotipi di progetto e strumenti personalizzati.

I progetti possono anche essere raccolti insieme in una *soluzione*, ovvero un raggruppamento di uno o più progetti che interagiscono tra loro per creare un'applicazione. Le informazioni sul progetto e sullo stato relative alla soluzione vengono archiviate in due file di soluzione, il file della soluzione basata su testo [(. sln)](solution-dot-sln-file.md) e il [file dell'opzione utente della soluzione binaria (con estensione suo)](solution-user-options-dot-suo-file.md). Questi file sono simili ai file di gruppo (con estensione VBG) usati nelle versioni precedenti di Visual Basic e i file dell'area di lavoro (con estensione DSW) e delle opzioni utente (con estensione opt) usati nelle versioni precedenti di C++.

Per altre informazioni, vedere [progetti](../../extensibility/internals/projects.md) e [soluzioni](../../extensibility/internals/solutions-overview.md).

## <a name="project-and-item-templates"></a>Modelli di progetti e di elementi
 Visual Studio include modelli di progetto e modelli di elementi di progetto predefiniti. È anche possibile creare modelli personalizzati o acquisire modelli dalla community e quindi integrarli in Visual Studio. [MSDN Code Gallery](https://code.msdn.microsoft.com/site/search?query=visual%20studio) è la posizione ideale per i modelli e le estensioni.

 I modelli contengono la struttura del progetto e i file di base necessari per compilare un particolare tipo di applicazione, controllo, libreria o classe. Quando si vuole sviluppare software simile a uno dei modelli, creare un progetto basato sul modello e quindi modificare i file nel progetto.

> [!NOTE]
> Questa architettura del modello non è supportata per i [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetti.

 Per ulteriori informazioni, vedere [aggiunta di modelli di progetto e di elementi di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="properties-and-options"></a>Proprietà e opzioni
 Nella finestra **Proprietà** vengono visualizzate le proprietà di uno o più elementi selezionati: le pagine opzioni di [estensione](../../extensibility/internals/extending-properties.md) contengono set di opzioni relative a un particolare componente, ad esempio un linguaggio di programmazione o un pacchetto VSPackage: [Opzioni e pagine opzioni](../../extensibility/internals/options-and-options-pages.md). Le impostazioni sono in genere funzionalità correlate all'interfaccia utente che possono essere importate ed esportate: [supporto per le impostazioni utente](../../extensibility/internals/support-for-user-settings.md).

## <a name="visual-studio-services"></a>Servizi di Visual Studio
 Un servizio fornisce un set specifico di interfacce per i componenti da utilizzare. Visual Studio offre un set di servizi che possono essere usati da qualsiasi componente, incluse le estensioni. I servizi di Visual Studio, ad esempio, consentono di visualizzare o nascondere le finestre degli strumenti in modo dinamico, abilitare l'accesso alla guida, alla barra di stato o agli eventi dell'interfaccia utente. L'editor di Visual Studio fornisce anche servizi che possono essere importati dalle estensioni dell'editor. Per altre informazioni, vedere [uso e fornitura di servizi](../../extensibility/using-and-providing-services.md).

## <a name="debugger"></a>Debugger
 Il debugger è l'interfaccia utente per i componenti di debug specifici della lingua. Se è stato creato un nuovo servizio di linguaggio, sarà necessario creare un motore di debug specifico da associare al debugger. Per altre informazioni, vedere [estensibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).

## <a name="source-control"></a>Controllo del codice sorgente
 Per informazioni sull'implementazione di un plug-in del controllo del codice sorgente o di un pacchetto VSPackage, vedere [controllo del codice sorgente](../../extensibility/internals/source-control.md).

## <a name="wizards"></a>Procedure guidate
 È possibile creare una procedura guidata insieme a un nuovo tipo di progetto, in modo che la procedura guidata possa aiutare gli utenti a prendere le decisioni giuste quando creano un nuovo progetto di quel tipo. Per ulteriori informazioni, vedere [procedure guidate](../../extensibility/internals/wizards.md).

## <a name="custom-tools"></a>Strumenti personalizzati
 Gli strumenti personalizzati consentono di associare uno strumento a un elemento in un progetto e di eseguire lo strumento ogni volta che il file viene salvato. Per ulteriori informazioni, vedere [strumenti personalizzati](../../extensibility/internals/custom-tools.md).

## <a name="vssdk-utilities"></a>Utilità VSSDK
 Il VSSDK include un set di utilità che potrebbero essere necessarie per lavorare con diversi aspetti dei pacchetti VSPackage. Per ulteriori informazioni, vedere [utilità VSSDK](../../extensibility/internals/vssdk-utilities.md).

## <a name="using-windows-installer"></a>Utilizzo di Windows Installer
 In alcuni casi potrebbe essere necessario usare il Windows Installer anziché il programma di installazione VSIX. ad esempio, potrebbe essere necessario scrivere nel registro di sistema. Per informazioni sull'uso di Windows Installer con le estensioni, vedere [installazione di VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

## <a name="help-viewer"></a>Visualizzatore della Guida
 È possibile integrare la guida e le pagine F1 nel Visualizzatore della guida. Per ulteriori informazioni, vedere [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).
