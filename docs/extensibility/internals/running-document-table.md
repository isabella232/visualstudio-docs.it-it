---
title: Esecuzione della tabella documento | Microsoft Docs
description: Informazioni su come l Visual Studio IDE gestisce la tabella dei documenti in esecuzione, che include tutti i documenti aperti in memoria.
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
ms.workload:
- vssdk
ms.openlocfilehash: d260534d58853afc6b84ba484eb3a806250e2aa6
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900408"
---
# <a name="running-document-table"></a>Tabella documenti in esecuzione
L'IDE gestisce l'elenco di tutti i documenti attualmente aperti in una struttura interna denominata tabella di documenti in esecuzione (RDT). Questo elenco include tutti i documenti aperti in memoria, indipendentemente dal fatto che questi documenti siano attualmente in fase di modifica. Un documento è qualsiasi elemento persistente, inclusi i file in un progetto o nel file di progetto principale ,ad esempio un file con estensione vcxproj.

## <a name="elements-of-the-running-document-table"></a>Elementi della tabella documento in esecuzione
 La tabella del documento in esecuzione contiene le voci seguenti.

|Elemento|Descrizione|
|-------------|-----------------|
|Moniker di documento|Stringa che identifica in modo univoco l'oggetto dati del documento. Si tratta del percorso assoluto del file per un sistema di progetto che gestisce i file, ad esempio C:\MyProject\MyFile. Questa stringa viene usata anche per i progetti salvati in archivi diversi da file system, ad esempio stored procedure in un database. In questo caso, il sistema del progetto può inventare una stringa univoca che può riconoscere ed eventualmente analizzare per determinare come archiviare il documento.|
|Proprietario della gerarchia|Oggetto gerarchia proprietario del documento, come rappresentato da <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> un'interfaccia .|
|ID elemento|Identificatore di elemento per un elemento specifico all'interno della gerarchia. Questo valore è univoco tra tutti i documenti della gerarchia proprietaria di questo documento, ma non è garantito che questo valore sia univoco tra gerarchie diverse.|
|Oggetto dati del documento|Come minimo, si tratta di un `IUnknown`<br /><br /> . L'IDE non richiede alcuna interfaccia specifica oltre `IUnknown` l'interfaccia per l'oggetto dati documento di un editor personalizzato. Tuttavia, per un editor standard, l'implementazione dell'interfaccia dell'editor è necessaria per gestire le chiamate di persistenza <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> dei file dal progetto. Per altre informazioni, vedere [Salvataggio di un documento standard.](../../extensibility/internals/saving-a-standard-document.md)|
|Flags|I flag che controllano se il documento viene salvato, se viene applicato un blocco di lettura o modifica e così via, possono essere specificati quando vengono aggiunte voci al file RDT. Per altre informazioni, vedere l'enumerazione <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS>.|
|Modifica conteggio blocchi|Numero di blocchi di modifica. Un blocco di modifica indica che in un editor il documento è aperto per la modifica. Quando il numero di blocchi di modifica passa a zero, all'utente viene richiesto di salvare il documento, se è stato modificato. Ad esempio, ogni volta che si apre  un documento in un editor usando il comando Nuova finestra, viene aggiunto un blocco di modifica per tale documento in RDT. Per impostare un blocco di modifica, il documento deve avere una gerarchia o un ID elemento.|
|Conteggio blocchi in lettura|Numero di blocchi in lettura. Un blocco di lettura indica che il documento viene letto tramite un meccanismo, ad esempio una procedura guidata. Un blocco di lettura mantiene attivo un documento in RDT, indicando che il documento non può essere modificato. È possibile impostare un blocco di lettura anche se il documento non ha una gerarchia o un ID elemento. Questa funzionalità consente di aprire un documento in memoria e immetterlo in RDT senza che il documento sia di proprietà di alcuna gerarchia. Questa funzionalità viene usata raramente.|
|Supporto di blocco|Istanza di <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> un'interfaccia. Il titolare del blocco viene implementato da funzionalità come le procedure guidate che aprono e modificano documenti all'esterno di un editor. Un supporto di blocco consente alla funzionalità di aggiungere un blocco di modifica al documento per impedire la chiusura del documento mentre è ancora in corso di modifica. In genere, i blocchi di modifica vengono aggiunti solo dalle finestre dei documenti,ovvero dagli editor.|

 A ogni voce in RDT è associata una gerarchia univoca o un ID elemento, che in genere corrisponde a un nodo nel progetto. Tutti i documenti disponibili per la modifica sono in genere di proprietà di una gerarchia. Le voci effettuate nel controllo RDT controllano quale progetto o, più precisamente, quale gerarchia è attualmente proprietaria dell'oggetto dati del documento in fase di modifica. Usando le informazioni in RDT, l'IDE può impedire l'apertura di un documento da più di un progetto alla volta.

 La gerarchia controlla anche la persistenza dei dati e usa le informazioni in RDT per aggiornare **le** finestre di dialogo Salva **e** Salva con nome. Quando gli utenti modificano  un documento e quindi scelgono il comando  Esci dal menu **File,** l'IDE li richiede con la finestra di dialogo Salva modifiche per visualizzare tutti i progetti e gli elementi del progetto attualmente modificati. In questo modo gli utenti possono scegliere quale dei documenti salvare. L'elenco dei documenti da salvare, ovvero i documenti con modifiche, viene generato da RDT. Tutti gli elementi che si prevede di visualizzare nella finestra **di** dialogo Salva modifiche all'uscita dall'applicazione devono avere record in RDT. RdT coordina i documenti salvati e indica se all'utente viene richiesta un'operazione di salvataggio usando i valori specificati nella voce Flag per ogni documento. Per altre informazioni sui flag RDT, vedere <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS> l'enumerazione .

