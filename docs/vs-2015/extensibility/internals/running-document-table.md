---
title: Tabella documenti in esecuzione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7ea32df892efa47c91d8292bdc9065080318a059
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155549"
---
# <a name="running-document-table"></a>Tabella documenti in esecuzione
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L'IDE gestisce l'elenco di tutti i documenti attualmente aperti in una struttura interna denominata tabella documenti in esecuzione (RDT). Questo elenco include tutti i documenti aperti in memoria, indipendentemente dal fatto che questi documenti siano attualmente in fase di modifica. Un documento è un elemento che viene mantenuto, inclusi i file in un progetto o il file di progetto principale (ad esempio, un file con estensione vcxproj).  
  
## <a name="elements-of-the-running-document-table"></a>Elementi della tabella documenti in esecuzione  
 La tabella documenti in esecuzione contiene le voci seguenti.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Moniker documento|Stringa che identifica in modo univoco l'oggetto dati del documento. Si tratta del percorso di file assoluto per un sistema di progetto che gestisce i file (ad esempio, C:\MyProject\MyFile). Questa stringa viene usata anche per i progetti salvati in archivi diversi dai file System, ad esempio le stored procedure in un database. In questo caso, il sistema del progetto può inventare una stringa univoca che può riconoscere ed eventualmente analizzare per determinare come archiviare il documento.|  
|Proprietario della gerarchia|Oggetto Hierarchy proprietario del documento, come rappresentato da un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia.|  
|ID elemento|Identificatore di elemento per un elemento specifico all'interno della gerarchia. Questo valore è univoco tra tutti i documenti nella gerarchia che possiede questo documento, ma questo valore non è necessariamente univoco tra gerarchie diverse.|  
|Oggetto dati documento|Come minimo, si tratta di un `IUnknown`<br /><br /> . L'IDE non richiede alcuna interfaccia particolare, oltre all' `IUnknown` interfaccia per l'oggetto dati del documento di un editor personalizzato. Tuttavia, per un editor standard, l'implementazione dell'editor dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaccia è necessaria per gestire le chiamate di persistenza dei file dal progetto. Per ulteriori informazioni, vedere [salvataggio di un documento standard](../../extensibility/internals/saving-a-standard-document.md).|  
|Flags|Flag che controllano se il documento viene salvato, se viene applicato un blocco di lettura o di modifica e così via, quando le voci vengono aggiunte a RDT. Per altre informazioni, vedere l'enumerazione <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|  
|Modifica conteggio blocchi|Numero di blocchi di modifica. Un blocco di modifica indica che in alcuni editor il documento è aperto per la modifica. Quando il numero di blocchi di modifica passa a zero, all'utente viene richiesto di salvare il documento, se è stato modificato. Ad esempio, ogni volta che si apre un documento in un editor usando il comando **nuova finestra** , viene aggiunto un blocco di modifica per il documento in RDT. Per impostare un blocco di modifica, è necessario che il documento disponga di un ID di gerarchia o di elemento.|  
|Conteggio blocchi letti|Conteggio dei blocchi di lettura. Un blocco di lettura indica che il documento viene letto tramite un meccanismo, ad esempio una procedura guidata. Un blocco di lettura conserva un documento attivo in RDT, indicando che non è possibile modificare il documento. È possibile impostare un blocco di lettura anche se il documento non dispone di un ID di gerarchia o di elemento. Questa funzionalità consente di aprire un documento in memoria e di immetterlo in RDT senza che il documento appartenga a una gerarchia. Questa funzionalità viene utilizzata raramente.|  
|Titolare blocco|Istanza di un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaccia. Il titolare del blocco viene implementato da caratteristiche quali procedure guidate che aprono e modificano documenti all'esterno di un editor. Un titolare di blocco consente alla funzionalità di aggiungere un blocco di modifica al documento per impedire che il documento venga chiuso mentre è ancora in fase di modifica. In genere, i blocchi di modifica vengono aggiunti solo dalle finestre dei documenti (ovvero gli editor).|  
  
 A ogni voce di RDT è associato un ID di elemento o gerarchia univoco, che in genere corrisponde a un nodo nel progetto. Tutti i documenti disponibili per la modifica sono in genere di proprietà di una gerarchia. Le voci eseguite in RDT controllano quale progetto, o, in modo più accurato, quale gerarchia attualmente possiede l'oggetto dati del documento modificato. Utilizzando le informazioni contenute in RDT, l'IDE può impedire l'apertura di un documento da più di un progetto alla volta.  
  
 La gerarchia controlla anche la persistenza dei dati e usa le informazioni contenute in RDT per aggiornare le finestre di dialogo **Salva** e **Salva con nome** . Quando gli utenti modificano un documento e quindi scelgono il comando **Esci** dal menu **file** , l'IDE richiede la finestra di dialogo **Salva modifiche** per visualizzare tutti i progetti e gli elementi di progetto attualmente modificati. Ciò consente agli utenti di scegliere i documenti da salvare. L'elenco dei documenti da salvare, ovvero i documenti con modifiche, viene generato dal RDT. Tutti gli elementi che si prevede di visualizzare nella finestra di dialogo **Salva modifiche** al momento dell'uscita dall'applicazione devono avere record in RDT. RDT coordina i documenti salvati e indica se all'utente viene richiesto di eseguire un'operazione di salvataggio utilizzando i valori specificati nella voce Flags per ogni documento. Per ulteriori informazioni sui flag RDT, vedere l' <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> enumerazione.  
  
