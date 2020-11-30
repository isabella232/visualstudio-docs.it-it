---
title: Caricamento ritardato dei documenti | Microsoft Docs
description: Informazioni sul caricamento ritardato dei documenti in Visual Studio e sulle estensioni di codice in modo che non eseguano query sugli elementi di un documento prima di caricarli.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6489c819efe0fd29cd2d120c08414cf0532ad6f
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328392"
---
# <a name="delayed-document-loading"></a>Caricamento ritardato dei documenti

Quando un utente riapre una soluzione di Visual Studio, la maggior parte dei documenti associati non viene caricata immediatamente. La cornice della finestra del documento viene creata in uno stato di inizializzazione in sospeso e un documento segnaposto (denominato frame dello stub) viene inserito nella tabella documenti in esecuzione (RDT).

L'estensione può causare il caricamento inutilmente dei documenti del progetto eseguendo una query sugli elementi nei documenti prima che vengano caricati, che possono aumentare il footprint di memoria complessivo per Visual Studio.

## <a name="document-loading"></a>Caricamento di documenti

Il frame e il documento dello stub vengono inizializzati completamente quando l'utente accede al documento, ad esempio selezionando la scheda della cornice della finestra. Il documento può anche essere inizializzato da un'estensione che richiede i dati del documento, accedendo direttamente a RDT per acquisire i dati del documento oppure accedendo al RDT indirettamente effettuando una delle chiamate seguenti:

- Metodo della cornice della finestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .

- Il metodo della cornice della finestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> su una delle proprietà seguenti:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Se l'estensione usa codice gestito, è consigliabile non chiamare, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a meno che non si sia certi che il documento non sia nello stato di inizializzazione in sospeso o che si voglia che il documento sia completamente inizializzato. Il motivo è che il metodo restituisce sempre l'oggetto dati del documento, creandolo se necessario. Al contrario, è necessario chiamare uno dei metodi nell' `IVsRunningDocumentTable4` interfaccia.

- Se l'estensione USA C++, è possibile passare `null` per i parametri non desiderati.

- È possibile evitare il caricamento di documenti superflui chiamando uno dei metodi seguenti prima di richiedere le proprietà pertinenti prima di richiedere altre proprietà:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> utilizzando [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Questo metodo restituisce un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> oggetto che include un valore per [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) se il documento non è ancora stato inizializzato.

È possibile scoprire quando un documento è stato caricato sottoscrivendo l'evento RDT generato quando un documento viene inizializzato completamente. Esistono due possibilità:

- Se il sink di evento implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , è possibile sottoscrivere <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,

- In caso contrario, è possibile effettuare la sottoscrizione a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .

L'esempio seguente è un ipotetico scenario di accesso ai documenti: un'estensione di Visual Studio vuole visualizzare alcune informazioni sui documenti aperti, ad esempio il conteggio dei blocchi di modifica e qualcosa sui dati del documento. Enumera i documenti in RDT usando <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> , quindi chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> per ogni documento per recuperare il conteggio dei blocchi di modifica e i dati del documento. Se il documento è nello stato di inizializzazione in sospeso, la richiesta dei dati del documento ne causa l'inizializzazione inutilmente.

Un modo più efficiente per accedere a un documento consiste nell'usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> per ottenere il numero di blocchi di modifica e quindi usare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> per determinare se il documento è stato inizializzato. Se i flag non includono [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), il documento è già stato inizializzato e la richiesta dei dati del documento con <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> non provoca alcuna inizializzazione non necessaria. Se i flag includono [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), l'estensione deve evitare di richiedere i dati del documento fino all'inizializzazione del documento. Questa inizializzazione può essere rilevata nel `OnAfterAttributeChange(Ex)` gestore eventi.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Estensioni di test per verificare se forzano l'inizializzazione

Non esiste alcuna indicazione visibile per indicare se un documento è stato inizializzato, pertanto può essere difficile determinare se l'estensione sta forzando l'inizializzazione. È possibile impostare una chiave del registro di sistema che rende più semplice la verifica, in quanto causa il titolo di ogni documento non inizializzato completamente per avere il testo *[Stub]* nel titolo.

In **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad** impostare **StubTabTitleFormatString** su *{0} [Stub]*.
