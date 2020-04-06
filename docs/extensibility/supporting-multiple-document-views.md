---
title: Supporto di più visualizzazioni di documento Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a952414fa7156d80675564e519e556ccedd524a3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699545"
---
# <a name="supporting-multiple-document-views"></a>Supporto di più visualizzazioni documento
È possibile fornire più di una visualizzazione di un documento creando oggetti di visualizzazione del documento e di documento separati per l'editor. Alcuni casi in cui sarebbe utile una visualizzazione documento aggiuntiva sono:

- Supporto per una nuova finestra: si desidera che l'editor fornisca due o più visualizzazioni dello stesso tipo, in modo che un utente che dispone già di una finestra aperta nell'editor possa aprire una nuova finestra selezionando il comando **Nuova finestra** dal menu **Finestra.**

- Supporto per form e visualizzazioni codice: si desidera che l'editor fornisca visualizzazioni di tipi diversi. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], ad esempio, fornisce sia una visualizzazione Form che una visualizzazione codice.

  Per altre informazioni, vedere la procedura CreateEditorInstance nel file di EditorFactory.cs nel progetto dell'editor personalizzato creato dal modello di pacchetto di Visual Studio.For more information about this, see the CreateEditorInstance procedure in the EditorFactory.cs file in the custom editor project created by the Visual Studio Package Template. Per ulteriori informazioni su questo progetto, vedere [Procedura dettagliata: creazione di un editor personalizzato](../extensibility/walkthrough-creating-a-custom-editor.md).

## <a name="synchronizing-views"></a>Sincronizzazione delle viste
 Quando si implementano più visualizzazioni, l'oggetto dati del documento è responsabile della sincronizzazione di tutte le visualizzazioni con i dati. È possibile utilizzare le interfacce di gestione degli eventi per <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> sincronizzare più visualizzazioni con i dati.

 Se non si <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> utilizza l'oggetto per sincronizzare più visualizzazioni, è necessario implementare un sistema di eventi personalizzato per gestire le modifiche apportate all'oggetto dati del documento. È possibile utilizzare diversi livelli di granularità per mantenere aggiornate più visualizzazioni. Con un'impostazione di massima granularità, durante la digitazione in una visualizzazione le altre visualizzazioni vengono aggiornate immediatamente. Con la granularità minima, le altre viste non vengono aggiornate fino a quando non vengono attivate.

## <a name="determining-whether-document-data-is-already-open"></a>Determinare se i dati del documento sono già apertiDetermining whether Document Data is Already Open
 La tabella documenti in esecuzione (RDT) nell'ambiente di sviluppo integrato (IDE) consente di tenere traccia se i dati per un documento sono già aperti, come illustrato nel diagramma seguente.

 ![Immagine di DocDataView](../extensibility/media/docdataview.gif "Docdataview") Visualizzazioni multiple

 Per impostazione predefinita, ogni visualizzazione (oggetto visualizzazione documento) è contenuta nella relativa cornice della finestra ( ).<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Come già osservato, tuttavia, i dati del documento possono essere visualizzati in più visualizzazioni. A tale scopo, Visual Studio controlla RDT per determinare se il documento in questione è già aperto in un editor. Quando l'IDE chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> per creare l'editor, un `punkDocDataExisting` valore non NULL restituito nel parametro indica che il documento è già aperto in un altro editor. Per ulteriori informazioni sul funzionamento di RDT, vedere [Esecuzione della tabella documenti](../extensibility/internals/running-document-table.md).

 Nell'implementazione, esaminare <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> l'oggetto `punkDocDataExisting` dati del documento restituito per determinare se i dati del documento sono appropriati per l'editor. Ad esempio, solo i dati HTML devono essere visualizzati da un editor HTML. Se è appropriato, la factory dell'editor deve fornire una seconda visualizzazione per i dati. Se `punkDocDataExisting` il parametro non `NULL`è , è possibile che l'oggetto dati del documento sia aperto in un altro editor o, più probabilmente, che i dati del documento siano già aperti in una visualizzazione diversa con lo stesso editor. Se i dati del documento sono aperti in un editor diverso non supportato dalla factory dell'editor, Visual Studio non riesce ad aprire la factory dell'editor. Per ulteriori informazioni, vedere [Procedura: associare viste ai dati del documento](../extensibility/how-to-attach-views-to-document-data.md).
