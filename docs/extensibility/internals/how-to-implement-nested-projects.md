---
title: 'Procedura: Implementare progetti annidati | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d22d67d81776f83683e11d1ca613a9138137e75c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945809"
---
# <a name="how-to-implement-nested-projects"></a>Procedura: Implementare progetti annidati

Quando si crea un tipo di progetto annidato, esistono alcuni passaggi aggiuntivi che devono essere implementati. Un progetto padre acquisisce alcune delle responsabilità stessa con la soluzione per i progetti annidati (figlio). Il progetto padre è un contenitore di progetti simili a una soluzione. In particolare, esistono diversi eventi che devono essere generati dalla soluzione e per i progetti padre per compilare la gerarchia di oggetti annidati. Questi eventi sono descritti nel processo seguente per la creazione di progetti annidati.

## <a name="create-nested-projects"></a>Creare i progetti annidati

1.  L'ambiente di sviluppo integrato (IDE) carica le informazioni di avvio e file di progetto del progetto padre chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaccia. Il progetto principale viene creato e aggiunto alla soluzione.

    > [!NOTE]
    > A questo punto, è abbastanza recente del processo per il progetto principale creare il progetto annidato perché è necessario creare il progetto principale prima di possono creare i progetti figlio. Dopo questa sequenza, il progetto principale può applicare le impostazioni per i progetti figlio e i progetti figlio possono acquisire le informazioni dai progetti padre se necessario. Questa sequenza è se è necessario nel client, ad esempio controllo del codice sorgente (SCC) e **Esplora soluzioni**.

     Il progetto padre deve attendere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metodo deve essere chiamato dall'IDE prima può creare annidato (figlio) o più progetti.

2.  Le chiamate IDE `QueryInterface` del progetto padre per <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>. Se la chiamata ha esito positivo, le chiamate dell'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metodo dell'elemento padre per aprire tutti i progetti annidati per il progetto padre.

3.  Le chiamate di progetto padre il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> metodo per notificare ai listener che i progetti annidati sta per essere creata. Controllo del codice sorgente, ad esempio, è in ascolto in modo da sapere se si verificano nell'ordine i passaggi nel processo di creazione del progetto e soluzione. Se si verificano i passaggi non in ordine, la soluzione potrebbe non essere registrata con controllo del codice sorgente in modo corretto.

4.  Le chiamate di progetto padre <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> metodo o il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> metodo su ciascuno dei relativi progetti figlio.

     Si passa <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> per il `AddVirtualProject` metodo per indicare che il progetto virtuale (annidato) deve essere aggiunte alla finestra progetto, esclusa dalla compilazione, aggiunto al controllo del codice sorgente e così via. `VSADDVPFLAGS` Consente di controllare la visibilità del progetto annidata e indicare quali funzionalità è associato ad esso.

     Se si ricarica un progetto figlio già esistente che dispone di un progetto GUID archiviato nel file di progetto del progetto padre, le chiamate di progetto padre `AddVirtualProjectEx`. L'unica differenza tra `AddVirtualProject` e `AddVirtualProjectEX` è quello `AddVirtualProjectEX` ha un parametro per abilitare il progetto principale specificare una per ogni istanza `guidProjectID` per il progetto figlio abilitare <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> alla funzione in modo corretto.

     Se non è presente alcuna GUID disponibili, ad esempio quando si aggiunge un nuovo progetto annidato, la soluzione crea uno per il progetto al momento viene aggiunto all'elemento padre. È responsabilità del progetto padre per rendere persistente tale GUID nel file di progetto del progetto. Se si elimina un progetto annidato, anche il GUID per il progetto può essere eliminato.

5.  Le chiamate dell'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> metodo su ogni progetto figlio del progetto padre.

     Il progetto padre deve implementare `IVsParentProject` se si desidera nidificare i progetti. Ma l'elemento padre del progetto mai chiamate `QueryInterface` per `IVsParentProject` anche se sono progetti principali in esso contenuti. La soluzione gestisce la chiamata a `IVsParentProject` e, se è implementato, chiama il metodo `OpenChildren` per creare i progetti annidati. `AddVirtualProjectEX` viene sempre chiamato da `OpenChildren`. Non si dovrebbe mai essere chiamato dal progetto padre per mantenere la gerarchia di eventi di creazione nell'ordine.

6.  Le chiamate dell'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> metodo sul progetto figlio.

7.  Le chiamate di progetto padre il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> metodo per notificare ai listener che siano stati creati i progetti figlio per l'elemento padre.

8.  Le chiamate dell'IDE di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> metodo sul progetto padre dopo l'apertura di tutti i progetti figlio.

     Se non esiste già, il progetto principale viene creato un GUID per ogni progetto annidato chiamando `CoCreateGuid`.

    > [!NOTE]
    > `CoCreateGuid` un'API COM viene chiamata quando viene creato un GUID. Per altre informazioni, vedere `CoCreateGuid` e GUID in MSDN Library.

     Il progetto principale archivia questo GUID nel file di progetto deve essere recuperato la prossima volta che viene aperto nell'IDE. Vedere il passaggio 4 per altre informazioni relative al chiamante di `AddVirtualProjectEX` per recuperare il `guidProjectID` per il progetto figlio.

9. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> viene quindi chiamato il metodo per l'ID dell'elemento padre che per convenzione delegare per il progetto annidato. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> recupera le proprietà del nodo che annida un progetto che si desidera delegare quando viene chiamato sull'oggetto padre.

     Poiché i progetti padre e figlio vengono creata un'istanza a livello di codice, è possibile impostare proprietà per i progetti annidati a questo punto.

    > [!NOTE]
    > Non solo si ricevono le informazioni sul contesto dal progetto annidato, ma è anche possibile richiedere se il progetto principale dispone di alcun contesto per quell'elemento controllando <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>. In tal modo, è possibile aggiungere gli attributi della Guida dinamica aggiuntivi e le opzioni di menu specifiche per singoli progetti annidati.

10. La gerarchia viene compilata per la visualizzazione nel **Esplora soluzioni** con una chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> (metodo).

     La gerarchia è passare all'ambiente tramite `GetNestedHierarchy` per compilare la gerarchia per la visualizzazione in Esplora soluzioni. In questo modo, la soluzione sa che il progetto è presente e può essere gestito per la compilazione per il gestore di compilazione o può consentire i file del progetto da inserire nel controllo del codice sorgente.

11. Quando sono stati creati tutti i progetti annidati per Project1, il controllo viene passato nuovamente alla soluzione e il processo viene ripetuto per Project2.

     Lo stesso processo per la creazione di progetti annidati si verifica per un progetto figlio con un elemento figlio. In questo caso, se BuildProject1, ovvero un elemento figlio di Project1, aveva i progetti figlio, essi viene creati dopo BuildProject1 e prima Project2. Il processo è ricorsivo e la gerarchia viene compilata dall'alto verso il basso.

     Quando un progetto annidato viene chiuso perché l'utente ha chiuso la soluzione o le specifiche del progetto, con l'altro metodo nella `IVsParentProject`, <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>, viene chiamato. Progetto padre esegue il wrapping di chiamate per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> metodo con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> metodi per notificare ai listener di eventi della soluzione che i progetti annidati vengono chiusi.

Gestiscono alcuni altri concetti da prendere in considerazione quando si implementano i progetti annidati gli argomenti seguenti:

- [Considerazioni per scaricare e ricaricare i progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Supporto della procedura guidata per i progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implementare la gestione dei comandi per i progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtra la finestra di dialogo AddItem per i progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Vedere anche

- [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrare i modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Elenco di controllo: Creare nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [File della procedura guidata (con estensione vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)