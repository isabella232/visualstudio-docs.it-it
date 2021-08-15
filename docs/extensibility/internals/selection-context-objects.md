---
title: Oggetti del contesto di selezione | Microsoft Docs
description: Informazioni sui componenti interni di come l Visual Studio IDE usa un oggetto contesto di selezione globale per determinare cosa deve essere visualizzato nell'IDE.
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
ms.openlocfilehash: 5eb966ef49d4de7533b9022c37113b05a46fa42b7e985a36086215a445e7b406
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121238424"
---
# <a name="selection-context-objects"></a>Oggetti del contesto di selezione
L'ambiente di sviluppo integrato (IDE) usa un oggetto contesto di selezione globale per determinare gli elementi da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] visualizzare nell'IDE. Ogni finestra nell'IDE può avere un proprio oggetto contesto di selezione inserito nel contesto di selezione globale. L'IDE aggiorna il contesto di selezione globale con i valori di una finestra quando tale finestra ha lo stato attivo. Per altre informazioni, vedere [Commenti e suggerimenti per l'utente.](../../extensibility/internals/feedback-to-the-user.md)

 Ogni frame di finestra o sito nell'IDE ha un servizio denominato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . L'oggetto creato dal pacchetto VSPackage che si trova nel frame della finestra deve chiamare il metodo per `QueryService` ottenere un puntatore all'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

 Le finestre cornice possono evitare che parti delle informazioni sul contesto di selezione vengano propagate al contesto di selezione globale quando vengono avviate. Questa funzionalità è utile per le finestre degli strumenti che potrebbero essere necessario iniziare con una selezione vuota.

 La modifica del contesto di selezione globale attiva eventi che i pacchetti VSPackage possono monitorare. I pacchetti VSPackage possono eseguire le attività seguenti implementando `IVsTrackSelectionEx` <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> e le interfacce:

- Aggiornare il file attualmente attivo in una gerarchia.

- Monitorare le modifiche a determinati tipi di elementi. Ad esempio, se il pacchetto  VSPackage usa una finestra Proprietà speciale, è possibile monitorare le modifiche nella finestra Proprietà **attiva** e riavviare il pacchetto quando necessario.

  La sequenza seguente illustra il corso tipico del rilevamento della selezione.

1. L'IDE recupera il contesto di selezione dalla finestra appena aperta e lo inserisce nel contesto di selezione globale. Se il contesto di selezione HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, queste informazioni non vengono propagate al contesto globale. Per altre informazioni, vedere [Commenti e suggerimenti per l'utente.](../../extensibility/internals/feedback-to-the-user.md)

2. Gli eventi di notifica vengono trasmessi a qualsiasi VSPackage che li ha richiesti.

3. Il pacchetto VSPackage agisce sugli eventi ricevuti eseguendo attività quali l'aggiornamento di una gerarchia, la riattivazione di uno strumento o altre attività simili.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Project Types](../../extensibility/internals/project-types.md) (Tipi di progetto)
