---
title: 'Procedura: Implementare progetti annidati | Microsoft Docs'
description: Informazioni su come implementare progetti annidati Visual Studio generando eventi dalla soluzione e dai progetti padre per compilare una gerarchia di progetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- nested projects, implementing
- projects [Visual Studio SDK], nesting
ms.assetid: d20b8d6a-f0e0-4115-b3a3-edda893ae678
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: de258e2b1ca7f57573a1e79d33c6a80960325d3662c8af9ce9e8111a330b6f12
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359312"
---
# <a name="how-to-implement-nested-projects"></a>Procedura: Implementare progetti annidati

Quando si crea un tipo di progetto annidato, è necessario eseguire diversi passaggi aggiuntivi. Un progetto padre assume alcune delle stesse responsabilità della soluzione per i progetti annidati (figlio). Il progetto padre è un contenitore di progetti simile a una soluzione. In particolare, esistono diversi eventi che devono essere generati dalla soluzione e dai progetti padre per compilare la gerarchia dei progetti annidati. Questi eventi sono descritti nel processo seguente per la creazione di progetti annidati.

## <a name="create-nested-projects"></a>Creare progetti annidati

1. L'ambiente di sviluppo integrato (IDE) carica il file di progetto e le informazioni di avvio del progetto padre chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> l'interfaccia . Il progetto padre viene creato e aggiunto alla soluzione.

    > [!NOTE]
    > A questo punto, è troppo presto nel processo per il progetto padre creare il progetto annidato perché il progetto padre deve essere creato prima di poter creare i progetti figlio. Seguendo questa sequenza, il progetto padre può applicare le impostazioni ai progetti figlio e i progetti figlio possono acquisire informazioni dai progetti padre, se necessario. Questa sequenza è se è necessaria in dai client, ad esempio il controllo del codice sorgente (SCC) **e Esplora soluzioni**.

     Il progetto padre deve attendere che il metodo venga chiamato dall'IDE prima di poter creare uno o più <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> progetti annidati (figlio).

2. L'IDE `QueryInterface` chiama sul progetto padre per <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject> . Se questa chiamata ha esito positivo, l'IDE chiama il metodo dell'elemento padre per aprire tutti <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren%2A> i progetti annidati per il progetto padre.

3. Il progetto padre chiama il metodo per notificare ai listener che i progetti annidati <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnBeforeOpeningChildren%2A> stanno per essere creati. SCC, ad esempio, è in ascolto di tali eventi per sapere se i passaggi del processo di creazione della soluzione e del progetto sono in esecuzione nell'ordine indicato. Se i passaggi vengono eseguiti in ordine, la soluzione potrebbe non essere registrata correttamente con il controllo del codice sorgente.

4. Il progetto padre chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProject%2A> il metodo o il metodo su ognuno dei progetti <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.AddVirtualProjectEx%2A> figlio.

     Passare al metodo per indicare che il progetto virtuale (annidato) deve essere aggiunto alla finestra del progetto, escluso dalla compilazione, aggiunto al controllo del codice sorgente <xref:Microsoft.VisualStudio.Shell.Interop.__VSADDVPFLAGS> `AddVirtualProject` e così via. `VSADDVPFLAGS` consente di controllare la visibilità del progetto annidato e indicare la funzionalità associata.

     Se si ricarica un progetto figlio esistente in precedenza con un GUID di progetto archiviato nel file di progetto del progetto padre, il progetto padre chiama `AddVirtualProjectEx` . L'unica differenza tra e è che dispone di un parametro per consentire al progetto padre di specificare una per ogni istanza del progetto figlio per abilitare e `AddVirtualProject` `AddVirtualProjectEX` funzionare `AddVirtualProjectEX` `guidProjectID` <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfGuid%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.GetProjectOfProjref%2A> correttamente.

     Se non è disponibile alcun GUID, ad esempio quando si aggiunge un nuovo progetto annidato, la soluzione ne crea uno per il progetto al momento dell'aggiunta all'elemento padre. È responsabilità del progetto padre rendere persistente il GUID del progetto nel file di progetto. Se si elimina un progetto annidato, è possibile eliminare anche il GUID per tale progetto.

