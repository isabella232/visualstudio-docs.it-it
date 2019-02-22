---
title: Gli oggetti di contesto di selezione | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- selection, tracking
- selection, context objects
ms.assetid: 7308ea8f-a42c-47e5-954e-7dee933dce7a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e6fa51b39cf6b4cf7917d560469eac06d43fee2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637776"
---
# <a name="selection-context-objects"></a>Oggetti del contesto di selezione
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) usa un oggetto di contesto di selezione globale per determinare che cosa deve essere visualizzata nell'IDE. Ogni finestra dell'IDE può avere un proprio oggetto di contesto di selezione il push nel contesto di selezione globale. L'IDE aggiorna il contesto di selezione globale con i valori da una finestra quando tale finestra ha lo stato attivo. Per altre informazioni, vedere [commenti e suggerimenti all'utente](../../extensibility/internals/feedback-to-the-user.md).

 Ogni frame della finestra o un sito nell'IDE offre un servizio chiamato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. L'oggetto creato dal pacchetto VSPackage che viene posizionato nella cornice della finestra che deve chiamare il `QueryService` metodo per ottenere un puntatore al <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> interfaccia.

 Finestre cornice consente di mantenere le parti relative informazioni di contesto di selezione la propagazione al contesto di selezione globale quando vengono avviate. Questa possibilità è utile per le finestre degli strumenti che potrebbero essere necessario avviare con una selezione vuota.

 Modifica gli eventi del trigger di contesto di selezione globale in grado di monitorare i pacchetti VSPackage. I VSPackage possono eseguire le attività seguenti implementando `IVsTrackSelectionEx` e <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> interfacce:

- Aggiornare il file attualmente attivo in una gerarchia.

- Monitorare le modifiche a determinati tipi di elementi. Ad esempio, se il pacchetto VSPackage Usa una speciale **delle proprietà** finestra, è possibile monitorare le modifiche in attivo **proprietà** finestra e quelle in uso quando è necessario riavviare.

  La sequenza seguente illustra il corso tipico di traccia della selezione.

1.  L'IDE recupera il contesto della selezione dalla finestra appena aperta e lo inserisce nel contesto di selezione globale. Se il contesto di selezione Usa HIERARCHY_DONTPROPAGATE o SELCONTAINER_DONTPROPAGATE, tali informazioni non viene propagate al contesto globale. Per altre informazioni, vedere [commenti e suggerimenti all'utente](../../extensibility/internals/feedback-to-the-user.md).

2.  Eventi di notifica vengono trasmessi a un pacchetto VSPackage che li richiesta.

3.  Il pacchetto VSPackage agisce sugli eventi che riceve eseguendo attività come l'aggiornamento di una gerarchia, la riattivazione di uno strumento o altre operazioni simili.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>
- [Gerarchie in Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
- [Selezione e valuta nell'IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [Tipi di progetto](../../extensibility/internals/project-types.md)