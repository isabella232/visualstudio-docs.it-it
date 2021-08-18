---
title: Completamento delle istruzioni in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sul funzionamento del completamento delle istruzioni e su come implementarlo nel servizio di linguaggio legacy in un VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6b84a36b61aeed08de0aeb9c359fe9d32653e939
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137691"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Completamento delle istruzioni in un servizio di linguaggio legacy
Il completamento delle istruzioni è il processo tramite il quale il servizio di linguaggio consente agli utenti di terminare una parola chiave o un elemento del linguaggio che hanno iniziato a digitare nell'editor principale. Questo argomento illustra il funzionamento del completamento delle istruzioni e come implementarlo nel servizio di linguaggio.

 I servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare il completamento delle istruzioni, vedere [Procedura dettagliata: Visualizzazione del completamento delle istruzioni](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. In questo modo si miglioreranno le prestazioni del servizio di linguaggio e si potranno sfruttare le nuove funzionalità dell'editor.

## <a name="implementing-statement-completion"></a>Implementazione del completamento delle istruzioni
 Nell'editor principale il completamento delle istruzioni attiva un'interfaccia utente speciale che consente di scrivere codice in modo più semplice e rapido. Il completamento delle istruzioni consente di visualizzare oggetti o classi pertinenti quando sono necessari, evitando così di dover ricordare elementi specifici o di cercarli in un argomento di riferimento della Guida.

 Per implementare il completamento delle istruzioni, il linguaggio deve disporre di un trigger di completamento dell'istruzione, che può essere analizzato. Ad esempio, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] usa un operatore punto (.), mentre usa un operatore freccia [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] (->). Un servizio di linguaggio può usare più trigger per avviare il completamento delle istruzioni. Questi trigger vengono programmati nel filtro dei comandi.

## <a name="command-filters-and-triggers"></a>Filtri e trigger dei comandi
 I filtri di comando intercettano le occorrenze del trigger o dei trigger. Per aggiungere il filtro di comando alla vista, implementare l'interfaccia e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> associarla alla vista chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo . È possibile usare lo stesso filtro di comando ( ) per tutti gli aspetti del servizio di linguaggio, ad esempio il completamento delle istruzioni, i marcatori di errore <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> e i suggerimenti sui metodi. Per altre informazioni, vedere [Intercettazione di comandi legacy del servizio di linguaggio](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Quando il trigger viene immesso nell'editor, in particolare il buffer di testo, il servizio di linguaggio chiama quindi il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo . In questo modo l'editor visualizza l'interfaccia utente in modo che l'utente possa scegliere tra i candidati per il completamento delle istruzioni. Questo metodo richiede l'implementazione <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> di e i flag come <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> parametri. L'elenco di elementi di completamento viene visualizzato in una casella di riepilogo a scorrimento. Mentre l'utente continua a digitare, la selezione all'interno della casella di riepilogo viene aggiornata in modo da riflettere la corrispondenza più vicina ai caratteri più recenti digitati. L'editor principale implementa l'interfaccia utente per il completamento delle istruzioni, ma il servizio di linguaggio deve implementare l'interfaccia per definire un set di elementi di completamento <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> candidati per l'istruzione.

## <a name="see-also"></a>Vedi anche
- [Intercettazione dei comandi dei servizi di linguaggio legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
