---
title: Caricamento ritardato dei documenti Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f78d49013c1f0bd359d4439b73620a159a9ccc0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708818"
---
# <a name="delayed-document-loading"></a>Caricamento ritardato dei documenti

Quando un utente riapre una soluzione di Visual Studio, la maggior parte dei documenti associati non vengono caricati immediatamente. La cornice della finestra del documento viene creata in uno stato di inizializzazione in sospeso e un documento segnaposto (denominato frame stub) viene inserito nella tabella documento in esecuzione (RDT).

L'estensione può causare il caricamento inutilmente dei documenti di progetto eseguendo una query sugli elementi nei documenti prima che vengano caricati, con conseguente aumento del footprint di memoria complessivo per Visual Studio.

## <a name="document-loading"></a>Caricamento dei documenti

Il frame e il documento stub vengono inizializzati completamente quando l'utente accede al documento, ad esempio selezionando la scheda della cornice della finestra. Il documento può anche essere inizializzato da un'estensione che richiede i dati del documento, accedendo direttamente a RDT per acquisire i dati del documento o accedendo indirettamente a RDT effettuando una delle seguenti chiamate:

- Metodo della <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> cornice della finestra.

- Il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> cornice della finestra in una delle seguenti proprietà:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Se l'estensione utilizza codice gestito, non è consigliabile chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> a meno che non si sia certi che il documento non si trovi nello stato di inizializzazione in sospeso o si desideri che il documento sia completamente inizializzato. Il motivo è che il metodo restituisce sempre l'oggetto dati doc, creandolo se necessario. Al contrario, è necessario chiamare `IVsRunningDocumentTable4` uno dei metodi sull'interfaccia.

- Se l'estensione utilizza il linguaggio C, è possibile passare `null` per i parametri non desiderati.

- È possibile evitare il caricamento di documenti non necessari chiamando uno dei seguenti metodi prima di richiedere le proprietà rilevanti prima di richiedere altre proprietà:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>utilizzando [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Questo metodo <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> restituisce un oggetto che include un valore per [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) se il documento non è ancora stato inizializzato.

È possibile scoprire quando un documento è stato caricato sottoscrivendo l'evento RDT che viene generato quando un documento è completamente inizializzato. Ci sono due possibilità:

- Se il sink <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>di evento <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>implementa , è possibile sottoscrivere ,

- In caso contrario, è possibile iscriversi a <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.

L'esempio seguente è un ipotetico scenario di accesso ai documenti: un'estensione di Visual Studio desidera visualizzare alcune informazioni sui documenti aperti, ad esempio il conteggio dei blocchi di modifica e qualcosa sui dati del documento. Enumera i documenti in RDT <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>utilizzando <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> , quindi chiama per ogni documento per recuperare il conteggio dei blocchi di modifica e i dati del documento. Se il documento si trova nello stato di inizializzazione in sospeso, la richiesta dei dati del documento ne determina l'inizializzazione inutilmente.

Un modo più efficiente di accedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> a un documento consiste nell'utilizzare per ottenere il conteggio dei blocchi di modifica e quindi utilizzare <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> per determinare se il documento è stato inizializzato. Se i flag non includono [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), il documento è già stato inizializzato <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> e la richiesta dei dati del documento con non causa alcuna inizializzazione non necessaria. Se i flag includono [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), l'estensione deve evitare di richiedere i dati del documento fino a quando il documento non viene inizializzato. Questa inizializzazione può `OnAfterAttributeChange(Ex)` essere rilevata nel gestore eventi.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Testare le estensioni per verificare se forzano l'inizializzazioneTest extensions to see if they force initialization

Non vi è alcun segnale visibile per indicare se un documento è stato inizializzato, quindi può essere difficile scoprire se l'estensione sta forzando l'inizializzazione. È possibile impostare una chiave del Registro di sistema che semplifica la verifica, perché fa sì che il titolo di ogni documento che non è completamente inizializzato per avere il testo *[Stub]* nel titolo.

In **HKEY_CURRENT_USER software , Microsoft VisualStudio 14.0 ,** impostare **StubTabTitleFormatString** su * {0} [Stub]*.
