---
title: 'Procedura: implementare progetti annidati | Microsoft Docs'
description: Informazioni su come implementare i progetti annidati in Visual Studio generando eventi dalla soluzione e dai progetti padre per compilare una gerarchia del progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1b02fca5d37d7e75cd7c32527bb09358425e626
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932540"
---
# <a name="how-to-implement-nested-projects"></a>Procedura: implementare progetti annidati

Quando si crea un tipo di progetto annidato, è necessario implementare alcuni passaggi aggiuntivi. Un progetto padre assume alcune delle stesse responsabilità della soluzione per i progetti annidati (figlio). Il progetto padre è un contenitore di progetti simile a una soluzione. In particolare, esistono diversi eventi che devono essere generati dalla soluzione e dai progetti padre per compilare la gerarchia di progetti annidati. Questi eventi sono descritti nel processo seguente per la creazione di progetti annidati.

## <a name="create-nested-projects"></a>Creazione di progetti annidati

1. Il Integrated Development Environment (IDE) carica il file di progetto del progetto padre e le informazioni di avvio chiamando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> interfaccia. Il progetto padre viene creato e aggiunto alla soluzione.

    > [!NOTE]
    > A questo punto, è troppo presto nel processo che il progetto padre crei il progetto annidato, perché il progetto padre deve essere creato prima di poter creare i progetti figlio. In seguito a questa sequenza, il progetto padre può applicare le impostazioni ai progetti figlio e i progetti figlio possono acquisire informazioni dai progetti padre, se necessario. Questa sequenza è necessaria per i client, ad esempio il controllo del codice sorgente (SCC) e **Esplora soluzioni**.

     Il progetto padre deve attendere che il <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metodo venga chiamato dall'IDE prima di poter creare il progetto o i progetti annidati (figlio).

2. L'IDE chiama `QueryInterface` per il progetto padre <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> . Se la chiamata ha esito positivo, l'IDE chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> metodo dell'elemento padre per aprire tutti i progetti annidati per il progetto padre.

3. Il progetto padre chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> metodo per notificare ai listener che stanno per essere creati i progetti annidati. SCC, ad esempio, è in ascolto di tali eventi per verificare se i passaggi della soluzione e del processo di creazione del progetto si verificano nell'ordine. Se i passaggi non vengono eseguiti in ordine, è possibile che la soluzione non venga registrata correttamente con il controllo del codice sorgente.

4. Il progetto padre chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> il metodo o il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> metodo su ognuno dei relativi progetti figlio.

     Passare <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> al `AddVirtualProject` metodo per indicare che il progetto virtuale (annidato) deve essere aggiunto alla finestra del progetto, escluso dalla compilazione, aggiunto al controllo del codice sorgente e così via. `VSADDVPFLAGS` consente di controllare la visibilità del progetto annidato e indicare la funzionalità a essa associata.

     Se si ricarica un progetto figlio precedentemente esistente con un GUID di progetto archiviato nel file di progetto del progetto padre, il progetto padre chiama `AddVirtualProjectEx` . L'unica differenza tra `AddVirtualProject` e `AddVirtualProjectEX` è che `AddVirtualProjectEX` dispone di un parametro per consentire al progetto padre di specificare un oggetto per ogni istanza `guidProjectID` affinché il progetto figlio abiliti <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> funzioni correttamente.

     Se non è disponibile alcun GUID, ad esempio quando si aggiunge un nuovo progetto annidato, la soluzione ne crea una per il progetto nel momento in cui viene aggiunta all'elemento padre. È responsabilità del progetto padre salvare in modo permanente il GUID del progetto nel file di progetto. Se si elimina un progetto annidato, è possibile eliminare anche il GUID per il progetto.

5. L'IDE chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> metodo su ogni progetto figlio del progetto padre.

     Il progetto padre deve implementare `IVsParentProject` se si desidera annidare i progetti. Il progetto padre non chiama mai `QueryInterface` `IVsParentProject` anche se contiene progetti padre. La soluzione gestisce la chiamata a `IVsParentProject` e, se è implementata, chiama `OpenChildren` per creare i progetti annidati. `AddVirtualProjectEX` viene sempre chiamato da `OpenChildren` . Non deve mai essere chiamato dal progetto padre per tenere in ordine gli eventi di creazione della gerarchia.

6. L'IDE chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> metodo nel progetto figlio.

7. Il progetto padre chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> metodo per notificare ai listener che sono stati creati i progetti figlio per l'elemento padre.

8. L'IDE chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> metodo sul progetto padre dopo l'apertura di tutti i progetti figlio.

     Se non esiste già, il progetto padre crea un GUID per ogni progetto annidato chiamando `CoCreateGuid` .

    > [!NOTE]
    > `CoCreateGuid` è un'API COM chiamata quando è necessario creare un GUID. Per ulteriori informazioni, vedere `CoCreateGuid` e GUID in MSDN Library.

     Il progetto padre archivia il GUID nel file di progetto da recuperare alla successiva apertura nell'IDE. Per ulteriori informazioni relative alla chiamata di per `AddVirtualProjectEX` recuperare il `guidProjectID` per il progetto figlio, vedere il passaggio 4.

9. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodo viene quindi chiamato per l'elemento ItemId padre che per convenzione si delega al progetto annidato. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>Recupera le proprietà del nodo che nidifica un progetto che si desidera delegare quando viene chiamato sull'elemento padre.

     Poiché i progetti padre e figlio vengono creati a livello di codice, è possibile impostare le proprietà per i progetti annidati in questo punto.

    > [!NOTE]
    > Non solo si ricevono le informazioni sul contesto dal progetto annidato, ma è anche possibile chiedere se il progetto padre dispone di un contesto per tale elemento controllando [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). In questo modo, è possibile aggiungere attributi guida dinamici aggiuntivi e opzioni di menu specifiche per singoli progetti annidati.

10. La gerarchia viene compilata per la visualizzazione in **Esplora soluzioni** con una chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> metodo.

     La gerarchia viene passata all'ambiente tramite `GetNestedHierarchy` per compilare la gerarchia per la visualizzazione in Esplora soluzioni. In questo modo, la soluzione sa che il progetto esiste e può essere gestito per la compilazione da parte del gestore di compilazione oppure può consentire l'inserimento dei file nel progetto nel controllo del codice sorgente.

11. Quando sono stati creati tutti i progetti annidati per Project1, il controllo viene passato nuovamente alla soluzione e il processo viene ripetuto per Progetto2.

     Questo processo per la creazione di progetti annidati si verifica per un progetto figlio con un figlio. In questo caso, se BuildProject1, che è un elemento figlio di Project1, aveva progetti figlio, verranno creati dopo BuildProject1 e prima di Progetto2. Il processo è ricorsivo e la gerarchia viene compilata dall'alto verso il basso.

     Quando un progetto annidato viene chiuso perché l'utente ha chiuso la soluzione o il progetto specifico, viene chiamato l'altro metodo in `IVsParentProject` , <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> . Il progetto padre esegue il wrapping delle chiamate al <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> metodo con i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> metodi e per notificare ai listener gli eventi della soluzione che i progetti annidati sono in fase di chiusura.

Negli argomenti seguenti vengono trattati molti altri concetti da considerare quando si implementano i progetti annidati:

- [Considerazioni per lo scaricamento e il ricaricamento di progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Supporto della procedura guidata per i progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implementare la gestione dei comandi per i progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrare la finestra di dialogo AddItem per i progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Vedi anche

- [Aggiungi elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrare modelli di progetti e di elementi](../../extensibility/internals/registering-project-and-item-templates.md)
- [Elenco di controllo: creare nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [File della procedura guidata (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
