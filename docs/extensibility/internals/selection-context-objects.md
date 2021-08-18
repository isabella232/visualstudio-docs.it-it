---
title: Oggetti del contesto di selezione | Microsoft Docs
description: Informazioni sui componenti interni del modo in cui l Visual Studio IDE usa un oggetto contesto di selezione globale per determinare cosa deve essere visualizzato nell'IDE.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6e6df11b81a48a95d9c401ff801be548923c6f52
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122132275"
---
# <a name="selection-context-objects"></a>Oggetti del contesto di selezione
L'ambiente di sviluppo integrato (IDE) usa un oggetto contesto di selezione globale per determinare ciò che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve essere visualizzato nell'IDE. Ogni finestra nell'IDE può avere un proprio oggetto contesto di selezione inserito nel contesto di selezione globale. L'IDE aggiorna il contesto di selezione globale con i valori di una finestra quando tale finestra ha lo stato attivo. Per altre informazioni, vedere [Commenti e suggerimenti per l'utente.](../../extensibility/internals/feedback-to-the-user.md)

 Ogni frame di finestra o sito nell'IDE ha un servizio denominato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . L'oggetto creato dal pacchetto VSPackage che si trova nel frame della finestra deve chiamare il metodo per `QueryService` ottenere un puntatore all'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

 Le finestre cornice possono evitare che parti delle informazioni sul contesto di selezione vengano propagate al contesto di selezione globale quando vengono avviate. Questa funzionalità è utile per le finestre degli strumenti che potrebbero essere necessario iniziare con una selezione vuota.

 La modifica del contesto di selezione globale attiva gli eventi che i pacchetti VSPackage possono monitorare. I pacchetti VSPackage possono eseguire le attività seguenti implementando `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> e le interfacce:

- Aggiornare il file attualmente attivo in una gerarchia.

- Monitorare le modifiche a determinati tipi di elementi. Ad esempio, se il pacchetto  VSPackage usa una finestra proprietà speciale, è possibile monitorare le modifiche nella finestra Proprietà **attiva** e riavviare il pacchetto quando necessario.

  La sequenza seguente illustra il corso tipico del rilevamento della selezione.

1. L'IDE recupera il contesto di selezione dalla finestra appena aperta e lo inserisce nel contesto di selezione globale. Se il contesto di selezione usa HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, queste informazioni non vengono propagate al contesto globale. Per altre informazioni, vedere [Commenti e suggerimenti per l'utente.](../../extensibility/internals/feedback-to-the-user.md)

2. Gli eventi di notifica vengono trasmessi a qualsiasi VSPackage che li ha richiesti.

3. Il pacchetto VSPackage agisce sugli eventi ricevuti eseguendo attività quali l'aggiornamento di una gerarchia, la riattivazione di uno strumento o altre attività simili.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)
