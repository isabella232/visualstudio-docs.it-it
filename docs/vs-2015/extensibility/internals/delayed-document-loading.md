---
title: Caricamento ritardato dei documenti | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196864"
---
# <a name="delayed-document-loading"></a>Caricamento dei documenti ritardato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando un utente riapre una soluzione di Visual Studio, la maggior parte dei documenti associati non viene caricata immediatamente. La cornice della finestra del documento viene creata in uno stato di inizializzazione in sospeso e un documento segnaposto (denominato frame dello stub) viene inserito nella tabella documenti in esecuzione (RDT).  
  
 L'estensione può causare il caricamento inutilmente dei documenti del progetto eseguendo una query sugli elementi nei documenti prima che vengano caricati. Questo può aumentare il footprint di memoria complessivo per Visual Studio.  
  
## <a name="document-loading"></a>Caricamento di documenti  
 Il frame e il documento dello stub vengono inizializzati completamente quando l'utente accede al documento, ad esempio selezionando la scheda della cornice della finestra. Il documento può anche essere inizializzato da un'estensione che richiede i dati del documento, accedendo direttamente a RDT per acquisire i dati del documento oppure accedendo al RDT indirettamente effettuando una delle chiamate seguenti:  
  
- Il metodo di visualizzazione frame della finestra: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .  
  
- Il metodo GetProperty della cornice della finestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> su una delle proprietà seguenti:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Se l'estensione usa codice gestito, è consigliabile non chiamare, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a meno che non si sia certi che il documento non si trovi nello stato di inizializzazione in sospeso o che si desideri che il documento sia completamente inizializzato. Questo è dovuto al fatto che questo metodo restituisce sempre l'oggetto dati del documento, creandolo se necessario. Al contrario, è necessario chiamare uno dei metodi sull'interfaccia IVsRunningDocumentTable4.  
  
  Se l'estensione USA C++, è possibile passare `null` per i parametri non desiderati.  
  
  È possibile evitare il caricamento di documenti superflui chiamando uno dei metodi seguenti prima di richiedere le proprietà pertinenti: prima di richiedere altre proprietà.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Questo metodo restituisce un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> oggetto che include un valore per <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> se il documento non è ancora stato inizializzato.  
  
  È possibile scoprire quando un documento è stato caricato sottoscrivendo l'evento RDT generato quando un documento viene inizializzato completamente. Esistono due possibilità:  
  
- Se il sink di evento implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , è possibile sottoscrivere <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,  
  
- In caso contrario, è possibile effettuare la sottoscrizione a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .  
  
  Di seguito è riportato uno scenario ipotetico di accesso ai documenti. Un'estensione di Visual Studio vuole visualizzare alcune informazioni sui documenti aperti, ad esempio il numero di blocchi di modifica e qualcosa sui dati del documento. Enumera i documenti in RDT usando <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> , quindi chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> per ogni documento per recuperare il conteggio dei blocchi di modifica e i dati del documento. Se il documento è nello stato di inizializzazione in sospeso, la richiesta dei dati del documento ne causa l'inizializzazione inutilmente.  
  
  Un modo più efficiente per eseguire questa operazione consiste nell'usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> per ottenere il numero di blocchi di modifica e quindi usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> per determinare se il documento è stato inizializzato. Se i flag non includono <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , il documento è già stato inizializzato e la richiesta dei dati del documento con <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> non provoca alcuna inizializzazione non necessaria. Se i flag includono <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , l'estensione deve evitare di richiedere i dati del documento fino all'inizializzazione del documento. Questa operazione può essere rilevata nel gestore eventi OnAfterAttributeChange (ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Test delle estensioni per verificare se forzano l'inizializzazione  
 Non esiste alcuna indicazione visibile per indicare se un documento è stato inizializzato, pertanto può essere difficile determinare se l'estensione sta forzando l'inizializzazione. È possibile impostare una chiave del registro di sistema che rende più semplice la verifica, in quanto causa il titolo di ogni documento non inizializzato completamente in modo da includere il testo `[Stub]` nel titolo.  
  
 In **HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0\backgroundsolutionload]** impostare **StubTabTitleFormatString** su ** {0} [Stub]**.
