---
title: Supporto di più visualizzazioni documento | Microsoft Docs
description: Informazioni su come fornire più di una visualizzazione di un documento usando dati del documento e oggetti visualizzazione documento separati per l'editor personalizzato in Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - multiple document views
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 67c61071ee877e147d806a29f7c36c0dad1eb848
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117436"
---
# <a name="supporting-multiple-document-views"></a>Supporto di più visualizzazioni documento
È possibile fornire più di una visualizzazione di un documento creando dati del documento e oggetti visualizzazione documento separati per l'editor. Di seguito sono riportati alcuni casi in cui sarebbe utile una visualizzazione aggiuntiva del documento:

- Supporto per la nuova finestra: si vuole che l'editor fornirà due o più visualizzazioni dello stesso tipo,  in modo che un utente che ha già una finestra aperta nell'editor possa aprire una nuova finestra selezionando il comando Nuova finestra dal **menu** Finestra.

- Supporto per le visualizzazioni modulo e codice: si vuole che l'editor fornirà visualizzazioni di tipi diversi. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], ad esempio, fornisce sia una visualizzazione form che una visualizzazione codice.

  Per altre informazioni, vedere la procedura CreateEditorInstance nel file EditorFactory.cs nel progetto dell'editor personalizzato creato dal modello Visual Studio pacchetto. Per altre informazioni su questo progetto, vedere [Procedura dettagliata: Creazione di un editor personalizzato.](../extensibility/walkthrough-creating-a-custom-editor.md)

## <a name="synchronizing-views"></a>Sincronizzazione delle viste
 Quando si implementano più viste, l'oggetto dati del documento è responsabile della sincronizzazione di tutte le viste con i dati. È possibile usare le interfacce di gestione degli eventi in <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> per sincronizzare più visualizzazioni con i dati.

 Se non si usa l'oggetto per sincronizzare più visualizzazioni, è necessario implementare il proprio sistema di eventi per gestire le modifiche <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> apportate all'oggetto dati del documento. È possibile usare diversi livelli di granularità per mantenere aggiornate più visualizzazioni. Con un'impostazione di massima granularità, durante la digitazione in una vista le altre viste vengono aggiornate immediatamente. Con la granularità minima, le altre viste non vengono aggiornate fino a quando non vengono attivate.

## <a name="determining-whether-document-data-is-already-open"></a>Determinare se i dati del documento sono già aperti
 La tabella dei documenti in esecuzione nell'ambiente di sviluppo integrato (IDE) consente di rilevare se i dati per un documento sono già aperti, come illustrato nel diagramma seguente.

 ![Grafico DocDataView](../extensibility/media/docdataview.gif "Docdataview") Più visualizzazioni

 Per impostazione predefinita, ogni visualizzazione (oggetto visualizzazione documento) è contenuta nella propria cornice della finestra ( <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> ). Come già detto, tuttavia, i dati del documento possono essere visualizzati in più visualizzazioni. A tale scopo, Visual Studio controllo RDT per determinare se il documento in questione è già aperto in un editor. Quando l'IDE chiama per creare l'editor, un valore non NULL restituito nel parametro indica che il documento <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> è già aperto in un altro `punkDocDataExisting` editor. Per altre informazioni sul funzionamento di RDT, vedere [Running Document Table](../extensibility/internals/running-document-table.md).

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>Nell'implementazione esaminare l'oggetto dati del documento restituito in per determinare se i dati `punkDocDataExisting` del documento sono appropriati per l'editor. Ad esempio, solo i dati HTML devono essere visualizzati da un editor HTML. Se è appropriato, la factory dell'editor deve fornire una seconda visualizzazione per i dati. Se il parametro non è , è possibile che l'oggetto dati del documento sia aperto in un altro editor o, più probabilmente, che i dati del documento siano già aperti in una visualizzazione diversa con lo stesso `punkDocDataExisting` `NULL` editor. Se i dati del documento sono aperti in un editor diverso che la factory dell'editor non supporta, Visual Studio non riesce ad aprire la factory dell'editor. Per altre informazioni, vedere [Procedura: Associare visualizzazioni ai dati del documento](../extensibility/how-to-attach-views-to-document-data.md).
