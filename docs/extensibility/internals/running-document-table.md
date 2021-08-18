---
title: Esecuzione della tabella documenti | Microsoft Docs
description: Informazioni su come l Visual Studio IDE gestisce la tabella di documenti in esecuzione, che include tutti i documenti aperti in memoria.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- read locks
- running document table (RDT), IVsDocumentLockHolder interface
- running document table (RDT)
- running document table (RDT), edit locks
- document data objects, running document table
ms.assetid: bbec74f3-dd8e-48ad-99c1-2df503c15f5a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b087ab396920cbf25d0559b74915a17606b472ee
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049584"
---
# <a name="running-document-table"></a>Tabella documenti in esecuzione
L'IDE gestisce l'elenco di tutti i documenti attualmente aperti in una struttura interna denominata tabella di documenti in esecuzione (RDT). Questo elenco include tutti i documenti aperti in memoria, indipendentemente dal fatto che questi documenti siano in fase di modifica. Un documento è qualsiasi elemento persistente, inclusi i file in un progetto o il file di progetto principale (ad esempio, un file con estensione vcxproj).

## <a name="elements-of-the-running-document-table"></a>Elementi della tabella documento in esecuzione
 La tabella dei documenti in esecuzione contiene le voci seguenti.

|Elemento|Descrizione|
|-------------|-----------------|
|Moniker documento|Stringa che identifica in modo univoco l'oggetto dati del documento. Si tratta del percorso file assoluto per un sistema di progetto che gestisce i file, ad esempio C:\MyProject\MyFile. Questa stringa viene utilizzata anche per i progetti salvati in archivi diversi dai file system, ad esempio le stored procedure in un database. In questo caso, il sistema del progetto può inventare una stringa univoca che può riconoscere ed eventualmente analizzare per determinare come archiviare il documento.|
|Proprietario della gerarchia|Oggetto gerarchia proprietario del documento, come rappresentato da <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> un'interfaccia.|
|ID elemento|Identificatore di elemento per un elemento specifico all'interno della gerarchia. Questo valore è univoco tra tutti i documenti della gerarchia proprietaria di questo documento, ma non è garantito che sia univoco in gerarchie diverse.|
|Oggetto dati del documento|Come minimo, si tratta di un `IUnknown`<br /><br /> . L'IDE non richiede alcuna interfaccia specifica oltre l'interfaccia per l'oggetto dati documento di un `IUnknown` editor personalizzato. Tuttavia, per un editor standard, l'implementazione dell'interfaccia dell'editor è necessaria per gestire le chiamate di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> persistenza dei file dal progetto. Per altre informazioni, vedere [Salvataggio di un documento standard.](../../extensibility/internals/saving-a-standard-document.md)|
|Flags|I flag che controllano se il documento viene salvato, se viene applicato un blocco di lettura o modifica e così via, possono essere specificati quando vengono aggiunte voci al file RDT. Per altre informazioni, vedere l'enumerazione <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|
|Modifica conteggio blocchi|Numero di blocchi di modifica. Un blocco di modifica indica che in alcuni editor il documento è aperto per la modifica. Quando il numero di blocchi di modifica passa a zero, all'utente viene richiesto di salvare il documento, se è stato modificato. Ad esempio, ogni volta che si apre  un documento in un editor usando il comando Nuova finestra, viene aggiunto un blocco di modifica per tale documento in RDT. Per impostare un blocco di modifica, il documento deve avere una gerarchia o un ID elemento.|
|Conteggio blocchi di lettura|Conteggio dei blocchi di lettura. Un blocco di lettura indica che il documento viene letto tramite un meccanismo, ad esempio una procedura guidata. Un blocco di lettura mantiene attivo un documento in RDT, a indicare che il documento non può essere modificato. È possibile impostare un blocco di lettura anche se il documento non dispone di una gerarchia o di un ID elemento. Questa funzionalità consente di aprire un documento in memoria e immetterlo nel file RDT senza che il documento sia di proprietà di alcuna gerarchia. Questa funzionalità viene usata raramente.|
|Titolare del blocco|Istanza di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> un'interfaccia. Il titolare del blocco viene implementato da funzionalità quali le procedure guidate che aprono e modificano documenti all'esterno di un editor. Un segnaposto di blocco consente alla funzionalità di aggiungere un blocco di modifica al documento per impedire che il documento venga chiuso mentre è ancora in fase di modifica. In genere, i blocchi di modifica vengono aggiunti solo dalle finestre dei documenti, ovvero dagli editor.|

 A ogni voce in RDT è associata una gerarchia univoca o un ID elemento, che in genere corrisponde a un nodo nel progetto. Tutti i documenti disponibili per la modifica sono in genere di proprietà di una gerarchia. Le voci effettuate nel controllo RDT controllano quale progetto o, più precisamente, quale gerarchia è attualmente proprietaria dell'oggetto dati del documento in fase di modifica. Usando le informazioni in RDT, l'IDE può impedire l'apertura di un documento da più di un progetto alla volta.

 La gerarchia controlla anche la persistenza dei dati e usa le informazioni in RDT per aggiornare le finestre di **dialogo** Salva e **Salva** con nome. Quando gli utenti modificano  un documento e quindi scelgono il comando  Esci dal menu **File,** l'IDE li richiede con la finestra di dialogo Salva modifiche per visualizzare tutti i progetti e gli elementi di progetto attualmente modificati. In questo modo gli utenti possono scegliere i documenti da salvare. L'elenco dei documenti da salvare(ovvero i documenti con modifiche) viene generato da RDT. Tutti gli elementi che si prevede di visualizzare nella finestra **di** dialogo Salva modifiche all'uscita dall'applicazione devono avere record nel file RDT. RdT coordina i documenti salvati e indica se all'utente viene richiesto di eseguire un'operazione di salvataggio usando i valori specificati nella voce Flag per ogni documento. Per altre informazioni sui flag RDT, vedere <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> l'enumerazione .

