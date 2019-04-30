---
title: Completamento delle istruzioni in un servizio di linguaggio Legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- statement completion
- language services, statement completion
ms.assetid: 617439dc-3f0e-4e5f-b346-3e4e7fcf3c1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcc86d8c43703b0274c5282c9f4f843f760e697c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428902"
---
# <a name="statement-completion-in-a-legacy-language-service"></a>Completamento delle istruzioni in un servizio di linguaggio legacy
Completamento delle istruzioni è il processo mediante il quale il servizio di linguaggio consente agli utenti di completare una parola chiave del linguaggio o l'elemento che è stato avviato la digitazione nell'editor principale. Questo argomento illustra come funziona il completamento delle istruzioni e come implementarlo nel servizio di linguaggio.

 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni sul nuovo modo per implementare il completamento delle istruzioni, vedere [procedura dettagliata: Visualizzazione del completamento istruzioni](../../extensibility/walkthrough-displaying-statement-completion.md).

> [!NOTE]
> È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.

## <a name="implementing-statement-completion"></a>Implementazione di completamento istruzioni
 Nell'editor principale, il completamento delle istruzioni attiva un'interfaccia utente speciale in modo interattivo consente più facilmente e rapidamente scrittura codice. Completamento delle istruzioni facilita mediante la visualizzazione di classi o gli oggetti pertinenti quando sono necessari, che consente di evitare di dover ricordare elementi specifici o che sia necessario cercarli in un argomento di riferimento della Guida.

 Per implementare il completamento delle istruzioni, il linguaggio deve avere un trigger di completamento istruzione, che può essere analizzato. Ad esempio, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Usa un operatore punto (.), mentre [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] viene utilizzata una freccia (->) operatore. Un servizio di linguaggio possa usare più di un trigger per avviare il completamento delle istruzioni. Questi trigger vengono programmati nel filtro di comando.

## <a name="command-filters-and-triggers"></a>Filtri di comando e trigger
 Filtri di comando di intercettare le occorrenze del trigger o del trigger. Per aggiungere il filtro di comando per la visualizzazione, implementare il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia e collegarlo alla visualizzazione chiamando il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> (metodo). È possibile usare lo stesso filtro di comando (<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>) per tutti gli aspetti del servizio linguaggio, ad esempio il completamento delle istruzioni, i marcatori di errore e i suggerimenti di metodo. Per altre informazioni, vedere [intercetta comandi del servizio di linguaggio Legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md).

 Quando il trigger viene immesso nell'editor, in particolare, il buffer di testo, quindi chiama il servizio di linguaggio il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> (metodo). In questo modo l'editor visualizzare l'interfaccia utente in modo che l'utente può scegliere tra i candidati di completamento istruzione. Questo metodo richiede l'implementazione <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> e il <xref:Microsoft.VisualStudio.TextManager.Interop.UpdateCompletionFlags> flag come parametri. Verrà visualizzato l'elenco di elementi di completamento in una casella di riepilogo dello scorrimento. Quando l'utente continua a digitare, la selezione all'interno della casella di elenco viene aggiornata per riflettere che la corrispondenza più vicina ai più recenti caratteri tipizzati. L'editor principale implementa l'interfaccia utente per il completamento delle istruzioni, ma il servizio di linguaggio deve implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> interfaccia per definire un set di elementi di completamento candidato per l'istruzione.

## <a name="see-also"></a>Vedere anche
- [Intercettazione dei comandi dei servizi di linguaggio legacy](../../extensibility/internals/intercepting-legacy-language-service-commands.md)