---
title: Costanti IDE Documenti Microsoft
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2eddac1cc7d7e616deb197752adf41a4d68d15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710508"
---
# <a name="ide-constants"></a>Costanti IDE

La <xref:Microsoft.VisualStudio.VSConstants> classe fornisce costanti specifiche per l'ambiente di sviluppo integrato (IDE) e che in precedenza erano definite solo nei file di intestazione.

## <a name="logical-and-physical-views"></a>Viste logiche e fisiche

|valore|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` gestori devono passare questo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> valore al metodo per ottenere il **Apri con** la finestra di dialogo, in questo caso sulle possibili visualizzazioni del codice.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` i gestori passano <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> questo valore al metodo per ottenere la <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> finestra di dialogo Apri <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> **con,** in questo caso popolata da possibili visualizzazioni di debug che eseguono il mapping alla stessa visualizzazione di .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` gestori passano questo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> valore al metodo per ottenere il **Apri con** la finestra di dialogo, in questo caso per visualizzare le visualizzazioni della finestra di progettazione **del modulo.**|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` i gestori passano <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> questo valore al metodo per ottenere la finestra di dialogo **Apri con,** in questo caso la visualizzazione predefinita/primaria della factory dell'editor.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` gestori passano questo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> valore al metodo per ottenere il **Apri con** la finestra di dialogo, in questo per un documento o visualizzazione dell'editor di testo di dati.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>`cmdidOpenWith` i gestori passano <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> questo valore al metodo che richiede all'utente di scegliere quale visualizzazione definita dall'utente utilizzare.|

## <a name="editor-factory-flags"></a>Flag di fabbrica dell'editorEditor Factory Flags

|valore|Descrizione|
|-----------|-----------------|
|[Cef. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Flag obsoleto combinato bit per bit <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> come primo parametro del metodo.|
|[Cef. OpenAsNuovo](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Combinato bit per bit come <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>primo parametro del metodo , ciò indica che la factory dell'editor deve eseguire le correzioni necessarie.|
|[Cef. Openfile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Combinato bit per bit come <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> primo parametro del metodo, questo flag si escludono a vicenda di [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[Cef. Silenzioso](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Combinato bit per bit come <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> primo parametro del metodo, ciò indica che la factory dell'editor deve creare l'editor senza visualizzare un'interfaccia utente (UI).|

## <a name="visual-studio-errors"></a>Errori di Visual Studio

|valore|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Costante restituita dalle interfacce al comportamento asincrono quando l'oggetto in questione è già occupato|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Un HRESULT di errore specifico di Visual Studio per "Dati documento incompatibili".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Un HRESULT di errore specifico di Visual Studio e che indica "Pacchetto non caricato".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Un HRESULT di errore specifico di Visual Studio e che indica che il "progetto esiste già".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Un HRESULT di errore specifico di Visual Studio e che indica "Configurazione del progetto non riuscita".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Un HRESULT di errore specifico di Visual Studio e che indica "Progetto non caricato".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Un HRESULT di errore specifico di Visual Studio e che indica "Soluzione già aperta".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Un HRESULT di errore specifico di Visual Studio e che indica "Soluzione non aperta".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Restituito dalle interfacce di compilazione che dispongono <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> di parametri per specificare una matrice dall'interfaccia, ma l'implementazione può applicare il metodo solo a tutti gli output.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Il <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metodo restituisce questo valore se il documento ha un formato che non può essere aperto nell'editor.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Valore HRESULT che indica che l'utente ha premuto il pulsante Indietro in una procedura guidata di Visual Studio.|

## <a name="visual-studio-constants"></a>Costanti di Visual Studio

|valore|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Un HRESULT di errore specifico di Visual Studio e che indica "Progetto inoltrato".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Costante specifica di Visual Studio per un "marcatore della casella degli strumenti".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Costante specifica di Visual Studio per la trasmissione <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> di un messaggio di notifica tramite il metodo che indica l'inizio della modalità.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Costante specifica di Visual Studio per la trasmissione <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> di un messaggio di notifica tramite il metodo che indica la fine della modalità.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Costante specifica di Visual Studio per la trasmissione <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> di un messaggio di notifica tramite il metodo che indica che le metriche della barra dei comandi sono state modificate.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Costante specifica di Visual Studio che indica che non è stato impostato un cookie.|
|[Vsitemid. Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identificatore di elemento di Visual Studio che rappresenta l'assenza di un elemento di progetto. Questo valore viene utilizzato quando non è presente alcuna selezione corrente.|
|[Vsitemid. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identificatore di elemento di Visual Studio che rappresenta la radice di una gerarchia di progetto e viene utilizzato per identificare l'intera gerarchia, anziché un singolo elemento.|
|[Vsitemid. Selezione](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identificatore di elemento di Visual Studio che rappresenta l'elemento o gli elementi attualmente selezionati, che possono includere la radice della gerarchia.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Viene descritto quale componente dell'IDE è <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> stato appena selezionato, ad esempio in una chiamata.

|Costante|valore|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject (progetto di selezione)](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager (informazioni in base alla proprietà SelectionElement.UndoManager)](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5 (in modo 0x5)|
|[SelectionElement.WindowFrame (Fotogramma selezione)](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Costanti utilizzate per indicare un nuovo stato di selezione.

|Costante|valore|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Costanti della finestra di dialogo Selettore componenti

|Costante|valore|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM_USER 1280 USD|
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM_USER 1281 USD|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM_USER 1290 USD|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM_USER 1287 USD|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM_USER 1285 USD 1285|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM_USER 1288 EURO|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM_USER 1286 USD 1286|
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM_USER 1289 EURO|

## <a name="see-also"></a>Vedere anche

- [Comandi definiti dall'IDE per l'estensione dei sistemi di progetto](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
