---
title: Caricamento ritardato dei documenti | Microsoft Docs
description: Informazioni sul caricamento ritardato dei documenti in Visual Studio e su come codificare le estensioni in modo che non eseentassi di query sugli elementi di un documento prima che venga caricato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 63fd214225d1999d53c1ff696803499eba9c4b8a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063447"
---
# <a name="delayed-document-loading"></a>Caricamento ritardato dei documenti

Quando un utente riapre una Visual Studio soluzione, la maggior parte dei documenti associati non viene caricata immediatamente. La cornice della finestra del documento viene creata in uno stato di inizializzazione in sospeso e un documento segnaposto (denominato frame stub) viene inserito nella tabella RDT (Running Document Table).

L'estensione può causare il caricamento non necessario dei documenti di progetto tramite query su elementi nei documenti prima del caricamento, con un possibile aumento del footprint di memoria complessivo per Visual Studio.

## <a name="document-loading"></a>Caricamento di documenti

Il frame e il documento dello stub vengono inizializzati completamente quando l'utente accede al documento, ad esempio selezionando la scheda della cornice della finestra. Il documento può anche essere inizializzato da un'estensione che richiede i dati del documento, accedendo direttamente a RDT per acquisire i dati del documento o accedendo indirettamente a RDT effettuando una delle chiamate seguenti:

- Metodo della cornice <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> della finestra.

- Il metodo frame <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> della finestra in una delle proprietà seguenti:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Se l'estensione usa codice gestito, è consigliabile non chiamare a meno che non si sia certi che il documento non si trova nello stato di inizializzazione in sospeso o non si desidera che il documento sia <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> completamente inizializzato. Il motivo è che il metodo restituisce sempre l'oggetto dati doc, creandolo se necessario. È invece necessario chiamare uno dei metodi `IVsRunningDocumentTable4` sull'interfaccia .

- Se l'estensione usa C++, è possibile `null` passare per i parametri non desiderati.

- È possibile evitare il caricamento di documenti non necessari chiamando uno dei metodi seguenti prima di richiedere le proprietà pertinenti prima di richiedere altre proprietà:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> usando [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Questo metodo restituisce un <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> oggetto che include un valore per [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) se il documento non è ancora stato inizializzato.

È possibile scoprire quando un documento è stato caricato sottoscrivendo l'evento RDT generato quando un documento è completamente inizializzato. Esistono due possibilità:

- Se il sink di evento implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> , è possibile sottoscrivere <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,

- In caso contrario, è possibile sottoscrivere <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .

L'esempio seguente è un ipotetico scenario di accesso ai documenti: un'estensione Visual Studio vuole visualizzare alcune informazioni sui documenti aperti, ad esempio il numero di blocchi di modifica e qualcosa sui dati del documento. Enumera i documenti in RDT usando , quindi chiama per ogni documento per recuperare il numero di blocchi di modifica e <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> i dati del documento. Se il documento si trova nello stato di inizializzazione in sospeso, la richiesta dei dati del documento ne determina l'inizializzazione inutilmente.

Un modo più efficiente per accedere a un documento è usare per ottenere il conteggio dei blocchi di modifica e quindi usare per determinare se il documento <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> è stato inizializzato. Se i flag non includono [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), il documento è già stato inizializzato e la richiesta dei dati del documento con non causa <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> alcuna inizializzazione non necessaria. Se i flag includono [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), l'estensione deve evitare di richiedere i dati del documento fino a quando il documento non viene inizializzato. Questa inizializzazione può essere rilevata nel `OnAfterAttributeChange(Ex)` gestore eventi .

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Testare le estensioni per verificare se forzano l'inizializzazione

Non esiste alcun segnale visibile per indicare se un documento è stato inizializzato, quindi può essere difficile scoprire se l'estensione forza l'inizializzazione. È possibile impostare una chiave del Registro di sistema che semplifica la verifica, perché fa sì che il titolo di ogni documento non completamente inizializzato abbia il testo *[Stub]* nel titolo.

In **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad** impostare **StubTabTitleFormatString** su *{0} [Stub]*.
