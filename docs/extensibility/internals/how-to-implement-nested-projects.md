---
title: 'Procedura: implementare progetti annidati . Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8d9dfe567db0b8788b93b13aeb760d45f4c05b57
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707979"
---
# <a name="how-to-implement-nested-projects"></a>Procedura: implementare progetti annidatiHow to: Implement nested projects

Quando si crea un tipo di progetto annidato, è necessario implementare diversi passaggi aggiuntivi. Un progetto padre assume alcune delle stesse responsabilità della soluzione per i progetti annidati (figlio). Il progetto padre è un contenitore di progetti simili a una soluzione. In particolare, esistono diversi eventi che devono essere generati dalla soluzione e dai progetti padre per compilare la gerarchia dei progetti annidati. Questi eventi sono descritti nel processo seguente per la creazione di progetti annidati.

## <a name="create-nested-projects"></a>Creare progetti nidificati

1. L'ambiente di sviluppo integrato (IDE) carica il file di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> progetto del progetto padre e le informazioni di avvio chiamando l'interfaccia. Il progetto padre viene creato e aggiunto alla soluzione.

    > [!NOTE]
    > A questo punto, è troppo presto nel processo per il progetto padre per creare il progetto annidato perché il progetto padre deve essere creato prima di poter creare i progetti figlio. Seguendo questa sequenza, il progetto padre può applicare le impostazioni ai progetti figlio e i progetti figlio possono acquisire informazioni dai progetti padre, se necessario. Questa sequenza è se è necessaria per i client, ad esempio il controllo del codice sorgente (SCC) e **Esplora soluzioni**.

     Il progetto padre deve <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> attendere che il metodo venga chiamato dall'IDE prima di poter creare il progetto o i progetti annidati (figlio).

2. L'IDE `QueryInterface` chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject>progetto padre per . Se questa chiamata ha esito <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> positivo, l'IDE chiama il metodo dell'elemento padre per aprire tutti i progetti annidati per il progetto padre.

3. Il progetto padre <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> chiama il metodo per notificare ai listener che i progetti annidati stanno per essere creati. SCC, ad esempio, è in ascolto di tali eventi per sapere se i passaggi nel processo di creazione della soluzione e del progetto si verificano nell'ordine. Se i passaggi si verificano non in ordine, la soluzione potrebbe non essere registrata correttamente con il controllo del codice sorgente.

4. Il progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> padre chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> il metodo o il metodo su ciascuno dei relativi progetti figlio.

     Si <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> passa `AddVirtualProject` al metodo per indicare che il progetto virtuale (annidato) deve essere aggiunto alla finestra del progetto, escluso dalla compilazione, aggiunto al controllo del codice sorgente e così via. `VSADDVPFLAGS`consente di controllare la visibilità del progetto annidato e di indicare la funzionalità associata.

     Se si ricarica un progetto figlio esistente in precedenza con un GUID di progetto `AddVirtualProjectEx`archiviato nel file di progetto del progetto padre, il progetto padre chiama . L'unica `AddVirtualProject` differenza `AddVirtualProjectEX` tra `AddVirtualProjectEX` ed è che dispone di un `guidProjectID` parametro per consentire <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> al progetto padre di specificare un'istanza per il progetto figlio da abilitare e per funzionare correttamente.

     Se non è disponibile alcun GUID, ad esempio quando si aggiunge un nuovo progetto annidato, la soluzione ne crea uno per il progetto nel momento in cui viene aggiunto all'elemento padre. È responsabilità del progetto padre mantenere il GUID del progetto nel relativo file di progetto. Se si elimina un progetto nidificato, è possibile eliminare anche il GUID di tale progetto.

