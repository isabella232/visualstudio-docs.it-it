---
title: 'Procedura dettagliata: Aggiunta di funzionalità a un editor personalizzato | Microsoft Docs'
description: Informazioni su come aggiungere altre funzionalità a un editor personalizzato dopo aver creato l'editor usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 155906d5dfa35a66cd85053cac3c66c2a11a9b45ea94c7fc4f850e8656d5bf4c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121335017"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Procedura dettagliata: Aggiungere funzionalità a un editor personalizzato
Dopo aver creato un editor personalizzato, è possibile aggiungervi altre funzionalità.

## <a name="to-create-an-editor-for-a-vspackage"></a>Per creare un editor per un vspackage

1. Creare un editor personalizzato usando il modello di Visual Studio pacchetto.

     Per altre informazioni, vedere [Procedura dettagliata: Creare un editor personalizzato.](../extensibility/walkthrough-creating-a-custom-editor.md)

2. Decidere se l'editor deve supportare una singola visualizzazione o più visualizzazioni.

     Un editor che supporta il comando **Nuova** finestra o dispone di visualizzazione form e visualizzazione codice richiede oggetti dati di documento e oggetti visualizzazione documento separati. In un editor che supporta una sola visualizzazione, l'oggetto dati del documento e l'oggetto visualizzazione documento possono essere implementati nello stesso oggetto.

     Per un esempio di più visualizzazioni, vedere [Supportare più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).

