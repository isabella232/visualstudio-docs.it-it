---
title: Tabella documento in esecuzione Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9e6aa882921786b1592922372581beae8c4c2443
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705560"
---
# <a name="running-document-table"></a>Tabella documenti in esecuzione
L'IDE gestisce l'elenco di tutti i documenti attualmente aperti in una struttura interna denominata tabella documenti in esecuzione (RDT). Questo elenco include tutti i documenti aperti in memoria, indipendentemente dal fatto che questi documenti siano attualmente in fase di modifica. Un documento è qualsiasi elemento persistente, inclusi i file in un progetto o il file di progetto principale (ad esempio, un file con estensione vcxproj).

## <a name="elements-of-the-running-document-table"></a>Elementi della tabella documenti in esecuzione
 La tabella dei documenti in esecuzione contiene le voci seguenti.

|Elemento|Descrizione|
|-------------|-----------------|
|Moniker del documento|Stringa che identifica in modo univoco l'oggetto dati del documento. Questo sarebbe il percorso di file assoluto per un sistema di progetto che gestisce i file (ad esempio, C: Questa stringa viene utilizzata anche per i progetti salvati in archivi diversi dai file system, ad esempio le stored procedure in un database. In questo caso, il sistema del progetto può inventare una stringa univoca che può riconoscere ed eventualmente analizzare per determinare come archiviare il documento.|
|Proprietario gerarchia|Oggetto gerarchia proprietario del documento, rappresentato da un'interfaccia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|
|ID articolo|Identificatore dell'elemento per un elemento specifico all'interno della gerarchia. Questo valore è univoco tra tutti i documenti della gerarchia proprietaria di questo documento, ma non è garantito che questo valore sia univoco tra gerarchie diverse.|
|Oggetto dati del documento|Come minimo, si tratta di un`IUnknown`<br /><br /> . L'IDE non richiede alcuna `IUnknown` interfaccia particolare oltre l'interfaccia per l'oggetto dati del documento di un editor personalizzato. Tuttavia, per un editor standard, l'implementazione dell'editor dell'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> è necessaria per gestire le chiamate di persistenza dei file dal progetto. Per ulteriori informazioni, consultate [Salvataggio di un documento standard.](../../extensibility/internals/saving-a-standard-document.md)|
|Flags|I flag che controllano se il documento viene salvato, se viene applicato un blocco di lettura o modifica e così via, possono essere specificati quando vengono aggiunte voci a RDT. Per altre informazioni, vedere l'enumerazione <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|
|Modifica conteggio blocchi|Conteggio dei blocchi di modifica. Un blocco di modifica indica che in alcuni editor il documento è aperto per la modifica. Quando il conteggio dei blocchi di modifica passa a zero, all'utente viene richiesto di salvare il documento, se è stato modificato. Ad esempio, ogni volta che si apre un documento in un editor utilizzando il comando **Nuova finestra,** viene aggiunto un blocco di modifica per tale documento in RDT. Affinché sia impostato un blocco di modifica, il documento deve avere una gerarchia o un ID elemento.|
|Conteggio blocchi di letturaRead Lock Count|Conteggio dei blocchi di lettura. Un blocco di lettura indica che il documento viene letto attraverso un meccanismo, ad esempio una procedura guidata. Un blocco di lettura contiene un documento attivo in RDT, mentre indica che il documento non può essere modificato. È possibile impostare un blocco di lettura anche se il documento non dispone di una gerarchia o di un ID elemento. Questa funzionalità consente di aprire un documento in memoria e immetterlo in RDT senza che il documento sia di proprietà di alcuna gerarchia. Questa funzione viene utilizzata raramente.|
|Portaserratura|Istanza di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> un'interfaccia. Il supporto di blocco è implementato da funzionalità come procedure guidate che aprono e modificano documenti all'esterno di un editor. Un supporto di blocco consente alla funzione di aggiungere un blocco di modifica al documento per impedire la chiusura del documento mentre è ancora in fase di modifica. In genere, i blocchi di modifica vengono aggiunti solo dalle finestre di documento (ovvero gli editor).|

 A ogni voce in RDT è associata una gerarchia univoca o un ID elemento, che in genere corrisponde a un nodo del progetto. Tutti i documenti disponibili per la modifica sono in genere di proprietà di una gerarchia. Le voci effettuate nel controllo RDT controllano il progetto o, più precisamente, la gerarchia proprietaria dell'oggetto dati del documento in corso di modifica. Utilizzando le informazioni in RDT, l'IDE può impedire che un documento venga aperto da più di un progetto alla volta.

 La gerarchia controlla inoltre la persistenza dei dati e utilizza le informazioni in RDT per aggiornare le finestre di dialogo **Salva** e **Salva con nome.** Quando gli utenti modificano un documento e quindi scegliere il **esci** comando dal **File** menu, l'IDE chiede con il **Salva modifiche** la finestra di dialogo per visualizzare tutti i progetti e gli elementi di progetto che sono attualmente modificati. Ciò consente agli utenti di scegliere quale dei documenti salvare. L'elenco dei documenti da salvare, ovvero i documenti con modifiche, viene generato da RDT. Tutti gli elementi che si prevede di visualizzare nella finestra di dialogo **Salva modifiche** all'uscita dall'applicazione devono avere record in RDT. RDT coordina quali documenti vengono salvati e se all'utente viene richiesto di eseguire un'operazione di salvataggio utilizzando i valori specificati nella voce Flags per ogni documento. Per ulteriori informazioni sui flag RDT, vedere l'enumerazione. <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>