## <a name="edit-locks-and-read-locks"></a>Modificare i blocchi e leggere i blocchi  
 I blocchi di modifica e di lettura si trovano in RDT. La finestra del documento incrementa e decrementa il blocco di modifica. Pertanto, quando un utente apre una nuova finestra del documento, il numero di blocchi di modifica viene incrementato di uno. Quando il numero di blocchi di modifica raggiunge lo zero, la gerarchia viene segnalata in modo da renderli permanente o salvare i dati per il documento associato. La gerarchia può quindi salvare in modo permanente i dati in qualsiasi modo, inclusa la permanenza come file o come elemento in un repository. È possibile usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> metodo nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfaccia per aggiungere i blocchi di modifica e di lettura e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metodo per rimuovere questi blocchi.  
  
 In genere, quando viene creata un'istanza della finestra del documento per un editor, la cornice della finestra aggiunge automaticamente un blocco di modifica per il documento in RDT. Tuttavia, se si crea una visualizzazione personalizzata di un documento che non usa una finestra del documento standard, ovvero non implementa l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaccia, è necessario impostare un blocco di modifica personalizzato. Ad esempio, in una procedura guidata, un documento viene modificato senza essere aperto in un editor. Affinché i blocchi del documento vengano aperti da procedure guidate e entità simili, è necessario che tali entità implementino l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaccia. Per registrare il titolare del blocco del documento, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metodo e passare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementazione. In questo modo viene aggiunto il titolare del blocco del documento a RDT. Un altro scenario per implementare un contenitore di blocco del documento è se si apre un documento tramite una speciale finestra degli strumenti. In questo caso, non è possibile fare in modo che la finestra degli strumenti chiuda il documento. Tuttavia, registrando come contenitore di blocco del documento in RDT, l'IDE può chiamare l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> metodo per richiedere una chiusura del documento.  
  
## <a name="other-uses-of-the-running-document-table"></a>Altri usi della tabella documenti in esecuzione  
 Altre entità nell'IDE usano RDT per ottenere informazioni sui documenti. Ad esempio, il gestore del controllo del codice sorgente USA RDT per indicare al sistema di ricaricare un documento nell'editor, dopo aver ottenuto la versione più recente del file. A tale scopo, gestione controllo codice sorgente Cerca i file in RDT per verificare se uno di essi è aperto. In caso affermativo, il gestore del controllo del codice sorgente verifica prima di tutto che la gerarchia implementi il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo. Se il progetto non implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo, il gestore del controllo del codice sorgente verifica direttamente la presenza di un'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> metodo sull'oggetto dati del documento.  
  
 L'IDE usa anche RDT per ricreare un documento aperto, ovvero portarlo in primo piano, se un utente richiede il documento. Per ulteriori informazioni, vedere [visualizzazione di file tramite il comando Apri file](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Per determinare se un file è aperto in RDT, eseguire una delle operazioni seguenti.  
  
- Eseguire una query per il moniker del documento, ovvero il percorso completo del documento, per verificare se l'elemento è aperto.  
  
- Usare la gerarchia o l'ID elemento per chiedere al sistema del progetto il percorso completo del documento, quindi cercare l'elemento nella RDT.  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)   
 [Salvataggio permanente e tabella documenti in esecuzione](../../extensibility/internals/persistence-and-the-running-document-table.md)