3. Implementare una factory dell'editor configurando <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> l'interfaccia .

     Per altre informazioni, vedere [Factory dell'editor.](/previous-versions/visualstudio/visual-studio-2015/extensibility/editor-factories?preserve-view=true&view=vs-2015)

4. Decidere se l'editor deve usare l'attivazione sul posto o l'incorporamento semplificato per gestire la finestra dell'oggetto visualizzazione documento.

     Una finestra dell'editor di incorporamento semplificata ospita una visualizzazione documento standard, mentre una finestra dell'editor di attivazione sul posto ospita un controllo ActiveX o un altro oggetto attivo come visualizzazione documento. Per altre informazioni, vedere [Incorporamento semplificato](../extensibility/simplified-embedding.md) e [Attivazione sul posto.](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015)

5. Implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia per gestire i comandi.

6. Fornire la persistenza del documento e la risposta alle modifiche ai file esterni:

    1. Per rendere persistente il file, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> implementare e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> nell'oggetto dati documento dell'editor.

    2. Per rispondere alle modifiche ai file esterni, <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> implementare e <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> nell'oggetto dati del documento dell'editor.

        > [!NOTE]
        > Chiamare `QueryService` su per ottenere un <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> puntatore a `IVsFileChangeEx` .

7. Coordinare gli eventi di modifica dei documenti con il controllo del codice sorgente. Seguire questa procedura:

    1. Ottenere un puntatore `IVsQueryEditQuerySave2` a chiamando `QueryService` su <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .

    2. Quando si verifica il primo evento di modifica, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metodo .

         Questo metodo richiede all'utente di estrarre il file se non è già stato estratto. Assicurarsi di gestire una condizione "file non estratto" per evitare errori.

    3. Analogamente, prima di salvare il file, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> metodo .

         Questo metodo richiede all'utente di salvare il file se non è stato salvato o se è stato modificato dopo l'ultimo salvataggio.

8. Abilitare la **finestra Proprietà** per visualizzare le proprietà del testo selezionato nell'editor. Seguire questa procedura:

    1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> ogni volta che la selezione del testo cambia, passando l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .

    2. Chiamare `QueryService` sul servizio per ottenere un <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

9. Consente agli utenti di trascinare e rilasciare elementi tra l'editor e la casella degli strumenti **o** tra editor esterni (ad esempio Microsoft Word) e casella degli **strumenti**. Seguire questa procedura:

    1. Implementare `IDropTarget` nell'editor per avvisare l'IDE che l'editor è una destinazione di rilascio.

    2. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> l'interfaccia nella visualizzazione in modo che l'editor possa abilitare e disabilitare gli elementi nella casella **degli strumenti**.

    3. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> e chiamare sul servizio per ottenere un `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> puntatore alle interfacce e <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> .

         Questi passaggi consentono al vspackage di aggiungere nuovi elementi alla casella degli **strumenti**.

10. Decidere se si vogliono altre funzionalità facoltative per l'editor.

    - Se si vuole che l'editor supporti i comandi di ricerca e sostituzione, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> .

    - Se si vuole usare una finestra degli strumenti struttura documento nell'editor, implementare `IVsDocOutlineProvider` .

    - Se si vuole usare una barra di stato nell'editor, implementare e chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> `QueryService` per ottenere un <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> puntatore a `IVsStatusBar` .

         Ad esempio, un editor può visualizzare le informazioni riga/colonna, la modalità di selezione (flusso/casella) e la modalità di inserimento (inserimento/overstrike).

    - Se si vuole che l'editor supporti `Undo` il comando, il metodo consigliato è usare il modello di gestione dell'annullamento OLE. In alternativa, è possibile fare in modo che l'editor gestirà direttamente `Undo` il comando.

11. Creare le informazioni del Registro di sistema, inclusi i GUID per vspackage, i menu, l'editor e altre funzionalità.

     Di seguito è riportato un esempio generico di codice che verrebbe inserito nello script del file con estensione *rgs* per illustrare come registrare correttamente un editor.

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

     Questo passaggio consente di fornire il supporto della finestra Guida F1 e Guida dinamica per gli elementi nell'editor. Per altre informazioni, vedere [Procedura: Fornire il contesto per gli editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/how-to-provide-context-for-editors?preserve-view=true&view=vs-2015).

13. Esporre un modello a oggetti di automazione dall'editor implementando `IDispatch` l'interfaccia .

     Per altre informazioni, vedere [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Programmazione efficiente

- L'istanza dell'editor viene creata quando l'IDE chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo . Se l'editor supporta più visualizzazioni, crea sia i `CreateEditorInstance` dati del documento che gli oggetti visualizzazione documento. Se l'oggetto dati del documento è già aperto, viene passato un valore non Null `punkDocDataExisting` a `IVsEditorFactory::CreateEditorInstance` . L'implementazione della factory dell'editor deve determinare se un oggetto dati del documento esistente è compatibile tramite una query per individuare le interfacce appropriate. Per altre informazioni, vedere [Supporto di più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).

- Se si usa l'approccio di incorporamento semplificato, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> l'interfaccia .

- Se si decide di usare l'attivazione sul posto, implementare le interfacce seguenti:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > `IOleInPlaceComponent`L'interfaccia viene usata per evitare l'unione dei menu OLE 2.

   `IOleCommandTarget`L'implementazione gestisce comandi quali **Taglia**, **Copia** e **Incolla**. Quando si implementa , decidere se l'editor richiede il proprio `IOleCommandTarget` file *vsct* per definire la propria struttura del menu di comando o se può implementare i comandi standard definiti da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . In genere, gli editor usano ed estendono i menu dell'IDE e definiscono le proprie barre degli strumenti. Tuttavia, è spesso necessario per un editor definire i propri comandi specifici, oltre a usare il set di comandi standard dell'IDE. L'editor deve dichiarare i comandi standard che usa e quindi definire nuovi comandi, menu di scelta rapida, menu di primo livello e barre degli strumenti in un file con estensione *vsct.* Se si crea un editor di attivazione sul posto, implementare e definire i menu e le barre degli strumenti per l'editor in un file vsct anziché usare l'unione dei <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> menu OLE  2.

- Per evitare l'affollamento dei comandi di menu nell'interfaccia utente, è necessario usare i comandi esistenti nell'IDE prima di inventare nuovi comandi. I comandi condivisi sono definiti in *SharedCmdDef.vsct* e *ShellCmdDef.vsct.* Questi file vengono installati per impostazione predefinita nella sottodirectory VisualStudioIntegration\Common\Inc [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] dell'installazione.

- `ISelectionContainer` può esprimere sia selezioni singole che multiple. Ogni oggetto selezionato viene implementato come `IDispatch` oggetto .

- L'IDE implementa come servizio accessibile da o come oggetto di cui è possibile creare `IOleUndoManager` <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> un'istanza tramite <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> . L'editor implementa `IOleUndoUnit` l'interfaccia per ogni `Undo` azione.

- Un editor personalizzato può esporre oggetti di automazione in due posizioni:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Vedi anche

- [Contribuire al modello di automazione](../extensibility/internals/contributing-to-the-automation-model.md)