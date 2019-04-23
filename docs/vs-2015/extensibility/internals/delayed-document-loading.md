---
title: Caricamento dei documenti ritardato | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116927"
---
# <a name="delayed-document-loading"></a>Caricamento dei documenti ritardato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando un utente riapre una soluzione di Visual Studio, è possibile che la maggior parte dei documenti associati non vengono caricata contemporaneamente. La cornice della finestra documento viene creata in uno stato in sospeso-initialization, e un documento di segnaposto (denominato frame dello stub) viene inserito nel documento di tabella in esecuzione (RDT).  
  
 L'estensione può causare i documenti di progetto da caricare inutilmente eseguendo una query di elementi nei documenti prima che vengano caricati. Questo può accrescere il footprint di memoria complessiva per Visual Studio.  
  
## <a name="document-loading"></a>Caricamento dei documenti  
 L'intervallo di stub e un documento completamente vengono inizializzati quando l'utente accede al documento, ad esempio selezionando la scheda della cornice della finestra. Il documento può inoltre essere inizializzato da un'estensione che richiede i dati del documento, l'accesso a RDT direttamente per acquisire i dati del documento o l'accesso a RDT indirettamente effettuando una delle chiamate di seguenti:  
  
- La cornice della finestra il metodo show: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
- La cornice della finestra metodo GetProperty <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> su una delle seguenti proprietà:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Se l'estensione utilizza il codice gestito, non chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a meno che non si è certi che il documento non è nello stato in sospeso-initialization, o si desidera che il documento sia completamente inizializzata... Infatti, questo metodo restituisce sempre la documentazione di oggetto dati, creandone una se necessario. In alternativa, è necessario chiamare uno dei metodi nell'interfaccia IVsRunningDocumentTable4.  
  
  Se l'estensione utilizza C++, è possibile passare `null` per i parametri non desiderate.  
  
  È possibile evitare il caricamento di documenti non necessari chiamando uno dei metodi seguenti prima di richiedere per le proprietà rilevanti: prima di richiedere per le altre proprietà.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> usando <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Questo metodo restituisce un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> oggetto che include un valore per <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> se il documento non è ancora stato inizializzato.  
  
  È possibile scoprire quando un documento è stato caricato, sottoscrivere l'evento RDT che viene generato quando un documento è completamente inizializzato. Esistono due possibilità:  
  
- Se l'evento sink implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, è possibile sottoscrivere <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
- In caso contrario, è possibile sottoscrivere <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
  Di seguito è uno scenario di accesso documento ipotetico. Visual Studio estensione da visualizzare alcune informazioni sui documenti aperti, ad esempio la modifica è bloccare count e qualche informazione sui dati del documento. Enumera i documenti nella RDT utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, quindi chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> per ogni documento per poter recuperare i dati di conteggio e documento di blocco modifica. Se il documento è nello stato in sospeso-initialization, che richiede i dati del documento ne determina inutilmente da inizializzare.  
  
  Un modo più efficace di procedere consiste nell'usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> per ottenere il conteggio dei blocchi di modifica e quindi usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> per determinare se il documento è stato inizializzato. Se non includono i flag <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, il documento è già stato inizializzato e che richiede i dati del documento con <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> non fa in modo che tutte le inizializzazioni non necessarie. Se si include il flag <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, l'estensione deve evitare di richiedere i dati del documento fino a quando non viene inizializzato il documento. Può essere rilevato nel gestore dell'evento OnAfterAttributeChange(Ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Le estensioni per vedere se sono forzare l'inizializzazione di test  
 Non vi è alcuna indicazione visibile per indicare se un documento è stato inizializzato, pertanto può essere difficile scoprire se l'estensione viene forzato l'inizializzazione. È possibile impostare una chiave del Registro di sistema che semplifica la verifica, perché causa il titolo di tutti i documenti non completamente inizializzata per contenere il testo `[Stub]` nel titolo.  
  
 Nelle **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]**, impostare **StubTabTitleFormatString** al  **{0} [Stub]**.
