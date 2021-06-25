---
title: Oggetti contesto di selezione | Microsoft Docs
description: Informazioni sugli elementi interni del modo in cui l Visual Studio IDE usa un oggetto contesto di selezione globale per determinare gli elementi da visualizzare nell'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b0c97108eaba426a4def4c1052d3adc7348eb88b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898487"
---
# <a name="selection-context-objects"></a>Oggetti del contesto di selezione
L'ambiente di sviluppo integrato (IDE) usa un oggetto contesto di selezione globale per determinare gli elementi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da visualizzare nell'IDE. Ogni finestra nell'IDE può avere un proprio oggetto contesto di selezione inserito nel contesto di selezione globale. L'IDE aggiorna il contesto di selezione globale con i valori di una finestra quando tale finestra ha lo stato attivo. Per altre informazioni, vedere [Commenti e suggerimenti per l'utente.](../../extensibility/internals/feedback-to-the-user.md)

 Ogni frame di finestra o sito nell'IDE ha un servizio denominato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . L'oggetto creato dal pacchetto VSPackage posizionato nella cornice della finestra deve chiamare il metodo per `QueryService` ottenere un puntatore all'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

 Le finestre cornice possono evitare che parti delle informazioni sul contesto di selezione vengano propagate al contesto di selezione globale quando vengono avviate. Questa funzionalità è utile per le finestre degli strumenti che potrebbero iniziare con una selezione vuota.

 La modifica del contesto di selezione globale attiva eventi che i pacchetti VSPackage possono monitorare. I pacchetti VSPackage possono eseguire le attività seguenti implementando `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> le interfacce e :

- Aggiornare il file attualmente attivo in una gerarchia.

- Monitorare le modifiche a determinati tipi di elementi. Ad esempio, se il pacchetto VSPackage usa una finestra Proprietà **speciale,** è possibile monitorare le modifiche nella finestra Proprietà **attiva** e riavviare il pacchetto quando necessario.

  La sequenza seguente illustra il corso tipico del rilevamento della selezione.

1. L'IDE recupera il contesto di selezione dalla finestra appena aperta e lo inserisce nel contesto di selezione globale. Se il contesto di selezione HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, le informazioni non vengono propagate al contesto globale. Per altre informazioni, vedere [Commenti e suggerimenti per l'utente.](../../extensibility/internals/feedback-to-the-user.md)

2. Gli eventi di notifica vengono trasmessi a qualsiasi VSPackage che li ha richiesti.

3. Il VSPackage agisce sugli eventi ricevuti eseguendo attività come l'aggiornamento di una gerarchia, la riattivazione di uno strumento o altre attività simili.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)