## <a name="edit-locks-and-read-locks"></a>Modificare blocchi e blocchi di lettura
 I blocchi di modifica e di lettura risiedono nel file RDT. La finestra del documento incrementa e decrementa il blocco di modifica. Pertanto, quando un utente apre una nuova finestra del documento, il conteggio dei blocchi di modifica viene incrementato di uno. Quando il numero di blocchi di modifica raggiunge lo zero, la gerarchia viene segnalata per rendere persistenti o salvare i dati per il documento associato. La gerarchia può quindi rendere persistenti i dati in qualsiasi modo, inclusa la persistenza come file o come elemento in un repository. È possibile usare il metodo nell'interfaccia per aggiungere blocchi di modifica e di lettura e il <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> metodo per rimuovere questi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> blocchi.

 In genere, quando viene creata un'istanza della finestra del documento per un editor, la cornice della finestra aggiunge automaticamente un blocco di modifica per il documento in RDT. Tuttavia, se si crea una visualizzazione personalizzata di un documento che non usa una finestra standard del documento (ovvero non implementa l'interfaccia ), è necessario impostare un blocco di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> modifica personalizzato. In una procedura guidata, ad esempio, un documento viene modificato senza essere aperto in un editor. Per consentire l'apertura dei blocchi ai documenti da parte di procedure guidate ed entità simili, queste entità devono implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> l'interfaccia . Per registrare il titolare del blocco del documento, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> il metodo e passare l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> . In questo modo, il titolare del blocco del documento viene aggiunto a RDT. Un altro scenario per l'implementazione di un titolare del blocco del documento è l'apertura di un documento tramite una finestra degli strumenti speciale. In questo caso, non è possibile fare in modo che la finestra degli strumenti chiuda il documento. Tuttavia, registrando come titolare del blocco del documento in RDT, l'IDE può chiamare l'implementazione del metodo per richiedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> una chiusura del documento.

## <a name="other-uses-of-the-running-document-table"></a>Altri usi della tabella documenti in esecuzione
 Altre entità nell'IDE usano RDT per ottenere informazioni sui documenti. Ad esempio, la gestione del controllo del codice sorgente usa RDT per indicare al sistema di ricaricare un documento nell'editor, dopo aver ottenuto la versione più recente del file. A tale scopo, Gestione controllo codice sorgente cerca i file nel file RDT per verificare se uno di essi è aperto. In caso contrario, la gestione del controllo del codice sorgente verifica innanzitutto che la gerarchia implementi il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo . Se il progetto non implementa il metodo , gestione controllo codice sorgente verifica direttamente la presenza di un'implementazione del metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> nell'oggetto dati del documento.

 L'IDE usa anche RDT per riaccesare (portare in primo piano) un documento aperto, se un utente lo richiede. Per altre informazioni, vedere [Visualizzazione di file tramite il comando Apri file](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Per determinare se un file è aperto in RDT, eseguire una delle operazioni seguenti.

- Eseguire una query per il moniker del documento, ovvero il percorso completo del documento, per verificare se l'elemento è aperto.

- Usare l'ID della gerarchia o dell'elemento per chiedere al sistema del progetto il percorso completo del documento e quindi cercare l'elemento in RDT.

## <a name="see-also"></a>Vedi anche
- [Uso di RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Salvataggio permanente e tabella documenti in esecuzione](../../extensibility/internals/persistence-and-the-running-document-table.md)
