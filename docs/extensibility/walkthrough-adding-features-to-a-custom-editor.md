---
title: 'Procedura dettagliata: aggiunta di funzionalità a un editor personalizzato | Microsoft Docs'
description: Per informazioni su come aggiungere altre funzionalità a un editor personalizzato dopo aver creato l'editor, usare questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c08af63eaf68701f1a6703ac41fec20368d78931
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863205"
---
# <a name="walkthrough-add-features-to-a-custom-editor"></a>Procedura dettagliata: aggiungere funzionalità a un editor personalizzato
Dopo aver creato un editor personalizzato, è possibile aggiungervi altre funzionalità.

## <a name="to-create-an-editor-for-a-vspackage"></a>Per creare un editor per un pacchetto VSPackage

1. Creare un editor personalizzato usando il modello di progetto di pacchetto di Visual Studio.

     Per ulteriori informazioni, vedere [procedura dettagliata: creare un editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md).

2. Decidere se si desidera che l'editor supporti una sola visualizzazione o più visualizzazioni.

     Un editor che supporta il comando **nuova finestra** o con visualizzazione form e visualizzazione codice richiede oggetti dati del documento e oggetti visualizzazione del documento distinti. In un editor che supporta solo una singola visualizzazione, l'oggetto dati del documento e l'oggetto visualizzazione del documento possono essere implementati nello stesso oggetto.

     Per un esempio di visualizzazioni multiple, vedere [supportare più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).

3. Implementare una factory dell'editor impostando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia.

     Per altre informazioni, vedere [Editor Factory](/previous-versions/visualstudio/visual-studio-2015/extensibility/editor-factories?preserve-view=true&view=vs-2015).

4. Decidere se si vuole che l'editor usi l'attivazione sul posto o l'incorporamento semplificato per gestire la finestra oggetto visualizzazione documento.

     Una finestra Editor di incorporamento semplificata ospita una visualizzazione del documento standard, mentre una finestra dell'editor di attivazione sul posto ospita un controllo ActiveX o un altro oggetto attivo come visualizzazione del documento. Per altre informazioni, vedere [incorporamento semplificato](../extensibility/simplified-embedding.md) e [attivazione sul posto](/previous-versions/visualstudio/visual-studio-2015/misc/in-place-activation?preserve-view=true&view=vs-2015).

5. Implementare l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia per gestire i comandi.

6. Fornire la persistenza del documento e la risposta alle modifiche al file esterno:

    1. Per rendere permanente il file, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> nell'oggetto dati del documento dell'editor.

    2. Per rispondere alle modifiche apportate ai file esterni, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> nell'oggetto dati del documento dell'editor.

        > [!NOTE]
        > Chiamare `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> per ottenere un puntatore a `IVsFileChangeEx` .

7. Coordina gli eventi di modifica del documento con il controllo del codice sorgente. Seguire questa procedura:

    1. Ottenere un puntatore a chiamando `IVsQueryEditQuerySave2` `QueryService` il <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> .

    2. Quando si verifica il primo evento di modifica, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> metodo.

         Questo metodo richiede all'utente di estrarre il file se non è già estratto. Assicurarsi di gestire una condizione di "file non estratto" per evitare gli errori.

    3. Analogamente, prima di salvare il file, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> metodo.

         Questo metodo richiede all'utente di salvare il file se non è stato salvato o se è stato modificato dopo l'ultimo salvataggio.

8. Abilitare la finestra **Proprietà** per visualizzare le proprietà per il testo selezionato nell'editor. Seguire questa procedura:

    1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> ogni volta che la selezione del testo viene modificata, passando l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .

    2. Chiamare `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> servizio per ottenere un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

