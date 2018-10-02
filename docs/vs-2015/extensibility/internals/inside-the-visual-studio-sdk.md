---
title: All'interno di Visual Studio SDK | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- roadmap, Visual Studio integration SDK
- Visual Studio integration SDK roadmap
- integration roadmap, Visual Studio SDK
ms.assetid: 9118eaa4-0453-4dc5-9e16-c7062d254869
caps.latest.revision: 31
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bf54468618e12abdd29921677687201f9840a70c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519666"
---
# <a name="inside-the-visual-studio-sdk"></a>All'interno di Visual Studio SDK
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [all'interno di Visual Studio SDK](https://docs.microsoft.com/visualstudio/extensibility/internals/inside-the-visual-studio-sdk).  
  
In questa sezione fornisce informazioni approfondite sulle estensioni di Visual Studio, tra cui architettura di Visual Studio, componenti, servizi, schemi, utilità e simili.  
  
## <a name="extensibility-architecture"></a>Architettura di estendibilità  
 La figura seguente mostra l'architettura di estendibilità di Visual Studio. I pacchetti VSPackage forniscono funzionalità di applicazione, che sono condivisi tra più IDE come servizi. L'IDE standard offre inoltre un'ampia gamma di servizi, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, che consentono di accedere alle funzionalità windowing di IDE.  
  
 ![Rappresentazione grafica dell'architettura di ambiente](../../extensibility/internals/media/environment.gif "ambiente")  
Generalizzato vista dell'architettura di Visual Studio  
  
## <a name="vspackages"></a>VSPackages  
 I VSPackage sono moduli software che compongono ed estendono Visual Studio con elementi dell'interfaccia utente, servizi, progetti, editor e finestre di progettazione. I VSPackage rappresentano l'unità centrale dell'architettura di Visual Studio. Per altre informazioni, vedere [VSPackage](../../extensibility/internals/vspackages.md).  
  
## <a name="visual-studio-shell"></a>Visual Studio Shell  
 La shell di Visual Studio fornisce funzionalità di base e supportare la comunicazione incrociata tra il componente VSPackage ed estensioni MEF. Per altre informazioni, vedere [Visual Studio Shell](../../extensibility/internals/visual-studio-shell.md).  
  
## <a name="user-experience-guidelines"></a>Linee guida sull'esperienza utente  
 Se si prevede di nuove funzionalità di progettazione per Visual Studio, è necessario dare un'occhiata a queste linee guida per i suggerimenti di progettazione e l'usabilità: [Visual Studio User Experience Guidelines](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="commands"></a>Comandi:  
 I comandi sono funzioni che eseguono attività, ad esempio la stampa di un documento, l'aggiornamento di una visualizzazione o la creazione di un nuovo file.  
  
 Quando si estende Visual Studio, è possibile creare comandi e registrarli con la shell di Visual Studio. È possibile specificare come questi comandi verranno visualizzato nell'IDE, ad esempio, in un menu o sulla barra degli strumenti. In genere viene visualizzato un comando personalizzato nel **strumenti** menu e un comando per la visualizzazione di una finestra degli strumenti verrà visualizzata nel **Other Windows** sottomenu del **visualizzazione** menu.  
  
 Quando si crea un comando, è necessario creare anche un gestore eventi per tale. Il gestore eventi determina quando il comando è visibile o abilitato, è possibile modificare il testo e garantisce che il comando risponda in modo appropriato quando viene attivato. Nella maggior parte dei casi, l'IDE gestisce i comandi usando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. I comandi in Visual Studio vengono gestiti inizia con il contesto del comando più interno, in base alla selezione locale e procedendo verso il contesto più esterno, in base alla selezione globale. I comandi aggiunti al menu principale sono immediatamente disponibili per lo scripting.  
  
 Per altre informazioni, vedere [comandi, menu e barre degli strumenti](../../extensibility/internals/commands-menus-and-toolbars.md).  
  
## <a name="menus-and-toolbars"></a>Menu e barre degli strumenti  
 Menu e barre degli strumenti consentono agli utenti di richiamare comandi. I menu sono righe o colonne di comandi che in genere vengono visualizzate come singoli elementi di testo nella parte superiore di una finestra degli strumenti. Sottomenu sono menu secondari che appaiono quando un utente sceglie i comandi che includono una piccola freccia. Menu di scelta rapida vengono visualizzati quando un utente fa clic determinati elementi dell'interfaccia utente. Alcuni nomi di menu comuni **File**, **Edit**, **visualizzazione**, e **finestra**. Per altre informazioni, vedere [estensione di menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
 Le barre degli strumenti sono righe o colonne di pulsanti e altri controlli, ad esempio le caselle combinate, caselle di riepilogo e caselle di testo. I pulsanti della barra degli strumenti hanno in genere immagini icona, ad esempio un'icona di cartella per un **Apri File** comando o una stampante per una **stampa** comando. Tutti gli elementi della barra degli strumenti sono associati a comandi. Quando si fa clic su un pulsante della barra degli strumenti, viene eseguito il comando associato. Nel caso di un controllo elenco a discesa, ogni elemento nell'elenco a discesa elenco è associato a un comando diverso. Alcuni controlli della barra degli strumenti, ad esempio un controllo barra di divisione, sono ibridi. Un lato del controllo è un pulsante della barra degli strumenti e l'altro lato è una freccia verso il basso che visualizza comandi diversi quando viene selezionato.  
  
## <a name="tool-windows"></a>Finestre degli strumenti  
 Finestre degli strumenti vengono usate nell'IDE per visualizzare le informazioni. **Casella degli strumenti**, **Esplora soluzioni**, **delle proprietà** finestra, e **Web Browser** sono riportati alcuni esempi di finestre degli strumenti.  
  
 Finestre degli strumenti offrono in genere vari controlli con cui l'utente può interagire. Ad esempio, il **proprietà** finestra consente all'utente di impostare le proprietà degli oggetti uno scopo specifico. Il **proprietà** finestra è specializzato in questo senso, ma anche generali perché può essere usato in molte situazioni diverse. Analogamente, il **Output** finestra è specializzata in quanto fornisce output basato su testo, ma generali perché molti sottosistemi in Visual Studio possono usarlo per fornire l'output all'utente di Visual Studio.  
  
 Prendere in considerazione l'immagine seguente di Visual Studio, che contiene diverse finestre degli strumenti.  
  
 ![Cattura di schermata](../../extensibility/internals/media/t1gui.png "T1gui")  
  
 Alcune delle finestre degli strumenti sono ancorate insieme in un unico riquadro che consente di visualizzare la finestra degli strumenti Esplora soluzioni e nasconde le altre finestre degli strumenti, ma li rende disponibili facendo clic sulle schede. Nella figura sono illustrate due altre finestre degli strumenti, il **elenco errori** e **Output** finestra ancorata insieme in un unico riquadro.  
  
 Viene inoltre illustrato il riquadro principale del documento che illustra diverse finestre dell'editor. Anche se finestre degli strumenti hanno in genere una sola istanza (ad esempio, è possibile aprire un solo **Esplora soluzioni**), finestre dell'editor possono avere più istanze, ognuno dei quali è possibile modificare un documento separato, ma che vengono ancorati in nel riquadro stesso. La figura mostra un riquadro del documento che dispone di due finestre dell'editor, una finestra di progettazione di form e una finestra del browser che mostra la pagina iniziale. Tutte le finestre nel riquadro del documento sono disponibili facendo clic sulle schede, ma la finestra dell'editor che contiene file EditorPane.cs è visibile e attivo.  
  
 Quando si estende Visual Studio, è possibile creare lo strumento windows che consentono agli utenti di Visual Studio di interagire con l'estensione. È anche possibile creare il proprio editor che consentono agli utenti di Visual Studio modificare i documenti. Poiché l'editor e finestre degli strumenti verrà integrato in Visual Studio, non devi programmarli per ancorare o vengano visualizzate correttamente in una scheda. Quando vengono registrati correttamente in Visual Studio, avranno automaticamente le funzionalità tipiche delle finestre degli strumenti e finestre dei documenti in Visual Studio. Per altre informazioni, vedere [estensione e personalizzazione di Windows lo strumento](../../extensibility/extending-and-customizing-tool-windows.md).  
  
## <a name="document-windows"></a>Finestre dei documenti  
 Una finestra del documento è una finestra cornice figlio di una finestra di interfaccia a documenti multipli (MDI). Le finestre dei documenti in genere usate per ospitare gli editor di testo, editor di form (noto anche come finestre di progettazione) o controlli di modifica, ma che possono ospitare anche altri tipi di funzionalità. Il **nuovo File** nella finestra di dialogo sono inclusi esempi di finestre dei documenti fornite da Visual Studio.  
  
 La maggior parte degli editor sono specifiche per un linguaggio di programmazione o in un tipo di file, ad esempio pagine HTML, pagine con frame, i file di C++ o file di intestazione. Selezionando un modello nel **nuovo File** nella finestra di dialogo in modo dinamico un utente crea una finestra del documento per l'editor per il tipo di file che viene associato al modello. Quando un utente apre un file esistente, viene creata anche una finestra di documento.  
  
 Le finestre dei documenti sono limitate all'area client MDI. Ogni finestra del documento contiene una scheda nella parte superiore e ordine di tabulazione è collegato ad altre finestre che possono essere aperte nell'area di MDI. Facendo clic sulla scheda di una finestra del documento consente di visualizzare un menu di scelta rapida che include opzioni per suddividere l'area MDI in più gruppi di schede orizzontali o verticali. Suddividere l'area MDI consente a più file da visualizzare nello stesso momento. Per altre informazioni, vedere [documento Windows](../../extensibility/internals/document-windows.md).  
  
## <a name="editors"></a>Editor  
 Editor di Visual Studio consente di personalizzarlo e usarlo per il proprio tipo di contenuto mediante Managed Extensibility Framework (MEF). In molti casi non dovrai creare un pacchetto VSPackage per estendere l'editor, anche se se si desidera includere funzionalità dalla shell (ad esempio, un comando di menu o un tasto di scelta rapida), è possibile combinare un'estensione MEF con un pacchetto VSPackage.  
  
 È anche possibile creare un editor personalizzato, ad esempio, se si desidera leggere e scrivere in un database o se si vuole usare una finestra di progettazione. È anche possibile usare un editor esterno, ad esempio Blocco note o WordPad Microsoft. Per altre informazioni, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
## <a name="language-services"></a>Servizi di linguaggio  
 Se si desidera che l'editor di Visual Studio per supportare nuove parole chiave di programmazione o anche un nuovo linguaggio di programmazione, si crea un servizio di linguaggio. Ogni servizio di linguaggio può implementare determinate funzionalità dell'editor completo, parziale o non ricorrere affatto. A seconda del modo in cui è configurato, il servizio di linguaggio può fornire l'evidenziazione della sintassi, corrispondenza parentesi graffe, il supporto IntelliSense e altre funzionalità dell'editor.  
  
 Il fulcro di un servizio di linguaggio sono uno scanner e parser. Uno scanner (o lexer) un file di origine viene suddivisa in elementi che sono note come token e un parser consente di stabilire le relazioni tra tali token. Quando si crea un servizio di linguaggio, è necessario implementare il parser e lo scanner in modo che Visual Studio può comprendere i token e la grammatica del linguaggio. È possibile creare servizi di linguaggio gestito o non gestito. Per altre informazioni, vedere [estensibilità del servizio di linguaggio Legacy](../../extensibility/internals/legacy-language-service-extensibility.md).  
  
## <a name="projects"></a>Progetti  
 In Visual Studio, i progetti sono contenitori utilizzati dagli sviluppatori per organizzare e compilare il codice sorgente e altre risorse. I progetti consentono di organizzare, compilare, eseguire il debug e distribuire il codice sorgente, i riferimenti a servizi Web e database e altre risorse. I pacchetti VSPackage possono estendere il sistema di progetto di Visual Studio, fornendo tipi di progetto, sottotipi di progetto e strumenti personalizzati.  
  
 I progetti possono anche essere raccolti in una soluzione, ovvero un raggruppamento di uno o più progetti che funzionano insieme per creare un'applicazione. Informazioni di progetto e lo stato relativo alla soluzione vengono archiviate in due file di soluzione, il file della soluzione basata su testo (con estensione sln) e il file di soluzione binario utente opzione (con estensione suo). Questi file sono simili ai file di gruppo (VBG) che sono stati usati nelle versioni precedenti di [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], e l'area di lavoro (con estensione DSW) e le opzioni utente (con estensione OPT) i file che sono stati usati nelle versioni precedenti di [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)].  
  
 Per altre informazioni, vedere [progetti](../../extensibility/internals/projects.md) e [soluzioni](../../extensibility/internals/solutions.md).  
  
## <a name="project-and-item-templates"></a>Modelli di progetti e di elementi  
 Visual Studio include modelli di progetto predefiniti e i modelli di progetto. È possibile inoltre rendere i propri modelli o acquisire modelli della community e li integrano in Visual Studio. Il [MSDN Code Gallery](http://code.msdn.microsoft.com/Project/ProjectDirectory.aspx?ProjectSearchText=visual%20studio) è lo strumento ideale per i modelli e le estensioni.  
  
 I modelli contengono la struttura del progetto e file di base necessari per compilare un particolare tipo di applicazione, controllo, raccolta o classe. Quando si desidera sviluppare software che è simile a uno dei modelli, creare un progetto che si basa sul modello e quindi modificare i file in tale progetto.  
  
> [!NOTE]
>  Questa architettura del modello non è supportata per [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] progetti. Per informazioni su come creare [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] modelli di progetto, vedere [progettare una procedura guidata](http://msdn.microsoft.com/library/a7c0be7e-9297-4fed-83e3-5645c896d56b).  
  
 Per altre informazioni, vedere [aggiunta di progetto e modelli di elemento di progetto](../../extensibility/internals/adding-project-and-project-item-templates.md).  
  
## <a name="properties-and-options"></a>Proprietà e le opzioni  
 Il **delle proprietà** finestra vengono visualizzate le proprietà di uno o più elementi selezionati: [estensione di proprietà](../../extensibility/internals/extending-properties.md) pagine Opzioni contengono set di opzioni che si riferiscono a un determinato componente, ad esempio un linguaggio di programmazione o un pacchetto VSPackage: [opzioni e le pagine di opzioni](../../extensibility/internals/options-and-options-pages.md). Le impostazioni sono le funzionalità in genere correlati dell'interfaccia utente che possono essere importate ed esportate: [supporto per le impostazioni utente](../../extensibility/internals/support-for-user-settings.md).  
  
## <a name="visual-studio-services"></a>Servizi di Visual Studio  
 Un servizio fornisce un set specifico di interfacce per i componenti da utilizzare. Visual Studio offre un set di servizi che può essere utilizzato da tutti i componenti, incluse le estensioni. Ad esempio, servizi Visual Studio abilitare finestre degli strumenti per essere visualizzato o nascosto in modo dinamico, abilitare l'accesso alla Guida in linea, barra di stato o eventi dell'interfaccia utente. Editor di Visual Studio fornisce anche servizi che possono essere importati tramite le estensioni dell'editor. Per altre informazioni, vedere [sull'utilizzo e la fornitura di servizi](../../extensibility/using-and-providing-services.md).  
  
## <a name="debugger"></a>Debugger  
 Il debugger è l'interfaccia utente per i componenti di debug specifiche della lingua. Se è stato creato un nuovo servizio di linguaggio, è necessario creare un motore di debug specifiche per associare il debugger. Per altre informazioni, vedere [Extensibility di Visual Studio Debugger](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="source-control"></a>Controllo del codice sorgente  
 Per informazioni sull'implementazione di un plug-in del controllo del codice sorgente o un pacchetto VSPackage, vedere [controllo del codice sorgente](../../extensibility/internals/source-control.md).  
  
## <a name="wizards"></a>Procedure guidate  
 È possibile creare una procedura guidata in combinazione con un nuovo tipo di progetto, in modo che la procedura guidata può aiutare gli utenti prendano le giuste decisioni durante la creazione di un nuovo progetto di quel tipo. Per altre informazioni, vedere [procedure guidate](../../extensibility/internals/wizards.md).  
  
## <a name="custom-tools"></a>Strumenti personalizzati  
 Gli strumenti personalizzati consentono di associare uno strumento a un elemento in un progetto ed eseguire tale strumento ogni volta che viene salvato il file. Per altre informazioni, vedere [strumenti personalizzati](../../extensibility/internals/custom-tools.md).  
  
## <a name="vssdk-utilities"></a>Utilità VSSDK  
 VSSDK include un set di utilità che potrebbe essere necessario per lavorare con diversi aspetti dei pacchetti VSPackage. Per altre informazioni, vedere [utilità VSSDK](../../extensibility/internals/vssdk-utilities.md).  
  
## <a name="using-windows-installer"></a>Utilizzo di Windows Installer  
 In alcuni casi potrebbe essere necessario usare il programma di installazione di Windows anziché il programma di installazione VSIX: ad esempio, potrebbe essere necessario scrivere nel Registro di sistema. Per informazioni sull'uso di Windows Installer con le estensioni, vedere [installazione di pacchetti VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md).  
  
## <a name="help-viewer"></a>Help Viewer  
 È possibile integrare il proprio Guida e le pagine F1 in Help Viewer. Per altre informazioni, vedere [Microsoft Help Viewer SDK](../../extensibility/internals/microsoft-help-viewer-sdk.md).

