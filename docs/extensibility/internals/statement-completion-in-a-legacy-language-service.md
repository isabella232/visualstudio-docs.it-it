---
title: Completamento delle istruzioni in un servizio di linguaggio Legacy . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbeb360cf5bc0f74d6b2d9b93086382dd35da988
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704934"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Completamento delle istruzioni in un servizio di linguaggio legacy
Il completamento delle istruzioni è il processo mediante il quale il servizio di linguaggio consente agli utenti di completare una parola chiave del linguaggio o un elemento che hanno iniziato a digitare nell'editor principale. In questo argomento viene illustrato il funzionamento del completamento delle istruzioni e come implementarlo nel servizio di linguaggio.

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni sul nuovo modo di implementare il completamento delle istruzioni, vedere [Procedura dettagliata: visualizzazione del completamento](../../extensibility/walkthrough-displaying-statement-completion.md)delle istruzioni .

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="implementing-statement-completion"></a>Implementazione del completamento delle istruzioniImplementing Statement Completion
 Nell'editor principale, il completamento delle istruzioni attiva un'interfaccia utente speciale che consente di scrivere codice in modo più semplice e rapido. Il completamento delle istruzioni consente di visualizzare oggetti o classi pertinenti quando sono necessari, evitando di dover ricordare elementi specifici o di cercarli in un argomento di riferimento della Guida.

 Per implementare il completamento delle istruzioni, il linguaggio deve disporre di un trigger di completamento delle istruzioni, che può essere analizzato. Ad esempio, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] utilizza un operatore [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] punto (.), mentre utilizza un operatore freccia (->). Un servizio di linguaggio può usare più di un trigger per avviare il completamento delle istruzioni. Questi trigger sono programmati nel filtro dei comandi.

## <a name="command-filters-and-triggers"></a>Filtri e trigger dei comandi
 I filtri dei comandi intercettano le occorrenze del trigger o dei trigger. Per aggiungere il filtro di comando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> alla visualizzazione, implementare l'interfaccia e associarlo alla visualizzazione chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo . È possibile utilizzare lo<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>stesso filtro di comando ( ) per tutti gli aspetti del servizio di linguaggio, ad esempio il completamento delle istruzioni, gli indicatori di errore e i suggerimenti per i metodi. Per ulteriori informazioni, vedere [Intercettazione di comandi del servizio](../../extensibility/internals/intercepting-legacy-language-service-commands.md)di linguaggio Legacy .

 Quando il trigger viene immesso nell'editor, in particolare nel <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> buffer di testo, il servizio di linguaggio chiama quindi il metodo . In questo modo l'editor per visualizzare l'interfaccia utente in modo che l'utente può scegliere tra i candidati di completamento delle istruzioni. Questo metodo richiede <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> l'implementazione e i <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> flag come parametri. L'elenco degli elementi di completamento viene visualizzato in una casella di riepilogo a scorrimento. Mentre l'utente continua a digitare, la selezione all'interno della casella di riepilogo viene aggiornata per riflettere la corrispondenza più vicina ai caratteri digitati più di recente. L'editor principale implementa l'interfaccia utente per il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> completamento delle istruzioni, ma il servizio di linguaggio deve implementare l'interfaccia per definire un set di elementi di completamento candidati per l'istruzione.

## <a name="see-also"></a>Vedere anche
- [Intercettazione dei comandi dei servizi di linguaggio legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
