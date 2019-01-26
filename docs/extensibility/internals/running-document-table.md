---
title: Esecuzione di tabella Document | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da0ec7eb05c27c3c5f78a4337f2df508b3f3e0ce
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54945905"
---
# <a name="running-document-table"></a>Tabella documenti in esecuzione
L'IDE gestisce l'elenco di tutti i documenti attualmente aperti in una struttura interna denominata tabella documenti in esecuzione (RDT). Questo elenco include tutti i documenti aperti in memoria, indipendentemente dal fatto che questi documenti sono attualmente in corso di modifica. Un documento è qualsiasi elemento che viene reso persistente, inclusi i file in un progetto o file di progetto principale (ad esempio, un file con estensione vcxproj).  
  
## <a name="elements-of-the-running-document-table"></a>Elementi della tabella documenti in esecuzione  
 La tabella documenti in esecuzione contiene le voci seguenti.  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Moniker di documento|Stringa che identifica in modo univoco l'oggetto dati del documento. Questo potrebbe essere il percorso file assoluto per un sistema di progetto che gestisce i file (ad esempio, C:\MyProject\MyFile). Questa stringa viene utilizzata anche per i progetti salvati in archivi diversi da file System, ad esempio stored procedure in un database. In questo caso, il sistema di progetto poter inventare una stringa univoca che può riconoscere e possibilmente analizza per determinare come archiviare il documento.|  
|Proprietario di gerarchia|L'oggetto gerarchia che possiede il documento, come rappresentato da un <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfaccia.|  
|ID dell'elemento|Identificatore dell'elemento di un elemento specifico all'interno della gerarchia. Questo valore è univoco tra tutti i documenti nella gerarchia che possiede questo documento, ma questo valore non deve necessariamente essere univoco in gerarchie diverse.|  
|Oggetto dati del documento|Come minimo, si tratta di un `IUnknown`<br /><br /> . L'IDE non richiede alcuna interfaccia specifica oltre il `IUnknown` interfaccia per l'oggetto dati del documento dell'editor personalizzato. Tuttavia, per un editor standard, implementazione dell'editor del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> interfaccia è necessaria per gestire le chiamate di persistenza file dal progetto. Per altre informazioni, vedere [salvataggio un documento Standard](../../extensibility/internals/saving-a-standard-document.md).|  
|Flag|Flag che controllano se il documento viene salvato, se viene applicato un blocco di lettura o di modifica e così via, può essere specificati quando le voci vengono aggiunte a RDT. Per altre informazioni, vedere l'enumerazione <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|  
|Conteggio dei blocchi di modifica|Numero di blocchi di modifica. Un blocco di modifica indica che alcuni editor presenta il documento aperto per la modifica. Quando il numero di blocchi di modifica esegue la transizione a zero, l'utente viene richiesto di salvare il documento, se è stato modificato. Ad esempio, ogni volta che si apre un documento in un editor utilizzando la **nuova finestra** comando, viene aggiunto un blocco di modifica per il documento in RDT. Affinché un blocco di modifica da impostare, il documento deve avere una gerarchia o ID elemento|  
|Conteggio dei blocchi in lettura|Conteggio dei blocchi in lettura. Un blocco di lettura indica che il documento viene letto tramite un meccanismo, ad esempio una procedura guidata. Un blocco di lettura contiene un documento attivo nella RDT continuando a indicare che il documento non può essere modificato. È possibile impostare un blocco di lettura, anche se il documento non dispone di una gerarchia o ID elemento Questa funzionalità consente di aprire un documento in memoria e immetterlo nella tabella RDT senza il documento di diventare proprietario di qualsiasi gerarchia. Questa funzionalità viene usata raramente.|  
|Contenitore del blocco|Un'istanza di un <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaccia. Il contenitore del blocco viene implementato dalle funzionalità, quali procedure guidate che aprire e modificano i documenti all'esterno di un editor. La funzionalità aggiungere un blocco di modifica al documento per impedire che il documento in fase di chiusura mentre è ancora in corso di modifica consente a un contenitore del blocco. In genere, modificare i blocchi vengono aggiunti solo per le finestre dei documenti (vale a dire, gli editor).|  
  
 Ogni voce nella tabella RDT presenta una gerarchia univoco o l'ID di elemento associato, che corrisponde in genere a un nodo del progetto. Tutti i documenti disponibili per la modifica sono in genere proprietà di una gerarchia. Le voci create nella RDT controllano quale progetto, o, in modo più accurato, gerarchia, in cui è attualmente proprietaria l'oggetto dati del documento in fase di modifica. Utilizzando le informazioni nella tabella RDT, l'IDE può impedire un documento viene aperto da più di un progetto alla volta.  
  
 La gerarchia anche controlla la persistenza dei dati e Usa le informazioni nella tabella RDT per aggiornare il **salvare** e **Salva con nome** finestre di dialogo. Quando l'utente modifica un documento e quindi scegliere il **Exit** dalle **File** menu, l'IDE viene richiesto con il **Salva modifiche** finestra di dialogo per visualizzare tutti i progetti e gli elementi di progetto che attualmente vengono modificati. Ciò consente agli utenti di scegliere quale di questi documenti da salvare. L'elenco di elementi da salvare (vale a dire, i documenti che contengono modifiche) viene generato da RDT. Tutti gli elementi che si prevedono di vedere nel **Save Changes** finestra di dialogo al momento di uscire dall'applicazione deve avere i record nella tabella RDT. RDT coordina i documenti vengono salvati e indica se viene richiesto all'utente su un salvataggio operazione utilizzando i valori specificati nella voce del flag per ogni documento. Per altre informazioni sui flag RDT, vedere il <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> enumerazione.  
  
