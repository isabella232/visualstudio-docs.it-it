---
title: Costanti dell'IDE | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 337d5dd0e8a167bd4e49f084d819eb4c1145c6a9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837472"
---
# <a name="ide-constants"></a>Costanti dell'IDE

Il <xref:Microsoft.VisualStudio.VSConstants> classe fornisce le costanti che sono specifiche per l'ambiente di sviluppo integrato (IDE) e che in precedenza sono stati definiti solo nei file di intestazione.

## <a name="logical-and-physical-views"></a>Visualizzazioni logiche e fisiche

|Value|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` i gestori devono passare il valore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per ottenere il **aperta con** finestra di dialogo, in questo caso le visualizzazioni di codice possibili.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` i gestori di passano questo valore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per ottenere il **Apri con** finestra di dialogo, in questo caso popolata con eventuali <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> visualizzazioni che eseguono il mapping alla stessa visualizzazione di debug <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` i gestori di passano questo valore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per ottenere il **Apri con** finestra di dialogo, in questo caso per **Visualizza modulo** le visualizzazioni di progettazione.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` i gestori di passano questo valore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per ottenere il **Apri con** finestra di dialogo, in questo caso la visualizzazione predefinita/primaria della factory dell'editor.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` gestori di passano questo valore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per ottenere il **Apri con** finestra di dialogo, in questo caso una visualizzazione dell'editor di testo dati o dei documenti.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` i gestori di passano questo valore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo che richiede all'utente di scegliere la visualizzazione definita dall'utente da usare.|

## <a name="editor-factory-flags"></a>Flag di Factory dell'editor

|Valore|Descrizione|
|-----------|-----------------|
|[CEF.CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Flag obsoleto combinato bit per bit come primo parametro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> (metodo).|
|[FORMATO CEF. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Combinazione bit per bit come primo parametro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, metodo, ciò indica la factory dell'editor deve eseguire le correzioni necessarie.|
|[FORMATO CEF. OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Combinazione bit per bit come primo parametro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> , questo flag è reciprocamente esclusiva del [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF.Silent](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Combinazione bit per bit come primo parametro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> (metodo), ciò indica la factory dell'editor deve creare l'editor senza visualizzare un'interfaccia utente (UI).|

## <a name="visual-studio-errors"></a>Errori di Visual Studio

|Value|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Costante restituita dalle interfacce al comportamento asincrono quando l'oggetto in questione in già in uso|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Un errore HRESULT specifico di Visual Studio per "dati del documento incompatibili".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Un errore HRESULT specifico di Visual Studio e che indica "Package non caricato."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Un errore HRESULT specifico di Visual Studio e che indica che la "Progetto esiste già".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Un errore HRESULT specifico di Visual Studio e che indica "errore di configurazione del progetto".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Un errore HRESULT specifico di Visual Studio e che indica "Progetto non caricato."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Indica un errore HRESULT specifico di Visual Studio e che "Soluzione già aperta."|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Indica un errore HRESULT specifico di Visual Studio e che "Soluzione non aperto".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Restituito dalle interfacce di compilazione che dispongono di parametri per specificare una matrice dal <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interfaccia, ma l'implementazione può solo applicare il metodo a tutti gli output.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Il <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metodo restituisce questo valore se il documento ha un formato che non può essere aperto nell'editor.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Valore HRESULT che indica che l'utente preme il pulsante Indietro in una procedura guidata di Visual Studio.|

## <a name="visual-studio-constants"></a>Costanti di Visual Studio

|Valore|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Un errore HRESULT specifico di Visual Studio e che indica "Progetto inoltrato".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Una costante specifica di Visual Studio per un "marcatore della casella degli strumenti".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Una costante specifica di Visual Studio per la trasmissione di messaggi di notifica tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodo che indica l'inizio della modalità.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Una costante specifica di Visual Studio per la trasmissione di messaggi di notifica tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodo che indica la fine della modalità.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Una costante specifica di Visual Studio per la trasmissione di messaggi di notifica tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodo per indicare che le metriche della barra dei comandi sono stati modificati.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Costante specifica di Visual Studio che indica che un cookie non è stato impostato.|
|[VSITEMID.Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Un identificatore di elemento di Visual Studio che rappresenta l'assenza di un elemento del progetto. Questo valore viene utilizzato quando è presente alcuna selezione corrente.|
|[VSITEMID.Root](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Un identificatore di elemento di Visual Studio che rappresenta la radice di una gerarchia del progetto e viene usato per identificare l'intera gerarchia anziché un singolo elemento.|
|[VSITEMID.Selection](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Un identificatore di elemento di Visual Studio che rappresenta l'elemento correntemente selezionato o elementi che possono includere la radice della gerarchia.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Viene descritto il componente dell'IDE appena selezionato, in un <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> chiamare, ad esempio.

|Costante|Valore|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Costanti usate per indicare un nuovo stato di selezione.

|Costante|Value|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Costanti di finestra di dialogo del selettore componenti

|Costante|Valore|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER + 1280|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER + 1281|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER + 1290|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER + 1287|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER + 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER + 1288|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER + 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER + 1289|

## <a name="see-also"></a>Vedere anche

- [Comandi definiti dall'IDE per l'estensione di sistemi di progetto](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)