5. L'IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.OpenChildren> chiama il metodo su ogni progetto figlio del progetto padre.

     Il progetto padre deve implementare `IVsParentProject` se si desidera annidare i progetti. Ma il progetto padre non chiama `QueryInterface` mai per anche se ha progetti padre `IVsParentProject` sottostanti. La soluzione gestisce la chiamata a `IVsParentProject` e, se implementata, chiama `OpenChildren` per creare i progetti annidati. `AddVirtualProjectEX` viene sempre chiamato da `OpenChildren` . Non deve mai essere chiamato dal progetto padre per mantenere gli eventi di creazione della gerarchia in ordine.

6. L'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterOpenProject%2A> il metodo sul progetto figlio.

7. Il progetto padre chiama il metodo per notificare ai listener che sono stati creati <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpeningChildren%2A> i progetti figlio per il padre.

8. L'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents.FireOnAfterOpenProject%2A> il metodo sul progetto padre dopo l'apertura di tutti i progetti figlio.

     Se non esiste già, il progetto padre crea un GUID per ogni progetto annidato chiamando `CoCreateGuid` .

    > [!NOTE]
    > `CoCreateGuid` è un'API COM chiamata quando deve essere creato un GUID. Per altre informazioni, vedere `CoCreateGuid` e GUID in MSDN Library.

     Il progetto padre archivia questo GUID nel file di progetto da recuperare alla successiva apertura nell'IDE. Vedere il passaggio 4 per altre informazioni relative alla chiamata di `AddVirtualProjectEX` per recuperare per il progetto `guidProjectID` figlio.

9. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> metodo viene quindi chiamato per l'elemento ItemID padre che per convenzione si delega al progetto annidato. recupera le proprietà del nodo che annida un progetto in cui si vuole delegare quando viene <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> chiamato sull'elemento padre.

     Poiché le istanze dei progetti padre e figlio vengono create a livello di codice, a questo punto è possibile impostare le proprietà per i progetti annidati.

    > [!NOTE]
    > Non solo si ricevono le informazioni di contesto dal progetto annidato, ma è anche possibile chiedere se il progetto padre ha un contesto per tale elemento controllando [__VSHPROPID. VSHPROPID_UserContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_UserContext>). In questo modo, è possibile aggiungere altri attributi della Guida dinamica e opzioni di menu specifiche per i singoli progetti annidati.

10. La gerarchia viene compilata per **la Esplora soluzioni** con una chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A> metodo .

     La gerarchia viene passata all'ambiente tramite `GetNestedHierarchy` per compilare la gerarchia per la visualizzazione in Esplora soluzioni. In questo modo, la soluzione sa che il progetto esiste e può essere gestito per la compilazione da parte della gestione compilazione oppure può consentire l'applicazione di file nel progetto al controllo del codice sorgente.

11. Dopo aver creato tutti i progetti annidati per Project1, il controllo viene passato nuovamente alla soluzione e il processo viene ripetuto per Project2.

     Lo stesso processo per la creazione di progetti annidati si verifica per un progetto figlio con un elemento figlio. In questo caso, se BuildProject1, figlio di Project1, aveva progetti figlio, verrebbero creati dopo BuildProject1 e prima di Project2. Il processo è ricorsivo e la gerarchia viene compilata dall'alto verso il basso.

     Quando un progetto annidato viene chiuso perché l'utente ha chiuso la soluzione o il progetto specifico stesso, viene chiamato l'altro metodo `IVsParentProject` in , <xref:Microsoft.VisualStudio.Shell.Interop.IVsParentProject.CloseChildren%2A> . Il progetto padre esegue il wrapping delle chiamate al metodo con e i metodi per notificare ai listener gli eventi della soluzione che i progetti <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.RemoveVirtualProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeClosingChildren%2A> annidati vengono <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterClosingChildren%2A> chiusi.

Gli argomenti seguenti trattano diversi altri concetti da considerare quando si implementano progetti annidati:

- [Considerazioni per lo scaricamento e il ricaricamento di progetti annidati](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [Supporto della procedura guidata per i progetti annidati](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [Implementare la gestione dei comandi per i progetti annidati](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [Filtrare la finestra di dialogo AddItem per i progetti annidati](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)

## <a name="see-also"></a>Vedi anche

- [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrare modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Elenco di controllo: Creare nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [File della procedura guidata (con estensione vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