## <a name="edit-locks-and-read-locks"></a>Modifica blocchi e blocchi di lettura
 I blocchi di modifica e di lettura risiedono in RDT. La finestra del documento incrementa e decrementa il blocco di modifica. Pertanto, quando un utente apre una nuova finestra del documento, il conteggio dei blocchi di modifica viene incrementato di uno. Quando il numero di blocchi di modifica raggiunge lo zero, la gerarchia viene segnalata per mantenere o salvare i dati per il documento associato. La gerarchia può quindi rendere persistenti i dati in qualsiasi modo, inclusa la persistenza come file o come elemento in un repository. È possibile <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> metodo nell'interfaccia per aggiungere blocchi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> di modifica e blocchi di lettura e il metodo per rimuovere questi blocchi.

 In genere, quando viene creata un'istanza della finestra del documento per un editor, la cornice della finestra aggiunge automaticamente un blocco di modifica per il documento in RDT. Tuttavia, se si crea una visualizzazione personalizzata di un documento che non utilizza <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> una finestra di documento standard (vale a dire, non implementa l'interfaccia), è necessario impostare il proprio blocco di modifica. Ad esempio, in una procedura guidata, un documento viene modificato senza essere aperto in un editor. Affinché i blocchi del documento vengano aperti da procedure guidate ed <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> entità simili, queste entità devono implementare l'interfaccia. Per registrare il segnaposto <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> del blocco documento, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> chiamare il metodo e passare l'implementazione. In questo modo si aggiunge il supporto del blocco del documento a RDT. Un altro scenario per l'implementazione di un supporto di blocco documento è se si apre un documento tramite una finestra degli strumenti speciale. In questo caso, non è possibile fare in modo che la finestra degli strumenti chiuda il documento. Tuttavia, registrandosi come titolare del blocco del documento in <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> RDT, l'IDE può chiamare l'implementazione del metodo per richiedere la chiusura del documento.

## <a name="other-uses-of-the-running-document-table"></a>Altri utilizzi della tabella documenti in esecuzione
 Altre entità nell'IDE utilizzano RDT per ottenere informazioni sui documenti. Ad esempio, il gestore del controllo del codice sorgente utilizza RDT per indicare al sistema di ricaricare un documento nell'editor, dopo aver ottenuto la versione più recente del file. A tale scopo, il gestore del controllo del codice sorgente cerca i file in RDT per verificare se uno di essi è aperto. In caso affermativo, il gestore del controllo del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> codice sorgente verifica innanzitutto se la gerarchia implementa il metodo. Se il progetto non <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> implementa il metodo, il gestore <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> del controllo del codice sorgente verifica direttamente un'implementazione del metodo sull'oggetto dati del documento.

 L'IDE utilizza anche RDT per riemergere (portare in primo piano) un documento aperto, se un utente richiede tale documento. Per ulteriori informazioni, consultate [Visualizzazione di file mediante il comando Apri file.](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md) Per determinare se un file è aperto in RDT, eseguire una delle operazioni seguenti.

- Eseguire una query per il moniker del documento (ovvero il percorso completo del documento) per scoprire se l'elemento è aperto.

- Utilizzare la gerarchia o l'ID elemento per richiedere al sistema del progetto il percorso completo del documento e quindi cercare l'elemento in RDT.

## <a name="see-also"></a>Vedere anche
- [Uso di RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Salvataggio permanente e tabella documenti in esecuzione](../../extensibility/internals/persistence-and-the-running-document-table.md)