## <a name="edit-locks-and-read-locks"></a>Blocchi di modifica e blocchi di lettura  
 I blocchi di modifica e i blocchi in lettura si trovano nella RDT. L'incrementi di finestra di documento e decrementa di blocco della modifica. Di conseguenza, quando un utente apre una nuova finestra del documento, il blocco di modifica conteggio incrementa di uno. Quando il numero di blocchi di modifica raggiunge lo zero, la gerarchia viene segnalata per rendere persistente o Salva i dati per il documento associato. La gerarchia può quindi rendere persistenti i dati in alcun modo, incluso il salvataggio come file o come un elemento in un repository. È possibile usare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> metodo nella <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> interfaccia per aggiungere blocchi di modifica e leggere i blocchi e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> metodo per rimuovere tali blocchi.  
  
 In genere, quando viene creata un'istanza di finestra del documento per un editor, il frame della finestra aggiunge automaticamente un blocco di modifica per il documento in RDT. Tuttavia, se si crea una visualizzazione personalizzata di un documento che non usa una finestra del documento standard (vale a dire, non implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> interfaccia), quindi è necessario impostare il proprio blocco di modifica. In una procedura guidata, ad esempio, un documento viene modificato senza viene aperto in un editor. Affinché blocchi del documento da aprire per le procedure guidate e le entità simili, è necessario implementare queste entità di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> interfaccia. Per registrare il contenitore del blocco del documento, chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> metodo e passare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> implementazione. In questo modo viene aggiunto il contenitore del blocco del documento a RDT. Un altro scenario per l'implementazione di un contenitore del blocco del documento è se si apre un documento tramite una finestra degli strumenti speciali. In questo caso, non si riesce a chiudere il documento di finestra degli strumenti. Tuttavia, con la registrazione come un contenitore del blocco del documento in RDT, l'IDE può chiamare l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> metodo per richiedere una chiusura del documento.  
  
## <a name="other-uses-of-the-running-document-table"></a>Altri usi della tabella documenti in esecuzione  
 Altre entità nell'IDE di utilizzare RDT per ottenere informazioni sui documenti. Ad esempio, il gestore di controllo di origine Usa RDT per indicare al sistema per ricaricare un documento nell'editor, dopo che ottiene la versione più recente del file. A tale scopo, il gestore di controllo sorgente cerca i file in RDT per verificare se uno di essi siano aperto. Se si trovano, quindi verifica innanzitutto la gestione di controllo di origine per verificare che la gerarchia implementi il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> (metodo). Se il progetto non implementa il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo, quindi l'origine controllano i controlli di gestione per l'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> metodo direttamente l'oggetto dati del documento.  
  
 L'IDE Usa anche RDT per resurface (portare in primo piano) un documento aperto, se un utente richiede che il documento. Per altre informazioni, vedere [i file di visualizzazione utilizzando il comando File Apri](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Per determinare se un file è aperto in RDT, effettuare una delle seguenti.  
  
-   Eseguire una query per il moniker del documento (ovvero, il percorso del documento completo) scoprire se l'elemento è aperto.  
  
-   Usare l'ID gerarchia o l'elemento per porre il sistema di progetto per il percorso completo di documenti e quindi cercare l'elemento nella RDT.  
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Rdt_readlock](../../extensibility/internals/rdt-readlock-usage.md)   
 [Salvataggio permanente e tabella documenti in esecuzione](../../extensibility/internals/persistence-and-the-running-document-table.md)