---
title: Completamento delle istruzioni in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sul funzionamento del completamento delle istruzioni e su come implementarlo nel servizio di linguaggio legacy in un pacchetto VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 815b47a700e87852596d7a65e341953f65b66cf9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894829"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Completamento delle istruzioni in un servizio di linguaggio legacy
Il completamento delle istruzioni è il processo mediante il quale il servizio di linguaggio consente agli utenti di completare una parola chiave o un elemento del linguaggio che hanno iniziato a digitare nell'editor principale. In questo argomento viene illustrato il funzionamento del completamento delle istruzioni e come implementarlo nel servizio di linguaggio.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni sul nuovo modo per implementare il completamento delle istruzioni, vedere [procedura dettagliata: visualizzazione del completamento delle istruzioni](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

## <a name="implementing-statement-completion"></a>Completamento istruzione di implementazione
 Nell'editor principale, il completamento delle istruzioni attiva un'interfaccia utente speciale che consente di scrivere codice in modo interattivo in modo più semplice e rapido. Il completamento delle istruzioni consente di visualizzare gli oggetti o le classi pertinenti quando sono necessari, evitando di dover ricordare elementi specifici o di cercarli in un argomento di riferimento della guida.

 Per implementare il completamento delle istruzioni, il linguaggio deve avere un trigger di completamento delle istruzioni, che può essere analizzato. Ad esempio, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Usa un operatore punto (.), mentre [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Usa un operatore Arrow (->). Un servizio di linguaggio può utilizzare più di un trigger per avviare il completamento delle istruzioni. Questi trigger sono programmati nel filtro dei comandi.

## <a name="command-filters-and-triggers"></a>Filtri e trigger dei comandi
 I filtri di comando intercettano le occorrenze del trigger o dei trigger. Per aggiungere il filtro del comando alla visualizzazione, implementare l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia e collegarla alla visualizzazione chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metodo. È possibile utilizzare lo stesso filtro di comando ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) per tutti gli aspetti del servizio di linguaggio, ad esempio il completamento delle istruzioni, i marcatori di errore e i suggerimenti dei metodi. Per ulteriori informazioni, vedere [intercettazione dei comandi del servizio di linguaggio legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Quando il trigger viene immesso nell'editor, in particolare il buffer di testo, il servizio di linguaggio chiama il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> metodo. Questo fa sì che l'editor possa visualizzare l'interfaccia utente in modo che l'utente possa scegliere tra i candidati per il completamento delle istruzioni. Per questo metodo è necessario implementare <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> e i <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> flag come parametri. L'elenco degli elementi di completamento viene visualizzato in una casella di riepilogo a scorrimento. Quando l'utente continua a digitare, la selezione all'interno della casella di riepilogo viene aggiornata per riflettere la corrispondenza più vicina ai caratteri più recenti digitati. L'editor principale implementa l'interfaccia utente per il completamento delle istruzioni, ma il servizio di linguaggio deve implementare l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaccia per definire un set di elementi di completamento candidati per l'istruzione.

## <a name="see-also"></a>Vedi anche
- [Intercettazione dei comandi dei servizi di linguaggio legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md)