9. Consentire agli utenti di trascinare e rilasciare elementi tra l'editor e la **casella degli strumenti** oppure tra editor esterni (come Microsoft Word) e la **casella degli strumenti**. Seguire questa procedura:

    1. Implementare nell' `IDropTarget` Editor per avvisare l'IDE che l'editor è un obiettivo di rilascio.

    2. Implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interfaccia nella visualizzazione in modo che l'editor possa abilitare e disabilitare gli elementi nella **casella degli strumenti**.

    3. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> e chiamare `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> servizio per ottenere un puntatore alle <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> interfacce e <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> .

         Questi passaggi consentono al pacchetto VSPackage di aggiungere nuovi elementi alla **casella degli strumenti**.

10. Decidere se si desiderano altre funzionalità facoltative per l'editor.

    - Se si desidera che l'editor supporti i comandi Trova e Sostituisci, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget> .

    - Se si desidera utilizzare una finestra degli strumenti struttura documento nell'editor, implementare `IVsDocOutlineProvider` .

    - Se si vuole usare una barra di stato nell'editor, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> e chiamare `QueryService` per <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> per ottenere un puntatore a `IVsStatusBar` .

         Un editor può, ad esempio, visualizzare le informazioni su righe/colonne, la modalità di selezione (flusso/casella) e la modalità di inserimento (inserimento/overstrike).

    - Se si vuole che l'editor supporti il `Undo` comando, il metodo consigliato consiste nell'usare il modello di gestione degli annullamenti OLE. In alternativa, è possibile fare in modo che l'editor gestisca `Undo` direttamente il comando.

11. Creare informazioni del registro di sistema, inclusi i GUID per il pacchetto VSPackage, i menu, l'editor e altre funzionalità.

     Di seguito è riportato un esempio generico di codice che si inserisce nello script del file con *estensione rgs* per dimostrare come registrare correttamente un editor.

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

     Questo passaggio consente di fornire la Guida sensibile al contesto e il supporto della finestra della Guida dinamica per gli elementi dell'editor. Per altre informazioni, vedere [procedura: fornire il contesto per gli editor](/previous-versions/visualstudio/visual-studio-2015/extensibility/how-to-provide-context-for-editors?preserve-view=true&view=vs-2015).

13. Esporre un modello a oggetti di automazione dall'editor implementando l' `IDispatch` interfaccia.

     Per altre informazioni, vedere [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).

## <a name="robust-programming"></a>Programmazione efficiente

- L'istanza dell'editor viene creata quando l'IDE chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metodo. Se l'editor supporta più visualizzazioni, in `CreateEditorInstance` vengono creati sia i dati del documento sia gli oggetti visualizzazione del documento. Se l'oggetto dati del documento è già aperto, `punkDocDataExisting` viene passato un valore non null a `IVsEditorFactory::CreateEditorInstance` . L'implementazione della factory dell'editor deve determinare se un oggetto dati del documento esistente è compatibile eseguendo una query per le interfacce appropriate. Per altre informazioni, vedere [supporto di più visualizzazioni documento](../extensibility/supporting-multiple-document-views.md).

- Se si usa l'approccio di incorporamento semplificato, implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia.

- Se si decide di utilizzare l'attivazione sul posto, implementare le interfacce seguenti:

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>

   <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>

   <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>

  > [!NOTE]
  > L' `IOleInPlaceComponent` interfaccia viene utilizzata per evitare l'Unione di menu OLE 2.

   L' `IOleCommandTarget` implementazione gestisce i comandi, ad esempio **taglia**, **copia** e **Incolla**. Quando `IOleCommandTarget` si implementa, decidere se l'Editor richiede il proprio file *. vsct* per definire la propria struttura del menu dei comandi o se può implementare comandi standard definiti da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . In genere, gli editor usano ed estendono i menu dell'IDE e definiscono le barre degli strumenti. Tuttavia, spesso è necessario che un editor definisca i propri comandi specifici, oltre a usare il set di comandi standard dell'IDE. L'editor deve dichiarare i comandi standard usati e quindi definire i nuovi comandi, i menu di scelta rapida, i menu di primo livello e le barre degli strumenti in un file con *estensione vsct* . Se si crea un editor di attivazione sul posto, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> e definire i menu e le barre degli strumenti per l'editor in un file con *estensione vsct* anziché utilizzare l'Unione dei menu OLE 2.

- Per evitare che il comando di menu venga affollato nell'interfaccia utente, è necessario usare i comandi esistenti nell'IDE prima di inventare nuovi comandi. I comandi condivisi sono definiti in *SharedCmdDef. vsct* e *ShellCmdDef. vsct*. Questi file vengono installati per impostazione predefinita nella sottodirectory VisualStudioIntegration\Common\Inc dell' [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] installazione.

- `ISelectionContainer` consente di esprimere selezioni singole e multiple. Ogni oggetto selezionato viene implementato come un `IDispatch` oggetto.

- L'IDE implementa `IOleUndoManager` come servizio accessibile da <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> o come oggetto di cui è possibile creare un'istanza tramite <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> . L'editor implementa l' `IOleUndoUnit` interfaccia per ogni `Undo` azione.

- Un editor personalizzato può esporre gli oggetti di automazione in due posizioni:

  - `Document.Object`

  - `Window.Object`

## <a name="see-also"></a>Vedi anche

- [Contribuire al modello di automazione](../extensibility/internals/contributing-to-the-automation-model.md)