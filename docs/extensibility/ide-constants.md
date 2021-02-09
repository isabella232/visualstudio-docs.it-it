---
title: Costanti IDE | Microsoft Docs
description: La classe VSConstants fornisce costanti specifiche dell'IDE e definite in precedenza solo nei file di intestazione.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3a6e3c7460beb95ad410cead8bd644c37489e16
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99883233"
---
# <a name="ide-constants"></a>Costanti IDE

La <xref:Microsoft.VisualStudio.VSConstants> classe fornisce costanti specifiche per l'Integrated Development Environment (IDE) e che sono state definite in precedenza solo nei file di intestazione.

## <a name="logical-and-physical-views"></a>Viste logiche e fisiche

|Valore|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>i `cmdidOpenWith` gestori devono passare questo valore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per ottenere la finestra di dialogo **Apri con** , in questo caso sulle possibili visualizzazioni di codice.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>i `cmdidOpenWith` gestori passano questo valore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per ottenere la finestra di dialogo **Apri con** , in questo caso popolata con possibili <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> visualizzazioni di debug che corrispondono alla stessa visualizzazione di <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>i `cmdidOpenWith` gestori passano questo valore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per ottenere la finestra di dialogo **Apri con** , in questo caso per **visualizzare** le visualizzazioni di progettazione dei form.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>i `cmdidOpenWith` gestori passano questo valore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per ottenere la finestra di dialogo **Apri con** , in questo caso la visualizzazione predefinita/primaria della factory dell'editor.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>i `cmdidOpenWith` gestori passano questo valore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo per ottenere la finestra di dialogo **Apri con** , in questo oggetto per la visualizzazione di un documento o di un editor di testo dati.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>i `cmdidOpenWith` gestori passano questo valore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metodo che richiede all'utente di scegliere la visualizzazione definita dall'utente da usare.|

## <a name="editor-factory-flags"></a>Flag factory dell'editor

|Valore|Descrizione|
|-----------|-----------------|
|[CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Flag obsoleto combinato bit per bit come primo parametro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metodo.|
|[CEF. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Combinato bit per bit come primo parametro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metodo, che indica che la factory dell'editor deve eseguire le correzioni necessarie.|
|[CEF. OpenFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Combinato bit per bit come primo parametro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metodo, questo flag si escludono a vicenda da [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[CEF. Silenzioso](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Combinato bit per bit come primo parametro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metodo, che indica che la factory dell'editor deve creare l'editor senza visualizzare un'interfaccia utente (UI).|

## <a name="visual-studio-errors"></a>Errori di Visual Studio

|Valore|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Costante restituita dalle interfacce al comportamento asincrono quando l'oggetto in questione è già occupato|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|Errore HRESULT specifico di Visual Studio per "dati del documento incompatibili".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|Errore HRESULT specifico di Visual Studio che indica che il pacchetto non è stato caricato.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|Errore HRESULT specifico di Visual Studio che indica che il progetto esiste già.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|Errore HRESULT specifico di Visual Studio che indica che la configurazione del progetto non è riuscita.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|Errore HRESULT specifico di Visual Studio che indica che il progetto non è stato caricato.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|Errore HRESULT specifico di Visual Studio che indica che la soluzione è già aperta.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|Errore HRESULT specifico di Visual Studio che indica che la soluzione non è aperta.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Restituito dalle interfacce di compilazione che dispongono di parametri per specificare una matrice dall' <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> interfaccia, ma l'implementazione può applicare solo il metodo a tutti gli output.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Il <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metodo restituisce questo valore se il documento ha un formato che non può essere aperto nell'editor.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Valore HRESULT che indica che l'utente ha premuto il pulsante indietro in una procedura guidata di Visual Studio.|

## <a name="visual-studio-constants"></a>Costanti di Visual Studio

|Valore|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|Errore HRESULT specifico di Visual Studio che indica "Project inoltred".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Costante specifica di Visual Studio per un "marcatore della casella degli strumenti".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Costante specifica di Visual Studio per la trasmissione di un messaggio di notifica tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodo che indica l'inizio della modalità.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Costante specifica di Visual Studio per la trasmissione di un messaggio di notifica tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodo che indica la fine della modalità.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Costante specifica di Visual Studio per la trasmissione di un messaggio di notifica tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> metodo che indica che le metriche della barra dei comandi sono state modificate.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Costante specifica di Visual Studio che indica che un cookie non è stato impostato.|
|[VSITEMID. Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identificatore di elemento di Visual Studio che rappresenta l'assenza di un elemento di progetto. Questo valore viene utilizzato quando non è presente alcuna selezione corrente.|
|[VSITEMID. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identificatore di elemento di Visual Studio che rappresenta la radice di una gerarchia del progetto e viene usato per identificare l'intera gerarchia, anziché un singolo elemento.|
|[VSITEMID. Selezione](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identificatore di elemento di Visual Studio che rappresenta l'elemento o gli elementi attualmente selezionati, che può includere la radice della gerarchia.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Viene descritto il componente dell'IDE appena selezionato, ad esempio, in una <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> chiamata.

|Costante|Valore|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[Selectionelement. PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[Selectionelement. progetto](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[Selectionelement. UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[Selectionelement. UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[Selectionelement. WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

## <a name="vsselelemid"></a>VSSELELEMID
 Costanti utilizzate per indicare un nuovo stato di selezione.

|Costante|Valore|
|--------------|-----------|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|

## <a name="component-selector-dialog-constants"></a>Costanti finestra di dialogo Selettore componenti

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

## <a name="see-also"></a>Vedi anche

- [Comandi definiti dall'IDE per l'estensione dei sistemi di progetto](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)
