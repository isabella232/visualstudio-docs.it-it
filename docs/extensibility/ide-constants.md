---
title: Costanti IDE | Microsoft Docs
description: La classe VSConstants fornisce costanti specifiche dell'IDE e precedentemente definite solo nei file di intestazione.
ms.custom: SEO-VS-2020
ms.date: 03/22/2018
ms.topic: reference
helpviewer_keywords:
- IDE, errors
- logical views
- errors [Visual Studio], IDE
- UI context constants
- constants, Visual Studio IDE
- IDE, constants
- physical views
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 802de0fd29d909320040667f972de422595bdd4f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904968"
---
# <a name="ide-constants"></a>Costanti IDE

La classe fornisce costanti specifiche dell'ambiente di sviluppo integrato (IDE) e precedentemente definite <xref:Microsoft.VisualStudio.VSConstants> solo nei file di intestazione.

## <a name="logical-and-physical-views"></a>Visualizzazioni logiche e fisiche

|Valore|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>I gestori devono passare questo valore al metodo per ottenere la finestra di dialogo Apri `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> con, in questo caso nelle possibili visualizzazioni del codice. |
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>I gestori passano questo valore al metodo per ottenere la finestra di dialogo Apri con, in questo caso popolata con le possibili visualizzazioni di debug mappate alla `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> stessa visualizzazione di  <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Debugging_guid> <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Code_guid> .|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Designer_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>I gestori passano questo valore al metodo per ottenere la finestra di dialogo Apri `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> con, in questo caso alle **visualizzazioni di Progettazione** form. |
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.Primary_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>I gestori passano questo valore al metodo per ottenere la finestra di dialogo Apri con, in questo caso la visualizzazione `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> predefinita/primaria  della factory dell'editor.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.TextView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>I gestori passano questo valore al metodo per ottenere la finestra di dialogo Apri con, in questo caso per una visualizzazione `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> dell'editor  di testo di dati o documento.|
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID.UserChooseView_guid>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97>I gestori passano questo valore al metodo che richiede all'utente di scegliere la visualizzazione `cmdidOpenWith` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> definita dall'utente da usare.|

## <a name="editor-factory-flags"></a>Flag factory dell'editor

|Valore|Descrizione|
|-----------|-----------------|
|[Cef. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>)|Flag obsoleto combinato bit per bit come primo parametro del <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metodo.|
|[Cef. OpenAsNew](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenAsNew>)|Combinato bit per bit come primo parametro del metodo , indica che la factory dell'editor deve <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> eseguire le correzioni necessarie.|
|[Cef. Openfile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_OpenFile>)|Combinato bit per bit come primo parametro del metodo, questo flag si <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> escludono a vicenda di [CEF. CloneFile](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_CloneFile>).|
|[Cef. Silenzioso](<xref:Microsoft.VisualStudio.VSConstants.CEF#Microsoft_VisualStudio_VSConstants_CEF_Silent>)|Combinato bit per bit come primo parametro del metodo , indica che la factory dell'editor deve creare l'editor senza <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> visualizzare un'interfaccia utente.|

## <a name="visual-studio-errors"></a>Visual Studio errori

|Valore|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|Costante restituita dalle interfacce al comportamento asincrono quando l'oggetto in questione è già occupato|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|HRESULT di errore specifico per l'Visual Studio per "Dati del documento incompatibili".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|HRESULT di errore specifico per Visual Studio e che indica "Pacchetto non caricato".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|HRESULT di errore specifico per Visual Studio e che indica che il progetto esiste già.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|HRESULT di errore specifico per l'Visual Studio e che indica che la configurazione del progetto non è riuscita.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|HRESULT di errore specifico per Visual Studio e che indica "Progetto non caricato".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|HRESULT di errore specifico per Visual Studio e che indica "Soluzione già aperta".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|HRESULT di errore specifico per Visual Studio e che indica "Soluzione non aperta".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|Restituito dalle interfacce di compilazione che dispongono di parametri per specificare una matrice dall'interfaccia , ma l'implementazione può applicare <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> il metodo solo a tutti gli output.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|Il <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> metodo restituisce questo valore se il documento ha un formato che non può essere aperto nell'editor.|
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|Valore HRESULT che indica che l'utente ha fatto clic sul pulsante Indietro in una Visual Studio guidata.|

## <a name="visual-studio-constants"></a>Visual Studio costanti

|Valore|Descrizione|
|-----------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|HRESULT di errore specifico per Visual Studio e che indica "Progetto inoltrato".|
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|Costante specifica per l'Visual Studio per un "marcatore della casella degli strumenti".|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|Costante specifica dell'Visual Studio per la trasmissione di un messaggio di notifica tramite il metodo che indica <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> l'inizio della modalità.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|Costante specifica dell'Visual Studio per la trasmissione di un messaggio di notifica tramite il metodo che indica la <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> fine della modalità.|
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|Costante specifica dell'Visual Studio per la trasmissione di un messaggio di notifica tramite il metodo che indica che le metriche della barra dei comandi <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> sono state modificate.|
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|Costante specifica dell'Visual Studio che indica che non è stato impostato un cookie.|
|[Vsitemid. Nil](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Nil>)|Identificatore Visual Studio elemento che rappresenta l'assenza di un elemento di progetto. Questo valore viene usato quando non è presente alcuna selezione corrente.|
|[Vsitemid. Radice](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Root>)|Identificatore Visual Studio elemento che rappresenta la radice di una gerarchia di progetto e viene usato per identificare l'intera gerarchia, anziché un singolo elemento.|
|[Vsitemid. Selezione](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID#Microsoft_VisualStudio_VSConstants_VSITEMID_Selection>)|Identificatore Visual Studio elemento che rappresenta l'elemento o gli elementi attualmente selezionati, che possono includere la radice della gerarchia.|

## <a name="ivsselectionevents"></a>IVsSelectionEvents
 Descrive il componente dell'IDE appena selezionato, ad esempio in una <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> chiamata.

|Costante|Valore|
|--------------|-----------|
|[SelectionElement.DocumentFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_DocumentFrame>)|0x2|
|[SelectionElement.PropertyBrowserSID](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_PropertyBrowserSID>)|0x4|
|[SelectionElement.StartupProject](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_StartupProject>)|0x3|
|[SelectionElement.UndoManager](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UndoManager>)|0x0|
|[SelectionElement.UserContext](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_UserContext>)|0x5|
|[SelectionElement.WindowFrame](<xref:Microsoft.VisualStudio.VSConstants.SelectionElement#Microsoft_VisualStudio_VSConstants_SelectionElement_WindowFrame>)|0x1|

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

## <a name="component-selector-dialog-constants"></a>Costanti della finestra di dialogo del selettore di componenti

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
