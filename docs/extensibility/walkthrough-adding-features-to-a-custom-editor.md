---
title: 'Procedura dettagliata: aggiunta di funzionalità a un editor personalizzato Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65ef0edf76780ba7c8b6f5d9347195c286bec466
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649841"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Procedura dettagliata: Aggiungere funzionalità a un editor personalizzatoWalkthrough: Add features to a custom editor
Dopo aver creato un editor personalizzato, è possibile aggiungervi altre funzionalità.

## <a name="to-create-an-editor-for-a-vspackage"></a>Per creare un editor per un pacchetto VSPackageTo create an editor for a VSPackage

1. Creare un editor personalizzato usando il modello di progetto di pacchetto di Visual Studio.Create a custom editor by using the Visual Studio Package project template.

     Per ulteriori informazioni, vedere [Procedura dettagliata: creare un editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Decidere se si desidera che l'editor supporti una singola visualizzazione o più visualizzazioni.

     Un editor che supporta il comando **Nuova finestra** o che dispone della visualizzazione Maschera e della visualizzazione codice richiede oggetti dati documento e oggetti visualizzazione documento separati. In un editor che supporta solo una singola visualizzazione, l'oggetto dati del documento e l'oggetto visualizzazione documento possono essere implementati sullo stesso oggetto.

     Per un esempio di più visualizzazioni, consultate [Supporto di più visualizzazioni documento.](../extensibility/supporting-multiple-document-views.md)

3. Implementare una factory dell'editor impostando l'interfaccia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>

     Per ulteriori informazioni, consultate [Editor factory .](/visualstudio/extensibility/editor-factories?view=vs-2015)

4. Decidere se si desidera che l'editor utilizzi l'attivazione sul posto o l'incorporamento semplificato per gestire la finestra dell'oggetto visualizzazione del documento.

     Una finestra dell'editor di incorporamento semplificata ospita una visualizzazione di documento standard, mentre una finestra dell'editor di attivazione sul posto ospita un controllo ActiveX o un altro oggetto attivo come visualizzazione del documento. Per ulteriori informazioni, consultate [Incorporamento semplificato](../extensibility/simplified-embedding.md) e [Attivazione sul posto](/visualstudio/misc/in-place-activation?view=vs-2015).

5. Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia per gestire i comandi.

6. Fornire la persistenza del documento e la risposta alle modifiche dei file esterni:Provide document persistence and response to external file changes:

    1. Per rendere persistente <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> il file, implementare e nell'oggetto dati del documento dell'editor.

    2. Per rispondere alle modifiche <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> apportate ai file esterni, implementare e <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> nell'oggetto dati del documento dell'editor.

        > [!NOTE]
        > Chiamare `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> per ottenere un `IVsFileChangeEx`puntatore a .

7. Coordinare gli eventi di modifica del documento con il controllo del codice sorgente. A tale scopo, seguire questa procedura:

    1. Ottenere un `IVsQueryEditQuerySave2` puntatore `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>a chiamando su .

    2. Quando si verifica il primo <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> evento di modifica, chiamare il metodo .

         Questo metodo richiede all'utente di estrarre il file se non è già estratto. Assicurarsi di gestire una condizione di "file non estratto" per evitare errori.

    3. Analogamente, prima di salvare <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> il file, chiamare il metodo .

         Questo metodo richiede all'utente di salvare il file se non è stato salvato o se è stato modificato dopo l'ultimo salvataggio.

8. Attivare la finestra **Proprietà** per visualizzare le proprietà per il testo selezionato nell'editor. A tale scopo, seguire questa procedura:

    1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> ogni volta che la selezione <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>del testo cambia, passando l'implementazione di .

    2. Chiamata `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> al servizio per <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>ottenere un puntatore a .

9. Consentire agli utenti di trascinare gli elementi tra l'editor e la **casella degli strumenti**o tra editor esterni (ad esempio Microsoft Word) e la casella degli **strumenti**. A tale scopo, seguire questa procedura:

    1. Implementare `IDropTarget` nell'editor per avvisare l'IDE che l'editor è una destinazione di rilascio.

    2. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> l'interfaccia nella visualizzazione in modo che l'editor possa abilitare e disabilitare gli elementi nella **Casella degli strumenti**.

    3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> Implementare `QueryService` e <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> chiamare sul servizio <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> per <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> ottenere un puntatore alle interfacce e .

         Questi passaggi consentono al pacchetto VSPackage di aggiungere nuovi elementi alla **casella degli strumenti**.

10. Decidere se si desidera altre funzionalità facoltative per l'editor.

    - Se si desidera che l'editor supporti i comandi di ricerca e sostituzione, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.

    - Se si desidera utilizzare una finestra degli strumenti `IVsDocOutlineProvider`struttura documento nell'editor, implementare .

    - Se si desidera utilizzare una barra di <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> stato `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> nell'editor, `IVsStatusBar`implementare e chiamare per ottenere un puntatore a .

         Ad esempio, un editor può visualizzare informazioni su riga/colonna, modalità di selezione (flusso / casella) e modalità di inserimento (inserimento / overstrike).

    - Se si desidera che `Undo` l'editor supporti il comando, il metodo consigliato consiste nell'utilizzare il modello di gestione degli annullamenti OLE. In alternativa, è possibile fare `Undo` in modo che l'editor gestisca direttamente il comando.

11. Creare informazioni del Registro di sistema, inclusi i GUID per il pacchetto VSPackage, i menu, l'editor e altre funzionalità.

     Di seguito è riportato un esempio generico di codice che è necessario inserire nello script del file *RGS* per dimostrare come registrare correttamente un editor.

    ```csharp
    NoRemove Editors
    {
          ForceRemove {...guidEditor...} = s 'RTF Editor'
          {
             val Package = s '{...guidVsPackage...}'
             ForceRemove Extensions
             {
                val rtf = d 50
             }
          }
    }
    NoRemove Menus
    {
          val {...guidVsPackage...} = s ',203,11'
    }
    ```

12. Implementare il supporto della Guida sensibile al contesto.

     Questo passaggio consente di fornire il supporto della finestra Guida F1 e Guida dinamica per gli elementi nell'editor. Per ulteriori informazioni, vedere [Procedura: fornire il contesto per gli editor.](/visualstudio/extensibility/how-to-provide-context-for-editors?view=vs-2015)

13. Esporre un modello a oggetti di `IDispatch` automazione dall'editor implementando l'interfaccia.

     Per altre informazioni, vedere [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Programmazione efficiente

- L'istanza dell'editor viene creata <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> quando l'IDE chiama il metodo. Se l'editor supporta `CreateEditorInstance` più visualizzazioni, crea sia i dati del documento che gli oggetti visualizzazione del documento. Se l'oggetto dati del documento è `punkDocDataExisting` già aperto, viene passato un valore non null a `IVsEditorFactory::CreateEditorInstance`. L'implementazione factory dell'editor deve determinare se un oggetto dati documento esistente è compatibile eseguendo una query per le interfacce appropriate su di esso. Per ulteriori informazioni, vedere [Supporto di più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).

- Se si utilizza l'approccio di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> incorporamento semplificato, implementare l'interfaccia.

- Se si decide di utilizzare l'attivazione sul posto, implementare le interfacce seguenti:If you decide to use in-place activation, implement the following interfaces:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > L'interfaccia `IOleInPlaceComponent` viene utilizzata per evitare l'unione di menu OLE 2.

   L'implementazione `IOleCommandTarget` gestisce comandi quali **Taglia**, **Copia**e **Incolla**. Durante `IOleCommandTarget`l'implementazione di , decidere se l'editor richiede un proprio file *vsct* [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]per definire la propria struttura di menu dei comandi o se è possibile implementare comandi standard definiti da . In genere, gli editor utilizzano ed estendono i menu dell'IDE e definiscono le proprie barre degli strumenti. Tuttavia, è spesso necessario per un editor per definire i propri comandi specifici oltre a utilizzare il set di comandi standard dell'IDE. L'editor deve dichiarare i comandi standard che utilizza e quindi definire eventuali nuovi comandi, menu di scelta rapida, menu di primo livello e barre degli strumenti in un file *vsct.* Se si crea un editor di <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> attivazione sul posto, implementare e definire i menu e le barre degli strumenti per l'editor in un file *vsct* anziché utilizzare l'unione di menu OLE 2.

- Per evitare l'affollamento dei comandi di menu nell'interfaccia utente, è necessario usare i comandi esistenti nell'IDE prima di inventare nuovi comandi. I comandi condivisi sono definiti in *SharedCmdDef.vsct* e *ShellCmdDef.vsct*. Per impostazione predefinita, questi file vengono installati nella sottodirectory [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VisualStudioIntegration, Inc, dell'installazione.

- `ISelectionContainer`possibile esprimere sia selezioni singole che multiple. Ogni oggetto selezionato viene `IDispatch` implementato come oggetto.

- L'IDE `IOleUndoManager` implementa come un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> servizio accessibile da un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>oggetto o come oggetto di cui è possibile creare un'istanza tramite . L'editor `IOleUndoUnit` implementa l'interfaccia per ogni `Undo` azione.

- Esistono due posizioni in cui un editor personalizzato può esporre oggetti di automazione:There are two places a custom editor can expose automation objects:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Vedere anche

- [Contribuire al modello di automazione](../extensibility/internals/contributing-to-the-automation-model.md)