## <a name="edit-locks-and-read-locks"></a>Modificare blocchi e blocchi di lettura
 I blocchi di modifica e di lettura si trovano in RDT. La finestra del documento incrementa e decrementa il blocco di modifica. Di conseguenza, quando un utente apre una nuova finestra del documento, il numero di blocchi di modifica aumenta di uno. Quando il numero di blocchi di modifica raggiunge zero, la gerarchia viene segnalata per rendere persistenti o salvare i dati per il documento associato. La gerarchia può quindi rendere persistenti i dati in qualsiasi modo, inclusa la persistenza come file o come elemento in un repository. È possibile usare il metodo nell'interfaccia per aggiungere blocchi di modifica e di lettura e il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.LockDocument%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> per rimuovere questi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnlockDocument%2A> blocchi.

 In genere, quando viene creata un'istanza della finestra del documento per un editor, la cornice della finestra aggiunge automaticamente un blocco di modifica per il documento in RDT. Tuttavia, se si crea una visualizzazione personalizzata di un documento che non usa una finestra di documento standard, ovvero non implementa l'interfaccia , è necessario impostare un blocco di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> modifica personalizzato. In una procedura guidata, ad esempio, un documento viene modificato senza essere aperto in un editor. Per consentire l'apertura dei blocchi di documenti da parte di procedure guidate ed entità simili, queste entità devono implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> l'interfaccia . Per registrare il titolare del blocco del documento, chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.RegisterDocumentLockHolder%2A> il metodo e passare l'implementazione. <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder> In questo modo, il titolare del blocco del documento viene aggiunto a RDT. Un altro scenario per l'implementazione di un titolare del blocco del documento è l'apertura di un documento tramite una finestra degli strumenti speciale. In questo caso, non è possibile fare in modo che la finestra degli strumenti chiuda il documento. Tuttavia, registrando come titolare del blocco del documento in RDT, l'IDE può chiamare l'implementazione del metodo per richiedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocumentLockHolder.CloseDocumentHolder%2A> la chiusura del documento.

## <a name="other-uses-of-the-running-document-table"></a>Altri usi della tabella documento in esecuzione
 Altre entità nell'IDE usano RDT per ottenere informazioni sui documenti. Ad esempio, il gestore del controllo del codice sorgente usa RDT per indicare al sistema di ricaricare un documento nell'editor, dopo aver ottenuto la versione più recente del file. A tale scopo, gestione controllo del codice sorgente cerca i file in RDT per verificare se sono aperti. In caso contrario, il gestore del controllo del codice sorgente verifica innanzitutto che la gerarchia implementi il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo . Se il progetto non implementa il metodo , il gestore del controllo del codice sorgente verifica direttamente un'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> metodo nell'oggetto dati del <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> documento.

 L'IDE usa anche RDT per riassare (portare in primo piano) un documento aperto, se un utente lo richiede. Per altre informazioni, vedere [Visualizzazione di file tramite il comando Apri file](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Per determinare se un file è aperto in RDT, eseguire una delle operazioni seguenti.

- Eseguire una query per il moniker del documento, ovvero il percorso completo del documento, per determinare se l'elemento è aperto.

- Usare la gerarchia o l'ID elemento per chiedere al sistema del progetto il percorso completo del documento e quindi cercare l'elemento in RDT.

## <a name="see-also"></a>Vedere anche
- [Uso di RDT_ReadLock](../../extensibility/internals/rdt-readlock-usage.md)
- [Salvataggio permanente e tabella documenti in esecuzione](../../extensibility/internals/persistence-and-the-running-document-table.md)
