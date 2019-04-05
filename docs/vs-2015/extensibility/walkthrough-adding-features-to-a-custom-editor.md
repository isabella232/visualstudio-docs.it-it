---
title: 'Procedura dettagliata: Aggiunta di funzionalità in un Editor personalizzato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - add features
ms.assetid: bfe083b6-3e35-4b9c-ad4f-b30b9ff412a5
caps.latest.revision: 39
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e6395f279af8b48d9f74981f61cceb431a1d00a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58970304"
---
# <a name="walkthrough-adding-features-to-a-custom-editor"></a>Procedura dettagliata: Aggiunta di funzionalità in un editor personalizzato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dopo aver creato un editor personalizzato, è possibile aggiungervi altre funzionalità.  
  
### <a name="to-create-an-editor-for-a-vspackage"></a>Per creare un editor per un pacchetto VSPackage  
  
1.  Creare un editor personalizzato usando il modello di progetto di pacchetto di Visual Studio.  
  
     Per altre informazioni, vedere [Procedura dettagliata: Creazione di un Editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
2.  Decidere se l'editor per supportare una singola visualizzazione o più visualizzazioni.  
  
     Un editor che supporta il **nuova finestra** comando o dispone di visualizzazione form e visualizzazione codice, richiede gli oggetti di visualizzazione di documenti e oggetti dati documenti separati. In un editor che supporta una sola visualizzazione, l'oggetto dati del documento e l'oggetto visualizzazione del documento possono essere implementati nello stesso oggetto.  
  
     Per un esempio di visualizzazioni multiple, vedere [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
3.  Implementare una factory dell'editor mediante l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> interfaccia.  
  
     Per altre informazioni, vedere [factory dell'Editor](../extensibility/editor-factories.md).  
  
4.  Decidere se si desidera che l'editor per utilizzare l'attivazione sul posto o semplificato l'incorporamento per gestire la finestra oggetto visualizzazione del documento.  
  
     Una finestra dell'editor di incorporamento semplificato ospita una visualizzazione del documento standard, mentre una finestra dell'editor di attivazione sul posto ospita un controllo ActiveX o altro oggetto come relativa visualizzazione documento attivo. Per altre informazioni, vedere [incorporamento semplificato](../extensibility/simplified-embedding.md) e [attivazione sul posto](../misc/in-place-activation.md).  
  
5.  Implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia per gestire i comandi.  
  
6.  Fornire persistenza documento e la risposta alle modifiche di file esterno eseguendo queste operazioni:  
  
    1.  Per rendere persistenti i file, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> e <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> nell'oggetto dati documento dell'editore.  
  
    2.  Per rispondere alle modifiche di file esterno, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> nell'oggetto dati documento dell'editore.  
  
        > [!NOTE]
        >  Chiamare `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.SVsFileChangeEx> per ottenere un puntatore a `IVsFileChangeEx`.  
  
7.  Coordinare gli eventi di modifica di documenti con controllo del codice sorgente. Per eseguire questa operazione:  
  
    1.  Ottenere un puntatore a `IVsQueryEditQuerySave2` chiamando `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.  
  
    2.  Quando si verifica il primo evento di modifica, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> (metodo).  
  
         Ciò richiede all'utente di estrarre il file se non si è già estratto. Assicurarsi di gestire una condizione di "file non estratto" per evitare errori  
  
    3.  Analogamente, prima di salvare il file, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFile%2A> (metodo).  
  
         Questo metodo richiede all'utente di salvare il file se non è stato salvato o se è stata modificata dall'ultimo salvataggio.  
  
8.  Abilitare la **proprietà** finestra per visualizzare le proprietà per il testo selezionato nell'editor. Per eseguire questa operazione:  
  
    1.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> ogni volta testo selezione viene modificata, passando nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  
  
    2.  Chiamare `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> service per ottenere un puntatore a <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
9. Consentire agli utenti di trascinare gli elementi tra l'editor e il **casella degli strumenti**, o tra gli editor esterni (ad esempio Microsoft Word) e il **della casella degli strumenti**. Per eseguire questa operazione:  
  
    1.  Implementare `IDropTarget` sull'editor per indicare all'IDE che l'editor è un obiettivo di rilascio.  
  
    2.  Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolboxUser> interfaccia per la vista in modo da abilitare e disabilitare gli elementi in un editor del **casella degli strumenti**.  
  
    3.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.ResetDefaults%2A> e chiamare `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.SVsToolbox> service per ottenere un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox2> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsToolbox3> interfacce.  
  
         In questo modo il pacchetto VSPackage aggiungere nuovi elementi per il **casella degli strumenti**.  
  
10. Decidere se tutte le altre caratteristiche facoltative per l'editor.  
  
    -   Se si desidera che l'editor per supportare trovare e sostituire i comandi, implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>.  
  
    -   Se si desidera utilizzare una finestra degli strumenti Struttura documento nell'editor, implementare `IVsDocOutlineProvider`.  
  
    -   Se si desidera usare una barra di stato nell'editor, implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> e chiamare `QueryService` per <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> per ottenere un puntatore a `IVsStatusBar`.  
  
         Ad esempio, un editor può visualizzare riga / informazioni di colonna, la modalità di selezione (trasmettere / finestra) e modalità di inserimento (inserimento /overstrike).  
  
    -   Se si desidera che l'editor per supportare il `Undo` comando, il metodo consigliato consiste nell'usare il modello di gestione di annullamento OLE. In alternativa, è possibile avere l'handle di editor la `Undo` comando direttamente.  
  
11. Creazione del Registro di sistema informazioni, inclusi i GUID per il pacchetto VSPackage i menu, l'editor e altre funzionalità.  
  
     Di seguito è riportato un esempio di codice che dovrà inserire nello script di file con estensione RGS per illustrare come registrare correttamente un editor generico.  
  
    ```  
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
  
     In questo modo è possibile fornire supporto della Guida F1 e finestra Guida dinamica per gli elementi nell'editor. Per altre informazioni, vedere [come: Fornire il contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md).  
  
13. Esporre un modello a oggetti da un editor di automazione tramite l'implementazione di `IDispatch` interfaccia.  
  
     Per altre informazioni, vedere [Contributing to the Automation Model](../extensibility/internals/contributing-to-the-automation-model.md).  
  
## <a name="robust-programming"></a>Programmazione efficiente  
  
-   L'istanza dell'editor viene creato quando si chiama l'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> (metodo). Se l'editor supporta più visualizzazioni, `CreateEditorInstance` crea i dati del documento e gli oggetti di visualizzazione documento. Se l'oggetto dati del documento è già aperto, non null `punkDocDataExisting` valore viene passato a `IVsEditorFactory::CreateEditorInstance`. Implementazione della factory dell'editor deve determinare se un oggetto dati del documento esistente è compatibile eseguendo una query per le interfacce appropriate su di esso. Per altre informazioni, vedere [Supporting Multiple Document Views](../extensibility/supporting-multiple-document-views.md).  
  
-   Se si usa l'approccio di incorporamento semplificato, implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia.  
  
-   Se si decide di utilizzare l'attivazione sul posto, implementare le interfacce seguenti:  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleObject>  
  
     <xref:Microsoft.VisualStudio.OLE.Interop.IOleInPlaceActiveObject>  
  
     <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent>  
  
    > [!NOTE]
    >  Il `IOleInPlaceComponent` interfaccia viene utilizzata per evitare l'unione di menu OLE 2.  
  
     I `IOleCommandTarget` implementazione gestisce i comandi, ad esempio **tagliare**, **copia**, e **Incolla**. Quando si implementa `IOleCommandTarget`, decidere se l'editor richiede un proprio file vsct per definire la propria struttura di menu comando o se è possibile implementare comandi standard definiti dalle [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. In genere, gli editor di usano ed estendono i menu dell'IDE e definiscono le proprie le barre degli strumenti. Tuttavia, spesso è necessario per un editor definire i proprio comandi specifici oltre all'utilizzo di set di comandi standard dell'IDE. A tale scopo, l'editor deve dichiarare i comandi standard USA e quindi definire qualsiasi nuovi comandi, menu di scelta rapida, i menu di primo livello e le barre degli strumenti in un file con estensione vsct. Se si crea un'attivazione sul posto dell'editor, quindi implementare <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponent> e definire i menu e barre degli strumenti per l'editor in un file con estensione vsct invece di usare l'unione di menu OLE 2.  
  
-   Per evitare di affollare nell'interfaccia utente di comando di menu, è necessario usare i comandi esistenti nell'IDE prima di inventare nuovi comandi. Comandi condivisi sono definiti in SharedCmdDef.vsct e ShellCmdDef.vsct. Questi file vengono installati per impostazione predefinita nella sottodirectory VisualStudioIntegration\Common\Inc del [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] installazione.  
  
-   `ISelectionContainer` possibile esprimere una o più selezioni. Ogni oggetto selezionato viene implementato come un `IDispatch` oggetto.  
  
-   L'IDE implementa il `IOleUndoManager` come un servizio accessibile da un <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> o come un oggetto che può essere creata un'istanza tramite <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A>. L'editor implementa il `IOleUndoUnit` per ogni interfaccia `Undo` azione.  
  
-   Esistono due posizioni un editor personalizzato può esporre gli oggetti di automazione:  
  
    -   `Document.Object`  
  
    -   `Window.Object`  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta come contributo al modello di automazione](../extensibility/internals/contributing-to-the-automation-model.md)   
 [Procedura: Fornire il contesto per gli editor](../extensibility/how-to-provide-context-for-editors.md)