5. L'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> chiama il metodo su ogni progetto figlio del progetto padre.

     Il progetto padre `IVsParentProject` deve implementare se si desidera nidificare i progetti. Ma il progetto `QueryInterface` padre `IVsParentProject` non richiede mai anche se ha progetti padre sotto di esso. La soluzione gestisce `IVsParentProject` la chiamata a e, se viene implementata, le chiamate `OpenChildren` per creare i progetti annidati. `AddVirtualProjectEX`viene sempre `OpenChildren`chiamato da . Non deve mai essere chiamato dal progetto padre per mantenere in ordine gli eventi di creazione della gerarchia.

6. L'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> chiama il metodo sul progetto figlio.

7. Il progetto padre <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> chiama il metodo per notificare ai listener che i progetti figlio per l'elemento padre sono stati creati.

8. L'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> chiama il metodo sul progetto padre dopo l'apertura di tutti i progetti figlio.

     Se non esiste già, il progetto padre crea un `CoCreateGuid`GUID per ogni progetto annidato chiamando .

    > [!NOTE]
    > `CoCreateGuid`è un'API COM chiamata quando deve essere creato un GUID. Per ulteriori informazioni, vedere `CoCreateGuid` e GUID in MSDN Library.

     Il progetto padre archivia questo GUID nel file di progetto da recuperare la volta successiva che viene aperto nell'IDE. Vedere il passaggio 4 per `AddVirtualProjectEX` ulteriori informazioni `guidProjectID` relative alla chiamata di per recuperare il per il progetto figlio.

9. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodo viene quindi chiamato per l'elemento padre ItemID che per convenzione si delega al progetto annidato. Recupera <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> le proprietà del nodo che annida un progetto che si desidera delegare quando viene chiamato sull'elemento padre.

     Poiché viene creata un'istanza di progetti padre e figlio a livello di codice, è possibile impostare le proprietà per i progetti annidati a questo punto.

    > [!NOTE]
    > Non solo si ricevono le informazioni sul contesto dal progetto annidato, ma è anche possibile chiedere se il progetto padre dispone di qualsiasi contesto per tale elemento controllando [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). In questo modo, è possibile aggiungere ulteriori attributi della Guida dinamica e opzioni di menu specifiche per i singoli progetti nidificati.

10. La gerarchia viene compilata per la visualizzazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> in **Esplora soluzioni** con una chiamata al metodo .

     Passare la gerarchia all'ambiente attraverso `GetNestedHierarchy` per compilare la gerarchia per la visualizzazione in Esplora soluzioni. In questo modo, la soluzione sa che il progetto esiste e può essere gestito per la compilazione dal gestore di compilazione o può consentire ai file nel progetto di essere inseriti nel controllo del codice sorgente.

11. Dopo aver creato tutti i progetti annidati per Project1, il controllo viene passato alla soluzione e il processo viene ripetuto per Project2.

     Questo stesso processo per la creazione di progetti annidati si verifica per un progetto figlio che ha un figlio. In questo caso, se BuildProject1, che è un elemento figlio di Project1, ha progetti figlio, verranno creati dopo BuildProject1 e prima di Project2. Il processo è ricorsivo e la gerarchia viene creata dall'alto verso il basso.

     Quando un progetto annidato viene chiuso perché l'utente ha chiuso `IVsParentProject` <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A>la soluzione o il progetto specifico stesso, viene chiamato l'altro metodo in , , . Il progetto padre esegue <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> il wrapping <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> delle <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> chiamate al metodo con i metodi e per notificare ai listener agli eventi della soluzione che i progetti annidati vengono chiusi.

Negli argomenti seguenti vengono trattati diversi altri concetti da considerare quando si implementano progetti annidati:The following topics deal with several other concepts to consider when you implement nested projects:

- [Considerazioni per lo scaricamento e il ricaricamento di progetti annidatiConsiderations for unloading and reloading nested projects](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Supporto della procedura guidata per i progetti nidificati](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implementare la gestione dei comandi per i progetti annidatiImplement command handling for nested projects](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrare la finestra di dialogo AggiungiElemento per i progetti nidificati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Vedere anche

- [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrare modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Elenco di controllo: creare nuovi tipi di progettoChecklist: Create new project types](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [File della procedura guidata (vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
